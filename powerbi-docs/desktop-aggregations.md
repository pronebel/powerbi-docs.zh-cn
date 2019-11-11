---
title: 在 Power BI Desktop 中使用聚合
description: 在 Power BI Desktop 中对大数据执行交互式分析
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ab84795ff5d140f23f19184bbc40e91133854f1f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876738"
---
# <a name="aggregations-in-power-bi-desktop"></a>Power BI Desktop 中的聚合

使用 Power BI 中的“聚合”  ，通过以前无法实现的方式对大数据执行交互式分析。 聚合可以大幅度降低为制定决策而解锁大型数据集的成本  。

![Microsoft Power BI Desktop 中的聚合](media/desktop-aggregations/aggregations_07.jpg)

以下介绍了使用聚合的优势  ：

* 针对大数据的查询性能  ：用户在 Power BI 报表中与视觉对象交互时，DAX 查询会被提交给数据集。 使用详细信息级别所需的一小部分资源，通过在聚合级别缓存数据来提高查询速度。 通过原本无法实现的方式解锁大数据。
* **数据刷新优化**：通过在聚合级别缓存数据来减小缓存大小，降低刷新时间。 加快为用户提供数据的速度。
* **实现平衡体系结构**：支持 Power BI 内存中缓存，以有效处理聚合查询。 限制在 DirectQuery 模式下发送到数据源的查询，帮助保持在并发限制内。 通过的查询通常是经筛选的事务级查询，数据仓库和大数据系统通常能很好地处理此类查询。

### <a name="table-level-storage"></a>表级别存储
表级别存储通常与聚合功能一起使用。 请参阅 [Power BI Desktop 中的存储模式](desktop-storage-mode.md)一文了解详细信息。

### <a name="data-source-types"></a>数据源类型
聚合可与表示维度模型的数据源一起使用，例如数据仓库、数据市场以及基于 Hadoop 的大数据源。 本文介绍每种数据源在 Power BI 中的典型建模差异。

所有 Power BI 导入和 DirectQuery 源（非多维）都可与聚合一起使用。

## <a name="aggregations-based-on-relationships"></a>基于关系的聚合

基于关系的聚合通常与维度模型一起使用  。 源自数据仓库和数据市场的 Power BI 数据集类似于星型/雪花型架构，且维度表和事实数据表之间的关系。

请考虑下述模型，它源自单个数据源。 假设所有表在开始时都使用 DirectQuery。 “Sales”事实数据表包含数十亿行  。 将“Sales”的存储模式设置为“导入”，缓存将占用大量内存和管理开销   。

![模型中的表](media/desktop-aggregations/aggregations_02.jpg)

相反，创建一个“Sales Agg”表作为聚合表  。 它的粒度高于“Sales”  表，因此所含行数更少。 行数应等于按 CustomerKey、DateKey 和 ProductSubcategoryKey 分组的 SalesAmount 的总和     。 没有数十亿行，可能是数百万行，更易于管理。

假设以下维度表最常用于具有高业务价值的查询。 这些表可以使用一对多（或多对一）关系对“Sales Agg”表决心筛选    。

* 地域
* 客户
* 日期
* 产品子类别
* 产品类别

下图展示了此模型。

![模型中的聚合表](media/desktop-aggregations/aggregations_03.jpg)

> [!NOTE]
> “Sales Agg”表只是另一个表，因此可通过各种方式加载  。 例如，可使用 ETL/ELT 进程或通过表的 [M 表达式](/powerquery-m/power-query-m-function-reference)在源数据库中执行聚合。 它可使用“导入”存储模式（有无 [Power BI Premium 中的增量刷新](service-premium-incremental-refresh.md)均可），或者可以是 DirectQuery 并使用[列存储索引](https://docs.microsoft.com/sql/relational-databases/indexes/columnstore-indexes-overview)针对快速查询进行了优化。 这种灵活性实现了平衡的体系结构，分散查询负载，避免堵塞。

### <a name="storage-mode"></a>存储模式 
继续以当前所用示例为例。 将“Sales Agg”的存储模式设为“导入”，提高查询速度   。

![设置存储模式](media/desktop-aggregations/aggregations_04.jpg)

执行此操作时，将显示以下对话框，告知相关的维度表可被设置为“双”  存储模式。 

![存储模式对话框](media/desktop-aggregations/aggregations_05.jpg)

将其设置为“双”模式后，相关的维度表即可充当“导入”或 DirectQuery，具体取决于子查询  。

* 可从内存缓存中返回查询，这些查询聚合“Sales Agg”表（该表是“导入”模式）中的指标，并按相关“双”模式表中的属性进行分组  。
* 可在 DirectQuery 模式下返回查询，这些查询聚合“Sales”表（该表是“DirectQuery”模式）中的指标，并按相关“双”模式表中的属性进行分组  。 查询逻辑（包括按操作分组）将向下传递到源数据库。

有关“双”存储模式的详细信息，请参阅[存储模式](desktop-storage-mode.md)一文  。

### <a name="strong-vs-weak-relationships"></a>强和弱关系
基于关系的聚合命中率要求强关系。

强关系包括以下组合，其中两个表均来自单个源  。

| “*多”端上的表 | “一”  端上的表 |
| ------------- |----------------------| 
| 双          | 双                 | 
| 导入        | 导入或双       | 
| DirectQuery   | DirectQuery 或双  | 

跨源  关系被视为强的唯一情况是两个表都为导入时。 多对多关系始终被视为弱。

有关不依赖于关系的跨源  聚合命中率，请参阅以下有关基于分组依据列的聚合部分。

### <a name="aggregation-tables-are-not-addressable"></a>聚合表不可寻址
对数据集具有只读访问权限的用户无法查询聚合表。 这可以避免与 RLS 一起使用时的安全问题。 使用者和查询可引用详细信息表，而不是聚合表；他们甚至无需知道存在聚合表。

出于此原因，应隐藏“销售聚合”表  。 如果不是，则在单击“全部应用”按钮时，管理聚合对话框会将其设置为隐藏。

### <a name="manage-aggregations-dialog"></a>管理聚合对话框
接下来将定义聚合。 右键单击“Sales Agg”表，选择“管理聚合”上下文菜单   。

![管理聚合菜单选项](media/desktop-aggregations/aggregations_06.jpg)

将显示“管理聚合”对话框  。 它为“Sales Agg”表中的每一列显示一行，可在其中指定聚合行为  。 提交到引用“Sales”表的 Power BI 数据集的查询将内部重定向到“Sales Agg”表   。 数据集的使用者甚至无需知道存在“Sales Agg”表  。

![管理聚合对话框](media/desktop-aggregations/aggregations_07.jpg)

下表显示“Sales Agg”表的聚合  。

![聚合表](media/desktop-aggregations/aggregations-table_01.jpg)

#### <a name="summarization-function"></a>汇总函数

汇总下拉列表提供以下可选值。
* 计数
* GroupBy
* 最大值
* 最小值
* 求和
* 计算表行数

#### <a name="validations"></a>验证

对话框强制实施以下重要验证：

* 所选详细信息列的数据类型必须与聚合列相同，“计数”和“计算表行数”汇总函数除外。 “计数”和“计算表行数”仅用于整数聚合列，且无需匹配的数据类型。
* 不允许使用涉及三个（及以上）表的链式聚合。 例如，如果表 B 的聚合引用表 C，则不能在表 A 上设置引用表 B 的聚合    。
* 不允许使用重复聚合，重复聚合是指两个项使用相同的汇总函数并引用相同的详细信息表/列。
* 详细信息表必须为 DirectQuery 模式，不能为“导入”模式。

大多数此类验证可通过禁用下拉值并在工具提示中显示解释性文本实施，如下图所示。

![通过工具提示显示的验证](media/desktop-aggregations/aggregations_08.jpg)

### <a name="group-by-columns"></a>按列分组

在此示例中，三个 GroupBy 项是可选的；它们不会影响聚合行为（DISTINCTCOUNT 示例查询除外，图示将随后附上）。 将它们包含在内主要是为了阅读方便。 如果不使用这些 GroupBy 项，聚合仍可根据关系命中。 这种行为不同于使用不带关系的聚合，本文后面部分的大数据示例将对此进行介绍。

### <a name="inactive-relationships"></a>非活动关系
不支持通过由非活动关系使用的外键列进行分组以及依赖 USERELATIONSHIP 函数进行聚合命中。

### <a name="detecting-whether-aggregations-are-hit-or-missed-by-queries"></a>检测查询是否命中聚合

若要深入了解如何使用 SQL Profiler 检测查询是返回自内存中缓存（存储引擎）还是 DirectQuery（推送到数据源），请参阅文章[存储模式](desktop-storage-mode.md)。 该过程还可以用于检测聚合是否将被命中。

此外，SQL Profiler 中还提供以下扩展事件。

    Query Processing\Aggregate Table Rewrite Query

下面的 JSON 代码片段显示了使用聚合时的事件输出示例。

* matchingResult 表示子查询使用了聚合  。
* dataRequest 表示子查询所用的分组依据列和聚合列  。
* mapping 表示已映射到的聚合表中的列  。

![使用聚合时的事件输出](media/desktop-aggregations/aggregations-code_01.jpg)

### <a name="query-examples"></a>查询示例
下面的查询命中聚合，因为“Date”表中的列为可以命中聚合的粒度  。 将使用 SalesAmount 的 Sum 聚合   。

![查询示例](media/desktop-aggregations/aggregations-code_02.jpg)

以下查询不会命中聚合。 尽管请求的是“SalesAmount”  的总和，但它将对“Product”  表中的列执行分组操作，该表的粒度不能命中聚合。 如果观察模型中的关系，产品子类别可以包含多个“Product”  行；查询将无法确定要聚合到哪种产品。 在这种情况下，查询将恢复为 DirectQuery 并将 SQL 查询提交到数据源。

![查询示例](media/desktop-aggregations/aggregations-code_03.jpg)

聚合不只是用于执行简单求和的简单计算。 复杂计算也能获益。 从概念上讲，复杂计算可针对每个 SUM、MIN、MAX 和 COUNT 划分为子查询，并且对每个子查询求值，以确定是否可以命中聚合。 由于查询计划优化，此逻辑并非在所有情况下都正确，但一般情况下都适用。 下面的示例将命中聚合：

![查询示例](media/desktop-aggregations/aggregations-code_04.jpg)

COUNTROWS 函数可以受益于聚合。 以下查询将命中聚合，因为针对“Sales”  表定义了计算  表行聚合。

![查询示例](media/desktop-aggregations/aggregations-code_05.jpg)

AVERAGE 函数可以受益于聚合。 以下查询将命中聚合，因为 AVERAGE 的内部计算方法为 SUM 除以 COUNT。 由于 UnitPrice 列具有针对 SUM 和 COUNT 定义的聚合，因此将命中聚合  。

![查询示例](media/desktop-aggregations/aggregations-code_06.jpg)

在某些情况下，DISTINCTCOUNT 函数可受益于聚合。 下面的查询将命中聚合，因为 CustomerKey  有 GroupBy 项，可在聚合表中维持 CustomerKey  的独特性。 此技术仍受性能阈值约束，非重复值超过 200 万到 500 万左右会影响查询性能。 然而，它可用于以下方案：详细信息表中包含数十亿行，列中包含 200 到 500 万个非重复值。 在这种情况下，非重复计数执行速度快于扫描包含数十亿行的表，即使缓存到内存中也是如此。

![查询示例](media/desktop-aggregations/aggregations-code_07.jpg)

### <a name="rls"></a>RLS
行级别安全性 (RLS) 表达式应同时筛选聚合表和详细信息表，以便正常工作。 在此示例中，“地理位置”表上的 RLS 表达式将起作用，因为“销售”表和“销售聚合”表的关系筛选都可筛选地理位置    。 无论查询是否命中聚合表，都将成功应用 RLS。

![聚合管理角色](media/desktop-aggregations/manage-roles.jpg)

“产品”表上的 RLS 表达式将仅筛选“销售”表，而不筛选“销售聚合”表    。 不建议这样做。 使用此角色访问数据集的用户所提交的查询无法将从聚合命中中获益。 由于聚合表是详细信息表中相同数据的另一种表示形式，因此应答聚合表中的查询是不安全的，因为无法应用 RLS 筛选器。

“销售聚合”表本身的 RLS 表达式将仅筛选聚合表而不筛选详细信息表  。 不允许这样。

![聚合管理角色](media/desktop-aggregations/filter-agg-error.jpg)

## <a name="aggregations-based-on-group-by-columns"></a>基于分组依据列的聚合 

基于 Hadoop 的大数据模型的特征与维度模型不同。 为避免大型表之间出现联接，它们通常不依赖关系。 相反，维度属性通常非规范化为事实表。 可以使用基于分组依据列的聚合解锁此类大数据模型，以便进行交互式分析  。

下表包含要聚合的“移动”数值列  。 其他所有列都为要分组的属性。 它包含 IoT 数据和大量行。 存储模式为 DirectQuery。 由于容量巨大，对跨整个数据集聚合的数据源的查询运行缓慢。

![IoT 表](media/desktop-aggregations/aggregations_09.jpg)

为了对此数据集启用交互式分析，我们添加了按大多数属性分组的聚合表，但经度和纬度等基数较大的属性除外。 这极大地减少了行数，使其小到足以顺利放入内存中缓存。 “Driver Activity Agg”表的存储模式为“导入”  。

![“Driver Activity Agg”表](media/desktop-aggregations/aggregations_10.jpg)

接下来，我们定义“管理聚合”对话框中的聚合映射  。 它为“Driver Activity Agg”表中的每一列显示一行，可在其中指定聚合行为  。

![“Driver Activity Agg”表的“管理聚合”对话框](media/desktop-aggregations/aggregations_11.jpg)

下表显示“Driver Activity Agg”表的聚合  。

![“Driver Activity Agg”聚合表](media/desktop-aggregations/aggregations-table_02.jpg)

### <a name="group-by-columns"></a>按列分组

在此示例中，GroupBy  项不可选  ；如果不使用该项，则不能命中聚合。 这种行为与使用基于关系的聚合不同，后者已在本文前面部分的维度模型示例中介绍。

### <a name="query-examples"></a>查询示例

下面的查询将命中聚合，因为聚合表中涵盖了“Activity Date”  列。 “计算表行数”聚合由 COUNTROWS 函数使用。

![查询示例](media/desktop-aggregations/aggregations-code_08.jpg)

尤其对于包含事实数据表中的筛选器属性的模型，使用“计算表行数”聚合是个好办法。 在用户未显式请求的情况下，Power BI 可能使用 COUNTROWS 向数据集提交查询。 例如，筛选器对话框显示每个值的行计数。

![筛选器对话框](media/desktop-aggregations/aggregations_12.jpg)

### <a name="rls"></a>RLS

以上详述的 RLS 规则不仅适用于基于关系的聚合，对于 RLS 表达式是否可以筛选聚合表和/或详细信息表，它也适用于基于按列分组的聚合。 在此示例中，应用于“驾驶员活动”表的 RLS 表达式可用于筛选“驾驶员活动聚合”表，因为聚合表中的所有按列分组数据都涵盖在详细信息表中   。 另一方面，“驾驶员活动聚合”表上的 RLS 筛选器不能应用于“驾驶员活动”表，因此不允许使用   。

## <a name="aggregation-precedence"></a>聚合优先级

聚合优先级允许单个子查询使用多个聚合表。

请考虑以下示例。 它是包含多个 DirectQuery 源的[复合模型](desktop-composite-models.md)。

* “Driver Activity Agg2”导入表的粒度很高，因为分组依据属性较少且基数较低  。 行数可以低至数千个，如此即可轻松放入内存中缓存。 这些属性恰好由高配置执行仪表板所用，因此引用它们的查询的运行速度应该很快。
* “Driver Activity Agg”表是 DirectQuery 模式的中间聚合表  。 它在 Azure SQL DW 中包含数十亿行，并已使用列存储索引在源处优化。
* “Driver Activity”表为 DirectQuery 模式，且包含源于大数据系统的数十亿行 IoT 数据  。 它充当钻取查询，用于查看受控制筛选器上下文中的各个 IoT 读数。

> [!NOTE]
> 只有当聚合表来自 SQL Server、Azure SQL 或 Azure SQL DW 源时，才支持将使用不同数据源的 DirectQuery 聚合表用于详细信息表。

此模型的内存占用量相对较小，但可解锁大型数据集。 它表示一种平衡的体系结构，因为它可根据使用查询负载的各体系结构组件的优势，将查询负载分散于各个组件。

![用于解锁大型数据集且内存占用较小的模型的表](media/desktop-aggregations/aggregations_13.jpg)

“Driver Activity Agg2”的“管理聚合”对话框显示“优先级”字段为 10（高于“Driver Activity Agg”的值），这意味着使用聚合进行查询时将首先考虑该表     。 如果子查询的粒度未在“Driver Activity Agg2”可应答范围内，则查询将转而考虑“Driver Activity Agg”   。 两个聚合表都无法应答的详细信息查询将被定向到“Driver Activity”  。

“详细信息表”列中指定的表为“Driver Activity”，而不是“Driver Activity Agg”，因为不允许使用链式聚合（请参阅本文前面的[验证](#validations)部分）    。

![管理聚合对话框](media/desktop-aggregations/aggregations_14.jpg)

下表显示“Driver Activity Agg2”表的聚合  。

![“Driver Activity Agg2”聚合表](media/desktop-aggregations/aggregations-table_03.jpg)

## <a name="aggregations-based-on-group-by-columns-combined-with-relationships"></a>基于分组依据列并结合了关系的聚合

甚至可以结合使用本文前面部分所述的两种聚合技术。 基于关系的聚合可能要求将非规范化维度表拆分为多个表  。 如果这对某些维度表而言代价较大或不切实际，可复制该聚合表中的必要属性，以供其他聚合所用的某些维度和关系使用。

以下模型复制了“Sales Agg”表中的“Month”、“Quarter”、“Semester”和“Year”      。 “Sales Agg”和“Date”表之间没有任何关系   。 具有指向“Customer”和“Product Subcategory”的关系   。 “Sales Agg”的存储模式为“导入”  。

![结合聚合技术](media/desktop-aggregations/aggregations_15.jpg)

下表显示了在“Sales Agg”表的“管理聚合”对话框中设置的项   。 “Date”为详细信息表的 GroupBy 项为必选项，以命中用于按“Date”属性分组的查询的聚合  。 如上一示例所示，因为存在关系（DISTINCTCOUNT 再次除外），所以 CustomerKey 和 ProductSubcategoryKey 的 GroupBy 项不会影响聚合命中。

![“Sales Agg”聚合表](media/desktop-aggregations/aggregations-table_04.jpg)

### <a name="query-examples"></a>查询示例

下面的查询将命中聚合，因为聚合表中包含 CalendarMonth，且 CategoryName 可通过一对多关系访问。 将使用 SalesAmount 的 Sum 聚合  。

![查询示例](media/desktop-aggregations/aggregations-code_09.jpg)

下面的查询不会命中聚合，因为聚合表中不包含 CalendarDay。

![查询示例](media/desktop-aggregations/aggregations-code_10.jpg)

以下时间智能查询不会命中聚合，因为 DATESYTD 函数将生成一个 CalendarDay 值表，该表不包含在聚合表中。

![查询示例](media/desktop-aggregations/aggregations-code_11.jpg)

## <a name="caches-should-be-kept-in-sync"></a>缓存应保持同步

如果内存中缓存与源数据不同步，结合使用 DirectQuery 和“导入”和/或“双”存储模式的聚合可能会返回不同的数据  。 查询执行不会试图掩盖数据问题，例如，通过筛选 DirectQuery 结果以匹配缓存值。 这些功能属于性能优化，且只能以不影响满足业务需求的方式使用。 你有责任了解自己的数据流，因此请相应地进行设计。 如有必要，可通过一些现成的技术处理源中的此类问题。

## <a name="next-steps"></a>后续步骤

以下文章提供了更多有关复合模型的信息，并详细介绍了 DirectQuery。

* [Power BI Desktop 中的复合模型](desktop-composite-models.md)
* [Power BI Desktop 中的多对多关系](desktop-many-to-many-relationships.md)
* [Power BI Desktop 中的存储模式](desktop-storage-mode.md)

DirectQuery 文章：

* [在 Power BI 中使用 DirectQuery](desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支持的数据源](desktop-directquery-data-sources.md)
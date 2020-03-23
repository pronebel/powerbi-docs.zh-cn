---
title: 分页报表的数据检索指南
description: 为 Power BI 分页报表创建数据源和数据集的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 067171f7ec74beccdb5a312c1cac5bbc6c87541f
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377641"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>分页报表的数据检索指南

本文面向设计 Power BI [分页报表](../paginated-reports/paginated-reports-report-builder-power-bi.md)的报表作者。 它提供了一些建议，可帮助你设计有效且高效的数据检索。

## <a name="data-source-types"></a>数据源类型

分页报表本身支持关系数据源和分析数据源。 这些源可进一步分类，分为基于云的或本地的。 本地数据源（无论是在本地托管还是在虚拟机中）需要数据网关，以便 Power BI 可以连接。 基于云的表示 Power BI 可以使用 Internet 连接直接连接。

如果可以选择数据源类型（新项目中很可能如此），建议使用基于云的数据源。 连接分页报告的网络延迟较低，特别是数据源与 Power BI 租户位于同一区域时。 此外，还可以使用单一登录 (SSO) 连接到这些源。 这意味着报表用户的标识可以流向数据源，从而允许强制按用户授予行级权限。 目前，本地数据源不支持 SSO（这意味着 SQL Server Analysis Services 不强制按用户授予行级权限）。

> [!NOTE]
> 虽然目前无法使用 SSO 连接到本地数据库，但仍可强制执行行级别权限。 通过将 UserID 内置字段传递到数据集查询参数来完成此操作  。 数据源将需要存储用户主体名称 (UPN) 值，以便能够正确筛选查询结果。
>
> 例如，请考虑将每位销售人员存储为“销售人员”表中的一行  。  该表包含 UPN 列以及销售人员的销售区域。 查询时，按报表用户的 UPN 对表进行筛选，该表还使用内部联接与销售事实相关联。 这样，查询便有效地从销售事实行中筛选出报表用户销售区域的行。

### <a name="relational-data-sources"></a>关系数据源

通常，关系数据源非常适合于操作样式报表，如销售发票。 它们还适用于需要检索超大型数据集的报表（超过 10,000 行）。 关系数据源还可以定义可由报表数据集执行的存储过程。 存储过程提供多个优点：

- 参数化
- 封装编程逻辑，允许进行更复杂的数据准备（例如临时表、游标或标量用户定义函数）
- 改进了可维护性，使存储过程逻辑易于更新。 在某些情况下，无需修改和重新发布分页报表（前提是列名和数据类型保持不变）。
- 改进了性能，因为缓存了它们的执行计划以供重用
- 跨多个报表重用存储过程

在 Power BI Report Builder 中，可以使用关系查询设计器以图形方式构造查询语句，但仅适用于 Microsoft 数据源。

### <a name="analytic-data-sources"></a>分析数据源

分析数据源非常适合于操作报表和分析报表，可以提供快速汇总的查询结果，甚至是对于非常大的数据卷。 模型度量值和 KPI 可以封装复杂的业务规则以实现数据的汇总。 但是，这些数据源不适用于需要检索超大型数据集的报表（超过 10,000 行）。

在 Power BI Report Builder 中，可以选择两个查询设计器：Analysis Services DAX 查询设计器，和 Analysis Services MDX 查询设计器。 这些设计器可用于 Power BI 数据集数据源或任何 SQL Server Analysis Services 或 Azure Analysis Services 模型（表格或多维）。

建议使用 DAX 查询设计器，只要它能完全满足查询需求。 如果模型没有定义所需的度量值，则需要切换到查询模式。 在此模式下，可以通过添加表达式来自定义查询语句（以实现汇总）。

MDX 查询设计器要求模型包含度量值。 该设计器具有 DAX 查询设计器不支持的两项功能。 具体而言，它允许以下操作：

- 定义查询级别的计算成员（在 MDX 中）。
- 将数据区域配置为请求非详细信息组中的[服务器聚合](/sql/reporting-services/report-design/report-builder-functions-aggregate-function)。 如果报表需要提供半加法或非加法度量值（如时间智能计算或非重复计数）的摘要，使用服务器聚合比检索低级别详细信息行和让报表计算摘要更有效。

## <a name="query-result-size"></a>查询结果大小

通常，最佳做法是只检索报表所需的数据。 因此，请不要检索报表所不需要的列或行。

若要限制行，应始终应用最严格的筛选器，并定义聚合查询。 聚合查询对源数据进行分组和汇总，以检索更高粒度的结果。 例如，假设你的报表需要提供销售人员销售额的汇总。 创建按销售人员分组的数据集查询，并汇总每个组的销售额，而不是检索所有销售订单行。

## <a name="expression-based-fields"></a>基于表达式的字段

可以使用基于表达式的字段来扩展报表数据集。 例如，如果有数据集源客户的名字和姓氏，你可能需要一个将这两个字段连接起来以生成客户全名的字段。 若要实现此计算，你有两个选择。 你可以：

- 创建一个“计算字段”，该字段是基于表达式的数据集字段  。
- 将表达式直接注入到数据集查询（使用数据源的本机语言），这会生成常规数据集字段。

建议尽可能地选择后一种方法。 直接将表达式注入数据集查询中有两个充分的理由：

- 你的数据源可能已进行了优化，可以比 Power BI 更有效地计算表达式（特别是关系数据库的情况）。
- 报表性能得到改进，因为 Power BI 不需要在呈现报表之前具体化计算字段。 数据集检索大量行时，计算字段可能明显延长报表呈现时间。

## <a name="field-names"></a>字段名

创建数据集时，其字段将自动按查询列命名。 可能这些名称不友好或不直观。 源查询列名也可能包含报表定义语言 (RDL) 对象标识符中不允许的字符（如空格和符号）。 在这种情况下，将用下划线字符 (_) 替换禁止使用的字符。

建议首先验证所有字段名称是否友好、简洁且仍具有意义。 如果不是，建议在开始报表布局之前重命名它们  。 这是因为重命名的字段不会将更改传播到报表布局中使用的表达式。 如果在开始报表布局之后决定重命名字段，则需要查找并更新所有损坏的表达式。

## <a name="filter-vs-parameter"></a>筛选器和参数

分页报表设计很可能会有报表参数。 报表参数通常用于提示报表用户筛选报表。 作为分页报表作者，你可以通过两种方式来实现报表筛选。 可以将报表参数映射到：

- 数据集筛选器，在这种情况下，报表参数值用于筛选数据集已检索的数据  。
- 数据集参数，在这种情况下，报表参数值将注入到发送到数据源的本机查询  。

> [!NOTE]
> 将按会话缓存所有报表数据集，最多缓存到上次使用后 10 分钟   。 提交新参数值（筛选）、以不同格式呈现报表，或以某种方式与报表设计交互（如切换可见性或排序）时，可以重新使用数据集。

假设有一个销售报表的示例，其中包含一个报表参数，用于按一年筛选报表。 数据集检索所有年份的销售  。 这是因为报表参数映射到数据集筛选器。 该报表显示请求年份的数据，该数据是数据集数据的一个子集。 如果报表用户将报表参数更改为其他年份，然后查看报表，则 Power BI 不需要检索任何源数据。 相反，它会将不同的筛选器应用于已缓存的数据集。 缓存数据集后，筛选可能会非常快。

现在，请考虑使用不同的报表设计。 这次报表设计会将销售年度报表参数映射到数据集参数。 这样，Power BI 会将年份值注入到本机查询中，数据集只检索该年份的数据。 每次报表用户更改年份报表参数值（然后查看报表）时，数据集都只检索对应于该年份的新查询结果。

这两种设计方法都可以筛选报表数据，并且这两种设计在报表设计中都很有用。 但是，优化的设计将取决于预期的数据量、数据波动性，以及预期的报表用户行为。

如果预期多次重复使用数据集行的不同子集，建议使用数据集筛选（这这样可以节省呈现时间，因为无需检索新数据）  。 在这种情况下，你会认识到检索更大的数据集的成本可以根据重复使用的次数进行权衡。 因此，对于需要较长时间才能生成的查询，这非常有用。 但请注意，按用户缓存大型数据集可能会对性能和容量吞吐量产生负面影响。

如果预计不太可能请求数据集行的不同子集，或筛选的数据集行的数量可能非常大（缓存效率低下），则建议使用数据集参数化  。 如果数据存储是可变的，则此设计方法也适用。 在这种情况下，每个报表参数值更改都将导致检索最新数据。

## <a name="non-native-data-sources"></a>非本机数据源

如果需要基于数据源开发分页报表，而这些数据源不[受分页报表本机支持](../paginated-reports/paginated-reports-data-sources.md)，可以先开发 Power BI Desktop 数据模型。 这样，你便可以连接到超过 100 的 [Power BI 数据源](../power-bi-data-sources.md)。 发布到 Power BI 服务后，即可开发连接到 Power BI 数据集的分页报表。

## <a name="data-integration"></a>数据集成

如果需要合并来自多个数据源的数据，可以使用两个选项：

- **合并报表数据集**：如果数据源[受分页报表本机支持](../paginated-reports/paginated-reports-data-sources.md)，则可以考虑创建使用 [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) 或 [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function) Report Builder 函数的计算字段。
- **开发 Power BI Desktop 模型**：但是，在 Power BI Desktop 中开发数据模型可能更有效。 可以使用 Power Query 根据任何[受支持的数据源](../power-bi-data-sources.md)来合并查询。 发布到 Power BI 服务后，即可开发连接到 Power BI 数据集的分页报表。

## <a name="sql-server-complex-data-types"></a>SQL Server 复杂数据类型

由于 SQL Server 是本地数据源，Power BI 必须通过网关进行连接。 但是，网关不支持为复杂数据类型检索数据。 复杂数据类型包括各种内置类型，例如 GEOMETRY 和 GEOGRAPHY [空间数据类型](/sql/relational-databases/spatial/spatial-data-sql-server)以及 [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)。 这些类型还包括用户定义类型通过 Microsoft.NET Framework 公共语言时 (CLR) 中的程序集的类来实现。

在地图可视化效果中绘制空间数据和分析需要 SQL Server 空间数据。 因此，SQL Server 是数据源时，不能使用地图可视化。 为清楚起见，如果数据源是 Azure SQL 数据库则可以使用，因为 Power BI 不通过网关进行连接。

## <a name="data-related-images"></a>数据相关图像

可以使用图像将徽标或图片添加到报表布局。 图像与报表数据集检索到的行相关时，有两种选择：

- 有可能还可以从数据源检索图像数据（如果已将其存储在表中）。
- 将映像存储在 web 服务器上时，可以使用动态表达式来创建映像 URL 路径。

有关详细信息和建议，请参阅[分页报表的图像指南](report-paginated-image.md)。

## <a name="redundant-data-retrieval"></a>冗余数据检索

报表可能会检索冗余数据。 当你删除数据集查询字段时，或当报表具有未使用的数据集时，可能会发生这种情况。 请避免发生这种情况，因为这会为数据源、网络和 Power BI 容量资源带来不必要的负担。

### <a name="deleted-query-fields"></a>删除的查询字段

在“数据集属性”窗口的“字段”页上，可以删除数据集查询字段（查询字段映射到由数据集查询检索到的列）    。 但 Report Builder 不会从数据集查询中删除相应的列。

如果需要从数据集中删除查询字段，建议从数据集查询中删除相应的列。 Report Builder 将自动删除任何冗余查询字段。 如果确实要删除查询字段，请确保同时修改数据集查询语句以删除这些列。

### <a name="unused-datasets"></a>未使用的数据集

报表运行时，将对所有数据集进行计算，即使它们未绑定到报表对象。 出于此原因，请确保在发布报表之前删除所有测试或开发数据集。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI 分页报表支持的数据源](../paginated-reports/paginated-reports-data-sources.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

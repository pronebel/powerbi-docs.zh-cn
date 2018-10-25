---
title: 在 Power BI Desktop 中使用存储模式（预览）
description: 使用存储模式来控制是否在 Power BI Desktop 中为报表在内存中缓存数据
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ce4aab1a477485a30a4166d86d166a4ac289108f
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45974221"
---
# <a name="storage-mode-in-power-bi-desktop-preview"></a>Power BI Desktop 中的存储模式（预览）

在 Power BI Desktop 中，可以指定表的存储模式，使你控制是否为报表在内存中缓存表数据。 

![Power BI Desktop 中的存储模式](media/desktop-storage-mode/storage-mode_01.png)

设置存储模式有许多优势。 可以在模型中为单个表单独设置存储模式，从而使单个数据集充分利用以下一个或多个优势：

* 查询性能 - 当用户在 Power BI 报表中与视觉对象交互时，DAX 查询会被提交给数据集。 通过正确设置存储模式将数据缓存到内存可提高查询性能并有助于和报表之间的交互。
* 大型数据集 - 未缓存的表不会出于缓存目的占用内存。 可以对大型数据集启用交互式分析，这些数据集因过大或过于昂贵而无法完全缓存到内存中。 可以选择哪些表值得缓存，而哪些不值得。
* 数据刷新优化 - 未缓存的表不需要刷新。 可以通过只缓存必要的数据来减少刷新次数，以满足你的服务级别协议和业务需求。
* 准实时需求 - 具有准实时需求的表可能从未缓存中受益，以减少数据延迟。
* 写回 - 写回使业务用户能够通过更改单元格值来探索模拟场景。 自定义应用程序可以将更改应用到数据源。 未缓存的表可以立即反映更改，以允许即时分析效果。

Power BI Desktop 中的存储模式设置是下列三个相关功能之一：

* 复合模型 - 允许报表在任何组合中有多个数据连接，包括 DirectQuery 连接或导入。
* 多对多关系 - 通过复合模型，可以在表之间建立多对多关系，进而删除表中的唯一值要求，并删除之前的解决办法，例如，引入新表只是为了建立关系。 
* 存储模式 - 现在，你可以指定哪些视觉对象需要对后端数据源进行查询，而那些不需要进行此查询的视觉对象则导入（即使是基于 DirectQuery），进而提升性能并减少后端负载。 在此之前，即使是像切片器这样的简单视觉对象，也会启动发送至后端源的查询。 

此复合模型的三个相关功能集合分别在不同文章中进行了说明：

* 复合模型在其专属文章 [Power BI Desktop 中的复合模型（预览）](desktop-composite-models.md)中详细介绍。
* 多对多关系在其专属文章 [Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)中介绍。
* 存储模式在本文中详细介绍。

## <a name="enabling-the-storage-mode-preview-feature"></a>启用存储模式预览功能

存储模式为预览功能，必须在 Power BI Desktop 中启用。 若要启用存储模式，请选择“文件”>“选项和设置”>“选项”>“预览功能”，然后选中“复合模型”复选框。 

![启用预览功能](media/desktop-composite-models/composite-models_02.png)

需要重新启动 Power BI Desktop 才能启用该功能。

![需要重新启动，更改才会生效](media/desktop-composite-models/composite-models_03.png)


## <a name="using-the-storage-mode-property"></a>使用存储模式属性

存储模式是一个属性，可以在模型的每个表上进行设置。 若要设置存储模式，从“字段”窗格中选择表，然后右键单击打开上下文菜单。 从上下文菜单中，选择“属性”。

![在上下文菜单中选择“属性”](media/desktop-storage-mode/storage-mode_02.png)

存储模式选择显示在表的“字段属性”窗格中。 从此处可以查看当前的存储模式或对其进行修改。

![为表设置存储模式](media/desktop-storage-mode/storage-mode_03.png)

存储模式有三个值：

* 导入 - 当设置为“导入”，将缓存导入表。 提交到 Power BI 数据集从导入表返回数据的查询只能从缓存数据中实现。
* DirectQuery - 使用此设置，DirectQuery 表不会被缓存。 提交给 Power BI 数据集从 DirectQuery 表返回数据的查询（例如，DAX 查询）只能通过对数据源执行按需查询来实现。 提交到数据源的查询使用该数据源的查询语言（例如，SQL）。
* 双 - 双表可以充当已缓存或未缓存，具体取决于提交到 Power BI 数据集的查询的上下文。 在某些情况下，查询通过缓存数据完成；在其他情况下，查询通过对数据源执行按需查询来完成。

将表更改为“导入”是一项不可逆操作；它不能更改回“DirectQuery”，或更改回“双”。

## <a name="constraints-on-directquery-and-dual-tables"></a>DirectQuery 表和“双”表约束

“双”表受到与 DirectQuery 表相同的约束。 其中包括有限的 M 转换，以及计算列中受限的 DAX 函数。 有关详细信息，请参阅[使用 DirectQuery 的影响](desktop-directquery-about.md#implications-of-using-directquery)。

## <a name="relationship-rules-on-tables-with-different-storage-modes"></a>针对具有不同存储模式的表的关系规则

关系必须符合基于相关表存储模式的规则。 本部分提供有效组合的示例。 有关完整信息，请参阅 [Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)。

在具有单一数据源的数据集上，以下 1 对多关系组合无效：

| 多端上的表 | 1 端上的表 |
| ------------- |----------------------| 
| 双          | 双                 | 
| 导入        | 导入或双       | 
| DirectQuery   | DirectQuery 或双  | 

## <a name="propagation-of-dual"></a>双传播
我们来看一个示例。 请考虑下列简单模型，其中所有表都来自支持导入和 DirectQuery 的单个源。

![存储模式的关系视图示例](media/desktop-storage-mode/storage-mode_04.png)

让我们假设 DirectQuery 将从此模型中的所有表开始。 然后，如果我们将 SurveyResponse 表的存储模式改为“导入”，则显示以下提示：

![存储模式警告对话框](media/desktop-storage-mode/storage-mode_05.png)

维度表（Customer、Date 和 Geography）必须设置为“双”，以符合前面所述的关系规则。 可以在单个操作中将这些表设置为“双”，而无需提前设置。

传播逻辑旨在帮助包含多个表的模型。 假设你有一个带 50 个表的模型，只有某些事实（事务）表需要进行缓存。 Power BI Desktop 中的逻辑指出需要设置为“双”的维度表的最小集，因此无需执行此操作。

传播逻辑仅遍历到 1 对多关系的一端。

* 将“Customer”表更改为“导入”（而不是更改 SurveyResponse）是不允许的，原因在于它与 DirectQuery 表“Sales”以及“SurveyResponse”的关系。
* 可以将“Customer”表更改为“双”（而不是更改 SurveyResponse）。 传播逻辑也将“Geography”表设置为“双”。

## <a name="storage-mode-usage-example"></a>存储模式的使用情况示例
让我们继续上一节中的示例，假设我们应用以下存储模式属性设置：

| 表格                   | 存储模式         |
| ----------------------- |----------------------| 
| *Sales*                 | DirectQuery          | 
| *SurveyResponse*        | 导入               | 
| *Date*                  | 双                 | 
| *Customer*              | 双                 | 
| *Geography*             | 双                 | 


执行这些存储模式属性设置会导致以下行为，假设“Sales”表有大量数据卷。
* 维度表（Date、Customer 和 Geography）将缓存，因此检索要显示的切片器值时，初始报表加载速度应较快。
* 如果不缓存“Sales”表，将出现以下结果：
    * 数据刷新速度得到提升，并会减少内存消耗
    * 基于“Sales”表的报表查询在 DirectQuery 模式下运行，这可能需要更长时间，但更接近实时，因为没有引入缓存延迟

* 基于“SurveyResponse”表的报表查询从内存中缓存返回，因此，它们应相对较快。

## <a name="queries-that-hit-or-miss-the-cache"></a>命中或错过缓存的查询

通过将 SQL Profiler 连接到 Power BI Desktop 的诊断端口，可以通过执行基于以下事件的跟踪来查看哪些查询命中或错过了内存中缓存：

* Queries Events\Query Begin
* Query Processing\Vertipaq SE Query Begin
* Query Processing\DirectQuery Begin

对于每个“Query Begin”事件，使用相同的 ActivityID 查看其他事件。 例如，如果没有任何“DirectQuery Begin”事件，但存在“Vertipaq SE Query Begin”事件，则已从缓存中对查询进行应答。

引用“双”模式表的查询从缓存中返回数据（如可能），否则它们会还原为 DirectQuery。

继续前面的示例，以下查询只引用“Date”表中的列，该表处于“双”模式。 因此，它应命中缓存。

![存储模式诊断脚本](media/desktop-storage-mode/storage-mode_06.png)

以下查询仅引用“Sales”表中的列，该表处于“DirectQuery”模式。 因此，它不应命中缓存。

![存储模式诊断脚本](media/desktop-storage-mode/storage-mode_07.png)

下面的查询非常有趣，因为它结合了这两个列。 此查询将不会命中缓存。 最初你可能希望它从缓存中检索 CalendarYear 值，并从源中检索 SalesAmount 值，然后将结果组合起来，但这样做的效率要低于将 SUM/GROUP BY 操作提交到源系统。 如果该操作向下推送到数据源，返回的行数可能会少得多。 

![存储模式诊断脚本](media/desktop-storage-mode/storage-mode_08.png)

> [!NOTE]
> 合并缓存和非缓存表时，此行为不同于 [Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)。

## <a name="caches-should-be-kept-in-sync"></a>缓存应保持同步

在上一节中显示的查询显示，“双”表有时会命中缓存，而有时不会命中缓存。 因此，如果缓存已过期，则可能返回不同的值。 查询执行不会试图掩盖数据问题，例如，通过筛选 DirectQuery 结果以匹配缓存值。 了解数据流是你的责任，并应相应地进行设计。 如有必要，有一些现成的技术可以在源中处理此类情况。

“双”存储模式是一种性能优化。 它只应在不影响满足业务需求功能的情况下使用。 对于备用行为，请考虑使用 [Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)一文中所述的技术。

## <a name="data-view"></a>数据视图
如果数据集中至少有一个表将其“存储模式”设置为“导入”或“双”，则会显示“数据视图”选项卡。

![Power BI Desktop 中的数据视图](media/desktop-storage-mode/storage-mode_09.png)

在“数据视图”中选择时，“双”表和“导入”表会显示缓存数据。 DirectQuery 表不显示数据，还显示了一条消息，表明 DirectQuery 表无法显示。


## <a name="limitations-and-considerations"></a>限制和注意事项

此版本的存储模式有一些限制，并与复合模型之间具有相关性。

以下 Live Connect（多维）源不能用于复合模型：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 数据集
* Azure Analysis Services

当使用 DirectQuery 连接到这些多维数据源时，不能同时连接到另一个 DirectQuery 源，也不能与导入的数据相结合。

在使用复合模型时，使用 DirectQuery 的现有限制仍然适用。 现在每个表都有许多这些限制，这取决于表的存储模式。 例如，导入表上的计算列可以引用其他表，但是 DirectQuery 表上的计算列仍限制为只能引用同一表上的列。 如果模型中的任何一个表都是 DirectQuery，则其他限制适用于整个模型。 例如，如果模型中有任何表具有 DirectQuery 的存储模式，则 QuickInsights 和问答功能在该模型上不可用。 

## <a name="next-steps"></a>后续步骤

以下文章提供了更多有关复合模型的信息，并详细介绍了 DirectQuery。

* [Power BI Desktop 中的复合模型（预览）](desktop-composite-models.md)
* [Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)

DirectQuery 文章：

* [在 Power BI 中使用 DirectQuery](desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支持的数据源](desktop-directquery-data-sources.md)


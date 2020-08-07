---
title: 访问 Excel 中的 Power BI 精选表（预览版）
description: 在 Excel 中，可以从数据类型库中 Power BI 数据集的精选表中查找数据。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/04/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 099e3aa11662232c5362895e93f0433620ce2ba9
ms.sourcegitcommit: a7227f6d3236e6e0a7bc1f83ff6099b5cd58bff3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768832"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>访问 Excel 中的 Power BI 精选表（预览版）

使用精选表可以将 Excel 中的数据链接到 Power BI 中的数据。 它使你可以更轻松地将企业数据添加到 Excel 工作表。 在 Excel 的数据类型库中，可以从 Power BI 数据集的精选表中查找数据。 本文介绍了如何执行此操作。

你是否在 Power BI 中创建数据集？ 请参阅[在 Power BI Desktop 中设置精选表](service-create-excel-featured-tables.md)。

> [!NOTE]
> 在 Excel 中，还可以分析可在 Power BI 中访问的任何 Power BI 数据集中的数据。 有关详细信息，请参阅“在 Excel 中分析 Power BI”一文中的[从 Excel 访问 Power BI 数据集的其他方法](service-analyze-in-excel.md#other-ways-to-access-power-bi-datasets-from-excel)。
> 

## <a name="the-excel-data-types-gallery"></a>Excel 数据类型库
Power BI 数据集中的特色表在 Excel“数据类型”库中的“数据”功能区上显示为数据类型 。

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel“数据”功能区中的“数据类型”库的屏幕截图。":::

展开库后，将显示通用数据类型（例如“股票”和“地理”），以及你可以使用的前十种“组织”数据类型（即来自 Power BI 数据集的精选表）  。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel 数据类型库的屏幕截图。":::

## <a name="search-for-power-bi-data-in-the-data-types-gallery"></a>在数据类型库中搜索 Power BI 数据

若要在 Power BI 精选表中查找数据，请在 Excel 工作表中选择一个单元格或某个范围，其中包含与精选表中的值匹配的值。 选择数据类型库旁边的“更多”箭头。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-more.png" alt-text="Excel 数据类型库中的“更多”图标的屏幕截图。":::

如果看到了要查找的表，请选择它。 否则，请选择“组织中的更多内容”。 Excel 将搜索你有权访问的所有精选表，查找匹配项。

:::image type="content" source="media/service-excel-featured-tables/excel-more-your-organization.png" alt-text="选择“组织中的更多内容”（预览）的屏幕截图。":::
 
Excel 会显示所有可能的表。 在“数据选择器”窗格的“筛选器”框中进行键入，以缩小选择范围 。 选择匹配的表。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-store.png" alt-text="Excel 组织数据、供应商数据类型表的屏幕截图。":::
 
如果 Excel 找到的匹配行具有高置信度，则该单元格会立即链接到这些行。 链接项图标指示单元格链接到 Power BI 中的行。

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="“链接项”图标的屏幕截图。":::

如果一个单元格包含多个潜在的匹配行，该单元格将显示一个问号图标，并将打开“数据选择器”窗格。 在下面的示例中，我们选择了 B3:B9 范围，然后搜索了 Power BI 精选表“Store”。 除单元格 B9“508 - Pasadena Lindseys”外，所有行都有匹配项。 “数据选择器”显示了两个可能的匹配项，在两个不同的表中显示相同的值。

:::image type="content" source="media/service-excel-featured-tables/excel-question-mark-featured-table.png" alt-text="Excel 数据选择器窗格的屏幕截图。":::
 
组织数据选项可以返回多个精选表的行。 Excel 按它们所源自的数据类型对可能匹配的行进行分组。 Excel 基于其最强的可能匹配行对数据类型进行排序。 使用 v 形箭头可以将数据类型折叠和展开到匹配行。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="具有多种可能性的 Excel 数据选择器窗格的屏幕截图。":::
 
对于每个建议，请在“数据选择器”窗格中选择行名称，以查看行中的更多详细信息，从而帮助你选择正确的行。 找到该行后，按“选择”将其链接到 Excel 中的单元格。 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="数据选择器详细信息的屏幕截图。":::

## <a name="explore-related-data"></a>浏览相关数据

现已在 Excel 工作表中的值和 Power BI 精选表中的数据之间创建了连接，接下来可以浏览该数据了。 使用这些数据来增强 Excel 报表。

### <a name="view-related-data-in-a-card"></a>查看卡片中的相关数据 
 
在单元格中选择“卡片”图标会显示一个卡片，其中包含来自精选表中的任何字段和计算字段的数据。 卡片的标题显示了精选表中行标签字段的值。
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="链接项详细信息的屏幕截图。":::

### <a name="insert-related-data-from-power-bi"></a>从 Power BI 插入相关数据 

选择“插入数据”图标，然后从字段列表中选择字段名称，以将其值添加到网格。  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="“选择字段名称”的屏幕截图。":::

字段值放置在相邻单元格中。 单元格公式会引用链接单元格和字段名称，因此可以使用 Excel 函数中的数据。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel 单元格公式的屏幕截图。":::

### <a name="use-cell-formulas"></a>使用单元格公式

在 Excel 表中，可以引用链接表列，然后使用 `.`（句点）引用添加数据字段。

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel 句点引用的屏幕截图。":::

同样，在单元格中，可以引用单元格并使用 `.`（句点）引用来检索字段。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="单元格句点引用的屏幕截图。":::

### <a name="show-a-card-change-or-convert-to-text"></a>显示卡片，更改或转换为文本

链接单元格已添加右键单击菜单选项。 右键单击单元格。 除了常见选项，还可以看到：

- **显示数据类型卡**。
- “数据类型” > “转换为文本” 。
- “数据类型” > “更改” 。
- **刷新**。

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="“右键单击”、“转换为文本”的屏幕截图。":::
 
“转换为文本”会删除指向 Power BI 精选表中相应行的链接。 重要的是，单元格中的文本将是链接单元格的行标签值。 如果已将某个单元格链接到不打算使用的行，请选择 Excel 中的“撤消”来还原初始单元格值。
 
## <a name="data-caching-and-refresh"></a>数据缓存和刷新

当 Excel 将某个单元格链接到 Power BI 精选表中的行时，它将检索并保存 Excel 文件中的所有字段值。 与你共享文件的任何人可以引用任何字段，无需请求 Power BI 的数据。  

使用“数据”功能区中的“全部刷新”按钮来刷新链接单元格中的数据。 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="“全部刷新”的屏幕截图。":::
 
还可以刷新单个单元格。 右键单击该单元格，然后选择“数据类型” > “刷新”。

## <a name="licensing"></a>许可

Excel 数据类型库和 Power BI 精选表的连接体验仅适用于 Excel E5 和 G5 客户。 

## <a name="security"></a>安全性

在 Power BI 中，只能看到有权访问的数据集中的精选表。 刷新数据时，必须具有访问 Power BI 中数据集的权限才能检索行。 需要[对 Power BI 中的数据集具有生成或写入权限](../connect-data/service-datasets-build-permissions.md)。
 
Excel 将为整行缓存返回的数据。 你与之共享 Excel 文件的任何人可以看到所有链接单元格中所有字段的数据。

如果 Power BI 数据集具有行级别安全性或应用了 Microsoft 信息保护敏感性标签，则该数据集中的精选表不会包含在 Excel 数据类型库中。 这是初始预览的一项限制。

## <a name="administrative-control"></a>管理控制

Power BI 管理员可以控制组织中哪些人可以使用 Excel 数据类型库中的精选表。 有关详细信息，请参阅管理门户中的[精选表设置](../admin/service-admin-portal.md#featured-tables-settings)。 
 
### <a name="auditing"></a>审核

管理审核日志会显示精选表的以下事件：

- AnalyzedByExternalApplication：使管理员可以查看哪些用户正在访问哪些精选表。
- UpdateFeaturedTables：使管理员可以查看哪些用户正在发布和更新精选表。

有关审核日志事件的完整列表，请参阅[在 Power BI 中跟踪用户活动](../admin/service-admin-auditing.md)。

## <a name="considerations-and-limitations"></a>注意事项和限制

下面是初始预览的一些限制：

- 集成功能在 Excel 预览体验成员版中提供。
- Excel 数据类型库包含具有 Power BI Desktop 和 Power BI 服务中相应许可证的用户的精选表。 在预览版发布时，可能不支持 Power BI 服务，但未来将添加该类支持。
- 具有以下功能的 Power BI 数据集中的精选表不在 Excel 中显示： 

    - 行级别安全性数据集。
    - 启用了 Microsoft 信息保护的数据集。
    - DirectQuery 数据集。
    - 具有实时连接的数据集。

- Excel 仅显示精选表的列和计算列中的数据。 初始预览中不提供以下内容：

    - 针对精选表定义的度量值。
    - 针对相关表定义的度量值以及从关系计算的隐式度量值。

- Excel 只显示新 Power BI 工作区中存储的精选表（数据类型）。 存储在经典工作区或“我的工作区”中的精选表不会在 Excel 中显示为数据类型。 你可以在 Power BI 中[将经典工作区升级到新工作区](service-upgrade-workspaces.md)。

Excel 中的数据类型体验类似于查找函数。 它采用 Excel 工作表提供的单元格值，并在 Power BI 的精选表中搜索匹配的行。 搜索体验具有以下行为：

- 使用“组织数据”按钮进行搜索时，Excel 只会搜索 Power BI 数据集中的精选表。
- 行匹配基于精选表中的文本列。 它使用的索引与 Power BI 问答功能一样，该功能针对英语语言搜索进行了优化。 在其他语言中搜索可能不会产生精确的匹配结果。 不考虑将数值列用于匹配。
- 匹配基于单个搜索词的精确和前缀匹配项。 单元格的值基于空格或制表符等其他空白字符进行拆分。 然后，每个词都被视为一个搜索词。 行的文本字段值将与每个搜索词进行比较以获得精确和前缀匹配结果。 如果行的文本字段以搜索词开头，则返回前缀匹配结果。 例如，如果单元格包含“Orange County”，则“Orange”和“County”就是不同的搜索词。 

    - 返回其文本列的值与“Orange”或“County”完全匹配的行。 
    - 返回其文本列的值以“Orange”或“County”开头的行。 
    - 重要的是，不会返回包含“Orange”或“County”但不以它们开头的行。

- Power BI 为每个单元格最多返回 100 行建议。
- XMLA 终结点不支持设置或更新精选表
- 具有数据模型的 Excel 文件可用于发布精选表。 将数据加载到 Power BI Desktop 中，然后发布精选表。
- 如果更改“表名”、“行标签”或“键列”，精选表可能会影响将单元格链接到表行的 Excel 用户。 
- Excel 会显示从 Power BI 数据集中检索数据的时间。 此时间并不一定是在 Power BI 中刷新数据的时间，也不一定是数据集中最新数据点的时间。 例如，假设 Power BI 中的数据集在一周前刷新，但基础源数据在刷新发生时已过时一周。 实际数据已存在 2 周，但 Excel 会将检索的数据显示为数据提取到 Excel 中的日期/时间。

## <a name="next-steps"></a>后续步骤

- [在 Power BI Desktop 中设置精选表](service-create-excel-featured-tables.md)
- 了解如何在 Excel 文档中[从 Power BI 使用 Excel 数据类型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)。
- 是否有任何问题? [尝试参与 Power BI 社区](https://community.powerbi.com/)


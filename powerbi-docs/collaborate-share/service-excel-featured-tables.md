---
title: 访问 Excel 中的 Power BI 精选表（预览版）
description: 在 Excel 中，可以从数据类型库中 Power BI 数据集的精选表中查找数据。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226349"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>访问 Excel 中的 Power BI 精选表（预览版）

在 Excel 中，可以从数据类型库中 Power BI 数据集的精选表中查找数据。 精选表使你可以更轻松地将企业数据添加到 Excel 工作表。 通过使用 Power BI 经过认证和升级的数据集功能，组织可支持更多用户查找和使用相关和可刷新的数据来做出更好的决策。 阅读有关在 Excel 文档中[从 Power BI 使用 Excel 数据类型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)的详细信息。

数据类型库仅显示建模者已在 Power BI 数据集中策展的精选表。 你还可以在 Excel 中浏览可在 Power BI 中访问的任何数据集。 在 Excel 中，在“数据”功能区的“获取数据”下选择“Power BI 数据集”  。

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>通过 Excel 数据类型库访问 Power BI 数据
Power BI 数据集的精选表显示在“数据”功能区的“Excel 数据类型库”中。

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel 数据功能区":::

展开后，库将显示排名靠前的可用数据类型。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel 数据类型库":::
 
若要在 Power BI 精选表中查找数据，请在 Excel 工作表中选择一个单元格或某个范围。

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="选择单元格":::
 
从库中选择“组织数据”选项，在你有权访问的已认证数据集的精选表中搜索数据。

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Excel 组织数据":::
 
如果知道要搜索的数据类型，或者使用“组织数据”选项找不到匹配行，请选择特定的数据类型。

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="选择数据类型":::
 
搜索时，如果找到的匹配行具有高置信度，则该单元格会立即链接到该行。 链接项图标指示单元格链接到 Power BI 中的行。

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="“链接项”图标":::

如果某个单元格包含多个可能的匹配行，则会显示数据选择器窗格。 单元格将显示问号图标，单击该图标会使数据选择器窗格打开到该行。 下面是用户选择 A2:A7 范围后搜索 Power BI 功能表的示例。

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="多个可能的匹配行":::

“数据选择器”窗格显示可能匹配的行。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Excel 数据选择器窗格":::
 
组织数据选项可以返回多个数据类型的行。 Excel 按它们所源自的数据类型对可能匹配的行进行分组。 Excel 基于其最强的可能匹配行对数据类型进行排序。 使用 v 形箭头可以将数据类型折叠和展开到匹配行。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Excel 数据选择器窗格":::
 
对于每一行，选择行名称可查看行中的更多详细信息，以帮助你选择正确的行。 找到行后，按“选择”将该行链接到 Excel 中的单元格。 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="数据选择器详细信息":::
 
选择某一行后，单元格将链接到该行，其值为 Power BI 精选表中的“行标签”字段的值。 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Excel 链接项":::
 
选择“链接单元格”图标会显示一个卡，其中包含来自精选表中的任何字段和计算字段的数据。 卡片的标题显示了精选表中行标签字段的值。
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="链接项详细信息":::

选择“插入数据”图标以向网格中添加字段值。

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="插入数据"::: 

从字段列表中选择字段名称，以将其值添加到网格。  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="选择字段名称":::

字段值放置在相邻单元格中。 单元格公式会引用链接单元格和字段名称，因此可以使用 Excel 函数中的数据。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel 单元格公式":::
 
将数据设置为 Excel 表格式时，添加字段将展开该表，并设置列标题以与字段名称匹配。 链接到相同数据类型的行也将用各自的值填充。

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="字段是列名称"::: 

## <a name="cell-formulas"></a>单元格公式

使用 Excel 表时，可以引用链接表列，然后使用 `.`（句点）引用添加数据字段。

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel 句点引用":::

同样，在使用单元格时，可以引用单元格，使用 `.`（句点）引用来检索字段。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="单元格句点引用":::
 
## <a name="data-caching-and-refresh"></a>数据缓存和刷新

当 Excel 将某个单元格链接到 Power BI 精选表中的行时，它将检索并保存 Excel 文件中的所有字段值。 与你共享文件的任何人可以引用任何字段，无需请求 Power BI 的数据。  

使用“数据”功能区中的“全部刷新”按钮来刷新链接单元格中的数据。 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="全部刷新":::
 
还可以刷新单个单元格。 右键单击该单元格，然后选择“数据类型” > “刷新”。

## <a name="show-a-card-change-or-convert-to-text"></a>显示卡片，更改或转换为文本

链接单元格已添加右键单击菜单选项。 右键单击单元格 > 选择“数据类型” >  

- “显示卡片”
- **刷新**
- **更改** 
- “转换为文本”。

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="右键单击，然后选择“转换为文本”":::
 
“转换为文本”会删除指向 Power BI 精选表中相应行的链接。 重要的是，单元格中的文本将是链接单元格的行标签值。 如果已将某个单元格链接到不打算使用的行，请选择 Excel 中的“撤消”来还原初始单元格值。

## <a name="licensing"></a>许可
Excel 数据类型库和 Power BI 精选表的连接体验仅适用于 Excel E5 和 G5 客户。 

## <a name="security"></a>安全性

在 Power BI 中，只能看到有权访问的数据集中的精选表。 刷新数据时，必须具有访问 Power BI 中数据集的权限才能检索行。 这需要有数据集的生成或写入权限。 Excel 将为整行缓存返回的数据。 你与之共享 Excel 文件的任何人可以看到所有链接单元格中所有字段的数据。

如果 Power BI 数据集具有行级别安全性或应用了 Microsoft 信息保护敏感性标签，则该数据集中的精选表不会包含在 Excel 数据类型库中。 这是初始预览的一项限制。

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>在 Power BI Desktop 中策展精选表
Excel 数据类型库会显示上载到 Power BI 服务的数据集中的精选表。 使用 Power BI Desktop 策展数据模型中的精选表，并将其上传到 Power BI 服务中。

### <a name="turn-on-the-featured-table-preview"></a>启用精选表预览

1. 在 Power BI Desktop 中，选择“文件” > “选项和设置” > “选项” > “预览功能”。
2. 选中“精选表”复选框。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="预览精选表选项":::

### <a name="select-a-table"></a>选择表

1. 在 Power BI Desktop 中，转到“模型”视图。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="模型视图":::
 
2. 选择一个表，将“是精选表”设置为“是”。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="将“是精选表”设置为“是”":::

4. 在“设置此精选表”中，提供必填字段：

    - “说明”。
    - “行标签”字段值用于 Excel 中，因此用户可以轻松地识别该行。 它在“数据选择器”窗格中和“信息”卡中显示为链接单元格的单元格值。 
    - “键列”字段值提供唯一的行 ID。 通过此值，Excel 可以将单元格链接到表中的特定行。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="设置精选表":::

将数据集发布或导入到 Power BI 服务后，精选表会显示在 Excel 数据类型库中。

- Excel 将缓存数据类型列表，因此你需要重新启动 Excel 以查看新发布的精选表。
- 预览中不支持某些数据集，在 Excel 中不会显示这些数据集中定义的精选表。 有关详细信息，请参阅注意事项和限制。

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

- Excel 只显示新 Power BI 工作区中存储的精选表。 存储在经典工作区或“我的工作区”中的精选表不会在 Excel 中显示为数据类型。 你可以在 Power BI 中[将经典工作区升级到新工作区](service-upgrade-workspaces.md)。

Excel 中的数据类型体验类似于查找函数。 它采用 Excel 工作表提供的单元格值，并在 Power BI 的精选表中搜索匹配的行。 搜索体验具有以下行为：

- 使用“组织数据”按钮进行搜索时，Excel 只会搜索已验证数据集中的精选表。
- 行匹配基于精选表中的文本列。 它使用的索引与 Power BI 问答功能一样，该功能针对英语语言搜索进行了优化。 在其他语言中搜索可能不会产生精确的匹配结果。 不考虑将数值列用于匹配。
- 匹配基于单个搜索词的精确和前缀匹配项。 单元格的值基于空格或制表符等其他空白字符进行拆分。 然后，每个词都被视为一个搜索词。 行的文本字段值将与每个搜索词进行比较以获得精确和前缀匹配结果。 如果行的文本字段以搜索词开头，则返回前缀匹配结果。 例如，如果单元格包含“Orange County”，则“Orange”和“County”就是不同的搜索词。 

    - 返回其文本列的值与“Orange”或“County”完全匹配的行。 
    - 返回其文本列的值以“Orange”或“County”开头的行。 
    - 重要的是，不会返回包含“Orange”或“County”但不以它们开头的行。

- Power BI 为每个单元格最多返回 100 行建议。
- XMLA 终结点不支持设置或更新精选表
- 具有数据模型的 Excel 文件可用于发布精选表。 将数据加载到 Power BI Desktop 中，然后发布精选表。
- 如果更改“表名”、“行标签”或“键列”，精选表可能会影响将单元格链接到表行的 Excel 用户。 
- Excel 会显示从 Power BI 数据集中检索数据的时间。 这并不一定是 Power BI 中的数据刷新时间，也不一定是数据集中最近数据点的时间。 例如，假设 Power BI 中的数据集在一周前刷新，但基础源数据在刷新发生时已过时一周。 实际数据已过时 2 周，但 Excel 会将检索的数据显示为数据提取到 Excel 中的日期/时间。

## <a name="next-steps"></a>后续步骤

- 是否有任何问题? [尝试参与 Power BI 社区](https://community.powerbi.com/)


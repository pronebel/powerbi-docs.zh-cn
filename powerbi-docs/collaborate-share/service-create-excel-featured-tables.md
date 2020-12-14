---
title: 在 Power BI Desktop 中设置精选表
description: 在 Power BI Desktop 中创建精选表，以便它们显示在 Excel 的组织数据类型库中。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906879"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>在 Power BI Desktop 中设置精选表，使其显示在 Excel 的组织数据类型库中

在 Excel 中的数据类型库中，用户可以从 Power BI 数据集的精选表中查找数据。 在本文中，你将了解如何在数据集中将表设置为“精选”。 这些标记使用户能够更轻松地将企业数据添加到他们的 Excel 工作表中。 下面是设置和共享精选表的基本步骤。

1. 在 Power BI Desktop 中标识数据集中的精选表（本文）
1. 将带有精选表的数据集保存到某个新工作区中。 报表创建者可以创建带有那些精选表的报表。 
1. 组织的其余部分可以连接到那些精选表（在 Excel 中称为数据类型），以获取相关且可刷新的数据。 [在 Excel 中访问 Power BI 精选表](service-excel-featured-tables.md)一文介绍了如何在 Excel 中使用这些精选表。

> [!NOTE]
> 可以[在 Power BI 中推广或认证数据集](../collaborate-share/service-endorse-content.md)。 这称为认可。 Excel 会对数据类型库中已认可的数据集中的表区分优先级。 Excel 首先列出已认证的数据集中的精选表，然后列出已推广的数据集中的表。 之后，Excel 会列出未经认可的数据集中的精选表。 

> [!NOTE]
> 从 Power BI Desktop 的 2020 年 12 月版开始，默认情况下可以创建精选表。 如果使用早期版本，请升级 Power BI Desktop 或通过“文件” > “选项和设置” > “选项” > “预览功能”启用“精选表”功能    。

## <a name="select-a-table"></a>选择表

1. 在 Power BI Desktop 中，转到“模型”视图。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="模型视图":::
 
2. 选择一个表，将“是精选表”设置为“是”。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="将“是精选表”设置为“是”":::

4. 在“设置此精选表”中，提供必填字段：

    - “说明”。 
        > [!TIP]
        > 从“精选表”开始描述，以帮助 Power BI 报表创建者识别它。
    - “行标签”字段值用于 Excel 中，因此用户可以轻松地识别该行。 它在“数据选择器”窗格中和“信息”卡中显示为链接单元格的单元格值。 
    - “键列”字段值提供唯一的行 ID。 通过此值，Excel 可以将单元格链接到表中的特定行。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="设置精选表":::

1. 将数据集发布或导入到 Power BI 服务后，精选表会显示在 Excel 数据类型库中。 你和其他报表创建者还可以创建基于此数据集生成的报表。

1. 在 Excel 中： 
    - Excel 将缓存数据类型列表，因此你需要重新启动 Excel 以查看新发布的精选表。
    - 某些数据集不受支持。 在这些数据集中定义的精选表将不会显示在 Excel 中。 有关详细信息，请参阅下一节“注意事项和限制”。

## <a name="considerations-and-limitations"></a>注意事项和限制

当前限制如下：

- 集成功能在 Excel 当前通道中提供。
- 具有以下功能的 Power BI 数据集中的精选表不在 Excel 中显示： 

    - DirectQuery 数据集。
    - 具有实时连接的数据集。

- Excel 仅显示在精选表中定义的列、计算列和度量值中的数据。 未提供以下内容：
   
    - 相关表上定义的度量值。
    - 根据关系计算的隐式度量值。

- Excel 只显示新 Power BI 工作区中存储的精选表（数据类型）。 存储在经典工作区中的精选表不会在 Excel 中显示为数据类型。 你可以在 Power BI 中[将经典工作区升级到新工作区](service-upgrade-workspaces.md)。

Excel 中的数据类型体验类似于查找函数。 它采用 Excel 工作表提供的单元格值，并在 Power BI 的精选表中搜索匹配的行。 搜索体验具有以下行为：

- 行匹配基于精选表中的文本列。 它使用的索引与 Power BI 问答功能一样，该功能针对英语语言搜索进行了优化。 在其他语言中搜索可能不会产生精确的匹配结果。 
- 不考虑将大多数数值列用于匹配。 如果“行标签”或“键列”是数值，则将包含它们以进行匹配。
- 匹配基于单个搜索词的精确和前缀匹配项。 单元格的值基于空格或制表符等其他空白字符进行拆分。 然后，每个词都被视为一个搜索词。 行的文本字段值将与每个搜索词进行比较以获得精确和前缀匹配结果。 如果行的文本字段以搜索词开头，则返回前缀匹配结果。 例如，如果单元格包含“Orange County”，则“Orange”和“County”就是不同的搜索词。 

    - 返回其文本列的值与“Orange”或“County”完全匹配的行。 
    - 返回其文本列的值以“Orange”或“County”开头的行。 
    - 重要的是，不会返回包含“Orange”或“County”但不以它们开头的行。

- Power BI 为每个单元格最多返回 100 行建议。
- 不支持使用某些符号。
- XMLA 终结点不支持设置或更新精选表
- 具有数据模型的 Excel 文件可用于发布精选表。 将数据加载到 Power BI Desktop 中，然后发布精选表。
- 如果更改“表名”、“行标签”或“键列”，精选表可能会影响将单元格链接到表行的 Excel 用户。 
- Excel 会显示从 Power BI 数据集中检索数据的时间。 此时间并不一定是在 Power BI 中刷新数据的时间，也不一定是数据集中最新数据点的时间。 例如，假设 Power BI 中的数据集在一周前刷新，但基础源数据在刷新发生时已过时一周。 实际数据已存在 2 周，但 Excel 会将检索的数据显示为数据提取到 Excel 中的日期/时间。
- 有关其他 Excel 注意事项，请参阅“在 Excel 中访问 Power BI 精选表”一文中的[注意事项和限制](service-excel-featured-tables.md#considerations-and-limitations)。

## <a name="next-steps"></a>后续步骤

- [访问 Excel 中的 Power BI 精选表](service-excel-featured-tables.md)
- 了解如何在 Excel 文档中[从 Power BI 使用 Excel 数据类型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)。
- 是否有任何问题? [尝试参与 Power BI 社区](https://community.powerbi.com/)


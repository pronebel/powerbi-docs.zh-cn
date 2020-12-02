---
title: 在 Power BI Desktop 中设置精选表（预览版）
description: 在 Power BI Desktop 中创建精选表，以便它们显示在 Excel 的数据类型库中。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: d2d87f16b8100424b47277360354d79ee834d467
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411922"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>在 Power BI Desktop 中设置精选表（预览版）

在 Excel 中的数据类型库中，用户可以从 Power BI 数据集的精选表中查找数据。 在本文中，你将了解如何在数据集中将表设置为“精选”。 这些标记使用户能够更轻松地将企业数据添加到他们的 Excel 工作表中。 下面是设置和共享精选表的基本步骤。

1. 在 Power BI Desktop 中标识数据集中的精选表（本文）
1. 将带有精选表的数据集保存到某个新工作区中。 报表创建者可以创建带有那些精选表的报表。 
1. 组织的其余部分可以连接到那些精选表（在 Excel 中称为数据类型），以获取相关且可刷新的数据。 文章[在 Excel 中访问 Power BI 精选表（预览版）](service-excel-featured-tables.md)介绍如何在 Excel 中使用这些精选表。

> [!NOTE]
> 可以[在 Power BI 中推广或认证数据集](../collaborate-share/service-endorse-content.md)。 这称为认可。 Excel 会对数据类型库中已认可的数据集中的表区分优先级。 Excel 首先列出已认证的数据集中的精选表，然后列出已推广的数据集中的表。 之后，Excel 会列出未经认可的数据集中的精选表。 

## <a name="turn-on-the-featured-table-preview"></a>启用精选表预览

1. 在 Power BI Desktop 中，选择“文件” > “选项和设置” > “选项” > “预览功能”。
2. 选中“精选表”复选框。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="预览精选表选项":::

3. 重启 Power BI Desktop。

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
    - 预览中不支持某些数据集，在 Excel 中不会显示这些数据集中定义的精选表。 有关详细信息，请参阅下一节“注意事项和限制”。

## <a name="considerations-and-limitations"></a>注意事项和限制

下面是初始预览的一些限制。

- 具有以下功能的 Power BI 数据集中的精选表不在 Excel 中显示：

    - DirectQuery 数据集。
    - 具有实时连接的数据集。

- Excel 仅显示精选表的列和计算列中的数据。 初始预览中未提供针对相关表定义的度量值以及从关系计算的隐式度量值。
- Excel 只显示新 Power BI 工作区中存储的精选表。 存储在经典工作区中的精选表不会在 Excel 中显示为数据类型。 你可以在 Power BI 中[将经典工作区升级到新工作区](service-upgrade-workspaces.md)。
- 有关其他 Excel 注意事项，请参阅“在 Excel 中访问 Power BI 精选表”一文中的[注意事项和限制](service-excel-featured-tables.md#considerations-and-limitations)。

## <a name="next-steps"></a>后续步骤

- [访问 Excel 中的 Power BI 精选表](service-excel-featured-tables.md)
- 了解如何在 Excel 文档中[从 Power BI 使用 Excel 数据类型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)。
- 是否有任何问题? [尝试参与 Power BI 社区](https://community.powerbi.com/)


---
title: 在报表中个性化设置视觉对象
description: 创建自己的报表视图，而无需对其进行编辑。
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/13/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 718363da3bd1f66de199db8d854d8d23d6de3eb5
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256724"
---
# <a name="personalize-visuals-in-a-report"></a>在报表中个性化设置视觉对象

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

很难让一个视觉对象满足每个人的要求。 但是，当同事与你共享报表时，你可能需要更改视觉对象，而无需要求你的同事为你进行更改。 

你可能想要交换轴上的内容，更改视觉对象类型，或在工具提示中添加一些内容。 借助“个性化设置此视觉对象”功能自行进行更改，当你具有你想要的视觉对象时，将其另存为[书签](end-user-bookmarks.md)以便回头使用此视觉对象。 你甚至不需要报表的编辑权限。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="个性化设置视觉对象":::
 
## <a name="what-you-can-change"></a>可以更改的内容

此功能帮助你通过临时浏览 Power BI 报表上的视觉对象进行深入了解。 下面是一些你可以进行的修改。 可用选项因视觉对象类型而异。 

- 更改可视化效果类型
- 交换度量值或维度
- 添加或删除图例
- 比较两个或多个度量值
- 更改聚合等

此功能不仅允许新的探索功能。 它还包括捕获和共享更改的方式：

- 捕获所做的更改
- 共享所做的更改
- 重置对报表所做的所有更改
- 重置对视觉对象所做的所有更改
- 清除最近的更改

> [!IMPORTANT]
> 个性化设置视觉对象的功能必须由报表设计者启用。 如果看不到“个性化设置此视觉对象”![个性化设置此视觉对象图标](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png)图标，则报表设计者不会为当前报表启用此功能。 请与报表所有者或 Power BI 管理员联系以启用该功能。 若要显示报表所有者的联系人信息，请从 Power BI 菜单栏中选择报表的名称。

## <a name="personalize-visuals-in-the-power-bi-service"></a>在 Power BI 服务中个性化设置视觉对象

通过个性化设置视觉对象，你无需离开[报表阅读视图](end-user-reading-view.md)，就能够以多种方式浏览数据。 下面的示例演示了可以根据需要修改可视化效果的不同方式。 

1. 在 Power BI 服务中，以“阅读视图”打开报表。

2. 在视觉对象的菜单栏中，选择“个性化设置此视觉对象”![个性化设置此视觉对象图标](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png)图标。 

### <a name="change-the-visualization-type"></a>更改可视化效果类型

你认为通过堆积柱形图显示数据的效果更佳吗？ 更改可视化效果类型。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="个性化设置视觉对象":::
 
### <a name="swap-out-a-measure-or-dimension"></a>交换度量值或维度
通过选择要替换的字段，然后选择其他字段来替换用于 X 轴的字段。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="个性化设置视觉对象":::
 
### <a name="add-or-remove-a-legend"></a>添加或删除图例
通过添加图例，可以根据类别对视觉对象进行颜色编码。 在此示例中，我们将基于公司名称进行颜色编码。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="个性化设置视觉对象":::

### <a name="change-the-placement-of-fields"></a>更改字段的位置

使用拖放，可以更改字段在同一视觉对象属性中的位置，甚至可以更改在不同的视觉对象属性中的位置。 例如，可以将图例中的字段快速移动到视觉对象的轴上。

:::image type="content" source="media/end-user-personalize-visuals/personalize-drag-and-drop.png" alt-text="个性化设置视觉对象":::

还可以快速对表或矩阵的列重新排序。

:::image type="content" source="media/end-user-personalize-visuals/personalize-reorder-columns.png" alt-text="个性化设置视觉对象":::

### <a name="compare-two-or-more-different-measures"></a>比较两个或多个不同的度量值
使用“+”图标为视觉对象添加多个度量值，以此比较不同度量值的值。 若要删除某个度量值，请选择“更多选项(...)”并选择“删除字段” 。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="个性化设置视觉对象":::

### <a name="change-aggregations"></a>更改聚合
通过更改“个性化设置”窗格中的聚合来更改计算度量值的方式。 选择“更多选项(...)”，然后选择要使用的聚合。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="个性化设置视觉对象":::

### <a name="capture-changes"></a>捕获更改 
使用个人书签捕获你的更改，这样便可返回到经过个性化设置的视图。 选择“书签” > “个人书签”并为书签提供一个名称。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="个性化设置视觉对象":::
 
还可以使书签成为默认视图。

### <a name="share-changes"></a>共享更改 
如果你具有“读取”和“重新共享”权限，共享报表时，你就可以选择包括你所做的更改。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="个性化设置视觉对象":::
 
### <a name="reset-all-your-changes-to-a-report"></a>重置对报表所做的所有更改

从报表画布的右上角，选择“重置为默认值”。 这会删除报表中的所有更改，并将其重新设置为作者上次保存的报表视图。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="个性化设置视觉对象":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>重置对视觉对象所做的所有更改

从视觉对象的菜单栏中，选择“重置此视觉对象”，删除对特定视觉对象所做的所有更改，并将其重新设置为作者上次保存的视觉对象视图。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="个性化设置视觉对象":::
 
### <a name="clear-recent-changes"></a>清除最近的更改

选择橡皮擦图标以清除你自打开“个性化设置”窗格后最近所做的所有更改。  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="个性化设置视觉对象":::

## <a name="limitations"></a>限制

目前，该功能有几个需要注意的限制。

- 对于整个报表或特定视觉对象，可以关闭“个性化设置此视觉对象”。 如果没有用于个性化设置视觉对象的选项，请咨询你的 Power BI 管理员或报表所有者。 若要显示报表所有者的联系人信息，请从 Power BI 菜单栏中选择报表的名称。
- 用户浏览不会自动保留。 需要将视图另存为个人书签，以便捕获所做的更改。
- 适用于 iOS 和 Android 平板电脑的 Power BI 移动应用和 Power BI Windows 应用均支持此功能；适用于手机的 Power BI 移动应用则不支持。 但所有 Power BI 移动应用都将接受在 Power BI 服务的个人书签中保存的任何视觉对象更改。

## <a name="next-steps"></a>后续步骤
[将报表视觉对象复制为静态图像](../visuals/power-bi-visualization-copy-paste.md)    
更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

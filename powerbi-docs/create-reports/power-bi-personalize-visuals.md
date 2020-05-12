---
title: 允许用户在报表中个性化设置视觉对象
description: 允许报表读者创建自己的报表视图，而无需对其进行编辑。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867107"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>允许用户在报表中个性化设置视觉对象

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

当你与广泛用户共享报表时，某些用户可能想要查看特定视觉对象的略有不同的视图。 他们可能想要交换轴上的内容，更改视觉对象类型，或在工具提示中添加一些内容。 很难让一个视觉对象满足每个人的要求。 利用这项新功能，你可以让使用者浏览和个性化设置视觉对象，所有这一切都可在报表阅读视图中实现。 他们可以按所需方式调整视觉对象，并将其另存为书签以供稍后访问。 他们无需具有报表的编辑权限，也无需返回到报表作者进行更改。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="个性化设置视觉对象":::
 
## <a name="what-report-consumers-can-change"></a>报表使用者可以更改的内容

利用此功能，使用者可以通过临时浏览 Power BI 报表上的视觉对象进行深入了解。 此功能非常适合希望启用其报表读者基本浏览方案的报表创建者。 下面是报表读者可以进行的修改：

- 更改可视化效果类型
- 交换度量值或维度
- 添加或删除图例
- 比较两个或多个度量值
- 更改聚合等

此功能不仅允许新的探索功能。 它还包括使用者捕获和共享其更改的方式：

- 捕获他们的更改
- 共享他们的更改
- 重置他们对报表的所有更改
- 重置他们对视觉对象的所有更改
- 清除他们最近的更改

## <a name="turn-on-the-preview-feature"></a>启用预览功能

由于此功能处于预览阶段，因此需要首先打开此功能开关。 转到“文件” > “选项和设置” > 选项”    。 在“全局设置”>“预览功能”中，确保选中“个性化设置视觉对象”    。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="启用“个性化设置视觉对象”":::

可能需要重启 Power BI Desktop 才能在当前文件的“设置”中看到该选项。

## <a name="enable-personalization-in-a-report"></a>启用“在报表中进行个性化设置”

打开预览开关后，需要为希望使用者能够为其个性化设置视觉对象的报表专门启用此开关。

可以在 Power BI Desktop 或 Power BI 服务中启用此功能。

### <a name="in-power-bi-desktop"></a>在 Power BI Desktop 中

若要在 Power BI Desktop 中启用此功能，请转到“文件” > “选项和设置” > “选项” > “当前文件” > “报表设置”      。 确保已启用“个性化设置视觉对象(预览)”  。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="启用“在报表中进行个性化设置”":::

### <a name="in-the-power-bi-service"></a>在 Power BI 服务中

要在 Power BI 服务中启用该功能，请转到报表“设置”  。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Power BI 服务中的报表设置":::

启用“个性化设置视觉对象(预览)” > 选择“保存”   。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="在服务中启用“个性化设置视觉对象”":::

## <a name="select-visuals-that-can-be-personalized"></a>选择可以进行个性化设置的视觉对象

为给定的报表启用此设置时，默认情况下，该报表中的所有视觉对象都可以进行个性化设置。 如果你不希望个性化设置所有视觉对象，可以按视觉对象启用或禁用此设置。

选择视觉对象 > 在“可视化效果”窗格中选择“格式”> 展开“视觉对象标头”    。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="选择视觉对象标头":::
 
滑动“个性化设置视觉对象” >  “开启”或“关闭”    。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="开启或关闭“个性化设置视觉对象”":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>在 Power BI 服务中个性化设置视觉对象

通过个性化设置视觉对象，使用者可以通过多种方式浏览数据，而无需离开报表阅读视图。 下面的示例演示了用户可以根据需要修改可视化效果的不同方式。 

1. 在 Power BI 服务中，以“阅读视图”打开报表。

2. 在视觉对象的右上角，选择“个性化设置此视觉对象” ![个性化设置此视觉对象图标](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png) 图标  。 

### <a name="change-the-visualization-type"></a>更改可视化效果类型

可通过更改“可视化效果类型”  ，查看可视化效果的不同表示形式。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="更改可视化效果类型":::
 
### <a name="swap-out-a-measure-or-dimension"></a>交换度量值或维度
可通过选择要替换的字段，然后选择另一个度量值或维度，来替换 X 轴上的度量值或维度。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="更改轴":::
 
### <a name="add-or-remove-a-legend"></a>添加或删除图例
通过添加图例，可以根据类别对视觉对象进行颜色编码。 可通过清除“个性化设置”窗格中的“图例”框来消除分类颜色编码   。 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="添加或删除图例":::

### <a name="compare-two-or-more-different-measures"></a>比较两个或多个不同的度量值
可使用“+”图标为视觉对象添加多个度量值，以此比较不同度量值的值。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="比较度量值":::

### <a name="change-aggregations"></a>更改聚合
可通过更改“个性化设置”窗格中的聚合来更改计算度量值的方式  。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="更改聚合":::

### <a name="capture-changes"></a>捕获更改 
使用个人书签捕获你的更改，这样便可返回到经过个性化设置的视图。 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="创建书签":::
 
还可以使书签成为默认视图。

### <a name="share-changes"></a>共享更改 
如果你具有“读取”和“重新共享”权限，共享报表时，你就可以选择包括你所做的更改。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="共享更改":::
 
### <a name="reset-all-your-changes-to-a-report"></a>重置对报表所做的所有更改

选择“重置为默认值”，删除报表中的所有更改，并将其重新设置为作者上次保存的报表视图  。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="重置保存所有更改":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>重置对视觉对象所做的所有更改

选择“重置此视觉对象”，删除对特定视觉对象所做的所有更改，并将其重新设置为作者上次保存的视觉对象视图  。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="重置所有视觉对象更改":::
 
### <a name="clear-recent-changes"></a>清除最近的更改

选择橡皮擦图标以清除你自打开“个性化设置”窗格后最近所做的所有更改  。  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="还原最近的更改":::

## <a name="limitations-and-known-issues"></a>限制和已知问题

目前，该功能有几个需要注意的限制。

- 此功能不支持嵌入方案，包括发布到 Web。
- 用户浏览不会自动保留。 需要将视图另存为个人书签，以便捕获所做的更改。
- 在 Power BI 移动应用中时，无法更改视觉对象。 但移动应用中会尊重在 Power BI 服务的个人书签中保存的任何视觉更改。

还存在一些待解决的已知问题：

- 不支持添加层次结构；需要添加单个子项。
- 不能将日期层次结构更改为日期，反之亦然。 
- 对于个人书签，你可能会收到根据你选择的序列略有不同的结果。 由于我们不会捕获报表的完整状态，而只捕获所做的修改，因此可能存在差异。 解决方法是选择“重置为默认值”，然后选择要查看的书签  。 

## <a name="next-steps"></a>后续步骤

尝试体验全新的视觉对象个性化设置。 在 [Power BI Ideas 网站](https://ideas.powerbi.com/forums/265200-power-bi)上，提供有关此功能的反馈，以及如何继续改进它。 

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


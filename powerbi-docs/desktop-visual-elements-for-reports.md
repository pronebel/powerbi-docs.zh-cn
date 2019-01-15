---
title: 使用视觉对象元素增强 Power BI 报表
description: 使用视觉对象元素（如壁纸和视觉对象标头）增强报表
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: bef307678c471303fde7382e3c1be1648d49f0db
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280300"
---
# <a name="use-visual-elements-to-enhance-power-bi-reports"></a>使用视觉对象元素增强 Power BI 报表

在 Power BI Desktop 中，可以使用视觉对象元素（如壁纸和改进的视觉对象标头）来实现可视化效果，进而增强报表外观。

![添加壁纸和小型视觉对象标头来增强报表](media/desktop-visual-elements-for-reports/visual-elements-for-reports_01.png)

从 2018 年 7 月发布的 Power BI Desktop 开始，可以在报表中使用增强功能，使分析和报表比之前更具吸引力。 本文中讨论的增强功能包括： 

* 将壁纸应用到报表，以此背景可以增强或突出显示想要通过数据呈现的情景元素
* 为单独的可视化效果使用改进的视觉对象标头，以便在报表画布上创建完全对齐的视觉对象。 

以下部分介绍如何使用这些增强功能，以及如何将它们应用于报表。

## <a name="using-wallpaper-in-power-bi-reports"></a>在 Power BI 报表中使用壁纸

可以使用壁纸为报表页以外的灰色区域设置格式。 下图有一个箭头，阐明了壁纸区域适用的位置。 

![壁纸覆盖报表周围的灰色区域](media/desktop-visual-elements-for-reports/visual-elements-for-reports_02.png)

可以基于每个报表页设置壁纸，也可以在报表中为每个页面使用相同壁纸。 若要设置壁纸，当报表中未选择任何视觉对象且“壁纸”卡在窗格中显示时，点击或单击“格式”图标。

![“格式”窗格中的“壁纸”区域](media/desktop-visual-elements-for-reports/visual-elements-for-reports_03.png)

可以通过选择“颜色”下拉列表选择要用作“壁纸”的颜色，或者可以选择“添加图像”按钮，选择一张图像用作壁纸。 还可以使用“透明度”滑块向壁纸应用透明度，无论它是颜色还是图像。

最好记住以下有关壁纸的定义：

* 报表区域以外的灰色区域是壁纸区域
* 画布中可以在其中放置视觉对象的区域称为报表页，在“格式窗格”中，可以使用“页面背景”下拉列表进行修改。

报表页始终在前景中（与壁纸相比），而壁纸在其后方，是报表页上最后面的元素。 当在页面上应用透明度时，报表中的视觉对象也会应用透明度，以此让壁纸在背景中通过视觉对象显现出来。

对于所有新报表，默认设置如下：

* 报表页设置为“白色”，其透明度设置为“100%”
* 壁纸设置为“白色”，其透明度设置为“0%”

当页面背景的透明度设置为大于 50%，创建或编辑报表时会出现虚线边框，以显示报表画布边框的边缘。 

![透明度超过 50% 会导致虚线边框](media/desktop-visual-elements-for-reports/visual-elements-for-reports_04.png)

请务必注意，虚线边框仅在编辑报表时显示，而不向查看已发布报表的人员显示，如在 Power BI 服务中查看时。

> [!NOTE]
> 如果对墙纸使用深色背景，并将文本颜色设置为白色或非常浅的颜色，请注意，“导出到 PDF”功能不会导出墙纸，因此导出的白色字体在导出后的 PDF 文件中几乎不可见。 有关导出到 PDF 的详细信息，请参阅[导出到 PDF](desktop-export-to-pdf.md)。


## <a name="using-improved-visual-headers-in-power-bi-reports"></a>使用 Power BI 报表中改进的视觉对象标头

从 2018 年 7 月发布的 Power BI Desktop 开始，显著改进了报表中的视觉对象标头。 主要改进是标头已从视觉对象中分离，因此可以根据首选布局和定位来调整其位置，且标头现在在视觉对象本身中显示，而不是在它的上方浮动。 

默认情况下，标头出现在视觉对象内部，与标题对齐。 在下图中，可以看到视觉对象中的标头（固定图标、展开图标和省略号图标），沿视觉对象标题的相同水平位置右对齐。

![视觉对象标头现在可以驻留在视觉对象中，也可以移动](media/desktop-visual-elements-for-reports/visual-elements-for-reports_05.png)

如果视觉对象没有标题，则标头在视觉对象的上方右对齐浮动，如下图所示。 

![如果没有标题，视觉对象标头在视觉对象的上方浮动](media/desktop-visual-elements-for-reports/visual-elements-for-reports_07.png)

如果视觉对象定位到报表顶部，视觉对象标头则会与视觉对象的底部对齐。 

![当位于报表顶部边框时，视觉对象标头会与底部对齐](media/desktop-visual-elements-for-reports/visual-elements-for-reports_08.png)

此外，每个视觉对象在“可视化效果”窗格的“格式”部分都有一张卡片，称为“视觉对象标头”。 在该卡片中，可以调整视觉对象标头各种类型的特征

![每个视觉对象在“格式”窗格中都有一张视觉对象标头卡](media/desktop-visual-elements-for-reports/visual-elements-for-reports_09.png)

> [!NOTE]
> 创作或编辑报表时，切换可见性不会影响报表。 必须发布报表并在阅读模式下查看它才能看到效果。 此行为确保在编辑过程中在视觉对象标头中提供的许多选项都非常重要，尤其是在编辑时提醒注意问题的警告图标。

对于仅在 Power BI 服务中显示的报表，可以通过转到“我的工作区”>“报表”，然后选择“设置”图标来调整视觉对象标头的使用。 在此处可看到为其选择了“设置”的报表的设置，而且可以从中调整设置，如下图所示。

![Power BI 服务中为使用改进的视觉对象标头的设置](media/desktop-visual-elements-for-reports/visual-elements-for-reports_10.png)

### <a name="enabling-improved-visual-headers-for-existing-reports"></a>为现有报表启用改进的视觉对象标头

新视觉对象标头是所有新报表的默认行为。 对于现有报表，需要在 Power BI Desktop 中启用此行为，方法是转到“文件”>“选项和设置”>“选项”，然后在“报表设置”部分，启用“将新式视觉对象标头与更新后的样式设置选项结合使用”复选框。

![现有报表必须标记“选项”复选框以使用改进的视觉对象标头](media/desktop-visual-elements-for-reports/visual-elements-for-reports_06.png)


## <a name="next-steps"></a>后续步骤
有关 Power BI Desktop 以及如何入门的详细信息，请查看以下文章。

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 的查询概述](desktop-query-overview.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [连接到 Power BI Desktop 中的数据](desktop-connect-to-data.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常见查询任务](desktop-common-query-tasks.md)   


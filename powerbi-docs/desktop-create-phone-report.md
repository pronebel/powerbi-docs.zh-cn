---
title: 针对 Power BI 移动应用优化报表
description: 了解如何通过创建专用于手机和平板电脑的纵向报表版本来优化 Power BI 移动应用的报表页。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 16af5a6c8b5341067c458329c68da0a1a0fe14a5
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2020
ms.locfileid: "74311468"
---
# <a name="optimize-reports-for-the-power-bi-mobile-apps"></a>针对 Power BI 移动应用优化报表
通过创建纵向布局可以改善在移动应用中查看报表的体验。 在 Power BI Desktop 和 Power BI 服务中，可以重新排列报表视觉对象并调整其大小，以便在纵向模式下获得最佳体验。  

正在查找有关在移动设备上查看报表的信息？ 请尝试参阅此快速入门：[浏览 Power BI 移动应用中的仪表板和报表](consumer/mobile/mobile-apps-quickstart-view-dashboard-report.md)。

![更适合在手机上显示的报表](media/desktop-create-phone-report/desktop-create-phone-report-1.png)

你可以创建[响应式视觉对象](#optimize-a-visual-for-any-size)和[响应式切片器](#enhance-slicers-to-work-well-in-phone-reports)，它们可以在任何位置重设大小。 如果向报表添加筛选器，这些筛选器会自动显示在优化的报表中。

## <a name="lay-out-a-portrait-version-of-a-report-page"></a>设计报表页的纵向版本

创建报表后，可以针对手机和平板电脑对其进行优化。

1. 在 Power BI Desktop 中的报表视图的“视图”选项卡上，选择“手机布局”    。  
   
    ![“手机布局”图标](media/desktop-create-phone-report/desktop-create-phone-report-3.png)
   
    在 Power BI 服务中，选择“编辑报表” > “移动布局”   。

    可以看到一个形状类似手机的空白画布。 原始报表页上的所有视觉对象将列在右侧的“可视化效果”窗格中  。

1. 要将视觉对象添加到手机布局中，请将它从“可视化效果”窗格拖动到手机画布中  。
   
    手机报表使用网格布局。 在将视觉对象拖动到移动画布时，它们将与该网格对齐。
   
    ![拖放视觉对象](media/desktop-create-phone-report/desktop-create-phone-report-4.gif)
   
    可以将部分或全部主报表页面视觉对象添加到手机报表页。 你可以每个视觉效果只添加一次，而无需包括所有视觉对象。

1. 就像调整仪表板和移动仪表板上的磁贴一样，你也可以在网格上调整视觉对象大小。
   
   手机报表网格可在不同型号的手机间缩放，因此，报表在小屏幕和大屏幕手机上的效果都很好。
   
   ![重设视觉对象大小](media/desktop-create-phone-report/desktop-create-phone-report-5.gif)

## <a name="optimize-a-visual-for-any-size"></a>将视觉对象优化为适应任意大小
可以将仪表板或报表中的视觉对象设置为“响应式”。  视觉对象大幅度更改以显示最大数量的数据和见解的视觉对象，与屏幕大小无关。 

在视觉对象缩放时，Power BI 会优先确保显示数据视图。 例如，它可以自动删除填充，并将图例移至视觉对象顶部，这样即便视觉对象变小，也仍可提供信息。

![响应式视觉对象重设大小](media/desktop-create-phone-report/desktop-create-phone-report-6.gif)

用户可自行选择是否为每个视觉对象启用响应式设置。 详细了解如何[优化视觉对象](visuals/desktop-create-responsive-visuals.md)。

## <a name="considerations-when-creating-phone-report-layouts"></a>创建手机报表布局时的注意事项
* 对于多页报表，可以优化全部或部分页面。 
* 如果已定义报表页的背景色，则手机报表将具有相同的背景色。
* 无法为特定手机修改格式设置。 主布局和移动布局之间的格式一致。 例如，字体大小是相同的。
* 要更改视觉对象（例如更改其格式、数据集、筛选器或任何其他属性），请返回到常规报表创作模式。
* Power BI 在移动应用中提供手机报表的默认标题和页面名称。 如果你已在报表中创建了标题和页面名称的文本视觉对象，请考虑不将它们添加到手机报表中。     

## <a name="remove-a-visual-from-the-phone-layout"></a>从手机布局中删除视觉对象
* 要删除视觉对象，请选择手机画布上的视觉对象右上角的“X”，或将其选中，然后按“删除”   。
  
   从此次删除视觉对象只会将其从手机布局画布中删除。 视觉对象和原始报表不受影响。
  
   ![删除视觉对象](media/desktop-create-phone-report/desktop-create-phone-report-7.gif)

## <a name="enhance-slicers-to-work-well-in-phone-reports"></a>增强切片器功能，使其在手机报表中正常运行
切片器提供在画布上筛选报表数据的功能。 在常规报表创作模式下设计切片器时，可以修改某些切片器设置以使其在手机报表中更易于使用：

* 确定报表读取器是否仅可以选择一个项或多个项。
* 在切片器周围放置一个框，以使报表更易于扫描。
* 使切片器呈垂直、水平或响应式  。 

如果将切片器设置为响应式，则在改变它大小和形状时，它显示更多或更少的选项。 它可以是调高、调短、调宽或调窄。 如果将其调整得足够小，它将变为报表页上的一个筛选器图标。 

![Power BI 响应式切片器](media/desktop-create-phone-report/desktop-create-phone-report-8.png)

详细了解有关[创建响应式切片器](power-bi-slicer-filter-responsive.md)的信息。

## <a name="publish-a-phone-report"></a>发布手机报表
要发布报表的手机版本，请[将主报表从 Power BI Desktop 发布到 Power BI 服务](desktop-upload-desktop-files.md)，并同时发布手机版本。
  
阅读有关 [Power BI 中的共享和权限](service-how-to-collaborate-distribute-dashboards-reports.md) 的详细信息。

## <a name="view-optimized-and-unoptimized-reports-on-a-phone-or-tablet"></a>在手机或平板电脑上查看优化和未优化的报表
在手机上的移动应用中，Power BI 将自动检测优化和未优化手机报表。 如果存在优化的手机报表，Power BI 手机应用将自动在手机报表模式下打开报表。

如果没有更适合在手机上显示的报表，报表会以未优化的横向视图打开。  

对于手机报表，将手机屏幕方向更改为横向后，无论报表优化与否，都会在包含原始报表布局的未优化视图中打开报表。

如果只优化了某些页，读取器会看到纵向视图中的消息，指示该报表可提供横向视图。

![手机页未优化](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

报表读取器可使手机或平板电脑转向一侧，以查看横向模式页。 详细了解如何[与更适合纵向模式显示的 Power BI 报表进行交互](consumer/mobile/mobile-apps-view-phone-report.md)。

## <a name="next-steps"></a>后续步骤
* [在 Power BI 中创建仪表板电话视图](service-create-dashboard-mobile-phone-view.md)。
* [查看针对你的电话进行优化的 Power BI 报表](consumer/mobile/mobile-apps-view-phone-report.md)。
* [创建优化为适应任意大小的响应式视觉对象](visuals/desktop-create-responsive-visuals.md)。
* 更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)。


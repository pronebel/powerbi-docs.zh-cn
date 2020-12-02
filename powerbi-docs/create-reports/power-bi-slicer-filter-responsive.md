---
title: 在 Power BI 中创建可以重设大小的响应式切片器
description: 了解如何创建可以重设大小以适合你报表的响应式切片器
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 5fde91f2cfabd1f5a7727d3ec8a80d8ecddc7fc6
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393430"
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi"></a>在 Power BI 中创建可以重设大小的响应式切片器

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

重设响应式切片器的大小以适合报表上的任意空间。 你可以将响应式切片器重设为不同的大小和形状，从水平到方形再到垂直均可，切片器中的值可按照你的操作重新排列。 在 Power BI Desktop 和 Power BI 服务中，你可以使水平切片器和日期/范围切片器响应。 日期/范围切片器也具有改进的触摸区域，因此可以用指尖更轻松地对它们进行更改。 可以根据需要变换响应式切片器的大小，它们还会自动重设大小以适应 Power BI 服务以及 Power BI 移动应用中的报表。 

![响应式切片器可以有各种形状](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer.gif)

## <a name="create-a-slicer"></a>创建切片器

创建动态切片器的第一步是创建基本切片器。 

1. 在“可视化效果”窗格中，选择切片器图标![切片器图标](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer-icon.png)。
2. 将要筛选的字段拖动到“字段”  。

    ![将字段添加到切片器](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-1-create.png)

## <a name="convert-to-a-horizontal-slicer"></a>转换为水平切片器

1. 选择切片器后，在“可视化效果”  窗格中选择“格式”  选项卡。
2. 展开“常规”  部分，然后为“方向”  选择“水平”  。

    ![将切片器设置为水平](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-2-horizontal.png) 

1.  你可能想要将其变宽，以显示更多的值。

     ![使切片器更宽](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-3-wider.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>将其设置为响应式并对其进行试验

此步骤很容易。 

1. 在“常规”部分“格式”选项卡中的“方向”下，将“响应”滑动到“打开”。  

    ![切片器现在为响应式](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-4-responsive-on.png)

1. 现在你可以使用它了。 拖动边角可使其变短、变高、变宽及变窄。 如果将其调整得足够小，则它会变为一个筛选器图标。

    ![响应式切片器太小，因此变为一个筛选器图标](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-5-mini-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>将其添加到手机报表布局

在 Power BI Desktop 中，你可以为报表的每个页面创建一个手机布局。 如果页面具有电话布局，则以纵向视图显示在手机上。 否则，你需要在横向视图中查看它。 

1. 在“视图”  菜单中，选择“手机布局”  。

     ![“手机布局”图标，“视图”菜单](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-6-phone-layout-button.png)
    
1. 将手机报表中所需的全部视觉对象拖动到网格中。 当拖动响应式切片器时，请将其设置为所需的大小 - 在这种情况下，所需的是筛选器图标大小。

    ![将切片器添加到手机报表布局](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-7-phone-slicer-icon.png)

阅读有关如何创建[针对 Power BI 手机应用的优化报表](desktop-create-phone-report.md)的详细信息。

## <a name="make-a-time-or-range-slicer-responsive"></a>将时间或范围切片器设置为响应式

你可以按照相同的步骤将时间或范围切片器设置为响应式。 将“响应”  设置为“打开”  之后，请注意下列事项：

- 视觉对象将根据画布允许的尺寸来优化输入框的顺序。 
- 数据元素显示已经过优化，以根据画布允许的尺寸使切片器尽可能地适用。 
- 切片器上新的圆形手柄优化了触摸交互。 
- 当视觉对象变得太小而无法使用时，它将变成一个表示其位置视觉对象类型的图标。 要与其进行交互，只需双击在焦点模式中打开它即可。 这样既可节省报表页面的宝贵空间而又不会丢失功能。

## <a name="next-steps"></a>后续步骤

- [Power BI 服务中的切片器](../visuals/power-bi-visualization-slicers.md)
- 更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
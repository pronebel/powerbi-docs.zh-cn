---
title: 向 Power BI 报表添加可视化效果 - 第 1 部分
description: 向 Power BI 报表添加可视化效果 - 第 1 部分
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b275d4e7fdb4e289d2331a2f58db504071ea609b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758591"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>向 Power BI 报表添加视觉对象（第 1 部分）

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

本文简要介绍如何在报表中创建可视化效果。 它适用于 Power BI 服务和 Power BI Desktop。 有关更高级的内容，请参阅[本系列的第 2 部分](power-bi-report-add-visualizations-ii.md)。 请观看 Amanda 的视频演示，她将介绍如何在报表画布上创建、编辑视觉对象并对其进行格式设置的一些不同方法。 然后使用[销售和市场营销示例](../sample-datasets.md)来创建自己的报表并进行体验。

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>先决条件

本教程使用[销售和市场营销 PBIX 文件](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix)。

1. 在 Power BI Desktop 菜单栏的左上部分，选择“文件” > “打开”  
   
2. 查找“销售和市场营销示例 PBIX 文件”的副本 

1. 在报表视图 ![报表视图图标的屏幕截图。](media/power-bi-visualization-kpi/power-bi-report-view.png) 中，打开“销售和市场营销示例 PBIX 文件”  。

1. 选择 ![黄色选项卡的屏幕截图。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) ，以添加新报表页。

## <a name="add-visualizations-to-the-report"></a>将可视化效果添加到报表

1. 通过从“字段”窗格中选择字段来创建可视化效果。 

    从数值字段入手，如“销售额” > “总销售额”   。 Power BI 将创建一个包含单个柱形的柱形图。

    ![包含一个柱形的柱形图的屏幕截图。](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    也可以从分类字段入手，如“名称”  或“产品”  。 Power BI 会创建表，并将相应字段添加到“值”  井中。

    ![具有四个类别的表的屏幕截图](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    也可以从地理位置字段入手，如“地理位置”   > “城市”  。 Power BI 会结合必应地图创建地图可视化效果。

    ![地图可视化效果的屏幕截图。](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>更改可视化效果类型

 创建可视化效果，然后更改其类型。 
 
 1. 依次选择“产品”   > “类别”  ，再依次选择“产品”   > “产品数”  ，以将它们添加到“值”  井中。

    ![突出显示“值”井的“字段”窗格屏幕截图。](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. 选择“堆积柱形图”  图标，将可视化效果更改为柱形图。

   ![突出显示“堆积柱形图”图标的“可视化效果”窗格屏幕截图。](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. 若要更改视觉对象的排序方式，请选择“更多操作”(…)  。使用排序选项更改排序方向（升序或降序），并更改用于排序的列（排序依据）  。

   ![“更多操作”下拉列表的屏幕截图。](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>后续步骤

 继续学习：

* [第 2 部分：向 Power BI 报表添加可视化效果](power-bi-report-add-visualizations-ii.md)

* 在报表中[与可视化效果交互](../consumer/end-user-reading-view.md)。


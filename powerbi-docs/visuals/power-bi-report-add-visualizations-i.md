---
title: 向 Power BI 报表添加可视化效果 - 第 1 部分
description: 向 Power BI 报表添加可视化效果 - 第 1 部分
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299243"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>向 Power BI 报表添加可视化效果 - 第 1 部分

本文简要介绍如何在报表中创建可视化效果。 它适用于 Power BI 服务和 Power BI Desktop。 有关更高级的内容，请参阅[本系列的第 2 部分](power-bi-report-add-visualizations-ii.md)。 请观看 Amanda 的视频演示，她将介绍如何在报表画布上创建、编辑视觉对象并对其进行格式设置的一些不同方法。 然后使用[销售和市场营销示例](../sample-datasets.md)来创建自己的报表并进行体验。

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>打开报表并添加新页面

1. [在“编辑视图”中打开报表](../service-interact-with-a-report-in-editing-view.md)。

    本教程使用“[销售和市场营销示例](../sample-datasets.md)”。

1. 如果看不到“字段”  窗格，请选择箭头图标来打开它。

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. 向报表添加空白页。

## <a name="add-visualizations-to-the-report"></a>将可视化效果添加到报表

1. 通过从“字段”窗格中选择字段来创建可视化效果。 

    从数值字段入手，如“销售事实”   > “销售额($)”  。 Power BI 将创建一个包含单个柱形的柱形图。

    ![包含一个柱形的柱形图的屏幕截图。](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    也可以从分类字段入手，如“名称”  或“产品”  。 Power BI 会创建表，并将相应字段添加到“值”  井中。

    ![依次选择“产品”和“类别”来创建表的 GIF。](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    也可以从地理位置字段入手，如“地理位置”   > “城市”  。 Power BI 会结合必应地图创建地图可视化效果。

    ![地图可视化效果的屏幕截图。](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. 创建可视化效果，然后更改其类型。 依次选择“产品”   > “类别”  ，再依次选择“产品”   > “产品数”  ，以将它们添加到“值”  井中。

   ![突出显示“值”井的“字段”窗格屏幕截图。](media/power-bi-report-add-visualizations-i/part1table1.png)

1. 选择“堆积柱形图”  图标，将可视化效果更改为柱形图。

   ![突出显示“堆积柱形图”图标的“可视化效果”窗格屏幕截图。](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. 在报表中创建可视化效果时，可以[将其固定到仪表板](../service-dashboard-pin-tile-from-report.md)。 若要固定可视化效果，请选择固定图标 ![固定图标的屏幕截图。](media/power-bi-report-add-visualizations-i/pinnooutline.png)。

   ![突出显示固定图标的柱形图可视化效果屏幕截图。](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>后续步骤

 继续学习：

* [第 2 部分：向 Power BI 报表添加可视化效果](power-bi-report-add-visualizations-ii.md)

* 在报表中[与可视化效果交互](../consumer/end-user-reading-view.md)。

* [对可视化效果执行更多操作](power-bi-report-visualizations.md)。

* [保存报表](../service-report-save.md)。

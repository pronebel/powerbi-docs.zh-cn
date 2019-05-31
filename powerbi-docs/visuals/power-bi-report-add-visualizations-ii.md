---
title: 第 2 部分，向 Power BI 报表添加可视化效果
description: 第 2 部分，向 Power BI 报表添加可视化效果
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c42d96fea37a6309908dd357425c3d0504e18397
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61410042"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>第 2 部分，向 Power BI 报表添加可视化效果
在[第 1 部分](power-bi-report-add-visualizations-ii.md)中，通过选中字段名称旁边的复选框来创建基本可视化对象。  在第 2 部分中，你将了解如何使用拖放功能并充分利用“字段”  和“可视化对象”  窗格创建和修改可视化对象。

### <a name="prerequisites"></a>先决条件
- [第 1 部分](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop - 可使用 Power BI 服务或 Power BI Desktop 将可视化效果添加到报表。 本教程使用 Power BI Desktop。 
- [零售分析示例](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>创建新的可视化对象
在本教程中，我们将深入探讨我们的零售分析数据集并创建几个关键的可视化对象。

### <a name="open-a-report-and-add-a-new-blank-page"></a>打开报表并添加新的空白页。
1. 打开 Power BI Desktop 中的零售分析示例 .PBIX 文件。 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2. 选择画布底部的黄色加号图标，以添加新页面。

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>添加查看本年度销售额（与上一年相比）的可视化对象。
1. 从“销售额”  表中，选择“本年度销售额”   > **值**和“去年销售额”  。 Power BI 将创建柱形图。  这挺有趣的，你可能想要深入了解。 每月销售额看上去如何？  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. 从“时间”表中，将“会计月”  拖动到“轴”  区域。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [将可视化对象更改](power-bi-report-change-visualization-type.md)为“区域”图表。  有许多可视化类型可供选择 - 请参阅[每种类型的描述、最佳做法提示和教程](power-bi-visualization-types-for-reports-and-q-and-a.md)，获取类型选择相关帮助。 从“可视化对象”窗格中，选择区域图表图标 ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png)。
4. 选择省略号，然后选择“按会计月进行排序”  ，对视觉对象排序。
5. [调整可视化对象的大小](power-bi-visualization-move-and-resize.md)，方法是选择可视化对象，抓取其中一个边框圈并进行拖动。 使其宽度足以消除滚动条，同时足够小，从而使我们有足够的空间来添加其他可视化对象。
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [保存报表](../service-report-save.md)。

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>添加按位置查看销售额的地图可视化对象
1. 从“商店”  表中，选择“区域”  。 Power BI 识别出 Territory 是一个位置，并创建地图可视化对象。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. 将“总商店数”  拖动至“大小”区域。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. 添加图例。  若要按商店名称查看数据，将  “连锁店”拖动到“图例”区域。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>后续步骤
* [Power BI 报表中的可视化对象](power-bi-report-visualizations.md)的详细信息。  
* 更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


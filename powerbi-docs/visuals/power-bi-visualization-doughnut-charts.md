---
title: Power BI 中的圆环图
description: Power BI 中的圆环图
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5720e52b61332aeca82d0b23b776f590634e622f
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829610"
---
# <a name="doughnut-charts-in-power-bi"></a>Power BI 中的圆环图
圆环图类似于饼图，因为它显示部分与整体的关系。 唯一的区别是中心为空，因而有空间可用于标签或图标。

## <a name="create-a-doughnut-chart"></a>创建圆环图
这些说明使用零售分析示例创建一个按类别显示本年度销售额的圆环图。 若要继续学习，请[下载示例](../sample-datasets.md)（适用于 Power BI 服务或 Power BI Desktop）。

1. 从空白报表页入手。 如果使用的是 Power BI 服务，请确保在 [“编辑视图”](../service-interact-with-a-report-in-editing-view.md) 中打开报表。

2. 在“字段”窗格中，选择“销售额”\>“去年销售额”。  
   
3. 从可视化对象窗格中，选择圆环图的图标![圆环图图标](media/power-bi-visualization-doughnut-charts/power-bi-icon.png)，将条形图转换为圆环图。 如果“去年销售额”不在“值”区域中，请将它拖动到其中。
     
   ![包含所选圆环图的可视化效果窗格](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. 依次选择“**项**”\>“**类别**”，将其添加到**图例**区域中。 
     
    ![字段窗格旁边的圆环图](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. （可选）[调整大小和图表文本的颜色](power-bi-visualization-customize-title-background-and-legend.md)。 

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
* 圆环图值的总和相加必须达到 100%。
* 类别太多会难以查看和解释。
* 圆环图最适用于将特定部分与整体进行比较，而不是将各个部分相互比较。 

## <a name="next-steps"></a>后续步骤
[Power BI 中的漏斗图](power-bi-visualization-funnel-charts.md)

[Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)



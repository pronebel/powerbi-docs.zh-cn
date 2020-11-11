---
title: Power BI 中的折线图
description: Power BI 中的折线图
author: msftrien
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: acbd6e40a351885b8644aca48edf41db81462864
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2020
ms.locfileid: "93411972"
---
# <a name="line-charts-in-power-bi"></a>Power BI 中的折线图

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

折线图是一系列用点表示并用直线连接的数据点。 折线图可能会有一条或多条折线。 折线图有 X 轴和 Y 轴。 

![简单折线图](media/power-bi-line-charts/power-bi-line.png)



## <a name="create-a-line-chart"></a>创建折线图
下面的说明使用“销售和市场营销示例”应用，以创建按类别显示今年销售额的折线图。 若要跟着本教程一起操作，请从 appsource.com 获取示例应用。

> [!NOTE]
> 与 Power BI 同事共享报表时，你和这位同事都应具有独立的 Power BI Pro 许可证，并且应将报表保存在 Premium 容量中。

1. 从空白报表页入手。 如果使用的是 Power BI 服务，请务必在[编辑视图](../create-reports/service-interact-with-a-report-in-editing-view.md)中打开报表。

2. 在“字段”窗格中，依次选择“SalesFact”  \>“Total units”  ，再依次选择“Date”   > “Month”  。  此时，Power BI 在报表画布上创建柱形图。

    ![在“字段”窗格中进行选择](media/power-bi-line-charts/power-bi-step1.png)

4. 选择“可视化效果”窗格中的“折线图”模板，将视觉对象转换为折线图。 

    ![转换为折线图](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. 将折线图筛选为仅显示 2012 年 - 2014 年的数据。 如果“筛选器”窗格处于折叠状态，立即展开它。 在“字段”窗格中，依次选择“Date”  \>“Year”  ，并将它拖到“筛选器”窗格中。 将它放在“此视觉对象中的筛选器”  标题下。 
     
    ![“字段”窗格旁边的折线图](media/power-bi-line-charts/power-bi-year-filter.png)

    将“高级筛选器”  更改为“基本筛选器”  ，并选中“2012 年”  、“2013 年”  和“2014 年”  。

    ![“年份”筛选器](media/power-bi-line-charts/power-bi-filter-year.png)

6. （可选）[调整大小和图表文本的颜色](power-bi-visualization-customize-title-background-and-legend.md)。 

    ![增加字体大小并更改 Y 轴字体](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>向折线图添加其他折线
折线图可以有许多不同的折线。 而且，在某些情况下，折线上的值可能会高度相异，导致不能很好地一起显示。 接下来，将先介绍如何在当前折线图中添加其他折线，再介绍如何在折线所代表的值高度相异时设置图表的格式。 

### <a name="add-additional-lines"></a>添加其他折线
我们将按区域拆分总单位数，而不是将所有区域的总单位数视为折线图上的一条折线。 添加其他折线，具体方法是依次转到“地理位置”   > “区域”  ，并将“区域”拖到“图例”井中。

   ![每个区域对应一条折线](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>使用两个 Y 轴
若要在同一折线图上研究总销售额和总单位数，该怎么办？ 销售额数字远高于单位数数字，导致折线图无法使用。 事实上，总单位数对应的红色折线似乎为零。

   ![屏幕截图展示了如何使用单个 y 轴将总单位数显示为基本上是平面的，并与销售数字进行无用的比较。](media/power-bi-line-charts/power-bi-diverging.png)

若要在一个图表上显示高度相异值，请使用组合图。 有关组合图的所有信息，可以阅读 [Power BI 中的组合图](power-bi-visualization-combo-chart.md)。 在下面的示例中，可以通过添加第二个 Y 轴，在一个组合图上同时显示销售额和总单位数。 

   ![屏幕截图展示了销售额值的条形图，左侧为 y 轴，右侧为总单位数与 y 轴的直线。](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="highlighting-and-cross-filtering"></a>突出显示和交叉筛选
有关使用筛选器窗格的信息，请参阅[向报表添加筛选器](../create-reports/power-bi-report-add-filter.md)。

选择折线图上的数据点可交叉突出显示和交叉筛选报表页上的其他可视化效果，反之亦然。 若要跟着本教程一起操作，请打开“市场占有率”  选项卡。  

在折线图上，一个数据点是 X 轴和 Y 轴上值的交点。 在你选择数据点后，Power BI 会添加标记，以指明哪个点（对于一条折线）或哪些点（如果有两条或更多条折线）是报表页上其他视觉对象的交叉突出显示和交叉筛选来源。 如果视觉对象非常密集，Power BI 会选择最靠近你在视觉对象上单击位置的点。

在此示例中，我们选择的数据点包含以下值：在 2014 年 7 月，单位数市场占有率 R12 为 33.16%，单位数市场占有率为 34.74%。

![选择折线图上的一个数据点](media/power-bi-line-charts/power-bi-single-select.png)

请注意柱形图是如何交叉突出显示的，仪表是如何交叉筛选的。

若要管理图表相互交叉突出显示和交叉筛选的方式，请参阅 [Visualization interactions in a Power BI report（Power BI 报表中的可视化效果交互）](../create-reports/service-reports-visual-interactions.md)

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
* 一个折线图不能有两个 Y 轴。  必须改用组合图。
* 在上面的示例中，图表的格式设置为，增加字体大小、更改字体颜色、添加坐标轴标题、居中对齐图表标题和图例、让两个坐标轴从零开始等。 “格式设置”窗格（“滚动油漆刷”图标）有一组似乎无穷无尽的选项，可以让图表按照你希望的方式显示。 最佳学习方式是，打开“格式设置”窗格并进行探索。

## <a name="next-steps"></a>后续步骤

[Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)






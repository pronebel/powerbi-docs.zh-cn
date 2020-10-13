---
title: 在 Power BI 中使用功能区图表
description: 在 Power BI Desktop 中创建和使用功能区图表
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 0e5687f9bb3f27af7bdfee28cd9753fbda4fa44f
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635760"
---
# <a name="create-ribbon-charts-in-power-bi"></a>在 Power BI 中创建功能区图表

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

可创建功能区图表来直观显示数据，并快速发现哪个数据类别具有最高排名（最大值）。 功能区图表能够高效地显示排名变化，并且会在每个时间段内始终将最高排名（值）显示在最顶部。 

![屏幕截图展示了功能区图表，其中包含按年份和季度显示的“Audio”、“Cell phones”和其他类别的数据。](media/desktop-ribbon-charts/ribbon-charts-01.png)

> [!NOTE]
> 与 Power BI 同事共享报表时，你和这位同事都应具有独立的 Power BI Pro 许可证，并且应将报表保存在 Premium 容量中。 请参阅[共享报表](../collaborate-share/service-share-reports.md)。

## <a name="prerequisites"></a>先决条件

本教程使用[零售分析示例 PBIX 文件](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)。

1. 在菜单栏的左上方，选择“文件” > “打开” 
   
2. 查找**零售分析示例 PBIX 文件**的副本

1. 在报表视图中打开**零售分析示例 PBIX 文件**![报表视图屏幕截图图标](media/power-bi-visualization-kpi/power-bi-report-view.png)。

1. 选择 ![黄色选项卡的屏幕截图。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) ，以添加新报表页。

## <a name="create-a-ribbon-chart"></a>创建功能区图表

1. 若要创建功能区图表，请在“可视化效果”面板中选择“功能区图表”。

    ![可视化效果模板](media/desktop-ribbon-charts/power-bi-template.png)

    功能区图表使用功能区在可视化时间连续区间内连接一个数据类别，从而使你可以看到某个给定的类别在图表的 x 轴（通常是时间线）范围内是如何排名的。

2. 选择“轴”“图例”和“值”的字段。  在此示例中，我们选择了：“商店” > “开店日期”，“产品” > “类别”，以及“销售额” > “本年度销售额” > “值”      。  

    ![已选择字段](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    由于数据集仅包含一年的数据，因此我们还从“轴”中删除了“年份”和“季度”字段  。

3. 功能区图表显示每个月份的排名。 请注意排名如何随时间推移而变化。 例如，从 2 月到 3 月，主页类别从第二个移动到第五个。

    ![屏幕截图展示了你创建的功能区图表，并突出显示了其中的一些数据。](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>设置功能区图表格式
在创建功能区图表时，可以在“可视化效果”窗格的“格式”部分使用格式设置选项。 功能区图表的格式设置选项类似于堆叠柱状图中的相应选项，只不过它还具有特定于功能区的其他格式设置选项。

![屏幕截图展示了选择了格式图标并展开了“功能区”区域。](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

功能区图表的这些格式设置选项可让你进行调整。

* “间距”可调整功能区之间的间隔大小。 数值为列的最大高度的百分比。
* “匹配系列颜色”可以将功能区的颜色与系列颜色进行匹配。 设置为关闭时，功能区为灰色。
* “透明度”指定功能区的透明度，默认设置为 30。
* “边框”可以在功能区的顶部和底部使用深色边框。 默认情况下，边框为关闭状态。

由于功能区图表没有 y 轴标签，因此可能要添加数据标签。 从格式设置窗格，选择“数据标签”。 

![数据标签的格式设置选项](media/desktop-ribbon-charts/power-bi-labels.png)

设置数据标签的格式设置选项。 在此示例中，我们将文本颜色设置为白色，并将显示单位设置为千。

![屏幕截图展示了你的最终格式化功能区图表。](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>后续步骤

[Power BI 中的散点图和气泡图](power-bi-visualization-scatter.md)

[Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)

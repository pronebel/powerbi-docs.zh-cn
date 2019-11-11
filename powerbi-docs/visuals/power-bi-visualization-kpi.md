---
title: 关键绩效指标 (KPI) 视觉对象
description: 在 Power BI 中创建关键绩效指标 (KPI) 视觉对象
author: mihart
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 42a9f2c641a0cdac9b7a129ffc5ecc6f7fb8cf8d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870874"
---
# <a name="key-performance-indicator-kpi-visuals"></a>关键绩效指标 (KPI) 视觉对象

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

关键绩效指标 (KPI) 是一个视觉提示，用于传达针对可度量目标已完成的进度。 若要详细了解 KPI，请参阅 [PowerPivot 中的关键绩效指标 (KPI)](/previous-versions/sql/sql-server-2012/hh272050(v=sql.110))。

请观看下面的视频，Will 在其中介绍了如何创建各个指标视觉对象：仪表、卡片和 KPI。
   > [!NOTE]
   > 此视频使用较旧版本的 Power BI Desktop。
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-kpi"></a>何时使用 KPI

当存在以下情况时，KPI 是一个不错的选择：

* 若要度量进度。 回答问题：“我是领先还是落后？”

* 若要度量与目标的距离。 回答问题：“我领先或落后了多远？”

## <a name="kpi-requirements"></a>KPI 要求

设计人员将 KPI 视觉对象建立在特定度量值的基础上。 KPI 旨在根据已定义目标来评估指标的当前值和状态。 KPI 视觉对象需要用于评估值的基础  度量值、目标  度量值或值，以及阈值  或目标  。

KPI 数据集需要包含 KPI 目标值。 如果数据集不包含目标值，你可以创建它们，具体方法是向数据模型或 PBIX 文件添加含目标的 Excel 工作表。

## <a name="prerequisites"></a>先决条件

本教程使用[零售分析示例 PBIX 文件](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)。

1. 在菜单栏的左上方，选择“文件” > “打开”  

1. 查找**零售分析示例 PBIX 文件**的副本

1. 在报表视图中打开“零售分析示例 PBIX 文件”  。 ![报表视图图标的屏幕截图。](media/power-bi-visualization-kpi/power-bi-report-view.png)

1. 选择 + 来添加新页面  。 ![黄色选项卡的屏幕截图。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png)

## <a name="how-to-create-a-kpi"></a>如何创建 KPI

此示例将创建一个 KPI，用于度量在实现销售目标方面的进度。

1. 在“字段”  窗格中，依次选择“销售额”>“今年总销售单位数”  。  此值为指标。

1. 添加“时间”>“财政月”  。  此值表示趋势。

1. 选择视觉对象右上角的省略号，并检查 Power BI 是否按“会计月份”  升序排序柱形。

    > [!IMPORTANT]
    > 将可视化效果转换为 KPI 后，便无  排序选项。 必须现在进行正确排序。

    ![同时选择了“升序排序”和“会计月份”的已展开省略号菜单的屏幕截图。](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    正确排序后，视觉对象如下所示：

    ![正确排序的视觉对象的屏幕截图。](media/power-bi-visualization-kpi/power-bi-chart.png)

1. 选择“可视化效果”  窗格中的“KPI”  图标，将视觉对象转换为 KPI。

    ![突出显示“KPI”的“可视化效果”窗格屏幕截图。](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. 若要添加目标，请将“去年总销售单位数”  拖到“目标”  字段中。

    ![已完成 KPI 视觉对象和包含描述值的“字段”窗格的屏幕截图。](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. 你也可以根据需要选择滚动油漆刷图标打开“格式”窗格来设置 KPI 格式。

    * **指标** - 控制指标的显示单位和小数位数。

    * **趋势轴** - 如果设置为“开”  ，视觉对象将趋势轴显示为 KPI 视觉对象的背景。  

    * **目标** - 如果设置为“开”  ，视觉对象显示目标，以及与目标的距离百分比。

    * **颜色编码 > 方向** - 人们认为一些 KPI 值越高越好  ，而另一些 KPI 值则越低越好  。 例如，收入与等待时间。 通常更高的收入值好于更高的等待时间值。 选择“越高越好”  ，并视需要更改颜色设置。

KPI 也适用于 Power BI 服务和移动设备。 这样，可以始终连接到业务检测信号。

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

如果 KPI 并非如上所示，可能是因为你未按“会计月份”  进行排序。 KPI 没有排序选项。 必须重新开始，并先按“会计月份”  排序，再  将可视化效果转换为 KPI。

## <a name="next-steps"></a>后续步骤

* [关于 Power BI 地图可视化效果的提示和技巧](power-bi-map-tips-and-tricks.md)

* [Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

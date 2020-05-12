---
title: Power BI 中的树状图
description: Power BI 中的树状图
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 189cc784577df277b0b0517253699ae06842b30c
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866877"
---
# <a name="treemaps-in-power-bi"></a>Power BI 中的树状图

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

树状图将分层数据显示为一组嵌套矩形。 层次结构中的每个级别都由一个有色矩形（分支）表示，其中包含更小的矩形（叶）。 Power BI 根据度量值来确定每个矩形内的空间大小。 矩形按大小从左上方（最大）到右下方（最小）排列。

![“产品数(按类别和制造商)”树状图的屏幕截图。](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

例如，若要分析销售情况，可能有服装类别作为顶级分支：城市  、乡村  、青年  和混合  。 Power BI 会将类别矩形拆分为叶（即服装类别内的服装制造商）。 这些叶根据销售量确定大小和底纹。

在上面的“城市”  分支中，销售了许多“VanArsdel”  服装。 销售的“Natura”  和“Fama”  服装较少。 “Leo”  服装仅销售了几件。 因此，在树状图的“城市”  分支中：

* “VanArsdel”  的矩形最大，位于左上角。

* “Natura”  和“Fama”  的矩形略小。

* 有其他许多矩形，代表已销售的其他所有服装。

* “Leo”  的矩形很小。

通过比较每个叶节点的大小和底纹，可以跨其他服装类别比较销量：矩形越大，颜色越深，值就越大。


## <a name="when-to-use-a-treemap"></a>何时使用树状图

当存在以下情况时，树状图是一个不错的选择：

* 若要显示大量的分层数据。

* 如果条形图无法有效处理大量值。

* 若要显示每个部分与整体之间的比例。

* 若要跨层次结构中的每个类别级别显示度量值的分布模式。

* 若要使用大小和颜色编码来显示属性。

* 若要发现模式、离群值、最重要影响因素和异常。

## <a name="prerequisite"></a>先决条件

本教程使用[零售分析示例 PBIX 文件](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)。

1. 在菜单栏的左上方，选择“文件” > “打开”  
   
2. 查找**零售分析示例 PBIX 文件**的副本

1. 在报表视图中打开**零售分析示例 PBIX 文件**![报表视图屏幕截图图标](media/power-bi-visualization-kpi/power-bi-report-view.png)。

1. 选择 ![黄色选项卡的屏幕截图。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) ，以添加新报表页。

> [!NOTE]
> 与 Power BI 同事共享报表时，你和这位同事都应具有独立的 Power BI Pro 许可证，并且应将报表保存在 Premium 容量中。    



获取“零售分析示例”  数据集后，可以开始操作了。

## <a name="create-a-basic-treemap"></a>创建一个基本的树状图

你将创建报表，并添加基本树状图。


1. 在“字段”  窗格中，依次选择“销售额”   > “去年销售额”  度量值。

   ![依次选择“销售额”>“去年销售额”和生成的视觉对象的屏幕截图。](media/power-bi-visualization-treemaps/treemapfirstvalue-new.png)

1. 选择“树状图”图标 ![“树状图”图标的屏幕截图](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) ，以将图表转换为树状图。

   ![不含配置的树状图的屏幕截图。](media/power-bi-visualization-treemaps/treemapconvertto-new.png)

1. 选择“项目” > “类别”，这会将“类别”添加到“组”井中     。

    Power BI 将创建一个树状图，其中矩形的大小基于总销售额，颜色代表类别。 实际上你已创建以可视化方式描述按类别的总销售额的相对大小的层次结构。 “男装”  类的销售额最高，“袜”  类销售额最低。

    ![已配置的树状图的屏幕截图。](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. 选择“商店” > “连锁店”，这会将“连锁店”添加到“详细信息”井中以完成树状图     。 现在你可以按类别和连锁店比较上年度的销售额。

   ![将“商店”>“连锁店”添加到“详细信息”的树状图的屏幕截图。](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > 不能同时使用色彩饱和度和详细信息。

1. 将鼠标悬停在**连锁店**区域上方以显示**类别**中该部分的工具提示。

    例如，将鼠标悬停在“090-家居”  矩形中的 Fashions Direct  ，将显示家居类别 Fashions Direct 部分的工具提示。

   ![显示的“主页”工具提示的屏幕截图。](media/power-bi-visualization-treemaps/treemaphoverdetail-new.png)


## <a name="highlighting-and-cross-filtering"></a>突出显示和交叉筛选

突出显示树状图中的一个**类别**或**详细信息**，以交叉突出显示和交叉筛选报表页上的其他可视化效果。 若要跟着本教程一起操作，请向此报表页添加一些视觉对象，或将树状图复制到此报表的其他一个报表页中。 下图中的树状图已复制到**概述**页。 

1. 在树状图中，选择“类别”  或“类别”  中的“连锁店”  。 这会交叉突出显示报表页上的其他可视化效果。 例如，选择“050-Shoes”会显示去年的鞋子销售额为 **$16,352,432**，其中“Fashions Direct”贡献了 **$2,174,185** 的销售额   。

   ![展示交叉突出显示的“商店销售情况概览”报表的屏幕截图。](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. 在按连锁店的上年度销售额  饼图中，选择“Fashions Direct”  切片，交叉筛选树状图。
   ![交叉筛选功能的 GIF 演示。](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. 若要管理图表如何相互交叉突出显示和交叉筛选，请参阅[更改 Power BI 报表中视觉对象的交互方式](../service-reports-visual-interactions.md)。

## <a name="next-steps"></a>后续步骤

* [Power BI 中的瀑布图](power-bi-visualization-waterfall-charts.md)

* [Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)

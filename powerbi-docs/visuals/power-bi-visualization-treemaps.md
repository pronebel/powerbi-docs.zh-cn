---
title: Power BI 中的树状图
description: Power BI 中的树状图
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: dd7360761cc78aed9b01eb99165de9f0b4b91ffe
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54274757"
---
# <a name="treemaps-in-power-bi"></a>Power BI 中的树状图
树状图将分层数据显示为一组嵌套矩形。  一个有色矩形（通常称为“分支”）代表层次结构中的一个级别，该矩形包含其他矩形（“叶”）。  根据要度量的值分配每个矩形内部的空间。 矩形从左上方（最大）到右下方（最小）按大小排列。

![](media/power-bi-visualization-treemaps/pbi-nancy_viz_treemap.png)

例如，如果我正在分析销量，我可能会为服装类别设置顶层矩形（又名分支）：城市、乡村、青年和混合。  我的类别矩形将根据所属类别的服装制造商拆分成更小的矩形（又名叶子）。 这些小矩形将根据销售的数量确定大小和明暗度。  

在上述的城市分支中，销售了许多 `Maximus` 服装，少量的 `Natura` 和 `Fama` 以及几个 `Leo`。  因此，我的树状图的城市分支将会呈现为：
* 针对 `Maximus` 的最大矩形位于左上角
* 针对 `Natura` 和 `Fama` 的较小矩形
* 针对所有其他服装销量的许多其他矩形 
* 针对 `Leo` 的小矩形。  

通过比较每个叶子节点的大小和明暗度，我可以比较其他服装类别销售的货品量；矩形越大，颜色越深，值会越大。

## <a name="when-to-use-a-treemap"></a>何时使用树状图
当存在以下情况时，树状图是一个不错的选择：

* 要显示大量的分层数据。
* 条形图不能有效地处理大量值。
* 要显示每个部分与整体之间的比例。
* 要显示层次结构中指标在各个类别层次的分布的模式。
* 要使用大小和颜色编码显示属性。
* 要发现模式、离群值、最重要因素和异常。

### <a name="prerequisites"></a>先决条件
 - Power BI 服务或 Power BI Desktop
 - 零售分析示例

## <a name="create-a-basic-treemap"></a>创建一个基本的树状图
想要先观看别人创建一个树状图？  跳到此视频的 2:10 处观看 Amanda 创建一个树状图。

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

或者，创建你自己的树状图。 以下说明使用零售分析示例。 若要按照介绍进行操作，请登录 Power BI 服务，并依次选择“获取数据”\>“示例”\>“零售分析示例”\>“连接”\>“转至仪表板”。 在报表中创建可视化效果需要对数据集和报表拥有编辑权限。 幸运的是，Power BI 示例是可以编辑的。 但是无法向某人已与你共享的报表添加可视化效果。  

1. 选择“总商店数”磁贴，打开“零售分析示例”报表。    
2. 打开[编辑视图](../service-interact-with-a-report-in-editing-view.md)并选择“销售” > “上年度销售额”指标。   
   ![](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)   
3. 将图表转换为树状图。  
   ![](media/power-bi-visualization-treemaps/treemapconvertto_new.png)   
4. 将**项目**  >  **类别**拖放到**组**中。 Power BI 将创建一个树状图，其中矩形的大小基于总销售额，颜色代表类别。  实际上你已创建以可视化方式描述按类别的总销售额的相对大小的层次结构。  “男装”类的销售额最高，“袜”类销售额最低。   
   ![](media/power-bi-visualization-treemaps/power-bi-complete.png)   
5. 将“商店”  >  “连锁店”拖放到“详细信息”以完成树状图。 现在你可以按类别和连锁店比较上年度的销售额。   
   ![](media/power-bi-visualization-treemaps/power-bi-details.png)
   
   > [!NOTE]
   > 不能同时使用色彩饱和度和详细信息。
   > 
   > 
5. 将鼠标悬停在**连锁店**区域上方以显示**类别**中该部分的工具提示。  例如，将鼠标悬停在“090-家居”矩形中的 Fashions Direct，将显示家居类别 Fashions Direct 部分的工具提示。  
   ![](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)
6. [将树状图添加为仪表板磁贴（固定视觉对象）](../service-dashboard-tiles.md)。 
7. [保存报表](../service-report-save.md)。

## <a name="highlighting-and-cross-filtering"></a>突出显示和交叉筛选
有关使用筛选器窗格的信息，请参阅[向报表添加筛选器](../power-bi-report-add-filter.md)。

突出显示树状图中的一个类别或详细信息，可以交叉突出显示和交叉筛选报表页上的其他可视化效果，反之亦然。 若要按照介绍进行操作，请在此报表页中添加一些视觉对象，或者将树状图复制到此报表中的一个其他非空白页中。

1. 在树状图中，选择一个类别或类别中的一个连锁店。  这样可以交叉突出显示页面上的其他可视化效果。 例如，选择 **050-Shoes** 可显示鞋子的上年度销售额为 $3,640,471，其中 $2,174,185 来自 Fashions Direct。  
   ![](media/power-bi-visualization-treemaps/treemaphiliting.png)

2. 在按连锁店的上年度销售额饼图中，选择“Fashions Direct”切片，交叉筛选树状图。  
   ![](media/power-bi-visualization-treemaps/treemapnoowl.gif)    

3. 若要管理图表相互交叉突出显示和交叉筛选的方式，请参阅 [Visualization interactions in a Power BI report（Power BI 报表中的可视化效果交互）](../service-reports-visual-interactions.md)

## <a name="next-steps"></a>后续步骤

[Power BI 中的瀑布图](power-bi-visualization-waterfall-charts.md)

[Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)
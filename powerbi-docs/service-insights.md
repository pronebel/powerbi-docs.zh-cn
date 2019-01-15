---
title: 通过 Power BI 自动生成数据见解
description: 了解如何获取有关数据集和仪表板磁贴的见解。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 9e1c4a3942c75f41dc105e424685d32badbf3866
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54276413"
---
# <a name="generate-data-insights-automatically-with-power-bi"></a>通过 Power BI 自动生成数据见解
你有新数据集，但不太确定要从何处着手？  需要快速生成仪表板？  想要查找你可能错失的见解？

运行快速见解便可基于你的数据生成有趣的交互式可视化效果。 你可以对整个数据集（快速见解）或对特定仪表板磁贴（作用域内见解）运行快速见解。 甚至可以在某个见解上运行见解！

> [!NOTE]
> 见解不适用于 DirectQuery，仅适用于上传到 Power BI 的数据。
> 

见解功能以一组与 Microsoft Research 联合开发且数量不断增长的[高级分析算法](service-insight-types.md)为基础构建而成，我们将继续通过该功能让更多人以新颖直观的方式从其数据中寻找见解。

## <a name="run-quick-insights-on-a-dataset"></a>对数据集运行快速见解
观看 Amanda 如何对数据集运行快速见解，在焦点模式下打开见解，将其中一个见解作为磁贴固定到仪表板中，然后为仪表板磁贴获取见解。

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


现在轮到你了。 使用[供应商质量分析示例](sample-supplier-quality.md)探索见解。

1. 从“数据集”选项卡中选择省略号 (…)，然后选择“获取见解”。
   
    ![“数据集”选项卡](media/service-insights/power-bi-ellipses.png)
   
    ![省略号菜单](media/service-insights/power-bi-tab.png)
2. Power BI 使用[各种算法](service-insight-types.md)来搜索数据集中的趋势。
   
    ![“正在搜索见解”对话框](media/service-insights/pbi_autoinsightssearching.png)
3. 你的见解会在几秒内准备就绪。  选择“查看见解”以显示可视化效果。
   
    ![成功消息](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > 某些数据集不能生成见解，因为数据不具有统计学意义。  若要了解详细信息，请参阅[针对见解优化数据](service-insights-optimize.md)。
   > 
    
1. 可视化效果会在特殊的“快速见解”画布中显示，最多可包含 32 个不同的见解卡片。 每张卡片会有一个图表或图形，并附上简短的说明
   
    ![快速见解画布](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>与见解卡片交互
  ![“固定”图标](media/service-insights/pbi_hover.png)

1. 将鼠标悬停在某个卡片上，选择固定图标，以将可视化效果添加到仪表板中。
2. 将鼠标悬停在某张卡片上，选择省略号 (…)，然后选择“查看见解”。 见解全屏随即打开。
   
    ![见解全屏](media/service-insights/power-bi-insight-focus.png)
3. 在“焦点”模式下，你可以：
   
   * 筛选可视化效果。  若要显示筛选器，请选择右上角的箭头以展开“筛选器”窗格。
        ![深入探索展开的筛选器菜单](media/service-insights/power-bi-insights-filter-new.png)
   * 通过选择“固定”![固定图标](media/service-insights/power-bi-pin-icon.png) 图标或“固定视觉对象”将见解卡固定到仪表板。
   * 在卡片自身中运行见解。 这通常称为“作用域内见解”。 在右上角，选择灯泡图标 ![获取见解图标](media/service-insights/power-bi-bulb-icon.png)或“获取见解”。
     
       ![菜单栏显示“获取见解”图标](media/service-insights/pbi-autoinsights-tile.png)
     
     该见解显示在左侧，而完全根据该见解中的数据获得的新卡片显示在右侧。
     
       ![对见解的见解](media/service-insights/power-bi-insights-on-insights-new.png)
4. 若要返回到最初的见解画布，请在左上角选择“退出焦点模式”。

## <a name="run-insights-on-a-dashboard-tile"></a>对仪表板磁贴运行见解
将搜索范围缩小为仅针对用于创建单个仪表板磁贴的数据搜索见解，而不是针对整个数据集搜索见解。 这通常也称为“作用域内见解”。

1. 打开仪表板。
2. 将鼠标悬停在一个磁上。 选择省略号 (…)，然后选择“查看见解”。 该磁贴以[焦点模式](service-focus-mode.md)打开，并在右侧显示见解卡片。    
   
    ![焦点模式](media/service-insights/pbi-insights-tile.png)    
4. 你是否对某个见解产生了兴趣？ 选择该见解卡片以深入进行了解。 选中的见解显示在左侧，而完全根据该见解中的数据获得的新见解卡片显示在右侧。    
6. 继续发掘数据，当你发现感兴趣的见解时，从右上角选择“固定视觉对象”，将其固定到仪表板上。

## <a name="next-steps"></a>后续步骤
如果你拥有一个数据集，请[对其进行优化以用于 Quick Insights](service-insights-optimize.md)

了解[可用的快速见解的类型](service-insight-types.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


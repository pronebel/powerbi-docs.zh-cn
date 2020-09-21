---
title: 运行和查看有关仪表板磁贴的见解
description: 作为 Power BI 最终用户，了解如何获取有关仪表板磁贴的见解。
author: mihart
ms.reviewer: mihart
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/09/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 21bccbd11f8d2060b648e22c8ed8aa9471c820f0
ms.sourcegitcommit: 002c140d0eae3137a137e9a855486af6c55ad957
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89642529"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>使用 Power BI 查看有关仪表板磁贴的数据见解

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

仪表板上的每个视觉对象[磁贴](end-user-tiles.md)都是数据探索的入口。 选择磁贴时，它将打开报表或[打开“问答”](end-user-q-and-a.md)，可以在其中筛选、排序以及深入挖掘报表背后的数据集。 当运行见解时，Power BI 会为你进行数据探索。

![显示“查看见解”选项的省略号菜单模式](./media/end-user-insights/power-bi-insight.png)

运行见解便可基于数据生成有趣的交互式视觉对象。 见解可以在特定的仪表板磁贴上运行，甚至可以在见解上运行见解！

见解功能是在一组与 Microsoft Research 联合开发且数量不断增长的[高级分析算法](end-user-insight-types.md)的基础之上构建而成，我们将继续使用这些算法让更多人以直观的新方式从数据中获取见解。

## <a name="run-insights-on-a-dashboard-tile"></a>对仪表板磁贴运行见解
当在仪表板磁贴上运行见解时，Power BI 仅搜索用于创建该单个仪表板磁贴的数据。 

1. [打开仪表板](end-user-dashboards.md).
2. 将鼠标悬停在一个磁上。 选择“更多选项”(…)，并选择“查看见解” 。 

    ![此屏幕截图显示了选择省略号的显示下拉列表](./media/end-user-insights/power-bi-hover.png)


3. 该磁贴以[焦点模式](end-user-focus.md)打开，并在右侧显示见解卡片。    
   
    ![焦点模式](./media/end-user-insights/power-bi-insights-tiles.png)    
4. 你是否对某个见解产生了兴趣？ 选择该见解卡片以深入进行了解。 选中的见解显示在左侧，而完全根据该见解中的数据获得的新见解卡片显示在右侧。    

 ## <a name="interact-with-the-insight-cards"></a>与见解卡片交互
打开某个见解后，继续探索。

   * 筛选画布上的视觉对象。  若要显示筛选器，请选择右上角的箭头以展开“筛选器”窗格。

      ![包含展开的“筛选器”菜单的见解](./media/end-user-insights/power-bi-filter.png)
   
   * 在见解卡自身上运行见解。 这通常称为“相关见解”。 选择一个见解卡以将其激活。 该见解卡将移动到报表画布的左侧，而完全根据该见解中的数据获得的新卡片将显示在右侧。
   
      ![展开的“相关见解”和“筛选器”菜单](./media/end-user-insights/power-bi-insights-card.png)
   
     
若要返回报告，请从左上角选择“退出焦点模式”。

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
- **查看见解**不适用于所有仪表板磁贴类型。 例如，它不适用于 Power BI 自定义视觉对象。<!--[Power BI visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>后续步骤

[使用分析功能](end-user-analyze-visuals.md)  在报表视觉对象上运行见解  
了解[可用的 Insights 类型](end-user-insight-types.md)


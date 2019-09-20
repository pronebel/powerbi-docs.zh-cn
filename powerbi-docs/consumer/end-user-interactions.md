---
title: 了解视觉对象在报表中的交互方式
description: 适用于 Power BI 最终用户的文档，此文档介绍了视觉对象在报表页面上的交互方式。
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2019
ms.locfileid: "66413167"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>视觉对象如何在 Power BI 报表中彼此交叉筛选
Power BI 的强大功能之一是报表页上所有视觉对象的互连方式。 如果在某个视觉对象上选择一个数据点，此页面上包含该数据的其他所有视觉对象将根据所选内容而更改。 

![视觉对象互动的视频](media/end-user-interactions/interactions.gif)

默认情况下，选择报表页上可视化效果中的数据点将交叉筛选、交叉突出显示以及钻取此页面上的其他可视化效果。 

这可用于确定数据中的一个值分配给另一个值的方式。 例如，在圆环图中选择“缓和”段，突出显示从该段到“按月计算的总单位”图表中每列呈现的内容，并筛选出右侧的折线图。

![视觉对象交互的图像](media/end-user-interactions/power-bi-interactions.png)

请参阅[关于筛选和突出显示](../power-bi-reports-filters-and-highlighting.md)。 

视觉对象在一个页面上进行确切交互的方式是由报表设计器设置的  。 设计器具有可以启用和关闭视觉对象交互以及更改默认的交叉筛选、交叉突出显示和钻取行为的选项。 
  
> [!NOTE]
> 词语“ *交叉筛选* ”和“ *交叉突出显示* ”用于区分本文描述的行为与使用“**筛选器**”窗格来筛选和突出显示可视化组件的效果。  

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
- 如果报表拥有支持[钻取](../power-bi-visualization-drill-down.md)的可视化效果，在默认情况下，钻取某个可视化效果不会对报表页上的其他可视化效果造成影响。     
- 如果使用 visualA 以与 visualB 进行交互，则 visualA 中的视觉对象级筛选器将应用于 visualB。

## <a name="next-steps"></a>后续步骤
[如何使用报表筛选器](../power-bi-how-to-report-filter.md)

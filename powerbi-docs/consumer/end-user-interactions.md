---
title: 了解视觉对象在报表中的交互方式
description: 适用于 Power BI 最终用户的文档，此文档介绍了视觉对象在报表页面上的交互方式。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 28e6cea55b02fabddd0b2f118631a09c0344b66f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863094"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>视觉对象如何在 Power BI 报表中彼此交叉筛选
Power BI 的强大功能之一是报表页上所有视觉对象的互连方式。 如果在某个视觉对象上选择一个数据点，此页面上包含该数据的其他所有视觉对象将根据所选内容而更改。 

![视觉对象互动的视频](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>视觉对象如何相互交互

默认情况下，选择报表页上一个视觉对象中的数据点将交叉筛选或交叉突出显示此页面上的其他视觉对象。 视觉对象在一个页面上进行确切交互的方式是由报表设计器设置的  。 设计器具有可以启用和关闭视觉对象交互以及更改默认的交叉筛选、交叉突出显示和[钻取](end-user-drill.md)行为的选项  。 

如果尚未遇到层次结构或钻取，则可以通过阅读 [Power BI 中的向下钻取](end-user-drill.md)来了解所有相关信息。 

交叉筛选和交叉突出显示可用于确定数据中的一个值分配给另一个值的方式。 例如，在圆环图中选择“缓和”段，突出显示从该段到“按月计算的总单位”图表中每列呈现的内容，并筛选出折线图。

![视觉对象交互的图像](media/end-user-interactions/power-bi-interactions.png)

请参阅[关于筛选和突出显示](end-user-report-filter.md)。 


  
> [!NOTE]
> 词语“交叉筛选”和“交叉突出显示”用于区分本文描述的行为与使用“筛选器”窗格来筛选和突出显示视觉对象的效果    。  

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
- 如果报表拥有支持[钻取](end-user-drill.md)的视觉对象，在默认情况下，钻取某个视觉对象不会对报表页上的其他视觉对象造成影响。     
- 如果使用 visualA 以与 visualB 进行交互，则 visualA 中的视觉对象级筛选器将应用于 visualB。

## <a name="next-steps"></a>后续步骤
[如何使用报表筛选器](../power-bi-how-to-report-filter.md)

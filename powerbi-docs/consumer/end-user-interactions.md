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
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 43046a5fab33f384a6d9f573a992843fa84a0713
ms.sourcegitcommit: a054782370dec56d49bb205ee10b7e2018f22693
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662218"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>视觉对象如何在 Power BI 报表中彼此交叉筛选
Power BI 的强大功能之一是报表页上所有视觉对象的互连方式。 如果在某个视觉对象上选择一个数据点，此页面上包含该数据的其他所有视觉对象将根据所选内容而更改。 

![视觉对象互动的视频](media/end-user-interactions/interactions.gif)

默认情况下，报表页上的可视化效果组件可用于交叉筛选、交叉突出显示以及钻取此页面上的其他可视化效果。 例如，在地图可视化效果上选择一个省/市/自治区可以突出显示柱形图并筛选折线图以仅显示适用于此省/市/自治区的数据。

请参阅[关于筛选和突出显示](../power-bi-reports-filters-and-highlighting.md)。 如果具有支持[钻取](../power-bi-visualization-drill-down.md)的可视化效果，在默认情况下，钻取某个可视化效果不会对报表页上的其他可视化效果造成影响。 

视觉对象在一个页面上进行确切交互的方式是由报表设计器设置的。 设计器具有可以启用和关闭视觉对象交互以及更改默认的交叉筛选、交叉突出显示和钻取行为的选项。
  
> [!NOTE]
> 词语“ *交叉筛选* ”和“ *交叉突出显示* ”用于区分本文描述的行为与使用“**筛选器**”窗格来筛选和突出显示可视化组件的效果。  

### <a name="next-steps"></a>后续步骤
[如何使用报表筛选器](../power-bi-how-to-report-filter.md)

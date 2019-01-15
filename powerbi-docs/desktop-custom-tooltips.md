---
title: 在 Power BI Desktop 中自定义工具提示
description: 使用拖放创建视觉对象的自定义工具提示
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5fc013df4526c62a9f2e1aa25328119983aaa30e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54278092"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>在 Power BI Desktop 中自定义工具提示
工具提示是向视觉对象上的数据点提供更多上下文信息和详细信息的一种巧妙方法。 下图展示了应用到 Power BI Desktop 中的图表的工具提示。

![默认工具提示](media/desktop-custom-tooltips/custom-tooltips-1.png)

创建可视化效果时，默认工具提示会显示数据点的值和类别。 很多能够自定义工具提示信息的实例都非常有用，并可向查看视觉对象的用户提供其他上下文和信息。 自定义工具提示可以指定显示为工具提示一部分的其他数据点。

## <a name="how-to-customize-tooltips"></a>自定义工具提示的方式
若要创建自定义工具提示，只需在**可视化效果**窗格的**字段**框中，将字段拖动到**工具提示**存储桶，如下图所示。 下图中，已将两个字段放入“工具提示”Bucket。

![添加工具提示字段](media/desktop-custom-tooltips/custom-tooltips-2.png)

将工具提示添加到字段框后，将鼠标悬停在可视化效果的数据点上会在工具提示中显示这些字段的值。

![自定义工具提示](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>使用聚合或 Quick Calcs 自定义工具提示
可以通过选择聚合函数或选择**工具提示**存储桶中的字段旁的箭头，然后从可用选项中选择 *Quick Calc* 来进一步自定义工具提示。

![通过快速计算编写工具提示](media/desktop-custom-tooltips/custom-tooltips-4.png)

自定义**工具提示**的方法有很多，使用数据集中的任何可用字段都可向查看仪表板或报表的用户传达快速信息和见解。


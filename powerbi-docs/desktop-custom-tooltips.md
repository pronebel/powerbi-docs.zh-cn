---
title: 在 Power BI Desktop 中自定义工具提示
description: 使用拖放创建视觉对象的自定义工具提示
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d5259ba22287a8a2ade3107e4320c39713dcb45e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239743"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>在 Power BI Desktop 中自定义工具提示
工具提示是向视觉对象上的数据点提供更多上下文信息和详细信息的一种巧妙方法。 下图展示了应用到 Power BI Desktop 中的图表的工具提示。

![默认工具提示](media/desktop-custom-tooltips/custom-tooltips-1.png)

创建可视化效果时，默认工具提示会显示数据点的值和类别。 自定义工具提示信息很有用，并可以提供其他上下文和用户查看视觉对象的信息时，有多个实例。 自定义工具提示可以指定显示为工具提示一部分的其他数据点。

## <a name="how-to-customize-tooltips"></a>自定义工具提示的方式
若要在中创建自定义工具提示**字段**框的**可视化效果**窗格中将字段拖到**工具提示**存储桶，如下图中所示。 下图中，已将两个字段放入“工具提示”Bucket  。

![添加工具提示字段](media/desktop-custom-tooltips/custom-tooltips-2.png)

将工具提示添加到字段框后，将鼠标悬停在可视化效果的数据点上会在工具提示中显示这些字段的值。

![自定义工具提示](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>使用聚合或 Quick Calcs 自定义工具提示
可以通过选择聚合函数或选择**工具提示**存储桶中的字段旁的箭头，然后从可用选项中选择 *Quick Calc* 来进一步自定义工具提示。

![通过快速计算编写工具提示](media/desktop-custom-tooltips/custom-tooltips-4.png)

有很多种自定义**工具提示**，使用任何字段在数据集中，可用来传达快速信息和查看仪表板或报表的用户的见解。


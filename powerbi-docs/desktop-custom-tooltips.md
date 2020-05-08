---
title: 在 Power BI Desktop 中自定义工具提示
description: 使用拖放创建视觉对象的自定义工具提示
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 93177ac56bc2d8ecfe4b85f4ab66daef6bf0f0f3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160988"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>在 Power BI Desktop 中自定义工具提示

工具提示是向视觉对象上的数据点提供更多上下文信息和详细信息的一种巧妙方法。 下图展示了应用到 Power BI Desktop 中的图表的工具提示。

![默认工具提示](media/desktop-custom-tooltips/custom-tooltips-1.png)

创建可视化效果时，默认工具提示会显示数据点的值和类别。 在许多情况下，自定义工具提示信息很有用。 自定义工具提示为查看视觉对象的用户提供附加的上下文和信息。 自定义工具提示可以指定显示为工具提示一部分的其他数据点。

## <a name="how-to-customize-tooltips"></a>自定义工具提示的方式

若要创建自定义工具提示，在“可视化效果”  窗格的“字段”  框中，将字段拖动到“工具提示”  Bucket，如下图所示。 下图中，已将三个字段放入“工具提示”  Bucket。

![添加工具提示字段](media/desktop-custom-tooltips/custom-tooltips-2.png)

将工具提示添加到“工具提示”  后，将鼠标悬停在可视化效果的数据点上会显示这些字段的值。

![自定义工具提示](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>使用聚合或快速度量自定义工具提示

可以通过选择聚合函数或快速度量  ，进一步自定义工具提示。 选择“工具提示”  Bucket 中字段旁边的箭头。 然后从可用选项中进行选择。

![具有快速度量的工具提示](media/desktop-custom-tooltips/custom-tooltips-4.png)

自定义工具提示的方法有很多，使用数据集中的任何可用字段都可向查看仪表板或报表的用户传达快速信息和见解。

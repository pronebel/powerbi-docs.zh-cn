---
title: 分析窗格
description: 如何在 Power BI 视觉对象中创建动态参考行
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425519"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Power BI 视觉对象中的分析窗格

2018 年 11 月，[本机视觉对象引入了](https://docs.microsoft.com/power-bi/desktop-analytics-pane)分析窗格  。
具有 API v2.5.0 的自定义视觉对象可以在分析窗格中显示和管理其属性  。

![分析窗格](./media/visualization-pane-analytics-tab.png)

其处理方式类似于[在“格式”窗格中管理属性](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options)，方法是在视觉对象的 capabilities.json 文件中定义一个对象。 

不同之处如下所示：

1. 在 `objectCategory` 的定义下，添加一个值为 2 的 `object` 字段。

    > [!NOTE]
    > `objectCategory` 字段是 API 2.5.0 中引入的可选字段。 它定义了对象控制的视觉对象方面（1 = 格式设置，2 = 分析）。 “格式设置”用于外观、颜色、轴、标签等。“分析”用于预测、趋势线、参考行和形状等。
    >
    > 如果忽略 `objectCategory`，它会默认为“格式设置”。

2. 对象必须具有以下两种属性：
    1. Bool 类型的 `show`，默认值为 false。
    2. 文本类型的 `displayName`。 所选择的默认值将成为实例的初始显示名称。

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

任何其他属性均可采用与格式设置对象相同的定义方式。 对象枚举的执行方式与在格式设置窗格中完全相同  。

已知限制和问题

  1. 尚无多实例支持。 对象的[选择器](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector)只能是静态选择器（即“选择器”：null），并且自定义视觉对象不能有用户定义的多个卡实例。
  2. 类型 `integer` 的属性显示不正确。 一种解决方法是，改用类型 `numeric`。

> [!NOTE]
> 仅为用于添加新信息或进一步揭示显示的信息的对象使用分析窗格。 例如，用于说明重要趋势的动态参考行。
> 控制视觉对象外观的任何选项（即格式设置）都应保留在“格式设置”窗格中。

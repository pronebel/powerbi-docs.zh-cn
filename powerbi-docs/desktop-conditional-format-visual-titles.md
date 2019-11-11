---
title: Power BI Desktop 中基于表达式的标题
description: 使用条件编程格式，在 Power BI Desktop 中创建会根据编程表达式进行更改的动态标题
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f3c1f047e3be7520005458294381877d1198ee21
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878632"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Power BI Desktop 中基于表达式的标题

可为 Power BI 视觉对象创建动态的自定义标题。 通过基于字段、变量或其他编程元素来创建数据分析表达式 (DAX)，可以根据需要自动调整视觉对象的标题。 这些更改基于筛选器、所选内容或其他用户交互和配置。

![Power BI Desktop 条件格式选项的屏幕截图](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

创建动态标题（有时称为“基于表达式的标题”  ）非常简单。 

## <a name="create-a-field-for-your-title"></a>为标题创建字段

创建基于表达式的标题的第一步是在模型中创建一个用于标题的字段。 

有各种创造性的方法可以让视觉对象标题反映出你想要表达的内容。 我们来看看几个示例。

可创建一个表达式，该表达式会根据视觉对象接收到的用于产品品牌名的筛选器上下文进行更改。 下图显示了此类字段的 DAX 公式。

![DAX 公式的屏幕截图](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

另一个示例是使用根据用户的语言或区域性进行更改的动态标题。 可使用 `USERCULTURE()` 函数在 DAX 度量值中创建特定于语言的标题。 此函数根据用户的操作系统或浏览器设置返回用户的区域性代码。 可使用以下 DAX switch 语句来选择正确的转换后的值。 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

或者，可从包含所有转换的查找表中检索字符串。 将该表放在模型中。 

这些只是有助于在 Power BI Desktop 中为视觉对象创建基于表达式的动态标题的一部分示例。 你可以采用任何你想象得到的方式来处理标题，只要适合你的模型。


## <a name="select-your-field-for-your-title"></a>为标题选择字段

在为模型中创建的字段创建 DAX 表达式后，需要将其应用于视觉对象的标题。

若要选择该字段并应用，请转到“可视化效果”窗格  。 在“格式”区域中，选择“标题”以显示可用于视觉对象的标题选项   。 

右键单击“标题文本”，这将显示一个上下文菜单，可在其中选择“fx条件格式”   。 选择该菜单项后，会出现“标题文本”对话框  。 

![“标题文本”对话框的屏幕截图](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

在该窗口中，可选择所创建的用于标题的字段。

## <a name="limitations-and-considerations"></a>限制和注意事项

当前基于表达式的视觉对象标题的实现存在一些限制：

* Python 视觉对象、R 视觉对象或“关键影响因素”视觉对象目前不支持基于表达式的格式设置。
* 为标题创建的字段必须是字符串数据类型。 目前不支持会返回数字或日期/时间（或任何其他数据类型）的度量值。
* 将视觉对象固定到仪表板时，不会保留基于表达式的标题。

## <a name="next-steps"></a>后续步骤

本文介绍了如何创建 DAX 表达式，将视觉对象的标题转换为可在用户与报表交互时发生更改的动态字段。 以下文章可能也会对你有所帮助。

* [表格中的条件格式设置](desktop-conditional-table-formatting.md)
* [在 Power BI Desktop 中使用跨报表钻取](desktop-cross-report-drill-through.md)
* [在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)

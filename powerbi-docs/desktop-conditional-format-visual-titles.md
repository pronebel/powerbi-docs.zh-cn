---
title: 基于表达式的 Power BI Desktop 中的标题
description: Power BI Desktop 中的更改以编程方式的表达式，使用条件格式以编程方式创建动态标题
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769735"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>基于表达式的 Power BI Desktop 中的标题

您可以创建动态的自定义你的 Power BI 视觉对象的标题。 通过创建数据分析表达式 (DAX) 基于字段、 变量或其他编程元素，根据需要可以自动调整视觉对象的标题。 这些更改基于筛选器中，选择，或其他用户交互和配置。

![Power BI Desktop 的屏幕截图条件格式设置选项](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

创建动态标题，有时称为*基于表达式的标题*，非常简单。 

## <a name="create-a-field-for-your-title"></a>创建你的标题字段

创建的基于表达式的标题的第一步是创建要用于标题在模型中的字段。 

有各种类型的创造性的方式能够反映你的想说，或想要表示在视觉对象的标题。 让我们看看几个示例。

可以创建表达式，用于更改基于视觉对象接收有关产品的品牌名称筛选器上下文。 下图显示了此类字段的 DAX 公式。

![屏幕截图的 DAX 公式](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

另一个示例使用更改，根据用户的语言或区域性的动态标题。 可以通过使用 DAX 度量值中创建特定于语言的标题`USERCULTURE()`函数。 此函数返回用户，基于其操作系统或浏览器设置的区域性代码。 以下 DAX switch 语句可用于选择正确的已翻译的值。 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

也可以从包含所有翻译的查找表中检索字符串。 将该表放在您的模型中。 

这些是只需几个示例可用于在 Power BI Desktop 中创建你的视觉对象的动态、 基于表达式的标题。 仅受您的模型和您发挥想象力，限制对应用标题可以执行哪些操作。


## <a name="select-your-field-for-your-title"></a>选择您为您的标题的字段

创建在模型中创建的字段的 DAX 表达式后，您需要将其应用于视觉对象的标题。

若要选择的字段，并将其应用，请转到**可视化效果**窗格。 在中**格式**区域中，选择**标题**以显示该视觉对象标题选项。 

右键单击时**标题文本**，将显示上下文菜单，可以选择 ***fx* 条件格式设置**。 选择该菜单项时**标题文本**对话框随即出现。 

![屏幕截图的标题文本对话框](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

从该窗口中，您可以选择创建要用于你的标题的字段。

## <a name="limitations-and-considerations"></a>限制和注意事项

有一些限制视觉对象的基于表达式的标题的当前实现：

* 基于表达式的格式设置不是当前支持 Python 视觉对象、 R 视觉对象或关键影响因素视觉对象。
* 创建标题的字段必须是字符串数据类型。 目前不支持返回数字或日期/时间 （或任何其他数据类型） 的度量值。

## <a name="next-steps"></a>后续步骤

本文介绍了如何创建将变成在与报表进行交互的用户可以更改的动态字段的视觉对象标题的 DAX 表达式。 您可能会发现以下文章有用以及。

* [在 Power BI Desktop 中使用跨报表钻取](desktop-cross-report-drill-through.md)
* [在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)
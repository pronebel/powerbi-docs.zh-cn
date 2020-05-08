---
title: 在 Power BI 中创建钻取按钮
description: 可以在 Power BI 报表中添加钻取按钮，以使报表的行为类似于应用，并加深与用户的互动。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d3cb3c8093446d4417a59c5f64ab6b85a765e3c8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79206438"
---
# <a name="create-a-drill-through-button-in-power-bi-preview"></a>在 Power BI 中创建钻取按钮（预览）

在 Power BI 中创建按钮时，可以选择“钻取(预览)”操作  。 此操作类型可创建一个按钮，该按钮将钻取到专门的页面，获取根据特定上下文筛选的详细信息。

如果希望提高报表中重要钻取方案的可发现性，则可以使用钻取按钮。

在此示例中，用户选择图表中的 Word 栏后即会启用“查看详细信息”按钮  。

![“查看详细信息”按钮](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

选择“查看详细信息”按钮后，会钻取到“市场篮分析”页面  。 从左侧的视觉对象中可以看到，钻取页面现在的筛选条件为 Word。

![筛选后的视觉对象](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>设置钻取按钮

要设置钻取按钮，首先需要在报表中[设置一个有效的钻取页面](desktop-drillthrough.md)。 然后，需要创建一个操作类型为“钻取”按钮，然后选择钻取页面作为“目标”   。

由于钻取按钮有两种状态（钻取“已启用”和“已禁用”），可看到两个工具提示选项。

![设置钻取按钮](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

如果将工具提示框留空，Power BI 会自动生成工具提示。 这些工具提示基于目标和钻取字段。

下面是禁用按钮时自动生成的工具提示的示例：

“要钻取到‘市场篮分析’（目标页面），请从‘产品’（钻取字段）中选择一个数据点”。

![禁用按钮时自动生成的工具提示](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

下面是启用按钮时自动生成的工具提示的示例：

“单击以钻取到‘市场篮分析’（目标页面）”。

![启用按钮时自动生成的工具提示](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

但是，如果要提供自定义工具提示，始终都可输入静态字符串。 尚不支持工具提示的条件格式。

可以使用条件格式根据选择的字段值更改按钮文本。 为此，需要创建一个度量值，根据 DAX 函数 SELECTEDVALUE 输出所需字符串。

下面是一个示例度量值，如果没有选择一个“产品”值，此度量值输出“查看产品详细信息”；否则，它输出“查看 [选定产品] 的详细信息”：

```
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0), "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

创建此度量值后，请为按钮文本选择“条件格式”选项  ：

![选择“条件格式”](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

然后，选择为按钮文本创建的度量值：

![基于字段的值](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

选择单个产品时，按钮文本显示：

“查看 Word 的详细信息”

![选择单个值时](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

如果未选择任何产品或选择了多个产品，则该按钮将被禁用，并且按钮文本显示：

“查看产品详细信息”

![选择多个值时](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="pass-filter-context"></a>传递筛选器上下文

按钮的工作方式与常规钻取类似，因此还可以通过交叉筛选包含钻取字段的视觉对象在其他字段中传递筛选器。 例如，使用 Ctrl  **单击和交叉筛选，可以将 Store 中的多个筛选器传递到钻取页面，因为所选内容对包含“产品”（即钻取字段）的视觉对象进行了交叉筛选** +   ：

![传递筛选器上下文](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

选择钻取按钮时，可看到 Store 和产品中的筛选器同时传递到目标页面中：

![此页上的筛选器](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>不明确的筛选器上下文

由于钻取按钮没有绑定到单个视觉对象，因此，如果选择不明确，则会禁用此按钮。

在此示例中，按钮处于禁用状态，因为两个视觉对象在“产品”中都包含一个选择。 关于可以从哪个视觉对象将钻取操作绑定到哪个数据点存在歧义：

![不明确的筛选器上下文](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="limitations"></a>限制

- 此按钮不允许多个目标使用单个按钮。
- 此按钮仅支持在同一报表中进行钻取。换句话说，它不支持交叉报表钻取。
- 按钮的禁用状态格式与报表主题中的颜色类别相关。 详细了解[颜色类别](desktop-report-themes.md#setting-structural-colors)。
- 钻取操作适用于所有内置视觉对象以及从 AppSource 导入的某些视觉对象  。 但并不保证此操作适用于从 AppSource 导入的所有视觉对象  。

## <a name="next-steps"></a>后续步骤
若要详细了解与按钮类似或与其交互的功能，请参阅以下文章：

* [创建按钮](desktop-buttons.md)
* [在 Power BI 报表中使用钻取](desktop-drillthrough.md)
* [在 Power BI 中使用书签共享见解和创建情景](desktop-bookmarks.md)


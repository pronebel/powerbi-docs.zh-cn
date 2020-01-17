---
title: 使用 What if 参数可视化变量
description: 创建自己的 What if 变量，想象并可视化 Power BI 报表中的变量
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8b9f1fc618e30d93da36b28f710dbd33f8125054
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2020
ms.locfileid: "75759305"
---
# <a name="create-and-use-what-if-parameters-to-visualize-variables-in-power-bi-desktop"></a>创建和使用 What-if 参数可视化 Power BI Desktop 中的变量
从 Power BI Desktop 2018 年 8 月版开始，用户可以为报表创建 What if 变量、以切片器的形式与变量交互，以及可视化并量化报表中的不同键值   。

![](media/desktop-what-if/what-if_01.png)

可以在 Power BI Desktop  中的“建模”  选项卡上找到“What if”  参数。 选择参数时，会显示一个对话框，可在其中配置该参数。

## <a name="creating-a-what-if-parameter"></a>创建 What if 参数
要创建 What if  参数，请在 Power BI Desktop  中的“建模”  选项卡上选择“What if”  按钮。 在下图中，我们已创建名为“折扣率”  的参数，并将其数据类型设置为十进制数字  。 最小  值为零，最大  值为 0.50 (50%)。 我们还将增量  设置为 0.05 或 5%。 这就是在报表中交互时将会调整的参数量。

![](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> 对于十进制数字，请务必在前面加上零，例如，0.50 而不是 .50。 否则，该数字不会得到验证，且“确定”  按钮将不可选。
> 
> 

为方便起见，“将切片器添加到此页”  复选框会将切片器和 What if  参数自动放置在当前报表页上。

![](media/desktop-what-if/what-if_03.png)

除创建参数外，创建 What if  参数还会创建一个度量值，可以用它来可视化 What if  参数的当前值。

![](media/desktop-what-if/what-if_04.png)

注意，创建 What if  参数后，该参数和度量值都会成为模型的一部分，这是很重要且很有用的一点。 因此，它们可在整个报表上使用，并可用于其他报表页。 而且，由于它们是模型的一部分，用户可以从报表页中删除切片器，或者如果想恢复它，只需在“字段”  列表中抓取 What if  参数并将其拖动到画布（然后将视觉对象更改为切片器），就能轻松地使该参数重新回到报表中。

## <a name="using-a-what-if-parameter"></a>使用 What if 参数
让我们使用 What if  参数创建一个简单示例。 在上一节中，我们创建了 What if  参数，现在，我们将通过创建其值会根据切片器调整的新度量值来利用该参数。 要实现此目的，我们会创建新的度量值。

![](media/desktop-what-if/what-if_05.png)

新的度量值只是应用了折扣率的总销售额。 当然，可以创建复杂且有趣的度量值，让报表的使用者可视化 What if  参数的变量。 例如，可以创建一个报表，让销售人员看到在达到特定销售目标或销售百分比时他们的薪酬，或看到销售额增加对更优厚折扣力度的影响。

当我们在公式栏中键入度量值公式，并将其命名为“折后销售额”  后，我们会看到其结果：

![](media/desktop-what-if/what-if_06.png)

然后，我们在轴上创建一个具有 OrderDate  的列视觉对象，并将 SalesAmount  和刚创建的度量值“折后销售额”  作为值。

![](media/desktop-what-if/what-if_07.png)

然后，当移动滑块时，我们会看到“折后销售额”  列反映已折扣的销售额。

![](media/desktop-what-if/what-if_08.png)

以上是其中包含的全部内容。 可以在各种情况中使用 What if  参数，以允许报表的使用者与在报表中创建的不同方案进行交互。


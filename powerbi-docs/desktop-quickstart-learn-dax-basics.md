---
title: Power BI Desktop 中的 DAX 基本概念
description: Power BI Desktop 中的 DAX 基本概念
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9ff04510a786fa89e1e461e6eefee1af90e58a8e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "75760626"
---
# <a name="apply-dax-basics-in-power-bi-desktop"></a>在 Power BI Desktop 中应用 DAX 的基础知识
本文适用于刚开始使用 Power BI Desktop 的用户。 为你提供有关如何使用数据分析表达式 (DAX) 的快速而简单的介绍，以便解决一些基本计算和数据分析问题。 我们将逐一探讨一些概念性信息、一系列可以完成的任务以及测试所学内容的知识检查。 学习完本文后，你便可充分了解 DAX 中最重要的基本概念。

## <a name="what-is-dax"></a>DAX 是什么？
DAX 是公式或表达式中可用于计算并返回一个或多个值的函数、运算符或常量的集合。 简单来说，DAX 可帮助你通过模型中已有的数据来创建新信息。

## <a name="why-is-dax-so-important"></a>为什么 DAX 很重要？
可以轻松地创建新的 Power BI Desktop 文件并导入一些数据。 你甚至可以创建显示宝贵见解的报表，而完全不需要使用任何 DAX 公式。 但是，如果你需要分析跨产品类别和不同日期范围内的增长百分比，该怎么办？ 或者，需要计算相对于市场趋势的同比增长，该怎么办？ DAX 公式具备这项功能以及许多其他重要功能。 了解如何创建有效的 DAX 公式可帮助你充分利用数据。 获取所需信息后，便可开始解决影响最终赢利的实际商业问题。 这便是 Power BI 的强大之处，而 DAX 将帮助你达成目的。

## <a name="prerequisites"></a>先决条件
你可能已经熟悉如何在 Microsoft Excel 中创建公式。 这一知识有助于了解 DAX，但即使你没有使用 Excel 公式的经验，此处描述的概念也将帮助你开始创建 DAX 公式并立即解决真实世界的 BI 问题。

我们将重点介绍计算中所用的 DAX 公式，更确切地说，也就是度量值和计算列中所用的 DAX 公式。 你应该已经熟悉使用 Power BI Desktop 来导入数据以及将字段添加到报表，而且还应熟悉[度量值](desktop-measures.md)和[计算列](desktop-calculated-columns.md)的基本概念。

### <a name="example-workbook"></a>示例工作簿

了解 DAX 的最佳方式是创建一些基本公式，用它来处理实际数据，并亲自查看结果。 此处的示例和任务使用 [Power BI Desktop 的 Contoso 销售示例文件](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip)。 此示例文件与 [教程：在 Power BI Desktop 中创建你自己的度量值](desktop-tutorial-create-measures.md)一文中使用的相同示例文件。 

## <a name="lets-begin"></a>现在就开始吧！
我们将围绕三个基本概念来阐述对 DAX 的理解：语法  、函数  和上下文  。 DAX 还有其他重要概念，但了解这三个概念将为你学习 DAX 技能奠定最佳基础。

### <a name="syntax"></a>语法
创建你自己的公式之前，我们来看看 DAX 公式语法。 语法包括组成公式的各种元素，简单来说就是公式的编写方式。 例如，以下是某个度量值的简单 DAX 公式：

![DAX 公式语法](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

此公式包含以下语法元素：

**A.** 度量值名称 Total Sales。 

**B.** 等号运算符 ( **=** ) 表示公式的开头。 完成计算后将会返回结果。

**C.** DAX 函数 SUM 会将 Sales[SalesAmount] 列中的所有数字相加。   稍后你将了解有关函数的详细信息。

**D.** 括号 () 会括住包含一个或多个参数的表达式。  所有函数都至少需要一个参数。 一个参数会传递一个值给函数。

**E.** 引用的表 Sales。 

**F.** Sales 表中的引用列 [SalesAmount]。  使用此参数，SUM 函数就知道在哪一列上进行聚合求和。

尝试了解 DAX 公式时，将每个元素分解成你平日思考及说出的话语会很有帮助。 例如，你可以将此公式读成：

> *对于名为 Total Sales 度量值，计算 (=) Sales 表的 [SalesAmount] 列中的值的总和。*
> 
> 

添加到报表后，此度量值会将所包括的其他每个字段的销售额（例如美国的手机）相加，进行计算并返回值。

你可能会想，“这个度量值的功能不是与直接将 SalesAmount 字段添加到我的报表中一样吗？” 没错。 但是，创建自己的度量值来对 SalesAmount 字段中的值求和有个好处：我们可以将它当作参数用于其他公式。 虽然现在可能有点难以理解，但随着你对 DAX 公式的熟悉，了解这度量值可让你的公式和模型更有效率。 事实上，稍后你将看到 Total Sales 度量值如何显示为其他公式中的参数。

现在我们将讨论关于此公式的一些其他内容。 我们将着重介绍 [SUM](https://msdn.microsoft.com/library/ee634387.aspx) 函数。 函数是预编写的公式，能够简化复杂计算和对数字、日期、时间、文本等内容的操作。 稍后你将了解有关函数的详细信息。

你还会看到 [SalesAmount] 列前面加上了列所属的 Sales 表。 这就是所谓的完全限定列名称，因为它包括列名称且前面加上了表名。 同一个表中引用的列不需要在公式中包含表名，这可以使引用多个列的长公式更短且更易于阅读。 但是，最好能够在你的度量值公式中包含表名，即使在同一表中亦然。

> [!NOTE]
> 如果表名包含空格、保留的关键字或不允许的字符，则必须用单引号引住该表名。 如果该名称包含 ANSI 字母数字字符范围以外的任何字符，则不论你的区域设置是否支持字符集，均需用引号引住表名。
> 
> 

公式语法的正确性非常重要。 大多数情况下，如果语法不正确，将返回语法错误。 其他情况下，语法可能正确，但返回的值可能不是预期值。 Power BI Desktop 中的 DAX 编辑器包括了建议功能，这项功能通过帮助你选择正确的元素来创建语法正确的公式。

我们来创建一个简单公式。 此任务将帮助你进一步了解公式语法以及编辑栏中的建议功能可以起到怎样的作用。

### <a name="task-create-a-measure-formula"></a>任务：创建度量值公式

1. [下载](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip)并打开 Contoso 销售示例 Power BI Desktop 文件。 
    
2. 在“报表”视图的字段列表中，右键单击 Sales 表，然后选择“新建度量值”   。
    
3. 在编辑栏中，通过键入新的度量值名称 Previous Quarter Sales 来替换“度量值”   。
    
4. 在等号后键入前几个字母 CAL  ，然后双击要使用的函数。 在此公式中，需要使用 CALCULATE  函数。

   你将通过我们传递给 CALCULATE 函数的参数，使用 CALCULATE 函数来筛选要求和的金额。 这就是所谓的嵌套函数。 CALCULATE 函数至少有两个参数。 第一个参数是要计算的表达式，第二个参数是筛选器。
   
5. 在 CALCULATE 函数的左括号 (   之后，键入 SUM  ，随后是另一个左括号 (  

   现在我们将参数传递给 SUM 函数。

6. 开始键入 Sal  ，然后选择 Sales[SalesAmount]  ，后跟右括号 )  。 

   这是 CALCULATE 函数的第一个表达式参数。
    
7. 在空格后键入逗号 (,  ) 以指定第一个筛选器，然后键入 PREVIOUSQUARTER  。 
    
   你将使用 PREVIOUSQUARTER 时间智能函数按上一季度来筛选 SUM 结果。
    
8. 在 PREVIOUSQUARTER 函数的括号 (  之后，键入 Calendar[DateKey]  。
    
   PREVIOUSQUARTER 函数有一个参数，即包含连续日期范围的列。 在本例中，这是日历表中的 DateKey 列。
    
9. 通过键入两个两个右括号 )) 关闭要传递给 PREVIOUSQUARTER 和 CALCULATE 函数的两个自变量  。
    
   该公式现在应如下所示：
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
10. 选中复选标记 ![“复选标记”图标](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) 或按 Enter 键，验证公式并将其添加到模型中。

你做到了！ 你刚才使用 DAX 创建了一个复杂的度量值，而不是一个简单的度量值。 这个公式将根据报表中应用的筛选器来计算上一季度的总销售额。 例如，如果我们将 SalesAmount 和新的 Previous Quarter Sales 度量值放置于图表中，然后添加 Year 和 QuarterOfYear 作为切片器，则会得到类似如下的结果：

![Previous Quarter Sales 和 SalesAmount 图](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

为你介绍 DAX 公式的几个重要方面： 

- 此公式包括两个函数。 [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx) 时间智能函数被嵌套为参数传递给 [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx) 筛选器函数。 

   DAX 可以包含多达 64 个嵌套函数。 一个公式不大可能会包含这么多嵌套函数。 实际上，创建和调试这样的公式会很困难，而且也不会太快。

- 在此公式中，你同样使用了筛选器。 筛选器会缩小要进行计算的范围。 在本例中，你选择了一个筛选器作为参数，它实际上是另一个函数的结果。 稍后你将了解有关筛选器的详细信息。

- 你使用了 CALCULATE 函数。 此函数是 DAX 中功能最强大的函数之一。 当你创作模型并创建更复杂的公式时，可能会多次使用此函数。 虽然有关 CALCULATE 函数的进一步讨论不在本文的讨论范围内，但是随着你对 DAX 了解的深入，请重视这个函数。

### <a name="syntax-quickquiz"></a>语法快速测验
1. 编辑栏上这个按钮的功能是什么？
   
   > ![按钮选择](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. 一律会用什么括住 DAX 公式中的列名？

本文末尾将提供解答。

### <a name="functions"></a>函数
函数是通过使用特定值、调用参数，并按特定顺序或结构来执行计算的预定义公式。 参数可以是其他函数、另一个公式、表达式、列引用、数字、文本、逻辑值（如 TRUE 或 FALSE）或者常量。

DAX 包含以下函数类别：[日期和时间](https://msdn.microsoft.com/library/ee634786.aspx)函数、[时间智能](https://msdn.microsoft.com/library/ee634763.aspx)函数、[信息](https://msdn.microsoft.com/library/ee634552.aspx)函数、[逻辑](https://msdn.microsoft.com/library/ee634365.aspx)函数、[数学](https://msdn.microsoft.com/library/ee634241.aspx)函数、[统计](https://msdn.microsoft.com/library/ee634822.aspx)函数、[文本](https://msdn.microsoft.com/library/ee634938.aspx)函数、[父/子](https://msdn.microsoft.com/library/mt150102.aspx)函数和[其他](https://msdn.microsoft.com/library/mt150101.aspx)函数。 如果你熟悉 Excel 公式中的函数，那么 DAX 中的很多函数都会让你觉得相似；但是，DAX 函数在以下方面是独一无二的：

* DAX 函数始终引用完整列或表。 如果你仅想使用某个表或列中的特定值，则可以向公式添加筛选器。
* 如果需要逐行自定义计算，DAX 提供可让你将当前行值或相关值用作一种参数的函数，以便执行因上下文而变的计算。 稍后你将了解有关上下文的详细信息。
* DAX 包括许多会返回表而非值的函数。 表不会显示出来，但可以将其用于提供其他函数的输入。 例如，你可以检索表，然后计算其中的非重复值，或者计算所筛选的表或列的动态总和。
* DAX 包括各种时间智能函数。 这些函数可让你定义或选择日期范围，并基于此范围执行动态计算。 例如，你可以比较并行时间段内的总和。
* Excel 有一个热门的函数 VLOOKUP。 不同于 Excel 中的 VLOOKUP，DAX 函数不会采用单元格或单元格区域作为引用。 DAX 函数采用某一列或表作为引用。 请记住，在 Power BI Desktop 中，将使用关系数据模型。 查找另一个表中的值其实很简单，而且在大多数情况下，完全不需要创建任何公式。
  
  如你所见，DAX 中的函数可帮助你创建功能非常强大的公式。 我们实际上只接触到了函数的基本概念。 随着你对 DAX 技能的熟悉，你将使用许多不同的函数来创建公式。 若要了解有关每个 DAX 函数的详细信息，最好的办法之一就是参阅 [DAX 函数参考](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference)。

### <a name="functions-quickquiz"></a>函数快速测验
1. 函数会始终引用何项？
2. 一个公式是否可以包含多个函数？
3. 可以使用哪种函数类别来将两个文本字符串连接成一个字符串？

本文末尾将提供解答。

### <a name="context"></a>上下文
上下文是需要了解的重要 DAX 概念之一。 DAX 中有两种上下文类型：行上下文和筛选上下文。 首先我们来看看行上下文。

**行上下文**

将行上下文想象成当前行是最简单的做法。 每当公式中含有应用了筛选器以识别表中某一行的函数时，都可应用此方法。 函数会应用所筛选的表中每行的固有行上下文。 这种类型的行上下文最常应用于度量值中。

**筛选器上下文**

筛选上下文比行上下文稍微更难理解。 可以非常轻松地将筛选器上下文视为：决定结果或值的计算中所应用的一个或多个筛选器。

筛选上下文并非原本就存在于行上下文中；而是另外应用到行上下文。 例如，若要进一步缩小要包括在计算中的值，可以应用筛选上下文，该筛选上下文不仅要指定行上下文，还要指定该行上下文中的特定值（筛选）。

可以在报表中轻松看到筛选上下文。 例如，当你将 TotalCost 添加到可视化效果，然后添加 Year 和 Region 时，你正在定义基于给定年份和区域来选择数据子集的筛选上下文。

为什么筛选上下文对 DAX 很重要？ 因为不仅可以通过将字段添加到可视化效果而轻松应用筛选上下文，还可以通过使用 ALL、RELATED、FILTER、CALCULATE 等函数，按照关系、其他度量值和列来定义筛选器，从而实现在 DAX 公式中应用筛选上下文。 例如，我们来看看名为 Store Sales 的度量值中的以下公式：

![Store Sales 度量值](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

为了更好地理解此公式，我们可以像处理其他公式一样对其进行分解：

此公式包含以下语法元素：

**A.** 度量值名称 Store Sales。 

**B.** 等号运算符 ( **=** ) 表示公式的开头。

**C.** **CALCULATE** 函数会在根据指定筛选器所修改的上下文中，作为参数来计算表达式。

**D.** 括号 () 会括住包含一个或多个参数的表达式。 

**E.** 同一表中作为表达式的 **[Total Sales]** 度量值。 Total Sales 度量值的公式为：=SUM(Sales[SalesAmount])。

**F.** 逗号 ( **,** ) 会分隔第一个表达式参数和筛选参数。

**G.** 完全限定的引用列为 **Channel[ChannelName]** 。 这是我们的行上下文。 此列中的每行各指定一个通道，例如 Store 或 Online。

**H.** 将特定值 Store 作为筛选器。  这是我们的筛选上下文。

此公式可确保仅针对将“Store”值用作筛选器的 Channel[ChannelName] 列中的行，计算 Total Sales 度量值所定义的销售额值  。

正如你所想象的，能够在公式内定义筛选上下文是多么巨大且强大的功能。 能够仅引用相关表中的特定值不过是其中一例。 如果你现在尚未完全理解上下文，请不要担心。 创建自己的公式时，你将可以更好地理解上下文以及其在 DAX 中非常重要的原因。

### <a name="context-quickquiz"></a>上下文快速测验
1. 上下文有哪两种类型？
2. 什么是筛选上下文？
3. 什么是行上下文？

本文末尾将提供解答。

## <a name="summary"></a>摘要
现在你对 DAX 中最重要的概念有了基本的认识，可以开始独立创建度量值的 DAX 公式。 DAX 确实有点难以理解，但是有许多资源可供你使用。 读完本文并对自己的几个公式进行试验之后，你可以进一步了解可帮助你解决业务问题的 DAX 概念和公式。 有许多 DAX 资源可供你使用；最重要的就是[数据分析表达式 (DAX) 参考](https://msdn.microsoft.com/library/gg413422.aspx)。

因为 DAX 在 Power Pivot 和 Analysis Services 表格模型等其他 Microsoft BI 工具中已存在数年，所以有许多有用信息。 你可以从 Microsoft 和顶级 BI 专业人员所提供的书籍、白皮书和博客中找到详细信息。 [TechNet 上的 DAX 资源中心 Wiki](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) 也是一个不错的起点。

### <a name="quickquiz-answers"></a>快速测验答案
语法：

1. 验证度量值并将其输入模型中。
2. 方括号 []。

函数：

1. 表和列。
2. 是。 公式可以包含多达 64 个嵌套函数。
3. [文本函数](https://msdn.microsoft.com/library/ee634938.aspx)。

上下文：

1. 行上下文和筛选上下文。
2. 计算中用于确定单个值的一个或多个筛选器。
3. 当前行。


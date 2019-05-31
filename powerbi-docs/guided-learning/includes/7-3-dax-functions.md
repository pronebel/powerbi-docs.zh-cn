---
ms.openlocfilehash: 06ee6ad7ade46d811c6340d905150c6dd3810c55
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273187"
---
DAX 拥有许多可用于成形、组织或分析数据的函数。 这些函数可以分为以下几个类别：

* **聚合**函数
* **计数**函数
* **逻辑**函数
* **信息**函数
* **文本**函数
* **日期**函数

与 Excel 类似，当开始向 Power BI Desktop **公式栏**键入公式时，会显示可用函数列表，以帮助你确定要选择的可用函数。 通过使用键盘上的**向上**和**向下**箭头键，可以突出显示任何可用函数，有关该函数的简要说明将会显示出来。

Power BI 会显示出与你当前所键入的字母相匹配的函数，因此，如果仅键入 S  ，那么列表中就会显示出以 S  开头的函数。 如果键入 Su  ，则列表中会显示名称中包含  字母序列 Su  的函数（不必以 Su  开头，只需包含该字母序列即可）。

![](media/7-3-dax-functions/dax-functions_1.png)

通过这种方式很容易试用 DAX 以及查找 Power BI 中可用的各种 DAX 函数。 你所要做的就是开始键入，Power BI 会全程帮助你完成。

知道了如何开始使用 DAX 公式后，让我们来依次看看各个函数类别。

## <a name="aggregation-functions"></a>聚合函数
DAX 提供多种**聚合**函数，包括以下常用函数：

* SUM
* AVERAGE
* MIN
* MAX
* SUMX（以及其他 *X* 函数）

这些函数仅适用于数字列，并通常一次只能聚合一列。

但是以 **X** 结尾的特殊聚合函数（例如 **SUMX** 则可同时处理多列。 这些函数循环访问表，并为每一行计算表达式。

## <a name="counting-functions"></a>计数函数
DAX 中经常使用的**计数**函数包括：

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

这些函数用来计数不同的元素，如非重复值、非空值和表行。

## <a name="logical-functions"></a>逻辑函数
DAX 中的**逻辑**函数包括：

* AND
* OR
* NOT
* IF
* IFERROR

这些特殊函数还可以用运算符  表达。 例如，在 DAX 公式中 **AND** 可以输入为（替换为） **&&** 。

如果公式中存在两个以上条件，则可以使用运算符（如 **&&** ），但在其他情况最好使用函数名本身（如 **AND**），以增强 DAX 代码可读性。

## <a name="information-functions"></a>信息函数
DAX 中的**信息**函数包括：

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

尽管这些函数在具体情况下有用，但提前知道列的数据类型，而不依赖这些函数来提供数据类型仍很有价值。

DAX 使用 **MAX** 和 **MIN** 函数来聚合  和比较  值。

## <a name="text-functions"></a>文本函数
DAX 中的**文本**函数包括：

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

这些**文本**函数与同名的 Excel 函数工作方式类似，因此，如果熟悉 Excel 如何处理文本函数，你就已经领先一步了。 如果不熟悉，则可以一直在 Power BI 上试用这些函数，以了解它们的详细行为方式。

## <a name="date-functions"></a>日期函数
DAX 包含以下**日期**函数：

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

尽管这些函数对于从日期  值中计算和提取信息很有用，但它们并不适用于使用日期表的时间智能。

> 视频内容由 [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax) 提供
> 
> 


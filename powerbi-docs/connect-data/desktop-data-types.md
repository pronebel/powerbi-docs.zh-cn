---
title: Power BI Desktop 中的数据类型
description: Power BI Desktop 中的数据类型
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: reference
ms.date: 05/06/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 5376bcf589c2193b408b705b814be69145ac52fe
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405459"
---
# <a name="data-types-in-power-bi-desktop"></a>Power BI Desktop 中的数据类型
本文介绍 Power BI Desktop 和数据分析表达式 (DAX) 中支持的数据类型。 

当你将数据加载到 Power BI Desktop 中时，它将尝试将源列的数据类型转换为能更好地支持更高效的存储、计算和数据可视化的数据类型。 例如，如果从 Excel 导入的值的列没有小数值，Power BI Desktop 会将整个数据列转换为整数数据类型，这能更好地存储整数。

这一概念很重要，因为某些 DAX 函数具有特殊的数据类型要求。 虽然在许多情况下 DAX 会为你隐式转换数据类型，但在某些情况下，它不会进行转换。  例如，如果 DAX 函数需要日期数据类型，而你的列的数据类型为文本，DAX 函数将不能正常工作。  因此，获取适用于列的正确数据类型是重要并且有用的。 隐式转换将会在本文的后一部分进行介绍。

## <a name="determine-and-specify-a-columns-data-type"></a>确定并指定列的数据类型
在 Power BI Desktop 中，你可以在查询编辑器（或数据视图和报表视图中）确定并指定列的数据类型：

**查询编辑器中的数据类型**

![在 Query 编辑器中显示的“数据类型”功能区的屏幕截图。](media/desktop-data-types/pbiddatatypesinqueryeditort.png)

**数据视图或报表视图中的数据类型**

![在“数据视图”中显示的“数据类型”功能区的屏幕截图。](media/desktop-data-types/pbiddatatypesindatareportview.png)

查询编辑器中的“数据类型”下拉列表中有两种数据类型在当前数据或报表视图中不存在，分别是：“日期/时间/时区”和“持续时间”。 当将使用这些数据类型的列加载到模型中，并在数据或报表视图中进行查看时，使用日期/时间/时区数据类型的列将会被转换为日期/时间，而使用持续时间数据类型的列将会被转换为十进制数字。

当前在查询编辑器外部不支持“二进制”数据类型。 在查询编辑器中，如果先将二进制文件转换为其他数据类型，然后再将它加载到 Power BI 模型，则可以在加载这些文件时使用该类型。 由于旧原因，它存在于数据视图和报表视图菜单中，但如果尝试将二进制列加载到 Power BI 模型，则可能会遇到错误。  

### <a name="number-types"></a>数字类型
Power BI Desktop 支持三种数字类型：

**十进制数** – 表示 64 位（八字节）浮点数。 它是最常见的数字类型，与你通常想象的数字相对应。  虽然十进制数类型被设计为处理带小数值的数字，但还可以处理整数。  十进制数类型可以处理从 -1.79E +308 到 -2.23E -308 的负值、0，以及从 2.23E -308 到 1.79E + 308 的正值。 例如，34、34.01 和 34.000367063 等数字都是有效的十进制数。 可以用十进制数类型表示的最大精度为 15 位数。 小数分隔符可出现在数字的任意位置。 十进制数类型与 Excel 存储其数字的方式相对应。

**定点十进制数** – 小数分隔符的位置是固定的。 小数分隔符右侧始终有四位数，并可以表示有意义的 19 位数。  它可以表示的最大值为 922,337,203,685,477.5807（正或负）。  定点十进制数类型在舍入可能会引发错误的情况下非常有用。  在处理许多带小数值的数字时，有时它们会累积并强制性地使数据稍有偏离。  由于小数分隔符右侧四位数其后的数字会被截断，定点十进制数可以帮助你避免这些类型的错误。   如果你熟悉 SQL Server，此数据类型可对应于 SQL Server 的十进制 (19,4)，或 Power Pivot 中的货币数据类型。 

**整数** – 表示 64 位（八字节）整数值。 由于它是一个整数，其小数位数右侧没有数字。 它支持 19 位数；从 -9,223,372,036,854,775,807 (-2^63+1) 到 9,223,372,036,854,775,806 (2^63-2) 的正数或负数。 它可以表示各种数值数据类型可能的最大精度。  与定点十进制数类型相同，在需要控制舍入的情况下，整数类型非常有用。 

> [!NOTE]
>  Power BI Desktop 数据模型支持 64 位整数值，但由于存在 JavaScript 限制，因此视觉对象可安全表达的最大数字是 9,007,199,254,740,991 (2^53-1)。 如果在数据模型中使用大于以上值的数字，可在将该数字添加到视觉对象前，通过计算减小其大小 
> 
>

### <a name="datetime-types"></a>日期/时间类型
Power BI Desktop 支持查询视图中的五种日期/时间数据类型。  在加载到模型的过程中，日期/时间/时区和持续时间都将被转换。 Power BI Desktop 数据模型只支持日期/时间，但它们可以独立地格式化为日期或时间。 

**日期/时间** – 表示日期和时间值。  实际上，日期/时间值是以十进制数类型进行存储的。  因此你实际上可以在这两种类型之间进行转换。   日期的时间部分存储为 1/300 秒 (3.33 ms) 的整数倍的分数。  支持 1900 年和 9999 年之间的日期。

**日期** – 仅表示日期（没有时间部分）。  转换为模型时，日期与表示分数值的带零日期/时间值相同。

**时间** – 仅表示时间（没有日期部分）。  转换为模型时，时间值与小数位数左侧没有数字的日期/时间值相同。

**日期/时间/时区** – 表示带时区偏移量的 UTC 日期/时间。  将这种数据加载到模型中时，它将被转换为日期/时间类型。 Power BI 模型不会根据用户的位置或区域设置等调整时区。如果在美国将值 09:00 加载到模型中，则无论在何处打开或查看报表，它都将显示为 09:00。 

**持续时间** – 表示时间的长度。 加载到模型中时，它将被转换为十进制数类型。  与十进制数类型相同，可将其添加到日期/时间字段，或从日期/时间字段中减去，并获取正确的结果。  与十进制数类型相同，你可以在显示度量值的可视化效果中轻松地使用它。

### <a name="text-type"></a>文本类型
**文本** - Unicode 字符数据字符串。 可以是字符串、数字或文本格式表示的日期。 其最大字符串长度为 268,435,456 Unicode 字符（256 Mega 字符）或 536,870,912 字节。

### <a name="truefalse-type"></a>True/False 类型
**True/False** – 为 True 或 False 的布尔值。

### <a name="blanksnulls-type"></a>空白/Null 类型
**空白** - DAX 中表示和替代 SQL Null 的数据类型。 你可以使用 [BLANK](/dax/blank-function-dax) 函数创建空白，并使用 [ISBLANK](/dax/isblank-function-dax) 逻辑函数对其进行测试。

### <a name="binary-data-type"></a>二进制数据类型

二进制数据类型可用于表示具有二进制格式的任何其他数据。 在查询编辑器中，如果先将二进制文件转换为其他数据类型，然后再将它加载到 Power BI 模型，则可以在加载这些文件时使用该类型。 Power BI 数据模型中不支持二进制列。 由于旧原因，它存在于数据视图和报表视图菜单中，但如果尝试将二进制列加载到 Power BI 模型，则可能会遇到错误。




> [!NOTE]
>  如果二进制列处于查询步骤的输出中，则尝试通过网关刷新数据可能会导致错误。 建议在查询的最后一个步骤中显式删除任何二进制列。    
> 

### <a name="table-data-type"></a>表数据类型
DAX 在许多函数中使用表数据类型，例如聚合和时间智能计算。 某些函数需要引用表；其他函数返回随后可用于输入到其他函数的表。 在某些需要表作为输入的函数中，你可以指定计算结果为表格的表达式；对于一些函数，则需要引用基础表。 有关特定函数的要求的详细信息，请参阅 [DAX 函数引用](/dax/dax-function-reference)。

## <a name="implicit-and-explicit-data-type-conversion-in-dax-formulas"></a>DAX 公式中的隐式和显式数据类型转换
关于用作输入和输出的数据类型，每个 DAX 函数都有特定的要求。 例如，某些函数要求对部分参数使用整数，而其他部分使用日期；另外一些函数则要求使用文本或表。

如果将列中与该函数所需数据类型不兼容的数据指定为参数，在很多情况下，DAX 将返回错误信息。 但是，只要可能，DAX 会尝试将数据隐式转换为所需的数据类型。 例如：

* 你可以以字符串的形式键入日期，DAX 会分析该字符串并尝试将其转换为 Windows 日期和时间格式之一。
* 你可以添加 TRUE+1 并获得结果 2，因为 TRUE 被隐式转换为数字 1，并执行 1+1 的操作。
* 如果在两个列中添加值，其中一个值恰好以文本方式表示 ("12")，而另一个值以数字方式表示 (12)，DAX 会将字符串隐式转换为数字，然后执行加法并获得数值结果。 下面的表达式将返回 44: = "22" + 22。
* 如果尝试连接两个数字，Excel 会将其以字符串表示并进行连接。 下面的表达式将返回 "1234": = 12 & 34。

### <a name="table-of-implicit-data-conversions"></a>隐式数据转换表
执行的转换的类型由运算符确定，它在执行所请求的操作之前会将值转换为所需的值。 这些表列出了运算符，并指示当其与交叉行内的数据类型配对时，对列中每种数据类型执行的转换。

> [!NOTE]
>  这些表中不包含文本数据类型。 当数字以文本格式表示时，在某些情况下，Power BI 将尝试确定数字类型并将其表示为数字。
> 
> 

**加法 (+)**

| 运算符 (+) | INTEGER | CURRENCY | REAL | 日期/时间 |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |日期/时间 |
| CURRENCY |CURRENCY |CURRENCY |REAL |日期/时间 |
| REAL |REAL |REAL |REAL |日期/时间 |
| 日期/时间 |日期/时间 |日期/时间 |日期/时间 |日期/时间 |

例如，如果在加法运算中将实数与货币数据结合使用，两个值都会转换为 REAL，并且返回的结果为 REAL。

**减法 (-)**

下表中，行标题是被减数（左侧），列标题是减数（右侧）。

| 运算符 | INTEGER | CURRENCY | REAL | 日期/时间 |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |CURRENCY |REAL |REAL |
| REAL |REAL |REAL |REAL |REAL |
| 日期/时间 |日期/时间 |日期/时间 |日期/时间 |日期/时间 |

例如，如果在减法运算中将日期与其他任何数据类型结合使用，两个值都会转换为日期，返回的值也会是日期。

> [!NOTE]
>    数据模型还支持一元运算符 - （负号），但此运算符不会更改操作数的数据类型。
> 
> 

**乘法 (*)**

| 运算符 (*) | INTEGER | CURRENCY | REAL | 日期/时间 |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |INTEGER |
| CURRENCY |CURRENCY |REAL |CURRENCY |CURRENCY |
| REAL |REAL |CURRENCY |REAL |REAL |

例如，如果在乘法运算中将整数与实数结合使用，两个数字都会转换成为实数，并且返回的值也是 REAL。

**除法 (/)**

下表中，行标题是分子（左侧），列标题是分母（右侧）。

| 运算符 (/)（行/列） | INTEGER | CURRENCY | REAL | 日期/时间 |
| --- | --- | --- | --- | --- |
| INTEGER |REAL |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |REAL |CURRENCY |REAL |
| REAL |REAL |REAL |REAL |REAL |
| 日期/时间 |REAL |REAL |REAL |REAL |

例如，如果在除法运算将整数与货币值结合使用，两个值都会转换为实数，并且结果也是实数。

### <a name="comparison-operators"></a>比较运算符
在比较表达式中，布尔值被视为大于字符串值，字符串值被视为大于数字或日期/时间值；数字和时间值被视为同级。 布尔值或字符串值不执行任何隐式转换；BLANK 或空白值会被转换为 0/""/false，具体取决于其他进行比较的值的数据类型。

下面的 DAX 表达式对此行为进行了说明：

=IF(FALSE()\>"true","Expression is true", "Expression is false")，返回 "Expression is true"

=IF("12"\>12,"Expression is true", "Expression is false")，返回 "Expression is true"

=IF("12"=12,"Expression is true", "Expression is false")，返回 "Expression is false"

针对数字或日期/时间类型所执行的隐式转换如下表所述：

| 比较运算符 | INTEGER | CURRENCY | REAL | 日期/时间 |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |CURRENCY |REAL |REAL |
| REAL |REAL |REAL |REAL |REAL |
| 日期/时间 |REAL |REAL |REAL |日期/时间 |

### <a name="handling-blanks-empty-strings-and-zero-values"></a>空白、空字符串和零值的处理
在 DAX 中，NULL、空值、空单元格或缺失值均以相同的新值类型 BLANK 表示。 你可以使用 BLANK 函数创建空白，并使用 ISBLANK 函数对其进行测试。

空白在运算中的处理方式（例如加法或连接）取决于单个函数。 下表总结了 DAX 和 Microsoft Excel 公式对空白的处理方式的区别。

| 表达式 | DAX | Excel |
| --- | --- | --- |
| BLANK + BLANK |BLANK |0（零） |
| BLANK + 5 |5 |5 |
| BLANK * 5 |BLANK |0（零） |
| 5/BLANK |无穷大 |Error |
| 0/BLANK |NaN |Error |
| 空白/空白 |BLANK |Error |
| FALSE OR BLANK |FALSE |FALSE |
| FALSE AND BLANK |FALSE |FALSE |
| TRUE OR BLANK |TRUE |TRUE |
| TRUE AND BLANK |FALSE |TRUE |
| BLANK OR BLANK |BLANK |Error |
| BLANK AND BLANK |BLANK |Error |

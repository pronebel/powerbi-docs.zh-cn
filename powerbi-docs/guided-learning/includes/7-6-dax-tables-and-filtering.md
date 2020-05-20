---
ms.openlocfilehash: 5bc0d3bbfb2c2b67b56e6406646f6131a360b97d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799700"
---
**DAX** 和 Excel 公式语言的一个显著区别是 DAX 允许在表达式之间传递整个表  ，而不仅限于单个值。 DAX 的一项强大功能是允许你在其表达式中筛选表格，然后使用筛选的值集。

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

通过 DAX，你可以创建全新的计算表，然后像处理其他表格一样处理它们 - 包括在这些表和存在于你的数据模型中的其他表之间建立关系。

## <a name="dax-table-functions"></a>DAX 表函数
DAX 提供一套丰富的**表**函数，包括：

* FILTER
* 全部
* VALUES
* DISTINCT
* RELATEDTABLE

这些函数返回一个完整的表，而不是一个值。 通常，你会在进一步的分析中将**表**函数的结果（而不是返回的一个最终值）作为更大的表达式的一部分使用。 值得注意的是，使用表函数时，其结果将继承其列的关系。

可以在表达式中混合使用表函数，前提是每一个表达式只使用一个表并返回一个表。 例如下面的 DAX 表达式：

    FILTER (ALL (Table), Condition)

该表达式将筛选整个 *表* ，而忽略当前筛选的任何内容。

DISTINCT 函数返回某一列的各个不同值，这些值在当前上下文中也可见。 因此，以上述 DAX 表达式为例，在表达式中使用“ALL”会忽略筛选，而使用“DISTINCT”替换“ALL”则可查看筛选  。

## <a name="counting-values-with-dax"></a>使用 DAX 对值进行计数
Power BI 报表生成人员想要回答的一个常见问题是：

* 我可以对该列设置多少个值？

如果你面前出现一个表，那么这是很好回答的简单问题，但是 DAX 会采用其他方式来计算该值，尤其是在表之间存在关系时。

例如，Power BI 和 DAX 包含未正确建立交叉索引的值。 如果传入关系已损坏，DAX 会将新行添加到每个字段都有空值的相关表中，并将其链接到未建立索引的行，以确保引用的完整性。 如果函数包含空白行（这在使用 **ALL** 时经常出现），那么列的返回值数目中将包含这些空白行。

你还可以使用 DAX 函数创建整个计算表。 使用 DAX 创建的计算表要求有一个**名称**和一个**表**函数。 计算的表的使用，包括建立关系，和任何其他表一样。

> 视频内容由 [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax) 提供
> 
> 


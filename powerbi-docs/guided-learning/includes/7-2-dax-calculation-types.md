---
ms.openlocfilehash: 4ea1b2141cf9a072f11a3a62789c7c0ec5b500a4
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799696"
---
你可以使用 DAX 创建的两个主要的计算：

* **计算列**
* **计算度量值**

在深入探讨创建上述二者之一前，最好牢固掌握用于表和列的 DAX 语法，你将在创建**计算列**或**计算度量值**时使用它。

## <a name="dax-table-and-column-name-syntax"></a>DAX 表名和列名语法
无论你要创建新的列还是度量值，都要务必了解 DAX 中的表名的一般格式：

    'Table Name'[ColumnName]

如果表名（如上所示）中有空格，那么表名周围的单引号则是必需的。 如果表名没有空格，则可以省略单引号，因此语法如下所示：

    TableName[ColumnName]

下图显示了在 Power BI 中创建的一个 DAX 公式：

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

你也可以完全省略表名而只使用列名，但这对于写入清晰的函数（从而，对于清晰的 DAX 代码）来说不是一个好的做法。 列名称必须始终包含方括号。

最佳做法是始终  执行以下操作：

* 表名中无空格
* 始终在公式中包含表名（不要将其省略掉，即使 DAX 允许）

## <a name="creating-calculated-columns"></a>创建计算列
当你要划分或筛选值，或者要对表中的每一行进行计算时，**计算列**非常有用。

通过从“建模”  选项卡选择“新建列”  ，你可以在 Power BI Desktop 中创建计算列。最好采用“数据”  视图（而不是“报表”  或“关系”  视图），因为你可以看到创建的新列以及“编辑栏”  填充并准备好用于 DAX 公式。

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

一旦你选择“新建列”  按钮，“编辑栏”  将填充基本列名（当然，你可以更改以使其适合你的公式）和 **=** 运算符，新列将显示在数据网格中，如下图所示。

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

计算列所需的元素如下：

* 新的列名
* 至少一个函数或表达式

如果在计算列公式中引用一个表或列，则无需在表中指定行 -- Power BI 会为每个计算的当前行计算列。

## <a name="creating-calculated-measures"></a>创建计算度量值
当你计算百分比或比率，或者需要复杂的聚合时，使用**计算度量值**。 若要创建使用 DAX 公式的度量值，请从“建模”  选项卡选择“新建度量值”  按钮。同样，最好采用 Power BI Desktop 的“数据”  视图，因为它显示“编辑栏”  并使写入 DAX 公式更加容易。

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

对于**度量值**，你会看到一个有度量值名称的新的度量值图标出现在“字段”  窗格中。 “编辑栏”  再次被 DAX 公式名称（这次，带有度量值）填充。

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

计算度量值的必需元素与计算列的必需元素是相同的：

* 新的度量值名称
* 至少一个函数或表达式

> 视频内容由 [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax) 提供
> 
> 


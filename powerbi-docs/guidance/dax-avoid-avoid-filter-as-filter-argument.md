---
title: DAX：避免使用 FILTER 作为筛选器参数
description: 有关使用 FILTER 函数作为筛选器参数的指南。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/30/2019
ms.openlocfilehash: 74ddac5a3ac2fa5e6e0fae9f3fdf5c7f79ba22d3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088571"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX：避免使用 FILTER 作为筛选器参数

作为数据建模者，通常你将编写需要在修改的筛选器上下文中计算的 DAX 表达式。 例如，你可以编写一个度量值定义来计算“高利润产品”的销售量。 本文稍后将介绍此计算。

> [!NOTE]
> 本文特别适用于应用筛选器导入表的模型计算。

[CALCULATE](/dax/calculate-function-dax) 和 [CALCULATETABLE](/dax/calculatetable-function-dax) DAX 函数是重要且有用的函数。 它们能让你编写删除或添加筛选器，或修改关系路径的计算。 这是通过在筛选器参数中传递完成的，筛选器参数是布尔表达式、表表达式或特殊筛选器函数。 我们仅在本文中讨论布尔和表表达式。

请考虑以下度量值定义，该定义使用表表达式计算红色产品销售量。 它将代替任何已应用于“产品”表的筛选器  。

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

CALCULATE 函数接受 [FILTER ](/dax/filter-function-dax)DAX 函数返回的表表达式，该函数将为“产品”表的每一行计算其筛选器表达式  。 它得出了正确的结果 - 红色产品的销售量结果。 但是，使用布尔表达式可以更有效地实现此目的。

下面是改进后的度量值定义，它使用布尔表达式而不是表表达式。 [KEEPFILTERS](/dax/keepfilters-function-dax) DAX 函数可确保任何应用到“颜色”  列的现有筛选器会保留，不会被覆盖。

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

建议尽量将筛选器参数作为布尔表达式传递。 这是因为“导入模型”表是内存中的列存储。 它们经过显示优化，可通过此方式高效筛选列。

但是，布尔表达式作为筛选器参数使用时，会存在一些限制。 它们：

- 不能将列与其他列进行比较
- 不能引用度量值
- 不能使用嵌套 CALCULATE 函数
- 不能使用扫描或返回表的函数

这意味着需要使用表表达式来满足更复杂的筛选要求。

现在请考虑一个不同度量值定义。

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

“高利润产品”的定义是标价超过其标准成本两倍的产品  。 在此示例中，必须使用 FILTER 函数。 这是因为筛选表达式对于布尔表达式而言过于复杂。

下面再提供一个示例。 这一次的要求是计算销售额，但是仅针对获得利润的月份。

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

在此示例中，依旧须使用 FILTER 函数。 这是因为需要评估“利润”度量值，以删除没有获得利润的月份  。 将布尔表达式作为筛选器参数使用时，不能在其中使用度量值。

## <a name="recommendations"></a>建议

为了获得最佳性能，建议尽量使用布尔表达式作为器筛选参数。

因此，只有在需要时才使用 FILTER 函数。 可以使用它来执行筛选器的复杂列比较。 这些列比较可能涉及到：

- 度量值
- 其他列
- 使用 [OR](/dax/or-function-dax) DAX 函数，或 OR 逻辑运算符 (||)

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- [筛选器函数 (DAX)](/dax/filter-function-dax)
- 学习路径：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)
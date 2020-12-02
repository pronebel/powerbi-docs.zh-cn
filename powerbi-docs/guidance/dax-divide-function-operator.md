---
title: DAX：DIVIDE 函数与除法运算符 (/)
description: 关于何时使用 DAX DIVIDE 函数的指导。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/09/2019
ms.openlocfilehash: ece1c0d939ef521b20142acb753de7b7554e870a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394120"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX：DIVIDE 函数与除法运算符 (/)

作为数据建模者，通过编写 DAX 表达式使分子分母相除时，可使用 [DIVIDE](/dax/divide-function-dax) 函数或除法运算符（正斜杠“/”）。

使用 DIVIDE 函数时，必须传递分子和分母表达式。 或者，可传递一个表示替代结果的值  。

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

按照设计，DIVIDE 函数可自动处理除数为零的情况。 如果无替代结果传入且分母为零或 BLANK，此函数返回 BLANK。 如果已有替代结果传入，则函数会返回替代结果而不是 BLANK。

DIVIDE 函数非常方便，因为它使表达式无需首先检测分母的值。 与 [IF](/dax/if-function-dax) 函数相比，该函数检测分母值时的性能更优。 性能提升非常重要，因为检查除数是否为零会产生大量费用。 进一步使用 DIVIDE 函数可以使表达式更为简洁顺畅。

## <a name="example"></a>示例

虽然以下度量值表达式生成一个安全除法运算，但使用了四个 DAX 函数。

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

该度量值表达式得出相同的结果，但更高效更顺畅。

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>建议

只要分母是可能返回零或 BLANK 的表达式，都建议使用 DIVIDE 函数  。

如果分母是一个常数值，则建议使用除法运算符。 在这种情况下，除法运算一定会成功，而且由于避免了不必要的检测，表达式性能更好。

仔细考虑 DIVIDE 函数是否应该返回替代值。 对于度量值，返回 BLANK 时通常设计更佳。 返回“空白”更好，因为在汇总为 BLANK 时报表视觉对象默认会取消分组。 这使视觉对象可专注于处理存在数据的组。 必要时，可启用[显示无数据的项目](../create-reports/desktop-show-items-no-data.md)选项，将视觉对象配置为显示筛选器上下文中所有的组（即返回值或 BLANK 的组）。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- 学习路径：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)
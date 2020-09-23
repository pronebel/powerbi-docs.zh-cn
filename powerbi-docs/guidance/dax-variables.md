---
title: DAX：使用变量改进公式
description: 关于在 DAX 表达式中使用变量的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: cd2f71a2d96a0057e3da5ee7e02bbb05498c6065
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965198"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX：使用变量改进公式

作为数据建模人员，编写和调试某些 DAX 计算可能会很困难。 复杂计算的要求通常包括编写复合表达式或复杂表达式。 复合表达式可能涉及使用多种嵌套函数，并且可能会重用表达式逻辑。

在 DAX 公式中使用变量有助于编写复杂而高效的计算。 变量可以：

- [提高性能](#improve-performance)
- [提高可读性](#improve-readability)
- [简化调试](#simplify-debugging)
- [降低复杂性](#reduce-complexity)

在本文中，我们将通过使用同比 (YoY) 销售增长的示例度量值来演示前三个优势。 （YoY 销售增长公式为：现年销售额减去去年同期销售额，再除以去年同期销售额。  ）

让我们从下面的度量值定义开始。

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

该度量值将产生正确的结果，不过还是让我们看看如何对其进行改进。

## <a name="improve-performance"></a>提高性能

请注意，该公式重复了计算“去年同期”的表达式。 此公式效率很低，因为它要求 Power BI 计算两次相同的表达式。 使用变量可以更高效地进行度量定义。

下面的度量值定义表示一项改进。 它使用表达式将“去年同期”结果分配给名为 SalesPriorYear 的变量  。 然后，在 RETURN 表达式中使用该变量两次。

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

该度量值将继续生成正确的结果，并在大约一半的查询时间内完成此操作。

## <a name="improve-readability"></a>提高可读性

在前面的度量值定义中，请注意变量名称的选择如何使 RETURN 表达式更易于理解。 该表达式简短而具有自述性。

## <a name="simplify-debugging"></a>简化调试

变量还有助于调试公式。 要测试分配给变量的表达式，可以临时重写 RETURN 表达式以输出变量。

以下度量值定义仅返回 SalesPriorYear 变量  。 请注意它注释掉预期 RETURN 表达式的方式。 通过此方法，可以在调试完成后轻松将其还原。

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>降低复杂性

在较早版本的 DAX 中，尚不支持变量。 需要使用引入新筛选器上下文的复杂表达式来使用 [EARLIER](/dax/earlier-function-dax) 或 [EARLIEST DAX](/dax/earliest-function-dax) 函数，以引用外部筛选器上下文。 遗憾的是，数据建模人员发现这些功能难以理解和使用。

变量始终在应用 RETURN 表达式的筛选器之外进行计算。 出于此原因，在修改后的筛选器上下文中使用变量时，实现的结果与 EARLIEST 函数相同。 因此，可以避免使用 EARLIER 或 EARLIEST 函数。 这意味着你现在可以编写较简单且更易于理解的公式。

请考虑以下添加到 Subcategory 表中的计算列定义  。 它基于 Subcategory Sales 列值评估每个产品子类别的排名  。

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

EARLIER 函数用于引用当前行上下文中的 Subcategory Sales 列值   。

可以通过使用变量而不是 EARLIER 函数来改进计算的列定义。 CurrentSubcategorySales 变量将 Subcategory Sales 列值存储在当前行上下文中，并且 RETURN 表达式在修改的筛选器上下文中使用它    。

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- [VAR](/dax/var-dax) DAX 文章
- 学习路径：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)
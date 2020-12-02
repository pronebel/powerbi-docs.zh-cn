---
title: DAX：适当使用错误函数
description: 关于何时使用 DAX 错误函数的指导。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: fd071fad18580074ce42c990db7f048ce2ad8c2d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394028"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX：适当使用错误函数

作为数据建模者，编写可能引发评估时间错误的 DAX 表达式时，可以考虑使用两个有用的 DAX 函数。

- [ISERROR](/dax/iserror-function-dax) 函数，它采用单个表达式并在该表达式导致错误时返回 TRUE。
- [IFERROR](/dax/iferror-function-dax) 函数，它采用两个表达式。 如果第一个表达式导致错误，则返回第二个表达式的值。 事实上，这样可以使将 ISERROR 函数嵌套在 [IF](/dax/if-function-dax) 函数内的实现更为优化。

但是，尽管这些函数可能会很有帮助，并有助于编写易于理解的表达式，但它们也会显著降低计算的性能。 出现这种情况是因为这些函数会增加所需的存储引擎扫描次数。

大多数评估时间错误是由于意外的空白或零值或无效的数据类型转换而导致的。

## <a name="recommendations"></a>建议

最好避免使用 ISERROR 和 IFERROR 函数。 而应在开发模型和编写表达式时应用防御策略。 策略可以包括：

- **确保将质量数据加载到模型中：** 使用 Power Query 转换可删除或替换无效或缺失的值，以及设置正确的数据类型。 出现错误（如数据转换无效）时，Power Query 转换还可用于筛选行。

    还可以通过将模型列“可以为 Null”  属性设置为“关闭”来控制数据质量，这将导致在遇到空白时无法进行数据刷新。 如果出现此错误，则成功刷新后加载的数据将保留在表中。
- **使用 IF 函数：** IF 函数逻辑测试表达式可确定是否会出现错误结果。 请注意，与 ISERROR 和 IFERROR 函数一样，此函数可能会导致额外的存储引擎扫描，但其性能可能更高，因为不会引发错误。
- **使用容错函数：** 某些 DAX 函数将测试并弥补错误情况。 这些函数允许你输入将返回的替代结果。 [DIVIDE](/dax/divide-function-dax) 函数是其中一个示例。 有关此函数的其他指导，请阅读 [DAX：DIVIDE 函数与除法运算符 (/)](dax-divide-function-operator.md) 一文。

## <a name="example"></a>示例

以下度量值表达式测试是否会引发错误。 将在此实例中返回空白（如果不提供具有 value-if-false 表达式的 IF 函数）。

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

该度量值表达式的下一版本已通过使用 IFERROR 函数代替 IF 和 ISERROR 函数得以改进。

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

但是，该度量值表达式的最终版本得出相同的结果，不过更高效更顺畅。

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)

- 学习路径：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)
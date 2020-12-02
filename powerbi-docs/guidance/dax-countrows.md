---
title: DAX：使用 COUNTROWS 而不是 COUNT
description: 关于何时使用 COUNTROWS 函数的指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 1a2b8c6450cfd855a0018fb64dd385a0db6e350f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394189"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX：使用 COUNTROWS 而不是 COUNT

你作为数据建模者，有时可能需要编写包含统计表行数的 DAX 表达式。 该表可以是模型表或返回表的表达式。

可以通过两种方法满足上述要求。 可以使用 [COUNT](/dax/count-function-dax) 函数来统计列值，也可以使用 [COUNTROWS](/dax/countrows-function-dax) 函数统计表行数。 假设所统计的列不包含 BLANK，则两个函数将获得相同的结果。

下面的度量值定义显示一个示例。 它计算“OrderDate”列值的数量  。

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

假设每个销售订单中“Sales”表粒度为一行，并且“OrderDate”列不包含 BLANK，则度量值将返回正确的结果   。

不过，更好的解决方法是使用下面的度量值定义。

```dax
Sales Orders =
COUNTROWS(Sales)
```

第二个度量值定义更好的原因有三个：

- 此方法更高效，因此它表现得更好。
- 它不考虑表的任何列中包含的 BLANK。
- 公式的意图更加明确，达到自我描述的程度。

## <a name="recommendation"></a>建议

当对表的行进行计数时，我们建议始终使用 COUNTROWS 函数。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- 学习路径：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)
---
title: DAX：使用 SELECTEDVALUE 而不是 VALUES
description: 关于何时使用 SELECTEDVALUE 函数的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 6aef2c06cc62668ea7dea9fe404e294d1a5faa93
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700469"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX：使用 SELECTEDVALUE 而不是 VALUES

作为数据建模人员，有时可能需要编写 DAX 表达式来测试列是否按特定值进行筛选。

在较早版本的 DAX 中，通过使用涉及三个 DAX 函数的模式可以安全地实现此要求。 函数为 [IF](/dax/if-function-dax)、[HASONEVALUE](/dax/hasonevalue-function-dax) 和 [VALUES](/dax/values-function-dax)。 下面的度量值定义显示一个示例。 它计算销售税金额，但仅限于面向澳大利亚客户的销售。

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

在此示例中，仅当单个值筛选 Country-Region 列时，HASONEVALUE 函数才返回 TRUE  。 如果为 TRUE，VALUES 函数将与文本“澳大利亚”进行比较。 VALUES 函数返回 TRUE 时，“Sales”度量值将乘以 0.10（表示 10%）  。 如果 HASONEVALUE 函数返回 FALSE（因为有多个值对列进行筛选），则第一个 IF 函数将返回 BLANK。

使用 HASONEVALUE 是一项防御性技术。 这是必需的，因为可能有多个值对 Country-Region 列进行筛选  。 在这种情况下，VALUES 函数将返回一个包含多行的表。 将包含多行的表与标量值进行比较会导致错误。

## <a name="recommendation"></a>建议

建议使用 [SELECTEDVALUE](/dax/selectedvalue-function) 函数。 该函数可得出与本文描述的模式相同的结果，但更高效、更顺畅。

借助 SELECTEDVALUE 函数现可对示例度量值定义进行重写。

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> 可以将替代结果值传递给 SELECTEDVALUE 函数  。 如果没有筛选器（或多个筛选器）应用于该列，则返回备用结果值。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)

---
title: DAX：列和度量值引用
description: 有关在 DAX 表达式中引用列和度量值的指南。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/18/2019
ms.openlocfilehash: 3d9f4ea374783b90705a8ec5644d67ddc5d1168b
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088525"
---
# <a name="dax-column-and-measure-references"></a>DAX：列和度量值引用

作为数据建模器，DAX 表达式将引用模型列和度量值。 列和度量值始终与模型表关联，但这些关联是不同的。 因此，我们对如何在表达式中对它们进行引用有不同的建议。

## <a name="columns"></a>列

列是表级别对象，列名称在表中必须是唯一的。 因此，可以在模型中多次使用相同的列名称，前提是它们属于不同的表。 还有一个规则：列名称不能与同一个表中存在的度量值名称或层次结构名称同名。

通常，DAX 不会对列强制使用完全限定的引用  。 完全限定的引用表示表名称在列名称之前。

下面是仅使用列名称引用的一个计算列定义示例。 “销售额”和“成本”列都属于名为“订单”的表    。

```dax
Profit = [Sales] - [Cost]
```

可以用完全限定的列引用来重写相同的定义。

```dax
Profit = Orders[Sales] - Orders[Cost]
```

但有时，当 Power BI 检测到歧义时，将要求使用完全限定的列引用。 输入公式时，红色的波浪和错误消息会发出警报。 此外，某些 DAX 函数（如 [LOOKUPVALUE](/dax/lookupvalue-function-dax) DAX 函数）要求使用完全限定的列。

建议始终完全限定列引用。 [建议](#recommendations)部分中列明了原因。

## <a name="measures"></a>度量值

度量值是模型级别对象。 因此，度量值名称在模型中必须是唯一的。 但是，在“字段”窗格中，报表作者将看到与单个模型表关联的每个度量值  。 此关联是出于装饰原因设置的，你可以通过设置度量值的“主表”属性来对其进行配置  。 有关详细信息，请参阅 [Power BI Desktop 中的度量值（组织度量值）](../transform-model/desktop-measures.md#organizing-your-measures)。

可以在表达式中使用完全限定的度量值。 DAX intellisense 甚至会提供建议。 但是，没必要这样做，也不建议这样做。 如果更改了度量值的主表，则使用完全限定的度量值引用的任何表达式都将中断。 然后需要对每个中断的公式进行编辑，以删除（或更新）度量值引用。

建议不要限定度量值引用。 [建议](#recommendations)部分中列明了原因。

## <a name="recommendations"></a>建议

我们的建议简单易记：

- 始终使用完全限定的列引用
- 一定不要使用完全限定的度量值引用

原因如下：

- **公式输入**：将接受表达式，因为没有任何不明确的引用需要解析。 此外，你还将满足需要完全限定的列引用的 DAX 函数的要求。
- **稳定性**：即使更改了度量值主表属性，表达式仍将继续工作。
- **可读性**：表达式是快速的且易于理解，你将根据是否为完全限定来快速确定它是列还是度量值。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- 学习路径：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)
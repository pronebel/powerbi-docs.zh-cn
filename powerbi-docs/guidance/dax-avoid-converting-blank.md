---
title: DAX：不要将空白转换为值
description: 关于将 BLANK 转换为值的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700377"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX：不要将空白转换为值

作为数据建模者，你在编写度量值表达式时，可能会遇到无法返回某个有意义的值的情况。 在这些情况下，你可能会想返回一个值，比如零。 建议认真考虑该设计是否高效实用。

请考虑以下度量值定义，它显式地将 BLANK 结果转换为零。

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

请考虑另一个度量值定义，它也将 BLANK 结果转换为零。

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

[DIVIDE](/dax/divide-function-dax) 函数将“Profit”度量值除以“Sales”度量值   。 如果结果为零或 BLANK，则返回第三个参数，即备用结果（可选）。 在此示例中，由于将零作为备用结果传递，因此保证了度量值总会返回值。

这些度量值的设计效率低下，导致报表设计不佳。

当它们被添加到报表视觉对象时，Power BI 试图在筛选器上下文中检索所有分组。 计算和检索大型查询结果通常会导致报表呈现速度缓慢。 每个示例度量值都会有效地将稀疏计算变为稠密计算，迫使 Power BI 使用更多内存（与必需的内存相比）。

而且，过多分组常常会使报表用户不堪重负。

让我们看看将“Profit Margin”度量值添加到表视觉对象后会发生什么情况，按客户分组显示  。

![表视觉对象有三列：Customer、Sales 和 Profit Margin。 该表显示了大概 10 行数据，但垂直滚动条表明还有很多行没有显示出来。 “Sales”列不显示任何值。 “Profit Margin”列仅显示零。](media/dax-avoid-converting-blank/table-visual-poor.png)

该表视觉对象显示的行数巨大。 （实际上模型中有 18484 名客户，因此表尝试显示所有客户。）请注意，视图中的客户达到没有任何销售量。 然而，由于“Profit Margin”度量值始终返回值，因此会显示没有销售量的客户  。

> [!NOTE]
> 如果视觉对象中要显示的数据点过多，Power BI 可能会使用数据缩减策略来删除或汇总大型查询结果。 有关更多信息，请查看[数据点限制和策略（按视觉对象类型）](../visuals/power-bi-data-points.md)。

我们来看一看改进“Profit Margin”度量值定义后会发生什么情况  。 仅当“Sales”度量值不为 BLANK（或零）时，它才会返回值  。

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

表视觉对象现在仅显示当前筛选器上下文中有实际销售额的客户。 改进后的度量值为报表用户提供了更高效、更实用的体验。

![同一个表视觉对象现在显示四行数据。 每一行都表示一个具有销售值的客户，且 Profit Margin 的值非零。](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> 必要时，可启用[显示无数据的项目](../desktop-show-items-no-data.md)选项，将视觉对象配置为显示筛选器上下文中所有的组（即返回值或 BLANK 的组）。

## <a name="recommendation"></a>建议

我们建议无法返回某个有意义的值时，度量值就返回 BLANK。

这种设计方法非常有效，可使 Power BI 更快地呈现报表。 此外，返回 BLANK 更好，因为在汇总为 BLANK 时报表视觉对象默认会取消分组。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)

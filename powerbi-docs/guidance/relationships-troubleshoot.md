---
title: 关系故障排除指南
description: 模型关系问题排查指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: e8f76bf1e1947815176a1b24be2b758489093071
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418523"
---
# <a name="relationship-troubleshooting-guidance"></a>关系故障排除指南

本文面向使用 Power BI Desktop 的数据建模者。 它指导你如何排查在开发模型和报表时可能会遇到的具体问题。

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>故障排除清单

如果报表视觉对象配置为使用两个（或更多）表中的字段，但它不显示正确的结果（或任何结果），那么问题可能与模型关系有关。

在这种情况下，需要遵循下面的常规故障排除清单。 可以逐个执行清单中的步骤，直到确定一个或多个问题所在。

1. 将视觉对象切换为表或矩阵，或打开“查看数据”窗格：在可以看到查询结果时，更容易排查问题
1. 如果查询结果为空，请切换到“数据”视图：验证表是否已加载数据行
1. 切换到“模型”视图：在其中可以轻松查看关系，并快速确定关系属性
1. 验证表之间是否存在关系
1. 验证基数属性是否已正确配置：如果“多”端列当前包含唯一值，且已被错误地配置为“一”端，那么基数属性可能不正确
1. 验证关系是否处于活动状态（实线）
1. 验证筛选器方向是否支持传播（解释箭头）
1. 验证是否关联了正确的列：选择关系或将光标悬停在上方可显示关联列
1. 验证关联列的数据类型是否相同或至少兼容：可以将文本列与整数列关联，但筛选器找不到任何要传播的匹配值
1. 切换到“数据”视图，并验证能否在关联列中找到匹配值

## <a name="troubleshooting-guide"></a>故障排除指南

下面列出了问题和可能解决方案。

|问题|可能的原因|
|---------|---------|
|视觉对象不显示结果|- 模型尚未加载数据<br />- 筛选器上下文中没有数据<br />- 行级别安全性已强制执行<br />- 表之间不传播关系：请遵循上述清单 <br />- 行级别安全性已强制执行，但未启用传播双向关系：请参阅[结合使用行级别安全性 (RLS) 与 Power BI Desktop](../create-reports/desktop-rls.md)|
|视觉对象对每个分组显示相同的值 |- 关系不存在<br />- 表之间不传播关系：请遵循上述清单 |
|视觉对象显示结果，但结果不正确|- 视觉对象未正确配置<br />- 度量值逻辑不正确<br />- 需要刷新模型数据<br />- 源数据不正确<br />- 关系列未正确关联（例如，ProductID  列映射到 CustomerID  ）<br />- 这是两个 DirectQuery 表之间的关系，关系的“一”端列包含重复值|
|出现 BLANK 分组或切片器/筛选器项，但源列不包含 BLANK|- 这是一种常规关系，“多”端列包含的值不存储在“一”端列中：请参阅 [Power BI Desktop 中的模型关系（常规关系）](../transform-model/desktop-relationships-understand.md#regular-relationships)<br />- 这是常规一对一关系，关联列包含 BLANK—请参阅 [Power BI Desktop 中的模型关系（常规关系）](../transform-model/desktop-relationships-understand.md#regular-relationships)<br />- 非活动关系“多”端列存储 BLANK，或包含的值不存储在“一”端中|
|视觉对象缺少数据|- 应用的筛选器不正确/不符合预期<br />- 行级别安全性已强制执行<br />- 这是一种有限关系，关联列包含 BLANK，或存在数据完整性问题：请参阅 [Power BI Desktop 中的模型关系（有限关系）](../transform-model/desktop-relationships-understand.md#limited-relationships)<br />- 这是两个 DirectQuery 表之间的关系，关系配置为[假定引用完整性](../transform-model/desktop-relationships-understand.md#assume-referential-integrity)，但存在数据完整性问题（关联列中的值不匹配）|
|行级别安全性未正确强制执行|- 表之间不传播关系：请遵循上述清单 <br />- 行级别安全性已强制执行，但未启用传播双向关系：请参阅[结合使用行级别安全性 (RLS) 与 Power BI Desktop](../create-reports/desktop-rls.md)|
|||

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI Desktop 中的模型关系](../transform-model/desktop-relationships-understand.md)
- 是否有任何问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

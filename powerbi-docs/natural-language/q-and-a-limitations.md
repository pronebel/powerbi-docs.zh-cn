---
title: Power BI 问答的限制
description: Power BI 问答现有的限制
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
ms.openlocfilehash: b71fd2986fb79adf88493416ac8234f2656aefa9
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866762"
---
# <a name="limitations-of-power-bi-qa"></a>Power BI 问答的限制

Power BI 问答当前有一些限制。

## <a name="data-sources"></a>数据源

### <a name="supported-data-sources"></a>支持的数据源

Power BI 问答支持 Power BI 服务中的以下数据源配置：

- 导入模式
- 实时连接到 Azure Analysis Services
- 实时连接到 SQL Server Analysis Services（通过网关）
- Power BI 数据集。

在这些配置中，还支持行级别安全性。

### <a name="data-sources-not-supported"></a>不支持数据源

Power BI 问答当前不支持以下配置：

- 任何类型的数据源的对象级别安全性
- 针对任何源的 DirectQuery。 解决方法是将 Live Connect 用于使用 DirectQuery 的 Azure Analysis Services。
- 复合模型
- Reporting Services 

## <a name="tooling-limitations"></a>工具限制

新工具对话框允许用户自定义并改进问答中的自然语言。 若要了解有关工具的详细信息，请参阅[问答工具简介](q-and-a-tooling-intro.md)。

## <a name="review-question-limitations"></a>回顾问题限制

回顾问题功能最多将已询问的有关数据模型的问题存储 28 天。 使用新的回顾问题功能时，你可能会注意到未记录某些问题。 这并非设计使然，因为自然语言引擎会执行一系列的数据清理步骤，以确保不会记录或显示用户的每个按键。

租户管理员可以使用租户管理员设置来管理存储问题的能力。 权限基于安全组。 

用户还可以通过选择“设置” > “常规”并取消选择“允许问答记录我的言语”来避免记录问题    。 

## <a name="teach-qa-limitations"></a>教导 Q&A 的限制

教导 Q&A 允许修正两种错误：

- 向字段分配字词。
- 向字词分配筛选条件。

目前，不支持重新定义已识别的术语或定义其他类型的条件或短语。 此外，在定义筛选条件时，只能使用有限的语言，其中包括：

- “国家/地区”是美国
- “国家/地区”不是美国
- 产品数 > 100
- 产品数大于 100
- 产品数 = 100
- 产品数为 100
- 产品数 < 100
- 产品数小于 100。

> [!NOTE]
> 问答工具仅支持导入模式。 尚不支持连接到本地或 Azure Analysis Services 数据源。 Power BI 的后续版本中将删除当前这一限制。

### <a name="statements-not-supported"></a>不支持语句

- 当前不支持在条件中使用度量值。 请将度量值转换为计算列以使其有效。
- 不支持使用多个条件。 解决方法是创建 DAX 计算列来判定多条件语句的真假，并改用此字段。
- 如果在问答提示输入数据子集时未指定筛选条件，则无法保存定义，即使整个语句没有红色下划线也是如此。

## <a name="next-steps"></a>后续步骤

用于改进自然语言引擎的最佳做法还有很多。 有关详细信息，请参阅[问答最佳做法](q-and-a-best-practices.md)。
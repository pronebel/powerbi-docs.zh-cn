---
title: 在 Power BI 中使用 DirectQuery 和 SAP Business Warehouse (BW)
description: 将 DirectQuery 用于 SAP Business Warehouse (BW) 时的注意事项
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6c47fb847ff5360031f4bfe2974db9c405a4ce5f
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670730"
---
# <a name="directquery-and-sap-business-warehouse-bw"></a>DirectQuery 和 SAP Business Warehouse (BW)
可以使用 DirectQuery 直接连接到 SAP Business Warehouse (BW) 数据源。 鉴于 SAP BW 的 OLAP/多维特性，SAP BW 的 DirectQuery 与 SQL Server 等关系源之间存在许多重要区别。 这些区别总结如下：

* 在关系源的 DirectQuery 中，有一组查询（在“获取数据”或“查询编辑器”对话框中定义）从逻辑上定义字段列表中的可用数据。 连接到 OLAP 源（如 SAP BW）时不是这样的情况。 当使用“获取数据”连接到 SAP 服务器时，只选择 Infocube 或 BEx 查询。 所选 Infocube/BEx 查询的所有键数字和维度都将在字段列表中可用。   
* 同样，当连接到 SAP BW 时，没有“查询编辑器”。 可通过选择“编辑查询>数据源设置”更改数据源设置（例如，服务器名称）。 可通过选择“编辑查询”>“管理参数”更改任何参数的设置。
* 鉴于 OLAP 源的唯一特性，除为 DirectQuery 规定的正常限制以外，还应用其他限制（用于建模和可视化）。 本文后面部分将介绍这些限制。

此外，非常重要的是要了解 SAP BW 的许多功能在 Power BI 中不受支持，并且由于 SAP BW 的公共接口的性质，在某些重要情况下，通过 Power BI 看到的结果与使用 SAP 工具看到的结果不匹配。 本文后面部分将介绍这些限制。 应仔细查看这些限制和行为差异，确保正确解释通过 Power BI 看到的结果（由 SAP 公共接口返回）。  

> [!NOTE]
> 自 Power BI Desktop 2018 年 3 月更新之后，才能使用 DirectQuery over SAP BW 预览版功能。 预览版期间，反馈和建议的改进会带来变化，进而影响使用该预览版创建的报表。 现已发布 DirectQuery over SAP BW 的通用版 (GA)，因此必须弃用通过 DirectQuery over SAP BW 创建的任何现有（基于预览版）的报表（即使用通用版之前的版本创建的报表）。 在使用通用版之前的 DirectQuery over SAP BW 创建的报表中，如果通用版之前的版本尝试将具有任何更改的元数据更新到基础 SAP BW 多维数据集，则调用此类刷新时会出现错误。 请使用通用版的 DirectQuery over SAP BW 基于空白报表重新创建这些报表。 

## <a name="additional-modeling-restrictions"></a>其他建模限制
在 Power BI 中使用 DirectQuery 连接到 SAP BW 时的主要其他建模限制如下所示：

* 不支持计算列：创建计算列的功能处于禁用状态。 这也意味着创建计算列的“分组”和“聚类分析”功能不可用。
* 针对度量值的其他限制：对可在度量值中使用的 DAX 表达式规定有其他限制，以反映 SAP BW 提供的支持级别。
* 不支持定义关系：关系是外部 SAP 源中固有的，并且无法在模型中定义其他关系。
* 没有数据视图：数据视图通常显示表中的详细信息级别数据。 鉴于 OLAP 源（如 SAP BW）的性质，此视图不适用于 SAP BW。
* 列和度量值详细信息固定：字段列表中所示的列和度量值列表由基础源固定，不能修改。 例如，不能删除列，也不能更改其数据类型（但是，可以将其重命名）。
* DAX 中的其他限制：DAX 中存在可在度量值定义中使用的其他限制，以反映源中的限制。 例如，不能在表中使用聚合函数。

## <a name="additional-visualization-restrictions"></a>其他可视化效果限制
在 Power BI 中使用 DirectQuery 连接到 SAP BW 时，可视化效果中的其他主要限制如下所示：

* **没有列聚合：** 不能更改视觉对象上的列的聚合；它始终为“不汇总”
* 禁用度量值筛选：禁用度量值筛选以反映 SAP BW 提供的支持。
* 多重选择和包括/排除：如果点表示来自多个列的值，则禁用在视觉对象上多重选择数据点的功能。 例如，给定的条形图显示按国家/地区划分的销售额，图例中含有类别，则将不能选择表示（美国，自行车）和（法国，服装）的点。 同样，不能选择表示（美国，自行车）的点并将其从视觉对象中排除。 这两个限制都是为了反映 SAP BW 提供的支持。

## <a name="support-for-sap-bw-features"></a>对 SAP BW 功能的支持
下表列出了使用 Power BI 时不完全支持，或行为方式不同的所有 SAP BW 功能。   

| 功能 | 说明 |
| --- | --- |
| 本地计算 |BEx 查询中定义的本地计算将更改通过 BEx 分析器等工具显示的数字。 但是，它们不会反映在通过公共 MDX 接口从 SAP 返回的数字中。 <br/> <br/> 在这种情况下，Power BI 视觉对象中显示的数字不一定与 SAP 工具中相应的视觉对象的数字匹配。<br/> <br/>  例如，当从将聚合设置为累积（即运行总和）的 BEx 查询连接到查询多维数据集时，Power BI 将返回基数，忽略该设置。  然后，分析师当然可以在 Power BI 中本地应用运行总和计算，但如果不执行此操作，则需要在解释这些数字时保持谨慎。 |
| 聚合 |在某些情况下（尤其是在处理多种货币时），SAP 公共接口返回的聚合数字与 SAP 工具显示的数字不匹配。 <br/> <br/> 在这种情况下，Power BI 视觉对象中显示的数字不一定与 SAP 工具中相应的视觉对象的数字匹配。 <br/> <br/> 例如，不同货币的总计将在 BEx 分析器中显示为 "*"，但总计将由 SAP 公共接口返回，而没有表示此类聚合数字无意义的任何信息。 因此 Power BI 将显示该数字（聚合，例如 $、EUR 和 AUD）。 |
| 货币格式 |Power BI 中不会反映任何货币格式（例如，$2,300 或 4000 AUD）。 |
| 度量单位 |Power BI 中不会反映度量单位（例如，230 KG）。 |
| 键与文本（短、中、长） |对于如 CostCenter 等 SAP BW 特性，字段列表将显示单个列“成本中心”。  使用此列将显示默认文本。  通过显示隐藏的字段，还可以看到唯一的名称列（返回由 SAP BW 分配的唯一名称，并且是唯一性的基础）。<br/> <br/>  键和其他文本字段不可用。 |
| 特性的多个层次结构 |在 SAP 中，某一特性可以具有多个层次结构。 在 BEx 分析器等工具中，当特性包含在查询中时，用户可以选择要使用的层次结构。 <br/> <br/> 在 Power BI 中，可以在字段列表中将各种层次结构视为同一维度上的不同层次结构。  但是，从位于同一维度的两个不同层次结构中选择多个级别将导致 SAP 返回空数据。 |
| 不规则层次结构的处理 |![](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| 缩放系数/反转符号 |在 SAP 中，键数字可以具有定义为格式选项的缩放系数（如 1000），这意味着所有显示都会按照该系数进行缩放。 <br/> <br/> 同样，它可以具有反转符号的属性设置。 在 Power BI 中使用此类键数字（在视觉对象中或作为计算的一部分）将导致使用未缩放的数字（并且不会反转符号）。 基础缩放系数不可用。 在 Power BI 视觉对象中，轴（K、M、B）上显示的缩放单元可作为视觉对象格式的一部分进行控制。 |
| 级别动态显示/消失的层次结构 |最初连接到 SAP BW 时，将检索关于层次结构级别的信息，从而导致字段列表中出现一组字段。 将缓存这些字段，如果级别设置发生更改，那么在调用“刷新”之前，这组字段的设置不会更改。 <br/> <br/> 这仅在 Power BI Desktop 中可行。 发布后，无法在 Power BI 服务中调用反映级别更改的此类“刷新”。 |
| 默认筛选器 |BEx 查询可以包含默认筛选器，SAP BEx 分析器将自动应用该筛选器。 这些不会公开，因此 Power BI 中的等效用法默认不会应用相同的筛选器。 |
| 隐藏的键数字 |BEx 查询可以控制键数字的可见性，隐藏的数字不会显示在 SAP BEx 分析器中。 这不会通过公共 API 反映，因此此类隐藏的键数字仍将显示在字段列表中。 但是，它们可以隐藏在 Power BI 中。 |
| 数字格式 |任何数字格式（小数位数、小数点等）都不会在 Power BI 中自动反映。 但是，可以在 Power BI 中控制此类格式。 |
| 层次结构版本控制 |SAP BW 允许维护层次结构的不同版本，例如 2007 年与 2008 年的成本中心层次结构。 由于公共 API 未公开关于版本的信息，所以 Power BI 中仅最新版本可用。 |
| 时间相关层次结构 |使用 Power BI 时，会在当前日期计算时间相关层次结构。 |
| 币种转换 |SAP BW 基于多维数据集中保留的汇率支持币种转换。 公共 API 未公开此类功能，因此 Power BI 中此类功能均不可用。 |
| 排序顺序 |可以在 SAP 中定义特性的排序顺序（按文本或按键）。 Power BI 中不会反映此排序顺序。 例如，月份可能显示为 “April”、“Aug” 等。 <br/> <br/> 在 Power BI 中无法更改此排序顺序。 |
| 技术名称 |在“获取数据”中，可以同时看到特性/度量值名称（说明）和技术名称。 字段列表将仅包含特性/度量值名称（说明）。 |
| 属性 |无法访问 Power BI 中特性的属性。 |
| 最终用户语言设置 |用于连接到 SAP BW 的区域设置设置为连接详细信息的一部分，并且不会反映最终报表使用者的区域设置。 |
| 文本变量 |SAP BW 允许字段名称包含变量（例如“$YEAR$ Actuals”）的占位符，占位符会随后替换为所选值。 例如，如果为该变量选择 2016 年，则在 BEx 工具中该字段显示为“2016 Actuals”。 <br/> <br/> Power BI 中的列名称不会随变量值而改变，因此将显示为“$YEAR$ Actuals”。  但是，以后可以在 Power BI 中更改列名称。 |
| 客户退出变量 | 公共 API 未公开客户退出变量，因此此类变量不受 Power BI 支持。 |
| 特性结构 | 基础 SAP BW 源中的任何特性结构都将导致在 Power BI 中公开的度量值数量的“激增”。 例如，根据 Sales 和 Costs 两个度量值，以及包含 Budget 和 Actual 的特性结构，将公开四个度量值：Sales.Budget、Sales.Actual、Costs.Budget、Costs.Actual。 |


## <a name="next-steps"></a>后续步骤
有关 DirectQuery 的详细信息，请查看以下资源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支持的数据源](desktop-directquery-data-sources.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)


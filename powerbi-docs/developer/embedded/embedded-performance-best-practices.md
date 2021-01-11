---
title: 用于增强嵌入式 BI 见解的 Power BI 嵌入式分析性能最佳做法
description: 本文提供 Power BI 嵌入式分析最佳做法相关指导。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: f8bf41ae9a4b6f2e16aae2c05df8fa4448a0457c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888779"
---
# <a name="power-bi-embedded-analytics-performance-best-practices"></a>Power BI 嵌入式分析性能最佳做法

本文提供在应用程序中更快呈现报表、仪表板和磁贴的相关建议。

> [!Note]
> 请注意，加载时间主要取决于与报表和数据本身相关的元素，包括视觉对象、数据的大小以及查询和度量值的复杂性。 有关详细信息，请参阅 [Power BI 优化指南](../../guidance/power-bi-optimization.md)。

## <a name="update-tools-and-sdk-packages"></a>更新工具和 SDK 包

使工具和 SDK 包保持最新。

* 始终使用最新版本的 [Power BI Desktop](https://powerbi.microsoft.com/desktop/)。

* 安装最新版本的 [Power BI 客户端 SDK](https://github.com/Microsoft/PowerBI-JavaScript)。 我们将持续发布更多功能，请持续关注并跟进后续发布。

## <a name="embed-parameters"></a>嵌入参数

`powerbi.embed(element, config)` 方法接收元素和 config。config 参数包括对性能有影响的字段。

### <a name="embed-url"></a>嵌入 URL

避免自己生成嵌入 URL。 确保通过调用[获取报表](/rest/api/power-bi/reports/getreportsingroup)、[获取仪表板](/rest/api/power-bi/dashboards/getdashboardsingroup)或[获取磁贴](/rest/api/power-bi/dashboards/gettilesingroup) API 来获取嵌入 URL。 我们将一个名为 config 的参数添加到了 URL，用于改进性能。

### <a name="permissions"></a>权限

如果不打算在“编辑模式”下嵌入报表，则提供“查看”权限。 通过这种方式，嵌入代码不会初始化用于编辑模式的组件。

### <a name="filters-bookmarks-and-slicers"></a>筛选器、书签和切片器

通常情况下，报表视觉对象会连同缓存数据一并保存。 缓存数据用于提供感知性能。 执行查询时，报表会呈现缓存数据。 如果提供了筛选器、书签或切片器，则缓存的数据不相关，并且只能在可视化查询结束后呈现视觉对象。

如果嵌入具有相同筛选器、书签和切片器的报表，为提高性能，请保存已应用的筛选器、书签和切片器的报表。 这会呈现包含筛选器、书签和切片器的缓存数据的报表。

## <a name="switching-between-reports"></a>在报表之间切换

在将多个报表嵌入到同一 iframe 时，不要为每个报表生成新的 iframe。 而是使用包含不同配置的 `powerbi.embed(element, config)` 嵌入新报表。

> [!NOTE]
> 在为客户嵌入时切换报表（也称为“应用拥有数据”场景），需要使用一个对所有报表和数据集具有权限的嵌入令牌。 有关更多信息，请参阅[生成令牌 API](/rest/api/power-bi/embedtoken/generatetoken)。

## <a name="query-caching"></a>查询缓存

具有 Power BI Premium 容量或 Power BI Embedded容量的组织可使用查询缓存来加快与数据集关联的报表的速度。

[详细了解 Power BI 中的查询缓存](../../connect-data/power-bi-query-caching.md)。

## <a name="preload"></a>预加载

使用 `powerbi.preload()` 改善最终用户体验。 方法 `powerbi.preload()` 会下载 Javascript、css 文件和其他项目，这些内容稍后将用于嵌入报表。

如果不立即嵌入报表，请调用 `powerbi.preload()`。 例如，如果主页未显示 Power BI 嵌入内容，则使用 `powerbi.preload()` 下载并缓存用于嵌入内容的项目。

## <a name="bootstrapping-the-iframe"></a>启动 iframe

> [!NOTE]
> 需要 [Power BI 客户端 SDK](https://github.com/Microsoft/PowerBI-JavaScript) 版本 2.9 才能启动 iframe。

借助 `powerbi.bootstrap(element, config)`，你可以先开始嵌入，然后再提供所有必需的参数。 启动 API 将准备并初始化 iframe。
使用启动 API 时，仍需在同一个 HTML 元素上调用 `powerbi.embed(element, config)`。

此功能的一个用例示例为并行运行 iframe 启动和后端调用，来执行嵌入。
> [!TIP]
> 如果能够在向最终用户显示 iframe 前先生成它，则使用启动 API。

[详细了解 iframe 启动](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance)。

## <a name="measure-performance"></a>测量性能

### <a name="performance-events"></a>性能事件

若要测量嵌入的性能，可以使用两个事件：

1. 加载的事件：报表初始化所用的时间（Power BI 徽标将在加载完成后消失）。
2. 呈现的事件：使用实际数据呈现出完整报表所用的时间。 每次重新呈现报表（例如，应用筛选器后）时将触发呈现事件。 若要测量报表，请确保对第一个事件执行了计算。

缓存数据在可用时呈现，但不生成其他事件。

[详细了解事件处理](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events)。

### <a name="performance-analyzer"></a>性能分析器

若要检查报表元素的性能，可以在 Power BI Desktop 中使用性能分析器。
使用性能分析器可以查看和记录用于度量每个报表元素的执行方式的日志。

[详细了解性能分析器](../../create-reports/desktop-performance-analyzer.md)。

> [!NOTE]
> 请务必始终将嵌入报表的性能与 powerbi.com 上的性能进行对比。 这可以帮助你了解性能问题的来源

## <a name="next-steps"></a>后续步骤

* [Power BI 优化指南](../../guidance/power-bi-optimization.md)
* [如何对 Power BI 嵌入式分析问题进行故障排除](embedded-troubleshoot.md)
* [Power BI 嵌入式分析常见问题解答](embedded-faq.md)
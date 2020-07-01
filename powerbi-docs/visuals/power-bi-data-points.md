---
title: 大型数据集、数据点限制和数据策略
description: 视觉对象和数据缩减策略的数据限制
author: mihart
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 97bccec3ec0e92ebfcc6b9251cf5c17f176fbed1
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240144"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>应用数据点限制和策略（按视觉对象类型）

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

在 Power BI 中呈现视觉对象时，可视化效果必须快速而准确。 这就需要为每个视觉对象类型配置的基础算法。 Power BI 中的视觉对象必须足够灵活以处理不同大小的数据集。 某些数据集只有少量数据点，而其他数据集具有数千万亿字节的数据点。 本文介绍了 Power BI 用于呈现可视化效果的策略。

## <a name="data-reduction-strategies"></a>数据缩减策略
每个视觉对象采用一个或多个数据缩减策略  以便处理要分析的大量数据。 即使是简单的表也会采用策略来避免将整个数据集加载到客户端。  所使用的缩减策略因视觉对象类型而异。 在生成发送到服务器的数据请求的过程中，每个视觉对象会从支持的数据缩减策略  中进行选择。 

每个视觉对象可控制这些策略中的参数来影响数据总量。   

## <a name="strategies"></a>策略
对于每个策略，存在基于要可视化的数据的形状和类型的默认值。 但可以在“Power BI 格式设置”窗格中覆盖默认值以提供正确的用户体验。 

* **数据窗口化**（分段）：允许用户通过逐渐加载整个数据集的片段来滚动浏览视觉对象中的数据。
* **前 N 个**：仅显示前 N 项
* **简单示例**：显示第一个、最后一个以及第 N 个均匀分布的项。
* **后 N 项**：仅显示后 N 项。  可用于监视频繁更新的数据。
* **高密度采样** - 改进了采样算法，从而更好地设置离群值和/或曲线的形状。
    * **装箱行采样** - 根据跨轴的区间中的离群值对数据点进行采样
    * **重叠点采样** - 根据用于保留离群值的重叠值对数据点进行采样

## <a name="statistics"></a>统计信息
某些模型可以提供有关某些列的值数量的统计信息。 显示此类信息时，如果视觉对象不显式覆盖策略的值计数，我们将利用该信息来跨多个层次结构提供更好的平衡。

有关详细信息，请参阅 [Analysis Services 中的新增功能](https://docs.microsoft.com/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017)

## <a name="dynamic-limits"></a>动态限制
除了上述策略之外，具有分组列的两个层次结构（轴和图例或类别和系列）的视觉对象还会使用一个名为“动态限制”  的其他策略。  动态限制旨在更好地平衡数据点。 

动态限制比静态限制提供更好的稀疏数据点选择。 例如，可以将视觉对象配置为选择 100 个类别和 10 个系列，总共包含 1000 个点。 但实际数据具有 50 个类别和 20 个系列。  在查询运行时，动态限制选择所有 20 个系列以填充请求的 1000 个点。

服务器拥有以下功能时，会自动应用动态限制：

* 在具有本地 SSAS 版本 2016 或更高版本的 Power BI Desktop 中，[利用服务器的 SuperDax 功能](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* 在 Desktop 和 Power BI 服务中，使用导入的模型时，进行直接查询、实时连接到服务或实时连接到 AS PaaS。 

* 在 Power BI 服务中，通过本地网关连接到本地 SSAS 时，我们无法使用动态限制。 本地网关不完全支持从本地 SSAS 返回结果集的不同结构的动态限制策略。  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>策略和数据点限制（按视觉对象类型）

### <a name="area-chart"></a>分区图
请参阅[行采样的工作原理](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>条形图/柱形图
- 处于分类模式时
    - 类别：通过一次使用 500 行的窗口进行虚拟化
    - 系列：前 60 个
    - 处于标量模式下时（可使用动态限制）
        - 最大点数：10,000
        - 类别：500 个值的示例
        - 系列：前 20 个值

### <a name="card-multirow"></a>卡片（多行） 
- 值：通过一次使用 200 行的窗口进行虚拟化

### <a name="combo-chart"></a>组合图
 使用相同策略作为柱形图。 请注意，**组合图**中的行不会使用**折线图**使用的高密度算法。

### <a name="power-bi-visuals"></a>Power BI 视觉对象
最多可以获得 30,000 个，但由视觉对象作者指示要使用的策略。 默认限制为 1000，但视觉对象创建者可以对其进行更改，最大值为 30,000。

### <a name="doughnut"></a>圆环图
- 最大点数：3,500
- 组：前 500 个
- 详细信息:前 20 个

### <a name="filled-map-choropleth"></a>着色地图等值线图 
着色地图可以使用统计信息或动态限制。 Power BI 将按以下顺序尝试使用缩减：动态限制、统计信息和配置。 
- 最大点数：10000
- 类别：前 500 个
- 系列（同时显示 X 和 Y 时）：前 20 个

### <a name="funnel"></a>漏斗图
- 最大点数：3,500
- 类别：前 3,500 个

### <a name="kpi"></a>KPI
- 趋势轴
- 后 3,500 个

### <a name="line-chart"></a>折线图
请参阅[行采样的工作原理](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>折线图，高密度
请参阅[高密度采样](../create-reports/desktop-high-density-sampling.md)

### <a name="map"></a>地图 
- 最大点数：3,500

根据配置，一个地图可以具有：
- 位置：前 3,500 个
- 位置、大小：前 3,500 个
- 位置、纬度和经度聚合（+/- 大小）：前 3,500 个
- 纬度、经度：请参阅[高密度散点图](../create-reports/desktop-high-density-scatter-charts.md)
- 纬度、经度、大小：前 3,500 个
- 图例、纬度、经度：请参阅[高密度散点图](../create-reports/desktop-high-density-scatter-charts.md)
- 图例、纬度、经度、大小：前 233 个图例、前 15 个纬度和经度（可使用统计信息或动态限制）
- 位置、图例、纬度和经度聚合（+/- 大小）：前 233 个位置、前 15 个图例（可使用统计信息或动态限制）

### <a name="matrix"></a>Matrix
- 行：通过一次使用 500 行的窗口进行虚拟化
- 列：前 100 个分组列 
- 值：多个值不会计入数据缩减

### <a name="powerapps-visual"></a>PowerApps 视觉对象
最多可以获得 30,000 个，但由视觉对象作者指示要使用的策略。 默认限制为 1000，但视觉对象创建者可以对其进行更改，最大值为 30,000。

### <a name="radial-gauge"></a>径向仪表
无缩减策略

### <a name="slicer"></a>切片器
- 值：通过一次使用 200 行的窗口进行虚拟化

### <a name="scatter-chart-high-density"></a>散点图（高密度）
请参阅[高密度散点图](https://docs.microsoft.com/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>饼图
- 最大点数：3,500
- 组：前 500 个
- 详细信息:前 20 个

### <a name="r--python-visuals"></a>R 和 Python 视觉对象
仅限于 150,000 行。 如果选择了 150,000 行以上，则仅使用前 150,000 行

### <a name="ribbon-chart"></a>带状图
- 处于分类模式时
    - 类别：通过一次使用 500 行的窗口进行虚拟化（数据窗口化）
    - 系列：前 60 个
    - 处于标量模式下时（可使用动态限制）
        - 最大点数：10,000
        - 类别：500 个值的示例
        - 系列：前 20 个值

### <a name="shape-map-preview"></a>形状映射（预览版）
形状映射可使用统计信息或动态限制。 
- 最大点数：1,500
- 类别：前 500 个

### <a name="table"></a>表
- 值：通过一次使用 500 行的窗口进行虚拟化（数据窗口化）

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>树形图（可使用统计信息或动态限制）
- 最大点数：3,500
- 组：前 500 个
- 详细信息:前 20 个

### <a name="waterfall-chart"></a>瀑布图
- 只有类别存储桶时
    - 最大点数：3,500
    - 仅限类别 - 前 3,500 个
- 同时显示类别和明细时
    - 类别：通过一次使用 30 行的窗口进行虚拟化（数据窗口化）
    - 明细 - 前 200 个值


## <a name="next-steps"></a>后续步骤
[可视化效果类型](power-bi-report-visualizations.md)

---
title: 使用管理门户监视 Power BI 高级容量
description: 使用 Power BI 管理门户，监视高级容量。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564897"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>在管理门户中监视容量

**运行状况**选项卡**容量设置**在管理门户中的区域提供有关你的容量和已启用工作负荷摘要指标。  

![在门户中的容量运行状况选项卡](media/service-admin-premium-monitor-portal/admin-portal-health.png)

如果需要更全面的指标，请使用[Power BI Premium 容量指标](service-admin-premium-monitor-capacity.md)应用。 应用程序提供向下钻取和筛选，和的最详细度量值接近容量性能影响每个方面。 若要了解详细信息，请参阅[与该应用程序监视器高级容量](service-admin-premium-monitor-capacity.md)。

## <a name="system-metrics"></a>系统指标

上**运行状况**选项卡上，在最高级别，CPU 使用率和内存使用情况提供的容量最重要的指标的快速视图。 这些度量值具有累积性，包括所有启用的容量的工作负荷。

| **指标** | **说明** |
| --- | --- |
| CPU 使用率 | 平均 CPU 利用率，以占总可用 CPU。 |
| 内存使用情况 | 平均内存使用率，以千兆字节 (GB)。|

## <a name="workload-metrics"></a>工作负荷度量值

每个工作负荷的容量已启用。 显示 CPU 使用率和内存使用情况。

| **指标** | **说明** |
| --- | --- |
| CPU 使用率 | 平均 CPU 利用率，以占总可用 CPU。 |
| 内存使用情况 | 平均内存使用率，以千兆字节 (GB)。|

### <a name="detailed-workload-metrics"></a>详细的工作负荷度量值

每个工作负荷的其他度量值。 显示的指标类型取决于工作负荷。 若要查看工作负荷的详细度量值，请单击 （下） 箭头展开。

![展开工作负荷的运行状况](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>数据流

##### <a name="dataflow-operations"></a>数据流操作

| **指标** | **说明** |
| --- | --- |
| 总计数 | 每个数据流的总刷新次数。 |
| 成功计数 | 每个数据流的总成功刷新。|
| 平均持续时间 （分钟） | 刷新数据流的平均持续时间（以分钟为单位） |
| 最大持续时间 （分钟） | 数据流运行时间最长的刷新持续时间（以分钟为单位）。 |
| 平均等待时间 （分钟） | 计划时间与刷新数据流开始时间之间的平均延迟（以分钟为单位）。 |
| 最大等待时间 （分钟） | 数据流的最长等待时间（以分钟为单位）。  |

#### <a name="datasets"></a>数据集

##### <a name="refresh"></a>刷新

| **指标** | **说明** |
| --- | --- |
| 总计数 | 每个数据集的总刷新次数。 |
| 成功计数 | 每个数据集刷新成功的总数。 |
| 失败计数 | 每个数据集的刷新失败的总数。 |
| 成功率  | 成功刷新除以总刷新以度量值的数目。 可靠性。 |
| 平均持续时间 （分钟） | 刷新数据集的平均持续时间（以分钟为单位）。  |
| 最大持续时间 （分钟） | 数据集运行时间最长的刷新持续时间（以分钟为单位）。 |
| 平均等待时间 （分钟） | 计划时间与刷新数据集开始时间之间的平均延迟（以分钟为单位）。 |
| 最大等待时间 （分钟） | 数据集的最长等待时间（以分钟为单位）。 |

##### <a name="query"></a>查询

| **指标** | **说明** |
| --- | --- |
| 总计数 | 为数据集运行的查询的总数。 |
| 平均持续时间(毫秒) |数据集的平均查询持续时间（以毫秒为单位）|
| 最长持续时间(毫秒) |数据集中运行时间最长的查询的持续时间（以毫秒为单位）。 |
| 平均等待时间（毫秒） |数据集的平均查询等待时间（以毫秒为单位）。 |
| 最大等待时间 （毫秒） |数据集中等待时间最长的查询的持续时间（以毫秒为单位）。 |

##### <a name="eviction"></a>逐出

| **指标** | **说明** |
| --- | --- |
| 模型计数 | 此容量的数据集逐出的总数。 容量面临内存压力时，节点从内存中逐出一个或多个数据集。 首先逐出处于非活动状态（当前没有执行查询/刷新操作）的数据集。 然后按“最近最少使用的项”(LRU) 这一顺序依次逐出。 |

#### <a name="paginated-reports"></a>分页报表

##### <a name="report-execution"></a>报表执行

| **指标** | **说明** |
| --- | --- |
| 执行计数  | 报表的执行次数和用户查看。|

##### <a name="report-usage"></a>报告使用情况

| **指标** | **说明** |
| --- | --- |
| 成功计数 | 用户查看报表次数。 |
| 失败计数 |用户查看报表次数。|
| 行计数 |报表中数据的行数。 |
| 数据检索持续时间 （毫秒） |检索报表数据所需的平均时间（以毫秒为单位）。 较长的持续时间可能表示查询速度缓慢或其他数据源问题。  |
| 处理的持续时间 （毫秒） |处理报表数据所需的平均时间（以毫秒为单位）。 |
| 呈现持续时间 （毫秒） |在浏览器中呈现报表所需的平均时间（以毫秒为单位）。 |

> [!NOTE]
> 有关详细度量值**AI**工作负载尚不可用。

## <a name="next-steps"></a>后续步骤

你现已了解如何监视 Power BI Premium 容量，可以了解有关优化容量的更多信息。

> [!div class="nextstepaction"]
> [优化 Power BI Premium 容量](service-premium-capacity-optimize.md)

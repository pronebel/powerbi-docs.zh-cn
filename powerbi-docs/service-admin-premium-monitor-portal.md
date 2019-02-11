---
title: 使用管理门户监视 Power BI 高级容量
description: 使用 Power BI 管理门户，监视高级容量。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 59097c07719e4bb8db188e8a86db377076aea7a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794123"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>在管理门户中监视容量

本文介绍如何使用管理门户中的“容量”设置获取容量性能的快速视图。  若要获取有关容量最深度的指标，最好使用 [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) 应用。

## <a name="capacity-metrics"></a>容量指标

管理门户的“容量设置”区域提供了四个仪表，用于指示过去七天的负载和容量所使用的资源。 这四个磁贴以小时为频率工作，指示过去七天内相应指标超过 80% 的小时数。 此指标表明最终用户体验可能会降级。

![7 天内的使用情况](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **指标** | **说明** |
| --- | --- |
| CPU |CPU 使用率超过 80% 的次数。 |
| 内存抖动 |表示后端核心的内存压力。 具体而言，这一指标指示因使用多个数据集产生的内存压力，而从内存清除数据集的次数。 |
| 内存使用情况 |平均内存使用量，以千兆字节 (GB) 表示。 |
| DQ/秒 | 直接查询和实时连接数超过限制的 80% 的次数。 <br>  DirectQuery 的总数和每秒实时连接查询数受限。 限制如下：P1、P2、P3 分别为 30/s、60/s 和 120/s。  直接查询和实时连接查询数计入上述限额。 例如，如果一秒内有 15 个 DirectQueries 和 15 次实时连接，则达到限制<br> 这同样适用于本地连接和云连接。 |
|  |  |

指标反映的是过去一周的利用率。  如果想要查看更详尽的指标视图，可单击任意摘要磁贴进行查看。  此操作将调出详细图表，显示高级容量的每个指标。 下图显示了 CPU 指标的详细信息。

![详细的 CPU 使用情况图表](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

这些图表过去一周内每小时汇总一次，有助于在高级容量可能出现特定的性能相关事件时进行隔离。

也可将指标的基础数据随意导出到 csv 文件。  导出后，过去一周每天每隔三分钟即显示一次详细信息。

## <a name="next-steps"></a>后续步骤

你现已了解如何监视 Power BI Premium 容量，可以了解有关优化容量的更多信息。

> [!div class="nextstepaction"]
> [Power BI Premium 容量资源管理和优化](service-premium-understand-how-it-works.md)

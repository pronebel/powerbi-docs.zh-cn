---
title: 监视 Power BI Embedded 数据引用
description: 监视 Power BI Embedded 时所需的重要参考资料。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: fc6b9dd4d50d665211324d1b6c05e62468fc034d
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690740"
---
# <a name="monitoring-power-bi-embedded-data-reference"></a>监视 Power BI Embedded 数据引用

有关为 Power BI Embedded 收集和分析监视数据的详细信息，请参阅 [Monitor Power BI Embedded](monitor-power-bi-embedded.md)。

## <a name="metrics"></a>指标

本部分列出了为 Power BI Embedded 收集的所有自动收集的平台指标。  

|指标类型 | 资源提供程序/类型命名空间<br/> 和到各个指标的链接 |
|-------|-----|
| Capacities | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities) |

### <a name="capacities"></a>Capacities

资源提供程序和类型：[Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities)

| 名称 | 指标 | 计价单位 | 说明 |
|:---|:-------|:-----|:------------|
|内存 (Gen1) |memory_metric               |字节        |内存。 范围：A1 为 0-3 GB，A2 为 0-5 GB，A3 为 0-10 GB，A4 为 0-25 GB，A5 为 0-50 GB，A6 为 0-100 GB。 仅支持 Power BI Embedded Generation 1 资源。 |
|内存抖动（数据集）(Gen1) |memory_thrashing_metric     |百分比      |平均内存抖动。 仅支持 Power BI Embedded Generation 1 资源。 |
|QPU 高利用率 (Gen1) |qpu_high_utilization_metric |计数        |过去 1 分钟 QPU 高利用率，1 表示高 QPU 利用率，否则为 0。 仅支持 Power BI Embedded Generation 1 资源。 |
|查询持续时间（数据集）(Gen1) |QueryDuration               |毫秒 |上一个间隔中的 DAX 查询持续时间。 仅支持 Power BI Embedded Generation 1 资源。 |
|查询池作业队列长度（数据集）(Gen1) |QueryPoolJobQueueLength     |计数        |查询线程池队列中的作业数。 仅支持 Power BI Embedded Generation 1 资源。 |

## <a name="metric-dimensions"></a>指标维度

有关指标维度定义的详细信息，请参阅[多维指标](/azure/azure-monitor/platform/data-platform-metrics#multi-dimensional-metrics)。

Power BI Embedded 没有任何包含维度的指标。

## <a name="resource-logs"></a>资源日志

本部分列出了可为 Power BI Embedded 收集的资源日志类型。

有关参考，请参阅 [Azure Monitor 支持的所有资源日志类别类型](/azure/azure-monitor/platform/resource-logs-schema)列表。

本部分列出了为 Power BI Embedded 收集的所有资源日志类别类型。  

|资源日志类型 | 资源提供程序/类型命名空间<br/> 和到各个指标的链接 |
|-------|-----|
| Capacities | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/resource-logs-categories#microsoftpowerbidedicatedcapacities) |

## <a name="azure-monitor-logs-tables"></a>Azure Monitor 日志表

本部分介绍所有与 Power BI Embedded 相关的 Azure Monitor 日志 Kusto 表，可通过 Log Analytics 进行查询。

|资源类型 | 说明 |
|-------|-----|
| [Power BI Embedded](/azure/azure-monitor/reference/tables/tables-resourcetype#power-bi-embedded) |参见下面的表格列表 |

### <a name="power-bi-embedded"></a>Power BI Embedded

| 表 |  说明 |
|:---------|:-------------|------------------|
| [AzureActivity](/azure/azure-monitor/reference/tables/azureactivity) | Azure 活动日志中的条目，可用于深入了解 Azure 中发生的任何订阅级别或管理组级别事件。    |                             |                                                   | 
| AzureDiagnostics   | 存储使用 Azure 诊断模式的 Azure 服务的资源日志。 资源日志描述 Azure 资源的内部操作。 |
| [AzureMetrics](/azure/azure-monitor/reference/tables/azuremetrics)   | 由 Azure 服务发出的指标数据，用于衡量其运行状况和性能。 |

有关所有 Azure Monitor 日志/Log Analytics 表的参考，请参阅 [Azure Monitor 日志表参考](/azure/azure-monitor/reference/tables/tables-resourcetype)。

## <a name="activity-log"></a>活动日志

可以选择“引擎”  和或“AllMetrics”  类别。

### <a name="engine"></a>引擎

引擎类别指示资源记录下面列出的事件。 每个事件都有对应的属性。

|     事件名称     |     事件描述     |
|----------------------------|----------------------------------------------------------------------------------|
|    Audit Login    |    记录自跟踪启动后的引擎事件的所有新连接。    |
|    Session Initialize    |    记录自跟踪启动后的所有会话初始化事件。    |
|    Vertipaq Query Begin    |    记录自跟踪启动后的所有 VertiPaq SE 查询开始事件。    |
|    Query Begin    |    记录自跟踪启动后的所有查询开始事件。    |
|    Query End    |    记录自跟踪启动后的所有查询结束事件。    |
|    Vertipaq Query End    |    记录自跟踪启动后的所有 VertiPaq SE 查询结束事件。    |
|    Audit Logout    |    记录自跟踪启动后从引擎事件断开的所有连接。    |
|    Error    |    记录自跟踪启动后的所有引擎错误事件。    |

#### <a name="event-example"></a>事件示例

下表显示了一个事件示例。

| 属性名称 | Vertipaq Query End 示例 | 属性说明 |
|---|---|---|
| EventClass | XM_SEQUERY_END | 事件类用于对事件进行分类。 |
| EventSubclass | 0 | 事件子类提供有关每个事件类的其他信息。 （例如，0: VertiPaq Scan） |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | 根活动 ID。 |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | 事件（如果可用）的启动时间。 |
| StartTime | 2018-04-06T18:30:11.9137358Z | 事件（如果可用）的启动时间。 |
| JobID | 0 | 进度的作业 ID。 |
| ObjectID | 464 | 对象 ID |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | 事件的结束时间。 |
| 持续时间 | 0 | 事件使用的时间（毫秒）。 |
| SessionType | User | 会话类型（哪个实体导致了该操作）。 |
| ProgressTotal | 0 | 总进度。 |
| IntegerData | 0 | 整型数据。 |
| Severity | 0 | 异常错误的严重级别。 |
| 成功 | 1 | 1 = 成功。 0 = 失败（例如，1 表示权限检查成功，而 0 表示权限检查失败）。 |
| Error | 0 | 给定事件的错误号。 |
| ConnectionID | 3 | 唯一连接 ID。 |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | 正在运行用户语句的数据集的 ID。 |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | 会话 GUID。 |
| SPID | 180 | 服务器进程 ID。 它唯一标识用户会话。 这直接对应于 XML/A 使用的会话 GUID。 |
| ClientProcessID | NULL | 客户端应用程序的进程 ID。 |
| ApplicationName | NULL | 创建到服务器的连接的客户端应用程序的名称。 |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | Power BI Embedded 容量资源的名称。 |

### <a name="allmetrics"></a>AllMetrics

查看“AllMetrics”  选项记录了可以在 Power BI Embedded 资源中使用的所有指标的数据。

下表列出了与可以在活动日志中创建的与 Power BI Embedded 相关的操作。

## <a name="schemas"></a>架构

Power BI Embedded 使用 Power BI 专用架构。

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[监视 Azure Power BI Embedded](monitor-power-bi-embedded.md)

>[!div class="nextstepaction"]
>[Azure 资源诊断日志记录](/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

>[!div class="nextstepaction"]
>[Set-AzureRmDiagnosticSetting](/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)
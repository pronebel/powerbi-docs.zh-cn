---
title: 网关性能监视 （公共预览版）
description: 本文提供有关监视性能的本地数据网关活动的信息。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535358"
---
# <a name="gateway-performance-monitoring-public-preview"></a>网关性能监视 （公共预览版）

若要监视性能，网关管理员具有传统上依赖于手动监视性能计数器通过 Windows 性能监视器工具。 我们现在提供其他查询日志记录和一个[网关性能 PBI 模板文件](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit)可视化结果。 此功能提供了新的角度了解网关使用情况，并可进行故障排除低性能查询。

> [!NOTE]
> 此功能目前仅在标准模式下的本地数据网关而不用于个人模式。

## <a name="enable-performance-logging"></a>启用性能日志记录

若要启用此功能，请对以下更改*Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*文件中"\Program Files\On-本地数据网关"文件夹：

1. 更新**QueryExecutionReportOn**到_True_以启用查询执行使用网关的其他日志记录。 启用此选项创建查询执行报表和查询执行聚合报告文件。

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. 更新**SystemCounterReportOn**到_True_以启用对内存和 CPU 系统计数器的其他日志记录。 启用此选项会创建系统计数器聚合报告文件。

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. 您可以根据需要更新，在配置文件中有其他值。

    - **ReportFilePath**:确定存储的三个日志文件的路径。 默认情况下，此路径为"\Users\PBIEgwService\AppData\Local\Microsoft\On-premises 数据 gateway\Report"或"Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On 内部部署数据 gateway\Report"，具体取决于 OS 版本。 如果你使用服务帐户为网关以外_PBIEgwService_，此路径的一部分替换为服务帐户名称。
    - **ReportFileCount**:确定要保留每种类型的日志文件数。 默认值为 10。
    - **ReportFileSizeInBytes**:确定要维护的文件的大小。 默认值为 104857600。
    - **QuerExecutionAggregationTimeInMinutes**:确定某聚合查询执行信息的分钟数。 默认值为 5。
    - **SystemCounterAggregationTimeInMinutes**:确定某聚合系统计数器的分钟数。 默认值为 5。

1. 向配置文件进行了更改后，重新启动网关对这些配置值才会生效。 现在将开始看到报表文件中为指定的位置生成**ReportFilePath**。

    > [!NOTE]
    > 它可能最多 10 分钟的时间加上的时间设置为**QuerExecutionAggregationTimeInMinutes**配置文件，直到文件开始显示在文件夹中。

## <a name="understand-performance-logs"></a>了解性能日志

当打开此功能时，我们将创建三个新的日志文件：

- 查询执行报表
- 在查询执行聚合报告
- 系统计数器聚合报告

查询执行报表包含详细的查询执行信息。 我们捕获以下属性：

|属性 |说明 |
| ---- | ---- |
|**GatewayObjectId** |网关的唯一标识符。 |
|**RequestId** |网关请求的唯一标识符。 它可能是相同的多个查询。 |
|**DataSource** |包含数据源类型和数据源。 |
|**QueryTrackingId** |查询的唯一标识符。 |  
|**QueryExecutionEndTimeUTC** |查询执行完成时的时间。 |
|**QueryExecutionDuration**(ms) |用于执行查询的持续时间。 |
|**QueryType** |键入的查询-例如，传递的查询可能是 Power BI 刷新/DirectQuery 或从 PowerApps 和 Microsoft Flow 的查询。 |
|**DataProcessingEndTimeUTC** |时间数据处理等后台处理、 数据检索、 压缩、 数据处理已完成的活动。 |
|**DataProcessingDuration**(ms) |后台处理、 数据检索、 压缩、 数据处理等类似的数据处理活动的持续时间。 |
|**Success** |指示是否查询成功还是失败。 |
|**ErrorMessage** |如果查询失败，指示错误消息。 |
| | |

在查询执行聚合报告包含查询信息聚合到的时间间隔内聚合**GatewayObjectId**，**数据源**，**成功**，以及**QueryType**。 默认值为 5 分钟，但可以按如下所述调整。 我们捕获以下属性：

|属性 |说明 |
| ---- | ---- |
|**GatewayObjectId** |网关的唯一标识符。 |
|**AggregationStartTimeUTC** |为其查询属性进行合计的时间范围的开头。 |
|**AggregationEndTimeUTC** |对属性进行合计的查询的时间范围的结尾。 |
|**DataSource** |包含数据源类型和数据源。 |
|**Success** |指示是否查询成功还是失败。 |
|**AverageQueryExecutionDuration**(ms) |查询执行的平均时间聚合时间窗口。 |
|**MaxQueryExecutionDuration**(ms) |聚合时间窗口的最大查询执行时间。 |
|**MinQueryExecutionDuration**(ms) |聚合时间窗口的最小查询执行时间。 |
|**QueryType** |键入的查询-例如，传递的查询可能是 Power BI 刷新/DirectQuery 或从 PowerApps 和 Microsoft Flow 的查询。 |
|**AverageDataProcessingDuration**(ms) |等的聚合时间窗口等后台处理、 数据检索、 压缩、 数据处理的数据处理活动的平均时间。 |
|**MaxDataProcessingDuration**(ms) |聚合时间窗口等后台处理、 数据检索、 压缩、 数据处理等的数据处理活动的最长时间。 |
|**MinDataProcessingDuration**(ms) |聚合时间窗口等后台处理、 数据检索、 压缩、 数据处理等的数据处理活动的最短时间。 |
|**Count** |查询数。 |
| | |

系统计数器聚合报告包含系统计数器的值聚合到一个时间间隔。 默认值为 5 分钟，但可以按如下所述调整。 我们捕获以下属性：

|属性 |说明 |
| ---- | ---- |
|**GatewayObjectId** |网关的唯一标识符。 |
|**AggregationStartTimeUTC** |已为其聚合系统计数器的时间范围的开头。 |
|**AggregationEndTimeUTC** |有关哪些系统计数器中聚合的时间范围的结尾。 |
|**CounterName** |系统计数器，网关，混合应用程序，包括内存和 CPU 使用率和总体机托管网关。 |
|**Max** |聚合时间窗口的系统计数器的最大值。 |
|**Min** |聚合时间窗口的系统计数器的最小值。 |
|**Average** |聚合时间窗口的系统计数器的平均值。 |
| | |

## <a name="visualize-gateway-performance"></a>直观显示网关性能

现在，你可以可视化的日志文件中的数据。

1. 下载[网关性能 PBI 模板](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit)和使用 Power BI desktop 将其打开。

1. 在打开的对话框中，检查的文件夹路径与中的值相匹配**ReportFilePath**。

    ![弹出窗口中的文件夹路径](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. 选择**负载**，并且模板文件开始从日志文件加载数据。 然后应在报表中使用的数据填充所有视觉对象。

1. 可以选择将此文件保存为 PBIX 并将其发布到你的服务自动刷新。

此外，你可以自定义此模板文件，以满足您的需要。 有关 Power BI 模板的详细信息，请参阅此[Microsoft Power BI 博客文章](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/)。
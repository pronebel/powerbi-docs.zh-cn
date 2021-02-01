---
title: 监视 Power BI Embedded
description: 从此处开始了解如何监视 Power BI Embedded。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: 1b8ebbd7913bc5763f9f4dd8576fbc4783e8d531
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690731"
---
# <a name="monitor-power-bi-embedded"></a>监视 Power BI Embedded

当你的关键应用程序和业务流程依赖于 Azure 资源时，你需要监视这些资源的可用性、性能和操作。 本文介绍 Power BI Embedded 生成的监视数据，以及如何使用 Azure Monitor 的功能对此数据进行分析和发出警报。

## <a name="monitor-overview"></a>Monitor 概述

在 Azure 门户中，每个 Power BI Embedded 实例的“概述”页都包含以下信息：

* 资源组 - 实例所属[资源组](/azure/azure-resource-manager/management/overview#resource-groups)
* 状态 - Power BI Embedded 实例的状态
* 位置 - Power BI Embedded 实例的位置
* 资源名称 - Power BI Embedded 实例的名称
* SKU - Power BI Embedded 实例使用的 SKU
* 订阅名称 - Power BI Embedded 实例订阅名称
* 订阅 ID - Power BI Embedded 实例订阅 ID

## <a name="what-is-azure-monitor"></a>说明是 Azure Monitor？

Power BI Embedded  使用 [Azure Monitor](/azure/azure-monitor/overview) 创建监视数据，该服务是 Azure 中的一个完整堆栈监视服务，它提供了一组完整的功能来监视 Azure 资源以及其他云和本地的资源。

一开始可以阅读[使用 Azure Monitor 监视 Azure 资源](/azure/azure-monitor/insights/monitor-azure-resource)一文，其中介绍了以下概念：

- 说明是 Azure Monitor？
- 与监视相关的成本
- 监视 Azure 中收集的数据
- 配置数据收集
- Azure 中用于分析监视数据并就其发出警报的标准工具

以下各节将介绍为 Power BI Embedded 收集的特定数据，并提供有关使用 Azure 工具配置数据收集和分析此数据的示例。

## <a name="monitoring-data"></a>监视数据

Power BI Embedded 收集与[监视 Azure 资源中的数据](/azure/azure-monitor/insights/monitor-azure-resource#monitoring-data-from-Azure-resources)中所述的其他 Azure 资源相同的监视数据。

有关 Power BI Embedded 创建的指标和日志指标的详细信息，请参阅[监视 Power BI Embedded 数据引用](monitor-power-bi-embedded-reference.md)。

## <a name="collection-and-routing"></a>收集和路由

平台指标和活动日志会自动收集和存储，但你可以使用诊断设置将其路由到其他位置。  

在创建诊断设置并将其路由到一个或多个位置之前，不会收集和存储资源日志。

有关使用 Azure 门户、CLI 或 PowerShell 创建诊断设置的详细过程，请参阅[创建诊断设置以收集 Azure 中的平台日志和指标](/azure/azure-monitor/platform/diagnostic-settings)。 创建诊断设置时，请指定要收集的日志类别。 [Power BI Embedded 监视数据引用](monitor-power-bi-embedded-reference.md#resource-logs)中列出了 Power BI Embedded 的类别。

### <a name="using-powershell-to-enable-diagnostics"></a>使用 PowerShell 启用诊断

若要使用 PowerShell 来启用指标和诊断日志记录，请使用下面列出的命令。 若要详细了解如何使用 PowerShell 启用诊断，请参阅[使用 PowerShell 在 Azure Monitor 中创建和配置 Log Analytics 工作区](/azure/azure-monitor/platform/powershell-workspace-configuration)。

* 若要在存储帐户中启用诊断日志的存储，请使用以下命令：

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    存储帐户 ID 是你想要发送日志的存储帐户的资源 ID。

* 若要将诊断日志流式传输到事件中心，请使用以下命令：

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* Azure 服务总线规则 ID 是具有以下格式的字符串：

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* 若要将诊断日志发送到 Log Analytics 工作区，请使用以下命令：

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* 可以使用以下命令来获取你的 Log Analytics 工作区的资源 ID：

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

可以组合这些参数，以启用多个输出选项。

以下部分将讨论可以收集的指标和日志。

## <a name="analyzing-metrics"></a>分析指标

可以通过从“Azure Monitor”菜单中打开“指标”，使用指标资源管理器基于其他 Azure 服务中的指标来分析 Power BI Embedded 指标。 有关使用此工具的详细信息，请参阅 [Azure 指标资源管理器入门](/azure/azure-monitor/platform/metrics-getting-started)。

有关为 Power BI Embedded 收集的平台指标列表，请参阅[监视 Power BI Embedded 数据引用指标](monitor-power-bi-embedded-reference.md#metrics)  

若要参考，可以查看 [Azure Monitor 中所有受支持的资源指标](/azure/azure-monitor/platform/metrics-supported)列表。

## <a name="analyzing-logs"></a>分析日志

Azure Monitor 日志中的数据以表形式存储，每个表具有自己独有的属性集。  

Azure Monitor 中的所有资源日志都具有后跟服务特定字段的相同字段。 [Azure Monitor 资源日志架构](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-schema#top-level-resource-logs-schema)中概述了常见架构。Power BI Embedded 资源日志架构可在 [Power BI Embedded 数据引用](monitor-power-bi-embedded-reference.md#schemas)中找到。

[活动日志](/azure/azure-monitor/platform/activity-log)是 Azure 中的一种平台日志，可用于深入了解订阅级别事件。 你可以单独查看它或将它路由到 Azure Monitor 日志，然后便可以在其中使用 Log Analytics 执行复杂得多的查询。  

有关为 Power BI Embedded 收集的资源日志类型列表，请参阅 [监视 Power BI Embedded 数据引用](monitor-power-bi-embedded-reference.md#resource-logs)  

有关 Azure Monitor 日志使用的并可通过 Log Analytics 查询的表列表，请参阅[监视 Power BI Embedded 数据引用](monitor-power-bi-embedded-reference.md#azure-monitor-logs-tables)  

### <a name="sample-kusto-queries"></a>示例 Kusto 查询

> [!IMPORTANT]
> 从 Power BI Embedded 菜单中选择“日志”时，会打开 Log Analytics，同时查询范围设置为当前 Power BI Embedded 资源。 这意味着日志查询只包含来自该资源的数据。 如果要运行包含来自其他 Power BI Embedded 资源或来自其他 Azure 服务的数据的查询，请从“Azure Monitor”菜单中选择“日志”。 有关详细信息，请参阅 [Azure Monitor Log Analytics 中的日志查询范围和时间范围](/azure/azure-monitor/log-query/scope/)。

下面是用于监视 Power BI Embedded 的查询示例。

* 这是在五分钟（300,000 毫秒）内完成的查询。

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```
* 标识容量名称。

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```

## <a name="alerts"></a>警报

在监视数据中发现重要情况时，Azure Monitor 警报会主动通知你。 有了警报，你就可以在客户注意到你的系统中的问题之前确定和解决它们。 可以在[指标](/azure/azure-monitor/platform/alerts-metric-overview)、[日志](/azure/azure-monitor/platform/alerts-unified-log)和[活动日志](/azure/azure-monitor/platform/activity-log-alerts)上设置警报。

## <a name="next-steps"></a>后续步骤

可以了解有关 Azure 资源诊断日志记录的详细信息。

>[!div class="nextstepaction"]
>[监视 Power BI Embedded 数据引用](monitor-power-bi-embedded-reference.md)

>[!div class="nextstepaction"]
>[使用 Azure Monitor 监视 Azure 资源](/azure/azure-monitor/insights/monitor-azure-resource)
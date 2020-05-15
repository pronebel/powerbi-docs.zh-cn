---
title: Azure 中 Power BI Embedded 服务的诊断日志记录 | Microsoft Docs
description: 了解如何在 Azure 中设置 Power BI Embedded 服务的诊断日志记录。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 362c765fb5e739563b8d21eaed53304eddce8acc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79495794"
---
# <a name="diagnostic-logging-for-power-bi-embedded-in-azure"></a>Azure 中 Power BI Embedded 的诊断日志记录

使用 [Azure 资源诊断日志](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)，可以记录来自你的容量中的许多事件、将其置入分析工具并深入了解你的资源的行为。

使用诊断可以解答几个应用场景，例如：

* 检测运行时间较长或存在问题的查询。
* [容量指标](https://powerbi.microsoft.com/blog/power-bi-developer-community-april-update/)的派生。
* 跟踪特定数据集的使用情况。

## <a name="set-up-diagnostics-logging"></a>设置诊断日志记录

### <a name="azure-portal"></a>Azure 门户

1. 在 [Azure 门户](https://portal.azure.com) > Power BI Embedded 资源中，选择导航窗格中的“诊断日志”，然后选择“启用诊断”   。

    ![在 Azure 门户中，为 Power BI Embedded 启用诊断日志记录](media/azure-pbie-diag-logs/azure-pbie-diag-logs-01.png)

2. 在“诊断设置”  中，指定以下选项：

    * “名称”  - 输入要创建的诊断设置的名称。

    * “存档到存储帐户”  - 若要使用此选项，需要连接到现有存储帐户。 请参阅[创建存储帐户](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)，并按照说明来创建存储帐户。 然后，在门户中返回该页以选择你的存储帐户。 新创建的存储帐户可能需要几分钟的时间才会显示在下拉菜单中。 日志文件存储为 JSON 格式。
    * 流式传输到事件中心  - 若要使用此选项，需要连接到现有事件中心命名空间和事件中心。 若要了解详细信息，请参阅[使用 Azure 门户创建事件中心命名空间和事件中心](https://docs.microsoft.com/azure/event-hubs/event-hubs-create)。
    * 发送到 Log Analytics  - 若要使用此选项，请使用现有工作区，或按照门户中[创建新工作区](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-collect-azurevm#create-a-workspace)的步骤来来创建一个新的 Log Analytics 工作区。 这将利用 [Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)，它可提供内置分析、仪表板和通知功能。 可以使用 Log Analytics 从其他资源连接更多数据，并跨所有应用程序的资源获取数据的单个和完整视图。 它还可以连接到 [Power BI（只需单击一次）](https://docs.microsoft.com/azure/log-analytics/log-analytics-powerbi)。
    有关在 Log Analytics 中查看你的日志的详细信息，请参阅[在 Log Analytics 中查看日志](https://docs.microsoft.com/azure/log-analytics/log-analytics-activity)。
    * 引擎  - 选择此选项以记录以下[列出的引擎事件](#whats-logged)集。
    * AllMetrics  - 选择此选项以存储[指标](https://docs.microsoft.com/azure/analysis-services/analysis-services-monitor#server-metrics)中的详细数据。 如果要存档到存储帐户，可以为诊断日志选择保持期。 日志将在保持期到期后被自动删除。

3. 选择“保存”  。

    若要更改保存诊断日志的方式，可以返回到此页面以修改设置。

    ![诊断设置](media/azure-pbie-diag-logs/diag-settings.png)

### <a name="using-powershell-to-enable-diagnostics"></a>使用 PowerShell 启用诊断

若要使用 PowerShell 来启用指标和诊断日志记录，请使用以下命令：

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

### <a name="rest-api"></a>REST API

了解如何[使用 Azure Monitor REST API 更改诊断设置](https://docs.microsoft.com/rest/api/monitor/)。 

### <a name="resource-manager-template"></a>资源管理器模板

了解如何[使用资源管理器模板在创建资源时启用诊断设置](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-enable-diagnostic-logs-using-template)。

## <a name="whats-logged"></a>记录哪些内容？

可以选择“引擎”  和或“AllMetrics”  类别。

### <a name="engine"></a>引擎

引擎类别指示资源记录以下事件，在每个事件上有以下属性：

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

<br>
<br>

| 属性名称 | Vertipaq Query End 示例 | 属性说明 |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
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
| 成功 | 第 1 个 | 1 = 成功。 0 = 失败（例如，1 表示权限检查成功，而 0 表示权限检查失败）。 |
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

   ![显示指标](media/azure-pbie-diag-logs/azure-pbie-diag-logs-02.png)

## <a name="manage-your-logs"></a>管理你的日志

日志通常在日志记录设置后的几个小时内可用。 由你管理你的存储帐户中的日志：

* 使用标准 Azure 访问控制方法，通过限制访问你的日志的人员来保护日志的安全。
* 在存储帐户中删除不想继续保留的日志。
* 请确保设置保持期，以便将旧日志从你的存储帐户中删除。

## <a name="view-logs-in-log-analytics"></a>在 Log Analytics 中查看日志

指标和服务器事件与 Log Analytics 中的 xEvents 集成，以用于并行分析。 还可以将 Log Analytics 配置为接收来自其他 Azure 服务的事件，以从整体上展示整个体系结构的诊断日志记录数据。

若要在 Log Analytics 中查看你的诊断数据，请从左侧菜单或管理区域中打开“日志”  页面，如下所示。

![Log Analytics 页面](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics.png)

启用数据收集后，在“日志”  中，选择“收集的所有数据”  。

![收集的所有数据](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-all-collected-data.png)

在“类型”  中，选择“AzureDiagnostics”  ，然后选择“应用”  。 AzureDiagnostics 包括引擎事件。 注意，将实时创建 Log Analytics 查询。

![Azure 诊断](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-azure-diagnostics.png)

选择 EventClass\_  或事件名称之一，Log Analytics 将继续构造查询。 请确保保存查询，以便稍后重复使用。

请确保参阅 [Log Analytics](https://docs.microsoft.com/azure/log-analytics/)，它提供了对收集的数据使用增强的查询、仪表板和警报功能的网站。

### <a name="queries"></a>查询

有数千个供你使用的查询。 可通过以下几个查询开始操作。 若要了解有关使用新的日志搜索查询语言的详细信息，请参阅[了解 Log Analytics 中的日志搜索](https://docs.microsoft.com/azure/log-analytics/log-analytics-log-search)。

* 返回该结果的查询需要不到五分钟的时间（300,000 毫秒）来完成。

    ```
    search *
    | where Type == "AzureDiagnostics"
    | where ( OperationName == "QueryEnd" )
    | where toint(Duration_s) < 300000
    ```

    ![持续时间查询结果](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-duration-query.png)

* 标识容量名称。

    ```
    search *
    | where ( Type == "AzureDiagnostics" )
    | summarize count() by CapacityName_s 
    ```

    ![容量名称查询结果](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-capacity-name-query.png)

## <a name="next-steps"></a>后续步骤

可以了解有关 Azure 资源诊断日志记录的详细信息。

> [!div class="nextstepaction"]
> [Azure 资源诊断日志记录](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

> [!div class="nextstepaction"]
> [Set-AzureRmDiagnosticSetting](https://docs.microsoft.com/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)

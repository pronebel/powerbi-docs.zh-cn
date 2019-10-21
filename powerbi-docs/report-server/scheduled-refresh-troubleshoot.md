---
title: 对 Power BI 报表服务器中的计划刷新进行故障排除
description: 本文将讨论可用于解决 Power BI 报表服务器中计划刷新问题的资源。
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: troubleshooting
ms.date: 11/01/2017
ms.author: mblythe
ms.openlocfilehash: 6f35ab1dfb14fe5a48fce0b56823ce7bab32d05d
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72543929"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>对 Power BI 报表服务器中的计划刷新进行故障排除
本文将讨论可用于解决 Power BI 报表服务器中计划刷新问题的资源。

对于后续出现的问题，本文将进行信息更新以为你提供帮助。

## <a name="common-issues"></a>常见问题
以下是在尝试为报表计划刷新时会遇到的较为常见的一些问题。 

### <a name="driver-related-problems"></a>驱动程序相关的问题
连接到不同的数据源可能需要安装第三方驱动程序才能成功连接。 不仅需要在使用 Power BI Desktop 的计算机上安装驱动程序，而且还需要确保在报表服务器上安装驱动程序。

另外，可能会同时提供 32 位和 64 位驱动程序。 请确保安装 64 位驱动程序，因为 Power BI 报表服务器是 64 位的。

有关如何安装和配置第三方驱动程序的详细信息，请咨询制造商。

### <a name="memory-pressure"></a>内存压力
当报表需要更多内存来进行处理和呈现时，可能会出现内存压力。 报表上的计划刷新可能需要占用计算机上的大量内存， 尤其是对于较大的报表。 内存压力可能会导致报表失败，也可能会导致报表服务器本身崩溃。

如果持续遇到内存压力，则可能需要查看报表服务器的横向扩展部署，以便分散资源负载。 另外，还可以使用 rsreportserver.config 内的 `IsDataModelRefreshService` 设置定义给定的报表服务器用于数据刷新。使用此设置，可以定义一个或多个服务器作为前端服务器来处理按需报表，并将另一组服务器定义为专用于计划的刷新。

有关如何监视 Analysis Services 实例的信息，请参阅[监视 Analysis Services 实例](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance)。

有关 Analysis Services 中内存设置的信息，请参阅[内存属性](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties)。

### <a name="kerberos-configuration"></a>Kerberos 配置
使用 Windows 凭据连接到数据源可能需要配置 Kerberos 约束委派才能建立成功的连接。 有关如何配置 Kerberos 约束委派的详细信息，请参阅[配置 Kerberos 以使用 Power BI 报表](configure-kerberos-powerbi-reports.md)。

## <a name="known-issues"></a>已知问题
有关已知问题的信息可用时将在此处列出。

## <a name="configuration-settings"></a>配置设置
可以使用以下设置影响计划的刷新。 在 SQL Server Management Studio (SSMS) 中设定的设置适用于横向扩展部署中的所有报表服务器。 在 rsreportserver.config 中配置的设置适用于设定这些设置的特定服务器。

**SSMS 中的设置：**

| 设置 | 说明 |
| --- | --- |
| MaxFileSizeMb |已上载报表的最大文件大小。 默认值为 1000 MB (1 GB)。 最大值为 2000 MB (2 GB)。 |
| ModelCleanupCycleMinutes |定义检查模型以将其从内存中收回的频率。 默认值为 15 分钟。 |
| ModelExpirationMinutes |根据上次使用时间定义模型的到期并将其收回的时长。 默认值为 60 分钟。 |
| ScheduleRefreshTimeoutMinutes |定义一个模式的数据刷新需要多长时间。 默认值为 120 分钟。 没有上限。 |

**rsreportserver.config 中的设置：**

```xml
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>用于故障排除的工具
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>与 Power BI 报表的计划刷新相关的日志
保存有关计划刷新信息的日志文件是 RSPowerBI_ 日志。 这些文件位于报表服务器安装位置的 LogFiles 文件夹中。 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**错误条件**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***成功刷新***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**不正确的凭据**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>启用详细日志记录
在 Power BI 报表服务器中启用详细日志记录与 SQL Server Reporting Services 相同。

1. 打开 `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`。
2. 在 `<system.diagnostics>` 下，将 DefaultTraceSwitch 更改为 4。  
3. 在 `<RStrace>` 下，将 Components 更改为 all:4。   

### <a name="executionlog"></a>ExecutionLog
每当呈现 Power BI 报表或执行计划刷新计划时，都会向数据库中的执行日志添加新条目。 这些条目可在报表服务器目录数据库内的 ExecutionLog3  视图中查看。

Power BI 报表的执行日志条目不同于其他报表类型的条目。

* TimeRendering 列始终是 0。 Power BI 报表的呈现是在浏览器中，而不在服务器中。
* 存在 2 种请求类型和后续项操作：
  * **交互式**：每当查看报表时。
    * **ASModelStream**：当数据模型从目录流式传输到 Analysis Services 时。
    * **ConceptualSchema**：当用户单击查看报表时。
    * **QueryData**：每当从客户端请求数据时。
  * **刷新缓存**：每当已执行计划刷新计划时。
    * **ASModelStream**：每当数据模型从目录流式传输到 Analysis Services 时。
    * **DataRefresh**：每当从一个或多个数据源刷新数据时。
    * **SaveToCatalog**：每当将数据模型保存回目录时。

## <a name="analysis-services"></a>Analysis Services
有时你可能要修改 Analysis Services 以诊断问题，或者调整内存限制。

> [!IMPORTANT]
> 这些设置将在升级报表服务器时重置。 请务必保留更改的副本，并根据需要重新应用。
> 
> 

### <a name="install-location"></a>安装位置
Power BI 报表服务器和 Analysis Services 的默认位置如下所示。

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>配置 Analysis Services 设置 (msmdsrv.ini)
在 `<install directory>\PBIRS\ASEngine` 目录中，将会找到 msmdsrv.ini  文件，其可用于控制 Analysis Services 的不同设置。 打开此文件时，你会很快意识到此文件并没有你所期望的 msmdsrv.ini 文件中的所有设置。 

这是因为在 `<install directory>\PBIRS\ASEngine\workspaces` 中启动了由 Power BI 报表服务器运行的实际 Analysis Services 进程。 在该文件夹中，你将看到经常使用的完整 msmdsrv.ini  文件。 重要的是不要修改工作区文件夹内的文件，因为每当 Analysis Services 进程启动时都会重写该文件。 如果你想要控制设置，请通过修改 `<install directory>\PBIRS\ASEngine` 目录中的 msmdsrv.ini 来实现。

每当启动 Analysis Services 进程时，都会重置以下设置。 你对这些设置进行的任何更改都将被忽略。

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>分析本地 Analysis Services 进程
SQL 事件探查器跟踪可以在本地 Analysis Services 进程上运行，以进行诊断。 要连接到本地 Analysis Services 实例，请执行以下操作。

SQL Server Profiler 跟踪包含在 [SQL Server Management Studio (SSMS) 下载](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)中。

1. 以管理员身份启动 SQL Server Profiler  。
2. 选择“新建跟踪”  按钮。
3. 在“连接到服务器”  对话框中，选择“Analysis Services”  ，然后输入 localhost:5132  作为服务器名。
4. 在“跟踪属性”  对话框中，选择要捕获的事件，然后选择“运行”  。

## <a name="lock-pages-in-memory-windows-privilege"></a>锁定内存页 Windows 特权
如果发现无法呈现 Power BI 报表，则可将“锁定内存页”  特权分配给正在运行 Power BI 报表服务器的服务帐户可能会有所帮助。 有关如何配置“锁定内存页”  的详细信息，请参阅[分配给 Analysis Services 服务帐户的 Windows 特权](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv)。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


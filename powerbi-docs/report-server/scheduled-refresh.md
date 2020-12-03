---
title: Power BI 报表服务器中 Power BI 报表计划的刷新
description: 通过 Power BI 报表的计划内刷新，可以不断更新包含嵌入模型的报表的数据。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/09/2020
ms.openlocfilehash: 4dd8914abe1f098b66d23daa299200b90b9bda6a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412566"
---
# <a name="power-bi-report-scheduled-refresh-in-power-bi-report-server"></a>Power BI 报表服务器中 Power BI 报表计划的刷新
通过对 Power BI 报表设置计划的刷新，可使报表数据保持最新状态。

![Power BI 报表服务器中的计划的刷新](media/scheduled-refresh/scheduled-refresh-success.png)

计划的刷新特定于含嵌入模型的 Power BI 报表。 这意味着，你会将数据导入报表，而不使用实时连接或 DirectQuery。 在导入你的数据时，它从原始数据源断开连接并且需要更新以使数据保持最新。 计划的刷新是让数据保持最新的方法。

在报表的管理部分配置计划的刷新。 有关如何配置计划的刷新的更多信息，请参阅[如何配置 Power BI 报表计划的刷新](configure-scheduled-refresh.md)。

## <a name="how-this-works"></a>运行原理
为 Power BI 报表中使用计划的刷新时涉及多个组件。

* SQL Server 代理作为计时器用于生成计划的事件。
* 将计划的作业添加到报表服务器数据库中的事件和通知队列。 对于扩展部署，将在部署中的所有报表服务器之间共享该队列。
* 所有作为计划事件的结果发生的报表处理都将作为后台进程执行。
* 在 Analysis Services 实例中加载数据模型。
* 对于某些数据源，Power Query 混合引擎用于连接数据源并转换数据。 可直接从用于托管 Power BI 报表服务器的数据模型的 Analysis Services 服务连接其他数据源。
* 新的数据被加载到 Analysis Services 中的数据模型。
* 在扩展配置中，可以跨节点复制数据模型。
* Analysis Services 处理数据并执行任何所需的计算。

Power BI 报表服务器为所有计划的操作维护事件队列。 它定期轮询队列，检查是否有新事件。 默认情况下，每隔 10 秒扫描一次队列。 通过修改 RSReportServer.config 文件中的 **PollingInterval**、 **IsNotificationService** 和 **IsEventService** 配置设置可以更改此间隔。 “IsDataModelRefreshService”还可用于设置报表服务器是否处理计划的事件。

### <a name="analysis-services"></a>Analysis Services
呈现 Power BI 报表和执行计划的刷新需要在 Analysis Services 中加载 Power BI 报表的数据模型。 Analysis Services 进程将与 Power BI 报表服务器一起运行。

## <a name="considerations-and-limitations"></a>注意事项和限制
### <a name="when-scheduled-refresh-cant-be-used"></a>无法使用计划的刷新时
并非所有 Power BI 报表都具有在其上创建的计划刷新计划。 下面是无法在其上创建计划刷新计划的 Power BI 报表列表。

* 报表包含一个或多个使用实时连接 Analysis Services 数据源。
* 报表包含一个或多个使用 DirectQuery 的数据源。
* 报表不包含任何数据源。 例如，通过“输入数据”手动输入数据，或报表仅包含静态内容，如图像、文本等。

除了上述列表，在“导入”模式下，还有一些含数据源的特定场景，你不能为其创建刷新计划。

* 如果使用的是“文件”或“文件夹”数据源且文件路径是本地路径（例如 C:\Users\user\Documents），则无法创建刷新计划。 路径必须是报表服务器可以连接到网络共享之类的路径。 例如“\\myshare\Documents”。
* 如果只能使用 OAuth（例如 Facebook、Google Analytics、Salesforce 等）连接数据源，则无法创建缓存刷新计划。 目前，RS 针对任何数据源均不支持 OAuth 身份验证，无论是针对分页报表、移动报表，还是 Power BI 报表。

### <a name="memory-limits"></a>内存限制
报表服务器的传统工作负荷已类似于 Web 应用程序。 能够加载具有导入数据或 DirectQuery，能够执行计划的刷新，这两种能力都依赖于与报表服务器一起托管的 Analysis Services 实例。 因此，这可能会导致服务器上意外的内存压力。 在知道 Analysis Services 和报表服务器可能会占用内存的情况下，相应地规划服务器部署。

有关如何监视 Analysis Services 实例的信息，请参阅[监视 Analysis Services 实例](/sql/analysis-services/instances/monitor-an-analysis-services-instance)。

有关 Analysis Services 中内存设置的信息，请参阅[内存属性](/sql/analysis-services/server-properties/memory-properties)。

### <a name="data-model-size-limit"></a>数据模型大小限制
在计划刷新期间加载到内部 Analysis Services 引擎中的数据模型具有 2000 MB (2GB) 的最大大小。 无法配置此最大大小。 如果数据模型增长超过 2GB，你将收到刷新错误“结果的长度超出了目标大型类型的长度限制(2GB)。” 在这种情况下，我们建议在 Analysis Services 实例中托管该模型，并在报表中使用到该模型的实时连接。

## <a name="next-steps"></a>后续步骤
在 Power BI 报表上配置[计划的刷新](configure-scheduled-refresh.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
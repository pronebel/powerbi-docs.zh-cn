---
title: Power BI 性能最佳做法
description: 本文将介绍如何在 Power BI 中构建快速可靠的报表
author: MarkMcGeeAtAquent
ms.author: kfile
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2018
LocalizationGroup: Reports
ms.openlocfilehash: f603a733c6c604a89b0b9608904acdf13b66b713
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54287775"
---
# <a name="power-bi-performance-best-practices"></a>Power BI 性能最佳做法

本文将介绍如何在 Power BI 中构建快速可靠的报表  

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>使用筛选器将报表视觉对象限制为仅显示需要的内容 

视觉对象需要显示的数据越多，加载视觉对象的速度越慢。 虽然此道理显而易见，但很容易忘记。 例如：假设你有一个大型数据集。 基于此数据集，你可以使用该表的一个表生成报表。 最终用户在此页上使用切片器来获取他们所需的行 - 通常他们只对某几十行感兴趣。

一个常见的错误是采用表未经筛选的默认视图 - 即显示全部的 100M+ 行。 这些行的数据必须加载到内存中并在每次刷新时解压缩。 这势必会产生大量的内存负载。 解决方案：使用“Top N”筛选器减少表显示的最大项数。 最大项数可以比用户所需行数大得多，例如 10,000。 因此，最终用户体验没有变化，但报表的内存使用率却下降了数个数量级，而且性能也相应得到提高。

对于报表中的所有视觉对象，建议采用以上类似的方法。 问问自己，是否需要此视觉对象中的所有数据？ 是否有方法可将视觉对象中显示的数据量滤除，而又不会对最终用户体验造成过多影响？ 请注意，尤其是表会产生大量费用。

## <a name="limit-visuals-on-report-pages"></a>限制报表页上的视觉对象

上述原则同样适用于特定报表上的视觉对象数量。 强烈建议将特定报表上的视觉对象数量限制为仅包括必需的视觉对象。 钻取页面是一个可提供更多详细信息而无需将更多视觉对象插入到报表中的好方法。  

## <a name="optimize-your-model"></a>优化你的模型

一些最佳做法：

- 如果可能，应删除未使用的表或列。 
- 避免对高基数（即，数百万个不同的值）字段进行非重复计数。  
- 请采取措施，以避免使用具有不必要精度和高基数的字段。 例如，可以将高度唯一的日期/时间值拆分为不同的列 - 例如月、年、日期等。或者，在可能的情况下，使用舍入高精度字段来减少基数（例如 13.29889 - > 13.3）。
- 尽可能使用整数而不是字符串。
- 谨慎对待需要测试表中每一行的 DAX 函数（例如 RANKX），在最坏的情况下，这些函数可以按照表的大小线性增长，以指数级增加运行时间和内存需求。
- 通过 DirectQuery 连接到数据源时，请考虑为通常经过重新筛选或切片的列添加索引，这将会大大提高报表的响应能力。  

有关优化 DirectQuery 数据源的更多指南，请参阅 [SQL Server 2016 Analysis Services 中的 DirectQuery](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)。

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery 和实时连接：了解基础数据源的性能

在 DirectQuery 或实时连接的情况下，当用户访问 Power BI 报表时，Power BI 会实时将查询发送到基础数据源。 数据源返回查询数据后，报表就会呈现。 因此，这些情况下的报表性能在很大程度上取决于基础数据源的性能。

在这些情况下，了解基础数据源的性能非常重要。 不同的数据源具有用于理解查询性能的不同工具。 例如，SQL Server 和 Azure SQL 提供了查询数据存储，可以捕获查询历史记录及其运行时统计信息。

作为一条经验法则，当部署基于 DirectQuery 和实时连接构建的 Power BI 报表时，请试用最终用户在 Power BI Desktop 中所做的操作。 如果报表在 Power BI Desktop 中加载缓慢，那么为最终用户加载服务的速度几乎肯定会很慢。 

## <a name="directquery-best-practices"></a>DirectQuery 最佳做法

以下部分介绍通过 DirectQuery 进行连接的常规最佳做法。
  
### <a name="db-design-guidance"></a>DB 设计指南

- 在可能的情况下，将计算列和度量值推送到源 - 距离源越近，性能提升的可能性就越高。
- 优化！ 了解查询的执行计划，为常用筛选列等添加索引等。

### <a name="modeling-guidance"></a>建模指南

- 从 Power BI Desktop 开始。
- 避免在查询编辑器中定义复杂的查询。
- 请勿在查询编辑器中使用相对日期筛选。  
- 最初保持简化度量值，然后以增量方式增加复杂性。
- 避免计算列和唯一标识符列之间存在关系。
- 尝试在关系上设置“假设引用完整性” - 在很多情况下，这可以显著提高查询性能。  

### <a name="general"></a>常规

- 首次应用筛选器。
- 考虑关闭视觉对象之间的交互 - 这将有助于降低用户交叉突出显示时的查询负载。
- 如上所述，限制视觉对象的数量和每个视觉对象的数据。
- 启用“行级别安全性”可能会导致性能发生重大变化。 确保测试用户假定的不同行级别的安全角色。
- 服务会强制执行查询级别超时，以确保长时间运行的查询无法独占系统资源。 超过 225 秒的查询将超时并导致视觉对象级别错误。

## <a name="understand-dashboards-and-query-caches"></a>了解仪表板和查询缓存

当加载仪表板时，固定到仪表板的视觉对象由查询缓存提供。 相反，在访问报表时，会在运行时生成针对数据源的查询 - Power BI 服务（在导入情况下）或你指定的数据源（在 DirectQuery 或实时连接的情况下）。  

> [!NOTE]
> 将实时报表磁贴固定到仪表板上时，它们不会从查询缓存中提供，相反，它们的行为类似于报表，会在运行时对后端核心进行查询。

顾名思义，与依赖数据源相比，从查询缓存中检索数据可提供更好、更稳定的性能。 利用此功能的一种方法是将仪表板作为用户的首个登录页。 将经常使用且请求次数较高的视觉对象固定到仪表板。 通过这种方式，仪表板成为有价值的“第一道防线”，可通过容量上的较低负载提供稳定的性能。 用户仍然可以单击查看报表以了解详情。  
 

对于 DirectQuery 和实时连接，此查询缓存是通过查询数据源进行定期更新的。 默认情况下，更新频率为每小时一次，不过也可以在数据集设置中进行配置。 每个查询缓存更新都会将查询发送到基础数据源来更新缓存。 生成的查询数量取决于在依赖于该数据源的仪表板上固定的视觉对象数量。 请注意，如果启用了“行级别安全性”，则会为每个不同的安全性上下文生成查询。 例如，如果你具有用户可以使用的两种不同角色与两种不同的数据视图，则在查询缓存刷新期间会生成两组查询。 

## <a name="understand-custom-visual-performance"></a>了解自定义视觉对象性能 

确保将每个自定义的视觉对象通过其节奏来确保高性能。 自定义视觉对象优化欠佳可能会对整个报表性能产生负面影响。 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>通过 SQL 事件探查器和 Power BI Desktop 深入探索查询性能

要深入了解哪些视觉对象占用最多时间和资源，可以将 SQL 事件探查器连接到 Power BI Desktop，以对查询性能有一个全面的了解。

> [!NOTE]
> Power BI Desktop 支持连接到诊断端口。 诊断端口允许连接到其他工具并执行跟踪以进行诊断。 不支持对模型进行任何更改！更改模型可能会导致损坏和数据丢失。

说明如下所示：
  
1. **安装 SQL Server Profiler 并运行 Power BI Desktop** 

   SQL Server Profiler 作为 SQL Server Management Studio 的一部分提供。

2. **确定 Power BI Desktop 正在使用的端口**

   使用管理员特权运行命令提示符或 PowerShell，并使用 netstat 查找 Power BI Desktop 正在用于分析的端口：

   `> netstat -b -n`

   输出应该是应用程序及其开放端口的列表，例如：  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   查找 msmdsrv.exe 使用的端口，并将其写下来以供将来使用。 在本例中，可以使用端口 55786。
3. **将 SQL Server Profiler 连接到 Power BI Desktop**

   - 从“开始”菜单启动 SQL Server Profiler
   - “文件” > “新建跟踪”
   - 服务器类型：Analysis Services
   - 服务器名称：localhost:[上面找到的端口号]
   - 在下一个屏幕中，选择“运行”
   - 现在，SQL 事件探查器处于活动状态，并主动分析 Power BI Desktop 发送的查询。 
   - 执行查询时，你可以看到它们各自的持续时间和 CPU 时间，使用这些信息可以确定哪些查询是瓶颈。  

通过 SQL 事件探查器，可以识别占用最长 CPU 时间的查询，这相对可能就是性能瓶颈。 执行这些查询的视觉对象应成为持续优化的焦点。

## <a name="gateway-best-practices"></a>网关最佳做法

本地数据网关是将 Power BI 服务与本地数据连接的一个非常有用的工具。 同时，如果规划不善，也可能成为报表性能的瓶颈。 对于 DirectQuery/实时连接数据集来说更是如此，其中所有查询和查询响应通过网关传输。 以下是确保高性能网关的一些最佳做法： 

- 使用企业模式，而不是个人模式。
- 针对网关建议的硬件规格 - 八个 CPU 内核、16 GB RAM。
- 设置监视 - 在网关计算机上设置性能监视，了解网关是否变得过载而成为瓶颈。 有关详细信息，请参阅[本地数据网关故障排查](service-gateway-onprem-tshoot.md)。
- 纵向扩展或扩大 - 如果网关确实成为瓶颈，则考虑纵向扩展（即，将网关移至有更多 CPU 和 RAM 的功能更强大的计算机上），或扩大（例如，将数据集拆分到不同的网关）。 
- 单独导入与 DirectQuery - 如果扩大，请考虑将负责导入的网关与负责 DirectQuery 的网关分开。

## <a name="network-latency"></a>网络延迟

网络延迟可增加请求到达 Power BI 服务以及传输响应所需的时间，从而影响报表的性能。 Power BI 中的租户被分配一个特定区域。 通过导航到 powerbi.com，在右上角选择“?”，然后选择“关于 Power BI”，可查看租户的“主页”区域。 当来自租户的用户访问 Power BI 服务时，他们的请求将始终被路由到此区域。 请求到达 Power BI 服务后，服务就可以发送其他请求（例如，到基础数据源或网关的请求），这也会受到网络延迟的影响。

诸如 [Azure 速度测试](http://azurespeedtest.azurewebsites.net/)之类的工具，可以提供客户端与 Azure 区域之间的网络延迟的指示。 一般来说，为了尽量降低网络延迟的影响，请争取使数据源、网关和 Power BI 群集尽可能地靠近。 如果网络延迟成为一个问题，你可以尝试通过将网关和数据源放在虚拟机上来查找与 Power BI 群集更近的网关和数据源。

要进一步改善网络延迟状况，请考虑使用 [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/)，它能够在客户端与 Azure 数据中心之间创建更快、更可靠的网络连接。

## <a name="next-steps"></a>后续步骤

- [规划 Power BI 企业部署](https://aka.ms/pbienterprisedeploy)，并提供有关大规模 Power BI 部署的全面指导
- [SQL Server 2016 Analysis Services 中的 DirectQuery](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] 在 Power BI 中构建快速可靠的报表](https://www.youtube.com/watch?v=GhiJABR7XX0)
- [[YouTube] Power BI 企业部署](https://www.youtube.com/watch?v=K-zEWICvICM)
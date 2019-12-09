---
title: 管理 Microsoft Power BI Premium 容量
description: 介绍 Power BI Premium 容量的管理任务。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 2e32a61891cee2fb5e2a80167d5283962dc164bb
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74697465"
---
# <a name="managing-premium-capacities"></a>管理高级容量

管理 Power BI Premium 涉及创建、管理和监视 Premium 容量。 本文概要介绍容量；有关分步说明，请参阅[配置和管理容量](service-admin-premium-manage.md)。

## <a name="creating-and-managing-capacities"></a>创建和管理容量

Power BI 管理门户的“容量设置”页面显示已购买的 vCore 数和可用的 Premium 容量  。 在此页面中，Office 365 全局管理员或 Power BI 服务管理员可以从可用的 vCore 创建 Premium 容量，或修改现有的 Premium 容量。

创建 Premium 容量时，需要管理员定义以下内容：

- 容量名称（在租户中是唯一的）。
- 容量管理员（一个或多个）。
- 容量大小。
- 用于数据驻留的区域。

至少必须分配一个容量管理员。 分配为容量管理员的用户可以：

- 将工作区分配给该容量。
- 管理用户权限，以添加额外的容量管理员或具有分配权限的用户（使其能够将工作区分配到容量）。
- 管理工作负载，以配置分页报表和数据流工作负载的最大内存使用率。
- 重新启动容量，以重置系统重载后的所有操作。

容量管理员无法访问工作区内容（除非已在工作区权限中明确分配权限）。 除此之外，容量管理员还无权访问 Power BI 管理员权限范围内的所有内容（除非已明确分配权限），如使用情况指标、审核日志或租户设置。 重要的是，容量管理员无权创建新的容量或缩放现有容量。 管理员按容量分配，确保它们只能查看和管理为其分配的容量。

从 SKU 选项的可用列表中选择容量大小，此列表受池中可用的 vCore 数的限制。 可以从池中创建多个容量，池可以来自一个或多个已购买的 SKU。 例如，P3 SKU（32 个 vCore）可用于创建三个容量：一个 P2（16 个 vCore）和两个 P1（2 x 8 个 vCore）。 通过创建更小的容量，可以提升性能和规模，如[优化 Premium 容量](service-premium-capacity-optimize.md)一文中所述。 下图显示了虚构的 Contoso 组织的示例设置，该组织包含五个 Premium 容量（3 个 P1 和 2 个 P3），每个功能都包含多个工作区，以及共享容量中的几个工作区。

![虚构 Contoso 组织的示例设置](media/service-premium-capacity-manage/contoso-organization-example.png)

可以将 Premium 容量分配到 Power BI 租户的主区域以外的区域，这称为多地理位置。 多地理位置提供对 Power BI 内容所在的已定义地理区域内的数据中心的管理控制。 部署多地理位置通常是为了实现公司或政府合规性，而不是为了提升性能和规模。 加载报表和仪表板仍涉及对主区域元数据的请求。 若要了解详细信息，请参阅 [Power BI Premium 的多地理位置支持](service-admin-premium-multi-geo.md)。

Power BI 服务管理员和 Office 365 全局管理员可以修改 Premium 容量。 具体而言，他们可以：

- 更改容量大小以增加或减少资源。
- 添加或删除容量管理员。
- 添加或删除具有分配权限的用户。
- 添加或删除其他工作负载。
- 更改区域。

向特定的 Premium 容量分配工作区需要具有分配权限。 可以向整个组织、特定用户或组授予权限。

默认情况下，Premium 容量仅支持与当前运行的 Power BI 查询关联的工作负载。 Premium 容量还支持其他工作负载：AI（认知服务）、分页报表和数据流    。 每个工作负载都要求配置工作负载可使用的最大内存（以占可用内存总量的百分比的形式）。 请务必了解，增加最大内存分配可能会影响可托管的活动模型的数量和刷新的吞吐量。 

内存动态分配给数据流，但静态分配给分页报表。 静态分配最大内存是因为分页报表在容量的安全包含空间中运行。 设置分页报表内存时应小心谨慎，因为它会减小用于加载模型的可用内存。 若要了解详细信息，请参阅[默认内存设置](service-admin-premium-workloads.md#default-memory-settings)。

删除 Premium 容量时，不会同时删除其工作区和内容。 但是，它会将任何已分配的工作区移动到共享容量。 在不同的区域中创建 Premium 容量时，会将工作区移动到主区域的共享容量。

### <a name="assigning-workspaces-to-capacities"></a>将工作区分配到容量

可以在 Power BI 管理门户中将工作区分配到 Premium 容量，也可以在“工作区”  窗格中为工作区分配工作区。

容量管理员以及 Office 365 全局管理员或 Power BI 服务管理员可以在 Power BI 管理门户中批量分配工作区。 批量分配适用于：

- **用户拥有的工作区** - 向 Premium 容量分配这些用户拥有的所有工作区（包括个人工作区）。 如果已将工作区分配给不同的 Premium 容量，则会重新分配工作区。 此外，还会为用户分配工作区分配权限。

- 特定工作区 
- **整个组织的工作区** - 向 Premium 容量分配所有工作区（包括个人工作区）。 为所有现有和未来的用户分配工作区分配权限。 不建议使用此方法。 请首选更具针对性的方法。

可以使用“工作区”  窗格将工作区分配到 Premium 容量，前提是用户既是工作区管理员，又具有分配权限。

![使用“工作区”窗格将工作区分配到 Premium 容量](media/service-premium-capacity-manage/assign-workspace-capacity.png)

工作区管理员可以在不需要分配权限的情况下从容量中删除工作区（并分配到共享容量）。 从专用容量中删除工作区可以有效地将工作区重分配到共享容量。 请注意，从 Premium 容量中删除工作区可能会带来负面影响，例如，导致共享内容无法供 Power BI（免费）许可用户使用，或者当计划的刷新量超出共享容量所支持的配额时，将暂停计划刷新。

在 Power BI 服务中，可以通过带有工作区名称的菱形图标轻松识别分配给 Premium 容量的工作区。

![识别分配给 Premium 容量的工作区](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>监视容量

监视 Premium 容量可使管理员了解容量的实时情况。 可使用 Power BI 管理门户或 Power BI Premium 容量指标 (Power BI) 应用  来监视容量。

### <a name="power-bi-admin-portal"></a>Power BI 管理门户

在管理门户中，为每个容量提供“运行状况”选项卡，显示容量和每个已启用工作负载的摘要指标  。 指标显示过去七天的平均值。  

在容量级别，指标是已启用的所有工作负载的累积量。 提供以下指标：

- **CPU 使用率** - 提供平均 CPU 使用率（以占容量可用 CPU 总量的百分比的形式）。  
- **内存使用率** - 提供平均内存使用率 (GB)（以占容量可用内存总量的百分比的形式）。 

对于每个已启用的工作负载，提供了 CPU 使用率和内存使用率，还提供了特定于工作负载的大量指标。 例如，对于数据流工作负载，总计计数显示每个数据流的总刷新次数，平均持续时间显示数据流的平均刷新持续时间   。

![门户中的“容量运行状况”选项卡](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

若要详细了解每个工作负载的所有可用指标，请参阅[在管理门户中监视容量](service-admin-premium-monitor-portal.md)。

Power BI 管理门户中的监视功能旨在提供关键容量指标的快速摘要。 若要进行更详细的监视，建议使用 Power BI Premium 容量指标  应用。

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium 容量指标应用

[Power BI Premium 容量指标应用](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview)是一种可供容量管理员使用的 Power BI 应用，它的安装方式与任何其他 Power BI 应用类似。 它包含一个仪表板和一个报表。

![Power BI Premium 容量指标应用](media/service-premium-capacity-manage/capacity-metrics-app.png)

打开应用后，将加载仪表板以显示许多磁贴，这些磁贴表示用户作为容量管理员的所有容量的聚合视图。仪表板布局包括五个主要部分：

- **概述** - 应用版本、容量和工作区数量
- **系统摘要** - 内存和 CPU 指标
- **数据集摘要** - 数据集、DQ/LC、刷新和查询指标的数目
- **数据流摘要** - 数据流和数据集指标的数目
- **分页报表摘要** - 刷新和查看指标

通过单击任何仪表板磁贴，可以访问在其中固定了仪表板磁贴的基础报表。 它提供每个仪表板部分的更详细透视，并支持交互式筛选。 

可以按日期范围、容量、工作区和工作负载荷（报表、数据集、数据流）设置切片器，以及选择报表视觉对象中的元素以交叉筛选报表页，通过这些方式实现筛选。 交叉筛选是一种功能强大的技术，可用于将范围缩小到特定时间段、容量、工作区、数据集等，而且它在执行根本原因分析时非常有用。

有关应用中的仪表板和报表指标的详细信息，请参阅[通过应用监视 Premium 容量](service-admin-premium-monitor-capacity.md)。

### <a name="interpreting-metrics"></a>解释指标

应监视指标以基本了解资源使用情况和工作负载活动。 如果容量变慢，请务必了解要监视哪些指标以及可以得出的结论。

理想情况下，查询应在一秒钟内完成，以便向报表用户提供响应体验并实现更高的查询吞吐量。 如果后台进程（包括刷新）需要较长的时间才能完成，通常不必担心。

一般情况下，报表较慢可能表示容量过热。 如果无法加载报表，表明容量已过热。 在这两种情况下，根本原因都可以归因于多种因素，其中包括：

- **查询失败**：这无疑表明内存不足，并且无法将模型加载到内存中。 失败之前，Power BI 服务将尝试加载模型 30 秒钟。

- **查询等待时间过长**：这可能是由以下几个原因所致：
  - Power BI 服务首先需要逐出模型，然后加载要查询的模型（回想一下，仅凭较高的数据集逐出速度并不足以指示容量不足，除非同时还出现以下情况：长时间的查询等待时间指示内存抖动剧烈）。
  - 模型加载时间（尤其是等待将大型模型加载到内存中的时间）。
  - 长时间运行查询。
  - LC\DQ 连接过多（超出容量限制）。
  - CPU 饱和。
  - 页面上设计有大量视觉对象的复杂报表（回想一下，每个视觉对象都是一个查询）。

- **较长的查询持续时间**：可能指示模型设计未得到优化，特别是在容量中有多个数据集处于活动状态时，只有一个数据集产生较长的查询持续时间。 这表明容量有足够的资源，并且出现此问题的数据集不是最优的，或者只是查询速度很慢。 长时间运行的查询可能会出现问题，因为它们会阻止对其他进程所需资源的访问。
- **较长的刷新等待时间**：表示内存不足，因为许多活动模型占用内存，或者有问题的刷新阻止了其他刷新（超出了并行刷新限制）。

[优化 Premium 功能](service-premium-capacity-optimize.md)一文中详细介绍了如何使用所述的这些指标。

## <a name="acknowledgements"></a>致谢

本文由 Peter Myers、数据平台 MVP 和独立的 BI 专家通过 [Bitwise Solutions](https://www.bitwisesolutions.com.au/) 撰写。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [优化 Premium 容量](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [在 Premium 容量中配置工作负载](service-admin-premium-workloads.md)   

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


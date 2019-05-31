---
title: 管理 Microsoft Power BI Premium 容量
description: 描述用于 Power BI Premium 容量管理任务。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565247"
---
# <a name="managing-premium-capacities"></a>管理高级容量

管理 Power BI Premium 涉及创建、 管理和监视高级容量。

## <a name="creating-and-managing-capacities"></a>创建和管理容量

**容量设置**Power BI 管理门户页将显示购买的 v 核心和可用的高级容量的数量。 页面允许 Office 365 全局管理员或 Power BI 服务管理员，若要从可用的 v 核心，创建高级容量或修改现有的高级容量。

在创建高级容量时，管理员需要定义：

- 容量名称 （在租户中唯一）。
- 容量管理员。
- 容量大小。
- 针对数据驻留位置的区域。

必须分配至少一个容量管理员。 作为容量管理员分配的用户可以：

- 将工作区分配给容量。
- 管理用户权限时，若要添加更多容量管理员或具有分配权限 （以使他们能够向容量分配工作区） 的用户。
- 管理工作负荷，若要配置分页的报表和数据流工作负荷的最大内存使用情况。
- 重新启动的容量，由于系统超载重置所有操作。

容量管理员不能访问工作区内容，除非显式分配在工作区的权限。 它们还没有所有 Power BI 管理员区域访问权限 （除非显式分配） 的使用情况指标、 审核日志或租户设置等。 重要的是，容量管理员不有权创建新的容量或扩展现有的容量。 管理员分配在每个容量的基础上，确保它们可以仅查看和管理它们分配到的容量。

从可用的 SKU 选项列表的池中的可用 v 核心数仅限于选择容量大小。 可以从该池，可以从一个来源创建多个容量或更多购买 Sku。 例如，P3 SKU （32 个 v 核心） 无法用于创建三个容量： 一个 P2 (16 个 v 核心），和两个 P1 （2 x 8 虚拟核心）。 改进的性能和缩放可以通过创建较小大小的容量，如中所述[优化高级容量](service-premium-capacity-optimize.md)一文。 下图显示了一个虚构的 Contoso 组织包含五个高级容量的设置的示例 (3 倍 P1 版和 2 x P3) 与每个包含的应用工作区，并在共享容量中的多个工作区。

![虚构的 Contoso 组织的一个设置示例](media/service-premium-capacity-manage/contoso-organization-example.png)

高级容量可分配给名为多地域的 Power BI 租户主区域以外的区域。 多地域提供对 Power BI 内容驻留规定的地理区域内的数据中心的管理控制。 多地域部署的基本原理通常是为企业或政府法规遵从性，而不是性能和规模。 报表和仪表板加载仍然需要对元数据的主区域的请求。 若要了解详细信息，请参阅[对 Power BI Premium 的多地域支持](service-admin-premium-multi-geo.md)。

Power BI 服务管理员和 Office 365 全局管理员可以修改高级容量。 具体而言，他们可以：

- 更改容量大小增加或缩减资源。
- 添加或删除容量管理员。
- 添加或删除具有分配权限的用户。
- 添加或删除额外的工作负载。
- 更改区域。

分配权限需要为特定的高级容量分配工作区。 可以向整个组织、 特定用户或组授予权限。

默认情况下，高级容量支持与运行 Power BI 查询相关联的工作负荷。 高级容量还支持其他工作负载：**AI （认知服务）** ，**分页报表**，和**数据流**。 每个工作负荷需要配置可由工作负荷的最大内存 （作为总可用内存的百分比表示）。 请务必了解增加最大内存分配可能会影响可托管的活动模型数和刷新的吞吐量。 

内存动态分配到数据流，但以静态方式分配给分页报表。 以静态方式分配的最大内存的原因是分页的报表运行在受保护包含空间的容量中。 设置分页报表内存，因为它减少了加载模型的可用内存时应小心。 若要了解详细信息，请参阅[默认内存设置](service-admin-premium-workloads.md#default-memory-settings)。

正在删除高级容量可能并不会导致其工作区和内容的删除。 相反，它将任何已分配的工作区移动到共享容量。 不同的区域中创建的高级容量，在工作区移动到共享容量中的主区域。

### <a name="assigning-workspaces-to-capacities"></a>将工作区分配到容量

工作区可以在分配给高级容量在 Power BI 管理门户中，或为应用工作区，**工作区**窗格。

容量管理员和 Office 365 全局管理员或 Power BI 服务管理员，可以批量分配工作区在 Power BI 管理门户中。 大容量分配可以应用于：

- **按用户分配工作区**-包括个人工作区，这些用户拥有的所有工作区分配给高级容量。 当已经将它们分配到不同的高级容量时，这将包括工作区重新的分配。 此外，用户还分配工作区分配权限。

- 特定工作区 
- **整个组织的工作区**-所有工作区，包括个人工作区分配给高级容量。 所有当前和未来用户分配工作区分配权限。 不建议使用此方法。 一个更有针对性的方法是首选。

工作区可以通过使用添加到高级容量**工作区**窗格提供用户的这两个工作区管理员和具有分配权限。

![使用工作区窗格中，若要将工作区分配到高级容量](media/service-premium-capacity-manage/assign-workspace-capacity.png)

工作区管理员可以删除从容量 （到共享容量） 工作区，而无需分配权限。 有效地从专用容量中删除工作区将重新在工作区分配到共享容量中。 请注意，从高级容量中删除工作区可能有负面影响生成，例如，在共享的内容变得不可用到 Power BI 免费版中获得许可的用户或计划刷新的挂起时它们超出了支持的限额通过共享容量。

在 Power BI 服务中，由装饰的工作区名称的菱形图标轻松地标识分配给高级容量的工作区。

![标识工作区分配给高级容量](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>监视容量

监视高级容量为管理员提供了如何执行容量的了解。 可以使用 Power BI 管理门户监视容量或**Power BI Premium 容量指标**(Power BI) 应用。

### <a name="power-bi-admin-portal"></a>Power BI 管理门户

在管理员门户中，为每个容量**运行状况**选项卡上提供的容量和每个已启用的工作负荷的汇总指标。 度量值显示过去七天内的平均值。  

在容量级别中，指标是累积的所有已启用工作负荷。 提供以下指标：

- **CPU 使用率**-提供占总可用 CPU 的平均 CPU 利用率的容量。  
- **内存使用情况**-提供平均值 （以 gb 为单位） 的容量的可用内存的总的内存使用情况。 

对于每个已启用的工作负荷，CPU 使用率和内存使用情况提供以及大量的工作负荷特定度量值。 例如，对于数据流工作负荷，**总计数**显示总刷新每个数据流，并**平均持续时间**显示数据流的刷新的平均持续时间。

![在门户中的容量运行状况选项卡](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

若要了解有关每个工作负荷的所有可用度量值的详细信息，请参阅[监视在管理门户中的容量](service-admin-premium-monitor-portal.md)。

在 Power BI 管理门户中的监视功能旨在提供关键的容量指标的快速摘要。 有关更多详细监视，建议使用**Power BI Premium 容量指标**应用。

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium 容量指标的应用程序

[Power BI Premium 容量度量值应用](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview)容量管理员可对 Power BI 应用，并且安装其他任何 Power BI 应用一样。 它包含仪表板和报表。

![Power BI Premium 容量指标的应用程序](media/service-premium-capacity-manage/capacity-metrics-app.png)

应用程序打开后，加载仪表板提供大量磁贴表达的聚合的视图通过所有容量用户的容量管理员。仪表板布局包括五个主要部分：

- **概述**-应用程序版本、 数量的容量和工作区
- **系统摘要**-内存和 CPU 指标
- **数据集摘要**-数字的数据集、 DQ/LC、 刷新和查询指标
- **数据流摘要**-号码数据流，以及数据集度量值
- **分页报表摘要**-刷新和查看指标

可以通过单击任何仪表板磁贴访问基础报表，从该仪表板磁贴已固定。 它提供的每个仪表板部分更详细的观点，并支持交互式筛选。 

筛选可以实现通过设置切片器的日期范围、 容量、 工作区和工作负荷 （报表、 数据集，数据流），并通过选择报表中的元素视觉对象以交叉筛选报表页。 交叉筛选是一种功能强大的技术，可缩小到特定时间段、 容量、 工作区，数据集等，并执行根本原因分析时可能非常有用。

有关在应用中的仪表板和报表度量值的详细信息，请参阅[与该应用程序监视器高级容量](service-admin-premium-monitor-capacity.md)。

### <a name="interpreting-metrics"></a>解释指标

应该监视度量值来建立一个基本了解资源使用情况和工作负荷活动。 如果容量变得缓慢，务必了解要监视的指标，还可得出的结论。

理想情况下，查询应在向报表用户提供响应式体验，并启用更高的查询吞吐量一秒钟内完成。 它通常是问题的考虑的较小时 （包括刷新） 的背景过程要花费更长的时间才能完成。

一般情况下，慢速报告可能会过度加热容量的指示。 时报表将无法加载，这是过度加热容量的指示。 在任一情况下，根本原因可能是因引起的许多因素，包括：

- **查询失败**肯定指示内存压力和模型无法加载到内存中。 在 Power BI 服务将尝试加载模型，在失败之前的 30 秒。

- **过多的查询等待时间**可以是由于多种原因引起：
  - 需要为第一个 Power BI 服务中收回模型，然后加载要查询的模型 （回想一下，更高版本数据集逐出费率单独不相对值的指示容量压力，除非查询的长时间等待指示内存抖动附带）。
  - 模型加载时间 （尤其是等待加载到内存的大型模型）。
  - 长时间运行查询。
  - （超出容量限制） 的 LC\DQ 连接过多。
  - CPU 饱和所致。
  - 在页上 （回想一下每个视觉对象是一个查询） 的复杂报表设计与视觉对象的次数过多。

- **长查询持续时间**可以指示，模型设计未得到优化，尤其是在多个数据集处于活动状态中的容量，并只有一个数据集是否生成长时间查询持续时间。 这表明，足够的资源容量，并在问题数据集是非最优或只是速度缓慢。 长时间运行的查询可能存在问题，因为它们可以阻止其他进程所需的资源的访问权限。
- **长时间刷新等待时间**指示由于多个活动模型消耗的内存，内存不足或有问题的刷新阻止其他刷新 （超过并行刷新限制）。

中介绍了如何使用指标的更多详细的说明[优化高级容量](service-premium-capacity-optimize.md)一文。

## <a name="acknowledgements"></a>确认

撰写本文时由 Peter Myers、 数据平台 MVP 和独立 BI 专家[位解决方案](https://www.bitwisesolutions.com.au/)。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [优化高级容量](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [在高级容量中配置工作负荷](service-admin-premium-workloads.md)   

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

||||||

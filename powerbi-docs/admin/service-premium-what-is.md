---
title: 什么是 Microsoft Power BI Premium？
description: Power BI Premium 为组织提供容量，可带来更可靠的性能和更大的数据卷，而无需购买每用户许可证。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 01/18/2021
ms.custom: licensing support
LocalizationGroup: Premium
ms.openlocfilehash: c89cf7b00d5167ffb68a491a9cfdcea21378dfd5
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565163"
---
# <a name="what-is-power-bi-premium"></a>什么是 Power BI Premium？

可以使用 Power BI Premium 来访问仅 Premium 中提供的功能，并为组织中的 Power BI 内容提供更大的规模和更佳的性能。 借助 Power BI Premium，组织中的更多用户能够充分利用 Power BI，同时获得更好的性能和响应能力。 例如，借助 Power BI Premium，你和组织用户可获得以下功能：

> [!div class="checklist"]
> * Power BI 报表的规模更大，性能更强
> * 灵活地按容量许可
> * 一流的数据可视化和见解提取功能，例如 AI 驱动的分析，可组合和可重用的数据流以及分页报表
> * 通过各种仅限 Premium 的功能将自助服务和企业 BI 统一起来，这些功能可支持繁重的工作负载并在企业规模上实现
> * 内置许可证的作用是通过 Power BI 报表服务器扩展本地 BI
> * 支持按区域（多地区）提供的数据驻留和用于静态数据的客户管理的加密密钥 (BYOK)
> * 无需购买每用户许可证即可与任何人（甚至在组织外部）共享 Power BI 内容


![屏幕截图显示 Power BI 管理门户。](media/service-premium-what-is/premium-admin-portal.png) 

本文介绍了 Power BI Premium 中的主要功能。 必要时，提供包含更多详细信息的其他文章的链接。 有关 Power BI Pro 和 Power BI Premium 的详细信息，请参阅 [Power BI 定价](https://powerbi.microsoft.com/pricing/)的“Power BI 功能比较”部分。

## <a name="power-bi-premium-generation-2-preview"></a>Power BI Premium Generation 2（预览版）

Power BI Premium 最近发布了 Power BI Premium 的新版本，即 Power BI Premium Generation 2，为方便起见，我们将其称为 Premium Gen2 。 Premium Gen2 目前以预览版提供，可供 Premium 订阅者在预览期间使用。 可以选择使用原始版本的 Premium，也可以切换为使用 Premium Gen2。 只能将其中一个用于高级容量。

Premium Gen2 提供以下更新或改进的体验：

* 除按容量提供外，还可以提供 Premium Per User 许可。

* 可随时增强任何容量大小上的性能：在 Premium Gen2 上，“分析操作”的运行速度可提升最高 16 倍。 当容量上的负载接近容量限制时，操作始终以最快的速度执行，不会降低速度。

* **更大规模**：
    * 对刷新并发次数没有限制，不再要求跟踪在容量上刷新的数据集计划
    * 较少的内存限制
    * 报表交互和计划刷新之间完全隔离

* 使用清晰且标准化的容量使用率数据改进了指标，该数据仅取决于容量执行的分析操作的复杂度，而不取决于容量的大小、执行分析时系统的负载级别或其他因素。 通过改进的指标，利用内置的报表可以清楚地了解利用率分析结果、预算计划、退款和升级需求。 将在预览期间的稍后时间提供改进后的指标。 希望访问过去 7 天的使用指标的客户可联系客户支持人员来完成此操作。 

* 自动缩放允许当容量上的负载超过其限制时在 24 小时内的某个时间自动添加 1 个 V 核心，防止因过载而导致速度降低。 当检测到空闲时间时，将自动删除 V 核心。 额外的 V 核心按即用即付方式向 Azure 订阅收费。 自动缩放将在预览期间提供。 

* 降低了管理开销，同时提供有关容量使用率级别和负载增加的主动和可配置管理员通知。


### <a name="using-premium-gen2"></a>使用 Premium Gen2

启用 Premium Gen2 以利用其更新。 若要启用 Premium Gen2，请执行以下步骤：

1. 在管理门户中，导航到“容量设置”。
2. 选择“Power BI Premium”。
3. 随即出现某个标题为“Premium Generation 2(预览版)”的部分，该部分中有一个用于启用 Premium Generation 2（预览版）的滑块。 
4. 将滑块移至“已启用”。

下图显示了如何启用 Premium Gen2。 

![启用 Premium Generation 2](media/service-premium-what-is/enable-premium-gen2.gif#lightbox) 

### <a name="known-limitations-in-premium-gen2"></a>Premium Gen2 中的已知限制

以下已知限制目前适用于 Premium Gen2：

1.    无法在指标应用中跟踪 Premium Gen2 容量使用率。

2.    管理门户的 Premium Gen2 容量设置页面中尚不显示适用于特定工作负载的 Premium Gen2 容量设置。 若要更改设置，请将容量转换为 Premium 的原始版本，更改设置，然后再次将容量设置为使用 Premium Gen2。 内存分配设置不适用于 Premium Gen2 容量。

3.  如果在 Premium Gen2 上使用 XMLA，请确保使用的是[数据建模和管理工具](service-premium-connect-tools.md#data-modeling-and-management-tools)的最新版本。 

4.  只有最新的客户端库支持 Premium Gen2 中的 Analysis services 功能。 支持此要求的相关工具的预计发布日期如下：

    |工具|所需最低版本|预计发布日期|
    |---|---|---|
    |SQL Server Management Studio (SSMS)|18.8|2020 年 12 月 8 日|
    |SQL Server Data Tools (SSDT)|2.9.15|2020 年 12 月 30 日正式发布|
    | AS PowerShell| 大于 21.1.18229|2020 年 11 月 26 日|

5.  不支持将包含数据流的工作区从一个 Premium Gen2 容量重新分配到另一个区域中的另一个 Premium 容量。 也不支持将大型存储格式模型从一个 Premium 容量移到另一个 Premium 容量。 如果已迁移到其他区域中的容量，请执行以下步骤之一来还原功能：
 
    1.  创建新工作区并复制数据流
    2.  将工作区迁移回先前区域中的容量
    3.  切换回 Premium Gen 1

Premium Gen 2 正式发布 (GA) 时，可能会删除此限制。


## <a name="subscriptions-and-licensing"></a>订阅和许可

Power BI Premium 是租户级别的 Microsoft 365 订阅，可在两个 SKU（库存单位）系列中使用：

- P SKU (P1-P5)：用于嵌入和企业功能，需要包月或包年承诺，并按月计费，包含用于在本地安装 Power BI 报表服务器的许可证。

- 用于组织嵌入的 EM SKU (EM1-EM3)，要求按年承诺并按月计费。 EM1 和 EM2 SKU 仅通过批量许可计划提供， 无法直接购买。

### <a name="purchasing"></a>购买

Power BI Premium 订阅由 Microsoft 365 管理中心的管理员购买。 具体而言，仅全局管理员或计费管理员才能购买 SKU。 购买时，租户会收到相应数量的 V 核心用于分配给容量，这称为 *V 核心池*。 例如，购买 P3 SKU 会为租户提供 32 个 V 核心。 若要了解详细信息，请参阅[如何购买 Power BI Premium](service-admin-premium-purchase.md)。

#### <a name="power-bi-premium-per-user-preview"></a>Power BI Premium Per User（预览版）

借助 Power BI Premium Per User，组织能够在用户级别上提供高级功能许可。 Premium Per User (PPU) 包括所有 Power BI Pro 许可证功能，增加了分页报表、AI 和其他仅面向高级订阅者的功能。 Premium Per User 目前以预览版提供。 有关 Premium Per User 的详细信息，包括功能比较和有关预览版的其他信息，请参阅 [Power BI Premium Per User 常见问题解答（预览版）](service-premium-per-user-faq.md)。 


## <a name="reserved-capacities"></a>预留容量

使用 Power BI Premium，可以获得预留容量。 共享容量的工作负载分析处理在与其他客户共享的计算资源上运行，与之相反，预留容量仅供组织使用。 预留容量与预留计算资源分离，为托管内容提供可靠且一致的性能。 请注意，以下类型的 Power BI 处理内容存储在共享容量中，而不是预留容量中：

* Excel 工作簿（除非是首次将数据导入 Power BI Desktop）
* [推送数据集](/rest/api/power-bi/pushdatasets)
* [流数据集](../connect-data/service-real-time-streaming.md#set-up-your-real-time-streaming-dataset-in-power-bi)
* [问答](../create-reports/power-bi-tutorial-q-and-a.md)

工作区驻留在容量范围内。 每个 Power BI 用户都有一个称为“我的工作区”的个人工作区。 可创建其他工作区来启用协作，这些工作区称为“工作区”。 默认情况下，工作区（包括个人工作区）在共享容量中创建。 如果拥有高级容量，可将“我的工作区”和“工作区”都分配给高级容量。

容量管理员会自动将其“我的工作区”分配给高级容量。

### <a name="updates-for-premium-gen2-preview"></a>Premium Gen2（预览版）的更新

Premium Gen 2 节点不再使用预留基础结构。 该服务通过从计算能力很强的计算节点的共享池中分配足够的资源来确保可为每个运行的工作负载提供足够的计算能力。


### <a name="capacity-nodes"></a>容量节点

如 [订阅和许可](#subscriptions-and-licensing)部分所述，有两个 Power BI Premium SKU 系列：**EM** 和 **P**。所有 Power BI Premium SKU 均可作为容量 *节点* 提供，每个节点代表由处理器、内存和存储组成的一定数量的资源。 除资源外，每个 SKU 还对每秒处理的 DirectQuery 和 Live Connection 连接的数量，以及并行模型刷新次数进行了操作限制。

处理由一定数量的 V 核心实现，并在后端和前端之间平均分配。

**后端 V 核心** 负责核心 Power BI 功能，包括查询处理、缓存管理、运行 R 服务、模型刷新以及在服务器端呈现报表和图像。 后端 V 核心分配到固定数量的内存，这些内存主要用于托管模型，也称为“活动数据集”。

**前端 V 核心** 负责 Web 服务、仪表板和报表文档管理、访问权限管理、时间安排、API、上传和下载，以及通常与用户体验相关的所有内容。

存储设置为 **每个容量节点 100 TB**。

每个 Premium SKU（和等效大小的 A SKU）的资源和限制如下表所述：

| 容量节点 | 总虚拟核心 | 后端 V 核心 | RAM (GB) | 前端 V 核心 | DirectQuery/Live Connection（每秒） | 模型刷新并行度 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 3 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 <sup>[1](#limit)</sup>| 64 | 32 | 200 | 32 | 240 | 48 |
| P5 <sup>[1](#limit)</sup>| 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

<a name="limit">1</a> - 仅限特殊请求。 适用于大于 100 GB 的超大模型。

>[!NOTE]
>使用单个较大的 SKU（例如一个 P2 SKU）可能比组合较小的 SKU（例如两个 P1 SKU）更可取。 例如，你可以使用更大的模型，还可以实现与 P2 的更好的并行。

#### <a name="updates-for-premium-gen2-preview"></a>Premium Gen2（预览版）的更新

使用 Premium Gen2，每种大小的节点的可用内存量将设置为单个项目的内存占用限额，而不是内存的累积消耗量。 例如，在原始 Premium 中，处理的数据集的总内存占用被限制为 25 GB，而在 Premium Gen2 中，则是单个数据集的大小限制为 25 GB。

### <a name="capacity-workloads"></a>容量工作负载

容量工作负载是为用户提供的服务。 默认情况下，Premium 和 Azure 容量仅支持与运行 Power BI 查询关联的数据集工作负载。 无法禁用数据集工作负载。 可以为 [AI（认知服务）](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/)、[数据流](../transform-model/dataflows/dataflows-introduction-self-service.md)和[分页报表](../paginated-reports/paginated-reports-save-to-power-bi-service.md)启用其他工作负载。 这些工作负载仅在 Premium 订阅中受到支持。 

每个额外的工作负载都允许配置工作负载可使用的最大内存（以占内存总容量的百分比的形式）。 最大内存的默认值由 SKU 确定。 通过在使用这些额外工作负载时仅启用这些额外工作负载，可以最大化容量的可用资源。 仅在已确定默认设置不满足容量资源要求时，才能更改内存设置。 通过使用[管理门户](service-admin-portal.md)中的“容量设置”，或通过使用[容量 REST API](/rest/api/power-bi/capacities)，容量管理员可以为容量启用和配置工作负载。  

![启用工作负载](media/service-admin-premium-workloads/admin-portal-workloads.png)

若要了解详细信息，请参阅[配置 Premium 容量中的工作负载](service-admin-premium-workloads.md)。 

### <a name="how-capacities-function"></a>容量工作原理

Power BI 服务始终充分利用容量资源，同时不超过对容量施加的限制。

容量操作分类为 *交互式操作* 和 *后台操作*。 交互式操作包括呈现请求和响应用户交互（筛选、问答查询等）。 后台操作包括数据流和导入模型刷新，以及仪表板查询缓存。

重点是了解交互式操作应始终优先于后台操作，以确保可能的最佳用户体验。 如果资源不足，则会将后台操作添加到等待队列中，直到释放资源。 后台操作（如数据集刷新）可以由 Power BI 服务在进程中中断并添加到队列中以及随后停用。

导入模型必须完全加载到内存中，以便可以查询或刷新它们。 Power BI 服务使用复杂的算法来公平比较内存使用情况，但在极少数情况下，如果没有足够的资源来满足客户的实时需求，容量可能会过载。 虽然可以将许多导入模型存储在持久性存储中（每个高级容量最多为 100 TB），但并不是所有的模型都必须同时驻留在内存中，否则其内存中的数据集大小可能很容易超出容量内存限制。 除了加载数据集所需的内存以外，还需要额外的内存来执行查询和刷新操作。

因此，导入模型会根据用途加载到内存中或从内存中移除。 在导入模型被查询（交互式操作）时，或需要刷新导入模型（后台操作）时，系统会加载导入模型。

从内存中移除模型称为 *逐出*。 这是 Power BI 可以根据模型的大小快速执行的操作。 如果容量没有经历任何内存压力并且模型未处于空闲状态（即，在使用中），则模型可以在内存中驻留，而不会被逐出。 当 Power BI 确定没有足够的内存来加载模型时，Power BI 服务将通过逐出不活动的模型来尝试释放内存，通常定义为在过去 3 分钟内未使用的交互式操作加载的模型 \[[1](#endnote-1)\]。 如果没有要逐出的非活动模型，则 Power BI 服务会尝试逐出为后台操作加载的模型。 在尝试失败 30 秒后\[[1](#endnote-1)\]，最终可尝试使交互操作失败。 在这种情况下，报表用户会收到失败通知以及尽快重试的建议。 在某些情况下，由于服务操作，模型可能会从内存中卸载。

需要强调的是，数据集逐出是对容量做出的正常行为。 容量旨在通过以对用户透明的方式管理模型的内存中生命周期来平衡内存使用量。 高逐出率并不一定意味着容量分配到的资源不足。 但是，如果查询或刷新性能因在短时间范围内反复加载和逐出模型的开销而降低，就会成为一个问题。

因为必须将模型加载到内存中，所以导入模型的刷新始终为内存密集型。 还需要额外的中间内存来进行处理。 完全刷新可以使用大约两倍于模型所需的内存量，因为 Power BI 在处理操作完成前一直在内存中维护模型的现有快照。 这样，即使在处理模型时，也能对其进行查询。 在刷新完成并且新的模型数据可用之前，可以将查询发送到模型的现有快照。

增量刷新执行分区刷新，而不是完全模型刷新，通常会更快，需要的内存更少，并且可以显著降低容量的资源使用率。 对于模型，刷新也可能为 CPU 密集型，特别是那些具有复杂 Power Query 转换的模型，或者复杂或基于大量数据的计算表/列。

和查询一样，刷新需要将模型加载到内存中。 如果内存不足，Power BI 服务将尝试逐出非活动模型；如果无法这样做（因为所有模型都处于活动状态），刷新作业将排队。 刷新通常为 CPU 密集型，其出现这种情况的概率甚至比查询出现这种情况的概率更大。 出于此原因，将强加对并发刷新次数的限制（以 1.5 倍后端虚拟核数的上限计算）。 如果并发刷新过多，则计划的刷新将一直排队等待，直到刷新槽可用，从而导致操作需要花费更长时间才能完成。 按需刷新（例如由用户请求或 API 调用触发的刷新）将重试三次\[[1](#endnote-1)\]。 如果仍然没有足够的资源，则刷新将失败。

#### <a name="updates-for-premium-gen2-preview"></a>Premium Gen2（预览版）的更新

Premium Gen2 不需要累积内存限制，因此并发数据集刷新不会影响资源约束。 每个虚拟核心运行的刷新数量没有限制。 但是，每个数据集的刷新仍受现有容量内存和 CPU 限制的制约。 可以在任何给定时间安排和运行所需次数的刷新，Power BI 服务将尽力在计划的时间运行这些刷新。

部分注释：   
<a name="endnote-1"></a>\[1\]可能会有所变化。

### <a name="regional-support"></a>区域支持

创建新容量时，全局管理员和 Power BI 服务管理员可以指定一个区域供分配给容量的工作区驻留。 这称为 **多地理位置**。 借助多地理位置，组织可以通过将内容部署到特定区域中的数据中心来满足数据驻留要求，即使它与 Microsoft 365 订阅所在的区域不同。 若要了解详细信息，请参阅 [Power BI Premium 的多地理位置支持](service-admin-premium-multi-geo.md)。

### <a name="capacity-management"></a>容量管理

管理 Premium 容量涉及创建或删除容量、分配管理员、分配工作区、配置工作负载、监视，以及进行调整来优化容量性能。 

全局管理员和 Power BI 服务管理员可以从可用的 V 核心创建 Premium 容量，或修改现有的 Premium 容量。 创建容量时会指定容量大小和地理区域，并分配至少一个容量管理员。 

创建容量后，大多数管理任务都在[管理门户](service-admin-portal.md)中完成。

![屏幕截图显示选中了“我的工作区”的 Power BI 管理门户。](media/service-premium-what-is/premium-admin-portal.png)

容量管理员可以将工作区分配给容量、管理用户权限以及分配其他管理员。 容量管理员还可以配置工作负载、调整内存分配，并在必要时重启容量，以及在容量过载的情况下重置操作。

![屏幕截图显示 Power BI 管理门户中的容量管理。](media/service-premium-what-is/premium-admin-portal-mgmt.png)

容量管理员还可以确保容量平稳运行。 他们可直接在管理门户中或通过使用 Premium 容量指标应用监视容量运行状况。

若要了解有关创建容量、分配管理员和分配工作区的详细信息，请参阅[管理 Premium 容量](service-premium-capacity-manage.md)。 若要了解有关角色的详细信息，请参阅[与 Power BI 相关的管理员角色](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)。

### <a name="monitoring"></a>监视

监视 Premium 容量可使管理员了解容量的表现。 可使用管理门户和 [Power BI Premium 容量指标应用](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics)来监视容量。

门户中的监视功能提供快速视图，其中包含指示已放置的负载以及过去七天内容量平均使用的资源量的高级指标。 

![屏幕截图显示 Power BI 管理门户中的容量运行状况。](media/service-premium-what-is/premium-admin-portal-health.png)

> [!NOTE]
> **Premium Gen2（预览版）的更新** - Premium Gen2 只需要监视一个方面：容量在任何时候提供加载量时所需的 CPU 时间。 如果超出了购买的 SKU 大小所对应的 CPU 时间，容量会根据配置设置自动缩放以满足需求或限制交互式操作。


**Power BI Premium 容量指标** 应用提供有关容量表现的深度信息。 该应用提供高级仪表板和更加详细的报表。

![指标应用仪表板](media/service-admin-premium-monitor-capacity/app-dashboard.png)

在应用的仪表板中，可单击指标单元格来打开深度报表。 报表提供深度指标和筛选功能，可用于深入了解保持容量平稳运行所需的最重要信息。

![查询等待时间计数的周期性峰值指示潜在的 CPU 饱和度问题](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

若要了解有关监视容量的详细信息，请参阅 [Power BI 管理门户中的监视](service-admin-premium-monitor-portal.md)和[使用 Power BI Premium 容量指标应用进行监视](service-admin-premium-monitor-capacity.md)。

#### <a name="updates-for-premium-gen2-preview"></a>Premium Gen2（预览版）的更新
Premium Gen2 容量不使用 Metrics 应用，而是使用 Capacity Utilization 应用，后者将在预览期间提供。 希望查看其使用情况的客户可向客户支持人员请求，重新接收其过去 7 天的使用情况报表的副本。 报表将在请求后的 72 小时内提供。 对于每个容量，将从管理门户中的容量管理页面启动 Capacity Utilization 应用，它可用于分析 30 天及更早的数据。

### <a name="optimizing-capacities"></a>优化容量

充分利用你的容量对于确保用户获得良好性能以及让你的 Premium 投资实现最大价值而言至关重要。 通过监视关键指标，管理员可以确定如何最好地解决瓶颈问题以及采取必要的措施。 若要了解详细信息，请参阅[优化 Premium 容量](service-premium-capacity-optimize.md)和 [Premium 容量方案](service-premium-capacity-scenarios.md)。

### <a name="capacities-rest-apis"></a>容量 REST API

Power BI REST API 包含[容量 API](/rest/api/power-bi/capacities) 的集合。 通过这些 API，管理员能够以编程方式管理 Premium 容量的许多方面，包括启用和禁用工作负载、将工作区分配给容量等等。

## <a name="large-datasets"></a>大型数据集

Power BI Premium 支持上传 Power BI Desktop (.pbix) 模型文件，最大大小为 **10 GB**，具体取决于 SKU。 加载模型后，可将其发布到分配给 Premium 容量的工作区。 随后可将数据集刷新至最大 **12 GB** 的大小。

### <a name="size-considerations"></a>大小注意事项

大型数据集可能为资源密集型。 对于任何大于 1 GB 的数据集，应至少使用 P1 或 A4 SKU。 虽然将大型数据集发布到 A SKU（最高 A3）支持的工作区可能有用，但刷新它们将不起作用。

下表显示了用于将 .pbix 文件上传或发布到 Power BI 服务的建议 SKU：

   |SKU  |.Pbix 大小   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3、P4、P5    | 最多 10 GB  |

Power BI Embedded A4 SKU 等同于 P1 SKU、A5 = P2 和 A6 = P3。

### <a name="large-dataset-storage-format"></a>大型数据集存储格式

如果在数据集上启用[大型数据集存储格式](service-premium-large-models.md)设置，则 .pbix 文件大小限制仍适用于文件上传或发布。 大型数据集存储格式不影响上传大小限制。 但是，如果发布到服务时启用了增量刷新和大型数据集存储格式，则数据集可能快速增长并远远超过这些限制。 对于大型数据集存储格式，数据集大小仅受 Power BI Premium 容量大小的限制。

Power BI 数据集可在高度压缩的内存中缓存内存储数据，以便优化查询性能，在大型数据集上实现快速的用户交互。 以前，Power BI Premium 中的数据集在压缩后被限制为 10 GB。 有了大型模型，该限制被移除，数据集大小仅受到容量大小或管理员设置的最大大小限制。 启用此类大型数据集大小后，Power BI 数据集能够更好地与 Azure Analysis Services 模型大小保持一致。

.pbix 文件表示处于 *高度压缩状态* 的数据。 数据在加载到内存中时可能会扩展，并且在数据刷新期间可能会在内存中扩展数倍。

大型数据集的计划刷新可能需要很长时间，并且会占用大量资源。 请务必不要安排太多的重叠刷新。 建议配置[增量刷新](service-premium-incremental-refresh.md)，因为它更快速、更可靠且使用的资源更少。

如果自上次使用数据集以来已经过去一段时间，则大型数据集的初始报表加载可能需要很长时间。 需要较长时间加载的报表的加载条可显示加载进度。

尽管 Premium 容量中的每个查询内存和时间约束要高得多，但建议使用筛选器和切片器来将视觉对象限制为仅显示必要的内容。

## <a name="incremental-refresh"></a>增量刷新

增量刷新是在 Power BI Premium 和 Power BI Pro 中拥有和维护大型数据集不可或缺的部分。 增量刷新拥有许多优势，例如，刷新速度更快，因为只需刷新已更改的数据。 刷新更可靠，因为不需要维护与不稳定的数据源的长期连接。 资源消耗降低，因为要刷新的数据量减少，这降低了内存和其他资源的整体消耗。 增量刷新策略在 **Power BI Desktop** 中进行定义，并在发布到 Premium 容量中的工作区时应用。 

![刷新详细信息](media/service-premium-incremental-refresh/refresh-details.png)

若要了解详细信息，请参阅 [Power BI Premium 中的增量刷新](service-premium-incremental-refresh.md)。

## <a name="paginated-reports"></a>分页报表

P1-P3 和 A4_A6 SKU 支持的分页报表基于 SQL Server Reporting Services 中的报表定义语言 (RDL) 技术。 虽然基于 RDL 技术，但它与 Power BI 报表服务器不同，后者是可下载的报表平台并可在本地安装，其也包含在 Power BI Premium 中。 分页报表的格式设置为适应可以打印或共享的页面。 即使表格跨多个页，数据也能在表格中显示。 通过使用免费的 [**Power BI 报表生成器**](https://aka.ms/pbireportbuilder) Windows 桌面应用程序，用户可以创建分页报表并将其发布到服务中。

在 Power BI Premium 中，分页报表是必须使用管理门户为容量启用的工作负载。 容量管理员可以启用内存，然后以容量内存资源总量百分比的形式指定内存量。 与其他类型的工作负载不同，Premium 在容量范所含的空间中运行分页报表。 无论工作负载是否处于活动状态，系统都将使用为此空间指定的最大内存。 默认值为 20%。

> [!NOTE]
> 在“Premium Gen2 (预览版)”中，不提供对分页报表的内存管理。 使用 Premium Gen2 时，EM1-EM3 SKU 支持分页报表。

### <a name="paginated-reports-and-premium-gen2"></a>分页报表和 Premium Gen2

使用 Premium Gen2 时，Power BI 中的分页报表将受益于 Premium Gen2 中的体系结构和工程改进。 以下各部分介绍用于分页报表的 Premium Gen2 的好处。

**更广泛的 SKU 可用性** - 在 Premium Gen2 上运行的分页报表可以在所有可用的嵌入和高级 SKU 上运行报表。 计费在 24 小时内按 CPU 小时计算。 这大大扩展了支持分页报表的 SKU。

**动态缩放** - 使用 Premium Gen2，可以在需求上升时灵活应对与活动高峰或资源需求相关的挑战。 

**改进的缓存** - 在 Premium Gen2 之前，许多操作需要分页报表才能在为工作负载容量分配的内存上下文中执行。 现在，使用 Premium Gen2，减少了许多操作所需的内存，从而增强了客户执行长时间运行的操作且不影响其他用户会话的能力。 

**增强的安全性和代码隔离** - 使用 Premium Gen2，代码隔离可以在每个用户级别而不是每个容量级别上进行，与原始 Premium 产品/服务的情况一样。 

若要了解详细信息，请参阅 [Power BI Premium 中的分页报表](../paginated-reports/paginated-reports-report-builder-power-bi.md)。 若要了解有关启用分页报表工作负载的详细信息，请参阅[配置工作负载](service-admin-premium-workloads.md)。

## <a name="power-bi-report-server"></a>Power BI 报表服务器
 
Power BI Premium 随附 Power BI 报表服务器，后者是带有 Web 门户的本地报表服务器。 可以在本地生成 BI 环境，并在组织的防火墙后面分发报表。 报表服务器使用户可以访问 SQL Server Reporting Services 丰富的交互式功能以及企业报告功能。 用户可以浏览可视化数据并快速发现模式，以便更快地作出更好的决策。 报表服务器按照你自己的方式提供治理。 如果时机成熟，Power BI 报表服务器会使其能够轻松迁移到云中，此时，组织可以充分利用所有 Power BI Premium 功能。

若要了解详细信息，请参阅 [Power BI 报表服务器](../report-server/get-started.md)。

## <a name="unlimited-content-sharing"></a>无限内容共享

借助 Premium，每个人（无论是在组织内外）都可以查看 Power BI 内容（包括分页和交互式报表），而无需购买单独的许可证。 

![内容共享](media/service-premium-what-is/premium-sharing.png)

Premium 允许 Pro 用户广泛分发内容，且不要求查看内容的收件人提供 Pro 许可证。 内容创建者需要提供 Pro 许可证。 创建者连接到数据源、模型数据，并创建打包为工作区应用的报表和仪表板。 如果用户拥有“查看者”角色，即使没有 Pro 许可证仍可访问 Power BI Premium 容量的工作区。 

若要了解详细信息，请参阅 [Power BI 许可](service-admin-licensing-organization.md)。

## <a name="analysis-services-in-power-bi-premium"></a>Power BI Premium 中的 Analysis Services

在后台，久经企业考验的 Microsoft Analysis Services Vertipaq 引擎为 Power BI Premium 工作区和数据集提供技术支持。 Analysis Services 通过支持开放标准 XMLA 协议的客户端库和 API 提供可编程性以及客户端应用程序和工具支持。 默认情况下，Power BI Premium 容量数据集工作负荷支持 Microsoft 和第三方客户端应用程序和工具通过 XMLA 终结点执行只读操作。 容量管理员还可以选择禁用或允许通过终结点执行读/写操作。

借助只读权限，SQL Server Management Studio (SSMS) 和 SQL Server Profiler 等 Microsoft 工具以及 DAX Studio 和数据可视化应用程序等第三方应用程序可以使用 XMLA、DAX、MDX、DMV 和跟踪事件连接到并查询 Premium 数据集。 借助读/写权限，企业数据建模工具（如包含 Analysis Services 项目扩展的 Visual Studio 或开放源代码表格编辑器）可以将表格模型作为数据集部署到 Premium 工作区。 借助 SSMS 等工具，管理员可以使用表格模型脚本语言 (TMSL)，为元数据更改和高级数据刷新方案编写脚本。 

若要了解详情，请参阅[使用 XMLA 终结点的数据集连接](service-premium-connect-tools.md)。

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)


## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [管理高级容量](service-premium-capacity-manage.md)
> [Azure Power BI 嵌入式文档](https://azure.microsoft.com/services/power-bi-embedded/)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

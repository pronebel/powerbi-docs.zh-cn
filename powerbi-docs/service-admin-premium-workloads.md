---
title: 如何在 Power BI Premium 中配置工作负载
description: 了解如何在 Power BI 高级容量中配置工作负载。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564877"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>在高级容量中配置工作负载

本文介绍如何为 Power BI 高级容量启用和配置工作负载。 默认情况下，容量仅支持与正在运行的 Power BI 查询关联的工作负载。 还可以为 [AI（认知服务）](service-cognitive-services.md)  、[数据流](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)  和[分页报表](paginated-reports-save-to-power-bi-service.md)  启用和配置其他工作负载。

## <a name="default-memory-settings"></a>默认内存设置

查询工作负载针对由高级容量 SKU 确定的资源进行优化并受到这些资源的限制。 高级容量还支持可以使用容量资源的其他工作负载。 这些工作负载的默认内存值基于 SKU 可用的容量节点。 最大内存设置不是累计计算的。 为 AI 和数据流动态分配并为分页报表静态分配相当于最大指定值的内存。 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>用于软件即服务 (SaaS) 方案的 Microsoft Office SKU

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N/A | N/A | 20%的默认值;最小的 20% | 默认为 20%，最低为 10% | 默认为 20%，最低为 5% |
| 数据流 | N/A |默认为 20%，最低为 12%  | 默认为 20%，最低为 5%  | 默认为 20%，最低为 3% | 默认为 20%，最低为 2%  |
| 分页报表 | N/A |N/A | 默认为 20%，最低为 10% | 默认为 20%，最低为 5% | 默认为 20%，最低为 2.5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>用于平台即服务 (PaaS) 方案的 Microsoft Azure SKU

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N/A                      | 20%的默认值;最小的 100%                     | 20%的默认值;最小 50%                     | 20%的默认值;最小的 20% | 默认为 20%，最低为 10% | 默认为 20%，最低为 5% |
| 数据流         | 默认为 40%，最低为 40% | 默认为 24%，最低为 24% | 默认为 20%，最低为 12% | 默认为 20%，最低为 5%  | 默认为 20%，最低为 3% | 默认为 20%，最低为 2%   |
| 分页报表 | N/A                      | 不适用                      | N/A                     | 默认为 20%，最低为 10% | 默认为 20%，最低为 5% | 默认为 20%，最低为 2.5% |
| | | | | | |

## <a name="workload-settings"></a>工作负荷设置

### <a name="ai-preview"></a>AI （预览版）

除了**最大内存**设置，AI 工作负荷有其他设置，**允许从 Power BI Desktop 的使用情况**。 默认值是**关闭**。 此设置是保留供将来使用，并且可能不会显示在所有租户中。

### <a name="datasets-preview"></a>数据集 （预览）

默认情况下，数据集工作负荷已启用，并且不能禁用。 此工作负荷包含一项附加设置， **XMLA 终结点**。 默认值是**1**，启用的含义。 此设置指定客户端应用程序的连接遵循设置工作区和应用程序级别的安全组成员身份。 若要了解详细信息，请参阅[连接到数据集与客户端应用程序和工具](service-premium-connect-tools.md)。

### <a name="dataflows"></a>数据流

除了**最大内存**设置，数据流工作负荷有其他设置，**容器大小**。 此设置，可优化用于处理更复杂的计算密集型的数据流的数据流的工作负荷性能。

刷新数据流，数据流工作负荷产生的数据流中的每个实体的容器。 每个容器可能需要最多的卷中的内存中的容器大小设置指定。 默认值为所有 Sku **700 MB**。 您可能想要更改此设置，如果：

- 数据流花费很长时间来刷新，或在超时时数据流刷新失败。
- 数据流的实体包括计算步骤，例如，联接。  

它的建议使用[Power BI Premium 容量指标](service-admin-premium-monitor-capacity.md)应用程序以分析数据流工作负荷性能。 

在某些情况下，增加容器大小可能无法提高性能。 例如，如果不执行大量计算的情况下，数据流仅从源获取数据，不会帮助可能更改容器大小。 如果它将使数据流工作负荷，刷新操作的实体分配更多内存，可能有助于增加容器大小。 通过让更多的内存分配，它可以减少刷新计算很大程度的实体所需的时间。 

容器大小值不能超过数据流工作负荷的最大内存。 例如，P1 容量有 25 GB 的内存。 如果数据流工作负荷的最大内存 （%）设置为 20%，容器大小 (MB) 不能超过 5000。 在所有情况下，容器大小不能超过最大内存，即使设置较高的值。 

### <a name="paginated-reports-preview"></a>分页的报表 （预览）

分页的报表允许自定义代码来呈现报表时运行。 例如，动态地更改基于内容的文本颜色，这可能需要更多的内存。 Power BI Premium 在容量所含的空间中运行分页报表。 使用指定的最大内存*是否*工作负荷处于活动状态。 如果从默认情况下，更改的最大内存设置，请确保您设置低足够它不会产生负面影响的其他工作负荷。

在某些情况下，分页报表工作负荷可能会不可用。 在这种情况下，工作负荷在管理员门户中显示错误状态，且用户看到报表呈现为超时。 若要缓解此问题，禁用工作负荷，然后再次启用它。

## <a name="configure-workloads"></a>配置工作负载

通过仅在需要时启用工作负载，最大限度地利用容量的可用资源。 仅在已确定默认设置不满足容量资源要求时更改内存设置。  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>在 Power BI 管理门户中配置工作负载

1. 在“容量设置” > “高级容量”中，选择一个容量   。

1. 在“更多选项”  下，展开“工作负载”  。

1. 启用一个或多个工作负载，并设置“最大内存”  的值。   

    
    ![启用工作负载](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. 单击“**应用**”。

### <a name="rest-api"></a>REST API

可以使用[容量](https://docs.microsoft.com/rest/api/power-bi/capacities) REST API 启用工作负载并将其分配给容量。

## <a name="monitoring-workloads"></a>监视工作负载

[Power BI Premium 容量指标应用](service-admin-premium-monitor-capacity.md)提供数据集、数据流和分页报表指标，以监视为容量启用的工作负载。 

## <a name="next-steps"></a>后续步骤

[优化 Power BI Premium 容量](service-premium-capacity-optimize.md)     
[Power BI 中通过数据流自助进行数据准备](service-dataflows-overview.md)   
[Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)   

更多问题？ [在 Power BI 社区提问](http://community.powerbi.com/)
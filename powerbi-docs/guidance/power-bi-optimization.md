---
title: Power BI 优化指南
description: Power BI 优化指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 3a541c46f78c5e5cd25b47a94394a011fd61954f
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916535"
---
# <a name="optimization-guide-for-power-bi"></a>Power BI 优化指南

本文提供的指南使开发人员和管理员能够生产和维护优化的 Power BI 解决方案。 可以在不同的体系结构层优化解决方案。 这些层包括：

- 数据源
- 数据模型
- 可视化效果（包括仪表板、Power BI 报表和 Power BI 分页报表）
- 环境（包括容量、数据网关和网络）

## <a name="optimizing-the-data-model"></a>优化数据模型

数据模型支持整个可视化体验。 数据模型可以是外部托管的，也可以是内部托管的，在 Power BI 中，它们称为“数据集”  。 请务必了解你的选择，并为解决方案选择适当的数据集类型。 共有三种数据集模式：导入、DirectQuery 和复合。 有关详细信息，请参阅 [Power BI 服务中的数据集](../connect-data/service-datasets-understand.md)和 [Power BI 服务中的数据集模式](../connect-data/service-dataset-modes-understand.md)。

有关特定数据集模式的指南，请参阅：

- [导入建模的数据缩减方法](import-modeling-data-reduction.md)
- [Power BI Desktop 中的 DirectQuery 模型指导](directquery-model-guidance.md)
- [Power BI Desktop 中的复合模型指南](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>优化可视化效果

Power BI 可视化效果可以是仪表板、Power BI 报表或 Power BI 分页报表。 每种可视化效果都有不同的体系结构，因此具体指南也有所不同。 

### <a name="dashboards"></a>仪表板

请务必了解，Power BI 维护仪表板磁贴的缓存，但不包括实时报表磁贴和流式处理磁贴。 有关详细信息，请参阅 [Power BI 中的数据刷新（磁贴刷新）](../connect-data/refresh-data.md#tile-refresh)。 如果你的数据集强制实施动态[行级别安全性 (RLS)](../admin/service-admin-rls.md)，请务必了解性能影响，因为磁贴将以每用户为基础进行缓存。

将实时报表磁贴固定到仪表板后，查询缓存中不会提供这些磁贴。 而是执行类似于报表的操作，动态查询后端核心。

顾名思义，与依赖数据源相比，从缓存中检索数据可提供更好、更稳定的性能。 利用此功能的一种方法是将仪表板作为用户的首个登录页。 将经常使用且请求次数较高的视觉对象固定到仪表板。 通过这种方式，仪表板成为有价值的“第一道防线”，可通过容量上的较低负载提供稳定的性能。 用户仍然可以单击查看报表以分析详情。

对于 DirectQuery 和实时连接数据集，缓存是通过查询数据源进行定期更新的。 默认情况下，它每小时查询一次，但你可以在数据集设置中配置不同的频率。 每个缓存更新都会将查询发送到基础数据源来更新缓存。 生成的查询数量取决于在依赖于数据源的仪表板上固定的视觉对象数量。 请注意，如果启用了“行级别安全性”，则会为每个不同的安全性上下文生成查询。 例如，假设有两个不同的角色用于对用户进行分类，并且它们具有两个不同的数据视图。 在查询缓存刷新期间，Power BI 会生成两组查询。

### <a name="power-bi-reports"></a>Power BI 报表

对于优化 Power BI 报表设计，有一些建议。

> [!NOTE]
> 当报表基于 DirectQuery 数据集时，对于其他报表设计优化，请参阅 [Power BI Desktop 中的 DirectQuery 模型指南（优化报表设计）](directquery-model-guidance.md#optimize-report-designs)。

#### <a name="apply-the-most-restrictive-filters"></a>应用限制性最强的级别

视觉对象需要显示的数据越多，加载视觉对象的速度越慢。 虽然此道理显而易见，但很容易忘记。 例如：假设你有一个大型数据集。 基于该数据集，可以生成具有一个表的报告。 最终用户在此页上使用切片器来获取他们所需的行，通常他们只对某几十行感兴趣。

一个常见的错误是采用表未经筛选的默认视图，即显示全部的一亿多行。 这些行的数据会加载到内存中并在每次刷新时解压缩。 这种处理对存储器产生了巨大的需求。 解决方案：使用“Top N”筛选器减少表显示的最大项数。 可以将最大项数设置为大于用户所需数量，例如 10,000。 结果是最终用户体验不会发生变化，但内存使用会大幅下降。 最重要的是，提高了性能。

对于报表中的所有视觉对象，建议采用以上类似的设计方法。 问问自己，是否需要此视觉对象中的所有数据？ 是否有方法可将视觉对象中显示的数据量滤除，而又不会对最终用户体验造成过多影响？ 请注意，尤其是表可能成本高昂。

#### <a name="limit-visuals-on-report-pages"></a>限制报表页上的视觉对象

上述原则同样适用于报表页上添加的视觉对象数量。 强烈建议将特定报表页上的视觉对象数量限制为仅包括必需的视觉对象。 [钻取页面](report-drillthrough.md)和[报表页工具提示](report-page-tooltips.md)是不错的方法，它们可提供更多详细信息，而又不会在页面上显示过多视觉对象。

#### <a name="evaluate-custom-visual-performance"></a>评估自定义视觉对象性能

确保将每个自定义的视觉对象通过其节奏来确保高性能。 Power BI 视觉对象优化欠佳可能会对整个报表的性能产生负面影响。

### <a name="power-bi-paginated-reports"></a>Power BI 分页报表

通过将最佳做法设计应用到报表的数据检索，可以优化 Power BI 分页报表的设计。 有关详细信息，请参阅[分页报表的数据检索指南](report-paginated-data-retrieval.md)。

此外，请确保容量有足够的内存分配给[分页报表工作负载](../admin/service-admin-premium-workloads.md#paginated-reports)。

## <a name="optimizing-the-environment"></a>优化环境

通过配置容量设置、调整数据网关大小并减少网络延迟，可以优化 Power BI 环境。

### <a name="capacity-settings"></a>容量设置

使用容量（可用于 Power BI Premium (P SKU) 或 Power BI Embedded (A SKU、A4-A6)）时，可以管理容量设置。 有关详细信息，请参阅[管理高级容量](../admin/service-premium-capacity-manage.md)。 有关如何优化容量的指南，请参阅[优化 Premium 容量](../admin/service-premium-capacity-optimize.md)。

### <a name="gateway-sizing"></a>调整网关大小

当 Power BI 必须访问无法直接通过 Internet 访问的数据时，就需要网关。 可以将[本地数据网关](../connect-data/service-gateway-onprem.md)安装在本地服务器上，也可以安装在 VM 托管的基础结构即服务 (IaaS) 上。

若要了解网关工作负载和调整大小的建议，请参阅[本地数据网关大小调整](gateway-onprem-sizing.md)。

### <a name="network-latency"></a>网络延迟

网络延迟可增加请求到达 Power BI 服务以及传输响应所需的时间，从而影响报表的性能。 Power BI 中的租户被分配到一个特定区域。

> [!TIP]
> 要确定租户的位置，请参阅[我的 Power BI 租户位于何处？](../admin/service-admin-where-is-my-tenant-located.md)

当来自租户的用户访问 Power BI 服务时，他们的请求将始终被路由到此区域。 请求到达 Power BI 服务后，服务就可以发送其他请求（例如，到基础数据源或数据网关的请求），这也会受到网络延迟的影响。

诸如 [Azure 速度测试](https://azurespeedtest.azurewebsites.net/)之类的工具可提供客户端与 Azure 区域之间的网络延迟的指示。 一般来说，为了尽量降低网络延迟的影响，请争取使数据源、网关和 Power BI 群集尽可能地靠近。 它们最好位于同一区域中。 如果网络延迟成为一个问题，请尝试将网关和数据源放在云托管的虚拟机内，以查找与 Power BI 群集更近的网关和数据源。

## <a name="monitoring-performance"></a>监视性能

可以监视性能以确定瓶颈。 应重点针对速度缓慢的查询或报表视觉对象进行持续优化。 监视可以在设计时在 Power BI Desktop 中完成，也可以在 Power BI Premium 容量中的生产工作负载上完成。 有关详细信息，请参阅[在 Power BI 中监视报表性能](monitor-report-performance.md)。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI 指南](index.yml)
- [监视报表性能](monitor-report-performance.md)
- 白皮书：[规划 Power BI Enterprise 部署](https://go.microsoft.com/fwlink/?linkid=2057861)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)





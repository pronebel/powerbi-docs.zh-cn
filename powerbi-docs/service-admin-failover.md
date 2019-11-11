---
title: Power BI 高可用性、故障转移和灾难恢复常见问题解答
description: 了解 Power BI 服务如何向其用户提供高可用性，以及提供业务连续性和灾难恢复。
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: dd2c94b490cdf31bd383c7100b9a1bc372f8e75f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873687"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Power BI 高可用性、故障转移和灾难恢复常见问题解答

本文说明 Power BI 服务如何向其用户提供高可用性，以及提供业务连续性和灾难恢复。 阅读本文之后，应更好地了解如何实现高可用性、在什么情况下 Power BI 会执行故障转移以及在进行故障转移时服务预计会发生什么情况。

## <a name="what-does-high-availability-mean-for-power-bi"></a>“高可用性”对于 Power BI 意味着什么？

Power BI 是完全托管的软件即服务 (SaaS)。  Microsoft 对它进行设计和运营，使它可在发生基础结构故障时复原，从而使用户可以始终访问其报表。  该服务通过 [99.9% SLA](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) 进行支持。

## <a name="what-is-a-power-bi-failover"></a>什么是 Power BI 故障转移？

Power BI 维护 Azure 数据中心（也称为区域）中每个组件的多个实例，以保证业务连续性。 如果发生中断或导致 Power BI 在区域中无法访问或不可操作的问题，则 Power BI 会使该区域中的所有组件都故障转移到备份实例。 故障转移会将可用性和可操作性还原到新区域中的 Power BI 服务实例（通常在同一地理位置，记录在 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)中）。

进行了故障转移的 Power BI 服务实例仅支持读取操作  ，这意味着以下操作在故障转移期间不受支持：刷新、报表发布操作、仪表板或报表修改以及其他需要对 Power BI 元数据进行更改的操作（例如在报表中插入注释）。  显示仪表板和显示报表（不基于 Live Connect 到本地数据源上的 DirectQuery）等读取操作仍然可以正常运行。

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>备份实例如何与我的数据保持同步？

所有 Power BI 服务组件都定期同步其备份实例。 对于在 Power BI 中上传或更改的任何内容，我们都以 15 分钟时间点同步为目标。 发生故障转移时，Power BI 使用 [Azure 存储地域冗余复制](/azure/storage/common/storage-redundancy-grs)和 [Azure SQL 异地冗余复制](/azure/sql-database/sql-database-active-geo-replication)来保证备份实例存在于其他区域中并且可以在发生故障转移时进行使用。

## <a name="where-are-the-failover-clusters-located"></a>故障转移群集位于何处？

备份实例驻留在当组织注册 Power BI 时选择的相同地理位置（地区）处，除了在 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)中记录的情况。 一个地区可以包含多个区域，Microsoft 可能会将数据复制到给定地区中的任何区域以实现数据复原能力。 Microsoft 不会在地区外部复制或移动客户数据。 有关 Power BI 提供的地区与其中的区域的映射，请参阅 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)。

## <a name="how-does-microsoft-decide-to-failover"></a>Microsoft 如何决定故障转移？

有两个不同的系统会在可能需要进行故障转移时进行指示：

- 我们的外部和内部监视探测指示缺乏可用性或无法正常运行。 这类指示可以基于在 Power BI 组件中或是 Power BI 在区域中依赖的一个或多个服务中检测到的中断。
- Microsoft Azure 的中心运营团队会向我们告知区域中的严重中断。

在这两种情况下，Power BI 管理团队成员会制定故障转移决策；决策本身不会自动进行。 制定了决策之后，故障转移过程会自动进行。

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>如何知道 Power BI 现在处于故障转移模式？

会在 Power BI 支持页 ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)) 上发布通知。 该通知包含在故障转移过程中不可用的主要操作，包括发布、刷新、创建仪表板、复制仪表板以及权限更改。

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Power BI 进行故障转移需要多长时间？

制定了故障转移的决策之后，可能需要多达 60 分钟的时间使故障转移实例成为可用状态。

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>我的 Power BI 实例何时返回原始区域？

当解决了导致故障转移的问题时，Power BI 服务实例会返回到其原始区域。 检查 Power BI 支持页：解决了问题时，Power BI 团队会删除描述故障转移的通知。 此时，运行应恢复为正常状态。

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>是否由我负责我的 Power BI 解决方案的可用性？

如果组织中使用的 Power BI 解决方案涉及以下元素之一，则必须采取一些措施来保证解决方案仍然高度可用：

- 如果组织使用 Power BI Premium，则必须确保调整高级容量大小以满足部署的负载要求。  [Power BI Premium 规划和部署白皮书](https://aka.ms/Premium-Capacity-Planning-Deployment)和 [Power BI Premium 容量指标应用](service-admin-premium-monitor-capacity.md)可帮助规划和满足此要求。 我们定期向度量值应用和 Power BI 中的管理门户添加新功能以进行帮助。
- 如果组织使用本地数据网关访问本地数据源，则必须[按照本文所述](/data-integration/gateway/service-gateway-high-availability-clusters)来设置网关，以支持高可用性。 无论是在导入模式下刷新报表，还是在使用 DirectQuery 或 Live Connect 访问数据或数据模型，都请按照此指导进行操作。

## <a name="will-gateways-function-when-in-failover-mode"></a>在处于故障转移模式期间，网关是否会工作正常？

否。 需要本地数据源（基于直接查询和 Live Connect 的任何报表和仪表板）提供的数据不会在故障转移过程中起作用。 网关配置不会更改，不过：当 Power BI 实例恢复为其原始状态时，网关会恢复为其正常功能。

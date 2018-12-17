---
title: 什么是 Microsoft Power BI Premium？
description: Power BI Premium 是适用于组织或团队的专用容量，提供了更可靠的性能和更大的数据卷，使你无需购买每用户许可证。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/21/2018
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: cbfee8034639a65517f9adc57cc95dd1271e6044
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "53025433"
---
# <a name="what-is-microsoft-power-bi-premium"></a>什么是 Microsoft Power BI Premium？

Microsoft Power BI Premium 提供专用于为组织运行 Power BI 服务的资源。 可提供更可靠的性能和更大的数据卷。 使用 Premium，还可以广泛分发内容，无需为内容使用者购买每用户 Pro 许可证。 有关购买信息，请参阅[如何购买 Power BI Premium](service-admin-premium-purchase.md)。

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="premium-capacity-and-shared-capacity"></a>高级容量和共享容量

充分利用 Power BI Premium 的方式为，将工作区分配到“高级容量”。 高级容量是组织的专用资源。 未分配到高级容量的工作区属于“共享容量”。 通过共享容量，工作负载可在其他客户共享的计算资源上运行。

下图以 Contoso 组织为例，展示了高级容量和共享容量之间的关系。

![Power BI Premium 插图](media/service-premium/premium-chart.png)

| 分区图 | 说明 |
| --- | --- |
| **(1)** 高级容量中的项 | <ul><li>访问应用工作区（以成员或管理员身份）和发布应用都需要使用 Power BI Pro 许可证。<li>共享应用需要 Power BI Pro 许可证，但使用应用不需要。<li>所有仪表板收件人（无论其分配的许可证为何）都可设置数据警报。<li>用于嵌入的 REST API 使用具有 Power BI Pro 许可证的服务帐户，而不是用户帐户。</ul> |
| **(2)** 共享容量中的我的工作区 | <ul><li>共享和使用应用都需要 Power BI Pro 许可证。</ul> |
| **(3)** 共享容量中的应用工作区 | <ul><li>使用任何应用都需要 Power BI Pro 许可证。</ul>|
| | |

在共享容量中，为了确保所有用户的体验质量，Power BI 会对单个用户施加更多的限制。 默认情况下，你的工作区在共享容量中，包括个人“我的工作区”和应用工作区。

下表总结了共享容量与高级容量的区别。

|  | 共享容量 | Power BI 高级容量 |
| --- | --- | --- |
| 刷新频率 |每天 8 次 |每天 48 次 |
| 专用硬件隔离 |![不可用](media/service-premium/not-available.png) |![可用](media/service-premium/available.png) |
| 面向所有用户的企业分发__ | | |
| 应用和共享 |![不可用](media/service-premium/not-available.png) |![可用](media/service-premium/available.png) |
| 嵌入式 API 和控件 |![不可用](media/service-premium/not-available.png) |![可用](media/service-premium/available.png)<sup>2</sup> |
| 在本地发布 Power BI 报表 |![不可用](media/service-premium/not-available.png) |![可用](media/service-premium/available.png) |
| | | |

*<sup>1</sup> 有关详细信息，请参阅[按许可证类型列出的功能](service-features-license-type.md)*。  
<sup>2</sup> Power BI Premium 即将推出的增强功能。

若要深入了解如何将工作区分配到高级容量，请查阅[管理 Power BI Premium](service-admin-premium-manage.md)。

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>高级容量节点

不同虚拟核心容量的节点配置中可使用 Power BI Premium。 若要详细了解特定 SKU 产品/服务和成本，请参阅 [Power BI 定价](https://powerbi.microsoft.com/pricing/)。 也可使用[成本计算器](https://powerbi.microsoft.com/calculator/)。 有关嵌入分析容量规划的信息，请参阅[“规划 Power BI Enterprise 部署”白皮书](https://aka.ms/pbienterprisedeploy)。 简而言之：

* P 节点可用于嵌入式部署或服务部署。

* EM 节点只能用于嵌入式部署。 EM 节点无权使用高级功能，如与没有 Power BI Pro 许可证的用户共享应用。

>[!NOTE]
>只有拥有 Office 365 全局管理员角色的用户，才能正常访问此表中的链接。 其他人会收到 404 错误。

| 容量节点 | 总虚拟核心<br/>（后端 + 前端） | 后端虚拟核心 | 前端虚拟核心 | DirectQuery/实时连接限制 | 高峰时间的最大显示页数 | 是否支持 |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1（按月）](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 个虚拟核心 |0.5 个 V 核心，2.5 GB RAM |0.5 个 V 核心 |每秒 3.75 |150-300 |可用 |
| [EM2（按月）](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 个虚拟核心 |1 个 V 核心，5 GB RAM |1 个虚拟核心 |每秒 7.5 |301-600 |可用 |
| [EM3（按月）](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 个虚拟核心 |2 个 V 核心，10 GB RAM |2 个虚拟核心 | |601-1,200 |可用 |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 个虚拟核心 |4 个 V 核心，25 GB RAM |4 个虚拟核心 |每秒 30 个 |1,201-2,400 |可用（也可以[按月](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)） |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 个虚拟核心 |8 个 V 核心，50 GB RAM |8 个虚拟核心 |每秒 60 个 |2,401-4,800 |可用 |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 个虚拟核心 |16 个 V 核心，100 GB RAM |16 个虚拟核心 |每秒 120 个 |4,801-9600 |可用 |
| | | | | | | |

* 前端虚拟核心负责 Web 服务、仪表板和报表文档管理、访问 Rights Management、时间安排、API、上传和下载，并大体包括所有与用户体验相关的内容。

* 后端虚拟核心负责完成繁重的任务：查询处理、缓存管理、运行 R 服务器、数据刷新、自然语言处理、实时馈送和在服务器端绘制报表和图像。 后端虚拟核心也可保留一定的内存量。 处理大型数据模型或大量活动数据集时，内存充足尤为重要。

## <a name="workloads-in-premium-capacity"></a>高级容量中的工作负载

将 Power BI 中的工作负载视为可以向用户公开的众多服务之一。 默认情况下，Power BI Premium 和 Power BI Embedded 的容量仅支持与在云中运行 Power BI 查询相关联的工作负载。

我们现在为两个额外的工作负载提供预览支持：分页报表和数据流。 用户可以在 Power BI 管理门户中或通过 Power BI REST API 启用这些工作负载。 还可以设置每个工作负载可以使用的最大内存，从而控制不同工作负载相互影响的方式。 有关详细信息，请参阅[配置工作负载](service-admin-premium-manage.md#configure-workloads)。

### <a name="default-memory-settings"></a>默认内存设置

下表根据可用的不同[容量节点](#premium-capacity-nodes)显示默认和最小内存值。 内存动态分配给数据流，但静态分配给分页报表。 有关详细信息，请参阅下一部分：[分页报表的注意事项](#considerations-for-paginated-reports)。

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>用于软件即服务 (SaaS) 方案的 Microsoft Office SKU

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| 分页报表 | N/A | 默认为 20%，最低为 10% | 默认为 20%，最低为 5% | 默认为 20%，最低为 2.5% |
| 数据流 | 默认为 20%，最低为 8%  | 默认为 20%，最低为 4%  | 默认为 20%，最低为 2% | 默认为 20%，最低为 1%  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>用于平台即服务 (PaaS) 方案的 Microsoft Azure SKU

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| 分页报表 | N/A                      | 不适用                      | N/A                     | 默认为 20%，最低为 10% | 默认为 20%，最低为 5% | 默认为 20%，最低为 2.5% |
| 数据流         | 默认为 27%，最低为 27% | 默认为 20%，最低为 16% | 默认为 20%，最低为 8% | 默认为 20%，最低为 4%  | 默认为 20%，最低为 2% | 默认为 20%，最低为 1%   |

### <a name="considerations-for-paginated-reports"></a>分页报表的注意事项

如果使用分页报表工作负载，请注意以下几点。

* **分页报表中的内存分配**：使用分页报表，可以在呈现报表时运行自己的代码（例如根据内容动态更改文本颜色）。 鉴于这一事实，我们通过在容量内的容纳空间中运行分页报表来确保 Power BI 高级容量的安全。 我们将用户指定的最大内存分配给此空间，无论工作负载是否处于活动状态都是如此。 如果使用相同容量的 Power BI 报表或数据流，请务必为分页报表设置足够低的内存，使其不会对其他工作负载产生负面影响。

* **分页报表不可用**：在极少数情况下，分页报表工作负载可能变得不可用。 在这种情况下，工作负载在管理门户中显示错误状态，并且用户会看到报表呈现的超时。 要缓解此问题，请禁用工作负载，然后再次启用它。

## <a name="power-bi-report-server"></a>Power BI 报表服务器

Power BI Premium 还包括在组织内部运行本地 Power BI 报表服务器的功能。 若要了解详细信息，请参阅 [Power BI 报表服务器入门](report-server/get-started.md)。

## <a name="next-steps"></a>后续步骤

[Power BI Premium FAQ](service-premium-faq.md)
[如何购买 Power BI Premium](service-admin-premium-purchase.md)
[管理 Power BI Premium](service-admin-premium-manage.md)
[Microsoft Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)
[白皮书：计划 Power BI Enterprise 部署](https://aka.ms/pbienterprisedeploy)
[在组织中管理 Power BI](service-admin-administering-power-bi-in-your-organization.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

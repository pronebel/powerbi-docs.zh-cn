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
LocalizationGroup: Premium
ms.openlocfilehash: 2ca75f191f27bd158b9fab67c7be6902154f8ac1
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641220"
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
| 专用硬件隔离 |![](media/service-premium/not-available.png "不可用") |![](media/service-premium/available.png "可用") |
| 面向所有用户的企业分发 | | |
| 应用和共享 |![](media/service-premium/not-available.png "不可用") |![](media/service-premium/available.png "可用")<sup>1</sup> |
| 嵌入式 API 和控件 |![](media/service-premium/not-available.png "不可用") |![](media/service-premium/available.png "可用")<sup>2</sup> |
| 在本地发布 Power BI 报表 |![](media/service-premium/not-available.png "不可用") |![](media/service-premium/available.png "可用") |
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

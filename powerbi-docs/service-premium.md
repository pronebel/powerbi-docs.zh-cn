---
title: 什么是 Microsoft Power BI Premium？
description: Power BI Premium 是适用于组织或团队的专用容量，提供了更可靠的性能和更大的数据卷，使你无需购买每用户许可证。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: f327cb95c10756f079778d20e62cba4871b95c02
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964930"
---
# <a name="what-is-microsoft-power-bi-premium"></a>什么是 Microsoft Power BI Premium？

> [!NOTE]
> 本文目前正在更新，以说明新功能，提供更多详细信息并提高可读性。 有关最新信息，请参阅[部署和管理 Power BI Premium 容量](whitepaper-powerbi-premium-deployment.md)。

Power BI Premium 提供专用于为组织运行 Power BI 服务的资源。 可提供更可靠的性能和更大的数据卷。 使用 Premium，还可以广泛分发内容，无需为内容使用者购买每用户 Pro 许可证。  

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

下表总结了共享容量与高级容量的区别：

|  | 共享容量 | Power BI 高级容量 |
| --- | --- | --- |
| 刷新频率 |每天 8 次 |每天 48 次 |
| 与专用硬件隔离 |![不可用](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| 面向所有用户的企业版 | | |
| 应用和共享 |![不可用](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| 嵌入式 API 和控件 |![不可用](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| 在本地发布 Power BI 报表 |![不可用](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> Power BI Premium 今后即将推出的增强功能。



### <a name="premium-capacity-nodes"></a>高级容量节点

不同虚拟核心容量的节点配置中可使用 Power BI Premium。 若要详细了解特定 SKU 产品/服务和成本，请参阅 [Power BI 定价](https://powerbi.microsoft.com/pricing/)。 也可使用[成本计算器](https://powerbi.microsoft.com/calculator/)。 有关嵌入分析容量规划的信息，请参阅[“规划 Power BI Enterprise 部署”白皮书](https://aka.ms/pbienterprisedeploy)。 简而言之：

* P 节点可用于嵌入式部署或服务部署。

* EM 节点只能用于嵌入式部署。 EM 节点无权使用高级功能，如与没有 Power BI Pro 许可证的用户共享应用。

| 容量节点 | 总虚拟核心<br/>（后端 + 前端）  | 后端 V 核心 <sup>[1](#fn1)</sup> | 前端 V 核心 <sup>[2](#fn2)</sup> | DirectQuery/实时连接限制 | 最大并发刷新次数 |
| --- | --- | --- | --- | --- | --- |
| EM1（按月） |1 个虚拟核心 |0.5 个 V 核心，2.5 GB RAM |0.5 个 V 核心 |每秒 3.75 |  1 |
| EM2（按月） |2 个虚拟核心 |1 个 V 核心，5 GB RAM |1 个虚拟核心 |每秒 7.5 |  2 |
| EM3（按月） |4 个虚拟核心 |2 个 V 核心，10 GB RAM |2 个虚拟核心 | 15 | 3 |
| P1 |8 个虚拟核心 |4 个 V 核心，25 GB RAM |4 个虚拟核心 |每秒 30 个 | 6 |
| P2 |16 个虚拟核心 |8 个 V 核心，50 GB RAM |8 个虚拟核心 |每秒 60 个 | 12 |
| P3 |32 个虚拟核心 |16 个 V 核心，100 GB RAM |16 个虚拟核心 |每秒 120 个 | 24 |
| | | | | | |

<a name="fn1">1</a>：前端 V 核心负责完成 Web 服务。 例如，仪表板和报表文档管理、访问权限管理、计划安排、API、上传和下载，一般包括所有与用户体验相关的服务。 

<a name="fn2">2</a>：后端 V 核心负责完成繁重的任务，如查询处理、缓存管理、运行 R 服务器、数据刷新、自然语言处理、实时馈送以及报表和图像的服务器端呈现。 后端虚拟核心也可保留一定的内存量。 处理大型数据模型或大量活动数据集时，内存充足尤为重要。

## <a name="workloads-in-premium-capacity"></a>高级容量中的工作负载

默认情况下，Power BI Premium 和 Power BI Embedded 的容量仅支持与在云中运行 Power BI 查询相关联的工作负载。 高级版还支持“AI”、“数据流”和“分页报表”的其他工作负载。 在这些工作负载可以使用容量的资源之前，必须在 Power BI 管理门户中或通过 Power BI REST API 启用它们。 所有工作负载都具有各工作负载可以使用的最大内存量的默认设置。 但是，可以配置不同的内存使用设置，以确定工作负载如何相互影响并使用容量资源。 若要了解更多信息，请参阅[配置工作负载](service-admin-premium-workloads.md)。

## <a name="power-bi-report-server"></a>Power BI 报表服务器

Power BI Premium 还包括在组织内部运行本地 Power BI 报表服务器的功能。 若要了解详细信息，请参阅 [Power BI 报表服务器入门](report-server/get-started.md)。

## <a name="next-steps"></a>后续步骤

[部署和管理 Power BI Premium 容量](whitepaper-powerbi-premium-deployment.md)   
[如何购买 Power BI Premium](service-admin-premium-purchase.md)   
[Power BI Premium 常见问题解答](service-premium-faq.md)   



更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

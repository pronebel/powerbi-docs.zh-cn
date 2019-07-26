---
title: 部署 Power BI 数据网关指南
description: 了解部署 Power BI 网关的最佳做法和注意事项。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271727"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>部署 Power BI 数据网关指南

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

本文提供在网络环境中部署 Power BI 数据网关的指南和注意事项。

有关如何下载、安装、配置和管理本地数据网关的信息，请参阅[本地数据网关是什么](/data-integration/gateway/service-gateway-onprem)。 还可以通过访问 [Microsoft Power 博客](https://powerbi.microsoft.com/blog/)和[Microsoft Power BI 社区](https://community.powerbi.com/)网站来了解有关本地数据网关和 Power BI 的详细信息。

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>本地数据网关的安装注意事项

在为 Power BI 云服务安装本地数据网关之前，应记住几个注意事项。 以下各部分将介绍这些注意事项。

### <a name="number-of-users"></a>用户数

使用报表（该报表使用网关）的用户数是决定安装该网关位置的重要指标。 下面是要考虑的一些问题：

* 用户是否在一天中的不同时间使用这些报表？
* 他们使用什么类型的连接（DirectQuery 或 Import）？
* 是否所有用户都使用相同的报表？

如果用户每天都在同一时间访问给定的报表，则需要确保在能够处理所有这些请求的计算机上安装网关（请参阅以下各部分，了解可帮助确定此问题的性能计数器和最低要求）。

在 Power BI  中有一个约束，只允许每个报表  有一个  网关。因此，即使报表基于多个数据源，所有此类数据源也必须通过单个网关。 但是，如果仪表板基于多个  报表，则可以对每个提供的报表使用专用网关，从而将网关负载分发到有助于该单个仪表板的多个报表中。

### <a name="connection-type"></a>连接类型

 Power BI 提供了两种连接类型：  DirectQuery 和 Import  。 并非所有数据源都支持这两种连接类型，而且有很多原因可能会导致选择其中一种类型，如安全要求、性能、数据限制和数据模型大小。 可在[可用数据源类型列表](service-gateway-data-sources.md#list-of-available-data-source-types)部分中详细了解连接类型和支持的数据源。

根据所使用的连接类型，网关的用法可能会有所不同。 例如，应尽可能将 DirectQuery  数据源从“计划刷新”  数据源中分离出来（假设它们位于不同的报表中并且可以分开）。 这样做可以防止网关将成千上万的 DirectQuery 请求排入队列的时间与上午计划用于公司主仪表板的大型数据模型刷新时间相同。 以下是每种类型需要考虑的内容：

* “计划刷新”  ：根据查询大小和每天发生的刷新次数，可以选择保持在推荐的最低硬件要求之间或升级到更高性能的计算机。 如果没有折叠给定的查询，网关计算机上会发生转换，因此网关计算机可受益于拥有更多可用的 RAM。

* DirectQuery  ：每次任何用户打开报表或查看数据时，都会发送查询。 因此，如果预计有超过 1,000 位用户同时访问数据，那么需要确保计算机具有强大耐用的硬件组件。 更多 CPU 内核可使 DirectQuery  连接有更好的吞吐量。

可在本地数据网关[安装注意事项](/data-integration/gateway/service-gateway-install#requirements)中找到对在其上安装网关的计算机的要求。

### <a name="location"></a>位置

网关的安装位置可能会对查询性能产生重大影响，因此请尝试确保网关、数据源位置和 Power BI 租户尽可能靠近彼此，最大限度地减少网络延迟。 若要确定 Power BI 租户位置，请在 Power BI 服务中选择“?”  图标（右上角），然后选择“关于 Power BI”  。

![确定 Power BI 租户位置](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

此外，如果打算将 Power BI 网关与 Azure Analysis Services 一起使用，请确保两者中的数据区域匹配。 有关为多个服务设置数据区域的详细信息，请观看[此视频](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/)。

## <a name="next-steps"></a>后续步骤

* [配置代理设置](/data-integration/gateway/service-gateway-proxy)  
* [对网关进行排除故障 - Power BI](service-gateway-onprem-tshoot.md)  
* [本地数据网关常见问题解答 - Power BI](service-gateway-power-bi-faq.md)  

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


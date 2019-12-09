---
title: 深入了解本地数据网关
description: 本文深入探讨了本地网关。 它探讨了该服务与 Analysis Services 配合使用时在 Azure Active Directory 和本地 Active Directory 中的运行方式
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: c277c21ffd3546307f9c38dfc06364324702986f
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699374"
---
# <a name="on-premises-data-gateway-in-depth"></a>深入了解本地数据网关

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

我们已将本文中的信息移至 Power BI 和常规文档中的几篇文章中。请按照每个标题下的链接查找相关内容。

## <a name="how-the-gateway-works"></a>网关的工作原理

请参阅[本地数据网关体系结构](/data-integration/gateway/service-gateway-onprem-indepth)。

## <a name="list-of-available-data-source-types"></a>可用数据源类型的列表

请参阅[管理数据源](service-gateway-data-sources.md)。

## <a name="authentication-to-on-premises-data-sources"></a>向本地数据源进行身份验证

请参阅[向本地数据源进行身份验证](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources)。

## <a name="authentication-to-a-live-analysis-services-data-source"></a>向实时 Analysis Services 数据源进行身份验证

请参阅[向实时 Analysis Services 数据源进行身份验证](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source)。

## <a name="role-based-security"></a>基于角色的安全性

请参阅[基于角色的安全性](service-gateway-enterprise-manage-ssas.md#role-based-security)。

## <a name="row-level-security"></a>行级别安全性

请参阅[行级别安全性](service-gateway-enterprise-manage-ssas.md#row-level-security)。

## <a name="what-about-azure-active-directory"></a>Azure Active Directory 如何？

请参阅 [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory)。

## <a name="how-do-i-tell-what-my-upn-is"></a>如何辨别我的 UPN？

请参阅[如何辨别我的 UPN？](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is)。

## <a name="map-user-names-for-analysis-services-data-sources"></a>映射 Analysis Services 数据源的用户名

请参阅[映射 Analysis Services 数据源的用户名](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources)。

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>将本地 Active Directory 与 Azure Active Directory 同步

请参阅[将本地 Active Directory 与 Azure Active Directory 同步](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory)。

## <a name="what-to-do-next"></a>接下来该怎么做？

请参阅有关数据源的文章：

[管理数据源](service-gateway-data-sources.md)
[管理你的数据源 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[管理数据源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[管理数据源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
[管理数据源 - Oracle](service-gateway-onprem-manage-oracle.md)  
[管理数据源 - 导入/计划刷新](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>这时事情可能会出错

请参阅[对本地数据网关进行故障排除](/data-integration/gateway/service-gateway-tshoot)和[对网关进行故障排除 - Power BI](service-gateway-onprem-tshoot.md)。

## <a name="sign-in-account"></a>登录帐户

请参阅[登录帐户](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account)。

## <a name="windows-service-account"></a>Windows 服务帐户

请参阅[更改本地数据网关服务帐户](/data-integration/gateway/service-gateway-service-account)。

## <a name="ports"></a>端口

请参阅[端口](/data-integration/gateway/service-gateway-communication#ports)。

## <a name="forcing-https-communication-with-azure-service-bus"></a>强制 HTTPS 与 Azure 服务总线通信

请参阅[对 Azure 服务总线强制使用 HTTPS 通信](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus)。

## <a name="support-for-tls-12"></a>对 TLS 1.2 的支持

请参阅[用于网关流量的 TLS 1.2](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic)。

## <a name="how-to-restart-the-gateway"></a>如何重启网关

请参阅[重启网关](/data-integration/gateway/service-gateway-restart)。

## <a name="next-steps"></a>后续步骤

[本地数据网关是什么？](service-gateway-onprem.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
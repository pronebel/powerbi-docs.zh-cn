---
title: 使用到本地数据源的单一登录 (SSO)
description: 配置网关以启用从 Power BI 到本地数据源的单一登录 (SSO)。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6f270c28f643736f07c09ceb3e544e473f831ad9
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271854"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Power BI 中网关的单一登录 (SSO) 概述

通过使用 Kerberos 约束委派或安全断言标记语言 (SAML) 配置本地数据网关，可以获得无缝的单一登录连接，从而使 Power BI 报表和仪表板可以从本地数据进行更新。 本地数据网关使用用于连接到本地数据源的 DirectQuery 实现 SSO。

目前支持以下数据源：

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA（[Kerberos](service-gateway-sso-kerberos.md) 和 [SAML](service-gateway-sso-saml.md)）
* SAP BW ([Kerberos](service-gateway-sso-kerberos.md))
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

当用户与 Power BI 服务中的 DirectQuery 报表进行交互时，每个交叉筛选、切片、排序和报表编辑操作都可能会导致针对基础的本地数据源执行实时查询。 为数据源配置了 SSO 时，查询将以与 Power BI 交互的用户标识（即通过 Web 体验或 Power BI 移动应用）执行。 因此，每个用户都可以精确地看到自己在基础数据源中拥有权限的数据 - 配置单一登录后，不同用户之间没有共享的数据缓存。

## <a name="query-steps-when-running-sso"></a>运行 SSO 时的查询步骤

使用 SSO 运行的查询由三个步骤组成，如下图所示。

![SSO 查询步骤](media/service-gateway-sso-overview/sso-query-steps.png)

以下是有关这些步骤的其他详细信息：

1. 对于每个查询，当向配置的网关发送查询请求时，Power BI 服务  包括用户主体名称  (UPN)。

2. 网关需要将 Azure Active Directory UPN 映射到本地 Active Directory 标识。

   a.  如果已配置 Azure AD DirSync（也称为“Azure AD Connect”），则会自动在网关中进行映射  。

   b.  或者，网关可以通过在本地 Active Directory 域进行查找的方式来查找 Azure AD UPN，并将其映射到本地用户。

3. 网关服务进程模拟映射的本地用户，打开与基础数据库的连接并发送查询。 网关不需要与数据库安装在同一台计算机上。

## <a name="next-steps"></a>后续步骤

现在，你已了解 SSO 的基础知识，请阅读有关 Kerberos 和 SAML 的更多详细信息：

* [单一登录 (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [单一登录 (SSO) - Kerberos - 基于资源](service-gateway-sso-kerberos-resource.md)
* [单一登录 (SSO) - SAML](service-gateway-sso-saml.md)

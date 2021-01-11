---
title: 有关在 Power BI 嵌入式分析中生成嵌入令牌以增强嵌入式 BI 见解的注意事项
description: 了解生成嵌入令牌的注意事项、限制和所需权限。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 2f8da415b40bc5d9a621e5a0df8c1edffbbc8791
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886847"
---
# <a name="considerations-when-generating-an-embed-token"></a>生成嵌入令牌的注意事项

[生成令牌](/rest/api/power-bi/embedtoken)是一种 REST API，可生成用于在 Web 应用或门户中嵌入 Power BI 项的令牌。 该令牌用于授权对 Power BI 服务的请求。

生成令牌 API 使用单个标识（主用户或服务主体）为单个用户生成令牌，具体取决于该用户在应用中的凭据（有效标识）。

身份验证成功后，系统将授予对相关数据的访问权限。

>[!NOTE]
>生成令牌仅在[为客户嵌入内容](embed-sample-for-customers.md)（亦称为“应用拥有数据”方案）时适用。

可以使用以下 API 生成令牌：

* [仪表板](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [数据集](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [为多个报表生成令牌](/rest/api/power-bi/embedtoken/generatetoken)


* [报表创建](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [报表](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [平铺](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>工作区版本

Power BI 有两个工作区版本：“经典”工作区和“新”工作区。 可以在[新工作区和经典工作区的差异](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences)中深入了解这两种工作区之间的差异。

创建嵌入令牌时，不同的工作区具有不同的注意事项，且需具备不同的权限。

|                  |经典工作区 |新工作区|
|------------------|---------|--------|
|**注意事项**|<li>数据集和项必须在同一工作区中</li><li>无法使用服务主体</li>  |数据集和项可以在两个不同的新工作区中 |
|**工作区权限**|主用户必须是工作区的管理员  |服务主体或主用户必须至少是两个工作区的成员 |

>[!NOTE]
>* 不能为[我的工作区](../../consumer/end-user-workspaces.md#types-of-workspaces)创建嵌入令牌。
>* “项”一词是指 Power BI 项，例如仪表板、磁贴、问答或报表。

## <a name="securing-your-data"></a>保护数据

创建解决方案时，请考虑以下两种保护数据的方法：

* [基于工作区的隔离](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [基于行级别安全性的隔离](embed-multi-tenancy.md#row-level-security-based-isolation)

如果计划使用 RLS 方法，请查看本文末尾的 [RLS 注意事项和限制](generate-embed-token.md#row-level-security)。

## <a name="token-permissions"></a>令牌权限

在生成令牌 API 中，GenerateTokenRequest 部分描述令牌权限。

>[!NOTE]
>本节列出的令牌权限不适用于[为多个报表生成令牌](/rest/api/power-bi/embedtoken/generatetoken) API。

### <a name="access-level"></a>访问级别

使用 accessLevel 参数确定用户的访问级别。

* 查看 - 授予用户查看权限。

* 编辑 - 授予用户查看和编辑权限（仅当为报表生成嵌入令牌时适用）。

    如果使用[为多个报表生成令牌](/rest/api/power-bi/embedtoken/generatetoken) API，请使用 allowEdit 参数向用户授予查看和编辑权限。

* 创建 授予用户创建报表的权限（仅当为创建报表生成嵌入令牌时适用）。

    对于报表创建，还必须提供 datasetId 参数。

### <a name="saving-a-copy-of-the-report"></a>保存报表副本

使用 allowSaveAs 布尔值可让用户将报表另存为新报表。 默认情况下，此设置设为“否”。

仅当为报表生成嵌入令牌时，此参数才适用。

### <a name="row-level-security"></a>行级安全性

利用[行级别安全性 (RLS)](embedded-row-level-security.md)，可以选择使用与生成令牌所用的服务主体或主用户的标识不同的标识。 使用此选项，可以根据目标用户显示嵌入的信息。 例如，在你的应用程序中，你可以要求用户登录，如果登录用户为销售人员，则显示只包含销售信息的报表。

如果使用的是 RLS，在某些情况下，可以不指定用户标识（EffectiveIdentity 参数）。 这允许令牌有权访问整个数据库。 此方法可用于向具有查看整个数据集权限的管理员和经理等用户授予访问权限。 但是，不能在每个场景中都使用此方法。 下表列出了不同的 RLS 类型，并介绍了在不指定用户标识的情况下可以使用哪种身份验证方法。

该表还介绍了适用于每个 RLS 类型的注意事项和限制。

|RLS 类型  |能否在不指定有效用户 ID 的情况下生成嵌入令牌？  |注意事项和限制  |
|---------|---------|---------|
|云行级别安全性 (Cloud RLS)      |✔ 主用户<br/>✖ 服务主体          |         |
|RDL（分页报表）     |✖ 主用户<br/>✔ 服务主体        |不能使用主用户为 RDL 生成嵌入令牌。         |
|Analysis Services (AS) 本地实时连接    |✔ 主用户<br/>✖ 服务主体         |生成嵌入令牌的用户还需具备以下权限之一：<li>网关管理员权限</li><li>Datasource 模拟权限 (ReadOverrideEffectiveIdentity)</li>         |
|Analysis Services (AS) Azure 实时连接    |✔ 主用户<br/>✖ 服务主体         |无法重写生成嵌入令牌的用户标识。 自定义数据可用于实现动态 RLS 或安全筛选。<br/><br/>**注意：** 服务主体必须提供其对象 ID 作为有效标识（RLS 用户名）。         |
|单一登录 (SSO)     |✔ 主用户<br/>✖ 服务主体         |可以使用有效标识对象中的标识 blob 属性提供显式 (SSO) 标识         |
|SSO 和云 RLS     |✔ 主用户<br/>✖ 服务主体         |必须提供以下内容：<li>有效标识对象的标识 blob 属性中的显式 (SSO) 标识</li><li>有效 (RLS) 标识（用户名）</li>         |

>[!NOTE]
>服务主体必须始终提供以下内容：
>* 具有 RLS 数据集的任何项的标识。
>* 对于 SSO 数据集，定义了用户名属性的有效 RLS 标识。

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[注册应用](register-app.md)

> [!div class="nextstepaction"]
>[适用于客户的 Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Azure Active Directory 中的应用程序和服务主体对象](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[配合使用本地数据网关与服务主体的行级别安全性](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[使用服务主体嵌入 Power BI 内容](embed-service-principal.md)
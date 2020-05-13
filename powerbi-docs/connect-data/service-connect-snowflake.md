---
title: 使用 Power BI 连接到 Snowflake
description: 适用于 Power BI 的 Snowflake SSO
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83300312"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>在 Power BI 服务中连接到 Snowflake

## <a name="introduction"></a>简介

在 Power BI 服务中连接到 Snowflake 与其他连接器只在一方面不同，就是为 AAD 提供了额外的功能（使用 SSO 选项）。 集成的不同部分需要不同于 Snowflake、Power BI 和 Azure 的管理角色。 还可以选择在不使用 SSO 的情况下启用 AAD 身份验证。 基本身份验证的方式类似于服务中的其他连接器。

如果你对配置 AAD 集成有兴趣，还可以选择启用 SSO：
* 如果你是 Snowflake 管理员，请参阅 Snowflake 文档中的 [Power BI SSO 到 Snowflake - 入门](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html)文章。
* (SSO) 如果你是 Power BI 管理员，请查看“Power BI 服务配置 - 管理门户”部分
* (SSO) 如果你是 Power BI 创建者，请查看“Power BI 服务配置 - 启用数据集”部分

## <a name="power-bi-service-configuration"></a>Power BI 服务配置

### <a name="admin-portal"></a>管理门户

如果要启用 SSO，需要租户管理员转到管理门户并批准向 Snowflake 发送 Power BI AAD 凭据。

![Snowflake SSO 的租户管理员设置](media/service-connect-snowflake/snowflakessotenant.png)

导航到“管理门户”，选择“租户设置”侧栏项，向下滚动到“集成设置”，你将看到“Snowflake SSO”的选项。

收到警告后，必须手动启用此设置，以同意将 AAD 令牌发送到 Snowflake 服务器。 若要启用它，请单击“已禁用”开关，按“应用”并等待设置更改生效。 服务传播配置最长可能需要一小时。

完成此操作后，即可通过 SSO 使用报表。

### <a name="configuring-a-dataset-with-aad"></a>使用 AAD 配置数据集

基于 Snowflake 连接器的报表发布到 web 后，在 Power BI web 服务中，数据集创建者需要导航到适当的工作区，选择“数据集”，然后选择“设置”（位于相关数据集旁边的其他操作的“...”菜单下）。

由于 Power BI 的工作方式，仅当没有数据源通过本地数据网关运行时，SSO 才有效。

* 如果在数据模型中仅使用 Snowflake 源，选择不使用本地数据网关即可使用 SSO
* 如果你使用的是 Snowflake 源和其他源，则如果没有源使用本地数据网关，便可以使用 SSO
* 如果通过本地数据网关使用 Snowflake 源，则当前不支持 AAD 凭据。 如果尝试从安装了网关的单个 IP（而不是从整个 Power BI IP 范围）访问 VNet，此信息可能相关。
* 如果要将 Snowflake 源与需要网关的另一个源一起使用，则还需要通过本地数据网关使用 Snowflake，并且将不能使用 SSO。

有关如何使用本地数据网关的详细信息，请参阅文章[什么是本地数据网关？](https://docs.microsoft.com/power-bi/service-gateway-onprem)

如果不使用网关，则至此已设置完毕。 如果已在本地数据网关上配置 Snowflake 凭据，但仅在模型中使用该数据源，则可以单击“数据集设置”页上的开关以关闭该数据模型的网关。

![用于关闭网关的数据集设置](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

数据集创建者需要选择“数据源凭据”并登录。 数据集可通过基本凭据或 OAuth2 (AAD) 凭据登录到 Snowflake。 如果选择使用 AAD，则可以允许数据集使用 SSO。 第一个用户登录到 Snowflake 以访问该数据集时，需要选择要求其他用户使用其 Oauth2 凭据检索数据的选项。 这将启用 AAD SSO。 无论初始用户是通过基本身份验证还是 OAuth2 (AAD) 登录，都将发送 AAD 凭据以使用 SSO。 

![Snowflake SSO 的数据集设置](media/service-connect-snowflake/snowflakessocredui.png)

完成此操作后，任何其他用户都应自动使用其 AAD 身份验证连接到该 Snowflake 数据集中的数据。

如果选择不启用 SSO，刷新报表的用户将使用登录用户的凭据，与大多数其他 Power BI 报表相同。

### <a name="troubleshooting"></a>故障排除

如果遇到与集成有关的任何问题，请参阅 Snowflake [故障排除指南](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting)。


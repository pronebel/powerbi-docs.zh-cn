---
title: 列入允许列表的 Power BI URL
description: 本文介绍客户使用 Power BI 时应可访问的终结点。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/22/2018
ms.custom: seodec18
ms.openlocfilehash: 39a62950260789b50be034c2f55808e6991764db
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54293995"
---
# <a name="power-bi-urls-for-whitelisting"></a>列入允许列表的 Power BI URL

Power BI 联机服务也称为 Power BI SaaS（服务型软件）应用程序，需要连接 Internet。 下面的终结点应可供使用 Power BI 联机服务的客户访问。

若要使用 Power BI 联机服务，必须有权连接到下表中标记为“必需”的终结点，以及链接站点上任何标记为“必需”的终结点。 如果指向外部站点的链接表示特定部分，只需查看该部分中的终结点即可。

为使特定功能正常运行，标记为“可选”的终结点也可能列入允许列表。

Power BI 联机服务只需针对列出的终结点打开 TCP 端口 443。

通配符 (*) 表示根域下的所有级别，并且在信息不可用时，我们将使用 N/A。 “目标”列是包含 FQDN/域和外部站点链接的列表，其中包含更多终结点信息。

>[!Important]
>下表中的信息并不代表美国政府云、德国云或中国云**。

## <a name="authentication"></a>身份验证

Power BI 依赖于 Office 365 身份验证和标识部分中所需的终结点。 若要使用 Power BI，必须能够连接到以下链接网站中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 身份验证和标识 | 请参阅 Office 365 文档，了解 [Office Online 和常用 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N/A |

## <a name="general-site-usage"></a>常规站点使用

要实现 Power BI 的常规使用，必须能够连接到下表和以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 后端 API | *.analysis.windows.net | TCP 443 |
| 2 | **必需：** Office 365 集成 | 请参阅 Office 365 文档，了解 [Office Online 和常用 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/A |
| 3 | **必需：** 门户 | app.powerbi.com | TCP 443 |
| 4 | **必需：** 服务遥测 | dc.services.visualstudio.com | TCP 443 |
| 5 | **可选：** 信息性消息 | dynmsg.modpim.com | TCP 443 |
| 6 | **可选：** NPS 调查 | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>管理

若要在 Power BI 中执行管理功能，必须能够连接到以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 用于管理用户和查看审核日志 | 请参阅 Office 365 文档，了解 [Office Online 和常用 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/A |
| | | |

## <a name="getting-data"></a>获取数据

若要从特定数据源（如 OneDrive）获取数据，必须能够连接到下表中的终结点。 访问其他 Internet 域和 URL 可能需要组织内部使用特定的数据源。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** AppSource（Power BI 中的内部或外部应用） | appsource.microsoft.com </br> *.s-microsoft.com  | TCP 443 |
| 2 | **可选：** 登录并获取内容包的数据 | 取决于使用的内容包 | 取决于使用的内容包 |
| 3 | **可选：** 从个人 OneDrive 中导入文件 | 请参阅 [OneDrive 必需的 URL 和端口](https://docs.microsoft.com/onedrive/required-urls-and-ports) | N/A |
| 4 | **可选：** 60 秒教程视频中的 Power BI | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 5 | **可选：** PubNub 流式处理数据源 | 请参阅 [PubNub 文档](https://support.pubnub.com/support/solutions/articles/14000043522) | N/A |
| | | |

## <a name="dashboard-and-report-integration"></a>仪表板和报表集成

Power BI 依赖于特定终结点，以便能够支持仪表板和报表。 必须能够连接到下表和以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** Excel 集成 | 请参阅 Office 365 文档，了解 [Office Online 和常用 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/A |
| | | |

## <a name="custom-visuals"></a>自定义视觉对象

Power BI 依赖于特定终结点，以便能够查看和访问自定义视觉对象。 必须能够连接到下表和以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 从市场接口或从文件导入自定义视觉对象 | *.azureedge.net </br> *.blob.core.windows.net </br> store.office.com | TCP 443 |
| 2 | **可选：** 必应地图 | bing.com </br> platform.bing.com </br> *.virtualearth.net | TCP 443 |
| 3 | **可选：** PowerApps | 请参阅 PowerApps 系统要求站点中的[必需的服务](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services)部分 | N/A |
| 4 | **可选：** Visio | 请参阅 Office 365 文档，了解 [Office Online 和常用 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 以及 [SharePoint Online 和 OneDrive for Business](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N/A |
| | | |

## <a name="related-external-sites"></a>相关外部站点

Power BI 可链接到其他相关站点。 包括文档、支持、新功能请求等站点。 这些站点不会影响 Power BI 的功能，可以根据需要将其加入允许名单。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **可选：** 社区站点 | community.powerbi.com </br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **可选：** 文档站点 | docs.microsoft.com </br> img-prod-cms-rt-microsoft-com.akamaized.net </br> statics-uhf-eas.akamaized.net </br> cdnssl.clicktale.net </br> ing-district.clicktale.net | TCP 443 |
| 3 | **可选：** 下载站点（用于 Power BI Desktop 等） | download.microsoft.com | TCP 443 |
| 4 | **可选：** 外部重定向 | aka.ms </br> go.microsoft.com | TCP 443 |
| 5 | **可选：** 意见反馈网站| ideas.powerbi.com </br> powerbi.uservoice.com | TCP 443 |
| 6 | **可选：** Power BI 站点 - 登录页面、详细信息链接、支持站点、下载链接、合作伙伴展示等。 | powerbi.microsoft.com | TCP 443 |
| 7 | **可选：** Power BI 开发人员中心 | dev.powerbi.com | TCP 443 |
| 8 | **可选：** 支持站点 | support.powerbi.com </br> s3.amazonaws.com </br> *.olark.com </br> logx.optimizely.com </br> mscom.demdex.net </br> tags.tiqcdn.com | TCP 443 |
| | | |
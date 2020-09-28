---
title: 将 Power BI URL 添加到允许列表
description: 本文列出了要添加到用于连接到 Power BI 的允许列表的 URL 终结点和端口。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: e4aec179b298c5a8ca52cf73ac5fdceed7e8602a
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90857671"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>将 Power BI URL 添加到允许列表
[//]: # "suparnap、miwehnia、natham 是用于维护此列表的联系人"

Power BI 服务需要 Internet 连接。 本文的表中列出的终结点应可供使用 Power BI 服务的客户访问。

若要使用 Power BI 服务，必须能够连接到下表中标记为“必需”的终结点，以及链接站点上任何标记为“必需”的终结点。 如果指向外部站点的链接表示特定部分，只需查看该部分中的终结点即可。

为使特定功能正常运行，标记为“可选”的终结点也可能添加到允许列表。

Power BI 服务只需针对列出的终结点打开 TCP 端口 443。

通配符 (*) 表示根域下的所有级别，并且在信息不可用时，我们将使用 N/A。 “目标”列列出了域名和外部站点链接，其中包含更多终结点信息。

>[!Important]
>下表中的信息不适用于 Power BI Germany、由中国的世纪互联公司运营的 Power BI 或 Power BI for US Government。 若要详细了解如何在云服务之间通信，请阅读[连接政府版本和全球 Azure 云服务](service-govus-overview.md#connect-government-and-global-azure-cloud-services)。

## <a name="authentication"></a>身份验证

Power BI 依赖于 Microsoft 365 身份验证和标识部分中所需的终结点。 若要使用 Power BI，必须能够连接到以下链接网站中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 身份验证和标识 | 请参阅 [Microsoft 365 常用 URL 和 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文档  | 不适用 |

## <a name="general-site-usage"></a>常规站点使用

要实现 Power BI 的常规使用，必须能够连接到下表和以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 后端 API | api.powerbi.com | TCP 443 |
| 2 | **必需：** 后端 API | *.analysis.windows.net | TCP 443 |
| 3 | **必需：** 后端 API | *.pbidedicated.windows.net | TCP 443 |
| 4 | **必需：** 内容分发网络 (CDN) | content.powerapps.com | TCP 443 |
| 5 | **必需：** Microsoft 365 集成 | 请参阅 [Microsoft 365 常用 URL 和 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文档 | 不适用 |
| 6 | **必需：** 门户 | *.powerbi.com | TCP 443 |
| 7 | **必需：** 服务遥测 | dc.services.visualstudio.com | TCP 443 |
| 8 | **可选：** 信息性消息 | dynmsg.modpim.com | TCP 443 |
| 9 | **可选：** NPS 调查 | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>管理

若要在 Power BI 中执行管理功能，必须能够连接到以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 用于管理用户和查看审核日志 | 请参阅 [Microsoft 365 常用 URL 和 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文档 | 不适用 |
| | | |

## <a name="getting-data"></a>获取数据

若要从特定数据源（如 OneDrive）获取数据，必须能够连接到下表中的终结点。 组织中使用的特定数据源可能需要访问其他 Internet 域和 URL。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** AppSource（Power BI 中的内部或外部应用） | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **可选：** 登录并获取内容包的数据 | 取决于使用的内容包 | 取决于使用的内容包 |
| 3 | **可选：** 从个人 OneDrive 中导入文件 | 请参阅 [OneDrive 必需的 URL 和端口](/onedrive/required-urls-and-ports) | 不适用 |
| 4 | **可选：** 60 秒教程视频中的 Power BI | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **可选：** PubNub 流式处理数据源 | 请参阅 [PubNub 文档](https://support.pubnub.com/support/solutions/articles/14000043522) | 不适用 |
| | | |

## <a name="dashboard-and-report-integration"></a>仪表板和报表集成

Power BI 依赖于特定终结点，以便能够支持仪表板和报表。 必须能够连接到下表和以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** Excel 集成 | 请参阅 [Microsoft 365 常用 URL 和 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文档 | 不适用 |
| | | |

## <a name="power-bi-visuals"></a>Power BI 视觉对象

Power BI 依赖特定终结点来查看和访问 Power BI 视觉对象。 必须能够连接到下表和以下链接站点中的终结点。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **必需：** 从市场接口或从文件导入自定义视觉对象 | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **可选：** 必应地图 | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **可选：** PowerApps | 请参阅 PowerApps 系统要求站点中的[必需的服务](/powerapps/maker/canvas-apps/limits-and-config#required-services)部分 | 不适用 |
| 4 | **可选：** Visio | 请参阅 [Microsoft 365 常用 URL 和 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文档，以及 [SharePoint Online 和 OneDrive for Business](/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) 文档 | 不适用 |
| | | |

## <a name="related-external-sites"></a>相关外部站点

Power BI 可链接到其他相关站点。 这些站点托管文档、支持、新功能请求等。 对这些站点的访问不会影响 Power BI 的功能，因此将其添加到允许列表是可选的。

| 行 | 用途 | 目标 | 端口 |
| --- | --- | --- | --- |
| 1 | **可选：** 社区站点 | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **可选：** 文档站点 | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **可选：** 下载站点（用于 Power BI Desktop 等） | download.microsoft.com | TCP 443 |
| 4 | **可选：** 外部重定向 | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **可选：** 意见反馈网站| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **可选：** Power BI 站点 - 登录页面、详细信息链接、支持站点、下载链接、合作伙伴展示等。 | powerbi.microsoft.com | TCP 443 |
| 7 | **可选：** Power BI 开发人员中心 | dev.powerbi.com | TCP 443 |
| 8 | **可选：** 支持站点 | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
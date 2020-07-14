---
title: 适用于德国政府客户的常见问题解答
description: 针对德国政府客户，解答 Power BI 德国政府服务的常见问题
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: fb67243b14fc5a89de0efc6f8248aa2b37fb2bbf
ms.sourcegitcommit: 181679a50c9d7f7faebcca3a3fc55461f594d9e7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86034074"
---
# <a name="frequently-asked-questions-for-power-bi-for-germany-cloud-customers"></a>适用于德国云客户的 Power BI 常见问题解答
**Power BI 服务**具有可用于欧盟/欧洲自由贸易协议 (EU/EFTA) 客户的版本，通常称为 Microsoft Cloud Deutschland (MCD)。 本文中讨论的 **Power BI 服务**版本是为欧盟/EFTA 客户专门设计的，独立且不同于 **Power BI 服务**的商业版本或为政府客户提供的 Power BI 服务。

![Microsoft Power BI Germany 主页的屏幕截图。](media/service-govde-faq/govde-faq_01.png)

## <a name="questions-and-answers"></a>问题与解答

以下问题和答案为 Microsoft Cloud Deutschland (MCD)（为欧盟/EFTA 客户专门提供的 Power BI 服务云）中的 Power BI Pro 服务提供重要信息。

1. **德国云的 Power BI 服务是什么？**
   
   面向欧盟/EFTA 客户的 Power BI 服务（也称为 Microsoft Cloud Deutschland (MCD)）是符合 Power BI 服务要求的欧盟/EFTA 云，从德国数据中心传递。 用于欧盟/EFTA 云的 Power BI 服务中的所有客户数据均以静态方式存储在德国，T 系统作为独立的德国数据被信任方运行，并具有对德国法律所控制数据的物理和逻辑访问权限。 欧盟/EFTA 云的 Power BI 服务要求使用与 Power BI 服务的商业版帐户不同且独立的帐户。 请参阅[此处](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud)，了解有关 Microsoft Cloud Deutschland 的详细信息。
2. **在哪里可以找到 Power BI Germany 云的定价和注册信息？**
   
   你可以在 [Power BI Germany 云主页](https://powerbi.microsoft.com/power-bi-germany/)上找到大量信息，其中包括定价信息。 在该页面上，还可以找到一个用于注册 Power BI Pro 服务 30 天试用版（包含 25 个用户许可证）的链接。 在注册试用版的过程中，可以根据需要选择购买或添加其他许可证。 此外，我们还提供企业协议 (EA)、政府和非营利性定价。 请联系 Microsoft 客户代表，了解详细信息。
3. **我有一个德国云租户，它是 Azure Germany 和/或 Office 365 Germany 订阅的一部分。我可以使用现有租户注册 Power BI Germany 吗？**
   
   是的。 作为注册过程的一部分，你可以选择使用现有德国云租户管理员帐户登录，并将 Power BI Pro 服务许可证添加到德国云中的现有租户。 请注意，德国云租户和用户帐户与德国云的 Power BI 服务不同。
4. **德国云的 Power BI 服务是否提供免费服务？**
   
   不行。 我们不会在德国云的 Power BI 服务中提供免费的许可证版本。 但是，如果你的业务需求符合 Power BI 免费产品/服务要求，我们建议你[在我们的公有云中注册Power BI 免费产品/服务](https://powerbi.microsoft.com/get-started/)。
5. **我可以将 Power BI Desktop、Power BI 移动版、本地数据网关和 Publisher for Excel 与德国云的 Power BI 服务一起使用吗？**
   
   是。 我们更新了 Power BI 客户端产品，以便与德国云的 Power BI 服务无缝协作。 请使用德国云的 Power BI 服务帐户登录，以便开始使用与德国云的 Power BI 服务相同的客户端产品。 你可以从以下位置下载最新版本的客户端产品：
   
   * [Power BI Desktop](https://powerbi.microsoft.com/desktop/)
   * [Power BI 移动](https://powerbi.microsoft.com/mobile/)
   * [On-premises data gateway (本地数据网关)](https://powerbi.microsoft.com/gateway/)
   * [Power BI Publisher for Excel](https://powerbi.microsoft.com/excel-dashboard-publisher/)
6. **德国云的 Power BI 服务是存在任何功能限制？**
   
   以下服务功能目前在德国云的 Power BI 服务中不可用：
   
   * 向网络发布
   * ESRI 提供的 ArcGIS 地图
   * Power BI Embedded（单独计量的 ISV 许可，将在以后通过 [Microsoft Azure Germany](https://azure.microsoft.com/overview/clouds/germany/) 提供）
7. **在哪里可以找到德国云的 Power BI 服务具体配置信息，以便在我的应用程序中使用和集成？**
   
   我们更新了 [SaaS 嵌入开发人员示例](https://github.com/Microsoft/PowerBI-Developer-Samples)，以及德国云和其他 Power BI 云的具体配置信息。 请查看示例中的 Cloud Configs 文件夹，获取云具体配置终点。 下表列出了德国云的 Power BI 服务（以及用于交叉引用的公有云）的各种配置终点。

| **终结点名称和/或使用情况** | **德国云 URL 的 Power BI 服务** | **公有云中的等效 URL（用于交叉引用）** |
| --- | --- | --- |
| 主页、注册和登录 |[https://powerbi.microsoft.com/power-bi-germany/](https://powerbi.microsoft.com/power-bi-germany/) |[https://powerbi.microsoft.com/](https://powerbi.microsoft.com/) |
| Power BI 服务直接登录 |[https://app.powerbi.de/?noSignUpCheck=1](https://app.powerbi.de/?noSignUpCheck=1) |[https://app.powerbi.com/?noSignUpCheck=1](https://app.powerbi.com/?noSignUpCheck=1) |
| 服务 API |[https://api.powerbi.de/](https://api.powerbi.de/) |[https://api.powerbi.com/](https://api.powerbi.com/) |
| 用于用户许可证管理、服务运行状态，以及管理员支持请求的 Office 门户 |[https://portal.office.de/](https://portal.office.de/) |[https://portal.office.com/](https://portal.office.com/) |
| AAD 颁发机构 URI |[https://login.microsoftonline.de/common/oauth2/authorize/](https://login.microsoftonline.de/common/oauth2/authorize/) |[https://login.microsoftonline.com/common/oauth2/authorize/](https://login.microsoftonline.com/common/oauth2/authorize/) |
| Power BI 服务资源 URI |[https://analysis.cloudapi.de/powerbi/api](https://analysis.cloudapi.de/powerbi/api) |[https://analysis.windows.net/powerbi/api](https://analysis.windows.net/powerbi/api) |
| Power BI 视觉对象库 |[https://app.powerbi.de/visuals/](https://app.powerbi.de/visuals/) |[https://app.powerbi.com/visuals/](https://app.powerbi.com/visuals/) |
| 注册用于 Power BI 的应用程序（用于 Embedded） |[https://app.powerbi.de/apps](https://app.powerbi.de/apps) |[https://app.powerbi.com/apps](https://app.powerbi.com/apps) |
| Azure 门户（用于 Embedded） |[https://portal.microsoftazure.de/](https://portal.microsoftazure.de/) |[https://portal.azure.com/](https://portal.azure.com/) |
| 社区 |[https://community.powerbi.com/](https://community.powerbi.com/) |[https://community.powerbi.com/](https://community.powerbi.com/) |

## <a name="next-steps"></a>后续步骤
你可以使用 Power BI 执行各种操作。 有关更多信息和学习资料（包括介绍如何注册服务的文章），请查看以下资源：

* [Power BI 的引导学习](../guided-learning/index.yml)
* [Power BI 服务入门](../fundamentals/service-get-started.md)
* [什么是 Power BI Desktop？](../fundamentals/desktop-what-is-desktop.md)

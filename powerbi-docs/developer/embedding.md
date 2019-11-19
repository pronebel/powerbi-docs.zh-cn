---
title: Power BI 嵌入式分析
description: Power BI 提供用于使用嵌入式分析将仪表板和报表嵌入到应用程序的 API。 详细了解如何使用 Power BI 嵌入式分析软件、嵌入式分析工具或嵌入式商业智能工具嵌入到 PaaS 环境和 SaaS 环境中。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: 501b43b7a17d60bbb277cd68c1a5d13e09b14bd5
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73430728"
---
# <a name="embedded-analytics-with-power-bi"></a>Power BI 嵌入式分析

Azure (PaaS) 中的 Power BI 服务 (SaaS) 和 Power BI 嵌入式服务具有用于嵌入仪表板和报表的 API。 嵌入内容时，你可以通过它访问仪表板、网关和工作区等最新的 Power BI 功能。

可使用[嵌入安装程序工具](https://aka.ms/embedsetup)快速开始并下载示例应用程序。

选择最适合你的解决方案：

* 通过[为组织嵌入内容](embedding.md#embedding-for-your-organization)，可以扩展 Power BI 服务。 为达成此目标，请实现[为组织嵌入内容](https://aka.ms/embedsetup/UserOwnsData)解决方案。
* 通过[为客户嵌入内容](embedding.md#embedding-for-your-customers)，可为没有 Power BI 帐户的用户嵌入仪表板和报表。 为达成此目标，请实现[为客户嵌入内容](https://aka.ms/embedsetup/AppOwnsData)解决方案。

![PBIE 示例](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>使用 API

嵌入 Power BI 内容时，有两个主要方案：
- 为组织的用户（拥有 Power BI 许可证的用户）嵌入内容。 
 
- 为用户和客户嵌入内容，且无需 Power BI 许可证。 

这两种方案都可使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)。

对于没有 Power BI 许可证的客户和用户，可以使用同一 API 为组织或客户提供服务，将仪表板和报表嵌入自定义应用程序中。 客户会看到应用程序管理的数据。 此外，组织中的 Power BI 用户可以直接在 Power BI 中或者在嵌入式应用程序的上下文中使用附加的选项来查看他们的数据  。 可以充分利用 JavaScript 和 REST API 的功能以满足你的嵌入需要。

若要了解嵌入的工作原理，请参阅 [JavaScript 嵌入示例](https://microsoft.github.io/PowerBI-JavaScript/demo/)。

## <a name="embedding-for-your-organization"></a>为组织嵌入内容

通过**为组织嵌入内容**，可以扩展 Power BI 服务。 这种类型的嵌入要求应用程序的用户登录 Power BI 服务来查看内容。 组织中的用户登录后，只能访问他们拥有的，或者他们在 Power BI 服务中共享的仪表板和报表。

组织嵌入内容的示例包括 [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/)、[Microsoft Teams 集成（必须拥有管理员权限）](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/)以及 [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) 等内部应用程序。

若要为组织嵌入内容，请参阅[教程：为组织将 Power BI 内容嵌入应用程序](embed-sample-for-your-organization.md)。

为 Power BI 用户嵌入内容时，通过 [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) 可使用编辑和保存等自助服务功能。

可浏览[嵌入安装程序工具](https://aka.ms/embedsetup/UserOwnsData)以开始并下载示例应用程序，它会逐步引导你为组织集成报表。

## <a name="embedding-for-your-customers"></a>为客户嵌入内容

通过“为客户嵌入内容”，可为没有 Power BI 帐户的用户嵌入仪表板和报表  。 这种类型的嵌入也称为 Power BI Embedded  。

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) 是 Microsoft Azure  提供的一项服务，可让独立软件供应商 (ISV) 和开发人员将视觉对象、报表和仪表板快速嵌入到应用程序。 这种嵌入是通过基于容量、按小时计量的模型完成。

![为客户嵌入内容的嵌入流](media/embedding/powerbi-embed-flow.png)

Power BI Embedded 可让 ISV、其开发人员和客户受益。 例如，ISV 可以使用 Power BI Desktop 开始免费创建视觉对象。 ISV 可以通过尽量减少视觉分析开发工作而更快推向市场，并借由差异化数据体验从竞争中脱颖而出。 ISV 还可以选择对他们使用嵌入式分析创造的附加价值收取相关费用。

使用 Power BI Embedded，客户无需了解有关 Power BI 的任何信息。 可以使用两种不同的方法来创建嵌入式应用程序：
- Power BI Pro 帐户 
- 服务主体 

Power BI Pro 帐户充当应用程序的主帐户（将其视为代理帐户）。 使用此帐户可生成嵌入令牌，用于访问应用程序的 Power BI 仪表板和报表。

[服务主体](embed-service-principal.md)可以使用仅限应用的令牌将 Power BI 内容嵌入应用程序  。 使用它也可以生成嵌入令牌，用于访问应用程序的 Power BI 仪表板和报表。

使用 Power BI Embedded，开发人员可以更专注于构建其应用程序的核心功能，而不是花时间开发视觉对象和分析。 开发人员可以快速满足客户的报表和仪表板需求，并可以通过具有完整存档的 API 和 SDK 轻松嵌入。 通过在应用中启用易于导航的数据浏览，ISV 让客户能够使用任意设备在上下文中快速作出数据驱动型决策。

> [!IMPORTANT]
> 尽管嵌入内容需要 Power BI 服务，但客户无需具有 Power BI 帐户即可查看应用程序的嵌入内容。 

准备迁移到生产环境时，必须为工作区分配专用容量。 Microsoft Azure 中的 Power BI Embedded 提供用于应用程序的[专用容量](azure-pbie-create-capacity.md)。

有关嵌入内容的详细信息，请参阅[如何嵌入 Power BI 内容](embed-sample-for-customers.md)。

## <a name="next-steps"></a>后续步骤

现在可以尝试将 Power BI 内容嵌入应用程序，或尝试为客户嵌入 Power BI 内容。

> [!div class="nextstepaction"]
> [为组织嵌入内容](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Power BI Embedded 是什么？](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[为客户嵌入内容](embed-sample-for-customers.md)

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)

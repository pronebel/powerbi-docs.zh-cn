---
title: Power BI 嵌入式分析
description: Power BI 提供用于使用嵌入式分析将仪表板和报表嵌入到应用程序的 API。 了解有关如何使用 Power BI 嵌入式分析软件、嵌入式分析工具或嵌入式商业智能工具嵌入到 PaaS 环境和 SaaS 环境中的详细信息。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.custom: seodec18
ms.date: 02/05/2019
ms.openlocfilehash: ca159fb8cea26f4c707aabc99d9fa2c308a32e1a
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762435"
---
# <a name="embedded-analytics-with-power-bi"></a>Power BI 嵌入式分析

Azure (PaaS) 中的 Power BI 服务 (SaaS) 和 Power BI 嵌入式服务具有用于嵌入仪表板和报表的 API。 此功能意味着，在嵌入内容时，拥有一组功能以及对最新 Power BI 功能（如仪表板、网关和应用工作区）的访问权限。

可使用[嵌入安装程序工具](https://aka.ms/embedsetup)快速开始并下载示例应用程序。

选择最适合你的解决方案：

* 通过[为组织嵌入内容](embedding.md#embedding-for-your-organization)，可以扩展 Power BI 服务。 运行[为组织嵌入](https://aka.ms/embedsetup/UserOwnsData)解决方案。
* 通过[为客户嵌入内容](embedding.md#embedding-for-your-customers)，可为没有 Power BI 帐户的用户嵌入仪表板和报表。 运行[为客户嵌入](https://aka.ms/embedsetup/AppOwnsData)解决方案。

![PBIE 示例](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>使用 API

嵌入 Power BI 内容时，有两个主要方案。 为组织中的用户（拥有 Power BI 许可证）嵌入内容；为用户和客户嵌入内容且不要求他们拥有 Power BI 许可证。 两种方案都可使用 Power BI REST API。

对于没有 Power BI 许可证的客户和用户，可以使用同一 API 为组织或客户提供服务，将仪表板和报表嵌入自定义应用程序中。 客户会看到该应用程序管理的数据。 此外，对于组织中的 Power BI 用户，他们可以直接在 Power BI 中或者在嵌入式应用程序的上下文中使用附加的选项来查看他们的数据。 可以充分利用 JavaScript 和 REST API 的功能以满足你的嵌入需要。

若要查看有关嵌入工作原理的示例，请参阅 [JavaScript 嵌入示例](https://microsoft.github.io/PowerBI-JavaScript/demo/)。

## <a name="embedding-for-your-organization"></a>为组织嵌入内容

通过**为组织嵌入内容**，可以扩展 Power BI 服务。 为组织嵌入内容要求应用程序的用户在想要查看内容时登录 Power BI 服务。 组织中的用户登录后，只能访问他们拥有的，或者他们在 Power BI 服务中共享的仪表板和报表。

为组织嵌入内容的示例包括内部应用程序，如 [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/)、[Microsoft Teams 集成（必须拥有管理员权限）](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/)以及 [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard)。

若要为组织嵌入内容，请参阅以下内容：

* [将报表集成到应用](embed-sample-for-your-organization.md)

为 Power BI 用户嵌入内容时，通过 [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) 可使用编辑和保存等自助服务功能。

可浏览用于为组织嵌入的[嵌入安装程序工具](https://aka.ms/embedsetup/UserOwnsData)以开始并下载示例应用程序，它会逐步引导你为组织集成报表。

## <a name="embedding-for-your-customers"></a>为客户嵌入内容

通过为客户嵌入内容，可为没有 Power BI 帐户的用户嵌入仪表板和报表。 为客户嵌入内容也称为 Power BI Embedded。

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) 是 Microsoft Azure 提供的一项服务，可让独立软件供应商 (ISV) 和开发人员通过基于容量、按小时计量的模型，将视觉效果、报表和仪表板快速嵌入到应用程序中。

![为客户嵌入内容的嵌入流](media/embedding/powerbi-embed-flow.png)

Power BI Embedded 可让 ISV、其开发人员和客户受益。 例如，ISV 可以使用 Power BI Desktop 开始免费创建视觉对象。 ISV 可以通过尽量减少视觉分析开发工作而更快推向市场，并借由差异化数据体验在竞争中脱颖而出。 ISV 还可以选择对嵌入式分析创造的附加价值收取相关费用。

使用 Power BI Embedded，客户无需了解有关 Power BI 的任何信息。 可以使用两种不同的方法来创建嵌入式应用程序。 一种方法是使用 Power BI Pro 帐户。 另一种方法是使用服务主体。 

Power BI Pro 帐户充当应用程序的主帐户（将此主帐户视为代理帐户）。 借助 Power BI Pro 帐户，可以生成嵌入令牌，用于访问应用程序拥有和管理的 Power BI 服务中的仪表板和报表。

[服务主体](embed-service-principal.md)可以使用仅限应用的令牌将 Power BI 内容嵌入应用程序。 借助服务主体，可以生成嵌入令牌，用于访问应用程序拥有和管理的 Power BI 服务中的仪表板和报表。

使用 Power BI Embedded，开发人员可以更专注于构建其应用程序的核心竞争力，而不是花时间开发视觉对象和分析。 开发人员可以快速满足客户的报表和仪表板需求，并可以通过具有完整存档的 API 和 SDK 轻松嵌入。 通过在应用中启用易于导航的数据浏览，ISV 让客户能够使用任意设备在上下文中快速作出数据驱动型决策。

> [!IMPORTANT]
> 尽管嵌入操作依赖于 Power BI 服务，但在为客户嵌入内容时并不依赖于 Power BI Pro。 用户不需要注册 Power BI 来查看应用程序中嵌入的内容。

准备迁移到生产环境时，必须为应用工作区分配专用容量。 Microsoft Azure 中的 Power BI Embedded 提供用于应用程序的[专用容量](azure-pbie-create-capacity.md)。

有关如何嵌入的详细信息，请参阅[如何嵌入 Power BI 内容](embed-sample-for-customers.md)。

## <a name="next-steps"></a>后续步骤

现在可以尝试将 Power BI 内容嵌入应用程序，或尝试为客户嵌入 Power BI 内容。

> [!div class="nextstepaction"]
> [为组织嵌入内容](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Power BI Embedded 是什么？](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[为客户嵌入内容](embed-sample-for-customers.md)

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
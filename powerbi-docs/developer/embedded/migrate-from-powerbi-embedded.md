---
title: 如何将 Power BI 工作区集合内容迁移到 Power BI
description: 了解如何从 Power BI 工作区集合迁移到 Power BI Embedded，以及如何利用此改进功能在应用中嵌入内容。
author: KesemSharabi
ms.author: kesharab
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/30/2018
ms.openlocfilehash: 20546e0c9251f39ca49f6d713d5db48401937505
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114396"
---
# <a name="how-to-migrate-power-bi-workspace-collection-content-to-power-bi-embedded"></a>如何将 Power BI 工作区集合内容迁移到 Power BI Embedded

了解如何从 Power BI 工作区集合迁移到 Power BI Embedded，以及如何利用此改进功能在应用中嵌入内容。

Microsoft 最近[发布了 Power BI Embedded](https://powerbi.microsoft.com/blog/power-bi-embedded-capacity-based-skus-coming-to-azure/)，这是一个基于容量的新许可模型，可提高用户访问、共享和分发内容的灵活性。 此产品还提高了系统的可伸缩性和性能。

借助 Power BI Embedded，可在嵌入内容时拥有一个 API 外围和一组一致的功能，还可访问 Power BI 最新功能（例如仪表板、网关和工作区）。 再进一步的说，用户将能够使用 Power BI Desktop，然后能够借助 Power BI Embedded 实现部署。

当前的 Power BI 工作区集合还将提供一段时间。 签署了企业协议的客户将在现有协议的有效期内具有访问权限；自 Power BI Embedded 通用版发布起，通过 Direct 或 CSP 通道获取 Power BI 工作区集合的客户还将具有一年的访问权限。  本文将在以下方面提供指导：如何从 Power BI 工作区集合迁移到新的 Power BI Embedded 体验，以及应用程序中会有哪些更改。

> [!IMPORTANT]
> 虽然 Power BI Embedded 上的迁移具有依赖项，但在使用嵌入令牌时，Power BI 上没有为应用程序的用户提供依赖项  。 用户不需要注册 Power BI 来查看应用程序中嵌入的内容。 可为嵌入的非 Power BI 用户使用此嵌入方法。

![嵌入流](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

开始迁移到新的 Power BI Embedded 之前，可以快速完成一个演练，它可以帮助你使用[嵌入安装工具](https://aka.ms/embedsetup)来设置新的 Power BI Embedded 环境。

选择最适合你的解决方案：
* **为客户嵌入** - 适用于对[应用拥有数据](https://aka.ms/embedsetup/AppOwnsData)解决方案感兴趣的用户。 通过[为客户嵌入内容](embedding.md#embedding-for-your-customers)，可为没有 Power BI 帐户的用户嵌入仪表板和报表。 

* **为组织嵌入** - 适用于对[用户拥有数据](https://aka.ms/embedsetup/UserOwnsData)解决方案感兴趣的用户。 通过[为组织嵌入内容](embedding.md#embedding-for-your-organization)，可以扩展 Power BI 服务。

## <a name="prepare-for-the-migration"></a>迁移准备

需要完成一些准备工作才能从 Power BI 工作区集合迁移到 Power BI Embedded。 你将需要一个可用的租户，以及具有 Power BI Pro 许可证的用户。

1. 请确保你有权访问 Azure Active Directory (Azure AD) 租户。

    你需要确定要使用的租户设置。

   * 使用现有公司 Power BI 租户？
   * 为应用程序使用单独的租户？
   * 为每个客户使用单独的租户？

     如果决定为应用程序或每个客户创建一个新租户，请参阅[创建 Azure Active Directory 租户](create-an-azure-active-directory-tenant.md)或[如何获取 Azure Active Directory 租户](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant)。
2. 在此新租户中创建一个用户，作为应用程序“主”帐户。 该帐户需要注册 Power BI，并获得 Power BI Pro 许可证。

## <a name="accounts-within-azure-ad"></a>Azure AD 中的帐户

租户中必须有以下帐户。

> [!NOTE]
> 这些帐户需要具有 Power BI Pro 许可证才能使用工作区。

1. 租户管理员用户。

    建议此用户成为为实现嵌入而创建的所有工作区的成员。

2. 将创建内容的分析师帐户。

    应根据需要将这些用户分配到工作区。

3. 应用程序主用户帐户或嵌入帐户  。

    应用程序后端将存储此帐户的凭据，并将其用于获取与 Power BI REST API 一起使用的 Azure AD 身份验证令牌。 此帐户将用于生成应用程序的嵌入令牌。 此帐户还必须是为实现嵌入而创建的工作区的管理员。

> [!NOTE]
> 这只是组织中用于嵌入用途的常规用户帐户。

## <a name="app-registration-and-permissions"></a>应用注册和权限

你将需要在 Azure AD 中注册应用程序，并授予某些权限。

### <a name="register-an-application"></a>注册应用程序

必须向 Azure AD 注册应用，才能执行 REST API 调用。 除了转到 Power BI 应用注册页，这还包括转到 Azure 门户来应用其他配置。 有关详细信息，请参阅[注册 Azure AD 应用以便嵌入 Power BI 内容](register-app.md)。

应使用应用主  帐户来注册应用。

## <a name="create-workspaces-required"></a>创建工作区（必需）

如果应用程序服务多个客户，则可以利用工作区提供更好的隔离。 将在客户之间隔离仪表板和报表。 然后可以使用每个工作区的 Power BI 帐户以进一步隔离客户之间的应用程序体验。

> [!IMPORTANT]
> 不能使用个人工作区来利用嵌入到非 Power BI 用户功能。

你将需要具有 Pro 许可证的用户才能在 Power BI 中创建工作区。 默认情况下，创建工作区的 Power BI 用户将成为该工作区的管理员。

> [!NOTE]
> 应用主  帐户必须是工作区的管理员。

## <a name="content-migration"></a>内容迁移

在执行当前解决方案时，可同时将内容从工作区集合迁移到 Power BI Embedded，不需要停机处理。

可使用迁移工具，更轻松地将 Power BI 工作区集合中的内容复制到 Power BI Embedded  。 尤其是有大量内容时。 有关详细信息，请参阅 [Power BI Embedded 迁移工具](migrate-tool.md)。

内容迁移主要依赖两个 API。

1. 下载 PBIX - 此 API 可用于下载 2016 年 10 月之后上传到 Power BI 的 PBIX 文件。
2. 导入 PBIX - 此 API 可用于将任何 PBIX 上传到 Power BI。

有关相关的代码片段，请参阅[用于迁移 Power BI 工作区集合内容的代码片段](migrate-code-snippets.md)。

### <a name="report-types"></a>报表类型

有多种类型的报表，每种报表的迁移流程都稍有不同。

#### <a name="cached-dataset--report"></a>缓存数据集和报表

缓存数据集是指已导入数据的 PBIX 文件，而不是采用实时连接或 DirectQuery 连接。

流 

1. 从 PaaS 工作区调用下载 PBIX API。
2. 保存 PBIX。
3. 将导入 PBIX 调用到 SaaS 工作区。

#### <a name="directquery-dataset--report"></a>DirectQuery 数据集和报表

流 

1. 调用 GET https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources 并保存收到的连接字符串。
2. 从 PaaS 工作区调用下载 PBIX API。
3. 保存 PBIX。
4. 将导入 PBIX 调用到 SaaS 工作区。
5. 通过调用 POST 更新连接字符串 https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections
6. 通过调用 GET 获取 GW 和数据源标识符 https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources
7. 通过调用 PATCH 更新用户凭据 https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}

#### <a name="old-dataset--reports"></a>旧数据集和报表

这些数据集/报表是在 2016 年 10 月之前创建的。 下载 PBIX 不支持 2016 年 10 月之前上传的 PBIX

流 

1. 从开发环境中获取 PBIX（内部源代码管理）。
2. 将导入 PBIX 调用到 SaaS 工作区。

#### <a name="push-dataset--report"></a>推送数据集和报表

下载 PBIX 不支持推送 API  数据集。 无法将推送 API 数据集从 PaaS 移植到 SaaS。

流 

1. 使用数据集 JSON 调用“创建数据集” API，在 SaaS 工作区中创建数据集。
2. 为创建的数据集重新生成报表*。

通过尝试以下方法，可按某些方式将推送 API 报表从 PaaS 迁移到 SaaS。

1. 将一些虚 PBIX 上传到 PaaS 工作区。
2. 克隆推送 API 报表，并将其绑定到步骤 1 中的虚 PBIX。
3. 使用虚 PBIX 下载推送 API 报表。
4. 将虚 PBIX 上传到 SaaS 工作区。
5. 在 SaaS 工作区中创建推送数据集。
6. 将报表重新绑定到推送 API 数据集。

## <a name="create-and-upload-new-reports"></a>创建并上传新报表

除了迁移自 Power BI 工作区集合的内容外，还可使用 Power BI Desktop 创建报表和数据集，然后将这些报表发布到工作区。 发布报表的最终用户需要拥有 Power BI Pro 许可证才可发布到工作区。

## <a name="rebuild-your-application"></a>重新生成应用程序

1. 需要修改应用程序以使用 Power BI REST API 和 powerbi.com 中的报表位置。
2. 使用应用程序的*主*帐户重新生成 AuthN/AuthZ 身份验证。 可以使用[嵌入令牌](https://docs.microsoft.com/rest/api/power-bi/embedtoken)来允许此用户代表其他用户执行操作。
3. 将报表从 powerbi.com 嵌入到应用程序。

## <a name="map-your-users-to-a-power-bi-user"></a>将用户映射到 Power BI 用户

在应用程序中，将在应用程序中管理的用户映射到应用程序的*主* Power BI 凭据。 此 Power BI *主*帐户的凭据将存储在应用程序中，并且可用于创建嵌入令牌。

## <a name="what-to-do-when-you-are-ready-for-production"></a>做好生产准备时应执行的操作

准备好迁移到生产环境时，需要执行以下操作。

* 如果要使用单独的租户进行开发，则需要确保工作区以及仪表板和报表在生产环境中可用。 还需要确保在 Azure AD 中为生产租户创建了应用程序，并按照步骤 1 中所述分配了适当的应用权限。
* 购买符合需求的容量。 若要更好地了解所需容量的数量和类型，请参阅[Power BI Embedded 容量规划白皮书](https://aka.ms/pbiewhitepaper)。 可以在 Azure 中[购买容量](https://portal.azure.com/#create/Microsoft.PowerBIDedicated)。
* 编辑工作区，并在“高级”下将其分配给 Premium 容量。

    ![高级容量](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity02.png)

* 将更新后的应用程序部署到生产环境，并开始通过 Power BI Embedded 嵌入报表。

## <a name="after-migration"></a>迁移后

应在 Azure 中执行一些清理操作。

* 删除 Azure Power BI Embedded 工作区集合中部署的解决方案的所有工作区。
* 删除 Azure 中存在的任何工作区集合。

## <a name="next-steps"></a>后续步骤

[使用 Power BI 嵌入](embedding.md)  
[Power BI 工作区集合迁移工具](migrate-tool.md)  
[用于迁移 Power BI 工作区集合内容的代码片段](migrate-code-snippets.md)  
[如何嵌入 Power BI 仪表板、报表和磁贴](embed-sample-for-your-organization.md)  
[什么是 Power BI Premium？](../../service-premium-what-is.md)  
[JavaScript API Git 存储库](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git 存储库](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript 嵌入示例](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[工作区集合分析容量规划白皮书](https://aka.ms/pbiewhitepaper)  
[Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

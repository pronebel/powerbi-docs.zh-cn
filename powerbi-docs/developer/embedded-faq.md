---
title: 有关 Power BI Embedded 的常见问题
description: 浏览有关 Power BI Embedded 的常见问题和解答列表。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: abc45f3c32ee5db81f71295268db85bfce23aafd
ms.sourcegitcommit: 39bc75597b99bc9e8d0a444c38eb02452520e22b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58430429"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>有关 Power BI Embedded 的常见问题

* 如果你有其他问题，请[尝试询问 Power BI 社区](http://community.powerbi.com/)。
* 仍有问题？ 访问 [Power BI 支持页](https://powerbi.microsoft.com/support/)。

## <a name="general"></a>常规

### <a name="what-is-power-bi-embedded"></a>Power BI Embedded 是什么?

通过 [Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md)，应用程序开发人员将令人震撼的完全交互式报表嵌入到应用程序中，无需花费时间和费用生成自己的数据可视化和控件。

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Power BI Embedded 的目标受众是谁？

生产自己的应用程序的开发人员和软件公司，称为独立软件供应商 (ISV)。

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Power BI Embedded 与 Power BI 服务有什么不同？

Power BI Embedded 适用于以下 ISV 或开发人员：正在构建应用程序和希望将视觉对象嵌入到这些应用程序中，以帮助他们的客户做出决策，而无需从头开始构建分析解决方案。 [嵌入式分析](embedding.md)使业务用户能够访问业务数据并执行查询，以在应用程序中使用该数据获得洞察力。

Power BI 是“软件即服务”分析解决方案，为组织提供最关键业务数据的单一视图。

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Power BI Premium 与 Power BI Embedded 之间的区别是什么？

对于需要一个完整的 BI 解决方案的企业而言，Power BI Premium 可以根据它们的需要调整容量，从而提供组织、合作伙伴、客户和供应商的单一视图。 Power BI Premium 可以帮助组织做出决策。 Power BI Premium 是一款 SaaS 产品，能够让用户通过 Power BI 门户、移动应用和内部开发的应用使用内容。

Power BI Embedded 适用于正在构建应用程序和希望将视觉对象嵌入到这些应用程序中的 ISV 或开发人员。 由于 Power BI Embedded 适用于应用程序开发人员，应用程序的客户可以使用存储在 Power BI Embedded 容量上的内容（包括组织内外的任何人），因此 Power BI Embedded 能帮助你的客户做出决策。 Power BI Embedded 容量内容无法通过“一键式发布到 Web”或“一键式发布到 SharePoint”进行共享，并且不支持 SSRS 报表。

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Microsoft 建议客户购买 Power BI Premium 还是Power BI Embedded？

Microsoft 建议企业购买企业级自助服务云 BI 解决方案 Power BI Premium，建议 ISV 购买云助力的嵌入式分析组件 Power BI Embedded。 但是，客户可以购买哪种产品没有限制。

在某些情况下，ISV（通常是大型 ISV）可能希望使用 P SKU 在组织内获得预打包 Power BI 服务的额外好处，并嵌入它们的应用程序中。 如果有些企业只是对构建业务线应用程序和嵌入分析感兴趣，并且对使用预打包 Power BI 服务不感兴趣，它们可能会决定在 Azure 中使用 A SKU。

### <a name="how-many-embed-tokens-can-i-create"></a>我可以创建多少嵌入令牌？

使用 PRO 许可证的嵌入令牌仅用于开发测试，因此 Power BI 主帐户或[服务主体](embed-service-principal.md)可生成的嵌入令牌数量有限。 [购买容量](#technical)以便在生产环境中嵌入。 购买容量后，便能生成任意多个嵌入令牌。 转到[可用功能](https://docs.microsoft.com/rest/api/power-bi/availablefeatures)查看使用量值，该值以百分比表示当前嵌入使用量。

## <a name="technical"></a>技术

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Azure 中的 A SKU 与 Office 365 中的 EM SKU 之间有什么区别？

PowerBI.com 是一个企业解决方案，包括许多功能，例如社交协作、电子邮件订阅等其他功能。 在软件即服务产品中

Power BI Embedded 是一组 API，可供开发人员在平台即服务产品中创建嵌入式分析解决方案。 对于嵌入式分析方案，PowerBI.com 可帮助 ISV 和开发人员管理他们的嵌入式分析解决方案内容和租户级设置。

以下是可能用于各项的部分差异列表。

| 功能 | Power BI Embedded | Power BI Premium 容量 | Power BI Premium 容量 |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (A SKU) | (EM SKU) | (P SKU) |
| 从 Power BI 应用工作区嵌入项目 | Azure 容量 | Office 365 容量 | Office 365 容量 |
| 在嵌入应用程序中使用 Power BI 报表 | 是 | 是 | 是 |
| 在 SharePoint 中使用 Power BI 报表 | 否 | 是 | 是 |
| 在 Dynamics 中使用 Power BI 报表 | 否 | 是 | 是 |
| 在 Teams 中使用 Power BI 报表（不包括移动应用） | 否 | 是 | 是 |
| 在 Powerbi.com 和 Power BI 移动版中使用免费的 Power BI 许可证访问内容 | 否 | 否 | 是 |
| 使用 MS Office 应用中嵌入的免费 Power BI 许可证访问内容 | 否 | 是 | 是 |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI 现在提供三个用于嵌入的 SKU：A SKU、EM SKU 和 P SKU。 应该为我的方案购买哪一个？

|  |A SKU (Power BI Embedded)  |EM SKU (Power BI Premium)  |P SKU (Power BI Premium)  |
|---------|---------|---------|---------|
|购买  |Azure 门户 |Office |Office |
|用例 | 在自己的应用程序中嵌入内容 | <li> 在自己的应用程序中嵌入内容 <br><br><br> <li> 在 MS Office 应用程序中嵌入内容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams（不包括移动应用）](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> 在自己的应用程序中嵌入内容 <br><br><br> <li> 在 MS Office 应用程序中嵌入内容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams（不包括移动应用）](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> 通过 [Power BI 服务](https://powerbi.microsoft.com/)与 Power BI 用户共享内容  |
|账单 |每小时 |每月 |每月 |
|承诺  |无承诺 |每年  |每月/每年 |
|区别 |全弹性 - 可以在 Azure 门户中或通过 API 纵向/横向扩展、暂停/恢复资源  |可用于在 SharePoint Online 和 Microsoft Teams（不包括移动应用）中嵌入内容 |合并嵌入在应用程序中并在相同的容量中使用 Power BI 服务 |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>在 Azure 中创建 PBIE 容量的先决条件是什么？

* 登录到组织目录（不支持 MSA 帐户）。
* 必须有 Power BI 租户，即目录中至少有一个用户注册了 Power BI。 
* 需要在组织目录中有 Azure 订阅。

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>如何监视 Power BI Embedded 容量消耗？

* 使用 [Power BI 管理门户](../service-admin-portal.md#power-bi-embedded)。

* 在 Power BI 中下载[指标应用](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity)。

* 使用 [Azure 诊断日志记录](azure-pbie-diag-logs.md)。

### <a name="can-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>我的容量缩放能否自动调整以适应应用消耗量？

尽管现在没有自动缩放，但所有 API 均可随时缩放。

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>为什么创建/缩放/恢复容量会导致将容量置于挂起状态？

预配容量（缩放/恢复/创建）可能会失败。 预配调用的调用方应使用获取详细信息 API：[容量 - 获取详细信息](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails)来检查容量的预配状态。

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>能否只在特定区域创建 Power BI Embedded 容量？

使用[多地理位置（预览）](embedded-multi-geo.md)功能，可在不同于 Power BI 主租户位置的区域中购买 [Power BI Embedded 容量](azure-pbie-create-capacity.md)

### <a name="how-can-i-find-what-is-my-pbi-tenant-region"></a>如何找到我的 PBI 租户区域内容？

可使用 PBI 门户了解 PBI 租户区域的内容。

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > 关于 Power BI

![关于 Power BI](media/embedded-faq/about-01.png)
![租户区域](media/embedded-faq/tenant-location-01.png)

### <a name="what-is-supported-by-the-cloud-solution-provider-csp-channel"></a>云解决方案提供商 (CSP) 通道支持哪些内容？

* 可以为订阅类型为 CSP 的租户创建 PBIE
* 合作伙伴帐户可以登录到客户租户并为将客户租户用户指定为 Power BI 容量管理员的客户租户购买 PBIE

### <a name="why-do-i-get-an-unsupported-account-message"></a>为什么收到不受支持的帐户消息？

Power BI 要求使用组织帐户注册。 不支持使用 MSA（Microsoft 帐户）注册 Power BI。

### <a name="can-i-use-apis-to-create--manage-azure-capacities"></a>是否可以使用 API 创建和管理 Azure 的容量？

能，可使用 Powershell cmdlet 和 Azure 资源管理器 API 创建和管理 PBIE 资源。

* Rest API - https://docs.microsoft.com/rest/api/power-bi-embedded/
* Powershell cmdlet - https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>PBI Embedded 解决方案中的 PBI Embedded 专用容量角色是什么？

为了[将解决方案提升到生产](embed-sample-for-customers.md#move-to-production)，需要 Power BI 内容（在要分配给 Power BI Embedded (A SKU) 容量的应用程序中使用的应用工作区）。

### <a name="what-are-the-azure-regions-pbi-embedded-is-available"></a>什么是可使用 PBI Embedded 的 Azure 区域？

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) - 请参阅“产品可用性管理器”

可用性区域（16 个 - 与 Power BI 的区域相同）

* 美国（6 个）- 美国东部、美国东部 2，美国中北部、美国中南部、美国西部、美国西部 2
* 欧洲（2 个）- 北欧、西欧
* 亚太地区（2 个）- 东南亚、东亚
* 巴西（1 个）- 巴西南部
* 日本（1 个）- 日本东部
* 澳大利亚（1 个）- 澳大利亚东南部
* 印度（1 个）- 印度西部
* 加拿大（1 个）- 加拿大中部
* 英国（1 个）- 英国南部

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>什么是 Power BI Embedded 的身份验证模型？

Power BI Embedded 会继续使用 Azure AD 对主用户（指定的 Power BI Pro 许可用户）进行身份验证，或使用[服务主体](embed-service-principal.md)对 Power BI 中的应用程序进行身份验证。  

应用程序用户的身份验证和授权由 ISV 执行，ISV 可以为其应用程序实施身份验证。

如果你已有 Azure AD 租户，则可以使用现有的目录，也可以创建新的 Azure AD 租户以确保你的嵌入式应用程序内容安全。

若要获取 AAD 令牌，可以使用 [Azure Active Directory 身份验证库](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)之一。 有适用于多个平台的客户端库。

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>我的应用程序已使用 AAD 进行用户身份验证。 对“用户拥有数据”方案中的 Power BI 进行身份验证时，如何才能使用此标识？

它是标准 OAuth 代理流 (<https://docs.microsoft.com/azure/active-directory/develop/web-api>)。 需要将应用程序配置为需要 Power BI 服务权限（具有所需范围）。 获得应用的用户令牌后，只需使用用户访问令牌调用 ADAL API AcquireTokenAsync，并将 Power BI 资源 URL 指定为资源 ID。 请参阅以下代码片段，了解如何执行此操作：

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Power BI Embedded 与其他 Azure 服务有什么不同？

购买 Azure 中的 Power BI Embedded 之前，ISV/开发人员必须拥有 Power BI 帐户。 你的 Power BI Embedded 部署区决定 Power BI 帐户。 管理你在 Azure 中的 Power BI Embedded 资源，以便：

* 纵向/横向扩展
* 添加容量管理员
* 暂停/恢复服务

使用 PowerBI.com 将工作区分配/取消分配给 Power BI Embedded 容量。

### <a name="what-deploy-regions-are-supported"></a>支持什么部署区域？

澳大利亚东南部、巴西南部、加拿大中部、美国东部 2、印度西部、日本东部、美国中北部、欧洲北部、美国中南部、亚洲东南部、英国南部、欧洲西部、美国西部和美国西部 2。

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>可以嵌入哪种类型的内容包数据？

无法嵌入基于内容包数据集构建的仪表板和磁贴，但可嵌入基于内容包数据集构建的报表。

### <a name="what-is-the-difference-between-using-rls-vs-javascript-filters"></a>使用 RLS 与 JavaScript 筛选器有何区别？

对于何时使用 RLS 与 JavaScript 筛选器，我们通常会混淆，因为一种方法是用于控制具体用户可以看到的内容，另一种方法则是用于优化用户视图。

对于 RLS，ISV 开发人员在模型创建和嵌入令牌生成过程中控制数据筛选。 最终用户只能看到 ISV 允许其看到的内容。 在这种情况下，用户可以选择查看少于已筛选的内容，但无法通过规避 RLS 配置查看多于已允许的内容。

对于客户端筛选 (JavaScript)，ISV 可能会决定最终用户在初始视图中看到的内容，但 ISV 无法控制最终用户可能会应用于视图本身的更改。 虽然数据筛选可以在后端进行，但它是由 JavaScript 客户端代码触发，因此可以由最终用户更改，也就不能被视为安全。

有关详细信息，请参阅 [RLS 与 JavaScript 筛选器](embedded-row-level-security.md#using-rls-vs-javascript-filters)。

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>如何管理 Power BI 的服务主体的权限？

在使[服务主体](embed-service-principal.md)可用于 Power BI 后，应用程序的 AD 权限将不再有效。 然后，将通过 Power BI 管理门户管理应用程序权限。

服务主体继承其安全组中的所有 Power BI 租户设置的权限。 若要限制权限，请为服务主体创建专用的安全组并将其添加到相关已启用 Power BI 设置的“除特定安全组以外”列表。

当你以管理员身份将服务主体添加到新工作区时，这种情况很重要。 可以通过 [API](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) 或使用 Power BI 服务管理此任务。

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>何时使用应用程序 ID 与服务主体对象 ID？

传递应用程序 ID 进行身份验证时，[应用程序 ID](embed-sample-for-customers.md#application-id) 用于创建访问令牌。

若要引用服务主体用于操作或进行更改，请使用[服务主体对象 ID](embed-service-principal.md#how-to-get-the-service-principal-object-id) - 例如，以管理员身份将服务主体应用于工作区。

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>能否使用服务主体管理本地数据网关？

无法像使用主帐户一样，使用[服务主体](embed-service-principal.md)管理本地数据网关（数据网关）。

使用主帐户，可以安装数据网关，向网关添加用户，连接数据源和执行其他管理任务。

使用服务主体，可以使用 SQL Server Analysis Services (SSAS) 本地实时连接数据源配置[行级别安全性 (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview)。 使用服务主体与 Power BI Premium Embedded 集成时，可以通过这种方式管理用户及其对 SSAS 中数据的访问权限。

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>能否使用服务主体登录 Power BI 服务？

否，无法使用服务主体登录 Power BI。

此外，还无法以用户身份使用外部应用程序（SaaS 嵌入）中的内容，只有在生成嵌入令牌时才可以。

### <a name="what-are-the-best-practices-to-improve-performance"></a>提高性能的最佳做法有哪些？

[Power BI Embedded 性能](embedded-performance-best-practices.md)

## <a name="licensing"></a>许可

### <a name="how-do-i-purchase-power-bi-embedded"></a>如何购买 Power BI Embedded？

Power BI Embedded 是通过 Azure 提供的。

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>如果我已经购买了 Power BI Premium，现在我想要获得在 Azure 中使用 Power BI Embedded 的某些好处，会发生什么？

客户会继续支付任何现有的 Power BI Premium 购买费用，直到他们当前的协议期结束，然后可能会根据当时的需要切换 Power BI Premium 采购。

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>我是否仍需要购买 Power BI Premium 才能访问 Power BI Embedded？

否，Power BI Embedded 包括将解决方案部署并分发给客户所需的基于 Azure 的容量。

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Power BI Embedded 的采购承诺是什么？

客户可以按小时为单位更改使用情况。 Power BI Embedded 服务没有月承诺或年承诺。

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Power BI Embedded 的使用情况如何体现在我的账单上？

根据部署的节点类型，Power BI Embedded 按可预测的每小时费用收费。 只要资源处于活动状态，即使没有使用，也需要付费。 必须主动暂停资源，才能停止计费。

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>谁需要 Power BI Embedded 的 Power BI Pro 许可证，为什么？

任何需要使用 REST API 的开发人员都需要 Power BI Pro 许可证或[服务主体](embed-service-principal.md)。 需要将报表添加到 Power BI 工作区的任何分析人员都可以具有 Power BI Pro 许可证或使用服务主体。 需要管理 Power BI 租户和容量的任何租户管理员都需要具有 Power BI Pro 许可证。

由于 Power BI Embedded 允许使用 Power BI 门户来管理和验证嵌入式内容，因此需要使用 Power BI Pro 许可证对 PowerBI.com 内部的应用进行身份验证，这样才能访问相应存储库中的报表。

不过，若要在应用程序中[创建/编辑已嵌入报表](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View)，最终用户无需 Pro 许可证，因为该用户根本就不需要是 Power BI 用户。

### <a name="can-i-get-started-for-free"></a>开始我可以免费使用吗？

可以，你可以对 Power BI Embedded 使用你的 [Azure 信用额度](https://azure.microsoft.com/free/)

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>可以在 Azure 中获得 Power BI Embedded 的试用体验吗？

因为 Power BI Embedded 属于 Azure，所以可利用[注册 Azure 时获得的 200 美元额度](https://azure.microsoft.com/free/)使用此服务。

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Power BI Embedded 是否适用于国家云（美国政府版、德国版、中国版）？

Power BI Embedded 也适用于[国家云](embed-sample-for-customers-national-clouds.md)。

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded 是否适合非营利组织和教育机构？

非营利组织和教育机构可以购买 Azure。 Azure 对于这些类型的客户没有特殊定价。

## <a name="power-bi-workspace-collection"></a>Power BI 工作区集合

### <a name="what-is-power-bi-workspace-collection"></a>什么是 Power BI 工作区集合？

“Power BI 工作区集合”（Power BI Embedded 版本 1）是一种基于“Power BI 工作区集合”Azure 资源的解决方案。 此解决方案允许使用“Power BI 工作区集合”解决方案下的 Power BI 内容、专用的 API 和用于向 Power BI 验证应用程序的工作区集合密钥，为客户创建 Power BI Embedded 应用程序。

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>如何从 Power BI 工作区集合迁移到 Power BI Embedded？

1. 可以使用迁移工具将 Power BI 工作区集合内容克隆到 Power BI - https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration。

2. 从使用 Power BI 内容的 Power BI Embedded 应用程序 POC 入手。

3. 为生产做好准备后，购买 Power BI Embedded 专用容量，并将你的 Power BI 内容（工作区）分配给该容量。

    > [!Note]
    > 当使用 Power BI Embedded 解决方案并行生成时，可以继续使用 Power BI 工作区集合。 准备就绪后，可以让客户迁移到新的 Power BI Embedded 解决方案，停用 Power BI 工作区集合解决方案。

有关详细信息，请参考[如何将 Power BI 工作区集合内容迁移到 Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded)

### <a name="is-power-bi-workspace-collection-on-a-path-to-be-deprecated"></a>Power BI 工作区集合是否将要被弃用？

是的，但是已在使用 Power BI 工作区集合解决方案的客户可以继续使用它，直到它被弃用。 客户还可以创建新的工作区集合，以及任何仍使用 Power BI 工作区集合解决方案的 Power BI Embedded 应用程序。

但是，这也意味着新功能不会添加到任何 Power BI 工作区集合解决方案，建议客户规划迁移到新的 Power BI Embedded 解决方案。

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>何时停止 Power BI 工作区集合支持？

已在使用 Power BI 工作区集合解决方案的客户可以继续使用它，直至 2018 年 6 月底或直至其支持协议结束。

### <a name="in-what-regions-can-pbi-workspace-collection-be-created"></a>可以在哪些区域创建 PBI 工作区集合？

可用区域有：澳大利亚东南部、巴西南部、加拿大中部、美国东部 2、日本东部、美国中北部、欧洲北部、美国中南部、亚洲东南部、英国南部、欧洲西部、印度西部和美国西部。

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>为什么应当从 PBI 工作区集合迁移到 Power BI Embedded？

Power BI Embedded 解决方案中引入了一些 Power BI 工作区集合无法实现的新特性和新功能。

一些功能为：

* 所有 PBI 数据源都受支持，而 Power BI 工作区集合仅支持两个数据源。 
* Power BI Embedded 解决方案仅支持诸如常见问题、刷新、书签、嵌入仪表板和磁贴以及自定义菜单等新功能。
* 容量计费模型。

## <a name="embedding-setup-tool"></a>嵌入安装程序工具

### <a name="what-is-the-embedding-setup-tool"></a>什么是嵌入安装程序工具？

通过[工具](https://aka.ms/embedsetup)，可快速开始并下载示例应用程序，以便开始使用 Power BI 进行嵌入。

### <a name="which-solution-should-i-choose"></a>应选择哪种解决方案？

* 通过[为客户嵌入内容](embedding.md#embedding-for-your-customers)，可为没有 Power BI 帐户的用户嵌入仪表板和报表。 运行[为客户嵌入](https://aka.ms/embedsetup/AppOwnsData)解决方案。
* 通过[为组织嵌入内容](embedding.md#embedding-for-your-organization)，可以扩展 Power BI 服务。 运行[为组织嵌入](https://aka.ms/embedsetup/UserOwnsData)解决方案。

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>我已下载示例应用，应选择哪种解决方案？

若要采用“为客户嵌入”体验，请保存并解压缩 PowerBI-Developer-Samples.zip 文件。 然后打开 PowerBI-Developer-Samples-master\App Owns Data 文件夹并运行 PowerBIEmbedded_AppOwnsData.sln 文件。

若要采用“为组织嵌入”体验，请保存并解压缩 PowerBI-Developer-Samples.zip 文件。 然后打开 PowerBI-Developer-Samples-master\App Owns Data\integrate-report-web-app 文件夹并运行 pbi-saas-embed-report.sln 文件。

### <a name="how-can-i-edit-my-registered-application"></a>如何编辑已注册的应用程序？

若要了解如何编辑已注册 Azure AD 的应用程序，请参阅[快速入门：在 Azure Active Directory 中更新应用程序](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app)。

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>如何编辑我的 Power BI 用户配置文件或数据？

可以在[这里](https://docs.microsoft.com/power-bi/service-basic-concepts)了解如何编辑 Power BI 数据。

有关详细信息，请参阅[嵌入应用程序疑难解答](embedded-troubleshoot.md)。

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)
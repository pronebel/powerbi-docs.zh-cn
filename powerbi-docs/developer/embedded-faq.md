---
title: 有关 Power BI Embedded 的常见问题
description: 浏览有关 Power BI Embedded 的常见问题和解答列表。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 12/20/2018
ms.openlocfilehash: 3971651caf9be7e754f4232ffec8b4e4dbfdfe6d
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008410"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>有关 Power BI Embedded 的常见问题

* 如果你有其他问题，请[尝试询问 Power BI 社区](http://community.powerbi.com/)。
* 仍有问题？ 访问 [Power BI 支持页](https://powerbi.microsoft.com/support/)。

## <a name="general"></a>常规

### <a name="what-is-power-bi-embedded"></a>Power BI Embedded 是什么?

通过 Microsoft Power BI Embedded (PBIE)，应用程序开发人员将令人震撼的完全交互式报表嵌入到应用程序中，无需花费时间和费用重新生成自己的数据可视化和控件。

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Power BI Embedded 的目标受众是谁？

生产自己的应用程序的开发人员和软件公司，称为独立软件供应商 (ISV)。

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Power BI Embedded 与 Power BI 服务有什么不同？

Power BI Embedded 适用于以下 ISV 或开发人员：正在构建应用程序和希望将视觉对象嵌入到这些应用程序中，以帮助他们的客户做出决策，而无需从头开始构建分析解决方案。 嵌入式分析使业务用户能够访问业务数据并执行查询，以在应用程序中使用这些数据获得洞察力。

Power BI 是“软件即服务”分析解决方案，为组织提供最关键业务数据的单一视图。

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Power BI Premium 与 Power BI Embedded 之间的区别是什么？

对于需要一个完整的 BI 解决方案的企业而言，Power BI Premium 可以根据它们的需要调整容量，从而提供组织、合作伙伴、客户和供应商的单一视图。 Power BI Premium 可以帮助组织做出决策。 Power BI Premium 是一款 SaaS 产品，能够让用户通过 Power BI 门户、移动应用和内部开发的应用使用内容。

Power BI Embedded 适用于正在构建应用程序和希望将视觉对象嵌入到这些应用程序中的 ISV 或开发人员。 由于 Power BI Embedded 适用于应用程序开发人员，应用程序的客户可以使用存储在 Power BI Embedded 容量上的内容（包括组织内外的任何人），因此 Power BI Embedded 能帮助你的客户做出决策。 Power BI Embedded 容量内容无法通过“一键式发布到 Web”或“一键式发布到 SharePoint”进行共享，并且不支持 SSRS 报表。

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Microsoft 建议客户购买 Power BI Premium 还是 Power BI Embedded？

Microsoft 建议企业购买企业级自助服务云 BI 解决方案 Power BI Premium，建议 ISV 购买云助力的嵌入式分析组件 Power BI Embedded。 但是，客户可以购买哪种产品没有限制。

在某些情况下，ISV（通常是大型 ISV）可能希望使用 P SKU 在组织内获得预打包 Power BI 服务的额外好处，并嵌入它们的应用程序中。 一些企业可能会决定使用  Azure 中的 A SKU，前提是它们只对生成业务线应用程序并向其中嵌入分析感兴趣，而对使用预打包 Power BI 服务则不感兴趣。

### <a name="how-many-embed-tokens-can-i-create"></a>我可以创建多少嵌入令牌？

使用 PRO 许可证的嵌入令牌仅用于开发测试，因此 Power BI 主帐户生成的嵌入令牌数量有限。 必须[购买容量](#technical)，才能在生产环境中嵌入。 购买容量后，便能生成任意多个嵌入令牌。 转到[可用功能](https://docs.microsoft.com/rest/api/power-bi/availablefeatures)查看使用量值，该值以百分比表示当前嵌入使用量。

## <a name="technical"></a>技术

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Azure 中的 A SKU 与 Office 365 中的 EM SKU 之间有什么区别？

PowerBI.com 是一个企业解决方案，包括软件即服务套餐中的许多功能，例如社交协作、电子邮件订阅等

Power BI Embedded 是一组 API，可供开发人员在平台即服务产品中创建嵌入式分析解决方案。 对于嵌入式分析方案，应使用 PowerBI.com 帮助 ISV 和开发人员管理他们的嵌入式分析解决方案内容和租户级设置。

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
|用例 | 在自己的应用程序中嵌入内容 | <li> 在自己的应用程序中嵌入内容 <br><br></br> <li> 在 MS Office 应用程序中嵌入内容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams（不包括移动应用）](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> 在自己的应用程序中嵌入内容 <br><br></br> <li> 在 MS Office 应用程序中嵌入内容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams（不包括移动应用）](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br></br> <li> 通过 [Power BI 服务](https://powerbi.microsoft.com/en-us/)与 Power BI 用户共享内容  |
|账单 |每小时 |每月 |每月 |
|承诺  |无承诺 |每年  |每月/每年 |
|区别 |全弹性 - 可以在 Azure 门户中或通过 API 纵向/横向扩展、暂停/恢复资源  |可用于在 SharePoint Online 和 Microsoft Teams（不包括移动应用）中嵌入内容 |合并嵌入在应用程序中并在相同的容量中使用 Power BI 服务 |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>在 Azure 中创建 PBIE 容量的先决条件是什么？

* 需要登录到组织目录（不支持 MSA 帐户）。
* 必须有 Power BI 租户，即目录中至少有一个用户注册了 Power BI。 
* 需要在组织目录中有 Azure 订阅。

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>如何监视 Power BI Embedded 容量消耗？

* 使用 [Power BI 管理门户](../service-admin-portal.md#power-bi-embedded)。

* 在 Power BI 中下载[指标应用](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity)。

* 使用 [Azure 诊断日志记录](azure-pbie-diag-logs.md)。

### <a name="will-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>我的容量缩放是否会自动调整以适应应用消耗量？

虽然现在没有自动缩放，但是所有 API 都可以在任何时候缩放。

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>为什么创建/缩放/恢复容量会导致将容量置于挂起状态？

预配容量（缩放/恢复/创建）可能会失败。 预配调用的调用方应使用获取详细信息 API：[容量 - 获取详细信息](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails)来检查容量的预配状态。

### <a name="why-can-i-only-create-pbie-in-a-specific-region"></a>为什么只能在特定区域创建 PBIE？

你只能为 PBI 租户区域创建 PBIE 容量。

### <a name="how-can-i-find-what-is-my-pbi-tenant-region"></a>如何找到我的 PBI 租户区域内容？

可使用 PBI 门户了解 PBI 租户区域的内容。

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > 关于 Power BI

![关于 Power BI](media/embedded-faq/about-01.png)
![租户区域](media/embedded-faq/tenant-location-01.png)

### <a name="what-is-supported-with-the-cloud-solution-provider-csp-channel"></a>云解决方案提供商 (CSP) 通道支持哪些内容？

* 可以为订阅类型为 CSP 的租户创建 PBIE
* 合作伙伴帐户可以登录到客户租户并为将客户租户用户指定为 Power BI 容量管理员的客户租户购买 PBIE

### <a name="why-do-i-get-an-unsupported-account-message"></a>为什么收到不受支持的帐户消息？

Power BI 要求使用组织帐户注册。 不支持使用 MSA（Microsoft 帐户）注册 Power BI。

### <a name="can-i-use-apis-to-create--manage-azure-capacities"></a>是否可以使用 API 创建和管理 Azure 的容量？

能，可使用 Powershell cmdlet 和 Azure 资源管理器 API 创建和管理 PBIE 资源。

* Rest API - https://docs.microsoft.com/rest/api/power-bi-embedded/
* Powershell cmdlet - https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>PBI Embedded 解决方案中的 PBI Embedded 专用容量角色是什么？

为了[将解决方案提升到生产](https://docs.microsoft.com/power-bi/developer/embedding-content#step-3-promote-your-solution-to-production)，需要 Power BI 内容（在要分配给 Power BI Embedded (A SKU) 容量的应用程序中使用的应用工作区）。

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

Power BI Embedded 将继续使用 Azure AD 对主用户（指定的 Power BI Pro 许可用户）进行身份验证，进而对 Power BI 中的应用程序进行身份验证。

应用程序用户的身份验证和授权将由 ISV 执行，ISV 可以为其应用程序实施自己的身份验证。

如果你已有 Azure AD 租户，则可以使用现有的目录，也可以创建新的 Azure AD 租户以确保你的嵌入式应用程序内容安全。

若要获取 AAD 令牌，可以使用 Azure Active Directory 身份验证库 (https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) 之一。 有适用于多个平台的客户端库。

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-an-user-owns-data-scenario"></a>我的应用程序已使用 AAD 进行用户身份验证。 在“用户拥有数据”方案中对 Power BI 进行身份验证时，如何使用此标识？

它是标准 OAuth 代理流 (https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#web-application-to-web-api) 需要配置应用程序，使其具有访问 Power BI 服务的权限（在要求的范围内），用户获得应用令牌后，只需使用用户访问令牌调用 ADAL API AcquireTokenAsync 并将 PowerBI 资源 URL 指定为资源 ID 即可，请参阅以下代码片段了解操作方法：

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Power BI Embedded 与其他 Azure 服务有什么不同？

购买 Azure 中的 Power BI Embedded 之前，ISV/开发人员必须拥有 Power BI 帐户。 你的 Power BI Embedded 部署区域由你的 Power BI 帐户决定。 管理你在 Azure 中的 Power BI Embedded 资源，以便：

* 纵向/横向扩展
* 添加容量管理员
* 暂停/恢复服务

使用 PowerBI.com 将工作区分配/取消分配给 Power BI Embedded 容量。

### <a name="what-deploy-regions-are-supported"></a>支持什么部署区域？

澳大利亚东南部、巴西南部、加拿大中部、美国东部 2、印度西部、日本东部、美国中北部、欧洲北部、美国中南部、亚洲东南部、英国南部、欧洲西部、美国西部和美国西部 2。

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>可以嵌入哪种类型的内容包数据？

无法嵌入基于内容包数据集创建的仪表板和磁贴，但可嵌入基于内容包数据集创建的报表。

### <a name="what-is-the-difference-between-using-rls-vs-javascript-filters"></a>使用 RLS 与 JavaScript 筛选器有何区别？

对于何时使用 RLS 与 JavaScript 筛选器，我们通常会混淆，因为一种方法是用于控制具体用户可以看到的内容，另一种方法则是用于优化用户视图。

对于 RLS，ISV 开发人员在模型创建和嵌入令牌生成过程中控制数据筛选。 最终用户只能看到 ISV 允许其看到的内容。 在这种情况下，用户可以选择查看少于已筛选的内容，但无法通过规避 RLS 配置查看多于已允许的内容。

对于客户端筛选 (JavaScript)，ISV 可能会决定最终用户在初始视图中看到的内容，但 ISV 无法控制最终用户可能会应用于视图本身的更改。 虽然数据筛选可以在后端进行，但它是由 JavaScript 客户端代码触发，因此可以由最终用户更改，也就不能被视为安全。

有关详细信息，请参阅 [RLS 与 JavaScript 筛选器](embedded-row-level-security.md#using-rls-vs-javascript-filters)。

## <a name="licensing"></a>许可

### <a name="how-do-i-purchase-power-bi-embedded"></a>如何购买 Power BI Embedded？

Power BI Embedded 是通过 Azure 提供的。

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>如果我已经购买了 Power BI Premium，现在我想要获得在 Azure 中使用 Power BI Embedded 的某些好处，会发生什么？

客户将继续支付任何现有的 Power BI Premium 购买费用，直到他们当前的协议期结束，然后可能会根据当时的需要切换 Power BI Premium 采购。

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>我是否仍需要购买 Power BI Premium 才能访问 Power BI Embedded？

否，Power BI Embedded 包括将解决方案部署并分发给客户所需的基于 Azure 的容量。

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Power BI Embedded 的采购承诺是什么？

客户可以按小时为单位更改使用情况。 Power BI Embedded 服务没有月承诺或年承诺。

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Power BI Embedded 的使用情况如何体现在我的账单上？

根据部署的节点类型，Power BI Embedded 按可预测的每小时费用收费。 只要资源处于活动状态，即使没有使用，也需要付费。 必须主动暂停资源，才能停止计费。

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>谁需要 Power BI Embedded 的 Power BI Pro 许可证，为什么？

任何需要将报表添加到 Power BI 工作区的分析师、任何需要使用 REST API 的开发人员、任何需要管理 Power BI 租户和容量的租户管理员都需要 Power BI Pro 许可证。

由于 Power BI Embedded 允许使用 Power BI 门户来管理和验证嵌入式内容，因此需要使用 Power BI Pro 许可证对 PowerBI.com 内部的应用进行身份验证，这样才能访问相应存储库中的报表。

不过，若要在自己的应用程序中[创建/编辑已嵌入报表](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View)，最终用户无需 Pro 许可证，因为其根本就不需要是 Power BI 用户。

### <a name="can-i-get-started-for-free"></a>开始我可以免费使用吗？

可以，你可以对 Power BI Embedded 使用你的 [Azure 信用额度](https://azure.microsoft.com/free/)

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>可以在 Azure 中获得 Power BI Embedded 的试用体验吗？

因为 Power BI Embedded 属于 Azure，所以可利用[注册 Azure 时获得的 200 美元额度](https://azure.microsoft.com/free/)使用此服务。

### <a name="is-power-bi-embedded-available-for-sovereign-clouds-us-government-germany-china"></a>Power BI Embedded 是否适用于主权云（美国政府版、德国版、中国版）？

Power BI Embedded 可用于某些[主权云](embed-sample-for-customers-sovereign-clouds.md)。 它仍不适用于中国版云。

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

### <a name="when-will-power-bi-workspace-collection-support-be-discontinued"></a>何时停止 Power BI 工作区集合支持？

已在使用 Power BI 工作区集合解决方案的客户可以继续使用它，直至 2018 年 6 月底或直至其支持协议结束。

### <a name="in-what-regions-can-pbi-workspace-collection-be-created"></a>可以在哪些区域创建 PBI 工作区集合？

可用区域有：澳大利亚东南部、巴西南部、加拿大中部、美国东部 2、日本东部、美国中北部、欧洲北部、美国中南部、亚洲东南部、英国南部、欧洲西部、印度西部和美国西部。

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>为什么应当从 PBI 工作区集合迁移到 Power BI Embedded？

Power BI Embedded 解决方案中引入了 Power BI 工作区集合无法实现的新特性和新功能。

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

可以在[这里](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application)了解如何编辑已注册的 AAD 应用程序。

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>如何编辑我的 Power BI 用户配置文件或数据？

可以在[这里](https://docs.microsoft.com/power-bi/service-basic-concepts)了解如何编辑 Power BI 数据。

有关详细信息，请参阅[嵌入应用程序疑难解答](embedded-troubleshoot.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)

### <a name="what-are-the-best-practices-to-improve-performance"></a>提高性能的最佳做法有哪些？

[Power BI Embedded 性能](embedded-performance-best-practices.md)
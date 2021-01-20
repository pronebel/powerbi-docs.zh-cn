---
title: 适用于 Power BI 的 Azure 安全基线
description: Power BI 安全基线为实现 Azure 安全基准中指定的安全建议提供过程指导和资源。
author: mbaldwin
ms.author: margoc
ms.service: powerbi
ms.subservice: pbi-security
ms.topic: conceptual
ms.date: 11/20/2020
ms.custom: subject-security-benchmark
ms.openlocfilehash: a76c7f9d205fe47322768a514a1e5d89a36a2306
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565760"
---
# <a name="azure-security-baseline-for-power-bi"></a>适用于 Power BI 的 Azure 安全基线

此安全基线将 [Azure 安全基准版本 2.0](/azure/security/benchmarks/overview) 中的指南应用到 Power BI。 Azure 安全基准提供有关如何在 Azure 上保护云解决方案的建议。 内容按 Azure 安全基准定义的安全控制和适用于 Power BI 的相关指导进行分组。 已排除不适用于 Power BI 的控制。

若要了解 Power BI 如何完全映射到 Azure 安全基准，请参阅[完整 Power BI 安全基线映射文件](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines)。

## <a name="network-security"></a>网络安全

[有关详细信息，请参阅 *Azure 安全基线：* 网络安全性](/azure/security/benchmarks/security-controls-v2-network-security)。

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3：建立对 Azure 服务的专用网络访问

**指导**：Power BI 支持将 Power BI 租户连接到专用链接终结点并禁用公共 Internet 访问。

- [用于访问 Power BI 的专用链接](../admin/service-security-private-links.md)

**Azure 安全中心监视**：不适用

**责任**：共享

## <a name="identity-management"></a>标识管理

有关详细信息，请参阅 [Azure 安全基准：标识管理](/azure/security/benchmarks/security-controls-v2-identity-management)。

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1：将 Azure Active Directory 标准化为中央标识和身份验证系统

**指导**：Power BI 与 Azure Active Directory (Azure AD) 集成，后者是 Azure 的默认标识和访问管理服务。 你应在 Azure AD 上实现标准化，以治理组织的标识和访问管理。

在组织的云安全做法中，应优先处理 Azure AD 保护事宜。 Azure AD 提供标识安全分数，帮助你评估与 Microsoft 的最佳做法建议相关的标识安全状况。 使用评分来估计你的配置与最佳做法建议的匹配程度，并改善你的安全状况。

注意:Azure AD 支持外部标识，允许没有 Microsoft 帐户的用户使用其外部标识登录到其应用程序和资源。

- [Azure Active Directory 中的租赁](/azure/active-directory/develop/single-and-multi-tenant-apps)

- [如何创建和配置 Azure AD 实例](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [使用应用程序的外部标识提供者](/azure/active-directory/b2b/identity-providers)

- [Azure Active Directory 中的标识安全分数是什么](/azure/active-directory/fundamentals/identity-secure-score)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2：安全且自动地管理应用程序标识

**指导**：Power BI 和 Power BI Embedded 支持使用服务主体。 存储用于加密或访问 Key Vault 中 Power BI 的任何服务主体凭据，将适当的访问策略分配给保管库，并定期检查访问权限。

使用服务主体自动完成 Premium 工作区和数据集任务 https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3：使用 Azure AD 单一登录 (SSO) 进行应用程序访问

**指导**：Power BI 使用 Azure Active Directory 提供对 Azure 资源、云应用程序和本地应用程序的标识和访问管理。 此内容包括企业标识（例如员工）以及外部标识（如合作伙伴和供应商）。 这样，单一登录 (SSO) 便可以管理和保护对本地和云中的组织数据和资源的访问。 将所有用户、应用程序和设备连接到 Azure AD，实现无缝的安全访问和更好的可见性和控制。

- [了解 Azure AD 的应用程序 SSO](/azure/active-directory/manage-apps/what-is-single-sign-on)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4：对所有基于 Azure Active Directory 的访问使用强身份验证控制

**指导**：Power BI 可与 Azure AD 集成，后者通过多重身份验证 (MFA) 和强无密码方法支持强身份验证控制。
- 多重身份验证 - 启用 Azure AD MFA，并遵循 Azure 安全中心标识和访问管理建议，以获得 MFA 设置中的一些最佳做法。 可基于登录条件和风险因素，对所有用户、精选用户或在每用户级别强制执行 MFA。
- 无密码身份验证 - 有三个无密码身份验证选项可用：Windows Hello 企业版、Microsoft Authenticator 应用和本地身份验证方法（如智能卡）。

对于管理员和特权用户，请确保使用最高级别的强身份验证，然后向其他用户推出适当的强身份验证策略。

注意:只能对在 Azure AD 中启用的用户帐户强制执行 MFA。 Power BI 服务主体不支持使用 MFA。

- [如何在 Azure 中启用 MFA](/azure/active-directory/authentication/howto-mfa-getstarted)

- [Azure Active Directory 的无密码身份验证选项简介](/azure/active-directory/authentication/concept-authentication-passwordless)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5：监视并提醒帐户异常

**指导**：在 Microsoft Cloud App Security 中定义可以独立确定范围的异常情况检测策略，以便仅将其应用于要包括的用户和组。 这些异常情况检测策略可帮助检测和监视与用户访问和使用 Power BI 相关的行为异常。

- [在 Power BI 中使用 Microsoft Cloud App Security 控制](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6：基于条件限制 Azure 资源访问

**指导**：Power BI 支持 Azure AD 条件访问，以便基于用户定义的条件进行更精细的访问控制，例如，特定 IP 范围中的用户登录将需要使用 MFA 进行登录。 精细身份验证会话管理策略还可用于不同的用例。

- [Azure 条件访问概述](/azure/active-directory/conditional-access/overview)

- [常见的条件访问策略](/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [使用条件访问配置身份验证会话管理](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [在 Power BI 中使用 Microsoft Cloud App Security 控制](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7：消除意外的凭据透露

**指导**：对于 Power BI Embedded 应用程序，建议实现凭据扫描程序来识别代码中的凭据。 凭据扫描程序还会建议将发现的凭据转移到更安全的位置，例如 Azure Key Vault。

存储用于加密或访问 Key Vault 中 Power BI 的任何加密密钥或服务主体凭据，将适当的访问策略分配给保管库，并定期检查访问权限。
 
对于 GitHub，你可以使用原生的机密扫描功能来识别代码中的凭据或其他形式的机密。

- [对 Power BI 创建自己的加密密钥](../admin/service-encryption-byok.md)

 
如何设置凭据
- [扫描仪](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [GitHub 机密扫描](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Azure 安全中心监视**：不适用

**责任**：共享

## <a name="privileged-access"></a>特权访问

有关详细信息，请参阅 [Azure 安全基准：特权访问](/azure/security/benchmarks/security-controls-v2-privileged-access)。

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1：保护和限制具有较高权限的用户

**指导**：为了降低风险并遵循最小特权原则，建议将 Power BI 管理员的成员限制在少数用户。 具有这些特权权限的用户可能潜在地访问和修改组织的所有管理功能。 通过 Microsoft 365 或 Azure Active Directory，全局管理员在 Power BI 服务中也隐式拥有管理员权限。

Power BI 具有以下高特权帐户：
- 全局管理员
- 计费管理员
- 许可证管理员
- 用户管理员
- Power BI 管理员
- Power BI Premium 容量管理员
- Power BI Embedded 容量管理员

Power BI 支持 Azure AD 中的会话策略，以启用条件访问策略，并通过 Cloud App Security 服务路由在 Power BI 中使用的会话。

使用 M365 特权访问管理为 Power BI 管理员帐户启用实时 (JIT) 特权访问。

- [与 Power BI 相关的管理员角色](../admin/service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)

- [M365 特权访问管理](/microsoft-365/compliance/privileged-access-management-overview?amp;preserve-view=true&view=o365-worldwide)

- [Power BI 中的 Cloud App Security 控制](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2：限制对关键业务型系统的管理访问权限

**指导**：限制具有对 Power BI 提升访问权限的高特权帐户或角色的数量。

可使用[此处](/microsoft-365/compliance/privileged-access-management-overview?amp;preserve-view=true&view=o365-worldwide)的 M365 特权访问管理指南启用实时 (JIT) 特权访问。

可在[此处](https://aka.ms/PBIEnterpriseDeploymentWP)的 Power BI Enterprise 部署文档的第 183 页找到其他详细信息。

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3：定期审查和协调用户访问权限

**指导**：作为 Power BI 服务管理员，你可以使用基于 Power BI 活动日志的自定义报表来分析租户级别的所有 Power BI 资源的使用情况。 可以使用 REST API 或 PowerShell cmdlet 来下载活动。 还可以按日期范围、用户和活动类型筛选活动数据。

必须满足以下要求才能访问 Power BI 活动日志：
- 必须是全局管理员或 Power BI 服务管理员。
- 你已在本地安装了 [Power BI 管理 cmdlet](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) 或在 Azure Cloud Shell 中使用 Power BI 管理 cmdlet。

满足这些要求后，可以按照以下指导来跟踪 Power BI 中的用户活动：

- [跟踪 Power BI 中的用户活动](../admin/service-admin-auditing.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4：在 Azure AD 中设置紧急访问

**指导**：Power BI 与 Azure Active Directory 和 M365 集成，以管理其资源。 若要防止被意外锁定在 M365 租户或 Azure AD 组织之外，请设置一个紧急访问帐户，以便在无法使用正常管理帐户时进行访问。 紧急访问帐户通常拥有较高的权限，因此请不要将其分配给特定的个人。 紧急访问帐户只能用于“不受限”紧急情况，即不能使用正常管理帐户的情况。

应确保妥善保管紧急访问帐户的凭据（例如密码、证书或智能卡），仅将其告诉只能在紧急情况下有权使用它们的个人。

- [在 Azure AD 中管理紧急访问帐户](/azure/active-directory/users-groups-roles/directory-emergency-access)

- [保护你的 M365 帐户](/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6：使用特权访问工作站

**指导**：安全的独立工作站对于确保敏感角色（如管理员、开发人员和关键服务操作员）的安全至关重要。 使用高度安全的用户工作站和/或 Azure Bastion 来执行与管理 Power BI 相关的管理任务。 使用 Azure Active Directory、Microsoft Defender 高级威胁防护 (ATP) 和/或 Microsoft Intune 部署安全的托管用户工作站，用于执行管理任务。 可通过集中管理安全的工作站来强制实施安全配置，包括强身份验证、软件和硬件基线、受限的逻辑和网络访问。

了解特权访问
- [工作站](/azure/active-directory/devices/concept-azure-managed-workstation)

- [部署特权访问工作站](/azure/active-directory/devices/howto-azure-managed-workstation)

**Azure 安全中心监视**：不适用

**责任**：客户

## <a name="data-protection"></a>数据保护

[有关详细信息，请参阅 *Azure 安全基线：* 数据保护](/azure/security/benchmarks/security-controls-v2-data-protection)。

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1：对敏感数据进行发现、分类和标记

**指导**：使用报表、仪表板、数据集和数据流的 Microsoft 信息保护敏感度标签来保护敏感内容免遭未经授权的数据访问和泄露。

使用 Microsoft 信息保护敏感度标签来分类和标记 Power BI 服务中的报表、仪表板、数据集和数据流，并在将内容从 Power BI 服务导出到 Excel、PowerPoint 和 PDF 文件时保护敏感内容免遭未经授权的数据访问和泄露。

- [如何在 Power BI 中应用敏感度标签](../admin/service-security-apply-data-sensitivity-labels.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="dp-2-protect-sensitive-data"></a>DP-2：保护敏感数据

**指导**：Power BI 与 Microsoft 信息保护敏感度标签集成，以保护敏感数据。 有关更多详细信息，请参阅 [Power BI 中的 Microsoft 信息保护敏感度标签](../admin/service-security-sensitivity-label-overview.md)

Power BI 允许服务用户创建自己的密钥来保护静态数据。 有关更多详细信息，请参阅[对 Power BI 创建自己的加密密钥](../admin/service-encryption-byok.md)

客户可以选择将数据源保留在本地，并利用直接查询或实时连接和本地数据网关来最大程度地减少云服务的数据泄露。 有关更多详细信息，请参阅[什么是本地数据网关？](/data-integration/gateway/service-gateway-onprem)

Power BI 支持行级别安全性。 有关更多详细信息，请参阅 [Power BI 行级别安全性 (RLS)](../admin/service-admin-rls.md)。 请注意，RLS 甚至可以应用于直接查询数据源，在这种情况下，PBIX 文件充当安全代理。

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3：监视未经授权的敏感数据传输

**指导**：通过使用针对 Power BI 的 Microsoft Cloud App Security 支持，可部分实现此控制。

将 Cloud App Security 与 Power BI 结合使用，可帮助保护 Power BI 报表、数据和服务免遭意外泄露或破坏。 使用 Cloud App Security，可以为组织的数据创建条件访问策略，使用 Azure Active Directory (Azure AD) 中的实时会话控件来帮助确保你的 Power BI 分析是安全的。 设置这些策略后，管理员可以监视用户访问和活动，执行实时风险分析，并设置标签特定的控件。

使用
- [Power BI 中的 Microsoft Cloud App Security 控制](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4：加密传输中的敏感信息

**指导**：确保对于 HTTP 流量，连接到 Power BI 资源的任何客户端和数据源都可协商 TLS v1.2 或更高版本。

- [强制使用特定 TLS 版本](../admin/service-admin-power-bi-security.md#enforcing-tls-version-usage)

- [有关 TLS 安全性的信息](/security/engineering/solving-tls1-problem)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5：加密静态敏感数据

**指导**：Power BI 会对静态数据和正在处理的数据进行加密。 默认情况下，Power BI 使用 Microsoft 托管密钥来加密数据。 组织可以选择使用自己的密钥对 Power BI 中的静态用户内容（从报表图像到高级容量中已导入的数据集）进行加密。

- [使用 Power BI 中的“创建自己的密钥”](../admin/service-encryption-byok.md)

**Azure 安全中心监视**：不适用

**责任**：共享

## <a name="asset-management"></a>资产管理

有关详细信息，请参阅 [Azure 安全基准：资产管理](/azure/security/benchmarks/security-controls-v2-asset-management)。

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1：确保安全团队可以了解与资产相关的风险

**指导**：将 Azure Sentinel 与 Power BI Office 审核日志配合使用，以确保安全团队能够查看 Power BI 资产的风险。

- [将 Office 365 日志连接到 Azure Sentinel](/azure/sentinel/connect-office-365)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2：确保安全团队有权访问资产清单和元数据

**指导**：确保安全团队有权访问 Power BI Embedded 资源的持续更新清单。 安全团队通常需要此清单，以评估其组织遭遇新兴风险的可能性，并根据它不断提高安全性。 

Azure Resource Graph 可查询和发现订阅中的所有 Power BI Embedded 资源。  

请使用 Azure 中的标记以及其他元数据（名称、说明和类别）以合乎逻辑的方式组织资产。  

- [如何使用 Azure Resource Graph 浏览器创建查询](/azure/governance/resource-graph/first-query-portal)

- [资源命名和标记决策指南](/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=%2fazure%2fazure-resource-manager%2fmanagement%2ftoc.json)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="am-3-use-only-approved-azure-services"></a>AM-3：仅使用已批准的 Azure 服务

**指导**：Power BI 支持 Power BI Embedded 的基于 Azure 资源管理器的部署，并且可以通过 Azure Policy 使用自定义 Policy 定义来限制其资源的部署。

请使用 Azure Policy 来审核和限制用户可以在你的环境中预配哪些服务。 使用 Azure Resource Graph 查询和发现订阅中的资源。 你也可以使用 Azure Monitor 来创建规则，以便在检测到未经批准的服务时触发警报。

- [如何配置和管理 Azure Policy](/azure/governance/policy/tutorials/create-and-manage)

如何拒绝特定的资源类型
- [Azure Policy](/azure/governance/policy/samples/built-in-policies#general)

如何使用 Azure 创建查询
- [Resource Graph 资源管理器](/azure/governance/resource-graph/first-query-portal)

**Azure 安全中心监视**：不适用

**责任**：客户

## <a name="logging-and-threat-detection"></a>日志记录和威胁检测

有关详细信息，请参阅 [Azure 安全基准：日志记录和威胁检测](/azure/security/benchmarks/security-controls-v2-logging-threat-detection)。

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2：启用 Azure 标识和访问管理的威胁检测

**指导**：将 Power BI 中的任何日志转发到可用于设置自定义威胁检测的 SIEM。 此外，请根据[此处](../admin/service-security-using-microsoft-cloud-app-security-controls.md)的指南使用 Power BI 中的 Microsoft Cloud App Security (MCAS) 控制来启用异常情况检测。

- [跟踪 Power BI 中的用户活动](../admin/service-admin-auditing.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3：为 Azure 网络活动启用日志记录

**指导**：Power BI 是一种完全托管的 SaaS 产品/服务，基础网络配置和日志记录是 Microsoft 的责任。 对于使用专用链接的客户，可以配置一些日志记录和监视功能。

- [专用链接日志记录和监视](/azure/private-link/private-link-overview#logging-and-monitoring)

**Azure 安全中心监视**：不适用

**责任**：共享

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4：为 Azure 资源启用日志记录

**指导**：使用 Power BI，可以通过两个选项来跟踪用户活动：Power BI 活动日志和统一审核日志。 这些日志都包含 Power BI 审核数据的完整副本，但有几个重要区别，总结如下。
 
统一审核日志：

 
- 除 Power BI 审核事件外，还包括来自 SharePoint Online、Exchange Online、Dynamics 365 和其他服务的事件。

 
- 只有具有仅查看审核日志或审核日志权限的用户才有访问权限，例如全局管理员和审核员。

 
- 全局管理员和审核员可以使用 Microsoft 365 安全中心和 Microsoft 365 合规中心搜索统一审核日志。

 
- 全局管理员和审核员可以使用 Microsoft 365 管理 API 和 cmdlet 下载审核日志条目。

 
- 审核数据可保留 90 天。

 
- 即使租户移动到其他 Azure 区域，也要保留审核数据。
 
Power BI 活动日志：

 
- 仅包括 Power BI 审核事件。

 
 
- 全局管理员和 Power BI 服务管理员具有访问权限。

 
- 目前还没有用于搜索活动日志的用户界面。

 
- 全局管理员和 Power BI 服务管理员可以使用 Power BI REST API 和管理 cmdlet 下载活动日志条目。

 
- 活动数据可保留 30 天。

 
- 当租户移到其他 Azure 区域时，不保留活动数据。

- [Power BI 审核数据](../admin/service-admin-auditing.md#operations-available-in-the-audit-and-activity-logs)

- [Power BI 活动日志](../admin/service-admin-auditing.md#use-the-activity-log)

- [Power BI 审核日志](../admin/service-admin-auditing.md#use-the-audit-log)

**Azure 安全中心监视**：不适用

**责任**：共享

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5：集中管理和分析安全日志

**指导**：Power BI 将日志集中在两个位置：Power BI 活动日志和统一审核日志。 这些日志都包含 Power BI 审核数据的完整副本，但有几个重要区别，总结如下。
 

统一审核日志：

- 除了 Power BI 审核事件外，还包括来自 SharePoint Online、Exchange Online、Dynamics 365 和其他服务的事件。

- 只有具有仅查看审核日志或审核日志权限的用户才有访问权限，例如全局管理员和审核员。

- 全局管理员和审核员可以使用 Microsoft 365 安全中心和 Microsoft 365 合规中心搜索统一审核日志。

- 全局管理员和审核员可以使用 Microsoft 365 管理 API 和 cmdlet 下载审核日志条目。

- 审核数据可保留 90 天。

- 即使租户移动到其他 Azure 区域，也要保留审核数据。

 

Power BI 活动日志：

- 仅包括 Power BI 审核事件。

- 全局管理员和 Power BI 服务管理员具有访问权限。

- 目前还没有用于搜索活动日志的用户界面。

- 全局管理员和 Power BI 服务管理员可以使用 Power BI REST API 和管理 cmdlet 下载活动日志条目。

- 活动数据可保留 30 天。

- 当租户移到其他 Azure 区域时，不保留活动数据。

- [Power BI 审核数据](../admin/service-admin-auditing.md#operations-available-in-the-audit-and-activity-logs)

- [Power BI 活动日志](../admin/service-admin-auditing.md#use-the-activity-log)

- [Power BI 审核日志](../admin/service-admin-auditing.md#use-the-audit-log)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="lt-6-configure-log-storage-retention"></a>LT-6：配置日志存储保留期

**指导**：根据合规性、法规和业务要求，为 Office 审核日志配置存储保留策略。

- [Office 审核日志保留策略](/microsoft-365/compliance/audit-log-retention-policies)

**Azure 安全中心监视**：不适用

**责任**：客户

## <a name="incident-response"></a>事件响应

[有关详细信息，请参阅 *Azure 安全基线：* 事件响应](/azure/security/benchmarks/security-controls-v2-incident-response)。

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1：准备 - 更新 Azure 的事件响应流程

**指导**：确保组织具有响应安全事件的流程，已为 Azure 更新这些流程，并定期运用这些流程来确保就绪性。

- [在企业环境中实现安全性](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [事件响应参考指南](/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2：准备 - 设置事件通知

**指导**：在 Azure 安全中心中设置安全事件联系人信息。 如果 Microsoft 安全响应中心 (MSRC) 发现非法或未经授权的一方访问了你的数据，Microsoft 将使用此联系信息来与你取得联系。 还可以选择基于事件响应需求在不同的 Azure 服务中自定义事件警报和通知。 

- [如何设置 Azure 安全中心安全联系人](/azure/security-center/security-center-provide-security-contact-details)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3：检测和分析 - 基于高质量警报创建事件

**指导**：确保具有创建高质量警报和衡量警报质量的流程。 这样，你就可以从过去的事件中吸取经验，并为分析人员确定警报的优先级，这样他们就不会浪费时间来处理误报。

监视与 Microsoft Cloud App Security 中的 Power BI 相关的警报。 可以基于过去的事件经验、经验证的社区源以及旨在通过融合和关联各种信号源来生成和清理警报的工具构建高质量警报。

- [监视 Cloud App Security 中的警报](/cloud-app-security/monitor-alerts)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4：检测和分析 - 调查事件

**指导**：为组织制定事件响应指南。 定期进行练习来测试系统的事件响应功能。 识别弱点和差距，并根据需要修改计划。

确保在书面的事件响应计划中定义人员职责，以及事件处理/管理从检测到事件后审查的各个阶段。

- [Microsoft 威胁防护中的事件概述](/microsoft-365/security/mtp/incidents-overview)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5：检测和分析 - 确定事件优先级

**指导**：根据警报严重性和资产敏感度为分析人员提供要首先关注的事件的上下文。 

 
Microsoft 威胁防护应用关联分析，并将来自不同产品的所有相关警报和调查聚合到一个事件中。 鉴于 Microsoft 威胁防护在整个资产和产品套件中具有的端到端可见性，Microsoft 威胁防护还会针对只能识别为恶意的活动触发唯一警报。 这样，Microsoft 威胁防护就可以叙述广泛的攻击案例，使安全操作分析人员能够了解和处理整个组织内的复杂威胁。

- [在 Microsoft 威胁防护中确定事件的优先级](/microsoft-365/security/mtp/incident-queue?amp;preserve-view=true&view=o365-worldwide)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6：包含、根除和恢复 - 自动执行事件处理

**指导**：自动执行手动重复性任务来加快响应时间并减轻分析人员的负担。 执行手动任务需要更长的时间，这会导致减慢每个事件的速度，并减少分析人员可以处理的事件数量。 手动任务还会使分析人员更加疲劳，这会增加可导致延迟的人为错误的风险，并降低分析人员专注于复杂任务的工作效率。  
 
使用 Microsoft 威胁防护中的工作流自动化功能来自动触发调查和修正，以响应传入的安全警报。 
 
- [Microsoft 威胁防护中的自动调查和响应](/microsoft-365/security/mtp/mtp-autoir)

**Azure 安全中心监视**：不适用

**责任**：客户

## <a name="posture-and-vulnerability-management"></a>安全状况和漏洞管理

有关详细信息，请参阅 [Azure 安全基准：安全状况和漏洞管理](/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management)。

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1：为所有 Azure 服务建立安全配置 

**指导**：使用适用于你的组织和安全状况的设置配置 Power BI 服务。 应仔细考虑访问服务和内容的设置以及工作区和应用安全。 请参阅《Power BI Enterprise 部署》白皮书中的“Power BI 安全和数据保”。

- [Enterprise 部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2：为所有 Azure 服务维护安全配置

**指导**：使用 Power BI 管理 REST API 监视 Power BI 实例。

- [Power BI 管理 REST API](/rest/api/power-bi/admin)

- [Power BI Enterprise 部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8：执行定期攻击模拟

**指导**：根据需要，对 Azure 资源进行渗透测试或红队活动，并确保修正所有关键安全发现。

请遵循 Microsoft 云渗透测试互动规则，确保你的渗透测试不违反 Microsoft 政策。 使用 Microsoft 红队演练策略和执行，以及针对 Microsoft 托管云基础结构、服务和应用程序执行现场渗透测试。

- [Azure 中的渗透测试](/azure/security/fundamentals/pen-testing)

- [参与的渗透测试规则](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft 云红色组合](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure 安全中心监视**：不适用

**责任**：共享

## <a name="backup-and-recovery"></a>备份和恢复

有关详细信息，请参阅 [Azure 安全基准：备份和恢复](/azure/security/benchmarks/security-controls-v2-backup-recovery)。

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3：验证所有备份，包括客户管理的密钥

**指导**：如果使用 Power BI 中的“创建自己的密钥 (BYOK)”功能，则需定期验证是否可以访问和还原客户管理的密钥。

- [Power BI 中的 BYOK](../admin/service-encryption-byok.md)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4：减少密钥丢失风险

**指导**：如果使用 Power BI 中的“创建自己的密钥 (BYOK)”功能，则需要确保 Key Vault（用于控制客户管理的密钥）已按照下面 Power BI 文档的 BYOK 指导进行配置。 在 Azure Key Vault 中启用软删除和清除保护，以防止意外删除或恶意删除密钥。

- [Power BI 中的 BYOK](../admin/service-encryption-byok.md)

- [如何在 Key Vault 中启用软删除和清除保护](/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

对于网关密钥资源，请确保遵循下面网关恢复密钥文档中的指导。

- [本地数据网关恢复密钥](/data-integration/gateway/service-gateway-recovery-key)

**Azure 安全中心监视**：不适用

**责任**：客户

## <a name="governance-and-strategy"></a>治理和策略

有关详细信息，请参阅 [Azure 安全基准：治理和策略](/azure/security/benchmarks/security-controls-v2-governance-strategy)。

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1：定义资产管理和数据保护策略 

**指导**：确保为系统和数据的持续监视和保护记录并传达明确的策略。 确定业务关键数据和系统的发现、评估、保护和监视优先级。 

此策略应包括针对以下元素的记录在案的指南、策略和标准： 

-   与业务风险相符的数据分类标准

-   安全组织对风险和资产清单的洞察力 

-   安全组织对 Azure 服务使用的审批 

-   资产在其生命周期中的安全性

-   与组织数据分类相符的必需访问控制策略

-   使用 Azure 原生和第三方数据保护功能

-   传输中数据用例和静态数据用例的数据加密要求

-   合适的加密标准

有关详细信息，请参阅以下资源：
- [Azure 安全体系结构建议 - 存储、数据和加密](/azure/architecture/framework/security/storage-data-encryption?amp;bc=%2fsecurity%2fcompass%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fcompass%2ftoc.json)

- [Azure 安全基础知识 - Azure 数据安全、加密和存储](/azure/security/fundamentals/encryption-overview)

- [云采用框架 - Azure 数据安全和加密最佳做法](/azure/security/fundamentals/data-encryption-best-practices?amp;bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json)

- [Azure 安全基准 - 资产管理](/azure/security/benchmarks/security-controls-v2-asset-management)

- [Azure 安全基准 - 数据保护](/azure/security/benchmarks/security-controls-v2-data-protection)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2：定义企业分段策略 

**指导**：建立企业范围的策略，以便使用标识、网络、应用程序、订阅、管理组和其他控件的组合来细分对资产的访问。

仔细权衡安全分离需求与为需要彼此通信并访问数据的系统启用日常操作的需求。

确保跨控制类型（包括网络安全、标识和访问模型、应用程序权限/访问模型，以及人机过程控制）一致地实现分段策略。

- [有关 Azure 中的分段策略的指南（视频）](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [有关 Azure 中的分段策略的指南（文档）](/security/compass/governance#enterprise-segmentation-strategy)

- [使网络分段与企业分段策略相匹配](/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3：定义安全状况管理策略

**指导**：持续衡量并缓解你的个人资产及其托管环境的风险。 确定高价值资产和暴露程度高的受攻击面（例如已发布的应用程序、网络入口和出口点、用户和管理员终结点等）的优先级。

- [Azure 安全基准 - 状况和漏洞管理](/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4：协调组织角色、职责和责任

**指导**：确保为安全组织中的角色和责任记录并传达明确的策略。 优先考虑提供涉及安全决策的明确责任，对每个人进行共同职责模式培训，并为技术团队传授保护云的技术。

- [Azure 安全最佳做法 1 - 人员：针对云安全历程培训团队](/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Azure 安全最佳做法 2 - 人员：针对云安全技术培训团队](/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Azure 安全最佳做法 3 - 流程：针对云安全决策分配责任](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="gs-5-define-network-security-strategy"></a>GS-5：定义网络安全策略

**指导**：建立 Azure 网络安全方法，作为组织整体安全访问控制策略的一部分。  

此策略应包括针对以下元素的记录在案的指南、策略和标准： 

-   集中化的网络管理和安全职责

-   符合企业分段策略的虚拟网络分段模型

-   各种威胁和攻击场景中的补救策略

-   Internet 边缘及入口和出口策略

-   混合云和本地互连策略

-   最新的网络安全项目（例如网络关系图、参考网络体系结构）

有关详细信息，请参阅以下资源：
- [Azure 安全最佳做法 11 - 体系结构。单一的统一安全策略](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure 安全基准 - 网络安全](/azure/security/benchmarks/security-controls-v2-network-security)

- [Azure 网络安全概述](/azure/security/fundamentals/network-overview)

- [企业网络体系结构策略](/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6：定义标识和特权访问策略

**指导**：建立 Azure 标识和特权访问方法，作为组织整体安全访问控制策略的一部分。  

此策略应包括针对以下元素的记录在案的指南、策略和标准： 

-   集中化的标识和身份验证系统及其与其他内部和外部标识系统的互连

-   各种用例和条件中的强身份验证方法

-   保护权限高的用户

-   异常用户活动监视和处理  

-   用户标识和访问评审及协调流程

有关详细信息，请参阅以下资源：

- [Azure 安全基准 - 标识管理](/azure/security/benchmarks/security-controls-v2-identity-management)

- [Azure 安全基准 - 特权访问](/azure/security/benchmarks/security-controls-v2-privileged-access)

- [Azure 安全最佳做法 11 - 体系结构。单一的统一安全策略](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure 标识管理安全概述](/azure/security/fundamentals/identity-management-overview)

**Azure 安全中心监视**：不适用

**责任**：客户

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7：定义日志记录和威胁响应策略

**指导**：建立日志记录和威胁响应策略，以快速检测和修正威胁，同时满足合规性要求。 优先为分析人员提供高质量警报和无缝体验，以便他们能够专注于威胁而不是集成和手动步骤。 

此策略应包括针对以下元素的记录在案的指南、策略和标准： 

-   安全运营 (SecOps) 组织的角色和职责 

-   符合 NIST 或其他行业框架要求的明确定义的事件响应流程 

-   日志捕获和保留，用于支持威胁检测、事件响应和合规性需求

-   使用 SIEM、原生 Azure 功能和其他源，集中查看和关联有关威胁的信息 

-   与客户、供应商和公开的利益相关方之间的通信和通知计划

-   使用 Azure 原生的和第三方的平台进行事件处理，例如日志记录和威胁检测、取证以及攻击补救和根除

-   处理事件和事件后活动的流程，例如经验教训和证据保留

有关详细信息，请参阅以下资源：

- [Azure 安全基准 - 日志记录和威胁检测](/azure/security/benchmarks/security-controls-v2-logging-threat-detection)

- [Azure 安全基准 - 事件响应](/azure/security/benchmarks/security-controls-v2-incident-response)

- [Azure 安全最佳做法 4 - 流程。更新云的事件响应流程](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Azure 采用框架、日志记录和报告决策指南](/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Azure 企业规模、管理和监视](/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Azure 安全中心监视**：不适用

**责任**：客户

## <a name="next-steps"></a>后续步骤

- 参阅 [Azure 安全基准 V2 概述](/azure/security/benchmarks/overview)
- 详细了解 [Azure 安全基线](/azure/security/benchmarks/security-baselines-overview)
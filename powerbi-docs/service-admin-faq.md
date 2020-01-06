---
title: 管理 Power BI - 常见问题 (FAQ)
description: 了解有关 Power BI 注册、租户管理和其他管理任务的常见问题的答案。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 0c9d346017dc3b18abd6a56d0d3a62e1305e6575
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698730"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>管理 Power BI - 常见问题 (FAQ)

本文介绍了 Power BI 管理的常见问题。 有关 Power BI 管理的概述，请参阅[什么是 Power BI 管理？](service-admin-administering-power-bi-in-your-organization.md)。

## <a name="whats-in-this-article"></a>本文内容

### <a name="sign-up-for-power-bi-section"></a>“注册 Power BI”部分

* [使用 PowerShell](#using-powershell)
* [用户如何注册 Power BI？](#how-do-users-sign-up-for-power-bi)
* [组织中的各个用户如何注册？](#how-do-individual-users-in-my-organization-sign-up)
* [如何阻止用户加入现有 Office 365 租户？](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [如何允许用户加入现有 Office 365 租户？](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [如何检查是否在租户中实施了阻止？](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [如何阻止现有用户开始使用 Power BI？](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [如何允许现有用户注册 Power BI？](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>“管理 Power BI”部分

* [这会如何更改我当前为组织中的用户管理标识的方式？](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [我们如何管理 Power BI？](#how-do-we-manage-power-bi)
* [管理 Microsoft 为我的用户创建的租户的过程是怎样的？](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [如果我有多个域，是否可以控制向其中添加用户的 Microsoft 365 租户？](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [如何为已注册的用户删除 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [如何知道新用户加入了我的租户？](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [我是否还应为任何其他事项做好准备？](#are-there-any-additional-things-i-should-prepare-for)
* [我的 Power BI 租户位于何处？](#where-is-my-power-bi-tenant-located)
* [什么是 Power BI SLA（服务级别协议）？](#what-is-the-power-bi-sla)
* [Power BI 如何处理高可用性和故障转移？](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>“Power BI 中的安全性”部分

* [Power BI 是否满足特定于国家、地区和行业的合规性要求？](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Power BI 中安全性的工作原理是怎样的？](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>注册 Power BI

### <a name="using-powershell"></a>使用 PowerShell

必须使用 Windows PowerShell 脚本，才能执行此部分中的一些过程。 如果不熟悉 PowerShell，建议先参阅 [PowerShell 入门指南](https://go.microsoft.com/fwlink/p/?LinkID=286814)。 若要运行脚本，请先安装最新的 64 位版 [Azure Active Directory Graph PowerShell](/powershell/azure/active-directory/)。

### <a name="how-do-users-sign-up-for-power-bi"></a>用户如何注册 Power BI？

作为 Microsoft 365 管理员，你可通过 [Power BI 网站](https://powerbi.microsoft.com)或 Microsoft 365 管理中心内的[“购买服务”](https://admin.microsoft.com/AdminPortal/Home#/catalog)页来注册 Power BI。 当 Microsoft 365 管理员注册 Power BI 时，他们可以将用户许可证分配给应具有访问权限的用户。

此外，组织中的各个用户能够通过 [Power BI 网站](https://powerbi.microsoft.com)注册 Power BI。 当组织中的某个用户注册 Power BI 时，该服务会自动向此用户分配 Power BI 许可证。 有关详细信息，请参阅[以个人身份注册 Power BI](service-self-service-signup-for-power-bi.md) 和[组织中的 Power BI 授权](service-admin-licensing-organization.md)。

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>组织中的各个用户如何注册？

有三种方案可以适用于组织中的用户：

* **方案 1**：组织已有 Microsoft 365 环境，且要注册 Power BI 的用户已有 Microsoft 365 帐户。
    在这种场景中，如果用户已在租户（例如 contoso.com）中具有工作或学校帐户，但尚未注册 Power BI，那么 Microsoft 会直接为该帐户激活 Power BI（免费）计划。 系统会自动通知用户如何使用 Power BI 服务。

* **方案 2**：组织已有 Microsoft 365 环境，但要注册 Power BI 的用户没有 Microsoft 365 帐户。
    在这种场景中，用户在组织的域（例如，contoso.com）中具有电子邮件地址，但尚不具有 Microsoft 365 帐户。 在这种情况下，用户可以注册 Power BI，并自动获得帐户。 此操作使用户能够访问 Power BI 服务。 例如，如果名为 Nancy 的员工使用其工作电子邮件地址（如 nancy@contoso.com）进行注册，Microsoft 便会自动将 Nancy 添加为 Contoso Microsoft 365 环境中的用户，并为此帐户激活 Power BI。

* **方案 3**：组织没有连接到你的电子邮件域的 Microsoft 365 环境。
    组织无需执行任何管理操作即可利用 Power BI。 该服务将用户添加到仅限云的新用户目录中。 还可以选择作为租户的 Microsoft 365 全局管理员对其进行管理。

> [!IMPORTANT]
> 如果组织具有多个电子邮件域，且你希望将所有的电子邮件地址扩展名置于同一个租户中，请先将所有电子邮件地址域添加至一个 Azure Active Directory 租户，然后再注册用户。 创建用户后，没有可跨租户移动用户的自动机制。 若要详细了解此流程，请参阅本文稍后介绍的[如果我有多个域，是否可以控制向其中添加用户的 Microsoft 365 租户？](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)，以及[将域添加到 Microsoft 365](/office365/admin/setup/add-domain/)。

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>如何阻止用户加入现有 Microsoft 365 租户？

作为 Microsoft 365 全局管理员，你可以执行一些步骤来阻止用户加入现有 Microsoft 365 租户。 如果你阻止访问，用户的注册尝试便会失败，并会显示一条信息，指示他们联系其组织管理员。如果已禁用自动许可证分发（例如，通过 Office 365 教育版（学生和教职员工）），无需重复执行此流程。

若要禁止新用户加入托管租户，请运行以下 PowerShell 脚本。 （[详细了解 PowerShell][1]。）

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> 阻止访问可禁止组织中的新用户注册 Power BI。 在组织被禁进行新注册前注册 Power BI 的用户仍保留其许可证。 若要删除用户，请参阅本文稍后介绍的[我如何为已注册的用户删除 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)。

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>如何允许用户加入现有 Microsoft 365 租户？

若要让新用户加入托管租户，请运行以下 PowerShell 脚本。 （[详细了解 PowerShell][1]。）

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>如何检查是否在租户中实施了阻止？

使用以下 PowerShell 脚本检查设置。 AllowEmailVerifiedUsers  应为 false。 （[详细了解 PowerShell][1]。）

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>如何阻止现有用户开始使用 Power BI？

控制此操作的 Azure AD 设置为 AllowAdHocSubscriptions  。 大多数租户将此设置为 true，这意味着它处于启用状态  。 如果你通过合作伙伴获得 Power BI，则它可能设置为 false，这意味着它处于禁用状态  。

若要禁用临时订阅，请运行以下 PowerShell 脚本。（[详细了解 PowerShell][1]。）

1. 使用 Microsoft 365 凭据登录 Azure Active Directory。 以下 PowerShell 脚本中的第一行会提示你输入凭据。 第二行连接到 Azure Active Directory。

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![通过 PowerShell 登录 Azure Active Directory 的屏幕截图](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. 登录后，运行以下命令以查看租户的当前设置情况。

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. 运行以下命令以启用 (`$true`) 或禁用 (`$false`) AllowAdHocSubscriptions  。

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> 使用 AllowAdHocSubscriptions 标志在组织中控制多个用户功能，包括用户注册 Azure Rights Management 服务的能力  。 更改此标志会影响所有这些功能。 设置为 false 后，用户仍可以注册个人 Power BI Pro 试用版  。

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>如何允许现有用户注册 Power BI？

若要允许现有用户注册 Power BI，请运行针对上一个问题列出的命令，但在最后一步中传递 `$true` 而不是 `$false`。

## <a name="administration-of-power-bi"></a>Power BI 的管理

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>这会如何更改我当前为组织中的用户管理标识的方式？

有三种方案可以适用于组织中的用户：

* **方案 1**：如果组织已有 Microsoft 365 环境，并且组织中的所有用户都具有 Microsoft 365 帐户，则管理标识的方式不会发生变化。

* **方案 2**：如果组织已有 Microsoft 365 环境，但并非组织中的所有用户都有 Microsoft 365 帐户，那么我们会在租户中创建用户，并根据此用户的工作或学校电子邮件地址分配许可证。

    其结果是，在任何特定时间管理的用户数随组织中注册服务的用户数一起增加。

* **方案 3**：如果组织没有已连接到你的电子邮件域的 Microsoft 365 环境，则管理标识的方式也不会发生变化。

    该服务将用户添加到一个新的、仅在云上运行的用户目录中，在这里你可以作为 Microsoft 365 全局管理员对其进行管理。

### <a name="how-do-we-manage-power-bi"></a>我们如何管理 Power BI？

Power BI 为 Microsoft 365 全局管理员角色中的用户和 Power BI 服务管理员角色中的用户提供 Power BI 管理门户。 若要使用 Power BI 管理门户，需要在 Microsoft 365 或 Azure Active Directory 中将帐户标记为“全局管理员”，或需要某个人将 Power BI 服务管理员角色分配给你的用户帐户  。 有关详细信息，请参阅[了解 Power BI 管理员角色](service-admin-role.md)和 [ Power BI 管理门户](service-admin-portal.md)。 该门户提供了控制租户范围的设置、查看 Power BI 使用情况统计数据的能力以及指向用于管理用户和组的 Microsoft 365 管理中心的链接。

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>管理 Microsoft 为我的用户创建的租户的过程是怎样的？

自助服务用户注册使用 Azure AD 的云服务后，该服务会根据其电子邮件域将其添加到非托管 Azure AD 目录中。 你可以声明和管理他人使用“管理员接管”  流程创建的租户。 有关详细信息，请参阅[在 Azure Active Directory 中以管理员身份接管非托管目录](/azure/active-directory/users-groups-roles/domains-admin-takeover)。 所执行的接管类型取决于是否现有与域关联的托管租户：

* Power BI 支持内部管理员接管。 当你对非托管 Azure 目录执行内部管理员接管时，会将你添加为非托管目录的全局管理员  。 不会将用户、域或服务计划迁移到你管理的任何其他目录。

* Power BI 不再支持外部管理员接管。 当你对非托管 Azure 目录执行外部管理员接管时，会将非托管目录的 DNS 域名添加到托管的 Azure 目录  。 外部接管将无法访问原始非托管租户上的所有 Power BI 内容。 Power BI 报表将需要重新发布到新租户，并且需要在新租户中重新创建 Power BI 仪表板和应用。

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>如果我有多个域，是否可以控制向其中添加用户的 Microsoft 365 租户？

如果不执行任何操作，该服务会为每个用户电子邮件域和子域都创建一个租户。 如果你希望所有用户都处于相同租户中（不考虑其电子邮件地址扩展）：提前创建一个目标租户或者使用某个现有租户。 然后，在该租户内添加你希望合并的所有现有域和子域。 电子邮件地址以这些域和子域结尾的每个用户便会在注册时自动加入目标租户。

> [!IMPORTANT]
> 创建用户后，就没有受支持的自动机制可将用户跨租户移动。 若要了解如何向单个 Microsoft 365 租户添加域，请参阅[将用户和域添加到 Office 365](/office365/admin/setup/add-domain/)。

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>如何为已注册的用户删除 Power BI？

如果用户注册了 Power BI，但你不再希望他们有权访问 Power BI，可以删除此用户的 Power BI 许可证。

1. 转到 [MIcrosoft 365 管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在导航窗格中，选择“用户”   > “活动用户”  。

1. 找到要删除其许可证的用户，再选择其名称。

    也可以对用户执行批量许可证管理。 为此，请依次选择多个用户和“编辑产品许可证”  。

1. 在用户详细信息页上，选择“产品许可证”  旁边的“编辑”  。

1. 将“Power BI（免费）”或“Power BI Pro”（具体视你应用于帐户的许可证而定）设置为“关”    。

1. 选择**保存**。

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>如何知道新用户加入了我的租户？

通过自助注册加入租户的用户将获得一个唯一许可证，你可以在管理仪表板中的活动用户窗格内针对它进行筛选。 若要新建此视图，请按以下步骤操作。

1. 导航到 [MIcrosoft 365 管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在导航窗格中，选择“用户”   > “活动用户”  。

1. 在“视图”  菜单上，选择“添加自定义视图”  。

1. 命名新视图，并选择“已分配产品许可证”  下的“Power BI (免费)”  或“Power BI Pro”  。

    对每个视图只能选择一个许可证。 如果组织中既有“Power BI (免费)”  许可证，也有“Power BI Pro”  许可证，你可以创建两个视图。

1. 输入所需的其他任何条件，再选择“添加”  。

1. 创建新视图后，便可以使用“视图”菜单访问它  。

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>我是否还应为任何其他事项做好准备？

你可能会遇到密码重置请求增加的情况。 有关此过程的信息，请参阅[重置用户密码](/office365/admin/add-users/reset-passwords)。

你可以在 Microsoft 365 管理中心中通过标准过程从租户中删除用户。 不过，如果用户仍有组织提供的有效电子邮件地址，便能重新加入，除非你阻止所有用户加入。

### <a name="where-is-my-power-bi-tenant-located"></a>我的 Power BI 租户位于何处？

若要了解 Power BI 租户所在的数据区域，请参阅[我的 Power BI 租户位于何处？](service-admin-where-is-my-tenant-located.md)。

### <a name="what-is-the-power-bi-sla"></a>什么是 Power BI SLA？

有关 Power BI SLA（服务级别协议）的信息，请参阅 Microsoft 授权网站中“授权”部分内的[授权条款和文档](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37)一文  。

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Power BI 如何处理高可用性和故障转移？

有关高可用性和故障转移的信息，请参阅 [Power BI 高可用性、故障转移和灾难恢复常见问题解答](service-admin-failover.md)。

## <a name="security-in-power-bi"></a>Power BI 中的安全性

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI 是否满足特定于国家、地区和行业的合规性要求？

若要了解有关 Power BI 合规性的详细信息，请参阅 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx)。

### <a name="how-does-security-work-in-power-bi"></a>Power BI 中安全性的工作原理是怎样的？

Microsoft 以 Microsoft 365 为基础构建 Power BI，而 Microsoft 365 以 Azure 服务（如 Azure Active Directory）为基础而构建。 有关 Power BI 体系结构的概述，请参阅 [Power BI 安全性](service-admin-power-bi-security.md)。

## <a name="next-steps"></a>后续步骤

[Power BI 管理门户](service-admin-portal.md)  
[了解 Power BI 管理员角色](service-admin-role.md)  
[自助注册 Power BI](service-self-service-signup-for-power-bi.md)  
[购买 Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[什么是 Power BI Premium？](service-premium-what-is.md)  
[如何购买 Power BI Premium](service-admin-premium-purchase.md)  
[Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)  
[管理 Power BI 和 Office 365 中的组](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Office 365 用户帐户管理](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Office 365 组管理](/office365/admin/email/create-edit-or-delete-a-security-group/)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview

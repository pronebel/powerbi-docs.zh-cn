---
title: 管理 Power BI - 常见问题 (FAQ)
description: 了解在 Power BI 注册功能、 租户管理以及其他管理任务的常见问题的答案。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2e51017333a940bd9d7838e6a903c1a66ce2e342
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100783"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>管理 Power BI - 常见问题 (FAQ)

本文介绍了 Power BI 管理的常见问题。 有关 Power BI 管理的概述，请参阅[什么是 Power BI 管理？](service-admin-administering-power-bi-in-your-organization.md)。

## <a name="whats-in-this-article"></a>本文内容

### <a name="sign-up-for-power-bi-section"></a>“注册 Power BI”部分

* [使用 PowerShell](#using-powershell)
* [用户如何注册 Power BI？](#how-do-users-sign-up-for-power-bi)
* [组织中的各个用户如何注册？](#how-do-individual-users-in-my-organization-sign-up)
* [如何阻止用户加入现有 Office 365 租户？](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [如何允许用户加入现有 Office 365 租户？](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [如何检查是否实施了阻止租户中？](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [如何阻止现有用户开始使用 Power BI？](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [如何允许现有用户注册 Power BI？](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>“管理 Power BI”部分

* [这会如何更改我当前为组织中的用户管理标识的方式？](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [我们如何管理 Power BI？](#how-do-we-manage-power-bi)
* [管理 Microsoft 为我的用户创建的租户的过程是怎样的？](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [如果我有多个域，可以控制系统会将用户添加到 Office 365 租户？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [如何为已注册的用户删除 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [如何知道新用户加入了我的租户？](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [是否还应做哪些准备工作的任何其他事项？](#are-there-any-additional-things-i-should-prepare-for)
* [我的 Power BI 租户位于何处？](#where-is-my-power-bi-tenant-located)
* [什么是 Power BI SLA（服务级别协议）？](#what-is-the-power-bi-sla)
* [Power BI 如何处理高可用性和故障转移？](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>“Power BI 中的安全性”部分

* [Power BI 是否满足特定于国家、地区和行业的合规性要求？](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Power BI 中安全性的工作原理是怎样的？](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>注册 Power BI

### <a name="using-powershell"></a>使用 PowerShell

必须使用 Windows PowerShell 脚本，才能执行此部分中的一些过程。 如果不熟悉 PowerShell，建议先参阅 [PowerShell 入门指南](http://go.microsoft.com/fwlink/p/?LinkID=286814)。 若要运行脚本，请先安装最新的 64 位版 [Azure Active Directory Graph PowerShell](/powershell/azure/active-directory/)。

### <a name="how-do-users-sign-up-for-power-bi"></a>用户如何注册 Power BI？

作为管理员，你可以注册 Power BI 通过[Power BI 网站](https://powerbi.microsoft.com)或[购买服务](https://admin.microsoft.com/AdminPortal/Home#/catalog)上 Microsoft 365 管理中心内的页。 当管理员注册 Power bi 时，他们可以将用户许可证分配给应具有访问权限的用户。

此外，组织中的各个用户能够通过 [Power BI 网站](https://powerbi.microsoft.com)注册 Power BI。 当你的组织中的用户注册 Power bi 时，该服务会自动向用户分配 Power BI 许可证。 有关详细信息，请参阅[注册 Power BI 的个人身份](service-self-service-signup-for-power-bi.md)并[Power BI 中你的组织的许可](service-admin-licensing-organization.md)。

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>组织中的各个用户如何注册？

有三种方案可以适用于组织中的用户：

* **方案 1**：组织已有 Office 365 环境，且要注册 Power BI 的用户已有 Office 365 帐户。
    在此方案中，如果用户已有一个工作或学校帐户在租户 (例如，contoso.com) 中的，但不会还没有 Power BI 中，Microsoft 只会激活该帐户的计划。 若要使用 Power BI 服务了解如何使用自动通知用户。

* **方案 2**：组织已有 Office 365 环境，但要注册 Power BI 的用户没有 Office 365 帐户。
    在此方案中，用户在贵组织的域 (例如，contoso.com) 中有电子邮件地址，但还没有 Office 365 帐户。 在这种情况下，用户可以注册 Power BI，并自动获得帐户。 此操作允许用户访问 Power BI 服务。 例如，如果某位员工名为 Nancy 使用其工作电子邮件地址 (如nancy@contoso.com) 若要注册，Microsoft 会自动将 Nancy 添加为 Contoso 的 Office 365 环境中的用户并为该帐户激活 Power BI。

* **方案 3**：你的组织没有连接到你的电子邮件域的 Office 365 环境。
    没有所需的组织可以利用 Power BI 的任何管理操作。 该服务将用户添加到新的、 仅限云的用户目录。 您还可以选择作为租户管理员接管并对其进行管理。

> [!IMPORTANT]
> 如果组织具有多个电子邮件域，且你希望将所有的电子邮件地址扩展名置于同一个租户中，请先将所有电子邮件地址域添加至一个 Azure Active Directory 租户，然后再注册用户。 一旦你创建用户，没有自动的机制来跨租户移动用户。 此过程的详细信息，请参阅[如果我有多个域，可以控制系统会将用户添加到 Office 365 租户？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)这篇文章中更高版本并[将域添加到 Office 365](/office365/admin/setup/add-domain/)。

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>如何阻止用户加入现有 Office 365 租户？

作为管理员，你可以执行一些步骤来阻止用户加入现有 Office 365 租户。 如果阻止访问，用户尝试注册失败，并且出现一条消息，指导用户联系其组织的管理员。无需重复此过程，如果已禁用了自动许可证分发 （例如，通过 Office 365 教育版的学生、 教职员工和员工)。

若要禁止新用户加入托管租户，请运行以下 PowerShell 脚本。 （[详细了解 PowerShell][1]）

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> 阻止访问可禁止组织中的新用户注册 Power BI。 在组织被禁进行新注册前注册 Power BI 的用户仍保留其许可证。 若要删除用户，请参阅本文稍后介绍的[我如何为已注册的用户删除 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)。

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>如何允许用户加入现有 Office 365 租户？

使用以下 PowerShell 脚本以允许新用户加入托管的租户。 （[详细了解 PowerShell][1]）

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>如何检查是否实施了阻止租户中？

使用以下 PowerShell 脚本来检查设置。 AllowEmailVerifiedUsers  应为 false。 （[详细了解 PowerShell][1]）

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>如何阻止现有用户开始使用 Power BI？

控制此操作的 Azure AD 设置为 AllowAdHocSubscriptions  。 大多数租户将该值设置为 true，这意味着它已启用。 如果通过合作伙伴获取 Power BI，这可能会设置为 false，这意味着它处于禁用状态。

若要禁用临时订阅，请运行以下 PowerShell 脚本。 （[详细了解 PowerShell][1]）

1. 使用 Office 365 凭据登录 Azure Active Directory。 以下 PowerShell 脚本的第一行会提示你输入凭据。 第二行连接到 Azure Active Directory。

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![通过 PowerShell 屏幕截图的 Azure Active Directory 登录](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. 一次登录时，运行以下命令以查看你的租户的当前设置方式。

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. 运行以下命令以启用 (`$true`) 或禁用 (`$false`) **AllowAdHocSubscriptions**。

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> 使用**AllowAdHocSubscriptions**标志来控制你的组织，包括用户注册 Azure Rights Management 服务的功能中的多个用户功能。 更改此标志会影响所有这些功能。

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>如何允许现有用户注册 Power BI？

若要允许现有用户注册 Power BI 中，运行命令列出的前一个问题，但传递`$true`而不是`$false`中的最后一步。

## <a name="administration-of-power-bi"></a>Power BI 的管理

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>这会如何更改我当前为组织中的用户管理标识的方式？

有三种方案可以适用于组织中的用户：

* **方案 1**：如果你的组织已经具有现有 Office 365 环境并且你的组织中的所有用户都具有 Office 365 帐户，则管理标识的方式没有变化。

* **方案 2**：如果你的组织已经具有现有 Office 365 环境但你的组织中的不是所有用户都具有 Office 365 帐户，我们将在租户中创建用户并分配许可证根据用户的工作或学校电子邮件地址。

    结果是，将在任何特定时间所管理的用户数随着你的组织中的用户注册服务。

* **方案 3**：如果你的组织没有连接到你的电子邮件域的 Office 365 环境，没有任何更改管理标识的方式。

    该服务将用户添加到新的、 仅限云的用户目录。 此外，您可以选择作为租户管理员接管并对其进行管理。

### <a name="how-do-we-manage-power-bi"></a>我们如何管理 Power BI？

Power BI 提供了一个管理门户，可查看使用情况统计信息提供指向 Microsoft 365 管理中心内管理用户和组，并提供了控制租户范围的设置的功能。

若要使用 Power BI 管理门户，必须将标记你的帐户作为**全局管理员**在 Office 365 或 Azure Active Directory 或人必须分配 Power BI 服务管理员角色为你的用户帐户。 有关详细信息，请参阅[了解 Power BI 管理员角色](service-admin-role.md)并[Power BI 管理门户](service-admin-portal.md)。

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>管理 Microsoft 为我的用户创建的租户的过程是怎样的？

当自助服务用户注册使用 Azure AD 的云服务时，该服务将它们添加到非托管 Azure AD 目录根据其电子邮件域。 你可以声明和管理的租户的某人创建了使用此过程称为*管理员接管*。 接管执行操作的类型取决于是否已存在托管租户与域关联：

* “内部接管”  类型用于为域新建托管租户。

* “外部接管”  类型用于将域移到现有托管租户中。

有关详细信息，请参阅[以在 Azure Active Directory 中的管理员身份接管非托管目录](/azure/active-directory/users-groups-roles/domains-admin-takeover)。

在执行外部接管时，服务放入 Power BI 内容的之前创建的在接管[Power BI 存档工作区](service-admin-power-bi-archived-workspace.md)。 必须手动迁移要在新租户中使用的任何内容。

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>如果我有多个域，可以控制系统会将用户添加到 Office 365 租户？

如果不执行任何操作，该服务将创建每个用户的电子邮件域和子域的租户。 如果你希望所有用户都处于相同租户中（不考虑其电子邮件地址扩展）：目标提前创建租户，或使用现有租户。 然后添加所有现有域和你希望在该租户中合并的子域。 在注册时，自动以这些域和子域结尾的电子邮件地址与每个用户加入目标租户。

> [!IMPORTANT]
> 一旦你创建用户，没有任何受支持的自动化的机制来跨租户移动用户。 若要了解有关域添加到单个 Office 365 租户的信息，请参阅[将用户和域添加到 Office 365](/office365/admin/setup/add-domain/)。

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>如何为已注册的用户删除 Power BI？

如果用户注册了 Power BI，但你不再希望他们有权访问 Power BI，可以删除此用户的 Power BI 许可证。

1. 转到 [MIcrosoft 365 管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在左侧导航栏中，选择**用户**  >  **活动用户**。

1. 找到要删除其许可证的用户，再选择其名称。

    也可以对用户执行批量许可证管理。 为此，请依次选择多个用户和“编辑产品许可证”  。

1. 在用户详细信息页上，选择“产品许可证”  旁边的“编辑”  。

1. 根据什么许可你应用于其帐户时，设置**Power BI （免费）** 或**Power BI Pro**到**关闭**。

1. 选择**保存**。

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>如何知道新用户加入了我的租户？

作为此计划的一部分加入了你的租户的用户分配唯一的许可证，管理员仪表板中的活动用户窗格内可以根据筛选。 若要新建此视图，请按以下步骤操作。

1. 导航到 [MIcrosoft 365 管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在左侧导航栏中，选择**用户**  >  **活动用户**。

1. 在“视图”  菜单上，选择“添加自定义视图”  。

1. 命名新视图，并选择“已分配产品许可证”  下的“Power BI (免费)”  或“Power BI Pro”  。

    对每个视图只能选择一个许可证。 如果组织中既有“Power BI (免费)”  许可证，也有“Power BI Pro”  许可证，你可以创建两个视图。

1. 输入所需的其他任何条件，再选择“添加”  。

1. 创建新视图后，便可从**视图**菜单。

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>是否还应做哪些准备工作的任何其他事项？

你可能会遇到密码重置请求增加的情况。 有关此过程的信息，请参阅[重置用户的密码](/office365/admin/add-users/reset-passwords)。

你可以在 Microsoft 365 管理中心中通过标准过程从租户中删除用户。 不过，如果用户仍有组织提供的有效电子邮件地址，便能重新加入，除非你阻止所有用户加入。

### <a name="where-is-my-power-bi-tenant-located"></a>我的 Power BI 租户位于何处？

有关哪些数据区域在 Power BI 租户是中的信息，请参阅[我的 Power BI 租户位于何处？](service-admin-where-is-my-tenant-located.md)。

### <a name="what-is-the-power-bi-sla"></a>什么是 Power BI SLA？

有关 Power BI SLA （服务级别协议） 的信息，请参阅[许可条款和文档](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37)中的文章**许可**Microsoft 许可网站部分。

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Power BI 如何处理高可用性和故障转移？

有关高可用性和故障转移的信息，请参阅[Power BI 的高可用性、 故障转移和灾难恢复常见问题解答](service-admin-failover.md)。

## <a name="security-in-power-bi"></a>Power BI 中的安全性

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI 是否满足特定于国家、地区和行业的合规性要求？

若要了解有关 Power BI 合规性的详细信息，请参阅 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx)。

### <a name="how-does-security-work-in-power-bi"></a>Power BI 中安全性的工作原理是怎样的？

Microsoft Office 365，进而以 Azure Active Directory 等 Azure 服务的基础上建立 Power BI。 有关 Power BI 体系结构的概述，请参阅 [Power BI 安全性](service-admin-power-bi-security.md)。

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

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview
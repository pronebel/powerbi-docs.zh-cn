---
title: 管理 Power BI - 常见问题 (FAQ)
description: 了解有关 Power BI 注册、租户管理和其他管理任务的常见问题的答案。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: b77d20b8c9705e4b4cd811ea8dfa3008908a4438
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641663"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>管理 Power BI - 常见问题 (FAQ)

本文介绍了 Power BI 管理的常见问题。 有关 Power BI 管理的概述，请参阅[什么是 Power BI 管理？](service-admin-administering-power-bi-in-your-organization.md)。

## <a name="whats-in-this-article"></a>本文内容
**注册 Power BI**

* [用户如何注册 Power BI？](#how-do-users-sign-up-for-power-bi)
* [组织中的各个用户如何注册？](#how-do-individual-users-in-my-organization-sign-up)
* [如何阻止用户加入现有 Office 365 租户？](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [如何允许用户加入现有 Office 365 租户？](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [如何验证是否在租户中实施了阻止？](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [如何阻止现有用户开始使用 Power BI？](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [如何允许现有用户注册 Power BI？](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

**Power BI 的管理**

* [这会如何更改我当前为组织中的用户管理标识的方式？](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [我们如何管理 Power BI？](#how-do-we-manage-power-bi)
* [管理 Microsoft 为我的用户创建的租户的过程是怎样的？](#what-is-the-process-to-manage-a-tenant-created-by-Microsoft-for-my-users)
* [如果我有多个域，是否可以控制向其中添加用户的 Office 365 租户？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [如何为已注册的用户删除 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [如何知道新用户加入了我的租户？](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [我是否还应为任何其他事项做好准备？](#are-there-any-additional-things-i-should-be-prepared-for)
* [我的 Power BI 租户位于何处？](#where-is-my-power-bi-tenant-located)
* [什么是 Power BI SLA（服务级别协议）？](#what-is-the-power-bi-sla)

**Power BI 中的安全性**

* [Power BI 是否满足特定于国家、地区和行业的合规性要求？](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Power BI 中安全性的工作原理是怎样的？](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>注册 Power BI
### <a name="how-do-users-sign-up-for-power-bi"></a>用户如何注册 Power BI？
可以通过 [Power BI 网站](https://powerbi.microsoft.com)注册 Power BI。 还可以通过 Office 365 管理中心上的购买服务页面进行注册。 当管理员注册 Power BI 时，他们可以将用户许可证分配给应具有访问权限的用户。

此外，组织中的各个用户能够通过 [Power BI 网站](https://powerbi.microsoft.com)注册 Power BI。 当组织中的某个用户注册 Power BI 时，系统会自动向该用户分配 Power BI 许可证。 [了解详细信息](service-self-service-signup-for-power-bi.md)

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>组织中的各个用户如何注册？
有三种方案可以适用于组织中的用户：

方案 1：组织已具有现有 Office 365 环境，要注册 Power BI 的用户已具有 Office 365 帐户。
在此方案中，如果用户已在租户（例如，contoso.com）中具有工作或学校帐户，但尚未具有 Power BI，则 Microsoft 只需为该帐户激活计划，用户会自动收到通知，了解如何使用 Power BI 服务。

方案 2：组织已具有现有 Office 365 环境，要注册 Power BI 的用户没有 Office 365 帐户。
在此方案中，用户在组织的域（例如，contoso.com）中具有电子邮件地址，但尚未具有 Office 365 帐户。 在这种情况下，用户可以注册 Power BI，会自动获得帐户。 这使用户可以访问 Power BI 服务。 例如，如果名为 Nancy 的员工使用其工作电子邮件地址（例如，Nancy@contoso.com）进行注册，Microsoft 会自动在 Contoso 的 Office 365 环境中将 Nancy 添加为用户，并为此帐户激活 Power BI。

方案 3：组织没有连接到你的电子邮件域的 Office 365 环境。
组织无需执行任何管理操作即可利用 Power BI。 用户会添加到新的仅限云的用户目录中，你可以选择作为租户管理员进行接管并管理他们。

> [!IMPORTANT]
> 如果组织具有多个电子邮件域，且你希望将所有的电子邮件地址扩展名置于同一个租户中，请先将所有电子邮件地址域添加至一个 Azure Active Directory 租户，然后再注册用户。 没有可在租户创建之后跨租户移动用户的自动机制。 有关此过程的详细信息，请参阅本文后面部分中的[如果我有多个域，是否可以控制向其中添加用户的 Office 365 租户？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)，以及在线的[将域添加到 Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)。
> 
> 

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>如何阻止用户加入现有 Office 365 租户？
作为管理员，你可以执行一些步骤来阻止用户加入现有 Office 365 租户。 如果阻止此操作，则用户进行注册的尝试会失败，系统会指示他们与其组织管理员联系。如果已禁用了自动许可证分发（例如 Office 365 教育版（学生、教职员工和员工）），则无需重复此过程。

这些步骤需要使用 Windows PowerShell。 若要开始使用 Windows PowerShell，请参阅 [PowerShell 入门指南](http://go.microsoft.com/fwlink/p/?LinkID=286814)。

若要执行以下步骤，必须安装最新 64 位版本的[用于 Windows PowerShell 的 Azure Active Directory 模块](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

选择链接之后，选择**运行**以运行安装程序包。

**禁用自动租户联接**：使用此 Windows PowerShell 命令可阻止新用户加入托管租户：

* 针对新用户禁用自动租户加入：
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
* 针对新用户启用自动租户加入：
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

> [!NOTE]
> 该阻止行为将阻止组织中的新用户注册 Power BI。 在为组织禁用新注册之前注册 Power BI 的用户仍会保留其许可证。 有关如何为以前注册过 Power BI 的用户删除对该服务的访问权限的说明，请参阅 [如何删除许可证？] 部分。
> 
> 

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>如何允许用户加入现有 Office 365 租户？
若要允许用户加入租户，请运行与以上问题中所述相反的命令。

若要执行以下步骤，必须安装最新 64 位版本的[用于 Windows PowerShell 的 Azure Active Directory 模块](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>如何验证是否在租户中实施了阻止？
使用以下 PowerShell 脚本。

若要执行以下步骤，必须安装最新 64 位版本的[用于 Windows PowerShell 的 Azure Active Directory 模块](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Get-MsolCompanyInformation | fl allow*

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>如何阻止现有用户开始使用 Power BI？
作为管理员，你可以执行一些步骤来阻止用户注册 Power BI。 如果阻止此操作，则用户进行注册的尝试会失败，系统会指示他们与其组织管理员联系。如果已禁用了自动许可证分发（例如 Office 365 教育版（学生、教职员工和员工）），则无需重复此过程。 [了解详细信息](service-admin-licensing-organization.md#enable-or-disable-individual-user-sign-up-in-azure-active-directory)

对此进行控制的 AAD 设置是 **AllowAdHocSubscriptions**。 大多数租户会将此设置设置为 true，这意味着它处于启用状态。 如果你是通过合作伙伴获取 Power BI，则这可能会在默认情况下设置为 false，这意味着它处于禁用状态。

若要执行以下步骤，必须安装最新 64 位版本的[用于 Windows PowerShell 的 Azure Active Directory 模块](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

1. 你需要首先使用 Office 365 凭据登录 Azure Active Directory。 第一行会提示你输入凭据。 第二行连接到 Azure Active Directory。
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. 登录之后，你便可以发出以下命令以查看租户当前是针对哪种类型配置的。
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. 可以使用此命令启用 ($true) 或禁用 ($false) AllowAdHocSubscriptions。
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> AllowAdHocSubscriptions 标记用于控制组织中的若干用户功能，其中包括用户注册 Azure 权限管理服务的功能。 更改此标志会影响所有这些功能。
> 
> 

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>如何允许现有用户注册 Power BI？
若要允许现有用户注册 Power BI，请运行为以上问题列出的命令，但是传递 true 而不是 false。

若要执行以下步骤，必须安装最新 64 位版本的[用于 Windows PowerShell 的 Azure Active Directory 模块](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

1. 你需要首先使用 Office 365 凭据登录 Azure Active Directory。 第一行会提示你输入凭据。 第二行连接到 Azure Active Directory。
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. 登录之后，你便可以发出以下命令以查看租户当前是针对哪种类型配置的。
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. 可以使用此命令启用 ($true) 或禁用 ($false) AllowAdHocSubscriptions。
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> AllowAdHocSubscriptions 标记用于控制组织中的若干用户功能，其中包括用户注册 Azure 权限管理服务的功能。 更改此标志会影响所有这些功能。
> 
> 

## <a name="administration-of-power-bi"></a>Power BI 的管理
### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>这会如何更改我当前为组织中的用户管理标识的方式？
如果组织已具有现有 Office 365 环境，并且组织中的所有用户都具有 Office 365 帐户，标识管理不会更改。

如果组织已具有现有 Office 365 环境，但并非组织中的所有用户都具有 Office 365 帐户，则我们会在租户中创建用户并基于用户的工作或学校电子邮件地址分配许可证。 这意味着在任何特定时间所管理的用户数会随着组织中的用户注册服务而增长。

如果组织没有连接到你的电子邮件域的 Office 365 环境，则管理标识的方式不会发生变化。 用户会添加到新的仅限云的用户目录中，你可以选择作为租户管理员进行接管并管理他们。

### <a name="how-do-we-manage-power-bi"></a>我们如何管理 Power BI？
Power BI 提供了一个管理门户，它使你可以查看使用情况统计信息，提供了指向 Office 365 管理中心的链接以管理用户和组，并提供了控制租户范围设置的功能。 

> [!NOTE]
> 帐户必须标记为 Office 365 或 Azure Active Directory 中的 **全局管理员** ，或者已分配到 Power BI 服务管理员角色，才能获取对 Power BI 管理门户的访问权限。 若要详细了解 Power BI 服务管理员角色，请参阅[了解 Power BI 管理员角色](service-admin-role.md)。
> 
> 

有关详细信息，请参阅 [Power BI 管理门户](service-admin-portal.md)。

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>管理 Microsoft 为我的用户创建的租户的过程是怎样的？
如果 Microsoft 创建了某个租户，则你可以通过执行以下步骤来声明并管理该租户：

1. 通过注册 Power BI（使用与你要管理的租户域匹配的电子邮件地址域）来加入租户。 例如，如果 Microsoft 创建了 contoso.com 租户，你需要使用以 @contoso.com 结尾的电子邮件地址加入此租户。
2. 通过验证域所有权来声明管理员控制权：处于租户中之后，你可以通过验证域所有权将自己提升为 *全局管理员* 角色。 为此，请执行以下步骤：
   
   1. 转到 [https://portal.office.com](https://portal.office.com)。
   2. 在左上方选择应用启动器图标，然后选择**管理员**。
   3. 阅读**成为管理员**页面上的说明，然后选择**是，我想成为管理员**。
      
      > [!NOTE]
      > 如果此选项未出现，则已存在 Office 365 管理员。
      > 
      > 

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>如果我有多个域，是否可以控制向其中添加用户的 Office 365 租户？
如果不执行任何操作，则会为每个用户电子邮件域和子域都创建一个租户。

如果你希望所有用户都处于相同租户中（不考虑其电子邮件地址扩展）：

* 提前创建目标租户，或使用现有租户，添加你希望在该租户中合并的所有现有域和子域。 随后电子邮件地址以这些域和子域结尾的所有用户都会在注册时自动加入目标租户。

> [!IMPORTANT]
> 创建租户后，则不存在支持将用户跨租户迁移的自动机制。 若要了解有关域添加到单个 Office 365 租户的信息，请参阅[将用户和域添加到 Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)。
> 
> 

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>如何为已注册的用户删除 Power BI？
如果用户注册了 Power BI，但是你不再希望他们有权访问 Power BI，在可以为该用户删除 Power BI 许可证。

1. 导航到 Office 365 管理中心。
2. 在左侧导航栏中，选择**用户**  >  **活动用户**。
3. 找到要删除其许可证的用户，然后选择其名称 > **编辑**。
4. 在用户详细信息页面上，在左侧导航栏中选择**许可证**。
5. 取消选中**Power BI (免费)** 或**Power BI Pro**（具体取决于应用于其帐户的许可证）。
6. 选择“保存”。

> [!NOTE]
> 也可以对用户执行批量许可证管理。 若要执行该操作，请选择多个用户，然后选择**编辑**。
> 
> 

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>如何知道新用户加入了我的租户？
已作为此计划的一部分加入租户的用户会分配有唯一的许可证，你可以在管理仪表板中的活动用户窗格内针对它进行筛选。

若要创建此新视图，请在 Office 365 管理中心中，转到**用户**  >  **活动用户**，然后在**选择视图**菜单上，选择**新建视图**。 命名新视图，然后在**已分配的许可证**下，选择 **Power BI (免费)** 或 **Power BI Pro**。 对每个视图只能选择一个许可证。 如果组织中同时具有 **Power BI (免费)** 和 **Power BI Pro** 许可证，则你需要创建两个视图。 创建了新视图之后，你便能够查看租户中已在此计划中注册的所有用户。

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>我是否还应为任何其他事项做好准备？
你可能会遇到密码重置请求增加的情况。 有关此过程的信息，请参阅[重置用户密码](https://support.office.com/article/Reset-a-users-password-7a5d073b-7fae-4aa5-8f96-9ecd041aba9c)。

你可以在 Office 365 管理中心中通过标准过程从租户中删除用户。 但是，如果用户仍然具有来自你的组织的活动电子邮件地址，则他们能够重新加入，除非你阻止所有用户加入。

### <a name="where-is-my-power-bi-tenant-located"></a>我的 Power BI 租户位于何处？
若要了解有关如何查找 Power BI 租户所处的位置（也称为数据区域），请参阅[我的 Power BI 租户位于何处？](service-admin-where-is-my-tenant-located.md)

### <a name="what-is-the-power-bi-sla"></a>什么是 Power BI SLA？
有关 Power BI SLA（服务级别协议）的信息，请查阅 Microsoft 许可网站上“许可”部分中的[许可条款和文档](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37)一文。

## <a name="security-in-power-bi"></a>Power BI 中的安全性
### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI 是否满足特定于国家、地区和行业的合规性要求？
若要了解有关 Power BI 合规性的详细信息，请参阅 [Microsoft 信任中心](http://go.microsoft.com/fwlink/?LinkId=785324)。

### <a name="how-does-security-work-in-power-bi"></a>Power BI 中安全性的工作原理是怎样的？
Power BI 以 Office 365 的功能为基础而构建，后者进而以 Azure 服务（如 Azure Active Directory）为基础而构建。 有关 Power BI 体系结构的概述，请参阅 [Power BI 安全性](service-admin-power-bi-security.md)。 

## <a name="next-steps"></a>后续步骤
[Power BI 管理门户](service-admin-portal.md)  
[了解 Power BI 管理员角色](service-admin-role.md)  
[自助注册 Power BI](service-self-service-signup-for-power-bi.md)  
[购买 Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[什么是 Power BI Premium？](service-premium.md)  
[如何购买 Power BI Premium](service-admin-premium-purchase.md)  
[Office 365 用户帐户管理](https://technet.microsoft.com/library/office-365-user-account-management.aspx)  
[Office 365 组管理](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)  
[管理 Power BI 和 Office 365 中的组](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)  

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
---
title: 使用 Azure AD B2B 将内容分发给外部来宾用户
description: Power BI 与 Azure Active Directory 企业到企业 (Azure AD B2B) 集成后，即可将 Power BI 内容安全地分发给组织外的来宾用户。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b7327a7b32aacd222efc422263187f29285bd73
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71075777"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>使用 Azure AD B2B 将 Power BI 内容分发给外部来宾用户

Power BI 与 Azure Active Directory 企业到企业 (Azure AD B2B) 集成，便于你将 Power BI 内容安全分发给组织外的来宾用户，同时仍能继续控制内部数据。  

另外，你还可以使组织外部的来宾用户能够编辑和管理组织内的内容。

## <a name="enable-access"></a>启用访问权限

邀请来宾用户前，请务必先在 Power BI 管理门户中启用[与外部用户共享内容](service-admin-portal.md#export-and-sharing-settings)功能。

还可以使用[允许外部来宾用户编辑和管理组织中的内容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能。 借助该功能可以选择哪个来宾用户可以在工作区中查看和创建内容，包括浏览组织的 Power BI。

## <a name="who-can-you-invite"></a>可以邀请哪些用户？

可邀请使用任意电子邮件地址（包括个人帐户，如 gmail.com、outlook.com 和 hotmail.com）的来宾用户。 Azure AD B2B 将这些地址称为“社交标识”  。

## <a name="invite-guest-users"></a>邀请来宾用户

只有在首次邀请来宾用户加入组织时才需要发出邀请。 邀请用户的方法有两种：计划内邀请和临时邀请。

### <a name="planned-invites"></a>计划性邀请

如果确定要邀请哪些用户，请使用计划内邀请。 可使用 Azure 门户或 PowerShell 发送邀请。 只有租户管理员才能邀请用户。

若要在 Azure 门户中发送邀请，请按以下步骤操作。

1. 在[Azure 门户](https://portal.azure.com)中，选择“Azure Active Directory”  。

1. 在“管理”  下，选择“用户”   > “所有用户”   > “新建来宾用户”  。

    ![显示“新建来宾用户”选项的 Azure 门户的屏幕截图。](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. 输入“电子邮件地址”  和“个人消息”  。

    ![Azure AD 门户“新建来宾用户”对话框的屏幕截图。](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. 选择“邀请”  。

若要邀请多个来宾用户，请使用 PowerShell。 有关详细信息，请参阅 [Azure AD B2B 协作代码和 PowerShell 示例](/azure/active-directory/b2b/code-samples/)。

来宾用户需要在他们收到的电子邮件邀请中选择“开始”  。 然后就会将该来宾用户添加到租户。

![来宾用户电子邮件邀请的屏幕截图。](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>临时邀请

通过共享 UI 将外部用户添加到仪表板或报表，或通过访问页面添加到应用，即可随时邀请外部用户。 以下示例说明邀请外部用户使用应用时要执行的操作。

![在 Power BI 中被添加到应用访问列表的外部用户的屏幕截图。](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

该来宾用户将收到说明你已与其共享应用的电子邮件。

![与来宾用户共享应用时发送的电子邮件的屏幕截图](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

该来宾用户必须使用其组织电子邮件地址进行登录。 完成登录后，将收到接受邀请的提示。 登录后，将为来宾用户打开应用。 他们可以将链接设为书签，也可以保存电子邮件，以便稍后返回到应用。

## <a name="licensing"></a>许可

来宾用户必须拥有正确的授权，才能查看已共享的内容。 可使用以下三种方法来确保用户拥有正确的许可证：使用 Power BI Premium；分配 Power BI Pro 许可证；或使用来宾用户的 Power BI Pro 许可证。

使用[允许外部来宾用户编辑和管理组织中的内容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能时，向工作区提供内容或与他人共享内容的来宾用户需要具有 Power BI Pro 许可。

### <a name="use-power-bi-premium"></a>使用 Power BI Premium

如果你将应用工作区分配到 [Power BI Premium 容量](service-premium-what-is.md)，来宾用户无需获取 Power BI Pro 许可证，即可使用应用。 使用 Power BI Premium 时，应用还可以利用其他功能（如加快刷新速率、专用容量和大模型）。

![使用 Power BI Premium 的来宾用户体验的关系图。](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>向来宾用户分配 Power BI Pro 许可证

如果你在租户内向来宾用户分配 Power BI Pro 许可证，来宾用户便能查看租户内容。

![在租户内分配 Pro 许可证时的来宾用户体验关系图。](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>来宾用户拥有自己的 Power BI Pro 许可证

在来宾用户的租户中已向来宾用户分配 Power BI Pro 许可证。

![拥有自己的许可证的来宾用户体验的关系图。](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>可以编辑和管理内容的来宾用户 

使用[允许外部来宾用户编辑和管理组织中的内容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能时，指定的来宾用户能访问组织的 Power BI。 他们可以查看有权查看的任何内容。 他们可以访问主页、浏览工作区、安装应用、查看自己在访问列表上的位置，以及向工作区提供内容。 还可以创建或成为使用新工作区体验的工作区管理员。 存在一些限制。 “注意事项和限制”部分列出了这些限制。
 
要帮助这些用户登录到 Power BI，请向他们提供租户 URL。 要查找租户 URL，请执行以下步骤。

1. 在 Power BI 服务的顶部菜单栏中，依次选择帮助图标 (?  )和“关于 Power BI”  。

2. 查找“租户 URL”旁的值  。 该值就是可与来宾用户共享的租户 URL。

    ![显示来宾用户租户 URL 的“关于 Power BI”对话框的屏幕截图。](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>注意事项和限制

* 默认情况下，外部 Azure AD B2B 来宾仅限于使用内容。 外部 Azure AD B2B 来宾可以查看应用、仪表板、报表，导出数据以及为仪表板和报表创建电子邮件订阅。 他们无法访问工作区或发布自己的内容。 但这些限制不适用于通过[允许外部来宾用户编辑和管理组织中的内容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能获取访问权限的来宾用户。

* 对于通过[允许外部来宾用户编辑和管理组织中的内容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能启用的来宾用户，某些体验可能不可用。 他们需要使用 Power BI 服务 Web UI 来更新或发布报表，包括为上传 Power BI Desktop 文件获取数据。  不支持以下体验：
    * 从 Power BI Desktop 直接向 Power BI 服务发布
    * 来宾用户不能使用 Power BI Desktop 连接 Power BI 服务中的服务数据集
    * 绑定到 Office 365 组的经典工作区：
        * 来宾用户无法创建或成为这些工作区的管理员
        * 来宾用户可以是成员
    * 对于工作区访问列表，不支持发送临时邀请
    * 不支持来宾用户使用 Power BI Publisher for Excel
    * 来宾用户不能安装 Power BI Gateway，也不能将它连接到组织
    * 来宾用户不能安装发布到整个组织的应用
    * 来宾用户不能使用、创建、更新或安装组织内容包
    * 来宾用户不能使用“在 Excel 中分析”
    * 无法在评论中 @mentioned 来宾用户
    * 来宾用户不能使用订阅
    * 使用此功能的来宾用户应具有工作或学校帐户。 使用个人帐户的来宾用户会因登录限制受到更多限制。

* 此功能当前不可用于 Power BI SharePoint Online 报表 Web 部件。

* 有一些 Active Directory 设置可以限制外部来宾用户在整个组织范围内可以执行的操作。 同时适用于你的 Power BI 环境。 以下文档探讨的设置为：
    * [管理外部协作设置](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [允许或阻止向特定组织中的 B2B 用户发送邀请](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>后续步骤

有关详细信息（包括行级别安全性的工作方式），请查看白皮书：[使用 Azure AD B2B 将 Power BI 内容分发给外部来宾用户](https://aka.ms/powerbi-b2b-whitepaper)。

若要了解 Azure AD B2B，请参阅[什么是 Azure AD B2B 协作？](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/)。

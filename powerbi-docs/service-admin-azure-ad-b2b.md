---
title: 使用 Azure AD B2B 将内容分发给外部来宾用户
description: Power BI 与 Azure Active Directory 企业到企业 (Azure AD B2B) 集成后，即可将 Power BI 内容安全地分发给组织外的来宾用户。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 7e76f03a3795976aebd1480dc77a579c9245ed9e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282048"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>使用 Azure AD B2B 将 Power BI 内容分发给外部来宾用户

Power BI 与 Azure Active Directory 企业到企业 (Azure AD B2B) 集成，便于你将 Power BI 内容安全分发给组织外的来宾用户，同时仍能继续控制内部数据。

## <a name="enable-access"></a>启用访问权限

邀请来宾用户前，请务必先在 Power BI 管理门户中启用[导出和共享设置](service-admin-portal.md#export-and-sharing-settings)功能。

## <a name="who-can-you-invite"></a>可以邀请哪些用户？

可邀请使用任意电子邮件地址（包括个人帐户，如 gmail.com、outlook.com 和 hotmail.com）的来宾用户。 在 Azure AD B2B 中，这些地址称为“社交标识”。

## <a name="invite-guest-users"></a>邀请来宾用户

只有在首次邀请外部来宾用户加入组织时，才需要发送邀请。 邀请用户的方法有两种：计划内邀请和临时邀请。

### <a name="planned-invites"></a>计划性邀请

如果确定要邀请哪些用户，请使用计划内邀请。 可使用 Azure 门户或 PowerShell 发送邀请。 只有租户管理员才能邀请用户。

若要在 Azure 门户中发送邀请，请按以下步骤操作。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“Azure Active Directory”。

1. 在“管理”下，依次转到“用户” > “所有用户” > “新建来宾用户”。

    ![Azure AD 门户 - 新来宾用户](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. 输入“电子邮件地址”和“个人消息”。

    ![Azure AD 门户 - 新来宾用户邀请消息](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. 选择“邀请”。

若要邀请多个来宾用户，请使用 PowerShell。 有关详细信息，请参阅 [Azure AD B2B 协作代码和 PowerShell 示例](/azure/active-directory/b2b/code-samples/)。

来宾用户需要在他们收到的电子邮件邀请中选择“开始”。 然后就会将该来宾用户添加到租户。

![来宾用户电子邮件邀请](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>临时邀请

通过共享 UI 将外部用户添加到仪表板或报表，或通过访问页面添加到应用，即可随时发出邀请。 以下示例说明邀请外部用户使用应用时要执行的操作。

![被添加到应用访问列表的外部用户](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

来宾用户会收到指明已与其共享应用的电子邮件。

![指示已与来宾用户共享应用的电子邮件](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

该来宾用户必须使用其组织电子邮件地址进行登录。 完成登录后，将提示他们接受邀请。 登录后，系统会将来宾用户重定向到对应的应用内容。 他们可以将链接设为书签，也可以保存电子邮件，以便稍后返回到应用。

## <a name="licensing"></a>许可

来宾用户必须拥有正确的授权，才能查看已共享的应用。 为此，可使用以下三种方法：使用 Power BI Premium；分配 Power BI Pro 许可证；或使用来宾用户的 Power BI Pro 许可证。

### <a name="use-power-bi-premium"></a>使用 Power BI Premium

如果你将应用工作区分配到 [Power BI Premium 容量](service-premium.md)，来宾用户无需获取 Power BI Pro 许可证，即可使用应用。 使用 Power BI Premium 时，应用还可以利用其他功能（如加快刷新速率、专用容量和大模型）。

![使用 Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>向来宾用户分配 Power BI Pro 许可证

如果你在租户内向来宾用户分配 Power BI Pro 许可证，来宾用户便能查看租户内容。

![分配租户的 Pro 许可证](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>来宾用户拥有自己的 Power BI Pro 许可证

在来宾用户的租户中已向来宾用户分配 Power BI Pro 许可证。

![来宾用户拥有自己的许可证](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>注意事项和限制

* 外部 B2B 来宾仅限于使用内容。 外部 B2B 来宾可以查看应用、仪表板、报表，导出数据以及为仪表板和报表创建电子邮件订阅。 他们无法访问工作区或发布自己的内容。

* 此功能目前不可用于 Power BI 移动应用。 在移动设备上，你可以在浏览器中查看使用 Azure AD B2B 共享的 Power BI 内容。

* 此功能当前不可用于 Power BI SharePoint Online 报表 Web 部件。

## <a name="next-steps"></a>后续步骤

有关详细信息（包括行级别安全性的工作方式），请查看白皮书：[使用 Azure AD B2B 将 Power BI 内容分发给外部来宾用户](https://aka.ms/powerbi-b2b-whitepaper)。

若要了解 Azure AD B2B，请参阅[什么是 Azure AD B2B 协作？](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/)。

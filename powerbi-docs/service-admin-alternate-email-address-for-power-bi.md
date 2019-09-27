---
title: 使用备用电子邮件地址
description: 使用备用电子邮件地址
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906653"
---
# <a name="use-an-alternate-email-address"></a>使用备用电子邮件地址

你在注册 Power BI 时提供电子邮件地址。 默认情况下，Power BI 使用此地址向你发送服务活动的最新动态。 例如，当有人向你发送共享邀请时，邀请就会发送到此地址。

在某些情况下，可能希望将这些电子邮件发送到备用电子邮件地址，而不是注册时使用的电子邮件地址。 本文介绍了如何在 Office 365 和 PowerShell 中指定备用地址。 此外，本文还介绍了 Azure Active Directory (Azure AD) 如何解析电子邮件地址。

> [!NOTE]
> 指定备用地址并不影响 Power BI 用来发送服务最新动态、新闻稿和其他促销通信的电子邮件地址。 这些通信始终发送到你注册 Power BI 时使用的电子邮件地址。

## <a name="use-office-365"></a>使用 Office 365

若要在 Office 365 中指定备用地址，请按以下步骤操作。

1. 打开 [Office 365 个人信息页](https://portal.office.com/account/#personalinfo)。 如果应用提示你使用用于 Power BI 的电子邮件地址和密码登录，请执行此操作。

1. 在左侧菜单栏上，选择“个人信息”。

1. 在“联系详细信息”部分中，选择“编辑”。

    如果无法编辑详细信息，表明你的电子邮件地址是由 Office 365 管理员管理。 若要更新电子邮件地址，请联系管理员。

    ![联系人详细信息](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. 在“备用电子邮件地址”字段中，输入希望 Office 365 用于 Power BI 更新的电子邮件地址。

## <a name="use-powershell"></a>使用 PowerShell

若要在 PowerShell 中指定备用地址，请运行 [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/) 命令。

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Azure AD 中的电子邮件地址解析

要捕获用于 Power BI 的 Azure AD 嵌入令牌，可使用以下三种不同类型的电子邮件地址之一：

* 与用户的 Azure AD 帐户关联的主电子邮件地址

* UserPrincipalName (UPN) 电子邮件地址

* “其他电子邮件地址”数组属性

Power BI 根据以下顺序选择要使用的电子邮件地址：

1. 如果 Azure AD 用户对象中有邮件属性，Power BI 便会对电子邮件地址使用此邮件属性。

1. 如果 UPN 电子邮件地址不是 **\*.onmicrosoft.com** 域电子邮件地址（“\@”符号后面的信息），Power BI 便会对电子邮件地址使用此邮件属性。

1. 如果 Azure AD 用户对象中有“其他电子邮件地址”数组属性，Power BI 便会使用此列表中的第一个电子邮件地址（因为此属性中可能有电子邮件地址列表）。

1. 如果不符合上述任一条件，Power BI 便会使用 UPN 地址。

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)
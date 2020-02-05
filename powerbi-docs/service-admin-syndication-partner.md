---
title: 无法将 Power BI 添加到 O365 合作伙伴
description: 无法将 Power BI 添加到 Office 365 联合合作伙伴。 联合模型是 Office 365 使用的购买模型。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: cc85fb07f50a42952e9b293908a797b1cbac023f
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "74958347"
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>无法将 Power BI 添加到 Office 365 合作伙伴订阅

使用 Office 365，公司可以转售与自己的解决方案捆绑集成的 Office 365，从而为最终客户提供单一联系人，方便其购买产品、处理帐务和获取支持。

若要随 Office 365 订阅一起获取 Power BI，建议联系合作伙伴。 如果合作伙伴暂不提供 Power BI，可采用其他方法。

## <a name="work-with-your-partner-to-purchase-power-bi"></a>联系合作伙伴以购买 Power BI

若要购买 Power BI Pro 或 Power BI Premium 订阅，请联系合作伙伴，以考虑可采用的方法：

* 合作伙伴同意将 Power BI 添加到其产品组合，以便你可以从他们那里购买。

* 合作伙伴能够将你转换到一种模型，在其中可以直接从 Microsoft 或从提供 Power BI 的其他合作伙伴购买 Power BI。

## <a name="purchase-from-microsoft-or-another-channel"></a>从 Microsoft 或其他渠道购买

可以直接从 Microsoft 或其他合作伙伴处购买 Power BI，具体视与合作伙伴的关系而定。 可以在 Microsoft 365 管理中心内验证能否添加 Power BI 订阅（必须有全局管理员或计费管理员角色的成员身份）。

1. 转到 [MIcrosoft 365 管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在左侧菜单中，打开“帐务”  ：

    * 如果看到“订阅”  ，可以直接从 Microsoft 获取服务，也可以与提供 Power BI 的其他合作伙伴联系。

        ![“帐务”下有“订阅”](media/service-admin-syndication-partner/billingsub.png)

    * 如果看不到“订阅”  ，便无法直接从 Microsoft 或其他合作伙伴处购买。

如果合作伙伴不提供 Power BI，且你无法直接从 Microsoft 或其他合作伙伴处购买，请考虑注册免费试用版。

## <a name="sign-up-for-a-free-trial"></a>注册免费试用版

可以注册 Power BI 免费试用版。 如果在试用期到期时未购买 Power BI Pro，仍有允许使用许多 Power BI 功能的免费许可证。 有关详细信息，请参阅[以个人身份注册 Power BI](service-self-service-signup-for-power-bi.md)。

### <a name="enable-ad-hoc-subscriptions"></a>启用临时订阅

默认情况下，个人注册（亦称为“临时订阅”）处于禁用状态。 在此情况下，如果尝试注册，会显示以下消息：你的 IT 部门已禁用注册 Microsoft Power BI  。

![“抱歉...”图像](media/service-admin-syndication-partner/sorry.png)

若要启用临时订阅，可以与合作伙伴联系并请求打开该功能。 如果你是租户管理员，并且知道如何使用 Azure Active Directory PowerShell 命令，可以自行启用临时订阅。 [Azure Active Directory Graph PowerShell](/powershell/azure/active-directory/install-adv2/)

1. 使用 Office 365 凭据登录 Azure Active Directory。 下面脚本的第一行提示你输入凭据。 第二行连接到 Azure Active Directory。

    ```powershell
    $msolcred = get-credential
    connect-msolservice -credential $msolcred
    ```

    ![输入凭据](media/service-admin-syndication-partner/aad-signin.png)

1. 登录后，立即运行下面的命令，以检查 `AllowAdHocSubscriptions` 的当前设置。

    ```powershell
    Get-MsolCompanyInformation
    ```

1. 运行下面的命令，以启用注册免费试用版。

    ```powershell
    Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

## <a name="next-steps"></a>后续步骤

[组织中的 Power BI 许可](service-admin-licensing-organization.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
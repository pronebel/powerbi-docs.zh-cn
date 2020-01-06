---
title: 组织中的 Power BI 许可
description: 了解 Power BI 中可用的不同许可证类型：免费许可、Power BI Pro 和 Power BI Premium。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 7a2cc9a1deb87e94c0887b1ae00174d6791cf712
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700018"
---
# <a name="power-bi-licensing-in-your-organization"></a>组织中的 Power BI 许可

[!INCLUDE [license-capabilities](includes/license-capabilities.md)]

本文从管理员角度重点介绍用户许可。

## <a name="manage-power-bi-pro-licenses"></a>管理 Power BI Pro 许可证

作为管理员，你可以购买和分配 Power BI Pro 许可证；可以为你的组织注册 Power BI Pro 试用版。 用户自己也可以注册 Power BI Pro 试用版。

### <a name="purchase-power-bi-pro-licenses"></a>购买 Power BI Pro 许可证

作为管理员，你可以通过 Microsoft Office 365 或已认证的 Microsoft 合作伙伴购买 Power BI Pro 许可证。 购买许可证后，你可以将它们分配给各个用户。 有关更多信息，请参阅[购买和分配 Power BI Pro 许可证](service-admin-purchasing-power-bi-pro.md)。

### <a name="power-bi-pro-license-expiration"></a>Power BI Pro 许可证过期

Power BI Pro 许可证过期后，还有一个宽限期。 对于批量购买的许可证，宽限期为 90 天。 如果是直接购买许可证，则宽限期为 30 天。

Power BI Pro 的订阅生命周期与 Office 365 相同。 有关详细信息，请参阅 [Office 365 商业版订阅过期时，我的数据和访问权限会发生什么变化？](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3)。

### <a name="power-bi-pro-trial-for-individuals"></a>面向个人的 Power BI Pro 试用版

你组织中的个人可以注册 Power BI Pro 试用版。 有关更多信息，请参阅[以个人身份注册 Power BI](service-self-service-signup-for-power-bi.md)。

自己申请享受 Power BI Pro 试用版功能的用户不会在 Microsoft 365 管理中心内显示为 Power BI Pro 试用版用户（他们显示为 Power BI 免费用户）。 但是，他们会在 Power BI 中管理存储页面上显示为 Power BI Pro 试用版用户。

### <a name="power-bi-pro-trial-for-organizations"></a>面向组织的 Power BI Pro 试用版

如果你希望获取 Power BI 试用版许可证并调配给组织中的多个用户使用而无需其分别接受试用条款，则可以以组织为单位注册 Power BI Pro 试用版。

在执行注册步骤之前，请记住以下几点：

* 要进行注册，你必须是 Office 365 [全局管理员或帐务管理员](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)角色中的一员。  

* 每个租户只能申请一个组织试用版。 这意味着如果有人已将 Power BI Pro 试用版应用到你的租户，则无法再次应用。 如果需要这方面的帮助，请联系 [Office 365 计费支持](https://support.office.microsoft.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b?CorrelationId=552bbf37-214f-4202-80cb-b94240dcd671)。

1. 导航到 [MIcrosoft 365 管理中心](https://portal.office.com/adminportal/home#/homepage)。

1. 在导航窗格中，选择“账单”，然后选择“订阅”   。

   ![计费和订阅](media/service-admin-licensing-organization/service-power-bi-pro-in-your-organization-05.png)

1. 选择右侧的“添加订阅”。 

   ![添加订阅](media/service-admin-licensing-organization/service-power-bi-pro-in-your-organization-06.png)

1. 在“其他计划”下，将鼠标悬停在 Power BI Pro 的省略号 (...) 上方，然后选择“开始免费试用”。   

   ![开始免费试用](media/service-admin-licensing-organization/service-power-bi-pro-in-your-organization-07.png) 

1. 在订单确认屏幕上，选择“立即试用”。 

1. 在订单签收上选择“继续”。 

现在，可以[在 Office 365 中分配许可证](https://support.office.com/article/assign-licenses-to-users-in-office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)。

## <a name="manage-power-bi-free-licenses"></a>管理 Power BI 免费许可证

组织中的用户可以通过两种不同方式获取 Power BI 免费许可证的使用权：

* 你可在 Microsoft 365 管理中心内为其分配 Power BI 许可证。

* 如果用户[以个人身份注册 Power BI](service-self-service-signup-for-power-bi.md)，则会自动为其分配免费许可证。

### <a name="requesting-and-assigning-free-licenses"></a>请求和分配免费许可证

如果你计划集中管理许可证请求和分配，请首先检查你是否已拥有不受限制的 Power BI（免费）许可证块。

在某个用户首次以个人身份注册 Power BI 之后此许可证块可用。 在该过程中，此许可证块会附加到你的组织，并自动为进行注册的用户分配一个许可证。

1. 在 Microsoft 365 管理中心的“账单” > “许可证”下，检查是否为“无限制”    。

    ![无限制的免费许可证块](media/service-admin-licensing-organization/unlimited-licenses.png)

1. 如果此块可用，你现在可以[在 Office 365 中分配许可证](https://support.office.com/article/assign-licenses-to-users-in-office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)。 如果此块不可用，你有两种选择：

    * 让你组织内的某个成员单独先注册，以触发无限制块的创建。

    * 转到下一个步骤，注册固定数量的许可证。

如果不受限制的 Power BI（免费）许可证块不可用且你不想让用户单独进行注册，请按照此步骤操作。

1. 导航到 [MIcrosoft 365 管理中心](https://portal.office.com/admin/default.aspx)。

1. 在导航窗格中，选择“账单” > “订阅”   。

1. 选择右侧的“添加订阅 +”。 

1. 在“其他计划”下，将鼠标悬停在 Power BI（免费）的省略号 (...)  上方，然后选择“立即购买”  。 

    ![立即购买 - Power BI（免费）](media/service-admin-licensing-organization/buy-powerbi-free.png)

1. 输入要添加的许可证数，并选择  “立即结帐”或“添加到购物车”  。

1. 输入结帐流程中的所需信息。

    使用此方法时不会进行实际购买，不过你需要输入信用卡信息以进行计帐或选择开票。

1. 现在，你可以[在 Office 365 中分配许可证](https://support.office.com/article/assign-licenses-to-users-in-office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)。

1. 如果以后你决定要添加更多许可证，则可以返回到“添加订阅”，然后对 Power BI（免费）选择“更改许可证数量”   。

    ![更改许可证数量](media/service-admin-licensing-organization/change-license-quantity.png)

### <a name="enable-or-disable-individual-user-sign-up-in-azure-active-directory"></a>在 Azure Active Directory 中启用或禁用个人用户注册

作为管理员，你可以通过 Azure Active Directory (AAD) 选择启用或禁用个人用户注册。 本文中下面部分内容向你展示了如何使用 PowerShell 命令管理注册设定。 有关 Azure PowerShell 的详细信息，请参阅 [ Azure PowerShell 概述](/powershell/azure/overview)。

Azure AD 设置中用于控制注册功能的是 AllowAdHocSubscriptions 命令  。 在大多数租户环境中，该处值设定的是 true，这意味着它处于启用状态  。 如果你是通过合作伙伴获取 Power BI，则此处可能被设置为 false ，这意味着它处于禁用状态  。 如果你将该设置从 true 更改为 false，则会阻止组织中的新用户以个人身份进行注册   。 在设置更改之前注册 Power BI 的用户将保留其许可证。 请注意，设置为“false”，具有 Power BI（免费）许可证的用户仍可以注册个人 Power BI Pro 试用版  。

1. 使用 Microsoft 365 凭据登录 Azure Active Directory。 以下 PowerShell 脚本中的第一行会提示你输入凭据。 第二行连接到 Azure Active Directory。

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Azure Active Directory 登录](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. 登录之后，运行以下命令以查看当前是如何配置租户环境的。 （请注意，下面的“fl”使用字母“l”，而不是数字 1。）

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions 
    ```
1. 运行以下命令启用 ($true) 或禁用 ($false) AllowAdHocSubscriptions  。

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

> [!NOTE]
> AllowAdHocSubscriptions 标记用于控制组织中的若干用户权限，其中包括用户注册 Azure 权限管理服务的功能。 更改此标志会影响所有这些功能。

## <a name="next-steps"></a>后续步骤

[自助注册 Power BI](service-self-service-signup-for-power-bi.md)  

[购买和分配 Power BI Pro 许可证](service-admin-purchasing-power-bi-pro.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

---
title: 启用或禁用自助注册和购买
description: 如何通知管理员关闭用户注册 Power BI 和购买许可证的功能。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 561d8b6cd0e17e885ced984315a04376400a2a58
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81447501"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>启用或禁用自助注册和购买

在大多数组织中，自助注册是默认启用的。 组织中的个人用户都可以使用其工作或学校帐户注册 Power BI。 如果用户尝试使用需要 Pro 的功能，则还可以选择直接购买 Power BI Pro 许可证。 管理员可以决定是启用还是禁用自助注册， 还可以控制组织中的用户是否可以进行自助购买来获得自己的许可证。

> [!NOTE]
>如果已通过 Microsoft 云解决方案提供商 (CSP) 获取 Power BI，则可能会禁用该设置以阻止用户以个人身份注册。 你的云解决方案提供商也可以充当组织的全局管理员，要求你联系他们帮助更改此设置。
>
>

可以使用 PowerShell 命令更改控制自助注册和采购的设置。 有两种设置可用于控制组织中的用户是否可以进行自助注册或进行自助购买。

- 如果要禁用所有自助注册，请使用 Azure AD PowerShell 命令更改 Azure Active Directory 中名为 AllowAdHocSubscriptions 的设置  。 请按照本文中的步骤[启用或禁用自助注册](#enable-or-disable-self-service-signup)。 此选项将禁用所有 Microsoft 基于云的应用和服务的自助注册  。

- 如果要阻止用户购买自己的 Pro 许可证，请使用 MSCommerce PowerShell 命令更改“AllowSelfServicePurchase”设置  。 此设置允许关闭特定产品的自助购买。 请按照本文中的步骤[启用或禁用自用购买 Power BI Pro 许可证](#enable-or-disable-self-service-purchase)。

## <a name="enable-or-disable-self-service-signup"></a>启用或禁用自助注册

如果启用了自助注册，则 AllowAdHocSubscriptions 的值为 true   。 让我们来看看将此设置更改为 false 时会发生什么情况  ：

- 如果将该设置从 true 更改为 false，则会阻止组织中的新用户以个人身份进行注册。 在更改设置之前注册 Power BI 的任何用户将保留其许可证。

- 如果将设置更改为 false，则已有 Power BI（免费）许可证的用户仍可注册个人 Power BI Pro 试用版。

- 管理员需要将所有 Power BI 许可证分配给需要许可证的新用户。

### <a name="before-you-begin"></a>开始之前

这些步骤使用 Azure Active Directory PowerShell 命令更改“AllowAdHocSubscriptions”设置的值  。 必须安装 Azure AD PowerShell 模块才能使用这些命令。 有关使用 PowerShell 的详细信息，请参阅 [Windows PowerShell 入门](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)。

若要安装 Azure AD 模块，请以管理员身份启动 Windows PowerShell。 确保本地执行策略允许运行脚本。 如果遇到问题，请参阅 [PowerShell 执行策略](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)，了解如何更改本地策略。

运行以下命令以安装 Azure AD 模块：

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>更改自助注册策略

在 PowerShell 中，运行以下命令以连接到 Azure AD：

```powershell
Connect-MsolService
```

在登录对话框中输入管理员凭据，完成可能需要的任何双重身份验证。 验证后，将返回到 PowerShell 窗口。

若要查看当前设置，请运行以下命令。 使用“fl”开关将输出传输到格式化列表。

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

若要更改当前设置，请运行以下命令：

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

运行此命令后，将对所有用户禁用自助注册。 若要重新启用，请再次运行此命令并将该值设置为 $true。

## <a name="enable-or-disable-self-service-purchase"></a>启用或禁用自助购买

如果启用了自助购买，则 AllowSelfServicePurchase 的值为 true   。 让我们来看看将此设置更改为 false 时会发生什么情况  ：

- 如果将设置从 true 更改为 false，则会禁止组织中的用户购买自己的 Power BI Pro 许可证。 在更改设置之前购买许可证的任何用户将保留其许可证。

- 如果将设置更改为 false，则具有 Power BI（免费）许可证的用户无法获取个人 Power BI Pro 许可证。 

- 管理员需要为需要 Pro 许可证的所有用户分配该许可证。

### <a name="before-you-begin"></a>开始之前

这些步骤使用 MSCommerce PowerShell 命令更改“AllowSelfServicePurchase”设置的值  。 必须安装 MSCommerce PowerShell 模块才能使用这些命令。 有关使用 PowerShell 的详细信息，请参阅 [Windows PowerShell 入门](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)。

若要安装 MSCommerce 模块，请以管理员身份启动 Windows PowerShell。 确保本地执行策略允许运行脚本。 如果遇到问题，请参阅 [PowerShell 执行策略](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)，了解如何更改本地策略。

运行以下命令以安装 MSCommerce 模块：

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>更改自助注册策略

在 PowerShell 中，运行以下命令进行连接：

```powershell
Connect-MSCommerce
```

在登录对话框中输入管理员凭据，完成可能需要的任何双重身份验证。 验证后，PowerShell 窗口将显示连接成功。

若要查看当前设置，请运行以下命令。 为了防止文本被截断，请使用“fl”开关将输出传送到格式化列表。

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

可以通过提供 ProductId，禁用允许自助购买单独产品的设置  。 若要更改 Power BI 服务的当前设置，运行以下命令：

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

运行此命令后，将对所有用户禁用自助购买 Power BI。 若要重新启用，请再次运行此命令并将该值设置为 $true。

## <a name="next-steps"></a>后续步骤

有关 Power BI 中自助购买和 Power Platform 其余部分的详细信息，请参阅以下文章：

- [自助购买常见问题解答](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [将 AllowSelfServicePurchase 用于 MSCommerce PowerShell 模块](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)

---
title: Power BI 应用配置设置
description: 如何使用 MDM 工具自定义 Power BI 的行为
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 07/14/2020
ms.openlocfilehash: a867c0480e9c0762d1594016fb807cab8261c14c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414590"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>使用移动设备管理 (MDM) 工具远程配置 Power BI 应用

适用于 iOS 和 Android 的 Power BI 移动版应用支持应用设置，移动设备管理 (MDM) 服务（例如 Intune）的管理员可通过应用设置自定义应用的行为。

Power BI 移动版应用支持以下配置方案：

* 报表服务器配置（iOS 和 Android）
* 数据保护设置（iOS 和 Android）
* 禁用单一登录（iOS 和 Android）
* 交互设置（iOS 和 Android）

## <a name="report-server-configuration-ios-and-android"></a>报表服务器配置（iOS 和 Android）

适用于 iOS 和 Android 的 Power BI 应用允许管理员将报表服务器配置远程“推送”到注册设备。

| 密钥 | 类型 | 说明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | 字符串 | 报表服务器 URL。<br><br>应以 http/https 开头。|
| com.microsoft.powerbi.mobile.ServerUsername | 字符串 | [可选]<br><br>要用于连接服务器的用户名。<br><br>如果不存在此项，应用将提示用户键入用于连接的用户名。|
| com.microsoft.powerbi.mobile.ServerDisplayName | 字符串 | [可选]<br><br>默认值为“报表服务器”<br><br>应用中用于表示服务器的易记名称。 |
| com.microsoft.powerbi.mobile.OverrideServerDetails | 布尔 | [可选]<br><br>默认值为 True。 设置为 True 时，它会替代移动设备中已有的任何报表服务器定义。 已删除已配置的现有服务器。 将“替代”设置为 True 还可防止用户删除该配置。<br><br>设置为“False”将添加推送值，并保留任何现有设置。 如果已在移动应用中配置相同的服务器 URL，则应用将按原样保留该配置。 应用不会要求用户重新验证同一服务器。 |

## <a name="data-protection-settings-ios-and-android"></a>数据保护设置（iOS 和 Android）

适用于 iOS 和 Android 的 Power BI 移动应用使管理员能够自定义安全和隐私设置的默认配置。 对于 iOS，可强制用户在访问 Power BI 移动应用时提供其 Face ID、Touch ID 或密码。 对于 Android，可以强制用户使用生物识别身份验证（指纹 ID）。

| 密钥 | 类型 | 说明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | 布尔 | 默认值为 False。 <br><br>用户可能需要使用生物识别技术，例如 TouchID、FaceID (iOS) 或指纹 ID (Android)，来访问其设备上的应用。 需要时，除身份验证外还会使用生物识别技术。<br><br>如果使用应用保护策略，Microsoft 建议禁用此设置来防止双重访问提示。 |

>[!NOTE]
>将仅在支持生物识别身份验证的 Android 设备上应用数据保护设置。

## <a name="disable-single-sign-on-ios-and-android"></a>禁用单一登录（iOS 和 Android）

默认情况下，Power BI 移动应用会将用户必须提供用户名和密码的次数降至最低，从而为单个用户提供方便的单一登录体验。 这种单一登录行为假定设备是用户的个人设备，并且只有一个用户在使用该设备和设备上的应用。

管理员可以在应用配置文件中打开 DisableSingleSignOn 设置，远程配置应用以禁用单一登录，并在用户登录时明确询问他们的密码。

这是仅针对管理员的设置（可通过远程配置进行配置）。 最终用户无法更改此设置。

| 密钥 | 类型 | 说明 |
|---|---|---|
| com.microsoft.powerbi.mobile.DisableSingleSignOn | 布尔 | 默认值为 False。<br><br>用户注销后，应用将不会重复使用现有凭据，但会要求下一位用户提供密码才能进行身份验证并连接到 Power BI 服务。
 |

## <a name="interaction-settings-ios-and-android"></a>交互设置（iOS 和 Android）

适用于 iOS 和 Android 的 Power BI 应用使管理员能够在确定需要跨组织中的用户组更改默认交互设置时配置交互设置。

>[!NOTE]
>并非所有设备目前都支持所有交互。 若要查看当前跨设备可用性的图表，请参阅[配置报表交互设置](mobile-app-interaction-settings.md)。

| 密钥 | 类型 | 值 | 说明 |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | 字符串 |  <nobr>单击</nobr><br><nobr>双击</nobr> | 配置在点击视觉对象时，是否还会同时选择数据点。 |
| com.microsoft.powerbi.mobile.EnableMultiSelect | 布尔 |  <nobr>True</nobr><br><nobr>False</nobr> | 配置在点击数据点时，是会替换当前选定内容还是添加到当前选定内容中。 |
| com.microsoft.powerbi.mobile.RefreshAction | 字符串 |  <nobr>下拉以刷新</nobr><br>按钮 | 配置用户是使用按钮刷新报表还是应使用下拉刷新。 |
| com.microsoft.powerbi.mobile.FooterAppearance | 字符串 |  已停靠<br>动态 | 配置是将报表页脚停靠在报表底部还是自动隐藏。 |

## <a name="deploying-app-configuration-settings"></a>部署应用配置设置

以下是创建应用配置策略所需的步骤。 创建配置策略后，可以将其设置分配给用户组。

1. 连接 MDM 工具。
2. 创建并命名新的应用配置策略。
3. 选择要将此应用配置策略分发到的用户。
4. 为想要推送给用户的设置创建键值对。

借助 Intune 门户，管理员可以通过应用配置策略轻松地将这些设置部署到 Power BI 应用。 但是，任何 MDM 提供商都受到支持。 如果未使用 Intune，则需要参考有关如何部署这些设置的 MDM 文档。

## <a name="next-steps"></a>后续步骤

* 从 [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) 和 [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409) 获取 Power BI 移动版
* 关注 [Twitter 上的 @MSPowerBI](https://twitter.com/MSPowerBI)
* 加入 [Power BI 社区](https://community.powerbi.com/)的对话
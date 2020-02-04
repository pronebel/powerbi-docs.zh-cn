---
title: Power BI 应用配置设置
description: 如何使用 MDM 工具自定义 Power BI 的行为
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: painbar
ms.openlocfilehash: 58b2f96b069815af448352b3b54875dc4d6b27ee
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538258"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>使用移动设备管理 (MDM) 工具远程配置 Power BI 应用

适用于 iOS 和 Android 的 Power BI 移动版应用支持应用设置，移动设备管理 (MDM) 服务（例如 Intune）的管理员可通过应用设置自定义应用的行为。

Power BI 移动版应用支持以下配置方案：

* 报表服务器配置（iOS 和 Android）
* 数据保护设置（iOS 和 Android）
* 交互设置 (Android)

## <a name="report-server-configuration-ios-and-android"></a>报表服务器配置（iOS 和 Android）

适用于 iOS 和 Android 的 Power BI 应用允许管理员将报表服务器配置远程“推送”到注册设备。

| 密钥 | 类型 | 说明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | 字符串 | 报表服务器 URL。<br><br>应以 http/https 开头。|
| com.microsoft.powerbi.mobile.ServerUsername | 字符串 | [可选]<br><br>要用于连接服务器的用户名。<br><br>如果不存在此项，应用将提示用户键入用于连接的用户名。|
| com.microsoft.powerbi.mobile.ServerDisplayName | 字符串 | [可选]<br><br>默认值为“报表服务器”<br><br>应用中用于表示服务器的易记名称。 |
| com.microsoft.powerbi.mobile.OverrideServerDetails | 布尔 | [可选]<br><br>默认值为 True。 设置为 True 时，它会替代移动设备中已有的任何报表服务器定义。 已删除已配置的现有服务器。 将“替代”设置为 True 还可防止用户删除该配置。<br><br>设置为“False”将添加推送值，并保留任何现有设置。 如果已在移动应用中配置相同的服务器 URL，则应用将按原样保留该配置。 应用不会要求用户重新验证同一服务器。 |

## <a name="data-protection-settings-ios"></a>数据保护设置 (iOS)

适用于 iOS 和 Android 的 Power BI 应用使管理员能够自定义安全和隐私设置的默认配置。 可强制用户在访问 Power BI 应用时提供其 Face ID、Touch ID 或密码。

| 密钥 | 类型 | 说明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | 布尔 | 默认值为 False。 <br><br>用户可能需要使用生物识别技术（例如 Touch ID 或 Face ID）来访问其设备上的应用。 需要时，除身份验证外还会使用生物识别技术。<br><br>如果使用应用保护策略，Microsoft 建议禁用此设置来防止双重访问提示。 |

## <a name="interaction-settings-android"></a>交互设置 (Android)

适用于 Android 的 Power BI 应用使管理员能够在确定需要跨组织中的用户组更改默认交互设置时配置交互设置。 

| 密钥 | 类型 | 值 | 说明 |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | 字符串 |  <nobr>单击</nobr><br><nobr>双击</nobr> | 配置点击视觉对象是否还会同时选择数据点。 |
| ccom.microsoft.powerbi.mobile.RefreshAction | 字符串 |  <nobr>下拉以刷新</nobr><br>按钮 | 配置用户是使用按钮刷新报表还是下拉以刷新。 |
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

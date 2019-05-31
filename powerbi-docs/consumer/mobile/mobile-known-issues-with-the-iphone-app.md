---
title: 修复 iOS 移动应用中的“通信故障”- Power BI
description: 如果你看到消息“遇到了通信故障。 该故障可能与 Wi-Fi 连接的代理设置有关。”，那么本文可能会有所帮助。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: mshenhav
ms.openlocfilehash: 9e487f4305b663028714cbe45ab76abaaa4a6db9
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61135656"
---
# <a name="fixing-communication-failures-in-ios-mobile-apps---power-bi"></a>修复 iOS 移动应用中的“通信故障”- Power BI

| ![iPhone](./media/mobile-known-issues-with-the-iphone-app/iphone-logo-50-px.png) | ![iPad](./media/mobile-known-issues-with-the-iphone-app/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone |iPad |

## <a name="we-encountered-communication-failures"></a>“我们遇到了通信故障”
“我们遇到了通信故障。 该故障可能与 Wi-Fi 连接的代理设置有关。 切换到其他 Wi-Fi 连接可能解决此问题。”

如果你的 iPhone 或 iPad Internet 连接需要配置强制的显式 HTTP 代理（手动或自动），则可能会看到此消息。 在此情况下，Power BI 应用无法在你的 iOS 设备上运行。

### <a name="workaround"></a>解决方法
将 iPhone 或 iPad 切换到不需要显式 HTTP 代理设置的另一个连接（即配置为 HTTP 代理处于关闭状态的连接）。

## <a name="other-issues"></a>是否有其他问题？
请尝试在 [Power BI 社区](http://community.powerbi.com/)中提问


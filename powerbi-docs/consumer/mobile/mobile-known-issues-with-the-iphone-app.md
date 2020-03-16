---
title: 修复 iOS 移动应用中的“通信故障”- Power BI
description: 如果你看到消息“遇到了通信故障。 该故障可能与 Wi-Fi 连接的代理设置有关。”，那么本文可能会有所帮助。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 0162d78fd4358f415ac52ea70bd3460d3c28b722
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114914"
---
# <a name="fixing-communication-failures-in-ios-mobile-apps---power-bi"></a>修复 iOS 移动应用中的“通信故障”- Power BI

| ![iPhone](./media/mobile-known-issues-with-the-iphone-app/iphone-logo-50-px.png) | ![iPad](./media/mobile-known-issues-with-the-iphone-app/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone |iPad |

## <a name="we-encountered-communication-failures"></a>“我们遇到了通信故障”
“我们遇到了通信故障。 该故障可能与 Wi-Fi 连接的代理设置有关。 切换到其他 Wi-Fi 连接可能会解决此问题。”

如果你的 iPhone 或 iPad Internet 连接需要配置强制的显式 HTTP 代理（手动或自动），则可能会看到此消息。 在这种情况下，Power BI 应用无法在 iOS 设备上运行。

### <a name="workaround"></a>解决方法
将 iPhone 或 iPad 切换到不需要显式 HTTP 代理设置的另一个连接（即将“HTTP 代理”配置为“关”的连接）。

## <a name="other-issues"></a>是否有其他问题？
请尝试在 [Power BI 社区](https://community.powerbi.com/)中提问


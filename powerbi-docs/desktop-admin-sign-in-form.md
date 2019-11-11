---
title: 管理员如何管理 Power BI Desktop 登录窗体
description: 了解打开 Power BI Desktop 时如何管理初始登录窗体。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: b1ab5188ba8f5ccf54589d359f6f8ced1ada3060
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878863"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>管理员如何管理 Power BI Desktop 登录窗体
首次启动 Power BI Desktop 时，将会看到登录窗体。 若要继续操作，可以填写信息或登录 Power BI。 管理员可以使用注册表项来管理此窗体。 

![Power BI Desktop 的初始登录窗体](media/desktop-admin-sign-in-form/sign-in-form.png)

管理员可以使用以下注册表项禁用登录窗体。 还可以使用全局策略将其推送到整个组织。

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
也可以尝试使用以下密钥，根据某些客户的配置，该密钥已成功：

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

值为 0 将禁用此对话框。




更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


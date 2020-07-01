---
title: 管理员如何管理 Power BI Desktop 登录窗体
description: 了解打开 Power BI Desktop 时如何管理初始登录窗体。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 49b7d1129f73e146db1e34b1ec7d39a176cb37ed
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85228921"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>管理员：管理 Power BI Desktop 登录窗体
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


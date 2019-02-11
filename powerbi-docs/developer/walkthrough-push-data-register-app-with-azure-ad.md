---
title: 将应用注册到 Azure AD
description: 演练 - 将数据推送到数据集 - 将应用注册到 Azure AD
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: a3154a7b74d196f3c0aa2969e7c25bf56000a662
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762021"
---
# <a name="step-1-register-an-app-with-azure-ad"></a>步骤 1：将应用注册到 Azure AD

本文是[将数据推送到数据集](walkthrough-push-data.md)的分步演练的一部分。

将数据推送到 Power BI 数据集的第一步是在 Azure AD 中注册你的应用。 你需要先执行此操作以获取**客户端 ID**，它会在 Azure AD 中标识你的 Web 应用。 没有**客户端 ID**，Azure AD 则无法对你的 Web 应用进行身份验证。

> **注意**：注册 [Power BI](create-an-azure-active-directory-tenant.md) 的应用前，需要注册 Power BI。

以下是在 Azure AD 中注册应用的步骤。

## <a name="register-an-app-in-azure-ad"></a>在 Azure AD 中注册应用

1. 请转到 dev.powerbi.com/apps。
2. 单击**使用现有帐户登录**，并登录 Power BI 帐户。
3. 输入**应用名称**，例如“推送数据应用示例”。
4. 对于**应用类型**，选择**本机应用**。
5. 输入重定向 URL，例如 https://login.live.com/oauth20_desktop.srf。 对于**本机客户端应用**，重定向 URI 可为 **Azure AD** 提供有关其将进行身份验证的特定应用程序的更多详细信息。 客户端应用的标准 URI 为 https://login.live.com/oauth20_desktop.srf。
6. 对于**选择要访问的 API**，请选择**读写所有数据集**。 有关所有 Power BI 应用权限的信息，请参阅 [Power BI 权限](power-bi-permissions.md)。
7. 单击**注册应用**，并保存生成的**客户端 ID**。 **客户端 ID** 用于识别 Azure AD 中的应用。

以下是**注册适用于 Power BI 的应用程序**页面应有的外观：

![注册应用](media/walkthrough-push-data-register-app-with-azure-ad/powerbi-developer-sample-register-app.png)

接下来的步骤展示如何[获取身份验证访问令牌](walkthrough-push-data-get-token.md)。

[下一步 >](walkthrough-push-data-get-token.md)

## <a name="next-steps"></a>后续步骤

[注册 Power BI](create-an-azure-active-directory-tenant.md)  
[获取身份验证访问令牌](walkthrough-push-data-get-token.md)  
[演练：将数据推送到数据集](walkthrough-push-data.md)  
[注册应用程序](register-app.md)  
[Power BI REST API 概述](overview-of-power-bi-rest-api.md)  

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
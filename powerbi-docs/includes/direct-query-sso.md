---
title: 包含文件
description: 包含文件
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: ed87101fe7f5fadd24594d53bbd0ffb6f029faa4
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "90012924"
---
## <a name="single-sign-on"></a>单一登录

将 Azure SQL DirectQuery 数据集发布到服务后，可以使用 Azure Active Directory (Azure AD) OAuth2 为最终用户启用单一登录 (SSO)。

若要启用 SSO，请转到数据集的设置，打开“数据源”选项卡，然后选中“SSO”框。 

![配置 Azure SQL DQ 对话框](media/direct-query-sso/sso-dialog.png)

启用“SSO”选项后，如果用户访问基于数据源生成的报表，则 Power BI 会在查询中将这些用户的已经过身份验证的 Azure AD 凭据发送到 Azure SQL 数据库或数据仓库。 此选项使 Power BI 可以遵守在数据源级别配置的安全设置。

SSO 选项针对使用此数据源的所有数据集生效。 它不影响用于导入方案的身份验证方法。

> [!Note]
> 不支持 Azure 多重身份验证 (MFA)。 想要在 DirectQuery 中使用 SSO 的用户必须免除 MFA。

---
title: Power BI 移动 Windows 应用中的单一登录
description: 阅读有关 Power BI 移动 Windows 应用中的单一登录 (SSO) 的内容。 SSO 意味着，使用单个用户帐户仅登录一次即可访问业务所需的所有应用程序和资源。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: mshenhav
ms.openlocfilehash: fdbdebacc2ae41cdfa8296eb6b0c06e52f149cac
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290949"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Power BI 移动 Windows 应用中的单一登录

阅读有关 Power BI 移动 Windows 应用中的单一登录 (SSO) 的内容。 SSO 意味着，使用单个用户帐户仅登录一次即可访问业务所需的所有应用程序和资源。 登录后可以访问所有这些应用程序，而无需再次进行身份验证。 

由于 Power BI Windows 应用已集成到 Azure Active Directory 中，因此使用主组织帐户既可以登录到已加入域的设备，也可以登录到 Power BI 服务。 如果要在 Windows Phone 上查看 Power BI，请确保在设备设置中将用于 Power BI 的帐户配置为工作或学校帐户。  

仅为 Windows Azure Active Directory 管理的 Windows 设备启用 SSO。 

## <a name="sign-in-with-sso"></a>使用 SSO 登录

为了简化登录过程，在首次安装应用时，应用会自动尝试使用 SSO 对 Power BI 服务进行身份验证。 仅当此过程不成功时，应用才会要求你提供用于 Power BI 的凭据。  

如果你已使用适用于 Windows 的 Power BI 移动应用，则在升级到新版本的应用时还可以使用 SSO。 注销应用，关闭并重新打开它。 重新打开应用时，它会自动尝试使用当前的 Windows 凭据对 Power BI 服务进行身份验证。 

如果你不希望使用当前的 Windows 活动会话凭据登录到 Power BI，则只需转到“设置”，注销，然后使用其他凭据登录。 
 
## <a name="next-steps"></a>后续步骤

- [适用于 Windows 10 的 Power BI 移动应用入门](mobile-windows-10-phone-app-get-started.md)
- 是否有任何问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)


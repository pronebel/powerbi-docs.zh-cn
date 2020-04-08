---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621566"
---
服务主体是一种身份验证方法，可用于让 Azure AD 应用程序访问 Power BI 服务内容和 API。

在 Azure Active Directory (Azure AD) 应用程序创建后，[服务主体对象](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)也随之创建。 借助服务主体对象（亦称为“服务主体”  ），Azure AD 可以对应用程序进行身份验证。 经过身份验证后，应用程序可以访问 Azure AD 租户资源。

为了进行身份验证，服务主体使用 Azure AD 应用程序的应用程序 ID  ，以及下列项之一：
* 应用程序密码
* 证书
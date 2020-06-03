---
title: 服务主体概述
description: 服务主体概述
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 8482278d9054228dedafb6bd1b37368f5a4b5dce
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315738"
---
服务主体是一种身份验证方法，可用于让 Azure AD 应用程序访问 Power BI 服务内容和 API。

在 Azure Active Directory (Azure AD) 应用程序创建后，[服务主体对象](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)也随之创建。 借助服务主体对象（亦称为“服务主体”  ），Azure AD 可以对应用程序进行身份验证。 经过身份验证后，应用程序可以访问 Azure AD 租户资源。

为了进行身份验证，服务主体使用 Azure AD 应用程序的应用程序 ID  ，以及下列项之一：

* 应用程序密码
* 证书
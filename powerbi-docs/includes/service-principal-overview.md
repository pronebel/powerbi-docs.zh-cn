---
title: 服务主体概述
description: 服务主体概述
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 6086185fb671b9f418ef2ec070b762020fbe8f75
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989484"
---
服务主体是一种身份验证方法，可用于让 Azure AD 应用程序访问 Power BI 服务内容和 API。

在 Azure Active Directory (Azure AD) 应用程序创建后，[服务主体对象](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)也随之创建。 借助服务主体对象（亦称为“服务主体”  ），Azure AD 可以对应用程序进行身份验证。 经过身份验证后，应用程序可以访问 Azure AD 租户资源。

为了进行身份验证，服务主体使用 Azure AD 应用程序的应用程序 ID  ，以及下列项之一：

* 应用程序密码
* 证书
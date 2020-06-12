---
title: 服务主体限制
description: 服务主体限制
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: 8e50a529bfd398a4075ebf049ee4aec1bcf48b4d
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315740"
---
## <a name="considerations-and-limitations"></a>注意事项和限制

* 服务主体仅适用于[新的工作区](../collaborate-share/service-create-the-new-workspaces.md)。
* 使用服务主体时，不支持“我的工作区”。
* 移动到生产环境时，需要专用容量。
* 无法使用服务主体登录 Power BI 门户。
* 在 Power BI 管理门户的开发人员设置中启用服务主体需要 Power BI 管理权限。
* 无法使用服务主体[为组织应用程序嵌入内容](../developer/embedded/embed-sample-for-your-organization.md)。
* 不支持[数据流](../transform-model/service-dataflows-overview.md)管理。
* 服务主体目前不支持任何管理员 API。
* 使用带有 [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) 数据源的服务主体时，服务主体本身必须具有 Azure Analysis Services 实例权限。 使用包含服务主体的安全组来实现此目的，这不起作用。
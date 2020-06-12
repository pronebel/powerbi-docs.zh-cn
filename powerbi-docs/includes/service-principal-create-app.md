---
title: 服务主体创建应用
description: 服务主体创建应用
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315739"
---
1. 登录 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜索“应用程序注册”，然后单击“应用程序注册”链接。

    ![Azure 应用程序注册](media/embedded-service-principal/azure-app-registration.png)

3. 单击“新建注册”。

    ![新建注册](media/embedded-service-principal/new-registration.png)

4. 填写所需信息：
    * **名称** - 输入应用程序名称
    * **受支持的帐户类型** - 选择受支持的帐户类型
    * （可选）**重定向 URI** - 视需要输入 URI

5. 单击“注册”。

6. 注册后，可以从“概览”选项卡中获取“应用程序 ID”。复制并保存“应用程序 ID”，以供日后使用。

    ![应用程序 ID](media/embedded-service-principal/application-id.png)
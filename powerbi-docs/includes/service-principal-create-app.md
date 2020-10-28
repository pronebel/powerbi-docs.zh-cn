---
title: 服务主体创建应用
description: 服务主体创建应用
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 80886eab6de6c125d0361b326f5d31d2b3bb35e5
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524504"
---
1. 登录 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜索“应用程序注册”，然后单击“应用程序注册”链接。

    ![Azure 应用程序注册](media/embedded-service-principal/azure-app-registration.png)

3. 单击“新建注册”。

    ![新建注册](media/embedded-service-principal/new-registration.png)

4. 填写所需信息：
    * **名称** - 输入应用程序名称
    * **受支持的帐户类型** - 选择受支持的帐户类型
    * （可选） **重定向 URI** - 视需要输入 URI

5. 单击“注册”。

6. 注册后，可以从“概览”选项卡中获取“应用程序 ID”。复制并保存“应用程序 ID”，以供日后使用。

    ![展示在“概述”选项卡中获取应用程序 ID 的位置的屏幕截图。](media/embedded-service-principal/application-id.png)
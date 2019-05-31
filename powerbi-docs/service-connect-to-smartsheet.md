---
title: 使用 Power BI 连接到 Smartsheet
description: 适用于 Power BI 的 Smartsheet
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 841201aa87139b9630d6fc076d57109fb2b09804
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578918"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>使用 Power BI 连接到 Smartsheet
本文逐步拉取你从使用 Power BI 模板应用你的 Smartsheet 帐户的数据。 Smartsheet 提供了协作和文件共享的简单平台。 适用于 Power BI 的 Smartsheet 模板应用提供了一个仪表板、 报表和显示的你的 Smartsheet 帐户概述的数据集。 此外可以使用[Power BI Desktop](desktop-connect-to-data.md)直接连接到您的帐户中的各个工作表。 

你已安装模板应用后，可以更改仪表板和报表。 然后您可以将其分发到同事的应用为你的组织中。

连接到[Smartsheet 模板应用](https://app.powerbi.com/groups/me/getdata/services/smartsheet)适用于 Power BI。

>[!NOTE]
>使用 Smartsheet 管理员帐户是首选的连接并加载 Power BI 模板应用，因为它具有额外的访问权限。

## <a name="how-to-connect"></a>如何连接

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. 选择**Smartsheet** \> **立即获取**。
4. 在中**安装此 Power BI 应用？** 选择**安装**。
4. 在中**应用程序**窗格中，选择**Smartsheet**磁贴。

    ![Power BI 的 Smartsheet 应用磁贴](media/service-connect-to-smartsheet/power-bi-smartsheet-tile.png)

6. 在中**开始使用新的应用程序**，选择**将数据连接**。

    ![开始使用新应用](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

4. 对于身份验证方法，选择 **oAuth2 \> 登录**。
   
   出现提示时，输入 Smartsheet 凭据，然后按照身份验证过程进行操作。
   
   ![Smartsheet 凭据](media/service-connect-to-smartsheet/creds.png)
   
   ![Smartsheet 登录](media/service-connect-to-smartsheet/creds2.png)

5. Power BI 导入数据后，将打开 Smartsheet 仪表板。
   
   ![Smartsheet 仪表板](media/service-connect-to-smartsheet/power-bi-smartsheet-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>修改和分发您的应用程序

已安装 Smartsheet 模板应用。 这意味着还创建了 Smartsheet 应用工作区。 在工作区中，更改报表和仪表板中，，然后将其作为分发*应用*给你的组织中的同事。 

1. 若要查看左侧的导航栏中的新的 Smartsheet 工作区中，所有内容，请选择**工作区** > **Smartsheet**。 

    ![在左侧的导航窗格中的 Smartsheet 工作区](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace.png)

    此视图是工作区内容列表。 在右上角中，您会看到**更新应用**。 如果你已准备好将应用到你的同事分发，这是将开始位置。 

    ![Smartsheet 内容列表](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace-content.png)

2. 选择**报表**并**数据集**若要查看工作区中的其他元素。

    阅读有关[分发应用](service-create-distribute-apps.md)给你的同事。

## <a name="whats-included"></a>包含的内容
Smartsheet 模板应用的 Power BI 包括你的 Smartsheet 帐户，例如工作区数的概述报表，和工作表，已进行修改后等。管理员用户也在其系统，如顶层工作表创建者中看到大约用户的一些信息。  

若要直接连接到你帐户中的单独工作表，可以使用 [Power BI Desktop](desktop-connect-to-data.md) 中的 Smartsheet 连接器。  

## <a name="next-steps"></a>后续步骤

* [在 Power BI 中创建新的工作区](service-create-the-new-workspaces.md)
* [在 Power BI 中安装并使用应用](consumer/end-user-apps.md)
* [连接到外部服务的 Power BI 应用](service-connect-to-services.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)
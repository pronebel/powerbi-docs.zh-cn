---
title: 教程：连接到包含 Power BI 的 GitHub 存储库
description: 在本教程中，使用 Power BI 连接到 GitHub 服务中的真实数据，Power BI 即会自动创建仪表板和报表。
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578630"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>教程：连接到包含 Power BI 的 GitHub 存储库
在本教程中，使用 Power BI 连接到 GitHub 服务中的真实数据，Power BI 即会自动创建仪表板和报表。 连接到 Power BI 内容公共存储库 (也称为*存储库*)，并查看问题的答案：有多少人参与编辑 Power BI 公共内容？ 谁贡献最多？ 一周中哪天的贡献最大？ 和其他问题。 

![Power BI 中的 GitHub 报表](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

在本教程中，将完成以下步骤：

> [!div class="checklist"]
> * 如果还没有 GitHub 帐户，请注册一个帐户 
> * 登录 Power BI 帐户或进行注册（如果还没有）
> * 打开 Power BI 服务
> * 查找 GitHub 应用
> * 输入 Power BI 公共 GitHub 存储库的信息
> * 查看具有 GitHub 数据的仪表板和报表
> * 通过删除应用来清理资源

如果未注册 Power BI，请[免费注册](https://app.powerbi.com/signupredirect?pbi_source=web)后再进行操作。

## <a name="prerequisites"></a>先决条件

要完成本教程，需要一个 GitHub 帐户（如果还没有）。 

- 注册[的 GitHub 帐户](https://docs.microsoft.com/contribute/get-started-setup-github)。


## <a name="how-to-connect"></a>如何连接
1. 登录 Power BI 服务 (https://app.powerbi.com) 。 
2. 在左侧导航窗格中，选择“应用”，然后选择“获取应用”   。
   
   ![Power BI 获取应用](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. 选择**应用程序**，类型**GitHub**在搜索框中 >**立即获取**。
   
   ![Power BI 获取 GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. 在中**安装此 Power BI 应用？** 选择**安装**。
5. 在中**新的应用程序已准备**，选择**转到应用**。
6. 在中**开始使用新的应用程序**，选择**将数据连接**。

    ![开始使用新应用](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. 输入该存储库的存储库名称和存储库所有者。 此存储库的 URL 为 https://github.com/MicrosoftDocs/powerbi-docs，因此存储库所有者为 MicrosoftDocs，而存储库为 powerbi-docs     。 
   
    ![Power BI GitHub 存储库名称](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. 输入创建的 GitHub 凭据。 如果已在浏览器中登录到 GitHub，Power BI 可能会跳过此步骤。 

6. 有关**身份验证方法**，保留**oAuth2**选\>**登录**。

7. 按照 GitHub 验证界面。 向 Power BI 授予访问 GitHub 数据的权限。
   
   之后，Power BI 即可连接到 GitHub 和数据。  数据会每天刷新一次。

8. Power BI 导入数据后，您将看到新的 GitHub 工作区的内容。 
9. 在左侧的导航栏中选择工作区名称旁边的箭头。 你看到工作区包含一个仪表板和报表。 

    ![在左侧的导航窗格中的应用](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. 选择仪表板名称旁边的省略号 （...） >**重命名**> 类型**GitHub 仪表板**。
 
    ![Power BI GitHub 磁贴](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. 选择“全局导航”图标将左侧导航窗格最小化，以获得更多空间。

    ![“全局导航”图标](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. 选择 GitHub 仪表板。
    
    GitHub 仪表板包含实时数据，因此您看到的值可能不同。

    ![Power BI 中的 GitHub 仪表板](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>提问

1. 将光标置于**提出你的数据有关的问题**。 Power BI 提供了**问题入门**。 

1. 选择**多少用户是否有**。
 
    ![多少用户存在](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. 在中间**多少**并**用户是否有**，类型**拉取每个请求**。 

     Power BI 将创建条形图，显示的每个人的拉取请求数。

    ![每个用户的拉取请求数存在](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. 选择固定后，将其固定到仪表板，然后**退出问答**。

## <a name="view-the-github-report"></a>查看 GitHub 报表 

1. 在 GitHub 仪表板中，选择柱形图**拉取请求按月**以打开相关的报表。

    ![按月柱形图的拉取请求](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. 选择中的用户名**由用户总的拉取请求**图表。 在此示例中，我们看到自己的时间的大多数都是 2 月。

    ![Power BI GitHub 报表突出显示](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. 选择“打孔卡片”选项卡查看报表的下一页  。 
 
    ![Power BI GitHub 报表打孔卡片](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    星期二下午 3 显然是最常用的时间和日期的星期几*提交*，当用户签入其工作。

## <a name="clean-up-resources"></a>清理资源

现在，完成本教程后，可删除 GitHub 应用。 

1. 在左侧导航栏中选择“应用”  。
2. 将鼠标悬停在 GitHub 磁贴上，然后选择“删除”垃圾箱  。

    ![删除 GitHub 应用](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>后续步骤

在本教程中，已连接到 GitHub 公共存储库并已获取 Power BI 在仪表板和报表中进行格式化的数据。 你已通过浏览仪表板和报表回答了一些数据相关问题。 现在可深入了解如何连接到其他服务，例如 Salesforce、Microsoft Dynamics 和 Google Analytics。 
 
> [!div class="nextstepaction"]
> [连接到所使用的联机服务](service-connect-to-services.md)



---
title: 在 Power BI 中发布应用
description: 了解如何发布新应用，这是仪表板和报表使用内置导航的集合。
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941552"
---
# <a name="publish-an-app-in-power-bi"></a>在 Power BI 中发布应用

在 Power BI 中，你可以创建官方打包内容，然后将其分发到为广泛的受众*应用*。 在应用工作区中创建应用，可在工作区中与同事协作处理 Power BI 内容  。 然后可以将已完成的应用发布给组织中的许多人员。 

![Power BI 应用](media/service-create-distribute-apps/power-bi-new-apps.png)

业务用户通常需要多个 Power BI 仪表板和报表，才能经营自己的业务。 使用 Power BI 应用，可以创建仪表板和报表集合并将这些应用发布到整个组织或发布到特定人员或组。 对于报表创建者或管理员，应用能使管理这些集合的权限变得更轻松。

业务用户在多种不同的方式获取你的应用：

- 找到并从 Microsoft AppSource 安装您的应用程序
- 您可以向他们发送直接链接。
- 如果 Power BI 管理员已授予权限，则可将这些应用自动安装到同事的 Power BI 帐户中。

可以使用其自己内置的导航栏中，创建的应用，以便用户可以轻松找到如何使用你的内容。 不能修改应用的内容。 它们可以与其进行交互的 Power BI 服务中，或一个移动应用--筛选、 突出显示，和对数据本身进行排序。 他们将自动获得更新，你可以控制数据刷新的频率。 详细了解[业务用户的应用体验](consumer/end-user-apps.md)。

## <a name="licenses-for-apps"></a>应用许可证
若要创建或更新应用程序，需要一个 Power BI Pro 许可证。 应用程序*使用者*，有两个选项。

* 选项 1：所有业务用户需要 Power BI Pro 许可证才能查看应用  。 
* 选项 2：如果你的应用工作区驻留在 Power BI Premium 容量，你的组织中的免费用户可以查看应用内容。 请阅读[什么是 Power BI Premium？](service-premium.md)了解详细信息。

## <a name="publish-your-app"></a>发布应用
工作区中的仪表板和报表准备就绪后，选择要发布的仪表板和报表，然后将其作为应用发布。 

1. 在工作区列表视图中，决定哪些仪表板和报表所需**包括在应用中**。

     ![选择要发布的仪表板](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     如果您选择不包含具有相关的仪表板的报表，您将看到该报表旁边的警告。 您还可以发布应用程序中，但相关的仪表板不会有来自该报表的磁贴。

     ![关于相关仪表板的警告](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. 选择**发布应用**开始创建和发布应用程序从工作区的右上角的按钮。
   
     ![发布应用](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. 上**安装程序**，填写名称和描述以帮助用户查找应用。 可以设置要对其进行个性化设置的主题颜色。 此外可以将链接添加到支持站点。
   
     ![构建您的应用程序](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. 上**导航**，选择要作为应用程序的一部分进行发布的内容。 然后，添加应用程序导航栏中，组织中部分的内容。 请参阅[设计您的应用程序的导航体验](#design-the-navigation-experience-for-your-app)在本文中有关详细信息。
   
     ![应用导航](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. 上**访问**，决定有权访问应用的人员。 
    - 在中[经典的工作区](service-create-workspaces.md)： 你的组织、 特定人员或 Azure Active Directory (AAD) 安全组中的每个人。
    - 在中[体验的新工作区](service-create-the-new-workspaces.md)： 特定人员、 AAD 安全组和通讯组列表和 Office 365 组。

6. 如果您具有权限，可以为收件人自动安装该应用程序。 Power BI 管理员可以在 Power BI 管理门户中启用此设置。 详细了解[自动安装应用](#automatically-install-apps-for-end-users)这篇文章中。

     ![应用权限](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. 当选择**发布应用**，请参阅确认它已准备好发布的消息。 在中**共享此应用**对话框中，您可以复制直接链接到此应用程序的 URL。
   
     ![应用完成](media/service-create-distribute-apps/power-bi-apps-success.png)

您可以发送给的人员的直接链接已与你共享它，或用户可通过转到在应用选项卡上找到您的应用程序**下载并浏览更多应用从 AppSource**。 详细了解[业务用户的应用体验](consumer/end-user-apps.md)。

## <a name="change-your-published-app"></a>更改已发布的应用
发布应用后，你可能想要更改或更新它。 很容易进行更新，如果您的管理员或新的应用工作区中的成员。 

1. 打开对应于应用的应用工作区。 
   
     ![打开工作区](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. 对仪表板或报表进行任何所需的更改。
 
     应用工作区为临时区域，因此应用中所做更改在再次发布前不会生效。 这样就方便进行更改，而不会影响已发布的应用。  
 
    > [!IMPORTANT]
    > 如果删除报表和更新应用程序，即使将报表添加回应用程序，应用使用者会丢失所有自定义项的书签、 注释等。  
 
3. 返回到应用工作区列表的内容，然后选择**更新应用**在右上角。
   
1. 更新**安装程序**，**导航**，并**权限**，如果需要然后选择**更新应用**。
   
应用的发布对象会自动看到更新版应用。 

## <a name="design-the-navigation-experience-for-your-app"></a>设计您的应用程序的导航体验
**新的导航生成器**选项可用于构建您的应用程序自定义导航。 自定义导航便于用户查找和应用程序中使用的内容。 现有的应用具有此选项处于关闭状态和新应用程序默认为在上的选项。

关闭该选项后，可以选择**应用登陆页面**可以**特定内容**，例如仪表板或报表或选择**None**显示基本的列表向用户的内容。

当您启用**新的导航生成器**，可以设计自定义导航。 默认情况下所有报表、 仪表板和应用程序中包含的 Excel 工作簿作为简单列表都列出。 

![应用导航](media/service-create-distribute-apps/power-bi-apps-navigation.png)

您可以进一步自定义通过应用导航：
* 重新排序的项使用向上 / 向下箭头。 
* 重命名中的项**报告详细信息**，**仪表板的详细信息**，并**工作簿的详细信息**。
* 隐藏某些项从导航栏中。
* 使用**新建**选项可添加**部分**到组相关内容。
* 使用**新建**选项可添加**链接**到外部资源到左侧导航栏中。 

当您将添加**链接**，在**链接的详细信息**可以选择其中的链接将打开。 默认情况下在中打开链接**当前选项卡**，但你可以选择**新选项卡**，或**内容区域**。 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>使用新导航生成器选项的注意事项
下面是使用新的导航生成器时，需要注意的常规事项：
* 报表页在应用程序的导航区域中显示为可展开部分
* 如果关闭新导航生成器然后发布或更新您的应用程序，您会丢失所做的自定义项。 例如，部分、 排序、 链接和导航项的自定义名称将全部丢失。

当将链接添加到您的应用程序导航和选择内容区域选项：
* 请确保可以嵌入链接。 某些服务会阻止 Power BI 等第三方站点中其内容的嵌入。
* 不支持在其他工作区中嵌入 Power BI 服务内容，如报表或仪表板。 
* 嵌入 Power BI 报表服务器通过其本机内容嵌入 URL 从本地部署的内容。 使用中的步骤[创建 Power BI 报表服务器 URL](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url)获取的 URL。 注意，将应用常规身份验证规则，以便查看内容需要与本地服务器的 VPN 连接。 
* 安全警告在嵌入内容的顶部显示，以指示无法在 Power BI 中的内容。



## <a name="automatically-install-apps-for-end-users"></a>自动为最终用户安装应用
如果管理员为你提供权限，则可以自动安装应用程序*推送*到最终用户。 此推送功能，可以更轻松地分发到合适的人员或组正确的应用。 最终用户的应用内容列表中，您的应用程序将自动出现。 它们无需从 Microsoft AppSource 中查找，或单击安装链接。 请参阅管理员如何启用[将应用推送给最终用户](service-admin-portal.md#push-apps-to-end-users)Power BI 管理员门户文章中。

### <a name="how-to-push-an-app-automatically-to-end-users"></a>如何将应用自动推送到最终用户
管理员分配权限后，可通过一个新选项来自动安装应用  。 在选中的复选框并选中**发布应用**(或**更新应用**)、 应用程序推送到所有用户或组中定义**权限**上的应用程序的部分**访问**选项卡。

![启用推送应用功能](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>用户如何获取推送到它们的应用
将应用推送后，它在其应用程序列表中自动显示。 这样一来，你可以精选应用该特定用户或工作角色在你的组织需要唾手可得。

![启用推送应用功能](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>自动安装应用的注意事项
下面是将应用推送给最终用户时需要注意的事项：

* 自动向用户安装应用可能需要一些时间。 大多数应用程序将立即为用户，但推送应用功能的安装可能需要时间。  这取决于应用中的项数和授予访问权限的人员数。 我们建议在下班期间推送应用，那时的时间充足，用户也不需要使用应用。 请先与多位用户验证，再发送有关应用可用性的广泛沟通。

* 刷新浏览器。 用户可能需要刷新或关闭和重新打开浏览器才能看到“应用”列表中的推送应用。

* 如果用户未立即看到应用程序列表中的应用，它们应刷新或关闭并重新打开其浏览器。

* 尽量不要让用户不知所措。 请注意不要推送太多应用，以便用户了解预先安装的应用是有用的。 最好控制可以将应用推送给最终用户的人员，以协调计时。 建立一个用于获取应用推送给最终用户在组织中的联系点。

* 尚未接受邀请的来宾用户不获取自动安装的应用。  

## <a name="unpublish-an-app"></a>取消发布应用
应用工作区的任何成员都可以取消发布应用。

>[!IMPORTANT]
>取消发布应用后，应用用户将丢失其自定义设置。 他们会丢失任何个人书签、 注释或应用程序中的内容与关联的订阅。 仅在必须删除应用时才取消发布该应用。
> 
> 

* 在应用工作区中，依次选择右上角的省略号（“...”  ）和“取消发布应用”  。
  
     ![取消发布应用](media/service-create-distribute-apps/power-bi-app-unpublish.png)

此操作会为已向其发布该应用的所有人员卸载此应用，而且他们也不再有权访问此应用。 此操作不会删除应用工作区或其内容。

## <a name="view-your-published-app"></a>查看已发布的应用

当应用使用者打开您的应用程序时，他们会看到创建，而不是标准的 Power BI 左侧的导航窗格中的导航。 报表和仪表板中已定义的节列出了应用导航。 它还列出了每个报表中的单个页而不是，只是报表名称。

![导航的应用](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>后续步骤
* [创建应用工作区](service-create-workspaces.md)
* [在 Power BI 中安装并使用应用](consumer/end-user-apps.md)
* [适用于外部服务的 Power BI 应用](service-connect-to-services.md)
* [Power BI 管理门户](https://docs.microsoft.com/power-bi/service-admin-portal)
* 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

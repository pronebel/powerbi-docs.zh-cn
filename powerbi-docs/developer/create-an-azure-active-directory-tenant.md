---
title: 创建要用于 Power BI 的 Azure Active Directory 租户
description: 了解如何使用 Power BI REST API 新建用于自定义应用程序的 Azure Active Directory (Azure AD) 租户。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/30/2017
ms.openlocfilehash: eb5befbfc5e96867f0f4cf27eafd62829fb488f4
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762136"
---
# <a name="create-an-azure-active-directory-tenant-to-use-with-power-bi"></a>创建要用于 Power BI 的 Azure Active Directory 租户

了解如何使用 Power BI REST API 新建用于自定义应用程序的 Azure Active Directory (Azure AD) 租户。

在 Azure Active Directory 中，一个租户代表一个组织。 它是 Azure AD 服务的一个专用实例，组织在注册 Azure、 Microsoft Intune 或 Office 365 等 Microsoft 云服务时收到并拥有它。 各个 Azure AD 租户各不相同，相互独立。

拥有 Azure AD 租户后，可以定义应用程序并分配权限，以便应用程序使用 Power BI REST API。

你的组织可能已拥有你可用于应用程序的 Azure AD 租户。 你的应用程序可以使用该租户，你也可以专门为你的应用程序创建新租户。 本文讨论如何创建新租户。

## <a name="create-an-azure-active-directory-tenant"></a>创建 Azure Active Directory 租户

若要将 Power BI 集成到自定义应用程序内，需要在 Azure AD 中定义应用程序。 若要执行此操作，需要一个 Azure AD 内的目录。 这是你的租户。 如果组织未使用 Power BI 或 Office 365，因此没有租户，则[需要创建一个新租户](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant)。 如果不希望你的应用程序与组织的租户混合，可能也需要创建一个新租户。 这可以使内容保持独立。

或者，你可能只是出于测试目的创建租户。

若要创建新的 Azure AD 租户，请执行以下操作。

1. 浏览到 [Azure 门户](https://portal.azure.com)使用具备 Azure 订阅的帐户登录。

2. 选择“加号图标 (+)”并搜索“Azure Active Directory”。

    ![加号图标 (+)](media/create-an-azure-active-directory-tenant/new-directory.png)

3. 在搜索结果中选择“Azure Active Directory”。

    ![AAD 搜索](media/create-an-azure-active-directory-tenant/new-directory2.png)

4. 选择“创建”。

5. 提供“组织名”和“初始域名”。 然后选择“创建”。 这将创建你的目录。

    ![组织和域](media/create-an-azure-active-directory-tenant/organization-and-domain.png)

   > [!NOTE]
   > 初始域将是 onmicrosoft.com 的一部分。 以后可以添加其他域名。 可以向租户目录分配多个域。

6. 目录创建操作完成后，选择信息框来管理新目录。

你的目录现已创建。 接下来，我们要向这个租户添加用户。

## <a name="create-some-users-in-your-azure-active-directory-tenant"></a>在你的 Azure Active Directory 租户中创建一些用户

我们已有目录，现在请创建至少两个用户。 一个将作为租户的全局管理员，另一个作为用于嵌入的主用户。 将其视为服务帐户。

1. 在 Azure 门户中，确保位于 Azure Active Directory 浮出视窗上。

    ![](media/create-an-azure-active-directory-tenant/aad-flyout.png)

    如果不是，从左侧服务栏选择 Azure Active Directory 图标。

    ![](media/create-an-azure-active-directory-tenant/aad-service.png)
2. 在“管理”下选择“用户和组”。

    ![](media/create-an-azure-active-directory-tenant/users-and-groups.png)
3. 选择“所有用户”，然后选择“+ 新建用户”。
4. 为此用户提供名称和用户名。 这将是租户的全局管理员。 还需把“目录角色”更改为“全局管理员”。 还可以显示临时密码。 完成后，选择“创建”。

    ![](media/create-an-azure-active-directory-tenant/global-admin.png)

5. 需要为租户中的一名普通用户再执行一次相同的操作。 这可能还会用于你的主嵌入帐户。 本次将“目录角色”保留为“用户”。 请务必记下密码。 然后选择“创建”。

    ![](media/create-an-azure-active-directory-tenant/pbiembed-user.png)
6. 用你在步骤 5 中创建的用户帐户注册 Power BI。 要执行此操作，需转到 [powerbi.com](https://powerbi.microsoft.com/get-started/)选择“Power BI - 云协作和共享”下的“免费试用”。

    ![](media/create-an-azure-active-directory-tenant/try-powerbi-free.png)

    注册时，系统将提示你免费试用 Power BI Pro 60 天。 可以选择此项，成为一名 Pro 用户。 如果需要，现在也可以开始开发嵌入解决方案。

   > [!NOTE]
   > 请确保使用指定给用户帐户的电子邮件地址进行注册。

## <a name="next-steps"></a>后续步骤

现在，你已有 Azure AD 租户，可以使用此租户来测试 Power BI 中的项，并且（或者）进一步在应用程序中嵌入 Power BI 仪表板和报表。 有关如何嵌入项的详细信息，请参阅[如何嵌入 Power BI 仪表板、报表和磁贴](embedding-content.md)。

[什么是 Azure AD 目录？](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)  
[如何获取 Azure Active Directory 租户](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant)  

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
---
title: 创建新工作区的 Power BI
description: 了解如何创建新的工作区的仪表板、 报表和分页的报表旨在为你的组织提供关键指标的集合。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d0c0781ea5d3864f1cf3627cd42d53cca632102d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61141846"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>在 Power BI 中创建新的工作区

Power BI 将引入新的工作区体验。 工作区仍在与创建集合的仪表板、 报表和分页的报表的同事进行协作的地方。 然后可以绑定到该集合*应用*并将其分发到整个组织或特定人员或组。 

下面将会不同。 在新工作区，你可以：

- 将工作区角色分配给用户组：安全组、通讯组列表、Office 365 组和个人。
- 在 Power BI 中创建工作区，而无需创建 Office 365 组。
- 使用更精细的工作区角色在工作区中实现更灵活的权限管理。

> [!NOTE]
> 若要强制实施行级别安全性 (RLS) 的 Power BI Pro 用户浏览的工作区中的内容，请继续使用[经典的工作区](service-create-workspaces.md)。 选择**成员只能查看 Power BI 内容**选项。 或者，将 Power BI 应用发布到这些用户，或使用共享来分发内容。 即将推出的查看者角色将启用此方案的新工作区体验工作区在将来。

有关详细背景信息，请参阅[的新工作区](service-new-workspaces.md)一文。

## <a name="create-one-of-the-new-app-workspaces"></a>创建一个新的应用工作区

1. 首先，创建应用工作区。 选择“工作区”   > “创建应用工作区”  。
   
     ![创建应用工作区](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. 除非你选择自动创建的已升级的工作区，**还原为经典注册表**。
   
     ![新的工作区体验](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     如果选择**还原为经典注册表**，创建基于 Office 365 组工作区。 如果需要使用此选项**成员只能查看 Power BI 内容**选项为工作区成员强制实施行级别安全性 (RLS)。

2. 为工作区命名。 如果名称不可用，对其进行编辑以拿出一个唯一的名称。
   
     适用于工作区的应用将与工作区具有相同的名称和图标。
   
1. 下面是一些可以为你的工作区设置的可选项：

    上传**工作区图像**。 文件可以是.png 或.jpg 格式。 文件大小必须小于 45 KB。
    
    [添加**联系人列表**](#workspace-contact-list)。 默认情况下，工作区管理员是的联系人。 
    
    [指定**工作区的 OneDrive** ](#workspace-onedrive)通过键入只是现有 Office 365 组，而不是 URL 的名称。 现在此工作区可以使用该 Office 365 组的文件存储位置。 

    ![指定的 OneDrive 位置](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    若要将分配到工作区**专用容量**，然后在**Premium**选项卡上选择**专用容量**。
     
    ![专用容量](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. 选择**保存**。

    Power BI 创建工作区并将其打开。 可以在你所属的工作区列表中看到它。 

## <a name="workspace-contact-list"></a>工作区的联系人列表

新的工作区联系人列表，可指定哪些用户接收通知的工作区中发生的问题。 默认情况下，任何用户或组指定为工作区通知管理员，但您可以自定义列表。 用户或联系人列表中列出的组将显示在用户界面 (UI) 来帮助用户获得到的工作区相关的帮助。

1. 访问新**联系人列表**中有两种设置：

    在中**创建工作区**窗格首次创建时。

    在左侧的导航窗格中，选择箭头旁边**工作区**，选择工作区名称旁边的省略号 （...） >**工作区设置**。 **设置**窗格将打开。

    ![工作区设置](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. 下**高级** > **联系人列表**，接受默认值，**工作区管理员**，或添加您自己的列表**特定用户或组**. 
3. 选择**保存**。

## <a name="workspace-onedrive"></a>Workspace OneDrive

工作区的 OneDrive 功能允许你配置 Office 365 组的 SharePoint 文档库中文件存储可供工作区的用户。 首次创建 Power BI 的组。 

Power BI 不同步用户或组配置为具有与 Office 365 组成员身份的工作区访问的权限。 最佳做法是为提供相同的 Office 365 组，该组设置 Office 365 中配置其文件存储[访问工作区](#give-access-to-your-workspace)。 然后通过管理 Office 365 组的成员身份管理工作区访问权限。 

1. 访问新**工作区的 OneDrive**中有两种设置：

    在中**创建工作区**窗格首次创建时。

    在左侧的导航窗格中，选择箭头旁边**工作区**，选择工作区名称旁边的省略号 （...） >**工作区设置**。 **设置**窗格将打开。

    ![工作区设置](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. 下**高级** > **工作区的 OneDrive**，键入前面创建的 Office 365 组的名称。 Power BI 会自动将提取组的 OneDrive。

    ![指定的 OneDrive 位置](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. 选择**保存**。

### <a name="access-the-workspace-onedrive-location"></a>访问工作区的 OneDrive 位置

配置 OneDrive 位置后，你可以从工作区中的几个不同的位置获取到它：

- 选择**工作区** > *工作区名称*> 旁边的省略号 ( **...** ) 菜单 >**文件**。 

    ![工作区文件位置](media/service-new-workspaces/power-bi-new-workspace-files.png)

- 选择省略号 ( **...** ) 在工作区的右上角菜单 >**文件**。

    ![工作区文件位置](media/service-new-workspaces/power-bi-new-workspace-files-2.png)
    
- 在中**获取数据** > **文件**体验。 **OneDrive-企业**条目是你自己的 OneDrive for Business。 第二个 OneDrive 是已添加。

    ![工作区中文件的位置-获取数据](media/service-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-app-workspace"></a>将内容添加到应用工作区

创建新的工作区体验工作区后，就可以向其添加内容。 将内容添加新的和经典工作区中是类似。 使用创建按钮或使用获取数据以将内容添加到工作区。

1. 在中**欢迎使用**屏幕为新的工作区，你可以添加内容。 

    ![新工作区欢迎屏幕](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. 例如，选择“示例” > “客户盈利率示例”   。

> [!NOTE]
> 在新工作区中不能使用组织内容包或第三方内容包。 应用程序可用于所有第三方内容包你以前使用过。 如果您需要继续使用内容包，请使用经典的工作区。 内容包不推荐使用，因此它是最佳做法以改为使用应用程序。

在应用工作区内容列表中查看内容时，应用工作区名称列为所有者。

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>连接到新的工作区中的第三方服务

在新工作区体验中，我们正在做出改变以专注于应用  。 适用于第三方服务的应用使用户可以轻松地从他们使用的服务（如 Microsoft Dynamics CRM、Salesforce 或 Google Analytics）中获取数据。

在新的工作区体验中，您不能创建或使用组织内容包。 但可以使用为连接到第三方服务提供的应用，或要求内部团队为当前正在使用的任何内容包提供应用。 

## <a name="give-access-to-your-workspace"></a>授予对你的工作区访问权限

1. 在工作区内容列表中，因为你是管理员看到新的操作，请**访问**。

    ![工作区内容列表](media/service-create-the-new-workspaces/power-bi-workspace-content-list.png)

1. 选择“访问”  。

1. 将安全组、通讯组列表、Office 365 组或个人作为成员、参与者或管理员添加到这些工作区中。 有关不同角色的说明，请参阅[新工作区中的角色](service-new-workspaces.md#roles-in-the-new-workspaces)。

    ![在工作区中添加成员、管理员、参与者](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. 选择“添加” > “关闭”   。


## <a name="distribute-an-app"></a>分发应用

如果你想要官方将内容分发到大量受众的组织中，可以从你的工作区发布应用。  内容准备就绪后，选择的仪表板和报表要发布的虚拟机和模板，然后将其作为发布*应用*。 可从每个工作区创建一个应用。

阅读有关[发布应用程序从新工作区](service-create-distribute-apps.md)

## <a name="next-steps"></a>后续步骤
* 阅读有关[组织中的新工作区体验 Power BI 中的工作](service-new-workspaces.md)
* [创建经典的工作区](service-create-workspaces.md)
* [在 Power BI 中发布应用程序从新工作区](service-create-distribute-apps.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

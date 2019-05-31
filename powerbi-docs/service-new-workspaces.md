---
title: 组织中的新工作区的 Power BI 的工作
description: 了解有关新工作区，是仪表板和报表旨在为你的组织提供关键指标的集合。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9f5dfaa5a23ae46fef131a52355531b5fbde3051
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100694"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>组织在 Power BI 中的新工作区中工作

 *工作区*个位置进行协作与同事创建仪表板、 报表和分页的报表的集合。 新的工作区体验可帮助您更好地管理对内容的访问。 本文介绍了新的工作区，以及如何，它们不同于经典的工作区。  与经典的工作区，可以仍使用它们来创建和分发应用。 阅读有关如何[创建新的工作区体验](service-create-the-new-workspaces.md)。

新的工作区体验已达到正式版 (GA)，现在是默认工作区。 您仍可以继续创建和使用[经典的工作区](service-create-workspaces.md)基于 Office 365 组。 

> [!NOTE]
> 若要强制实施行级别安全性 (RLS) 的 Power BI Pro 用户浏览的工作区中的内容，请继续使用[经典的工作区](service-create-workspaces.md)。 选择**成员只能查看 Power BI 内容**选项。 或者，将 Power BI 应用发布到这些用户，或使用共享来分发内容。 即将推出的查看者角色将启用此方案的新工作区体验工作区在将来。

对于新工作区，你可以：

- 将工作区角色分配给用户组：安全组、通讯组列表、Office 365 组和个人。
- 在 Power BI 中创建工作区，而无需创建 Office 365 组。
- 使用更精细的工作区角色在工作区中实现更灵活的权限管理。

创建一个新工作区时，无需创建关联的基础 Office 365 组。 所有工作区管理操作都在 Power BI 中进行，而不是在 Office 365 中。 在新的工作区体验中，现在可以添加工作区访问列表中的 Office 365 组才可继续管理用户访问通过 Office 365 组的内容。

## <a name="administering-new-workspace-experience-workspaces"></a>管理新的工作区体验工作区
对于新的工作区体验工作区的管理是现在，在 Power BI 中，Power BI 管理员决定在组织中的哪些人员可以创建工作区。 他们还可以管理和恢复工作区。 若要执行此操作它们需要使用 Power BI 管理门户或 PowerShell Cmdlet。 对于经典工作区基于 Office 365 组，管理继续出现在 Office 365 管理门户和 Azure Active Directory 中。

在中**工作区设置**在管理员门户中，管理员可以使用的设置，使每个人或没有人在组织中创建工作区 （新工作区体验） 来创建新的工作区体验工作区。 管理员还可以限制特定安全组的成员进行创建。

> [!NOTE]
> 创建工作区 （新工作区体验） 设置默认值以仅允许管理员可创建 Office 365 组在 Power BI 中创建新的工作区的用户。 请务必在 Power BI 管理门户，以确保适当的用户可以创建新的工作区体验工作区中设置一个值。

![管理门户中的工作区设置](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

[提供了工作区列表](service-admin-portal.md#workspaces)Power BI 管理门户中。 

![工作区列表](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>与经典的工作区的新工作区并排显示

新的、 已升级工作区和现有的经典工作区共存并排显示，并且可以创建。 新的工作区体验是默认工作区类型。 Power BI 会继续列出用户是在 Power BI，为了避免更改现有工作流中的成员的所有 Office 365 组。 若要了解如何创建新的工作区，请阅读[创建新的工作区](service-create-the-new-workspaces.md)。 若要了解如何创建经典的工作区，请阅读[创建经典的工作区](service-create-workspaces.md)。

## <a name="roles-in-the-new-workspaces"></a>新工作区中的角色

若要授予对新的工作区访问权限，添加用户组或个人到工作区角色之一： 成员、 参与者或管理员。 用户组中的每个人都会获得定义的角色。 如果个人在多个用户组，他们获得最高级别的权限提供给它们分配的角色。

借助角色，可管理哪些人员可在工作区中执行哪些操作，以便实现团队协作。 新的工作区支持向个人和用户组（安全组、Office 365 组和通讯组列表）分配角色。 

向用户组分配角色，组中的个人有权访问内容。 如果嵌套用户组，则包含的所有用户都具有权限。 如果用户属于具有不同角色的多个用户组，则其获得被授予的最高级别的权限。 

新工作区提供三种角色：管理员、成员和参与者。

|功能   | 管理员  | 成员  | 参与者  | 
|---|---|---|---|
| 更新和删除工作区。  | X  |   |   |
| 添加/删除人员，包括其他管理员。  | X  |   |   |
| 添加成员或具有较低权限的其他人。  |  X | X  |   |
| 发布和更新应用。 |  X | X  |   |
| 共享一个项或共享应用。 |  X | X  |   |
| 允许其他人重新共享项目。 |  X | X  |   |
| 在工作区中创建、编辑和删除内容。  |  X | X  | X  |
| 将报表发布到工作区，删除内容。 |  X | X  | X  |
 
 
## <a name="licensing"></a>许可
添加到工作区中的每个人都需要 Power BI Pro 许可证。 在工作区中，这些用户全都可协作处理计划向更广泛的受众，甚至整个组织发布的仪表板和报表。 如果要将内容分发给组织内的其他人，可将 Power BI Pro 许可证分配给这些用户，或将工作区置于 Power BI 高级容量中。

> [!NOTE]
> 报表发布到新的工作区体验已具有更严格实施授权规则。 尝试从 Power BI Desktop 或其他客户端发布工具 Pro 许可证的情况下用户看到错误"只有具有 Power BI Pro 许可证的用户可以发布到此工作区。"

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>新工作区与当前工作区有何不同？

我们正在重新设计新工作区的某些功能。 以下是你可能需要为永久重定向的更改。 

* 创建这些工作区不会创建 Office 365 组像经典的工作区所做的一样。 但是，现在可以使用 Office 365 组来授予用户访问你的工作区将其分配角色。 
* 在经典的工作区中可以将只有个人添加到成员和管理员员列表中。 在新工作区中，可以向这些列表添加多个 AD 安全组、通讯组列表或 Office 365 组，以便更轻松地管理用户。 
- 可以从一个经典的工作区创建组织内容包。 无法从新工作区创建组织内容包。
- 可以使用组织内容包从一个经典的工作区。 无法从新工作区使用组织内容包。

## <a name="workspace-contact-list"></a>工作区的联系人列表
新**联系人列表**功能，可指定哪些用户收到通知的工作区中发生的问题。 默认情况下，任何用户或组指定为工作区通知管理员，但您可以自定义列表。 用户或联系人列表中列出的组将显示在用户界面 (UI) 来帮助用户获得到的工作区相关的帮助。 

详细了解[设置工作区的联系人列表](service-create-the-new-workspaces.md#workspace-contact-list)。

## <a name="workspace-onedrive"></a>Workspace OneDrive
工作区的 OneDrive 功能允许你配置 Office 365 组的 SharePoint 文档库中文件存储可供工作区的用户。 需要 Power BI 外部创建组。 

Power BI 不同步用户或组配置为具有与 Office 365 组成员身份的工作区访问的权限。 最佳做法是管理工作区通过相同的 Office 365 组配置此设置中的文件存储的访问权限。 

阅读有关如何[设置和访问工作区 OneDrive](service-create-the-new-workspaces.md#workspace-onedrive)。  
   
## <a name="auditing"></a>审核
为新的工作区体验工作区，Power BI 被审核以下活动。

| 友好名称 |   操作名称 |
|---|---|
| 已创建 Power BI 文件夹 | CreateFolder |
| 已删除 Power BI 文件夹 | DeleteFolder |
| 已更新 Power BI 文件夹 | UpdateFolder |
| 已更新 Power BI 文件夹访问权限| UpdateFolderAccess |

详细了解[Power BI 审核](service-admin-auditing.md#activities-audited-by-power-bi)。

## <a name="limitations-and-considerations"></a>限制和注意事项

要注意的限制：

- 工作区最多可以包含 1,000 个数据集，或每个数据集最多可以包含 1,000 个报表。 
- 具有 Power BI Pro 许可证的用户可以是最大 1,000 工作区的成员。
- 用于 Excel 的 power BI 发布服务器不受支持。

## <a name="workspace-features-that-work-differently"></a>工作方式不同的工作区功能

新工作区中，某些功能的工作方式与当前工作区不同。 这些差异是有意的根据的反馈，我们已收到来自客户，并启用与工作区的协作更灵活的方法：

- 强制许可：报表发布到新的工作区体验强制实施要求 Power BI Pro 许可证的用户在工作区中协作或共享给其他人在 Power BI 服务中的内容的现有授权规则。 Pro 许可证的情况下用户看到错误"只有具有 Powre BI Pro 许可证的用户可以发布到此工作区。"
- 成员可以或无法重新共享：替换为参与者角色
- 只读工作区：不向用户授予对工作区的只读访问权限，而是向用户分配即将推出的查看器角色，该角色允许对工作区中的内容进行类似的只读访问。
- 没有“退出工作区”按钮  。

## <a name="frequently-asked-questions"></a>常见问题解答

**是受影响的新工作区的现有内容的链接体验 GA**

否。 在经典的工作区中的现有项目的链接不受新工作区体验。 新的工作区体验的正式版 (GA) 更改默认工作区创建，但不会更改现有工作区。 

**现有工作区升级到 GA 的新工作区体验**

否。 新的工作区体验 GA 仅更改为新的工作区体验的默认工作区类型。 现有的经典工作区基于 Office 365 组的保持不变。

**工作区仍会为自动创建 Office 365 组**

是。 由于我们支持两种类型的工作区并排显示，我们继续列出用户有权访问工作区列表中的所有 Office 365 组。

## <a name="next-steps"></a>后续步骤
* [在 Power BI 中创建新的工作区](service-create-the-new-workspaces.md)
* [创建经典的工作区](service-create-workspaces.md)
* [在 Power BI 中安装并使用应用](service-create-distribute-apps.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

---
title: 在 Power BI 的新工作区中整理工作
description: 了解新工作区，即旨在为组织提供关键指标的仪表板和报表的集合。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/30/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8a9e2094619d4c6b0e0f6feb2c9767902b4f7b09
ms.sourcegitcommit: 08b73af260ded51daaa6749338cb85db2eab587f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74099673"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>在 Power BI 的新工作区中整理工作

 工作区是与同事协作创建仪表板、报表和分页报表的集合的地方。 新工作区体验有助于更好地管理对内容的访问。 本文介绍了新工作区及其与经典工作区的区别。  与经典工作区一样，仍可以使用它们来创建和分发应用。 详细了解如何[创建提供新工作区体验的工作区](service-create-the-new-workspaces.md)。

提供新工作区体验的工作区已正式发布 (GA)，现在为默认工作区。 仍可以继续创建和使用基于 Office 365 组的[经典工作区](service-create-workspaces.md)。 

> [!NOTE]
> 若要对浏览工作区中内容的用户强制实现行级别安全性 (RLS)，请使用 查看者角色。 若要强制执行 RLS 而不授予对工作区的访问权限，请向这些用户发布 Power BI 应用，或使用共享来分发内容。

新工作区可用于：

- 将工作区角色分配给用户组：安全组、通讯组列表、Office 365 组和个人。
- 在 Power BI 中创建工作区，而无需创建 Office 365 组。
- 使用更精细的工作区角色在工作区中实现更灵活的权限管理。
- Power BI 管理员可以控制谁能在 Power BI 中创建工作区。

创建一个新工作区时，无需创建关联的基础 Office 365 组。 所有工作区管理操作都在 Power BI 中进行，而不是在 Office 365 中。 在新工作区体验中，现在可以将 Office 365 组添加到工作区访问列表，以继续通过 Office 365 组管理用户对内容的访问。

## <a name="administering-new-workspace-experience-workspaces"></a>管理提供新工作区体验的工作区
Power BI 现在支持管理提供新工作区体验的工作区。Power BI 管理员不仅决定组织中谁能创建工作区， 他们还可以使用 Power BI 管理门户或 PowerShell CmdLets 来管理和恢复工作区。 对于基于 Office 365 组的经典工作区，管理工作继续在 Office 365 管理门户和 Azure Active Directory 中进行。

在管理门户的“工作区设置”中，管理员可以使用“创建工作区(新工作区体验)”设置，以允许组织中的每个人或禁止组织中的任何人创建提供新工作区体验的工作区。 管理员还可以限制特定安全组的成员进行创建。

> [!NOTE]
> “创建工作区(新工作区体验)”设置默认为，仅允许能够创建 Office 365 组的用户在 Power BI 中创建新工作区。 请务必在 Power BI 管理门户中设置值，以确保相应用户能够创建提供新工作区体验的工作区。

![管理门户中的工作区设置](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

Power BI 管理门户中[提供工作区列表](service-admin-portal.md#workspaces)。 

![工作区列表](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>新工作区与经典工作区共存

升级后的新工作区与现有经典工作区共存，你可以创建两种工作区中的任何一种。 提供新工作区体验的工作区是默认工作区类型。 为了避免更改现有工作流，Power BI 会继续列出用户在 Power BI 中所属的全部 Office 365 组。 若要了解如何创建新工作区，请参阅[创建新工作区](service-create-the-new-workspaces.md)。 若要了解如何创建经典工作区，请参阅[创建经典工作区](service-create-workspaces.md)。

## <a name="roles-in-the-new-workspaces"></a>新工作区中的角色

若要授予对新工作区的访问权限，请将用户组或个人添加到以下工作区角色之一：查看者、成员、参与者或管理员。 用户组中的每个人都会获得定义的角色。 如果某个人是多个用户组的成员，此人获得所分配角色提供的最高级别权限。

借助角色，可管理哪些人员可在工作区中执行哪些操作，以便实现团队协作。 新的工作区支持向个人和用户组（安全组、Office 365 组和通讯组列表）分配角色。 

向用户组分配角色，组中的个人有权访问内容。 如果嵌套用户组，则包含的所有用户都具有权限。

下面介绍以下四种角色的功能：管理员、成员、参与者和查看者。 上述功能（最后一个功能除外）都需要 Power BI Pro 许可证。

|功能   | 管理员  | 成员  | 参与者  | 查看者 |
|---|---|---|---|---|
| 更新和删除工作区。  | X  |   |   |   | 
| 添加/删除人员，包括其他管理员。  | X  |   |   |   |
| 添加成员或具有较低权限的其他人。  |  X | X  |   |   |
| 发布和更新应用。 |  X | X  |   |   |
| 共享一个项或共享应用。 |  X | X  |   |   |
| 允许其他人重新共享项目。 |  X | X  |   |   |
| 在工作区中创建、编辑和删除内容。  |  X | X  | X  |   |
| 将报表发布到工作区，删除内容。  |  X | X  | X  |   |
| 基于此工作区中的数据集在其他工作区中创建报表。 |  X | X  | X  |   |
| 复制报表。 | X | X | X |  |
| 查看项并与之交互。 |  X | X  | X  | X  |

> [!NOTE]
>若要复制报表，并基于此工作区中的数据集在另一个工作区中创建报表，相关人员需要满足其他条件：
>- 他们需要 Power BI Pro 许可证。 有关详细信息，请参阅下一部分[许可](#licensing)。
>- 他们需要此数据集的生成权限。 对于此工作区中的数据集，拥有管理员、成员和参与者角色的相关人员通过其工作区角色获得生成权限。
 
## <a name="licensing"></a>许可
你添加到共享容量中的工作区的每个人都需要 Power BI Pro 许可证。 在工作区中，这些用户全都可协作处理计划向更广泛的受众，甚至整个组织发布的仪表板和报表。 

如果要将内容分发给组织内的其他人，可将 Power BI Pro 许可证分配给这些用户，或将工作区置于 Power BI 高级容量中。

如果工作区位于 Power BI 高级容量中，具有查看者角色的用户可以访问工作区，即使没有 Power BI Pro 许可证，也不例外。 不过，如果你为这些用户分配更高级别的角色（如管理员、成员或参与者），他们会在尝试访问工作区时看到启动 Power BI Pro 试用版的提示。 若要对没有 Power BI Pro 许可证的用户利用查看者功能，请确保用户只有查看者角色，没有其他任何工作区角色，无论是个人还是通过用户组。 

> [!NOTE]
> 对于向提供新工作区体验的工作区发布报表，需要更严格地强制执行现有许可规则。 如果没有 Power BI Pro 许可证的用户尝试从 Power BI Desktop 或其他客户端工具发布报表，便会看到错误消息“只有拥有 Power BI Pro 许可证的用户，才能发布到此工作区”。

## <a name="how-the-new-workspaces-are-different"></a>新工作区的不同之处

我们已重新设计新工作区的某些功能。 以下是可以预见的永久性更改。 

* 创建这些工作区不会像经典工作区那样创建 Office 365 组。 不过，现在可以使用 Office 365 组来授予用户对工作区的访问权限，具体方法是向用户分配角色。 
* 在经典工作区中，只能将个人添加到成员和管理员列表中。 在新工作区中，可以向这些列表添加多个 AD 安全组、通讯组列表或 Office 365 组，以便更轻松地管理用户。 
- 可以从经典工作区创建组织内容包。 无法从新工作区创建组织内容包。
- 可以从经典工作区使用组织内容包。 无法从新工作区使用组织内容包。

## <a name="workspace-contact-list"></a>工作区联系人列表
借助联系人列表这一新功能，可以指定哪些用户接收关于工作区中发生的问题的通知。 默认情况下，任何指定为工作区管理员的用户或组都会收到通知，但你可以自定义列表。 联系人列表中列出的用户或组将显示在用户界面 (UI) 中，以帮助用户获得与工作区相关的帮助。 

详细了解[如何设置工作区联系人列表](service-create-the-new-workspaces.md#workspace-contact-list)。

## <a name="workspace-onedrive"></a>工作区 OneDrive
借助工作区 OneDrive 功能，可以配置 Office 365 组，而它的 SharePoint 文档库文件存储可供工作区用户使用。 必须在 Power BI 之外创建此组。 

Power BI 不会将配置为拥有工作区访问权限的用户或组的权限，与 Office 365 组成员身份同步。 最佳做法是，通过在此设置中配置其文件存储的同一 Office 365 组来管理工作区访问权限。 

详细了解如何[设置和访问工作区 OneDrive](service-create-the-new-workspaces.md#workspace-onedrive)。  
   
## <a name="auditing"></a>审核
对于提供新工作区体验的工作区，Power BI 审核以下活动。

| 友好名称 |   操作名称 |
|---|---|
| 已创建 Power BI 文件夹 | CreateFolder |
| 已删除 Power BI 文件夹 | DeleteFolder |
| 已更新 Power BI 文件夹 | UpdateFolder |
| 已更新 Power BI 文件夹访问权限| UpdateFolderAccess |

详细了解 [Power BI 审核](service-admin-auditing.md#activities-audited-by-power-bi)。

## <a name="limitations-and-considerations"></a>限制和注意事项

要注意的限制：

- 工作区最多可以包含 1,000 个数据集，或每个数据集最多可以包含 1,000 个报表。 
- 拥有 Power BI Pro 许可证的用户最多可以成为 1,000 个工作区的成员。
- 不支持 Power BI Publisher for Excel。

## <a name="workspace-features-that-work-differently"></a>工作方式不同的工作区功能

新工作区中，某些功能的工作方式与当前工作区不同。 这些差异是根据客户反馈有意而为之，可便于用户更灵活地使用工作区开展协作：

- 强制许可：对于向提供新工作区体验的工作区发布报表，将强制执行现有许可规则，这些规则要求用户必须有 Power BI Pro 许可证，才能在工作区中协作，或与 Power BI 服务中的其他人共享内容。 没有 Pro 许可证的用户会看到错误消息：“只有拥有 Power BI Pro 许可证的用户才能发布到此工作区。”
- 成员可以或无法重新共享：替换为参与者角色
- 只读工作区：向用户分配查看者角色，此角色对对工作区中内容的权限与只读访问权限类似，而不是向用户授予对工作区的只读访问权限。
- 如果工作区位于 Power BI 高级容量中，没有 Power BI Pro 许可证的用户可以访问工作区，即使用户只有查看者角色，也不例外。
- 若要允许具有查看者角色的用户导出数据，请确保他们有权在工作区中生成数据集。 详细了解[数据集的“生成”权限](service-datasets-build-permissions.md)。
- 没有“退出工作区”按钮。

## <a name="frequently-asked-questions"></a>常见问题解答

**指向现有内容的链接是否会受到新工作区体验正式版的影响？**

否。 指向经典工作区中现有项的链接不会受到新工作区体验的影响。 新工作区体验正式版 (GA) 更改你创建的默认工作区，但不更改现有工作区。 

**现有工作区是否会升级到新工作区体验正式版？**

否。 新工作区体验正式版只将默认工作区类型更改为新工作区体验。 基于 Office 365 组的现有经典工作区保持不变。

**是否仍自动为 Office 365 组创建工作区？**

是。 由于现在同时支持两种类型工作区，因此工作区列表中会继续列出用户有权访问的所有 Office 365 组。

## <a name="next-steps"></a>后续步骤
* [在 Power BI 中创建新工作区](service-create-the-new-workspaces.md)
* [创建经典工作区](service-create-workspaces.md)
* [在 Power BI 中安装并使用应用](service-create-distribute-apps.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)

---
title: 在 Power BI 的新工作区中整理工作
description: 了解新工作区，即旨在为组织提供关键指标的仪表板和报表的集合。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 701f478ce4dd59d77c1722b1386cd79ad3fbf2a0
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83693775"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>在 Power BI 的新工作区中整理工作

工作区是与同事协作创建仪表板、报表、数据集和分页报表的集合的地方。 新工作区体验有助于更好地管理对内容的访问。 本文介绍了新工作区及其与经典工作区的区别。  与经典工作区一样，仍可以使用它们来创建和分发应用。 已准备好创建新的工作区？ 阅读[创建新的工作区体验](service-create-the-new-workspaces.md)。

升级后的新工作区可以与现有经典工作区共存。 提供新工作区体验的工作区是默认工作区类型。 如果需要，你仍可以创建和使用基于 Microsoft 365 组的[经典工作区](service-create-workspaces.md)。 已准备好迁移经典工作区？ 有关详细信息，请参阅[在 Power BI 中将经典工作区升级到新工作区](service-upgrade-workspaces.md)。

新工作区可用于：

- 将工作区角色分配给用户组：安全组、通讯组列表、Microsoft 365 组和个人。
- 在 Power BI 中创建工作区，而无需创建关联的基础 Microsoft 365 组。 所有工作区管理操作都在 Power BI 中进行，而不是在 Microsoft 365 中。
- 如果需要，可以继续通过 Microsoft 365 组管理用户对内容的访问权限。 只需在工作区访问列表中添加 Microsoft 365 组。
- 使用更精细的工作区角色在工作区中实现更灵活的权限管理。

Power BI 继续列出你所属的所有 Microsoft 365 组。 这样可以避免更改现有工作流。

## <a name="new-and-classic-workspace-differences"></a>新的和经典的工作区差异

我们已重新设计新工作区的某些功能。 两种方法的主要区别如下所示。

- 创建这些工作区不会像经典工作区那样创建 Microsoft 365 组。 不过，现在可以使用 Microsoft 365 组来授予用户对工作区的访问权限，具体方法是向用户分配角色。
- 在经典工作区中，只能将个人添加到成员和管理员列表中。 在新工作区中，可以向这些列表添加多个 Active Directory 安全组、通讯组列表或 Microsoft 365 组，以便更轻松地管理用户。
- 可以从经典工作区创建组织内容包。 无法从新工作区创建组织内容包。
- 可以从经典工作区使用组织内容包。 无法从新工作区使用组织内容包。

### <a name="workspace-features-that-work-differently"></a>工作方式不同的工作区功能

新工作区中，某些功能的工作方式与当前工作区不同。 这些差异是特意的，它们基于我们从客户收到的反馈。 它们实现了一种更灵活的方法来与工作区协作。

- 强制许可：在向新工作区体验发布报表时，需要执行现有许可规则。 用户在工作区中协作或将内容共享到 Power BI 服务中的其他用户时，需要 Power BI Pro 许可证。 没有 Pro 许可证的用户会看到错误消息：“只有拥有 Power BI Pro 许可证的用户才能发布到此工作区。”
- 成员可以或不可以重新共享：参与者角色替换此设置。
- 只读工作区：不向用户授予对工作区的只读访问权限，而是将其分配给查看者角色。 它允许对工作区中的内容进行类似的只读访问。
- 如果工作区位于 Power BI Premium 容量中，则没有 Pro 许可证的用户也可以访问工作区，不过需要具有“查看者”角色。
- 允许用户导出数据：如果具有查看者角色的用户有权在工作区中生成数据集，这些用户可以导出数据。 详细了解[数据集的“生成”权限](../connect-data/service-datasets-build-permissions.md)。
- 没有“退出工作区”按钮。

### <a name="workspace-contact-list"></a>工作区联系人列表

借助联系人列表这一新功能，可以指定哪些用户接收关于工作区中发生的问题的通知。 默认情况下，任何指定为工作区管理员的用户或组都会收到通知，但你可以自定义列表。 联系人列表中列出的用户或组将显示在用户界面 (UI) 中，以帮助用户获得与工作区相关的帮助。 

详细了解[如何设置工作区联系人列表](service-create-the-new-workspaces.md#workspace-contact-list)。

### <a name="workspace-onedrive"></a>工作区 OneDrive

借助工作区 OneDrive 功能，你可以配置 Microsoft 365 组，使其 SharePoint 文档库文件存储可供工作区用户使用。 在 Power BI 之外创建组。

Power BI 不会将配置为拥有工作区访问权限的用户或组的权限，与 Microsoft 365 组成员身份同步。 最佳做法是，通过在此设置中配置其文件存储的同一 Microsoft 365 组来管理工作区访问权限。

详细了解如何[设置和访问工作区 OneDrive](service-create-the-new-workspaces.md#workspace-onedrive)。  

## <a name="roles-in-the-new-workspaces"></a>新工作区中的角色

要授予对新工作区的访问权限，请将用户组或个人添加到以下工作区角色之一：管理员、成员、参与者或查看者。 用户组中的每个人都会获得定义的角色。 如果某个人是多个用户组的成员，此人获得所分配角色提供的最高级别权限。

借助角色，可管理哪些人员可在工作区中执行哪些操作，以便实现团队协作。 新的工作区支持向个人和用户组（安全组、Microsoft 365 组和通讯组列表）分配角色。

向用户组分配角色，组中的个人有权访问内容。 如果嵌套用户组，则包含的所有用户都具有权限。

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> 若要对浏览工作区中内容的用户强制实现行级别安全性 (RLS)，请使用 查看者角色。 若要强制执行 RLS 而不授予对工作区的访问权限，请向这些用户发布 Power BI 应用，或使用共享来分发内容。

## <a name="licensing"></a>许可
你添加到共享容量中的工作区的每个人都需要 Power BI Pro 许可证。 在工作区中，这些用户全都可协作处理计划向更广泛的受众，甚至整个组织发布的仪表板和报表。 

如果要将内容分发给组织内的其他人，可将 Power BI Pro 许可证分配给这些用户，或将工作区置于 Power BI 高级容量中。

如果工作区位于 Power BI 高级容量中，具有查看者角色的用户可以访问工作区，即使没有 Power BI Pro 许可证，也不例外。 不过，如果你为这些用户分配更高级别的角色（如管理员、成员或参与者），他们会在尝试访问工作区时看到启动 Pro 试用版的提示。 若要对没有 Pro 许可证的用户使用查看者角色，请确保他们也没有其他工作区角色，无论是单独使用还是通过用户组。

> [!NOTE]
> 对于向提供新工作区体验的工作区发布报表，需要更严格地强制执行现有许可规则。 如果你没有 Power BI Pro 许可证而尝试从 Power BI Desktop 或其他客户端工具发布报表，便会看到错误消息“只有拥有 Power BI Pro 许可证的用户，才能发布到此工作区”。

## <a name="administering-new-workspace-experience-workspaces"></a>管理提供新工作区体验的工作区

现在，在 Power BI 管理门户中对提供新工作区体验的工作区进行管理。 Power BI 管理员决定组织中的哪些人员可以创建工作区和分发应用。 管理员可以查看组织中所有工作区的状态。 还可以管理和恢复工作区。 在“管理门户”一文中阅读有关[创建新工作区](../admin/service-admin-portal.md#create-the-new-workspaces)的详细信息。

## <a name="guest-users"></a>来宾用户

默认情况下，[Azure AD B2B 来宾用户](../admin/service-admin-azure-ad-b2b.md)无法访问工作区。 Power BI 管理员[允许外部来宾用户编辑和管理组织中的内容](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content)。 已启用的来宾用户可以访问他们有权访问的工作区。

## <a name="auditing"></a>审核

对于提供新工作区体验的工作区，Power BI 审核以下活动。

| 友好名称 | 操作名称 |
|---|---|
| 已创建 Power BI 文件夹 | CreateFolder |
| 已删除 Power BI 文件夹 | DeleteFolder |
| 已更新 Power BI 文件夹 | UpdateFolder |
| 已更新 Power BI 文件夹访问权限| UpdateFolderAccess |

详细了解 [Power BI 审核](../admin/service-admin-auditing.md)。

## <a name="limitations-and-considerations"></a>限制和注意事项

要注意的限制：

- 工作区最多可以包含 1,000 个数据集，或每个数据集最多可以包含 1,000 个报表。 
- 拥有 Power BI Pro 许可证的用户最多可以成为 1,000 个工作区的成员。
- 不支持 Power BI Publisher for Excel。

## <a name="frequently-asked-questions"></a>常见问题解答

指向现有内容的链接是否会受到新工作区体验的影响？

否。 指向经典工作区中现有项的链接不会受到新工作区体验的影响。 新工作区体验正式版 (GA) 更改你创建的默认工作区，但不更改现有工作区。 

**现有工作区是否会升级到新工作区体验正式版？**

否。 新工作区体验正式版只将默认工作区类型更改为新工作区体验。 基于 Microsoft 365 组的现有经典工作区保持不变。

**是否仍自动为 Microsoft 365 组创建工作区？**

是。 由于现在同时支持两种工作区，因此工作区列表中会继续列出你有权访问的所有 Microsoft 365 组。

## <a name="next-steps"></a>后续步骤

* [在 Power BI 中创建新工作区](service-create-the-new-workspaces.md)
* [创建经典工作区](service-create-workspaces.md)
* [在 Power BI 中安装并使用应用](service-create-distribute-apps.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)


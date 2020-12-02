---
title: 在 Power BI 的新工作区中整理工作
description: 了解新工作区，即旨在为组织提供关键指标的仪表板和报表的集合。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
ms.date: 10/21/2020
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 43af5a2ea924ababdba7b328b814045b75be5316
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411738"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>在 Power BI 的新工作区中整理工作

工作区是与同事协作创建仪表板、报表、数据集和分页报表的集合的地方。 新工作区体验有助于更好地管理对内容的访问。 本文介绍了新工作区及其与经典工作区的区别。  与经典工作区一样，仍可以使用它们来创建和分发应用。 

已准备好创建新的工作区？ 阅读[创建新的工作区体验](service-create-the-new-workspaces.md)。

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Power BI 新工作区体验":::

升级后的新工作区可以与现有经典工作区共存。 提供新工作区体验的工作区是默认工作区类型。 如果需要，你仍可以创建和使用基于 Microsoft 365 组的[经典工作区](service-create-workspaces.md)。 已准备好迁移经典工作区？ 有关详细信息，请参阅[在 Power BI 中将经典工作区升级到新工作区](service-upgrade-workspaces.md)。

## <a name="new-and-classic-workspace-differences"></a>新的和经典的工作区差异

我们已重新设计新工作区的某些功能。 两种方法的主要区别如下所示。

- 创建新工作区不会像经典工作区那样创建 Microsoft 365 组。 所有新工作区管理操作都在 Power BI 中进行，而不是在 Office 365 中。 如果需要，仍可以通过 Microsoft 365 组管理用户对内容的访问权限。 只需在工作区访问列表中添加 Microsoft 365 组。
- 使用更精细的工作区角色在新工作区中实现更灵活的权限管理。  在经典工作区中，只能将个人添加到成员和管理员列表中。 
- 将用户组分配到工作区角色：在新工作区中，可以向这些角色添加多个 Active Directory 安全组、通讯组列表或 Microsoft 365 组，以便更轻松地管理用户。 
- 联系人列表：在新工作区中，可以指定谁会收到工作区活动通知。
- 创建模板应用：只能在新工作区中创建模板应用。 模板应用是可以分发给组织外部客户的应用。 然后，这些客户可以通过你的模板应用连接到他们自己的数据。 详细了解[模板应用](../connect-data/service-template-apps-overview.md)。
- 共享数据集：若要在特定工作区外共享数据集，需要将包含数据集的报表保存到新工作区。 无法从经典工作区共享数据集。 详细了解[共享数据集](../connect-data/service-datasets-across-workspaces.md)。
- **组织内容包**：在经典工作区中创建和使用组织内容包。 无法在新工作区中创建或使用它们。 应用和模板应用会替换新工作区中的组织内容包。

本文详细介绍了这些功能。

> [!NOTE]
> Power BI 继续列出你所属的所有 Microsoft 365 组。 这样可以避免更改现有工作流。

### <a name="features-that-work-differently"></a>工作方式不同的功能

在新工作区中，某些功能的工作方式有所不同。 这些差异是特意的，它们基于我们从客户收到的反馈。 通过它们，可以更灵活地在工作区中进行协作。

- 强制许可：在向新工作区体验发布报表时会强制执行现有许可规则。 用户在新工作区中协作或将内容共享到 Power BI 服务中的其他用户时，需要 Power BI Pro 许可证。 没有 Pro 许可证的用户会看到错误消息：“只有拥有 Power BI Pro 许可证的用户才能发布到此工作区。”
- “成员可以重新共享”设置：新工作区中的参与者角色替代了经典工作区中的“成员可以重新共享”设置。
- 只读工作区：新工作区中的查看者角色替代了授予用户对经典工作区的只读访问权限。 通过查看者角色，可以对新工作区中的内容进行类似的只读访问。
- 如果工作区位于 Power BI Premium 容量中，则没有 Pro 许可证的用户也可以访问新工作区，不过需要具有查看者角色。
- 允许用户导出数据：如果具有新工作区查看者角色的用户有权在该工作区中生成数据集，则这些用户甚至可以导出数据。 详细了解[数据集的“生成”权限](../connect-data/service-datasets-build-permissions.md)。
- 新工作区中没有“离开工作区”按钮。

### <a name="workspace-contact-list"></a>工作区联系人列表

借助联系人列表这一新功能，可以指定哪些用户接收新工作区中的问题通知。 默认情况下，对于新工作区，任何指定为工作区管理员的用户或组都会收到通知。 你可以添加该列表。 联系人列表中的用户或组还会在新工作区的用户界面 (UI) 中列出，以便工作区最终用户知道要联系哪些用户或组。 

了解[如何创建工作区联系人列表](service-create-the-new-workspaces.md#create-a-contact-list)。

### <a name="workspace-onedrive"></a>工作区 OneDrive

正如我们所提到的，当你创建一个新工作区时，Power BI 不会在后台创建 Microsoft 365 组。 不过，你仍可能会发现，将 OneDrive 与新工作区相关联会很有用。 借助新工作区中的工作区 OneDrive 功能，你可以配置 Microsoft 365 组，使其 SharePoint 文档库文件存储可供工作区用户使用。 在 Power BI 之外创建组。
 
Power BI 不会在 Microsoft 365 组成员身份和具有新工作区访问权限的用户或组的权限之间进行同步。 你可以使其同步，方法是：通过在此设置中配置其文件存储的同一 Microsoft 365 组来管理工作区访问权限。 

了解如何[设置工作区 OneDrive](service-create-the-new-workspaces.md#set-a-workspace-onedrive)。  

## <a name="roles-in-the-new-workspaces"></a>新工作区中的角色

借助角色，可管理哪些人员可在新工作区中执行哪些操作，以便实现团队协作。 新的工作区支持向个人和用户组（安全组、Microsoft 365 组和通讯组列表）分配角色。 

要授予对新工作区的访问权限，请将用户组或个人分配到以下工作区角色之一：管理员、成员、参与者或查看者。 用户组中的每个人都会获得分配的角色。 如果某个人是多个用户组的成员，此人获得所分配角色提供的最高级别权限。 如果嵌套用户组，则包含的所有用户都具有权限。 上述功能（查看和交互除外）都需要 Power BI Pro 许可证。 有关详细信息，请参阅本文中的[许可](#licenses)部分。

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - 可以将用户单独或通过组分配到角色，即使用户无法使用该角色。 换言之，可以将没有 Power BI Pro 许可证的用户分配到需要许可证的角色。 有关详细信息，请参阅本文中的[许可证](#licenses)部分。
> - 若要对浏览工作区中内容的用户强制实现[行级别安全性 (RLS)](../admin/service-admin-rls.md)，请使用查看者角色。 在未授予新工作区访问权限的情况下，也可以强制执行 RLS。 [发布应用](service-create-distribute-apps.md)，并将其分发给这些用户，或使用[共享功能来分发内容](service-share-dashboards.md)。

## <a name="licensing-and-administering"></a>许可和管理

### <a name="licenses"></a>许可证
如果某个新工作区位于共享容量中，则添加到该工作区中的每个人都需要具有 Power BI Pro 许可证。 这些用户均可以协作处理新工作区中的仪表板和报表。 如果要将内容分发给组织内的其他人，可将 Power BI Pro 许可证分配给这些用户，或将工作区置于 Power BI Premium 容量中。

如果新工作区位于 Power BI Premium 容量中，具有查看者角色的用户可以访问工作区，即使没有 Power BI Pro 许可证也无妨。 不过，如果你为这些用户分配更高级别的角色（如管理员、成员或参与者），他们会在尝试访问工作区时看到启动 Pro 试用版的提示。 如果想让没有 Pro 许可证的用户使用查看者角色，请确保他们也未以个人或用户组成员的身份拥有其他工作区角色。

在向新工作区体验发布报表时，需要更严格地强制执行现有许可规则。 如果你没有 Power BI Pro 许可证而尝试从 Power BI Desktop 或其他客户端工具发布报表，便会看到错误消息“只有拥有 Power BI Pro 许可证的用户，才能发布到此工作区”。

> [!NOTE]
> Power BI 美国政府版不可用作免费许可证。 有关许可详细信息，请参阅[适用于美国政府客户的 Power BI](../admin/service-govus-overview.md)。

### <a name="guest-users"></a>来宾用户

默认情况下，[Azure AD B2B 来宾用户](../admin/service-admin-azure-ad-b2b.md)无法访问工作区。 Power BI 管理员[允许外部来宾用户编辑和管理组织中的内容](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content)。 已启用的来宾用户可以访问他们有权访问的工作区。

### <a name="administering-new-workspace-experience-workspaces"></a>管理提供新工作区体验的工作区

在 Power BI 管理门户中对提供新工作区体验的工作区进行管理。 Power BI 管理员决定组织中的哪些人员可以创建工作区和分发应用。 请参阅“管理用户”一文中的[管理用户创建工作区的能力](../admin/service-admin-portal.md#create-the-new-workspaces)。 

管理员还可以查看组织中所有工作区的状态。 他们可以管理、恢复甚至删除工作区。 请参阅“管理用户”一文中的[自行管理工作区](../admin/service-admin-portal.md#workspaces)。

### <a name="auditing"></a>审核

对于提供新工作区体验的工作区，Power BI 会审核以下活动。

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

现有工作区是否会升级到新工作区体验正式版？

否。 新工作区体验正式版只将默认工作区类型更改为新工作区体验。 基于 Microsoft 365 组的现有经典工作区保持不变。

是否仍自动为 Microsoft 365 组创建工作区？

是。 由于现在同时支持两种工作区，因此工作区列表中会继续列出你有权访问的所有 Microsoft 365 组。

## <a name="next-steps"></a>后续步骤

* [在 Power BI 中创建新工作区](service-create-the-new-workspaces.md)
* [创建经典工作区](service-create-workspaces.md)
* [在 Power BI 中安装并使用应用](service-create-distribute-apps.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)


---
title: 通过 Power BI 服务直接共享到 Microsoft Teams
description: 可以通过 Power BI 服务直接与 Microsoft Teams 共享 Power BI 仪表板和报表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 07/31/2020
ms.openlocfilehash: ae3f6b5f3026adf127b53dd07118fe05e4c06a00
ms.sourcegitcommit: 1b3a626c5ca612a7f23058f8e5cc0147a94db51c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348073"
---
# <a name="share-directly-to-microsoft-teams-from-the-power-bi-service"></a>通过 Power BI 服务直接共享到 Microsoft Teams

可以通过 Power BI 服务直接与 Microsoft Teams 共享 Power BI 仪表板、报表和视觉对象。 在 Power BI 服务中查看报表和仪表板时，使用“共享到 Teams”功能可快速开始对话。

## <a name="requirements"></a>要求

若要在 Power BI 中使用“共享到 Teams”功能，请确保此设置：

- Power BI 管理员未在 Power BI 管理门户中禁用“共享到 Teams”租户设置。 该设置允许组织隐藏“共享到 Teams”按钮。 有关详细信息，请参阅 [Power BI 管理门户](../admin/service-admin-portal.md#share-to-teams-tenant-setting)一文。

请参阅[使用 Power BI 在 Microsoft Teams 中开展协作](service-collaborate-microsoft-teams.md)，其中介绍了 Power BI 和 Microsoft Teams 协同工作的背景以及其他要求。

## <a name="share-power-bi-content-to-microsoft-teams"></a>将 Power BI 内容共享到 Microsoft Teams

按照以下步骤将 Power BI 服务中的报表、仪表板和视觉对象的链接共享到 Microsoft Teams 频道和聊天。

1. 选择以下选项之一：

   * 仪表板或报表的操作栏中的“共享到 Teams”：

       ![操作栏中的“共享到 Teams”按钮的屏幕截图。](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * 单个视觉对象的上下文菜单中的“共享到 Teams”：
    
      ![视觉对象上下文菜单中的“共享到 Teams”按钮的屏幕截图。](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. 在“共享到 Microsoft Teams”对话框中，选择要将链接发送到的团队或频道。 如果需要，可以输入一条消息。 系统可能会要求你先登录到 Microsoft Teams。

    ![包含信息和消息的“共享到 Microsoft Teams”对话框的屏幕截图。](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. 选择“共享”以发送链接。
    
1. 该链接将添加到现有对话或开始新聊天。

    ![包含指向 Power BI 项的链接的 Microsoft Teams 对话的屏幕截图。](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. 选择链接可在 Power BI 服务中打开该项。

1. 如果使用了特定视觉对象的上下文菜单，则在打开报表时会突出显示该视觉对象。

    ![已打开突出显示了特定视觉对象的 Power BI 报表的屏幕截图。](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>已知问题和限制

- 没有用于访问报表的 Power BI 许可证或权限的用户会看到“内容不可用”消息。
- 如果浏览器使用严格的隐私设置，则“共享到 Teams”按钮可能不起作用。 如果未正确打开对话框，则使用“遇到问题? 尝试在新窗口中打开”选项。
- “共享到 Teams”不包括链接预览。
- 链接预览和“共享到 Teams”不向用户授予查看该项的权限。 权限必须单独进行管理。
- 当报表作者将视觉对象的“更多选项”设置为“关”时，“共享到 Teams”按钮在视觉对象上下文菜单中不可用  。
- 请参阅“在 Microsoft Teams 中开展协作”一文中的[已知问题和限制](service-collaborate-microsoft-teams.md#known-issues-and-limitations)部分以了解其他问题。

## <a name="next-steps"></a>后续步骤

- [使用 Power BI 在 Microsoft Teams 中开展协作](service-collaborate-microsoft-teams.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)。

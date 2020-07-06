---
title: 排查共享仪表板和报表时遇到的问题
description: 如何解决与组织内外的同事共享 Power BI 仪表板和报表时遇到的问题。
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 06/23/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ef78847829ef292a16856a1597a53c95e7d20708
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85486690"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>排查共享仪表板和报表时遇到的问题

下面是在共享仪表板或报表时或其他人与你共享时可能会遇到的一些常见问题。 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>仪表板收件人在磁贴中看到锁定图标

与其共享的人员尝试查看报表时，可能会在仪表板中看到锁定的磁贴或“需要权限”消息。

![Power BI 锁定磁贴](media/service-share-dashboards/power-bi-locked_tile_small.png)

如果是这样，则需要向他们授予对基础数据集的权限。

1. 转到内容列表中的“数据集”选项卡。

1. 选择数据集旁边的省略号 (...)，然后选择“管理权限” 。

    ![管理权限](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. 选择“添加用户”。

    ![选择“添加用户”。](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. 输入个人、通讯组或安全组的完整电子邮件地址。 不能与动态通讯组列表共享。

    ![添加电子邮件地址](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. 选择“添加”。

## <a name="i-cant-share-a-dashboard-or-report"></a>我无法共享仪表板或报表

要共享仪表板或报表，你需要具有重新共享基础内容（任何相关的报表和数据集）的权限。 如果你看到一条消息，指示无法共享，请要求报表作者给予你重新共享这些报表和数据集的权限。

![“无法共享”消息](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>我无权访问仪表板或报表

如果你在选择指向报表或仪表板的链接时看到“请求访问”消息，则表示无权查看它。 你需要[请求访问它](service-request-access.md)。

## <a name="next-steps"></a>后续步骤

- [与同事和他人共享 Power BI 仪表板和报表](service-share-dashboards.md)
- [应如何针对仪表板及报表开展协作并进行共享？](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [共享筛选的 Power BI 报表](service-share-reports.md)
- 是否有任何问题? [尝试参与 Power BI 社区](https://community.powerbi.com/)

---
title: 跨工作区控制数据集的使用 - Power BI
description: 了解如何限制 Power BI 租户中的信息流。
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 6cc602b96207b1662f0738c0936ca816bbfd0a03
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92681036"
---
# <a name="control-the-use-of-datasets-across-workspaces"></a>跨工作区控制数据集的使用

跨工作区使用数据集是推动组织内数据文化和数据民主化的强大方法。 尽管如此，如果你是 Power BI 管理员，有时你会想要限制 Power BI 租户中的信息流。 使用租户设置“跨工作区使用数据集”，可完全或部分限制每个安全组的数据集重用。

![Power BI 管理员工作区设置](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

如果关闭此设置，则会对报表创建者造成以下影响：

- “跨工作区复制报表”按钮不可用。 
- 在基于共享数据集的报表中，“编辑报表”按钮不可用。
- 在 Power BI 服务中，发现体验仅显示当前工作区中的数据集。
- 在 Power BI Desktop 中，发现体验仅显示你是其成员的工作区中的数据集。
- 在 Power BI Desktop 中，如果用户打开具有实时连接的 .pbix 文件，该实时连接与用户所属的任何工作区之外的数据集相连，则用户会看到一条错误消息，要求连接到另一个数据集。

## <a name="provide-a-link-for-the-certification-process"></a>提供验证过程的链接

作为 Power BI 管理员，你可以在“认可”设置页面上提供“了解详细信息”链接的 URL 。  有关详细信息，请参阅[启用内容认证](../admin/service-admin-setup-certification.md)。 此链接可以转到关于验证过程的文档。 如果你未提供“了解详细信息”链接的目标，则默认指向[认可你的内容](../collaborate-share/service-endorse-content.md)一文。

![数据集验证“了解详细信息”](media/service-datasets-admin-across-workspaces/service-admin-certification-setup-dialog.png)

## <a name="next-steps"></a>后续步骤

- [跨工作区使用数据集](service-datasets-across-workspaces.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)

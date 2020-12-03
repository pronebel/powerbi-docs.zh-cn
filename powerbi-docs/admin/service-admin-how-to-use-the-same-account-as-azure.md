---
title: 将相同的帐户用于 Power BI 和 Azure
description: 如何将相同的帐户登录名用于 Power BI 和 Azure
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 2706fd8eb4cb2fddda99710e7c1dc32c2300aa26
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413601"
---
# <a name="using-the-same-account-for-power-bi-and-azure"></a>将相同的帐户用于 Power BI 和 Azure

如果你同时是 Power BI 和 Azure 的用户，则可能要对这两个服务使用相同的登录名，以便无需输入密码两次。

Power BI 会使用与工作或学校电子邮件地址关联的组织帐户使你登录。  Azure 会使用 Microsoft 帐户或组织帐户使你登录。

如果要同时对 Azure 和 Power BI 使用相同的登录名，请务必使用组织帐户登录到 Azure。

**如果我已使用 Microsoft 帐户登录 Azure，该怎么办？**

通过执行以下步骤可以作为协同管理员在 Azure 中添加组织帐户：

1. 登录 [Azure 门户](https://portal.azure.com/)。 如果你是多个 Azure 目录中的用户，请选择“订阅”，然后进行筛选以便仅查看你要编辑的目录和订阅。

1. 在导航窗格中，选择“访问控制(IAM)”，然后选择“添加”\>“添加共同管理员”  。

    ![访问控制的屏幕截图，其中突出显示了添加“共同管理员”。](media/service-admin-how-to-use-the-same-account-as-azure/add-co-administrator.png)

1. 输入与组织帐户关联的电子邮件地址，然后选择“添加”。

1. 下次登录 Azure 门户时，请使用组织电子邮件地址。

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

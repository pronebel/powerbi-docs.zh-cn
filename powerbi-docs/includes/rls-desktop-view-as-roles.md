---
ms.openlocfilehash: eb7cba03daee47f6772fc46be50419731b41765e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193590"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>在 Power BI Desktop 中验证角色
创建角色后，请在 Power BI Desktop 中测试角色结果。

1. 选择“以角色身份查看”  。 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    在“以角色身份查看”中，可以看到创建的角色  。

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. 选择创建的角色 >“确定”，应用该角色  。 报表呈现与该角色相关的数据。 

4. 你还可以选择其他用户，并提供给定用户  。 最好提供用户主体名称 (UPN)，因为 Power BI 服务和 Power BI 报表服务器使用该名称。

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. 选择“确定”，报表将基于该用户所见呈现内容  。 

在 Power BI Desktop 中，如果使用的是基于 DAX 表达式的动态安全，“其他用户”仅显示不同的结果  。 


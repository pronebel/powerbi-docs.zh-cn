---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464323"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>在 Power BI Desktop 中验证角色
创建角色后，请在 Power BI Desktop 中测试角色结果。

1. 从“建模”选项卡中，选择“以角色身份查看”。 

    ![选择“以角色身份查看”](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    “以角色身份查看”窗口将显示，在其中你可以看到已创建的角色。

    ![“以角色身份查看”窗口](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. 选择创建的角色，然后选择“确定”应用该角色。 

   报表呈现与该角色相关的数据。

4. 你还可以选择其他用户，并提供给定用户。 

    ![选择“其他用户”](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   最好提供用户主体名称 (UPN)，因为 Power BI 服务和 Power BI 报表服务器使用该名称。

   在 Power BI Desktop 中，如果使用的是基于 DAX 表达式的动态安全，“其他用户”仅显示不同的结果。 

5. 选择“确定”。 

   报表会基于用户能够查看的内容进行呈现。




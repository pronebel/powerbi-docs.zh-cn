---
title: 购买和分配 Power BI Pro 许可证
description: 了解如何购买和分配 Power BI Pro 用户许可证，以便用户可以访问 Power BI 服务中的所有内容并与同事协作。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 55cdfad221aef276c790e98de83dd844bc13aafe
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958650"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>购买和分配 Power BI Pro 用户许可证

Power BI Pro 是独立的用户许可证，它允许用户读取其他用户在 Power BI 服务中发布的报表和仪表板并与之交互，还允许用户与其他 Power BI Pro 用户共享内容和进行协作。 只有具有 Power BI Pro 用户许可证的用户才能发布或与其他用户共享内容，或使用其他用户创建的内容，除非该内容托管于 Power BI Premium 容量中。 有关详细信息，请参阅 [Power BI 定价](https://powerbi.microsoft.com/pricing/)的“Power BI 功能比较”  部分。

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>购买和分配 Power BI Pro 用户许可证

本文介绍如何在 Microsoft 365 管理中心购买 Power BI Pro 用户许可证，并介绍管理员将这些许可证分配给单个用户的两种方法：Microsoft 365 管理中心和 Azure 门户（选择一项）。

### <a name="prerequisites"></a>先决条件

要在 Microsoft 365 管理中心购买并分配许可证，你必须是 Microsoft 365 中的[全局管理员或计费管理员](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)角色的成员  。

要在 Azure 门户中分配许可证，则必须是 Power BI 用于 Azure Active Directory 查找的 Azure 订阅的所有者。

### <a name="purchase-licenses-in-microsoft-365"></a>在 Microsoft 365 中购买许可证

按照以下步骤在 Microsoft 365 管理中心购买 Power BI Pro 许可证：

1. 打开 [MIcrosoft 365 管理中心](https://portal.office.com/adminportal/home#/homepage)。

2. 在导航窗格中，选择“账单” > “订阅”   。

    ![导航窗格](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. 在“订阅”页面的右上角，选择“添加订阅”   。

    ![订阅](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. 找到所需的订阅套餐：

    在“企业套件”下选择“Office 365 企业版 E5”   。

    ![Office E5 订阅](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    在“其他计划”下选择“Power BI Pro”   。

    ![Power BI 订阅](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. 将鼠标悬停在所需订阅的省略号 ( **. . .** ) 处，选择“立即购买”  。

    ![立即购买](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. 根据你的计费偏好，选择“按月付费”或“按年付费”   。

7. 在“需要多少个用户?”下，输入所需的许可证数量，然后选择“立即签出”完成此交易   。

8. 验证获取的订阅是否已在“订阅”页面上列出  。

   ![获取的订阅](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. 若要在最初购买后添加更多许可证，请从“订阅”  页面中选择“Power BI Pro”  ，然后选择“添加/删除许可证”  。

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 管理中心分配许可证

按照以下步骤将 Power BI Pro 许可证分配给个人用户帐户：

1. 打开 [MIcrosoft 365 管理中心](https://portal.office.com/adminportal/home#/homepage)。

2. 在导航窗格中，展开“用户”  ，然后选择“活动用户”  。

    ![活跃用户](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. 选择一个用户，然后在“产品许可证”  下选择“编辑”  。

    ![编辑产品许可证](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. 在“Power BI Pro”下将设置切换为“开”，然后选择“保存”    。

    ![打开产品许可证](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. 根据所选帐户的**状态**，验证 Power BI Pro 许可证是否成功分配。

    ![验证许可证状态](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>在 Azure 门户中分配许可证

按照以下步骤将 Power BI Pro 许可证分配给个人用户帐户：

1. 打开 [Azure 门户](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0)。

2. 在导航窗格中，选择“Azure Active Directory”  。

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. 在“Azure Active Directory”  下，选择“许可证”  。

    ![许可证](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. 在“许可证”  下，选择“所有产品”  ，然后选择“Power BI Pro”  以显示许可用户列表。

    ![许可证 - 所有产品](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. 选择“分配”  将 Power BI Pro 许可证添加到用户帐户。

    ![分配许可证](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>后续步骤

现已分配许可证，可以了解有关 Power BI Pro 的详细信息。

[组织中的 Power BI 许可](service-admin-licensing-organization.md)

[查找已登录的 Power BI 用户](service-admin-access-usage.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

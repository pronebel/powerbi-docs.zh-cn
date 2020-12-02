---
title: 购买和分配 Power BI Pro 许可证
description: 了解如何购买和分配 Power BI Pro 用户许可证，以便用户可以访问 Power BI 服务中的所有内容并与他人协作。
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 5845e56bdcb2257d67d541e35d26c9285a5e9319
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408127"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>购买和分配 Power BI Pro 用户许可证

>[!IMPORTANT]
>本文适用于管理员。 你是否准备好升级到 Power BI Pro 许可证？ 直接转到[开始使用 Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) 以设置帐户。

Power BI Pro 是一种单独的用户许可证，使用户能够读取他人已发布到 Power BI 服务的报表和仪表板并与之进行交互。 具有此许可证类型的用户可以与 Power BI Pro 用户共享内容并开展协作。 只有 Power BI Pro 用户才能发布或与其他用户共享内容，或使用其他用户创建的内容，除非 Power BI Premium 容量托管该内容。 有关可用许可证和订阅类型的详细信息，请参阅[组织中的 Power BI 许可](service-admin-licensing-organization.md)。

## <a name="purchase-power-bi-pro-user-licenses"></a>购买 Power BI Pro 用户许可证

本文介绍了如何在 Microsoft 365 管理中心购买 Power BI Pro 用户许可证。 购买许可证后，可以将其分配给 Microsoft 365 管理中心或 Azure 门户中的用户。

> [!NOTE]
> 从 2020 年 1 月 14 日开始，商业云客户可以使用面向 Power Platform 产品（Power BI、Power Apps 和 Power Automate）的自助服务购买、订阅和许可证管理功能。 有关详细信息，请参阅[自助购买常见问题解答](/microsoft-365/commerce/subscriptions/self-service-purchase-faq)。 若要启用或禁用自助购买功能，请参阅[启用或禁用自助注册和购买](./service-admin-disable-self-service.md)。

### <a name="prerequisites"></a>先决条件

若要在 Microsoft 365 管理中心购买并分配许可证，则必须是 Microsoft 365 中的[全局管理员或计费管理员](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)角色的成员。

要在 Azure 门户中分配许可证，则必须是 Power BI 用于 Azure Active Directory 查找的 Azure 订阅的所有者。

### <a name="purchase-licenses-in-microsoft-365"></a>在 Microsoft 365 中购买许可证

> [!NOTE]
> 如果通常通过批量许可协议（例如企业协议）购买许可证，并且想要接收发票而不是使用信用卡或银行帐户进行购买，则需要以不同方式提交订单。 请与 Microsoft 经销商合作，或通过批量许可服务中心来添加或删除许可证。 有关详细信息，请参阅[管理订阅许可证](/microsoft-365/commerce/licenses/buy-licenses?view=o365-worldwide)。

按照以下步骤在 Microsoft 365 管理中心购买 Power BI Pro 许可证：

1. 登录 [MIcrosoft 365 管理中心](https://admin.microsoft.com)。

2. 在“导航”菜单上，选择“计费” > “购买服务”。

3. 搜索或滚动以查找要购买的订阅。 你会发现“Power BI”位于页面底部附近“可能感兴趣的其他类别”下方。 选择链接以查看可供组织使用的 Power BI 订阅。

4. 选择“Power BI Pro”。

5. 在“购买服务”页面上，选择“购买”。

6. 根据你的付费方式，选择“按月付费”或“按年付费” 。

7. 在“需要多少个用户?”下，输入要购买的许可证数量，然后选择“立即签出”完成此交易 。

8. 若要验证你的购买情况，请前往“账单” > “产品和服务”并查找“Power BI Pro”。

9. 若要稍后添加更多许可证，请在“产品和服务”页面上查找“Power BI Pro”，然后选择“添加/删除”。


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 管理中心分配许可证

有关在 Microsoft 365 管理中心分配许可证的信息，请参阅[将许可证分配给用户](/office365/admin/manage/assign-licenses-to-users)。

对于来宾用户，请参阅[在“许可证”页上将许可证分配给用户](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page)。 在将 Pro 许可证分配给来宾用户之前，请联系 Microsoft 帐户代表，以确保符合与 Microsoft 达成的协议条款。

## <a name="assign-licenses-in-the-azure-portal"></a>在 Azure 门户中分配许可证

按照以下步骤将 Power BI Pro 许可证分配给个人用户帐户：

1. 登录 [Azure 门户](https://portal.azure.com/)。

2. 搜索并选择“Azure Active Directory”。

3. 在“Azure Active Directory”资源菜单上的“管理”下方，选择“许可证”。

4. 从“许可证 - 概述”资源菜单中选择“所有产品”，然后选择“Power BI Pro”以显示许可用户列表。

5. 从命令栏中选择“+ 分配”。 “分配许可证”页面上，先选择一个用户，然后选择“分配选项”为选择的用户帐户启用 Power BI Pro 许可证。

## <a name="next-steps"></a>后续步骤

- [组织中的 Power BI 许可](service-admin-licensing-organization.md)

 - [查找已登录的 Power BI 用户](service-admin-access-usage.md)

 - [以个人身份注册 Power BI](../fundamentals/service-self-service-signup-for-power-bi.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
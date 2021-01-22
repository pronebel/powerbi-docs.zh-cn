---
title: Power BI 和 Azure 流出量
description: 基于租户位置和 Power BI Premium，了解 Azure 出口费用和 Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Data from databases
ms.openlocfilehash: ec47968294e0fd905d1733bdb30ae1840069aed7
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597465"
---
# <a name="power-bi-and-azure-egress"></a>Power BI 和 Azure 流出量

Azure 数据中心的数据移出（流出）可能会产生带宽费用。 将 Power BI 与 Azure 数据源一起使用时，通过确保 Power BI 租户与 Azure 数据源位于同一区域，可以避免 Azure 出口费用。

将部署数据源的相同 Azure 区域中部署 Power BI 租户时，不会因计划刷新和 DirectQuery 交互而产生出口费用。 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>确定 Power BI 租户的所在位置

要了解 Power BI 租户的所在位置，请参阅 [Power BI 租户的所在位置](../admin/service-admin-where-is-my-tenant-located.md)一文。

对于 Power BI Premium Multi-Geo 客户，如果 Power BI 租户不在某些基于 Azure 的数据源的最佳位置，你可以在所需的 Azure 区域中部署 Power BI Premium Multi-Geo，并通过使 Power BI 租户和 Azure 数据源位于同一 Azure 区域来从中受益。

## <a name="next-steps"></a>后续步骤

有关 Power BI Premium 或 Multi-Geo 的详细信息，请查看以下资源：

* [Azure 带宽定价详细信息](https://azure.microsoft.com/pricing/details/bandwidth/)
* [什么是 Microsoft Power BI Premium？](../admin/service-premium-what-is.md)
* [如何购买 Power BI Premium](../admin/service-admin-premium-purchase.md)
* [Power BI Premium 的 Multi-Geo 支持（预览）](../admin/service-admin-premium-multi-geo.md)
* [我的 Power BI 租户位于何处？](../admin/service-admin-where-is-my-tenant-located.md)
* [Power BI Premium 常见问题解答](../admin/service-premium-faq.md)

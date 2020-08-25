---
title: 在 Power BI 中使用客户管理的密钥
description: 了解如何在 Power BI 中使用客户管理的密钥。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160917"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>在 Power BI 中使用客户管理的密钥

Power BI 会对静态数据和正在处理的数据进行加密。 默认情况下，Power BI 使用 Microsoft 托管密钥来加密数据。 组织可以选择使用自己的密钥对 Power BI 中的静态用户内容（从报表图像到高级容量中已导入的数据集）进行加密。 

## <a name="why-use-customer-managed-keys"></a>为什么使用客户管理的密钥
借助 Power BI 客户管理的密钥 (CMK)，组织可以满足其云服务提供商（本例中为 Microsoft）对静态数据加密的合规性要求。 CMK 使组织能够使用他们提供和管理的密钥来加密其 Power BI 用户内容。 撤销客户管理的密钥后，所有人（包括 Microsoft）在一小时内无法读取 Power BI 中的用户内容。 与 BYOK 产品/服务相比，CMK 还涵盖 Power BI Premium 容量以外的用户内容，它强制实施更严格的缓存策略，并且默认情况下针对所有容量启用 BYOK。 
 
## <a name="how-to-use-customer-managed-keys"></a>如何使用客户管理的密钥
若要选择 Power BI 客户管理的密钥，你的组织必须满足大小要求。 组织的全局管理员必须向 Microsoft 提交支持请求，或者他们可以联系组织的 Microsoft 帐户管理器以了解有关该过程的详细信息。  


## <a name="next-steps"></a>后续步骤

以下链接提供了对使用客户管理的密钥非常有用的信息：

* [对 Power BI 创建自己的加密密钥](service-encryption-byok.md)
* [配置 Power BI Premium 的 Multi-Geo 支持](service-admin-premium-multi-geo.md)
* [容量工作原理](service-premium-what-is.md#how-capacities-function)
* [增量刷新](service-premium-incremental-refresh.md)。

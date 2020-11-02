---
title: 在 Power BI 中使用客户管理的密钥
description: 了解如何在 Power BI 中使用客户管理的密钥。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 10/21/2020
LocalizationGroup: Premium
ms.openlocfilehash: fc93ae0f54bfe4f72ec18687829e9eb78dfaedd7
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349359"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>在 Power BI 中使用客户管理的密钥

Power BI 会对静态数据和正在处理的数据进行加密。 默认情况下，Power BI 使用 Microsoft 托管密钥来加密数据。 组织可以选择使用自己的密钥对 Power BI 中的静态用户内容（从报表图像到高级容量中已导入的数据集）进行加密。 

## <a name="why-use-customer-managed-keys"></a>为什么使用客户管理的密钥

借助 Power BI 客户管理的密钥 (CMK)，组织可以满足其云服务提供商（本例中为 Microsoft）对静态数据加密的合规性要求。 CMK 仅提供给新的 Power BI Premium 客户，它使组织能够使用自己提供和管理的密钥加密 Power BI 用户内容。 撤销客户管理的密钥后，所有人（包括 Microsoft）在一小时内无法读取 Power BI 中的用户内容。 与 BYOK 产品/服务相比，除了导入到托管在高级容量上的报表和数据集的客户数据之外，CMK 还涵盖了服务生成的用户内容；它强制执行更严格的缓存策略，并且只能应用单个密钥来加密所有数据。


## <a name="how-to-use-customer-managed-keys"></a>如何使用客户管理的密钥
若要选择使用 Power BI 客户管理的密钥，你的组织必须与组织的 Microsoft 帐户管理员联系，验证组织是否满足启用 CMK 所需的特定大小要求。  


## <a name="next-steps"></a>后续步骤

以下链接提供了对使用客户管理的密钥非常有用的信息：

* [对 Power BI 创建自己的加密密钥](service-encryption-byok.md)
* [配置 Power BI Premium 的 Multi-Geo 支持](service-admin-premium-multi-geo.md)
* [容量工作原理](service-premium-what-is.md#how-capacities-function)
* [增量刷新](service-premium-incremental-refresh.md)。

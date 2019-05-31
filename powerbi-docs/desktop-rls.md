---
title: 了解 Power BI Desktop 行级别安全性 (RLS)
description: 如何为导入的数据集和 Power BI Desktop 内的 DirectQuery 配置行级别安全性。
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 05/03/2018
LocalizationGroup: Create reports
ms.openlocfilehash: e53805c8aa76fd2fe80246eb0974ec73bedd4d4f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769571"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Power BI Desktop 行级别安全性 (RLS)

Power BI Desktop 行级别安全性 (RLS) 可用于限制给定用户的数据访问。 筛选器可限制行级别上的数据。 你可以定义角色中的筛选器。

现在，你可以使用 Power BI Desktop 为导入到 Power BI 的数据模型配置 RLS。 你还可以在使用 DirectQuery（如 SQL Server）的数据集上配置 RLS。 在此之前，你只能在 Power BI 外的本地 Analysis Services 模型中实现 RLS。 对于 Analysis Services 的实时连接，你可以在本地模型上配置行级别安全性。 实时连接数据集不会显示安全选项。

> [!IMPORTANT]
> 如果在 Power BI 服务中定义了角色和规则，则需要在 Power BI Desktop 中重新创建这些角色，然后将报表发布到服务。

了解有关 [Power BI 服务中的 RLS](service-admin-rls.md) 选项的详细信息。

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>后续步骤

[Power BI 服务行级别安全性 (RLS)](service-admin-rls.md)  

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
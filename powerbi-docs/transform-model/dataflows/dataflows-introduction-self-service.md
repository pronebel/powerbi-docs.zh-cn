---
title: 数据流和自助数据准备简介
description: 概述什么是 Power BI 数据流以及何时使用它们
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b603c0a2ad300145db6342acac3473a2f4a567c6
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91637523"
---
# <a name="introduction-to-dataflows-and-self-service-data-prep"></a>数据流和自助数据准备简介

随着数据量的不断增长，将数据转换为格式正确且可操作信息的挑战也随之增加。 我们希望数据已准备好用于分析，可填充视觉效果、报告和仪表板，以便我们可以快速将数据量转化为可操作的见解。 借助 Power BI 中针对大数据的自助服务数据准备，用户只需单击几下即可将数据转换成 Power BI 见解。

![数据流](media/dataflows-introduction-self-service-flow.png)

## <a name="when-to-use-dataflows"></a>何时使用数据流

数据流旨在支持以下方案：

* 创建可重用的转换逻辑，该逻辑可由 Power BI 中的许多数据集和报表共享。 数据流可提升基础数据元素的可重用性，从而无需与云或本地数据源建立单独的连接。

* 在你自己的 Azure Data Lake Gen 2 存储中公开数据，以便将其他 Azure 服务连接到原始基础数据。

* 通过强制分析人员连接到数据流而不是基础系统，来创建单个事实源，从而使你可以控制访问哪些数据以及如何向报表创建者公开数据。 你还可以将数据映射到行业标准定义，以便创建整洁的精选视图，这些视图可用于 Power Platform 中的其他服务和产品。

* 如果你要处理大量数据并大规模执行 ETL，使用 Power BI Premium 的数据流可以更有效地进行缩放，并为你提供更大的灵活性。 数据流支持多种云源和本地源。 

* 防止分析人员直接访问基础数据源。 由于报表创建者可以在数据流的基础上进行构建，因此你最好只允许个别用户访问基础数据源，然后为分析人员提供访问数据流的权限，使其可以在数据流的基础上进行构建。 这种方法可以减少基础系统的负载，使管理员能够更好地控制何时通过刷新来加载系统。

创建数据流后，可以使用 Power BI Desktop 和 Power BI 服务创建数据集、报表、仪表板和应用，利用 Common Data Model 深入了解业务活动。 数据流刷新计划直接从创建数据流的工作区进行管理，就像数据集一样。

## <a name="next-steps"></a>后续步骤
本文概述了 Power BI 中大数据的自助数据准备，以及可以使用它的多种方法。 

以下文章提供有关数据流和 Power BI 的详细信息：

* [创建数据流](dataflows-create.md)
* [配置和使用数据流](dataflows-configure-consume.md)
* [将数据流存储配置为使用 Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [数据流的高级功能](dataflows-premium-features.md)
* [使用数据流的 AI](dataflows-machine-learning-integration.md)
* [数据流限制和注意事项](dataflows-features-limitations.md)


有关通用数据模型的详细信息，可以阅读其概述文章：
* [Common Data Model - 概述](https://docs.microsoft.com/powerapps/common-data-model/overview)
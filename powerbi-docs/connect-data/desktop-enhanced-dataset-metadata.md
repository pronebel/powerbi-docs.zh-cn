---
title: 在 Power BI Desktop 中使用增强的数据集元数据
description: 本文介绍了如何在 Power BI 中使用增强的数据集元数据。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/22/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 67141f67be85f5c292118d4e88cfe3c5a949ce4f
ms.sourcegitcommit: ff981839e805f523748b7e71474acccf7bdcb04f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "91019851"
---
# <a name="using-enhanced-dataset-metadata"></a>使用增强的数据集元数据

Power BI Desktop 创建报表时，还会使用相应的 PBIX 和 PBIT 文件创建数据集元数据。 以前，元数据以特定于 Power BI Desktop 的格式存储。 它使用 Base-64 编码的 M 表达式和数据源，并对元数据的存储方式进行了假设。

随着增强的数据集元数据功能的发布，许多这些限制都已消除。 打开文件时，PBIX 文件会自动升级到增强的元数据。 借助增强的数据集元数据，由 Power BI Desktop 创建的元数据根据[表格对象模型](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)使用与 Analysis Services 表格模型使用的格式相似的格式。


增强的数据集元数据功能具有战略性和基础性，因为未来的 Power BI 功能将基于其元数据构建。 始终都可从增强的数据集元数据中获益的一些其他功能包括用于管理 Power BI 数据集的 [XMLA 读/写](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)，以及将 Analysis Services 工作负载迁移到 Power BI 以受益于下一代功能。


## <a name="next-steps"></a>后续步骤

可以使用 Power BI Desktop 执行各种操作。 有关其功能的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的新增功能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop 的查询概述](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的数据类型](desktop-data-types.md)
* [使用 Power BI Desktop 成型和合并数据](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常见查询任务](../transform-model/desktop-common-query-tasks.md)
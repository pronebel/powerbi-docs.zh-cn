---
title: 在 Power BI Desktop 中使用增强的数据集元数据
description: 本文介绍了如何在 Power BI 中使用增强的数据集元数据。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906950"
---
# <a name="using-enhanced-dataset-metadata"></a>使用增强的数据集元数据

Power BI Desktop 创建报表时，还会使用相应的 PBIX 和 PBIT 文件创建数据集元数据。 以前，元数据以特定于 Power BI Desktop 的格式存储。 元数据使用了 Base64 编码的 M 表达式和数据源。 Power BI 对元数据的存储方式进行了假设。

随着增强的数据集元数据功能的发布，许多这些限制都已消除。 打开文件时，PBIX 文件会自动升级到增强的元数据。 借助增强的数据集元数据，由 Power BI Desktop 创建的元数据根据[表格对象模型](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)使用与 Analysis Services 表格模型使用的格式相似的格式。


增强的数据集元数据功能具有战略性和基础性。 未来的 Power BI 功能将基于其元数据构建。 这些其他功能从增强型数据集元数据中获益：

- [XMLA 读取/写入](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)，用于管理 Power BI 数据集
- 将 Analysis Services 工作负载迁移到 Power BI，从下一代功能中受益。

## <a name="limitations"></a>限制
在提供增强型元数据支持之前，对于 SQL Server、Oracle、Teradata 和旧 HANA 连接，Power BI Desktop 向数据模型添加了本机查询。 此查询由 Power BI 服务数据模型使用。 借助增强型元数据支持，Power BI 服务数据模型在运行时重新生成本机查询。 而不使用 Power BI Desktop 创建的查询。 在大多数情况下，此检索可正确解析自身，但某些转换需要读取基础数据才能运行。 你可能会在以前运行的报表中看到一些错误。 例如，错误显示： 

“无法将 Dimension City 表中的 M 查询转换为本机源查询。 请稍候重试或联系支持人员。 如果联系支持人员，请提供以下详细信息。” 

可以在 Power BI Desktop 中的三个不同位置修复查询：

- 应用更改或执行刷新时。
- 在 Power Query 编辑器的警告栏中，提示表达式无法折叠到数据源。
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="应用查询更改消息的屏幕截图：无法将表达式折叠到数据源。":::
- 打开报表以检查是否具有不受支持的查询时运行评估。 运行这些评估可能会影响性能。


## <a name="next-steps"></a>后续步骤

可以使用 Power BI Desktop 执行各种操作。 有关其功能的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的新增功能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop 的查询概述](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的数据类型](desktop-data-types.md)
* [使用 Power BI Desktop 成型和合并数据](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常见查询任务](../transform-model/desktop-common-query-tasks.md)

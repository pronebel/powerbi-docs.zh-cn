---
title: 数据流最佳做法
description: 最佳做法链接的集合和数据流指南
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 11/13/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 53a8573138a87f8be65183e0571077a02ac0715d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418178"
---
# <a name="dataflows-best-practices"></a>数据流最佳做法

Power BI 数据流是一种以企业为中心的数据准备解决方案，能够提供可供使用、重用和集成的数据生态系统。 本文提供了最佳做法列表，其中包含文章和其他信息的链接，这些链接将帮助你充分了解和使用数据流。


## <a name="dataflows-best-practices-table-and-links"></a>数据流最佳做法表和链接

下表提供了文章链接的集合，这些文章描述了在创建或使用数据流时的最佳做法。 这些链接包括有关开发业务逻辑、开发复杂的数据流、数据流的重用以及如何使用数据流实现企业规模的信息。


|**主题**  |**指南区域**  |**文章或内容的链接**  |
|---------|---------|---------|
|Power Query     | 提示和技巧，用于充分利用数据整理经验        |[Power Query 最佳做法](https://docs.microsoft.com/power-query/best-practices)        |
|利用计算实体     |在数据流中使用计算实体具有性能优势         |[计算实体方案](https://docs.microsoft.com/power-query/dataflows/computed-entities-scenarios)         |
|开发复杂的数据流     |用于开发大规模高性能数据流的模式         |[复杂数据流](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|重用数据流     |模式、指南和用例         |[重用数据流](https://docs.microsoft.com/power-query/dataflows/best-practices-reusing-dataflows)         |
|大规模实现     |大规模使用和指导以补充企业体系结构         |[使用数据流的数据仓库](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|利用增强的计算     |潜在地将数据流性能提高多达 25 倍         |[增强的计算引擎](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|优化工作负载设置     |通过了解可以利用的杠杆来最大程度地提高性能，从而充分利用数据流基础结构         |[数据流工作负载配置](dataflows-premium-workload-configuration.md)         |
|联接和展开表     |创建高性能联接         |[优化展开表操作](https://docs.microsoft.com/power-query/optimize-expanding-table-columns)         |
|查询折叠指南     |使用源系统加快转型         |[折叠查询](https://docs.microsoft.com/power-query/power-query-folding)         |
|使用数据分析     |了解列质量、分发和配置文件         |[数据事件探查工具](https://docs.microsoft.com/power-query/data-profiling-tools)         |
|实现错误处理     |开发功能强大的数据流，灵活刷新错误，并提供建议         |[常见错误的模式](https://docs.microsoft.com/power-query/dealing-with-errors)  </br> [复杂错误处理](https://docs.microsoft.com/power-query/error-handling)      |
|使用“架构”视图      |使用宽表并执行架构级别的操作时，可改进创作体验         |[“架构”视图](https://docs.microsoft.com/power-query/schema-view)         |
|||


        
## <a name="next-steps"></a>后续步骤

以下文章提供有关数据流和 Power BI 的详细信息：

* [数据流和自助数据准备简介](dataflows-introduction-self-service.md)
* [创建数据流](dataflows-create.md)
* [配置和使用数据流](dataflows-configure-consume.md)
* [数据流的高级功能](dataflows-premium-features.md)
* [将数据流存储配置为使用 Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [使用数据流的 AI](dataflows-machine-learning-integration.md)
* [数据流限制和注意事项](dataflows-features-limitations.md)
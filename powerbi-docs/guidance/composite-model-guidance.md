---
title: Power BI Desktop 中的复合模型指南
description: 用于开发复合模型的指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/24/2019
ms.openlocfilehash: e4ddc487f81835edfdc5ad8a4074a91204ee0336
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97884777"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的复合模型指南

本文面向开发 Power BI 复合模型的数据建模人员。 它介绍了复合模型用例，并提供了设计指南。 具体而言，本指南旨在帮助你确定复合模型是否适合你的解决方案。 如果适合，本文还将帮助你设计最佳模型。

> [!NOTE]
> 本文不涵盖对复合模型的介绍。 如果你不完全熟悉复合模型，建议先阅读[在 Power BI Desktop 中使用复合模型](../transform-model/desktop-composite-models.md)一文。
>
> 由于复合模型至少包含一个 DirectQuery 源，因此，必须深入了解[模型关系](../transform-model/desktop-relationships-understand.md)、[DirectQuery 模型](../connect-data/desktop-directquery-about.md)和 [DirectQuery 模型设计指南](directquery-model-guidance.md)。

## <a name="composite-model-use-cases"></a>复合模型用例

最好尽可能在“导入”模式下开发模型。 此模式提供最大的设计灵活性和最佳性能。

但是，不能通过“导入”模型来解决与大型数据卷或近实时数据报告相关的问题。 在这两种情况下，都可以考虑使用 DirectQuery 模型，前提是数据存储在 [DirectQuery 模式支持的](../connect-data/power-bi-data-sources.md)单一数据源中。

此外，还可以考虑在以下情况下开发复合模型。

- 模型可以是 DirectQuery 模型，但需要提高性能。 在复合模型中，可以通过为每个表配置适当的存储来提高性能。 还可以添加[聚合](../transform-model/desktop-aggregations.md)。 本文稍后会介绍这两种优化。
- 你希望将 DirectQuery 模型与必须导入到该模型中的其他数据组合在一起。 导入的数据可以从其他数据源或计算表中加载。
- 需要将两个或多个 DirectQuery 数据源合并到单个模型中。

> [!NOTE]
> 复合模型无法合并实时连接源或 DirectQuery 分析数据库源。 实时连接源包括[外部托管模型](../connect-data/service-datasets-understand.md#external-hosted-models)和 Power BI 数据集。 DirectQuery 分析数据库源包括 SAP Business Warehouse 和 SAP HANA。

## <a name="optimize-model-design"></a>优化模型设计

可以通过配置表[存储模式](../transform-model/desktop-storage-mode.md)，并添加[聚合](../transform-model/desktop-aggregations.md)来优化复合模型。

### <a name="table-storage-mode"></a>表存储模式

在复合模型中，可以为每个表配置存储模式（计算表除外）：

- **DirectQuery**：建议为表示大数据卷的表或需要提供近实时结果的表设置此模式。 数据永远不会导入这些表中。 通常，这些表是用于汇总的事实类型表。
- **导入**：建议为维度类型表（用于筛选和分组的表）设置此模式。 事实上，这是基于 DirectQuery 模式不支持的源的表的唯一选项。 计算表始终为导入表。
- **双**：建议为维度类型表设置此模式，在可能的情况下，将与来自同一源的 DirectQuery 事实类型表一起查询这些表。

Power BI 查询复合模型时，有几种可能的场景：

- **仅查询导入或双重表**：从模型缓存中检索所有数据。 它将提供尽可能快的性能。 这种情况在筛选器或切片器视觉对象查询的维度类型表中很常见。
- **查询同一源中的双重表或 DirectQuery 表**：通过向 DirectQuery 源发送一个或多个本机查询来检索所有数据。 它将提供尽可能快的性能，尤其是在源表上存在适当的索引时。 这种情况在与双重维度类型表和 DirectQuery 事实类型表相关的查询中很常见。 这些是源组内查询，因此，所有一对一关系或一对多关系都会被评估为[常规关系](../transform-model/desktop-relationships-understand.md#regular-relationships)。
- **所有其他查询**：这些查询涉及跨源组关系。 这可能是因为导入表与 DirectQuery 表相关，或者双重表与不同源中的 DirectQuery 表相关，在这种情况下，其行为与导入表类似。 所有关系均评估为[有限关系](../transform-model/desktop-relationships-understand.md#limited-relationships)。 这也意味着，应用于非 DirectQuery 表的分组必须作为虚拟表发送到 DirectQuery 源。 在这种情况下，本机查询可能效率低下，尤其是对于大型分组集。 而且，它可能会在本机查询中公开敏感数据。

总之，我们建议：

- 请仔细考虑一下，复合模型是正确的解决方案（虽然它允许不同数据源的模型级集成），但它还引入了可能具有各种后果的设计复杂性
- 当表是存储大型数据卷的事实类型表，或者它需要提供近实时结果时，请将存储模式设置为“DirectQuery” 
- 当表为维度类型表，并且将与基于相同源的 DirectQuery  事实类型表一同查询，请将存储模式设置为“双重” 
- 配置适当的刷新频率，使双重表（以及任何从属的计算表）的模型缓存与源数据库保持同步
- 尽量确保数据源（包括模型缓存）之间的数据完整性；有限关系将在相关列值不匹配时消除行
- 使用适当的索引优化 DirectQuery 数据源来实现高效联接、筛选和分组
- 如果存在截获本机查询的风险，请不要将敏感数据加载到导入表或双重表中；有关详细信息，请参阅[在 Power BI Desktop 中使用复合模型（安全隐患）](../transform-model/desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>聚合

可以在复合模型中向 DirectQuery 表添加聚合。 聚合缓存在模型中，因此它们表现为导入表（尽管它们不能像模型表那样使用）。 其目的是提高“更高粒度”查询的性能。 有关详细信息，请参阅 [Power BI Desktop 中的聚合](../transform-model/desktop-aggregations.md)。

建议聚合表遵循基本规则：其行计数应至少比基础表小 10 倍。 例如，如果基础表存储了十亿行，则聚合表不应超过一亿行。 此规则确保相对于创建和维护聚合表的成本而言，有足够的性能增益。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [在 Power BI Desktop 中使用复合模型](../transform-model/desktop-composite-models.md)
- [Power BI Desktop 中的模型关系](../transform-model/desktop-relationships-understand.md)
- [Power BI Desktop 中的 DirectQuery 模型](../connect-data/desktop-directquery-about.md)
- [在 Power BI Desktop 中使用 DirectQuery](../connect-data/desktop-use-directquery.md)
- [Power BI Desktop 中的 DirectQuery 模型疑难解答](../connect-data/desktop-directquery-troubleshoot.md)
- [Power BI 数据源](../connect-data/power-bi-data-sources.md)
- [Power BI Desktop 中的存储模式](../transform-model/desktop-storage-mode.md)
- [Power BI Desktop 中的聚合](../transform-model/desktop-aggregations.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)

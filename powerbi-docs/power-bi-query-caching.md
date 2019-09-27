---
title: 在 Power BI Premium 中查询缓存
description: 在 Power BI Premium 中查询缓存
author: KesemSharabi
ms.author: maggies
manager: rkarlin
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/16/2019
LocalizationGroup: ''
ms.openlocfilehash: 489069df43d2c09f6f5551987a61353e095aff7a
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71076178"
---
# <a name="query-caching-in-power-bi-premiumembedded"></a>在 Power BI Premium/Embedded 中查询缓存

具有 Power BI Premium 或 Power BI Embedded 的组织可使用查询缓存来加快与数据集关联的报表的速度。 查询缓存会指示 Premium/Embedded 容量使用其本地缓存服务来维护查询结果，避免基本数据源计算这些结果。

> [!IMPORTANT]
> 仅可在 Power BI Premium 或 Power BI Embedded 上使用查询缓存。 它不可用于使用 Azure Analysis Services 或 SQL Server Analysis Services 的 LiveConnect 数据集。

缓存的查询结果特定于用户和数据集上下文，且始终遵循安全规则。 目前，该服务仅对你登陆的初始页面进行查询缓存。 换言之，当你与报表进行交互时，不缓存查询。 查询缓存遵循[个人书签](consumer/end-user-bookmarks.md#personal-bookmarks)和[永久筛选器](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)，因此将缓存个性化报告生成的查询。 缓存查询后，还可利用相同查询所支持的[仪表板磁贴](service-dashboard-tiles.md)。 在频繁访问或无需频繁访问某数据集时，这尤其可提升性能。 查询缓存还可降低查询总数，从而减少 Premium/Embedded 容量上的负载。

你可在 Power BI 服务中数据集的“设置”页面上控制查询缓存行为。 可进行两种设置：

- 关：不对此数据集使用查询缓存。

- 开：对此数据集使用查询缓存。

![缓存查询对话框](media/power-bi-query-caching/power-bi-query-caching.png)

## <a name="considerations-and-limitations"></a>注意事项和限制

- 将缓存设置从“开”更改为“关”后，会从容量缓存中删除之前为数据集保存的所有查询结果。 你可显式关闭缓存，也可通过将管理员设置为“关”的容量默认设置进行还原来实现此目的。 将其关闭会导致任何报表下次针对此数据集运行查询出现短暂的延迟。 延迟原因是这些报表查询是按需运行的且不使用已保存的结果。 而且，所需的数据集可能需要加载到内存中，才能用于查询。
- 刷新查询缓存时，Power BI 必须对基础数据模型运行查询以获取最新结果。 如果大量数据集启用了查询缓存，且 Premium/Embedded 容量负载较重，则缓存刷新期间可能会出现一些性能下降。 性能下降是由于执行的查询量增加。

## <a name="next-steps"></a>后续步骤

* [什么是 Power BI Premium？](service-premium-what-is.md)
* [Azure 中的 Power BI Embedded 是指什么？](developer/azure-pbie-what-is-power-bi-embedded.md)
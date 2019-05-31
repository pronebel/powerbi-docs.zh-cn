---
title: 在 Power BI Premium 中查询缓存
description: 在 Power BI Premium 中查询缓存
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: c981a3e2a05129a470c8d26675226bfb42c1bb68
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769533"
---
# <a name="query-caching-in-power-bi-premium"></a>在 Power BI Premium 中查询缓存

具有 Power BI Premium 的组织可使用查询缓存来加快与数据集关联的报表的速度  。 查询缓存会指示高级容量使用其本地缓存服务来维护查询结果，避免基本数据源计算这些结果。

> [!IMPORTANT]
> 仅可在 Power BI Premium 上使用查询缓存。 它不可用于使用 Azure Analysis Services 或 SQL Server Analysis Services 的 LiveConnect 数据集。

缓存的查询结果特定于用户和数据集上下文，且始终遵循安全规则。 目前，该服务仅对你登陆的初始页面进行查询缓存。 换言之，当你与报表进行交互时，不缓存查询。 缓存会反映出个人书签和永久筛选器。 缓存查询后，还可利用相同查询所支持的[仪表板磁贴](service-dashboard-tiles.md)。 在频繁访问或无需频繁访问某数据集时，这尤其可提升性能。 查询缓存还可降低查询总数，从而减少高级容量上的负载。

你可在 Power BI 服务中数据集的“设置”页面上控制查询缓存行为  。 它具有两个可能的设置：

- 关  ：不对此数据集使用查询缓存。

- 开  ：对此数据集使用查询缓存。

![缓存查询对话框](media/power-bi-query-caching/power-bi-query-caching.png)

> [!NOTE]
> 将缓存设置从“开”更改为“关”后，会从容量缓存中删除之前为数据集保存的所有查询结果   。 你可显式关闭缓存，也可通过将管理员设置为“关”的容量默认设置进行还原来实现此目的  。 将其关闭会导致任何报表下次针对此数据集运行查询出现短暂的延迟。 延迟原因是这些报表查询是按需运行的且不使用已保存的结果。 而且，所需的数据集可能需要加载到内存中，才能用于查询。



---
title: Power BI 数据流的最佳做法
description: Power BI 数据流的最佳做法
author: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 4bbc8b71455d01405854304dd4b889f664ce8575
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877292"
---
# <a name="dataflows-best-practice"></a>数据流最佳实践

本文介绍了在 Power BI 中设计数据流的最佳做法。 可以使用本指南了解如何创建数据流，如何将这些做法应用于你自己的数据流。

> [!NOTE]
> 本文中所述的建议是指导原则。 对于本文中的每个最佳做法，可能有合理的理由偏离此指导。 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>拆分引入和转换以使用增强的计算引擎

当创建数据流时，你可能会想要在一个位置创建包含所有实体、转换、联接和增强功能的单个数据流。 对于较小的数据集，单个数据流可能有效。 但在处理较大的数据量时，执行联接或某些转换有时可能会遇到限制或内存限制。 为了解决这些问题，为扩展到更大数据量的 Power BI Premium 用户发布了增强的引擎。 增强的计算引擎仅适用于链接的实体或计算的实体，因此，为引入创建单独的数据流以及链接的工作流以执行所有复杂的合并和转换可以受益于此增强的引擎。

拆分数据流对于诊断和调试刷新问题也很有用，尤其是在使用具有限制的源时。

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>执行可使用增强的计算引擎的操作

确保使用增强的计算引擎，方法是确保先在计算实体中执行联接和筛选转换，然后再执行其他类型的转换。

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>连接到 SharePoint 时拆分数据流

当使用 SharePoint 并连接到多个文件时，你可能会注意到偶尔出现的故障。 SharePoint 会限制请求，确保它保持可靠且响应迅速。 因此，从 SharePoint 连接到 Excel 文件时，你可能倾向于下载单个数据流中的所有文件。 如果要下载的文件数超过 20 个，请创建两个或更多数据流以拆分刷新负载，并克服 SharePoint 限制。

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>避免为同一工作区中的链接实体计划刷新

如果你经常被锁在包含链接实体的数据流之外，则可能是由于同一工作区内的相应依赖数据流在数据流刷新期间被锁定。 此类锁定提供事务准确性，可确保两个数据流都成功刷新，但会阻止你编辑。 

如果为链接的数据流设置了单独的计划，则数据流可能会不必要地刷新，并阻止你编辑数据流。 有两个建议可避免此问题： 

* 避免为源数据流所在工作区中的链接数据流设置刷新计划
* 如果要单独配置刷新计划，并希望避免锁定行为，请在单独的工作区中分离数据流。

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>为引入、转换创建单独的工作区

若要使多个用户有权访问基础数据流数据，而不允许访问基础源系统的原始数据，请创建包含需要共享的所有数据的单独工作区，并分配权限。 当前不支持单个数据流权限。

### <a name="ensure-capacity-is-in-the-same-region"></a>确保容量在同一区域中

数据流当前不支持多个地理区域。 必须在 Power BI 租户所在的区域中创建高级容量。

### <a name="separate-on-premises-sources-from-cloud-sources"></a>从云源分离本地源

除了前面所述的最佳实践，你还可以为每种类型的源（如本地、云、SQL Server、Spark、Dynamics 等）创建单独的数据流。 强烈建议按数据源类型拆分数据流。 这种按源类型进行拆分有助于快速排查问题，并在刷新数据流时避免内部限制。

### <a name="separate-dataflows-into-a-separate-capacity"></a>将数据流拆分为单独的容量

如果遇到限制，或由于容量的内存限制而导致数据流经常失败，请考虑拆分数据流，或扩展高级容量以增加额外的内存。

## <a name="next-steps"></a>后续步骤

本文提供了有关数据流的最佳做法的信息。 有关数据流的详细信息，以下文章可能有所帮助：

* [数据流自助服务数据准备](service-dataflows-overview.md)
* [在 Power BI 中创建和使用数据流](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用计算实体](service-dataflows-computed-entities-premium.md)
* [将数据流与本地数据源配合使用](service-dataflows-on-premises-gateways.md)

有关 CDM 开发和教程资源的信息，请参阅以下内容：
* [通用数据模型 - 概述](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM 文件夹](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM 模型文件定义](https://go.microsoft.com/fwlink/?linkid=2045521)


有关 Power Query 和计划刷新的详细信息，可以阅读以下文章：
* [Power BI Desktop 中的查询概述](desktop-query-overview.md)
* [配置计划刷新](refresh-scheduled-refresh.md)

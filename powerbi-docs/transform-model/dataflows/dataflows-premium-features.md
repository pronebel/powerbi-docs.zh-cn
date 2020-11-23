---
title: 数据流的高级功能
description: 概述可用于 Power BI 数据流的 Premium 功能
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/13/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: eb5b4b37e59a771d65917df5706a7ebbca488d21
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94669077"
---
# <a name="premium-features-of-dataflows"></a>数据流的高级功能

Power BI Pro 和 Power BI Premium 用户支持数据流。 某些功能仅在 Power BI Premium 订阅中可用。 本文详细介绍了 Premium 专用功能及其用途。 

以下功能仅在 Power BI Premium 中可用：

* 增强的计算引擎
* 直接查询
* 计算实体
* 链接实体
* 增量刷新

以下各节详细介绍了这些功能。

## <a name="the-enhanced-compute-engine"></a>增强的计算引擎

Power BI 中增强的计算引擎使 Power BI Premium 订阅者能够使用其容量优化数据流的使用。 使用增强的计算引擎具有以下优势：

* 大大减少了对计算实体执行长时间运行的 ETL 步骤所需的刷新时间，例如执行“联接”、“去重”、“筛选”和“分组”操作   
* 对实体执行 DirectQuery 查询

默认情况下，增强的计算引擎处于“打开”状态。 如果增强型计算引擎未处于启用状态，可参阅下一部分，了解如何启用增强型计算引擎并获取常见问题的解答。

### <a name="using-the-enhanced-compute-engine"></a>使用增强的计算引擎

从 Power BI 服务的“容量设置”页中，在“数据流”部分启用增强的计算引擎。  默认情况下，增强的计算引擎处于“关闭”状态。 若要启用增强的计算引擎，请切换为“打开”（如下图所示），并保存设置。 

![打开增强的计算引擎](media/dataflows-premium-features/compute-engine-settings.png)

> [!IMPORTANT]
> 增强的计算引擎仅适用于 A3 及以上的 Power BI 容量。

打开增强的计算引擎后，返回到数据流。你应会看到，任何对基于现有链接实体创建的数据流（容量相同）执行复杂操作（如“联接”或“分组”操作）的计算实体的性能都有所提高 。 

若要充分利用计算引擎，请按以下方式将 ETL 阶段分成两个单独的数据流：

* **数据流 1** - 此数据流应该只从数据源接收所有必需的数据，并将其放入数据流 2。
* **数据流 2** - 在第二个数据流中执行所有 ETL 操作，但要确保引用数据流 1 且它应具有相同的容量。 你还要确保在执行任何其他操作之前，先执行可以折叠的操作（筛选、分组、去重、联接），确保计算引擎得到利用。

### <a name="common-questions-and-answers"></a>常见问题与解答

**问：** 我启用了增强的计算引擎，但刷新速度较慢。 为什么？

**答：** 如果你启用了增强的计算引擎，则对于刷新时间缓慢，可能有两种解释：

 * 启用增强的计算引擎后，它需要一些内存才能正常工作。 因此，可用于执行刷新的内存减少，增加了刷新排队的可能性，从而减少了可同时刷新的数据流的数量。 若要解决此问题，在启用增强计算时，增加为数据流分配的内存，以确保可用于并发数据流刷新的内存保持不变。

 * 导致刷新速度较慢的另一个原因是，计算引擎仅适用于现有实体。 如果数据流引用的数据源不是数据流，则不会出现速度提升。 性能不会得到提升，因为在某些大数据场景中，由于需要将数据传递到增强的计算引擎，因此从数据源进行的初始读取速度会比较慢。  

**问：** 我看不到增强的计算引擎的切换开关。 为什么？

**答：** 增强的计算引擎正在分阶段发布到世界各地的区域。 预计将于 2020 年底在所有区域实现支持。

**问：** 计算引擎支持哪些数据类型？

**答：** 增强的计算引擎和数据流当前支持以下数据类型。 如果数据流不使用以下数据类型之一，则刷新期间会发生错误：

* 日期/时间
* 小数
* 文本
* 整数
* 日期/时间/区域
* True/False
* 日期
* 时间

## <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>在 Power BI（预览版）中将 DirectQuery 用于数据流

可以使用 DirectQuery 直接连接到数据流，从而能直接连接到自己的数据流，而无需导入其数据。 

将 DirectQuery 用于数据流，可以让 Power BI 和数据流过程得到以下增强：

* 避免单独刷新计划 - DirectQuery 直接连接到数据流，无需创建导入的数据集。 因此，将 DirectQuery 与数据流一起使用意味着不再需要数据流和数据集的单独刷新计划，就能确保数据已同步。

* **筛选数据** - DirectQuery 对于处理数据流中经过筛选的数据视图非常有用。 如果要筛选数据以处理数据流中的一部分数据，可以使用 DirectQuery（和计算引擎）来筛选数据流数据，并处理筛选出的子集。


### <a name="using-directquery-for-dataflows"></a>将 DirectQuery 用于数据流

将 DirectQuery 用于数据流是一项预览功能，从 Power BI Desktop 2020 年 5 月版开始提供。 

若要将 DirectQuery 用于数据流，需要满足以下条件：

* 数据流必须位于已启用 Power BI Premium 的工作区中
* 必须打开计算引擎

### <a name="enable-directquery-for-dataflows"></a>为数据流启用 DirectQuery

为了确保数据流可用于 DirectQuery 访问，增强的计算引擎必须处于最优状态。 若要为数据流启用 DirectQuery，请将新的“增强的计算引擎设置”选项设置为“打开”。 下图展示的是正确选择的设置。

![对直接查询的精细控制](media/dataflows-premium-features/compute-engine-granular-control.png)

应用该设置后，请刷新数据流以让优化生效。

### <a name="considerations-and-limitations-for-directquery"></a>DirectQuery 的注意事项和限制

DirectQuery 和数据流存在一些已知限制：

* 在此功能的预览期间，部分客户在将 DirectQuery 用于数据流时可能会遇到超时或性能问题。 我们会在此预览期间积极地解决此类问题。

* 目前不支持具有导入和 DirectQuery 数据源的复合/混合模型。

* 大型数据流在查看可视化效果时可能会遇到超时问题。 遇到超时问题的大型数据流应使用导入模式。

* 在“数据源设置”下，如果使用 DirectQuery，数据流连接器将显示无效凭据。 这不会影响行为，并且数据集可以正常工作。 

## <a name="computed-entities"></a>计算实体

在 Power BI Premium 订阅中使用“数据流”时，可以执行“存储中计算”。 这让你能够对现有数据流执行计算，并返回让你能够专注于报表创建和分析的结果。

![计算实体](media/dataflows-premium-features/computed-entity.png)

若要执行“存储中计算”，首先必须创建数据流并将数据导入该 Power BI 数据流存储。 一旦具有包含数据的数据流后，就可以创建“计算实体”，它们是执行存储中计算的实体。

### <a name="considerations-and-limitations-of-computed-entities"></a>计算实体的注意事项和限制

* 使用组织的 Azure Data Lake Storage Gen2 帐户中创建的数据流时，仅当链接实体和计算实体位于同一存储帐户中时，这些实体才能正常工作。 

最佳做法如下：对由本地数据和云数据联接的数据执行计算时，为每个源创建一个新的数据流（一个用于本地，一个用于云），然后创建第三个数据流来合并/计算这两个数据源。

## <a name="linked-entities"></a>链接实体

与 Power BI Premium 订阅一起使用时，你可以引用现有数据流，从而可以使用计算实体对这些实体执行计算，或创建可在多个数据流中重复使用的“单个事实源”表。

## <a name="incremental-refresh"></a>增量刷新

可以将数据流设置为增量刷新，以避免每次刷新时都必须提取所有数据。 为此，请选择数据流，然后选择增量刷新图标。

![增量刷新](media/dataflows-premium-features/incremental-refresh.png)

设置增量刷新会向数据流添加用于指定日期范围的参数。 有关如何设置增量刷新的详细信息，请参阅[增量刷新](/power-query/dataflows/incremental-refresh)一文。

### <a name="considerations-for-when-not-to-set-incremental-refresh"></a>何时不设置增量刷新的注意事项

在以下情况下，请勿将数据流设置为增量刷新：

* 如果链接实体引用数据流，则不应使用增量刷新。 数据流不支持查询折叠（即使该实体启用了 DirectQuery）。 
* 引用数据流的数据集不应使用增量刷新。 一般来说，数据流刷新速度较快。 如果刷新时间比预期时间长，请考虑使用计算引擎和/或 DirectQuery 模式。

## <a name="next-steps"></a>后续步骤
以下文章提供有关数据流和 Power BI 的详细信息：

* [数据流最佳做法](dataflows-best-practices.md)
* [配置 Power BI Premium 数据流工作负载](dataflows-premium-workload-configuration.md)
* [数据流和自助数据准备简介](dataflows-introduction-self-service.md)
* [创建数据流](dataflows-create.md)
* [配置和使用数据流](dataflows-configure-consume.md)
* [将数据流存储配置为使用 Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [使用数据流的 AI](dataflows-machine-learning-integration.md)
* [数据流限制和注意事项](dataflows-features-limitations.md)
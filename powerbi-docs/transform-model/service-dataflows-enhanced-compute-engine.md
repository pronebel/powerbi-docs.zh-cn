---
title: 将增强的计算引擎用于数据流
description: 了解如何将 Power BI Premium 中增强的计算引擎用于数据流
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 06/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 7623be9f4eea3bd4d1a8c6fa7b4d1add3d41c783
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861512"
---
# <a name="the-enhanced-compute-engine"></a>增强的计算引擎

Power BI 中增强的计算引擎使 Power BI Premium 订阅者能够使用其容量优化数据流的使用。 使用增强的计算引擎具有以下优势：

* 大大减少了对计算实体执行长时间运行的 ETL 步骤所需的刷新时间，例如执行“联接”、“去重”、“筛选”和“分组”操作   
* 对实体执行 DirectQuery 查询（2020 年 2 月）

以下部分介绍如何启用增强的计算引擎，并回答常见问题。


## <a name="using-the-enhanced-compute-engine"></a>使用增强的计算引擎

从 Power BI 服务的“容量设置”页中，在“数据流”部分启用增强的计算引擎。  默认情况下，增强的计算引擎处于“关闭”状态。 若要将其打开，请切换到“打开”（如下图所示），并保存设置。 

![打开增强的计算引擎](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

> [!IMPORTANT]
> 增强的计算引擎仅适用于 A3 及以上的 Power BI 容量。

打开增强的计算引擎后，返回到数据流。你应会看到，任何对基于现有的链接实体创建的数据流（容量相同）执行复杂操作（如“联结”或“分组”操作）的计算实体的性能都有所提高。 

若要充分利用计算引擎，你应按照以下方式将 ETL 阶段分成两个单独的数据流：

* **数据流 1** - 此数据流应该只从数据源接收所有必需的数据，并将其放入数据流 2。
* **数据流 2** - 在第二个数据流中执行所有 ETL 操作，但要确保引用数据流 1 且它应具有相同的容量。 你还要确保在执行任何其他操作之前，先执行可以折叠的操作（筛选、分组、去重、联接），确保计算引擎得到利用。

## <a name="common-questions-and-answers"></a>常见问题与解答

**问：** 我启用了增强的计算引擎，但刷新速度较慢。 为什么？

**答：** 如果你启用了增强的计算引擎，则对于刷新时间缓慢，可能有两种解释：

 - 启用增强的计算引擎后，它需要一些内存才能正常工作。 因此，可用于执行刷新的内存减少，增加了刷新排队的可能性，从而减少了可同时刷新的数据流的数量。 若要解决此问题，在启用增强计算时，增加为数据流分配的内存，以确保可用于并发数据流刷新的内存保持不变。

 - 出现刷新速度慢的另一个原因是，计算引擎只能在现有实体的基础上工作，因此如果数据流引用的数据源不是数据流，则你将看不到任何性能改进。 性能不会得到提升，因为在某些大数据场景中，由于需要将数据传递到增强的计算引擎，因此从数据源进行的初始读取速度会比较慢。  

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

## <a name="next-steps"></a>后续步骤

本文提供了关于将增强的计算引擎用于数据流的信息。 以下文章也可提供帮助：

* [数据流自助服务数据准备](service-dataflows-overview.md)
* [在 Power BI 中创建和使用数据流](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用计算实体](service-dataflows-computed-entities-premium.md)
* [Power BI 数据流的开发人员资源](service-dataflows-developer-resources.md)

有关 Power Query 和计划刷新的详细信息，可以阅读以下文章：
* [Power BI Desktop 中的查询概述](desktop-query-overview.md)
* [配置计划刷新](../connect-data/refresh-scheduled-refresh.md)

有关通用数据模型的详细信息，可以阅读其概述文章：
* [通用数据模型 - 概述](/powerapps/common-data-model/overview)
---
title: 数据流限制以及支持的连接器和功能
description: 概述数据流的所有功能
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 89de77e65d8eb675d9e80c3b2497f39af7c32d33
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396578"
---
# <a name="dataflows-limitations-and-considerations"></a>数据流限制和注意事项

以下各节介绍了针对创作、刷新和容量管理的一些数据流限制，用户应牢记这些限制。

## <a name="dataflow-authoring"></a>数据流创作

创作数据流时，用户应注意以下事项：

* 数据流中的创作是在 Power Query Online (PQO) 环境中完成的；请参阅 [Power Query 限制](/power-query/power-query-online-limits)中所述的限制。
由于数据流创作是在 Power Query Online (PQO) 环境中完成的，因此对数据流工作负荷配置执行的更新只会影响刷新，而不会影响创作体验

* 数据流只能由其所有者修改

* 在“我的工作区”，数据流不可用

* 使用网关数据源的数据流不支持同一数据源的多个凭据

* 使用 Web.Page 连接器需要网关

## <a name="api-considerations"></a>API 注意事项

有关受支持数据流 REST API 的详细信息，请参阅 [REST API 参考](/rest/api/power-bi/dataflows)。 下面是要注意的一些事项：

* 导出和导入数据流会为该数据流提供新的 ID

* 导入包含链接实体的数据流不会修复数据流中的现有引用（应在导入数据流之前手动修复这些查询）

* 如果数据流最初是使用导入 API 创建的，则可以使用 CreateOrOverwrite 参数覆盖这些数据流

## <a name="dataflows-in-shared"></a>共享容量中的数据流

共享容量中的数据流存在以下限制：

* 刷新数据流时，共享容量中的超时时间为每个实体 2 小时，每个数据流 3 小时
* 只要对查询禁用了“启用加载”属性，链接实体就可以存在于共享数据流中，但不能在共享数据流中创建链接实体
* 不能在共享数据流中创建计算实体
* AutoML 和认知服务在共享数据流中不可用
* 增量刷新在共享数据流中不起作用

## <a name="dataflows-in-premium"></a>Premium 中的数据流

Premium 中存在的数据流具有以下限制和注意事项。

**刷新和数据注意事项：**

* 刷新数据流时，超时时间为 24 小时（不区分实体和/或数据流）

* 将数据流从增量刷新策略更改为普通刷新会删除所有数据，反之亦然

* 修改数据流架构会删除所有数据

**链接实体和计算实体：**

* 链接实体可以延续至 32 个引用的深度

* 不允许链接实体的循环依赖项

* 链接实体无法与从本地数据源获取数据的常规实体联接

* 当某一查询（例如查询 A）用于数据流中另一个查询（查询 B）的计算时，查询 B 将成为计算实体。 计算实体不能引用本地源。


**计算引擎：**

* 使用计算引擎时，数据引入的初始增长时间大约为 10% 到 20%。

  1. 这仅适用于计算引擎上第一个从数据源读取数据的数据流
  2. 随后使用该源的数据流不会产生相同的损失

* 只有特定操作可以使用计算引擎，并且只能通过链接实体或作为计算实体使用。 [此博客文章](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html)中提供了完整的操作列表。


**容量管理：**

* 按照设计，Premium Power BI 容量具有一个内部资源管理器，当容量的运行内存不足时，该管理器会以各种方式限制工作负荷。

  1. 对于数据流，这种限制压力减少了可用 M 容器的数量
  2. 可以将数据流的内存设置为 100%，并根据数据大小使用适当大小的容器，而工作负荷将相应地管理容器数量

* 通过将分配给工作负荷的内存总量除以分配给容器的内存量，可以确定大致的容器数量

## <a name="dataflow-usage-in-datasets"></a>数据集中数据流的使用

* 在 Power BI Desktop 中创建数据集并将其发布到 Power BI 服务时，请确保 Power BI Desktop 中用于 Dataflows 数据源的凭据与将数据集发布到服务时使用的凭据相同。
  1. 如果不能确保这些凭据相同，则会在数据集刷新时出现“找不到密钥”错误

## <a name="next-steps"></a>后续步骤
以下文章提供有关数据流和 Power BI 的详细信息：

* [数据流和自助数据准备简介](dataflows-introduction-self-service.md)
* [创建数据流](dataflows-create.md)
* [配置和使用数据流](dataflows-configure-consume.md)
* [将数据流存储配置为使用 Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [数据流的高级功能](dataflows-premium-features.md)
* [使用数据流的 AI](dataflows-machine-learning-integration.md)
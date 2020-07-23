---
title: Power BI Desktop 中的自动页面刷新
description: 文本介绍如何在 Power BI Desktop 中针对 DirectQuery 源自动刷新页面。
author: davidiseminger
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/10/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9a1e42b4901e8659bb5d999294f29a80a0389280
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557224"
---
# <a name="automatic-page-refresh-in-power-bi-desktop"></a>Power BI Desktop 中的自动页面刷新 

当监视关键事件时，请务必在源数据更新后尽快刷新数据。 例如，在制造行业，需要了解机器何时出现故障或即将出现故障，这一点很重要。

借助 Power BI 中的自动页面刷新功能，活动报表页能够以预定义的频率针对 [DirectQuery 源](https://docs.microsoft.com/power-bi/desktop-directquery-about)查询新数据。

## <a name="using-automatic-page-refresh"></a>使用自动页面刷新

自动页面刷新仅适用于 DirectQuery 数据源。

若要使用自动页面刷新，请选择要为其启用刷新的报表页面。 在“可视化效果”窗格中，选择“格式设置”按钮（油漆滚筒），然后在接近窗格底部的位置找到“页面刷新”。 

![页面刷新位置](media/desktop-automatic-page-refresh/automatic-page-refresh-01.png)

下图显示“页面刷新”卡片。 带编号的元素在图像后进行描述。

![页面刷新卡片](media/desktop-automatic-page-refresh/automatic-page-refresh-02.png)

1.    打开或关闭页面刷新
2.    页面刷新间隔的数值
3.    页面刷新间隔的单位

在此卡上，可以启用页面刷新并选择刷新持续时间。 默认值为 30 分钟。 （最小刷新间隔为 1 秒。）报表将按设置的间隔开始刷新。 

## <a name="determining-the-page-refresh-interval"></a>确定页面刷新间隔

启用自动页面刷新时，Power BI Desktop 会不断向 DirectQuery 源发送查询。 发送查询后，返回数据之前会有延迟。 因此，对于较短的刷新间隔，应确认查询在配置的间隔内成功返回查询的数据。 如果在间隔内未返回数据，则视觉对象的更新频率将低于配置的频率。

最佳做法是，刷新间隔应至少符合预期的新数据到达频率：

* 如果新数据以 20 分钟的间隔频率到达源，那么刷新间隔不能小于 20 分钟。 

* 如果新数据每秒到达一次，则将间隔设置为 1 秒。 

对于低刷新间隔（如 1 秒），请考虑以下因素：
- DirectQuery 数据源的类型
- 查询在其上创建的负载
- 报表查看器与容量数据中心之间的距离 

可以通过在 Power BI Desktop 中使用性能分析器来估算返回时间。 可以使用性能分析器检查每个视觉对象查询是否有足够的时间从源返回结果。 还可以决定将时间用在何处。 根据性能分析器的结果，可以对数据源进行调整，也可以在报表中试用其他视觉对象和度量值。

此图显示了性能分析器中 DirectQuery 的结果：

![性能分析器结果](media/desktop-automatic-page-refresh/automatic-page-refresh-03.png)

思考下此数据源的一些其他特征： 

-    数据以 2 秒的频率到达。 
-    性能分析器显示最大查询 + 显示时间大约为 4.9 秒（4688 毫秒）。 
-    数据源配置为每秒处理大约 1000 个并发查询。 
-    预计大约 10 个用户可以同时查看报表。

这会得到以下公式：

**5 个视觉对象 x 10 个用户 = 大约 50 个查询**

此计算结果显示负载比数据源可以支持的负载要多得多。 数据以 2 秒的速率到达，因此此值应为刷新频率。 但是，由于查询大约需要 5 秒钟才能完成，因此应将其设置为超过 5 秒。 

另请注意，在将报表发布到服务时，此结果可能会有所不同。 出现这种差异的原因是，报表将使用在云中托管的 Azure Analysis Services 实例。 可能需要相应地调整刷新频率。 

考虑到查询和刷新计时，Power BI 只有在所有剩余刷新查询全部完成后，才会运行下一个刷新查询。 因此，即使刷新间隔时间短于处理查询所用的时间，Power BI 也只会在剩余查询完成后才再次刷新。 

现在，我们来看看如何才能以容量管理员的身份检测和诊断性能问题。 还可以查看本文后面的[常见问题解答](#frequently-asked-questions)部分，以获取有关性能和故障排除的更多问题和答案。

## <a name="automatic-page-refresh-in-the-power-bi-service"></a>Power BI 服务中的自动页面刷新

还可以为已在 Power BI Desktop 中创作的报表设置自动页面刷新间隔，并将其发布到 Power BI 服务。 

若要为 Power BI 服务中的报表配置自动页面刷新，请使用与 Power BI Desktop 中使用的步骤类似的步骤。 在 Power BI 服务中配置时，自动页面刷新还支持[嵌入式 Power BI](../developer/embedded/embedding.md) 内容。 此图显示了 Power BI 服务的“页面刷新”配置：

![Power BI 服务中的自动页面刷新](media/desktop-automatic-page-refresh/automatic-page-refresh-04.png)

这些说明与带编号的元素相对应： 

1.    打开或关闭页面刷新。
2.    页面刷新间隔的数值。 必须是整数。
3.    页面刷新间隔的单位。

### <a name="page-refresh-intervals"></a>页面刷新间隔

Power BI 服务中允许的页面刷新间隔受报表的工作区类型影响。 这适用于以下报表：

* 将报表发布到启用了自动页面刷新的工作区
* 编辑工作区中已有的页面刷新间隔
* 直接在服务中创建报表

Power BI Desktop 对刷新间隔没有限制。 其刷新间隔频率甚至可以是每秒。 但将报表发布到 Power BI 服务时，会应用某些限制。 后续部分将介绍这些限制。

### <a name="restrictions-on-refresh-intervals"></a>对刷新间隔的限制

在 Power BI 服务中，基于工作区以及是否使用高级服务等因素对自动页面刷新应用限制。

为了阐明这些限制的工作原理，我们先了解一些容量和工作区背景知识。

容量是重要的 Power BI 概念。 它们表示用于托管和交付 Power BI 内容的一组资源（存储、处理器和内存）。 容量可以是共享容量，也可以是专用容量。 共享容量与其他 Microsoft 客户共享。 专用容量完全提交给单个客户。 有关专用容量的介绍，请参阅[管理高级容量](../admin/service-premium-capacity-manage.md)。

在共享容量中，工作负载可在与其他客户共享的计算资源上运行。 由于容量需要共享资源，因此会施加限制以确保“公平竞争”，如设置最大模型大小 (1 GB) 和每日最大刷新频率（每天 8 次）。

Power BI 工作区驻留在容量范围内。 它们表示安全性、协作和部署容器。 每个 Power BI 用户都有一个称为“我的工作区”的个人工作区。 可创建其他工作区来启用协作和部署。 它们称为“工作区”。 默认情况下，工作区（包括个人工作区）在共享容量中创建。

下面介绍了两个工作区方案的一些详细信息：

共享工作区。 对于常规工作区（不属于高级容量的工作区），自动页面刷新的最小间隔为 30 分钟（允许的最小间隔）。

高级工作区。 自动页面刷新在高级工作区中的可用性取决于高级管理员为 Power BI Premium 容量设置的工作负载设置。 有两个变量可能会影响你对自动页面刷新的设置：

 - 功能启用/禁用。 如果容量管理员已禁用该功能，你将无法在已发布的报表中设置任何类型的页面刷新。

 - 最小刷新间隔。 启用此功能时，容量管理员需要设置最小刷新间隔。 如果你的间隔低于最小值，Power BI 服务将覆盖你的间隔，以遵循容量管理员设置的最小间隔。 在下表中，此覆盖称为“容量管理员覆盖”。 

此表详细介绍了提供此功能的位置，以及针对每种容量类型和[存储模式](../connect-data/service-dataset-modes-understand.md)的限制：

| 存储模式 | 专用容量 | 共享容量 |
| --- | --- | --- |
| DirectQuery | 受支持：是 <br>最小刷新间隔：1 秒 <br>容量管理员覆盖：是 | 受支持：是 <br>最小刷新间隔：30 分钟 <br>容量管理员覆盖：否 |
| 导入 | 受支持：否 <br>最小刷新间隔：不适用 <br>容量管理员覆盖：不适用 | 受支持：否 <br>最小刷新间隔：不适用 <br>容量管理员覆盖：不适用 |
| 混合模式（DirectQuery + 其他数据源） | 受支持：是 <br>最小刷新间隔：1 秒 <br>容量管理员覆盖：是 | 受支持：是 <br>最小刷新间隔：30 分钟 <br>容量管理员覆盖：否 |
| 实时连接 AS | 受支持：否 <br>最小刷新间隔：不适用 <br>容量管理员覆盖：不适用 | 受支持：否 <br>最小刷新间隔：不适用 <br>容量管理员覆盖：不适用 |
| 实时连接 PBI | 受支持：否 <br>最小刷新间隔：不适用 <br>容量管理员覆盖：不适用 | 受支持：否 <br>最小刷新间隔：不适用 <br>容量管理员覆盖：不适用 |

> [!NOTE]
> 将启用了自动页面刷新的报表从 Power BI Desktop 发布到服务时，必须在“数据集设置”菜单中为 DirectQuery 数据源提供凭据。

## <a name="considerations-and-limitations"></a>注意事项和限制

在 Power BI Desktop 或 Power BI 服务中使用自动页面刷新时，需注意以下几点：

* 自动页面刷新不支持导入、LiveConnect 和推送存储模式。  
* 支持具有至少一个 DirectQuery 数据源的复合模型。
* Power BI Desktop 对刷新间隔没有限制。 间隔频率可以为每秒。 将报表发布到 Power BI 服务时，会应用某些限制，如本文[前面](#restrictions-on-refresh-intervals)所述。
* SharePoint Online 嵌入不支持自动刷新页面。

### <a name="performance-diagnostics"></a>性能诊断

自动页面刷新适用于监视方案和浏览快速变化的数据。 但有时可能会对容量或数据源施加过多负载。

为了防止数据源上的负载过大，Power BI 具有以下安全措施：

- 所有自动页面刷新查询都以较低的优先级运行，以确保交互式查询（如页面负载和交叉筛选视觉对象）优先。
- 如果查询未在下一个刷新周期之前完成，Power BI 不会发出新的刷新查询，直到上一个查询完成为止。 例如，如果刷新间隔为 1 秒，并且查询平均 4 秒执行一次，则 Power BI 每隔 4 秒才会有效地发出一次查询。

在以下两个方面仍会遇到性能瓶颈：

1. 容量。 查询首先会命中高级容量，高级容量将折叠从报表可视化效果生成的 DAX 查询并将其评估为源查询。
2. DirectQuery 数据源。 然后，上一步中的已转换查询将针对源运行。 源可以是 SQL Server 实例、SAP Hana 源等。

使用管理员可用的 [Premium Capacity Metrics 应用](../admin/service-admin-premium-monitor-capacity.md)，可以可视化低优先级查询使用的容量大小。

低优先级查询包括自动页面刷新查询和模型刷新查询。 目前没有办法区分来自自动页面刷新和模型刷新查询的负载。

如果你注意到使用低优先级查询时容量过载，可以执行以下几个操作：

- 请求更大的高级 SKU。
- 请求报表所有者减少刷新间隔时间。
- 在容量管理门户中，可以：
   - 禁用该容量的自动页面刷新。
   - 增加最小刷新间隔时间，这将对该容量中的所有报表产生影响。


### <a name="frequently-asked-questions"></a>常见问题解答

我是报表作者。**我在 Power BI Desktop 上将报表刷新间隔定义为 1 秒，但在发布报表后，报表未在服务中刷新。**

* 确保为该页面启用了自动页面刷新。 由于此设置是针对每个页面的，因此需要确保报表中要刷新的每个页面上都启用了此设置。
* 检查是否已上传到具有附加高级容量的工作区。 如果没有，刷新间隔将锁定在 30 分钟。
* 如果报表位于高级工作区中，请询问管理员是否已为附加容量启用了此功能。 此外，请确保容量的最小刷新间隔小于或等于报表刷新间隔。

我是容量管理员。**我更改了自动页面刷新间隔设置，但这些更改没有反映出来。换句话说，报表未按预期频率进行刷新，或者不刷新，即使我启用了自动页面刷新也是如此。**

* 在容量管理 UI 中所做的自动页面刷新设置更改需要最多 5 分钟的时间才会传播到报表中。
* 除了为容量启用自动页面刷新外，还需要为要启用的报表页面启用自动页面刷新。

我的报表在混合模式下运行。 **（混合模式意味着报表具有 DirectQuery 连接和“导入”数据源。）某些视觉对象不会刷新。**

- 如果视觉对象引用“导入”表，那么这是预期行为。 “导入”不支持自动页面刷新。
- 请参阅本节中的第一个问题。

我的报表在服务中正常刷新，但随后突然停止。

* 尝试刷新页面，查看问题是否能自行解决。
* 请咨询你的容量管理员。管理员可能已关闭该功能或提高了最小刷新间隔。 （请参阅本节中的第二个问题。）

我是报表作者。**我的视觉对象未按我指定的频率刷新。它们的刷新频率更低。**

* 如果查询运行时间较长，刷新间隔将会延迟。 自动页面刷新会等待所有查询完成，然后才会运行新查询。
* 容量管理员设置的最小刷新间隔可能大于你在报表中设置的最小刷新间隔。 要求容量管理员降低最小刷新间隔。

是否从缓存中执行自动页面刷新查询？

* 否。 所有自动页面刷新查询将绕过任何缓存的数据。


## <a name="next-steps"></a>后续步骤

有关详细信息，请参阅以下文章：

* [在 Power BI 中使用 DirectQuery](../connect-data/desktop-directquery-about.md)
* [在 Power BI Desktop 中使用复合模型](../transform-model/desktop-composite-models.md)
* [使用性能分析器检查报表元素性能](desktop-performance-analyzer.md)
* [部署和管理 Power BI Premium 容量](../guidance/whitepaper-powerbi-premium-deployment.md)
* [Power BI Desktop 中的数据源](../connect-data/desktop-data-sources.md)
* [在 Power BI Desktop 中调整和合并数据](../connect-data/desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](../connect-data/desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](../connect-data/desktop-enter-data-directly-into-desktop.md)   

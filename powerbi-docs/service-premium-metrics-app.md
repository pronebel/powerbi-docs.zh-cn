---
title: Power BI Premium 指标应用
description: 了解如何使用 Power BI Premium 指标应用来管理 Premium 容量并对其进行故障排除。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/19/2019
LocalizationGroup: Premium
ms.openlocfilehash: ae11ec64a0bffbd3e64c0fd677a7225c2b31f521
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488674"
---
# <a name="power-bi-premium-metrics-app"></a>Power BI Premium 指标应用

可以使用 Power BI Premium 指标应用来管理 Power BI Premium 订阅的运行状况和容量  。 在应用中，管理员使用应用的容量运行状况中心来查看可监视其 Premium 容量运行状况的指示器，并与之进行交互  。 指标应用包含登陆页面（称为“容量运行状况中心”）  ，以及有关三个重要指标的详细信息：

* 活动内存
* 查询等待
* 刷新等待

![Power BI Premium 指标应用](media/service-premium-metrics-app/premium-metrics-app-00.png)

以下部分详细介绍了登陆页面和三个指标报表页。 

## <a name="premium-capacity-health-center"></a>Premium 容量运行状况中心

当你打开“Power BI Premium 指标应用”时，会显示容量运行状况中心，其中概述了 Power BI Premium 容量的运行状况   。

![Premium 指标应用中的容量运行状况中心](media/service-premium-metrics-app/premium-metrics-app-01.png)

如果组织有多个 Premium 订阅，可以从登陆页面选择要查看的 Power BI Premium 容量。 若要查看 Premium 容量，请选择页面顶部附近的下拉列表（称为“选择容量以查看其指标”  ）。

这三个 KPI 根据应用于每个 KPI 的设置显示所选 Premium 容量的当前运行状况。 

若要查看有关每个 KPI 的详细信息，请选择每个 KPI 的视觉对象底部的“浏览”  按钮，此时将显示其详细信息页。 以下部分介绍了每个 KPI 及其页面提供的详细信息。

## <a name="the-active-memory-metric"></a>活动内存指标

活动内存指标是“容量规划”类别的一部分，这是一个很好的运行状况指标，用于评估容量的资源消耗情况，因此，可以根据需要调整容量以规划容量规模   。 

![活动内存 KPI](media/service-premium-metrics-app/premium-metrics-app-02.png)

活动内存是用于处理当前正在使用的数据集的内存，因此，在需要内存时不会被收回  。 活动内存指标指示容量是否可以处理已接近或超过容量的额外负载，或容量的当前负载。 当前正在使用的活动内存意味着更少的内存可用于支持其他刷新和查询。 

活动内存 KPI 用于度量容量的活动内存超过 70% 阈值 50 次（该标记设置为过去七天的 30%）的次数，这表示当用户可能开始查看查询的性能问题时，容量即将达到某个点  。

本部分中所示的仪表视觉对象显示，在上次刷新报表的过去 7 天内，容量超出 70% 阈值四次（按每小时的 bucket 量划分）。 仪表的最大值 168 表示过去七天（以小时为单位）。

若要了解活动内存 KPI 的详细信息，请单击“浏览”  按钮以查看提供其详细指标的特定可视化效果的报表页，以及该页右栏中显示的故障排除指南。 

介绍了两种方案，可以通过在页面上选择“方案 1”  或“方案 2”  将其显示在报表页上。 

![活动内存详细信息页](media/service-premium-metrics-app/premium-metrics-app-03.png)

与每个方案关联的故障排除指南提供了有关指标含义的详细说明，以便你可以更好地了解容量的状态，以及可以采取哪些措施来缓解任何问题。 

将在以下部分中介绍这两个方案。

### <a name="scenario-one---current-load-is-too-high"></a>方案 1 - 当前负载过高 

若要确定是否为容量提供足够的内存来完成其工作负载，请参考页面上的第一个视觉对象：“A：  占用内存百分比”，显示当前正在处理因而无法收回的数据集占用的内存。

红色虚线形式的警报阈值用于标记 90% 内存占用的事件。

黄色虚线形式的警告阈值用于标记 70% 内存占用的事件。 

黑色虚线表示内存使用量趋势线，该趋势线基于图形时间线上当前容量的内存使用量。

频繁出现警报阈值（红色虚线）和内存趋势线（黑色虚线）以上的活动内存表示内存容量压力，可能会阻止在该时间段内将其他数据集加载到内存中。 

出现这种情况时，应仔细查看页面上的其他图表，以更好地确定内存使用量和频繁使用如此多内存的原因，以及如何进行负载平衡或优化，或扩展容量（如果需要）。 

页面上的第二个视觉对象“B：  每小时加载的活动数据集”，显示加载到内存中的最大数据集数（按每小时的 bucket 量划分）。 

第三个视觉对象“C：  数据集在内存中的原因”是按工作区名称、数据集名称和数据集在内存中未压缩的大小列出数据集的表，说明将其加载到内存中的原因（例如，要对其进行刷新和/或查询）。

#### <a name="diagnosing-scenario-one"></a>诊断方案 1

一致的高活动内存使用率可能会导致强制收回主动使用的数据集，也可能会阻止加载新数据集。 以下步骤可以帮助你诊断问题

1. 查看图表“A：  占用内存百分比”

    **a.** 如果图表 A 显示超出警报阈值 (90%) 多次和/或连续数小时，则容量内存很快就会不足。 在下图中，我们可以看到超出警告阈值 (70%) 四次。

    ![图表 a 占用内存百分比](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** 标题为“B：  每小时加载的活动数据集”的图表显示加载到内存中的最大唯一数据集数（按每小时的 bucket 量划分）。 在视觉对象中选择某一栏将交叉筛选数据集在内存视觉对象中的原因。  

    ![图表 b 每小时占用的内存](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** 若要查看内存中加载的数据集的列表，请参考“数据集在内存中的原因”  表。 按“数据集大小(MB)”排序以突出显示占用最多内存的数据集  。 容量操作分类为*交互式操作*和*后台操作*。 交互式操作包括呈现请求和响应用户交互（筛选、问答查询等）。 通过查询总数和刷新总数可了解是否已在数据集上完成了交互式（查询）繁重或后台（刷新）操作。 重点是了解交互式操作应始终优先于后台操作，以确保可能的最佳用户体验。 如果资源不足，则会在释放资源时将后台操作添加到队列中进行处理。 后台操作（如数据集刷新和 AI 函数）可以由 Power BI 服务在进程中停止并添加到队列中。
    
    ![表 c 数据集列表](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>方案 1 的补救措施

可以执行以下步骤来解决与方案 1 相关的问题：

1. **扩展容量** - 将容量扩展到下一个 SKU 使之为当前 SKU 内存量的两倍，从而缓解容量当前遇到的内存压力。

2. **将数据集移动到另一个容量** - 如果具有包含更多可用内存的另一个容量，则可以将包含较大数据集的工作区移动到该容量。


### <a name="scenario-two---future-load-will-exceed-limits"></a>方案 2 - 未来负载将超过限制

若要确定是否为容量提供足够的内存来完成其工作负载，可以参考页面顶部的“A：  占用内存百分比”视觉对象，该视觉对象表示当前正在处理因而无法收回的的数据集占用的内存。 黑色虚线突出显示趋势。 在遇到内存压力的容量中，相同的视觉对象将清晰地显示呈上升趋势的内存趋势线（黑色虚线），这意味着它可能会阻止在该时间点将其他数据集加载到内存中。 趋势线（黑色虚线）基于七天数据显示增长趋势。 

![活动内存详细信息页](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>诊断方案 2

若要诊断方案 2，请确定趋势线是否呈超出警告或警报阈值的趋势。 

1. 请考虑“图表 A：” 

    ![占用内存图表](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** 如果图表显示向上斜率，则表明内存消耗已在过去七天内增加。

    **b.** 假设当前增长，并预测趋势线将超出警告阈值（黄色虚线）的时间。

    **c.** 至少每两天检查一次趋势线，以查看趋势是否继续。

#### <a name="remedies-for-scenario-two"></a>方案 2 的补救措施

可以执行以下步骤来解决与方案 2 相关的问题：

1. **扩展容量** - 将容量扩展到下一个 SKU 使之为当前 SKU 内存量的两倍，从而缓解容量当前遇到的内存压力。

2. **将数据集移动到另一个容量** - 如果具有包含更多可用内存的另一个容量，则可以将包含较大数据集的工作区移动到该容量。


## <a name="the-query-waits-metric"></a>查询等待指标

 “查询”类别指示用户是否可以体验响应速度缓慢或可能无法响应的报表视觉对象。 “查询等待”是查询从触发时开始执行所花费的时间  。 此 KPI 用于度量所选容量中 25% 或更多的查询在执行前是否等待 100 毫秒或更长的时间。 没有足够的可用 CPU 来执行所有挂起的查询时发生查询等待。 

![查询等待仪表](media/service-premium-metrics-app/premium-metrics-app-09.png)

此视觉对象中的仪表显示，在上次刷新报表的过去 7 天内，17.32% 的查询等待超过 100 毫秒。 

若要了解查询等待 KPI 的详细信息，请单击“浏览”  按钮以显示包含相关指标可视化效果的报表页，以及该页右栏中的故障排除指南。 故障排除指南有两个方案，每个方案提供指标的详细说明、容量的状态，以及可以采取哪些措施来缓解问题。

我们将在以下部分中依次介绍每个查询等待方案。

### <a name="scenario-one---long-running-queries-consume-cpu"></a>方案 1 - 长时间运行的查询占用 CPU

在方案 1 中，长时间运行的查询占用太多 CPU。 

你可以调查报表性能不佳是由重载的容量引起的，还是由设计不佳的数据集或报表而引起的。 有多个原因导致查询可能需要较长时间运行，其定义为需要超过 10 秒才能完成执行。 数据集大小和复杂性以及查询复杂性只是几个可能导致查询长时间运行的示例。 

在报表页上，将显示以下视觉对象： 

* 标题为“A：  大量等待时间”的顶级表列出了包含正在等待的查询的数据集。 
* “B：  每小时大量等待时间分布”显示了大量等待时间的分布。 
* 标题为“C：  每小时长时间查询计数”的图表显示已执行的长时间运行的查询的计数（按每小时的 bucket 量划分）。
* 最后一个视觉对象（表 D：  长时间运行的查询）列出了长时间运行的查询及其统计信息。

![查询等待详细信息页](media/service-premium-metrics-app/premium-metrics-app-10.png)

下面介绍了诊断和解决查询等待时间问题所采取的步骤。

#### <a name="diagnosing-scenario-one"></a>诊断方案 1

首先，可以确定在等待查询时是否发生长时间运行的查询。 

![大量等待时间表](media/service-premium-metrics-app/premium-metrics-app-11.png)

查看“图表 B”  ，其中显示等待超过 100 毫秒的查询数。 选择显示大量等待的列之一。

![大量等待时间分布](media/service-premium-metrics-app/premium-metrics-app-12.png)

单击具有大量等待时间的列时，会对“图表 C”进行筛选，以显示在该时间段内执行的长时间运行的查询的计数，如下图所示  ：

![每小时长查询计数](media/service-premium-metrics-app/premium-metrics-app-13.png)

此外，还会对“图表 D”进行筛选，以显示在所选时间段内长时间运行的查询  。

![长时间运行的查询](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>方案 1 的补救措施

下面是解决方案 1 中的问题所采取的步骤：

1. **运行 PerfAnalyzer 以优化报表和数据集** - 报表的性能分析器将显示页面上每个交互的效果，包括刷新每个视觉对象所需的时间以及所用时间的分布情况。

2. **扩展容量** - 将容量扩展到下一个 SKU 使之为 CPU 量的两倍，从而缓解可能导致长时间运行查询的任何 CPU 压力。

3. **将数据集移动到另一个容量** - 如果具有包含更多可用 CPU 的另一个容量，则可以将包含具有正在等待的查询的数据集的工作区移动到其他容量。

### <a name="scenario-two---too-many-queries"></a>方案 2 - 查询太多

在方案 2 中，执行的查询太多。

如果要执行的查询数超过容量限制，则会将查询放入队列中，直到资源可用于执行这些查询。 如果队列的大小增长得太大，该队列中的查询最终会等待超过 100 毫秒。

![方案 2](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>诊断方案 2

在“表 A”中，选择具有大量等待时间百分比的数据集  。

![大量等待时间表](media/service-premium-metrics-app/premium-metrics-app-16.png)

选择具有大量等待时间的数据集后，将对“图表 B”进行筛选  ，以显示过去七天内针对该数据集的查询的等待时间分布。 接下来，从“图表 B”中选择一列  。

![每小时大量等待时间分布图表](media/service-premium-metrics-app/premium-metrics-app-17.png)

然后对“图表 C”进行筛选，以显示从图表 B 中选择的时间内的队列长度  。

![每小时查询队列长度](media/service-premium-metrics-app/premium-metrics-app-18.png)

如果队列的长度超出阈值 20，则很可能是由于尝试同时执行的查询太多而导致选定数据集中的查询延迟。

![执行查询表](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>方案 2 的补救措施

可以执行以下步骤来解决与方案 2 相关的问题：

1. **扩展容量** - 将容量扩展到下一个 SKU 使之为当前 SKU 内存量的两倍，从而缓解容量当前遇到的内存压力。

2. **将数据集移动到另一个容量** - 如果具有包含更多可用内存的另一个容量，则可以将包含较大数据集的工作区移动到该容量。


## <a name="the-refresh-waits-metric"></a>刷新等待指标

 “刷新等待”指标提供有关用户何时可以体验陈旧或过时的报表数据的见解。  “刷新等待”是给定数据刷新等待开始执行的时间，从根据需要触发或计划运行的时间算起。 此 KPI 用于度量 10% 或更多挂起的刷新请求是否等待 10 分钟或更长时间。 当可用内存或 CPU 不足时，通常会发生等待。

![刷新等待仪表](media/service-premium-metrics-app/premium-metrics-app-20.png)

此仪表显示，在上次刷新报表的过去 7 天内，3.18% 的刷新等待超过 10 分钟。 

若要了解刷新等待 KPI 的详细信息，请单击“浏览”按钮，该按钮显示包含指标的页面，以及报表页右栏中的故障排除指南   。 本指南提供有关页面上的指标的详细说明，并帮助你了解容量的状态，以及可以采取哪些措施来缓解任何问题。

![了解刷新等待指标](media/service-premium-metrics-app/premium-metrics-app-21.png)

介绍了两种方案，可以通过在页面上选择“方案 1”或“方案 2”将其显示在报表页上。 我们将在以下部分中依次介绍每个方案。

### <a name="scenario-one---not-enough-memory"></a>方案 1 - 内存不足

在方案 1 中，没有足够的可用内存来加载数据集。 在内存不足的情况下导致刷新受限有以下两种情况：

1. 没有足够的内存可用来加载数据集。
2. 刷新由于优先级较高的操作而取消。 

加载数据集的优先级如下：

1. 交互式查询
2. 按需刷新
3. 计划的刷新

如果没有足够的内存来加载交互式查询的数据集，则会停止计划的刷新并卸载其数据集，直到有足够的内存可用。 如果未释放足够的内存，则会停止按需刷新并卸载其数据集。

#### <a name="diagnosing-scenario-one"></a>诊断方案 1

若要诊断方案 1，请首先确定限制是否是由于内存不足引起的。 步骤如下：

1.    通过单击“表 A”，从表中选择你感兴趣的数据集  ： 

    ![表 A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. 如果在“表 A”中选择了某个数据集，则会对“图表 B”进行筛选以在等待时显示   。

    ![图表 B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b.  然后对“图表 C”进行筛选以显示任何限制，下一步将对此进行说明。 

2. 查看当前筛选的“图表 C”  中的结果。如果图表显示在数据集等待时出现内存不足限制，则数据集由于内存不足而等待。

    ![图表 C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. 最后，检查“图表 D”  ，其中显示了按计划或按需发生的刷新类型。 同时发生的任何按需刷新可能会导致限制。

    ![图表 D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>方案 1 的补救措施

可以执行以下步骤来解决与方案 1 相关的问题：

1. **扩展容量** - 将容量扩展到下一个 SKU 使之为当前 SKU 内存量的两倍，从而缓解容量当前遇到的内存和 CPU 压力。

2. **将数据集移动到另一个容量** - 如果等待时间是由内存压力引起的，并且具有包含更多可用内容的另一个容量，则可以将包含具有正在等待的数据集的工作区移动到其他容量。

3. **分散计划的刷新** - 分散刷新有助于避免尝试同时执行太多刷新。



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>方案 2 - 没有足够的 CPU 用于刷新

在方案 2 中，没有足够的可用 CPU 来执行刷新。 

对于专用容量，Power BI 限制可同时发生的刷新次数。 此数字等于后端内核数 x 1.5。 例如，具有四个后端内核的 P1 专用容量可同时运行 6 次刷新。 达到最大并发刷新次数后，其他刷新将等待直至执行刷新完成。

![刷新的方案 2](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>诊断方案 2

若要诊断方案 2，请首先确定限制是否是由于刷新的最大并发数。 步骤如下：

1.    通过单击“表 A”，从表中选择你感兴趣的数据集  ： 

    ![表 A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. 如果在“表 A”中选择了某个数据集，则会对“图表 B”进行筛选以在等待时显示   。

    ![图表 B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b.  然后对“图表 C”进行筛选以显示任何限制，下一步将对此进行说明。 

2. 查看当前筛选的“图表 C”  中的结果。如果图表显示在数据集等待时出现最大并发数，则数据集由于没有足够的可用 CPU 而等待  。

    ![图表 C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. 最后，检查“图表 D”  ，其中显示了按计划或按需发生的刷新类型。 同时发生的任何按需刷新可能会导致限制。

    ![图表 D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>方案 2 的补救措施

1. **扩展容量** - 将容量扩展到下一个 SKU 使之为当前 SKU 内存量的两倍，并使并发刷新数为当前 SKU 的两倍，从而缓解容量当前遇到的内存和 CPU 压力。

2. **将数据集移动到另一个容量** - 如果等待时间是由达到最大并发数引起的，并且具有包含可用并发数的另一个容量，则可以将包含具有正在等待的数据集的工作区移动到其他容量。

3. **分散计划的刷新** - 分散刷新有助于避免尝试同时执行太多刷新。



## <a name="next-steps"></a>后续步骤

* [什么是 Power BI Premium？](service-premium-what-is.md)
* [Power BI Premium 发行说明](service-premium-release-notes.md)
* [Microsoft Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)
* [规划 Power BI Enterprise 部署白皮书](https://aka.ms/pbienterprisedeploy)
* [激活延长的 Power BI Pro 试用期](service-extended-pro-trial.md)
* [Power BI Embedded 常见问题解答](developer/embedded/embedded-faq.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
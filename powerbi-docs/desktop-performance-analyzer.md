---
title: 使用性能分析程序破译 Power BI Desktop 中的报表元素性能
description: 了解如何在资源使用情况和响应能力方面执行视觉对象和报表元素
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854404"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>使用性能分析程序破译报表元素的性能

在中**Power BI Desktop**可以找到的带报表元素，如视觉对象和 DAX 公式的每个性能如何。 使用**性能分析器**，可以看到，并且记录日志的度量值的每个报表元素时，这些用户进行交互的执行，其性能的哪些方面是大多数 （或最少） 占用大量资源。

![性能分析器](media/desktop-performance-analyzer/performance-analyzer-01.png)

性能分析器检查和显示所需更新或刷新所有视觉对象的持续时间启动，该用户交互并可显示的信息，因此您可以查看、 向下钻取，或将结果导出。 性能分析器可帮助您识别影响的报表，性能的视觉对象并确定所产生的影响的原因。

## <a name="displaying-the-performance-analyzer-pane"></a>显示性能分析工具窗格

在中**Power BI Desktop**选择**视图**功能区。 在**显示**区域中的**视图**您可以选中的复选框旁边的功能区**性能分析器**显示性能分析器窗格。

![查看功能区中选择性能分析器](media/desktop-performance-analyzer/performance-analyzer-02.png)

选择后，性能分析器显示在其自己的窗格中，在报表画布的右侧。

## <a name="using-performance-analyzer"></a>使用性能分析器

性能分析器度量值更新报表元素启动的运行查询会导致任何用户交互所需的处理时间 （包括创建或更新视觉对象的时间）。 例如，调整切片器需要的要修改的查询发送到数据模型的切片器视觉对象和受影响的视觉对象，必须应用新设置后更新。 

若要使性能分析器开始录制，只需选择**开始录制**

![开始录制](media/desktop-performance-analyzer/performance-analyzer-03.png)

显示和记录性能分析器窗格中的 Power BI 加载视觉对象的顺序，在报表中执行任何操作。 例如，假设有一个报表，用户就说过需要很长时间来刷新。 或在报表中的某些视觉对象需要时调整滑块显示较长时间。 性能分析工具可以告知你的视觉对象是问题所在，并标识该视觉对象的哪些方面花费的时间最长持续时间来处理。 

一旦您开始录制，**开始录制**按钮将灰带 （非活动状态，因为您已经开始录制） 和**停止**按钮处于活动状态。 

性能分析工具收集，并实时显示性能度量信息。 单击视觉对象，每次移动一个切片器，或以任何其他方式进行交互以便性能分析器立即在其窗格中显示的性能结果。

如果窗格具有超过了可显示的详细信息，将显示滚动条以导航到的其他信息。

每个交互在窗格中，描述启动日志条目的操作有一个部分标识符。 下图中，在交互的用户更改切片器。

![根据交互类型的部分](media/desktop-performance-analyzer/performance-analyzer-04.png)

每个视觉对象的日志信息包括所用的时间 （持续时间） 来完成下列类别的任务：

* **DAX 查询**-如果 DAX 查询是必需的这是与 Analysis services 返回的结果将查询发送的视觉对象之间的时间。
* **可视显示**-视觉对象，其中包括检索任何 web 映像或地理编码所需的时间在屏幕上绘制所需时间。 
* **其他**-视觉对象准备查询、 等待其他视觉对象，若要完成，或执行其他后台处理所需时间。

![日志信息的元素](media/desktop-performance-analyzer/performance-analyzer-06.png)

已与你想要测量性能分析器使用的报表中的元素交互后，可以选择**停止**按钮。 性能信息保持在窗格中，选择后**停止**分析。

若要清除性能分析工具窗格中的信息，请选择**清除**。 所有信息将被删除，当你选择不保存**清除**。 请参阅下一节以了解如何将信息保存在日志中。 

## <a name="refreshing-visuals"></a>刷新视觉对象

可以选择**刷新视觉对象**在性能分析工具窗格中，若要刷新当前报表的页上的所有视觉对象，从而有性能分析工具收集有关所有此类视觉对象的信息。

此外可以刷新单个视觉对象。 当记录性能分析器时，可以选择**刷新此视觉对象**找到右上角的每个视觉对象，若要刷新该视觉对象，并捕获其性能信息。

![刷新单个视觉对象](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>保存性能信息

可以通过选择保存性能分析工具创建的报表有关的信息**导出**按钮。 选择**导出**使用性能分析工具窗格中的信息创建一个.json 文件。 

![保存的日志文件的性能分析器](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>后续步骤
有关 Power BI Desktop  以及如何入门的详细信息，请查看以下文章。

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 的查询概述](desktop-query-overview.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [连接到 Power BI Desktop 中的数据](desktop-connect-to-data.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常见查询任务](desktop-common-query-tasks.md)   


---
title: 在 Power BI Desktop 中使用跨报表钻取
description: 了解如何在 Power BI Desktop 中从一个报表钻取到另一个报表
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e735d45a7a49c4a0365e35d5bb95957c6145f934
ms.sourcegitcommit: db4fc5da8e65e0a3dc35582d7142a64ad3405de7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70903752"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>在 Power BI Desktop 中使用跨报表钻取

借助 Power BI Desktop 中的跨报表钻取功能，可以根据上下文从一个报表跳转到另一个报表。 只要报表在 Power BI 服务中位于相同的工作区或应用内就会如此。 使用跨报表钻取连接两个或更多具有相关内容的报表，并将筛选器上下文与跨报表连接一起传递。 本文介绍如何为 Power BI 报表设置跨报表钻取，以及用户自行使用跨报表钻取时的体验。

![Power BI Desktop 钻取选项的屏幕截图](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

在开始设置和使用跨报表钻取之前，必须了解以下定义：

* **源视觉对象：** 使用视觉对象上下文菜单调用钻取操作的视觉对象。
* **源报表：** 包含用于跨报表钻取的源视觉对象的报表。
* **目标页：** 用户在启动钻取操作后登录的页面。
* **目标报表：** 包含用于跨报表钻取的目标页的报表。


> [!NOTE]
> “我的工作区”中单独共享的报表是显示为[与我共享](service-share-dashboards.md#share-a-dashboard-or-report)的报表，只能在最初共享这些报表的工作区中进行访问   。 


## <a name="enable-cross-report-drillthrough"></a>启用跨报表钻取

若要使报表成为跨报表钻取的目标，必须在“选项”窗口中为该报表启用此功能  。 转到“文件” > “选项和设置” > “选项”，然后转到左侧页面底部的“报表设置”     。

选中“允许此报表中的视觉对象使用其他报表中的钻取目标”复选框，如下图所示  。

![“选项”窗口的屏幕截图，突出显示了报表设置](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

现已启用跨报表钻取。

## <a name="set-up-cross-report-drillthrough"></a>设置跨报表钻取

设置跨报表钻取类似于在报表中设置钻取。 目标页上启用了钻取，从而允许其他视觉对象以已启用页为目标进行钻取。 有关在单个报表中创建钻取的步骤，请参阅[在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)。

若要启动设置过程，需要执行几个初始步骤：

* 设置钻取目标页，随后可从工作区或应用中的其他报表访问该页面。
* 允许报表查看其自身报表之外的钻取页。

在“可视化效果”窗格的“字段”部分中查找钻取选项，如下图所示   。

![“可视化效果”窗格的屏幕截图，突出显示了钻取选项](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

为页面启用钻取的第一步是验证源报表和目标报表的数据模型。 请确保： 

* 要传递的字段同时存在于两个数据模型中。
* 字段的名称与它们所属的表的名称相同（字符串也必须匹配，并且区分大小写）。

例如，如果要在“地域”表内的“国家/地区”字段上传递筛选器，则两个模型都必须具有“地域”表和该表中的“国家/地区”字段     。 如果没有，则必须在基础模型中更新字段名称或表名称。 仅更新字段的显示名称无法使跨报表钻取正常运行。 （请注意，每个报表中的架构不必完全相同。）

若要开始设置，需要准备好目标页。 在 Power BI Desktop 中，转到该页面并确保“跨报表”钻取开关设置为“打开”   。 

![跨报表开关设置为“打开”的屏幕截图](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

接下来，将要用作钻取目标的字段拖动到画布上。 选择是要将字段用作类别，还是汇总为度量值。 此时，你可以选择是否要为视觉对象禁用“保留所有筛选器”开关  。 如果不想将其他已应用的筛选器从源视觉对象传递到目标钻取视觉对象，请选择“关闭”  。

> [!NOTE]
> 如果将页面仅用于跨报表钻取，则应删除自动添加的“后退”按钮  。 “后退”按钮仅适用于单个报表中的导航  。 

配置视觉对象后，确保保存报表（如果使用的是 Power BI 服务）或保存并发布报表（如果使用的是 Power BI Desktop）。

上述部分介绍如何为 Power BI Desktop 启用跨报表钻取（在“选项”窗口中  ）。 如果使用 Power BI 服务创建跨报表钻取目标，则为了启用跨报表钻取，必须： 

1. 选择目标报表和源报表所在的工作区。
2. 选择“报表”  。
3. 选择源报表的“设置”图标。 
4. 确保跨报表钻取开关为“打开”。 
5. 保存报表。

分配过程如上所述。 报表已准备好进行跨报表钻取体验。 

在下一部分中，我们将从用户的角度来查看体验。

## <a name="cross-report-drillthrough-experience"></a>跨报表钻取体验

为报表配置跨报表钻取体验时，可以使用该功能。

选择 Power BI 服务中的源报表，然后按照设置目标页时指定的方式选择使用一个或多个字段的视觉对象。 接下来，右键单击数据点以打开视觉对象上下文菜单，然后选择“钻取”  。

![Power BI 服务中的源报表的屏幕截图，突出显示了钻取](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

随后会在目标跨报表钻取页中看到结果，就像在创建目标时进行设置一样。 根据钻取设置对结果进行筛选。

> [!IMPORTANT]
> Power BI 缓存跨报表钻取目标。 进行更改后，如果看不到预期的钻取目标，请确保刷新浏览器。 

跨报表目标的格式如下： 

`Target Page Name [Target Report Name]`

选择要钻取到的目标页后，Power BI 会转到该页面。 它基于目标页的设置传递筛选器上下文。 

来自源视觉对象的筛选器上下文可以包含以下内容： 

* 影响源视觉对象的报表、页面和视觉级筛选器。 
* 影响源视觉对象的交叉筛选和交叉突出显示。 
* 页面上的切片器和同步切片器。
* URL 参数。

登录到目标报表上进行钻取时，Power BI 仅为用于查找字段名称和表名称的精确字符串匹配的字段应用筛选器。 Power BI 不会应用目标报表中的粘滞筛选器。 但是，它会应用默认个人书签（如果存在）。 例如，如果默认个人书签包含“国家/地区 = 美国”的报表级筛选器，则 Power BI 会先应用该筛选器，然后再应用源视觉对象中的筛选器上下文  。 

对于跨报表钻取，Power BI 会将筛选器上下文传递给目标报表中的所有标准页。 Power BI 不会传递工具提示页面的筛选器上下文，因为工具提示页面是根据调用工具提示的源视觉对象筛选的。

如果要在执行跨报表钻取操作后返回到源报表，请使用浏览器的“后退”按钮  。 

## <a name="next-steps"></a>后续步骤

你可能还会对以下文章感兴趣：

* [在 Power BI Desktop 中使用切片器](visuals/power-bi-visualization-slicers.md)
* [在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)


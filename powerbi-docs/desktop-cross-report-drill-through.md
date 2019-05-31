---
title: 在 Power BI Desktop 中使用跨报表钻取
description: 了解如何从一个报表钻取到 Power BI Desktop 中的另一个
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375197"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>在 Power BI Desktop 中使用跨报表钻取

借助 Power BI Desktop 中的跨报表钻取功能，您可以根据上下文跳从报表到其他报表。 只要报表相同的工作区或 Microsoft Power BI 服务中的应用内，也是如此。 连接两个或多个报表具有相关的内容，并将传递以及跨报表连接的筛选器上下文使用跨报表钻取。 在本文中，您将学习如何设置 Power BI 报表的跨报表钻取和用户体验在为自己使用跨报表钻取时。

![Power BI Desktop 的屏幕截图钻取选项](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

下面的定义必须了解，我们开始之前设置和使用跨-报表钻取以下内容：

* **源视觉对象：** 视觉对象使用的视觉对象上下文菜单调用钻取操作。
* **源报表：** 包含源视觉对象以供跨报表钻取报表。
* **目标页：** 用户启动的钻取操作后进入页。
* **目标报表：** 包含用于跨报表钻取目标页的报表。

## <a name="enable-cross-report-drillthrough"></a>启用跨报表的钻取

若要使报表成为跨报表钻取操作的目标，必须启用该报表中的功能**选项**窗口。 转到**文件** > **选项和设置** > **选项**，然后转到**报告设置**附近在左侧页面的底部。

选择**允许在此报表使用的其他报表钻取目标中使用视觉对象**复选框，如下图所示。

![屏幕截图的选项窗口中，并突出显示的报表设置](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

现在启用跨报表钻取功能。

## <a name="set-up-cross-report-drillthrough"></a>设置跨报表钻取

跨报表钻取设置十分类似于设置钻取报表中。 允许目标钻取已启用的页的其他视觉对象在目标页上，启用钻取功能。 若要创建在一个报表的钻取的步骤，请参阅[在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)。

若要开始安装过程，您需要执行几个初始步骤：

* 设置钻取目标页，然后从工作区或应用中的其他报表进行访问。
* 允许报表来查看从外部其自己的报表的钻取页面。

查找中的钻取选项**字段**一部分**可视化效果**窗格中，在下图中所示。

![屏幕截图的可视化效果窗格中，突出显示的钻取选项](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

启用钻取页面的第一步是验证源和目标报表的数据模型。 请确保： 

* 在这两种数据模型中存在你想要传递的字段。
* 字段的名称和到其所属，这些表的名称是相同的 （字符串也必须匹配，并区分大小写）。

例如，如果你想要将筛选器传递字段*国家/地区*表内*Geography*，这两个模型都必须具有*Geography*表中，和一个*国家/地区*字段中的表。 如果没有，则必须更新的字段名称或基础模型中的表名称。 只需更新字段的显示名称将无法正常工作的跨报表钻取。 （请注意，每个报表中的架构不一定要完全相同。）

若要开始使用安装程序，需要做好准备的目标页。 在 Power BI Desktop 中，转到页面，并确保**跨报表**钻取切换键设置为**上**。 

![跨报表切换设置为 On 的屏幕截图](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

接下来，将您想要用作钻取目标拖动到画布上的字段。 选择你想要用作一种类别，或归纳出度量值的字段。 此时，可以选择是否想要禁用**保留所有筛选器**切换视觉对象。 如果不想要传递其他应用的筛选器从源 visual 目标钻取到可视化，选择**关闭**。

> [!NOTE]
> 如果使用的跨报表钻取的页，则应删除**回**自动添加的按钮。 **回**按钮仅适用于 nagivation 在一个报表。 

配置视觉对象后，请确保在 Power BI 服务中，如果将报表保存或保存并发布报表，如果您使用的 Power BI Desktop。

前面部分介绍了如何对 Power BI Desktop 中启用跨报表钻取 (在**选项**窗口)。 如果你使用 Power BI 服务以创建用于启用跨报表钻取，必须跨报表钻取目标： 

1. 选择位于你的目标报表和源报表的工作区。
2. 选择**报表**。
3. 选择**设置**源报表的图标。
4. 请确保跨报表钻取开关处于**上**。
5. 保存报表。

分配过程如上所述。 准备好进行跨报表钻取体验您的报表。 

在下一步部分中，我们看一下从用户的角度来看的体验。

## <a name="cross-report-drillthrough-experience"></a>跨报表钻取体验

在配置报表的跨报表钻取体验时，可以放置要使用的功能。

在 Power BI 服务中，选择源报表，然后选择视觉对象使用的字段或字段中指定设置的目标页时的方式。 接下来，右键单击要打开视觉对象上下文菜单中，选择数据点**钻取**。

![在 Power BI 服务中，源报表的带有钻取突出显示的屏幕截图](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

正如您把它们设置在创建目标时，然后将查看目标跨报表钻取页中的结果。 根据钻取设置筛选结果。

> [!IMPORTANT]
> Power BI 将缓存跨报表钻取目标。 如果进行了更改，请确保如果看不到钻取目标按预期方式刷新浏览器。 

跨报表的目标的格式以以下方式： 

`Target Page Name [Target Report Name]`

选择你想要钻取的目标页后，Power BI 将转到该页面。 它传递基于目标页的设置的筛选器上下文。 

自源视觉对象的筛选器上下文可以包括： 

* 报表、 页面和视觉对象级别筛选器会影响源视觉对象。 
* 交叉筛选和交叉突出显示的会影响源视觉对象。 
* 在页和同步切片器上的切片器。
* URL 参数。

当你选择用于钻取目标报表时，Power BI 仅适用为其找到确切的字符串匹配字段名称和表名称的字段的筛选器。 从目标报表，power BI 不适用于粘滞筛选器。 如果存在，它，但是，应用默认的个人书签。 例如，如果默认的个人书签包括的报表级别筛选器*国家/地区 = US*，Power BI 应用该筛选器第一次之前从源视觉对象应用筛选器上下文。 

用于跨报表钻取，Power BI 将筛选器上下文传递到目标报表中的所有标准页面。 Power BI 不会传递用于工具提示页筛选器上下文，因为工具提示页根据筛选上源视觉对象调用工具提示。

如果你想要跨报表钻取操作后返回到源报表，使用浏览器的**回**按钮。 

## <a name="next-steps"></a>后续步骤

你可能还会对以下文章感兴趣：

* [在 Power BI Desktop 中使用切片器](visuals/power-bi-visualization-slicers.md)
* [在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)


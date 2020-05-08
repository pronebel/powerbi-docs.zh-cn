---
title: 在 Power BI Desktop 中使用跨报表钻取
description: 了解如何在 Power BI Desktop 中从一个报表钻取到另一个报表
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 33d0b7850b5e396d8f03e80cbcb32768fb26bf6d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "81439793"
---
# <a name="use-cross-report-drillthrough-in-power-bi"></a>在 Power BI 中使用跨报表钻取

借助 Power BI 跨报表钻取  功能，可以在相同 Power BI 服务工作区或应用中根据上下文从一个报表跳转到另一个报表。 可以使用跨报表钻取连接两个或更多具有相关内容的报表，并将筛选器上下文与跨报表连接一起传递。 

若要启动跨报表钻取，请在源报表  的源视觉对象  中选择数据点，然后从上下文菜单中选择跨报表“钻取”  目标。 

![Power BI 跨报表钻取选项](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

钻取操作会在目标报表  中打开目标页  。 

![Power BI Desktop 跨报表钻取目标](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

本文演示如何为 Power BI 报表设置和使用跨报表钻取。

> [!NOTE]
> 无法在“我的工作区”  中将跨报表钻取用于单独共享的[“与我共享”报表](service-share-dashboards.md#share-a-dashboard-or-report)。 若要使用跨报表钻取，必须在从中共享它们的工作区中访问报表。

## <a name="enable-cross-report-drillthrough"></a>启用跨报表钻取

启用跨报表钻取的第一步是验证源报表和目标报表的数据模型。 虽然每个报表中的架构不必相同，但要传递的字段必须存在于这两个数据模型中。 字段的名称和它们所属的表的名称必须相同。 字符串必须匹配，并区分大小写。

例如，如果要在“美国”表内的“州”字段上传递筛选器，则两个模型都必须具有“美国”表和该表中的“州”字段     。 如果没有，则必须在基础模型中更新字段名称或表名称。 仅更新字段的显示名称无法使跨报表钻取正常运行。

验证模型之后，使源报表可以使用跨报表钻取。 

1. 在 Power BI Desktop 中，依次转到“文件”   > “选项和设置”   > “选项”  。 
1. 在“选项”  窗口左侧导航中的“当前文件”  部分底部，选择“报表设置”  。 
1. 在右下角的“跨报表钻取”  下，选择“允许此报表中的视觉对象使用其他报表中的钻取目标”  。 
1. 选择“确定”。  
   
   ![在 Power BI Desktop 中启用跨报表钻取](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

还可以从 Power BI 服务启用跨报表钻取。
1. 在 Power BI 服务中，选择包含目标和源报表的工作区。
1. 在工作区列表中的源报表名称旁，选择“更多选项”  ，然后选择“设置”  。 
1. 在“设置”  窗格底部旁边的“跨报表钻取”  下，选择“允许此报表中的视觉对象使用其他报表中的钻取目标”  ，然后选择“保存”  。
   
   ![在 Power BI 服务中启用跨报表钻取](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drillthrough-target"></a>设置跨报表钻取目标

为跨报表钻取设置目标页类似于在报表中设置钻取。 在目标页上启用钻取使其他视觉对象能够以已启用页为目标进行钻取。 若要在单个报表中创建钻取，请参阅[在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)。

可以在 Power BI Desktop 或 Power BI 服务中为跨报表钻取设置目标。 
1. 编辑目标文件，然后在目标报表的目标页上，选择“可视化”  窗格的“字段”  部分。 
1. 在“钻取”  下，将“跨报表”  切换为“开启”  。 
1. 将要用作钻取目标的字段拖动到“在此处添加钻取字段”  中。 对于每个字段，选择是否要在字段用作类别时或是如同度量值一样进行汇总时允许钻取。 
1. 选择是否要对视觉对象“保留所有筛选器”  。 如果不想将已应用于源视觉对象的筛选器传递到目标视觉对象，请选择“关闭”  。
   
   ![“可视化”窗格，突出显示了“钻取”选项](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. 如果将页面仅用于跨报表钻取，请删除自动添加到画布的“后退”按钮  。 “后退”按钮仅适用于报表中的导航  。 
1. 配置目标页之后，保存报表（如果使用的是 Power BI 服务）或保存并发布报表（如果使用的是 Power BI Desktop）。

分配过程如上所述。 报表已准备好进行跨报表钻取。 

## <a name="use-cross-report-drillthrough"></a>使用跨报告钻取

若要使用跨报表钻取，请在 Power BI 服务中选择源报表，然后按照设置目标页时指定的方式选择使用钻取字段的视觉对象。 右键单击数据点以打开视觉对象上下文菜单，选择“钻取”  ，然后选择钻取目标。 跨报表钻取目标的格式设置为“页名称 [报表名称]”  。

![Power BI 跨报表钻取选项](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

会在目标跨报表钻取页中看到结果，就像在创建目标时进行设置一样。 根据钻取设置对结果进行筛选。

![Power BI Desktop 跨报表钻取目标](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> Power BI 缓存跨报表钻取目标。 进行更改后，如果看不到预期的钻取目标，请确保刷新浏览器。 

如果在设置目标页时将“保留所有筛选器”  设置为“开启”  ，则来自源视觉对象的筛选器上下文可以包含以下内容： 

- 影响源视觉对象的报表、页面和视觉对象级筛选器 
- 影响源视觉对象的交叉筛选和交叉突出显示 
- 页面上的切片器和同步切片器
- URL 参数

登录到目标报表上进行钻取时，Power BI 仅为具有字段名称和表名称的精确字符串匹配的字段应用筛选器。 

Power BI 不应用来自目标报表的粘滞筛选器，但它会应用默认个人书签（如果有）。 例如，如果默认个人书签包含“国家/地区 = 美国”的报表级筛选器，则 Power BI 会应用该筛选器，然后再应用源视觉对象中的筛选器上下文  。 

对于跨报表钻取，Power BI 会将筛选器上下文传递给目标报表中的标准页。 Power BI 不会传递工具提示页面的筛选器上下文，因为工具提示页面是根据调用工具提示的源视觉对象筛选的。

如果要在执行跨报表钻取操作后返回到源报表，请使用浏览器的“后退”按钮  。 

## <a name="next-steps"></a>后续步骤

你可能还会对以下文章感兴趣：

- [Power BI 中的切片器](visuals/power-bi-visualization-slicers.md)
- [在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)


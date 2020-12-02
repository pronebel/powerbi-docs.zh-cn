---
title: 使用 Power BI Desktop 选择视觉对象中的多个数据元素或多个视觉对象
description: 只需按住 CTRL 并单击即可在 Power BI Desktop 视觉对象中选择多个数据点
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 11/11/2020
LocalizationGroup: Create reports
ms.openlocfilehash: d373aab740d7c0431ef89361c767f027cb1dd351
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396397"
---
# <a name="multi-select-data-elements-data-points-and-visuals-in-power-bi-desktop"></a>使用 Power BI Desktop 选择多个数据元素、数据点和视觉对象

可以使用 Power BI Desktop 在一个视觉对象中选择多个数据元素、在一个视觉对象中选择多个数据点，或在一个报表中选择多个视觉对象。 以下各节依次介绍其中的每个步骤。

## <a name="select-multiple-data-points"></a>选择多个数据点

在 Power BI Desktop 中，只需单击给定视觉对象中的数据点即可突出显示该视觉对象中的数据点。 例如，如果你有重要的条形图或图表元素，并且希望报表页上的其他视觉对象根据你的选择突出显示数据，可以单击一个视觉对象中的数据元素并查看反映在页面上的其他视觉对象中反映的结果。 这是基本的或单项选择突出显示。 下图显示了基本突出显示。 

![选择的单个数据点](media/desktop-multi-select/multi-select_01.png)

借助多重选择，现在可以在 Power BI Desktop 报表页中选择多个数据点，并突出显示页面上所有视觉对象中的结果。 这相当于 and 语句或功能，如“highlight results for Idaho and Virginia”（突出显示爱达荷州和弗吉尼亚州的结果）。 若要在视觉对象中选择多个数据点，使用“CTRL+单击”选择多个数据点。 下图显示了选择的多个数据点（多重选择）。

![选择的多个数据点](media/desktop-multi-select/multi-select_02.png)

此功能看似很简单，但在创建、共享报表和与报表交互时，它会启发各种可能性。 

## <a name="select-multiple-elements-using-rectangle-select-preview"></a>使用矩形选择来选择多个元素（预览）

可以使用矩形选择（通常也称为“套索选择”）在一个视觉对象中选择多个数据元素，或在一个报表中选择多个视觉对象。 

### <a name="select-multiple-visuals-on-the-canvas"></a>在画布上选择多个视觉对象

通过单击并拖动画布来创建矩形套索，以选择多个视觉对象和其他报表元素。 完全封装在套索内的所有视觉对象都将被选中。 如果按下 Ctrl 或 Shift 键（按住 Ctrl 并单击各个视觉对象进行多选），后续套索选择会将所选视觉对象添加到当前选择的多个内容中。 

如果已选择并套索一个视觉对象，请使用 Ctrl 或 Shift 关闭该选定内容。 套索不选择组内的单个视觉对象，但可以通过封装整个组来选择组。

画布不会随矩形套索选择自动滚动。 

### <a name="select-multiple-data-points-in-a-visual"></a>选择一个视觉对象中的多个数据点

可以使用相同的矩形套索步骤选择一个视觉对象中的多个数据点。 按住 Ctrl 键的同时，在视觉对象中单击并拖动以选择多个数据点。 释放鼠标按钮时，与矩形所选区域重叠的所有点都将被选中，之前套索选择的所有内容也将被保留。 如果在选择时用 Ctrl 套索选择了一个包含先前选择的点的区域，那么这些数据点将被取消选择（关闭）；使用套索的效果相同，Ctrl 并单击每个点。 

在进行套索选择时，如果使用 Shift 键，则以前选择的内容将被保留，并且已选择的数据点将保持选中状态。 因此，如果在执行套索选择时使用 Shift，则只向所选内容添加数据点，而不是切换所选区域中的数据点。

可以单击绘图区域上的空白区域清除当前选择，无需按键盘键。

有关此功能的详细信息，请参阅[关于此功能发布的博客文章](https://powerbi.microsoft.com/blog/power-bi-desktop-august-2020-feature-summary/#_Data_point)。

在一个视觉对象中选择多个数据点时，存在一些限制和注意事项：

* 线条、区域、散点图、树形图和地图支持套索选择
* 一次最多可以选择 300 个数据点
* 在 Power BI 服务中查看报表时，仅当保存和发布报表时启用套索选择功能时，矩形选择才会启用

## <a name="next-steps"></a>后续步骤

你可能还会对以下文章感兴趣：

* [在 Power BI Desktop 报表中使用网格线和对齐网格](desktop-gridlines-snap-to-grid.md)
* [关于 Power BI 报表中的筛选器和突出显示](power-bi-reports-filters-and-highlighting.md)


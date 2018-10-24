---
title: 在 Power BI Desktop 中使用切片器
description: 可以在 Power BI Desktop 中使用切片器筛选、突出显示和自定义报表
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: df4afe91de955eabfba6eeea9022cc5f9475cc33
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336843"
---
# <a name="using-slicers-power-bi-desktop"></a>在 Power BI Desktop 中使用切片器

可以在 Power BI Desktop 中使用切片器筛选报表页上视觉对象的结果。 此外，借助切片器，可以通过与切片器本身交互来轻松调整应用的筛选器。 还可以指定切片器如何显示以及如何与切片器进行交互的选项。 下图显示了一个切片器，可以看到它的“类型”下拉列表。 

![桌面版的切片器](./media/desktop-slicers/desktop-slicers_01.png)

切片器可以在以下任一类型中显示：

* 列表
* 下拉列表
* 介于
* 小于或等于
* 大于或等于

可以通过单击“可视化”窗格中的“切片器”视觉对象向报表添加切片器。

![切片器视觉对象类型](./media/desktop-slicers/desktop-slicers_02.png)

切片器在 Power BI Desktop 和 Power BI 服务中的操作类似。 若要了解介绍切片器使用方式的文章，请参阅 [Power BI 服务中的切片器](power-bi-visualization-slicers.md)。

## <a name="synchronize-slicers-across-report-pages"></a>跨报表页同步切片器

在 Power BI Desktop 中，可以跨多个报表页同步切片器。 若要同步切片器，请在功能区的“视图”窗格中，选择“同步切片器”。 在同步切片器时，将出现“同步切片器”窗格，如下图所示。

![显示“同步切片器”窗格](./media/desktop-slicers/desktop-slicers_03.png)

在“同步切片器”窗格中，可以指定应如何跨报表页同步切片器。 可以指定每个切片器是否应该应用于各个独立的报表页，以及切片器是否应该在各个独立的报表页上可见。

例如，可以将切片器放置在报表的第 2 页上，如下图所示。 然后，可以选择该切片器是否应该应用于每个所选页面，以及该切片器是否应在报表中的每个所选页面上可见。 可以为每个切片器应用上述任意组合。 

![同步切片器](./media/desktop-slicers/desktop-slicers_04.png)

使用窗格中的“添加到全部”链接将所选切片器应用到报表中的所有页面。


请注意，在“同步切片器”窗格上显示的选择仅适用于所选切片器。 可以将多个切片器应用于不同页面，并使用窗格定义每个切片器如何分别应用于报表中的不同页面。 

尽管可以同步所选的切片器，但不会同步样式、编辑和删除等其他选择。 

## <a name="advanced-options-for-slicers"></a>切片器的高级选项

还可在“同步切片器”窗格的“高级选项”部分中将组名称应用于切片器集合，并跨页面同步共享同一组的切片器。 

![切片器的组名称](./media/desktop-slicers/desktop-slicers_05.png)

通过此功能，可创建一组自定义的切片器来保持同步。 系统会提供默认名称，但可使用任何喜欢的名称。 

组名称使切片器更具灵活性。 可创建单独的组来同步使用相同字段的切片器，也将使用不同字段的切片器放入同一组中。 

## <a name="how-filtering-affects-selection-in-slicers"></a>筛选如何影响切片器中的选择

如果在切片器中进行选择，然后应用一个在通常情况下会删除所选项的筛选器，该所选项仍会留在切片器项列表的底部。 如果删除筛选器，则所选内容仍会留在切片器中。 你会注意到，如果从切片器中取消选中所选项，该项将从列表中消失。

![切片器中保留的所选项](./media/desktop-slicers/retained-selection-in-slicers.gif)


## <a name="next-steps"></a>后续步骤

你可能还会对以下文章感兴趣：

* [Power BI 服务中的切片器](power-bi-visualization-slicers.md)
* [在 Power BI Desktop 中使用数值范围切片器](../desktop-slicer-numeric-range.md)
* [在 Power BI Desktop 中使用相对日期切片器和筛选器](desktop-slicer-filter-date-range.md)


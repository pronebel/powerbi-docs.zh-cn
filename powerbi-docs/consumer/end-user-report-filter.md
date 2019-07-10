---
title: 浏览报表“筛选器”窗格
description: 如何在面向使用者的 Power BI 服务中向报表添加筛选器
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67533015"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>浏览报表“筛选器”窗格

本文将介绍 Power BI 服务中的报表“筛选器”窗格  。 使用筛选器可在数据中发现新见解。

Power BI 中有许多不同的方法来筛选数据。 有关筛选器的详细信息，请参阅[关于 Power BI 报表中的筛选器和突出显示](../power-bi-reports-filters-and-highlighting.md)。

![浏览器中报表的屏幕截图，其中箭头指向“筛选器”选项。](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>使用报表“筛选器”窗格

当同事与你共享报表时，请务必找到“筛选器”  窗格。 有时它在报表右侧处于折叠状态。 选择它以将其展开。

![展开“筛选器”窗格的报表屏幕截图。](media/end-user-report-filter/power-bi-filter-pane.png)

“筛选器”窗格包含报表设计者添加到报表中的筛选器   。 使用者（例如你）可与现有筛选器交互并保存更改，但不能向报表添加新的筛选器  。 例如，在上面的屏幕截图中，设计者添加了两个页面级筛选器：“细分市场”和“年份”   。 可与这些筛选器交互并进行更改，但无法添加第三个页面级筛选器。

在 Power BI 服务中，报表会保留在“筛选器”窗格中所做的任何更改  。 该服务将这些更改传递到报表的移动版本。

要将“筛选器”窗格重置为设计者的默认值，请选择 ![“重置为默认值”选项的屏幕截图。](media/end-user-report-filter/power-bi-reset.png)  从顶部菜单栏中。

## <a name="view-all-the-filters-for-a-report-page"></a>查看报表页的所有筛选器

“筛选器”窗格会显示设计者向报表添加的所有筛选器  。 也可在“筛选器”窗格查看筛选器相关信息并与之交互  。 可保存所作的更改，也可使用“重置为默认值”，还原到原始筛选器设置  。

若想保存更改，也可创建个人书签。  有关详细信息，请参阅[什么是书签？](end-user-bookmarks.md)。

“筛选器”窗格可显示和管理多种报表筛选器类型  。 它们可以应用于视觉对象、报表页和整个报表。

在本例中，我们选择了一个带有两个筛选器的视觉对象。 报表页也有筛选器，列于“此页上的筛选器”标题下  。 此外，整个报表有一个“日期”筛选器  。

![标出可视化效果极其相关筛选器的报表屏幕截图。](media/end-user-report-filter/power-bi-all-filters2.png)

部分筛选器旁边有“(全部)”选项  。 “(全部)”表示筛选器中包含所有值  。 在上述屏幕截图中，“细分市场(全部)”表示此报表页包含所有产品细分市场的相关数据  。 如果选择“西部区域”页面级筛选器，则报表页仅包含西部区域的数据  。

查看此报表的任何人都可与这些筛选器进行交互。

### <a name="view-only-those-filters-applied-to-a-visual"></a>仅查看应用于视觉效果的筛选器

要更仔细地查看应用于特定视觉对象的筛选器，请将鼠标悬停在视觉对象上以显示筛选器图标 ![筛选器图标的屏幕截图](media/end-user-report-filter/power-bi-filter-icon.png)。 选择该筛选器图标，查看包含所有筛选器和切片器等影响该视觉对象的弹出窗口。 弹出窗口上的筛选器与“筛选器”窗格上显示的筛选器相同  。

![筛选器列表的屏幕截图，其箭头指向这些筛选器在筛选器窗格中的位置。](media/end-user-report-filter/power-bi-hover-visual-filter.png)

下面是此视图可显示的筛选器类型：

- 基本筛选器

- 切片器

- 交叉突出显示

- 交叉筛选

- 高级筛选器

- 前 N 个筛选器

- 相对日期筛选器

- 同步切片器

- 包括/排除筛选器

- 通过 URL 传递的筛选器

在下例中：

1. 我们可看到柱形图已经过交叉筛选。

1. “包含”显示交叉筛选适合“细分市场”且其中包含 3 个市场   。

1. 已对“季度”应用切片器  。

1. 此报表页上应用的筛选器是“区域”，且 

1. 此视觉对象上应用了“isVanArsdel”和“年份”筛选器   。

![报表及其筛选器的屏幕截图，其中筛选器的编号与上面的编号列表一致。](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>在筛选器中搜索

有时，筛选器可能包含很长一列值。 可使用搜索框查找并选择所需的值。

![显示如何在筛选器中搜索的屏幕截图。](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>显示筛选器详细信息

要了解筛选器，请查看可用值和计数。  悬停鼠标并选择筛选器名称旁的箭头可查看该筛选器的详细信息。
  
![显示所选西部区域的筛选器屏幕截图。](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>更改筛选器选择

搜索数据见解的一种方法是与筛选器交互。 可使用字段名称旁边的下拉箭头更改筛选器选择。  根据 Power BI 正在筛选的筛选器和数据类型，选项范围从简单的列表选择到确定日期或数字的范围。 在下列高级筛选器中，我们已将树状图上的“年初至今总单位”筛选器更改为介于 2,000 到 3,000 之间  。 请注意，此更改会从树状图中删除 Prirum。
  
![显示已选择 Fashions Direct的报表及其筛选器的屏幕截图。](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> 要一次选择多个筛选器值，请按住 Ctrl 键。 大多数筛选器都支持多选。

### <a name="reset-filter-to-default"></a>将筛选器重置为默认值

若想撤消对筛选器所作的全部更改，请在顶部菜单栏中选择“重置为默认值”  。  此选择会将筛选器还原为报表设计者设置的原始状态。

![“重置为默认值”选项的屏幕截图。](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>清除筛选器

如果只存在一个你想设置为“(全部)”的筛选器，请选择橡皮擦图标 ![橡皮擦图标屏幕截图](media/end-user-report-filter/power-bi-eraser-icon.png) 将其清除  。 筛选器名称旁边。
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>后续步骤

了解[视觉对象在报表页上交叉筛选和交叉突出显示](end-user-interactions.md)的方式和原因
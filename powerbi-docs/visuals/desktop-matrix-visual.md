---
title: 在 Power BI 中使用矩阵视觉对象
description: 了解矩阵视觉对象如何在 Power BI 中实现阶梯布局和细化突出显示
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6ad8900e5a95148b3f8333aa1953cc939d56f0e6
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375455"
---
# <a name="use-the-matrix-visual-in-power-bi"></a>在 Power BI 中使用矩阵视觉对象
**矩阵**visual 类似于**表**。  表支持 2 个维度和数据是平面，显示和未聚合的含义重复值。 矩阵可以更轻松地跨多个维度中有意义的方式显示数据--支持阶梯的布局。 矩阵自动聚合数据，并使向下钻取。 

你可以创建矩阵视觉对象中的**Power BI Desktop**并**Power BI 服务**报表和与该报表页上的其他视觉对象矩阵内的交叉突出显示元素。 例如，你可以选择行、 列和各个单元格并交叉突出显示。 此外，用于在单个单元格和多个单元格选定区域复制和粘贴到其他应用程序。 

![交叉突出显示的矩阵和圆环图](media/desktop-matrix-visual/matrix-visual_2a.png)

矩阵有许多相关功能，我们将在本文的下面各部分中逐一介绍它们。


## <a name="understanding-how-power-bi-calculates-totals"></a>了解 Power BI 计算总计的方式

在进入如何使用“矩阵”  视觉对象的步骤之前，请务必了解 Power BI 在表格和矩阵中如何计算总计和小计的值。 对于总计和小计行，在基础数据的全部行上求取度量值，这不  仅仅是在可见的或显示的行中简单地相加值。 这意味着最终总计行的值与预计的值存在差异。 

看看以下矩阵视觉对象。 

![将表和矩阵进行比较](media/desktop-matrix-visual/matrix-visual_3.png)

在此示例中，显示矩阵视觉对象最右侧中的每一行*量*为每个销售人员/日期组合。 但是，由于显示的一个销售人员对应多个日期，这些数字可以出现不止一次。 因此，基础数据的准确总计并不等于可见值的简单相加。 当要求和的值位于一对多关系的“一”这一侧时，这是一种常见模式。

查看总计和小计时，请注意这些值是基于基础数据的，并不仅仅基于可见值。 

<!-- use Nov blog post video

## Expanding and collapsing row headers
There are two ways you can expand row headers. The first is through the right-click menu. You’ll see options to expand the specific row header you clicked on, the entire level or everything down to the very last level of the hierarchy. You have similar options for collapsing row headers as well.

![](media/desktop-matrix-visual/power-bi-expand1.png)

You can also add +/- buttons to the row headers through the formatting pane under the row headers card. By default, the icons will match the formatting of the row header, but you can customize the icons’ color and size separately if you want. 
Once the icons are turned on, they work similarly to the icons from PivotTables in Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

The expansion state of the matrix will save with your report. It can be pinned to dashboards as well, but consumers will need to open up the report to change the state. Conditional formatting will only apply to the inner most visible level of the hierarchy. Note that this expand/collapse experience is not currently supported when connecting to AS servers older than 2016 or MD servers.

![](media/desktop-matrix-visual/power-bi-expand3.png)

Watch the following video to learn more about expand/collapse in the matrix:

-->
## <a name="using-drill-down-with-the-matrix-visual"></a>向下钻取使用矩阵视觉对象
使用矩阵视觉对象，你可以执行各种有意思的向下钻取活动之前无法。 这包括向下钻取行、列、单独分区和单元格。 让我们来看看每种向下钻取活动的工作原理。

### <a name="drill-down-on-row-headers"></a>向下钻取行标题
在“可视化效果”  窗格中，如果你向“字段”  的“行”  部分添加多个字段，可以为矩阵视觉对象的行启用向下钻取功能。 这类似于创建层次结构，以便于你可以向下钻取（然后备份）层次结构，并分析每个级别的数据。

在下图中，**行**部分包含*销售阶段*并*机会大小*，我们可以钻取的行中创建的分组 （或层次结构）。

![显示所选的行的筛选器卡](media/desktop-matrix-visual/power-bi-rows-matrix.png)

如果视觉对象在“ **行** ”部分中形成了分组，那么视觉对象本身会在其左上角显示“ *钻取* ”和“ *扩展* ”图标。

![矩阵，其中所述的钻取控件](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

选择这些按钮可以向下钻取（或备份）层次结构，类似于其他视觉对象中的钻取和扩展行为。 在这种情况下，我们可以向下钻取从*销售阶段*到*机会大小*下, 图中，选择向下的钻取一个级别图标 （耙图标） 中所示。

![矩阵，其中所述的耙图标](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

除了使用这些图标，可以选择任意行标题，并从显示的菜单中选择向下钻取。

![矩阵中的行的菜单选项](media/desktop-matrix-visual/power-bi-matrix-menu.png)

请注意，显示的菜单中有多个选项，分别用于执行不同的操作：

选择**向下钻取**展开的矩阵*的*行级别，*不包括*所有其他行标题除所选行标题。 在下图中，**提案** > **向下钻取**选择。 请注意，其他顶层行不会再出现在矩阵中。 这种钻取方法是一项十分有用的功能，当我们介绍“交叉突出显示”  部分时，你会发现这项功能特别棒。

![下移一个级别的矩阵](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

选择**向上钻取**图标，返回上一顶层视图。 如果接下来选择**提案** > **显示下一级别**，会按升序列出所有下一级项 (在这种情况下，*机会大小*字段)，不含更高级别的层次结构分类。

![使用显示下一级别的矩阵](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

选择**向上钻取**图标让矩阵显示所有顶层类别，然后选择左上角**提案** > **扩展至下一级别**到请参阅层次结构-这两种级别的所有值*销售阶段*并*机会大小*。

![使用展开下一级别的矩阵](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

此外可以使用**展开**菜单项来控制显示更多。  例如，选择**提案** > **展开** > **选择**。 Power BI 将显示一个总计行对于每个*销售阶段*和全部*机会大小*选项*提案*。

![展开应用于建议后的矩阵](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>向下钻取列标题
类似于向下钻取行的功能，您可以也向下钻取**列**。 在下图中，有两个字段**列**字段井、 创建层次结构类似于我们在本文前面的行的使用。 在中**列**良好字段中，我们有*区域*并*段*。 只要第二个字段已添加到**列**，新的下拉菜单中，显示在视觉对象，它当前显示**行**。

![之后的第二个列值添加矩阵](media/desktop-matrix-visual/power-bi-matrix-row.png)

若要向下钻取列，请选择**列**从*上的钻取*可在矩阵的左上角的菜单。 选择*东部*区域，然后选择**向下钻取**。

![向下钻取列菜单](media/desktop-matrix-visual/power-bi-matrix-column.png)

当选择**向下钻取**，为列层次结构的下一级*区域 > 东部*显示，在这种情况下是*机会计数*。 在另一个区域显示，但将灰显。

![与列的矩阵钻取一个级别](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

其余的菜单项对列的行的相同方式工作 (请参阅上一节**向下钻取行标题**)。 你可以**显示下一级别**并**扩展至下一级别**就像可以按照与行的列。

> [!NOTE]
> 矩阵视觉对象左上角的“向下钻取”和“向上钻取”仅对行有效。 必须使用右键单击菜单，才能向下钻取列。
> 
> 

## <a name="stepped-layout-with-matrix-visuals"></a>使用矩阵视觉对象实现阶梯布局
“矩阵”  视觉对象自动缩进层次结构中每个父级下的子类别，这就是所谓的“阶梯布局”  。

在 *旧* 版矩阵视觉对象中，子类别显示在完全不同的列中，占用视觉对象更多空间。 下图展示了旧版“矩阵”  视觉对象中的表；请注意，子类别位于单独的列中。

![矩阵的默认格式的旧方法](media/desktop-matrix-visual/matrix-visual_14.png)

下图展示了采用“阶梯布局”  的“矩阵”  视觉对象的实际效果。 请注意，类别“ *计算机* ”将其子类别（“计算机附件”、“台式机”、“笔记本电脑”、“显示器”等）略微缩进，让视觉对象变得更简洁紧凑。

![当前该矩阵格式数据的方式](media/desktop-matrix-visual/matrix-visual_13.png)

可以轻松调整“阶梯布局”设置。 选择“矩阵”  视觉对象后，在“可视化效果”  窗格的“格式”  部分（滚动油漆刷图标）中，展开“行标题”  部分。 下面有两个选项：“阶梯布局”  开关（用于启用或禁用阶梯布局）和“阶梯布局缩进”  （用于指定缩进量，以像素为单位）。

![行标题卡片显示阶梯布局控件](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

如果禁用“**阶梯布局**”，子类别会显示在另一列中，而不是在父类别下缩进。

## <a name="subtotals-with-matrix-visuals"></a>矩阵视觉对象小计
可以在矩阵视觉对象中，打开或关闭行和列的小计。 在下图中，可以看到行小计已设置为“打开”  。

![矩阵显示总计和小计](media/desktop-matrix-visual/matrix-visual_20.png)

在“可视化效果”  窗格的“格式”  部分中，展开“小计”  卡，并将“行小计”  滑块移动至“关闭”  。 执行此操作后，将不显示小计。

![带有小计处于关闭状态的矩阵](media/desktop-matrix-visual/matrix-visual_21.png)

相同的操作过程适用于列小计。

## <a name="cross-highlighting-with-matrix-visuals"></a>使用矩阵视觉对象进行交叉突出显示
借助“矩阵”  视觉对象，可以选择矩阵中的任意元素，作为交叉突出显示的依据。 在“矩阵”  中选择一列即可突出显示它，报表页上的其他任何视觉对象也会予以反映。 此类型的交叉突出显示一直是其他视觉对象和数据点选择的常见功能，因此现在“矩阵”  视觉对象也可以提供此相同功能。

此外，还可以在按住 Ctrl 的同时单击鼠标进行交叉突出显示。 例如，在下图中，我们选择了“矩阵”  视觉对象中的一组子类别。 请注意，视觉对象中未选择的项为灰显，报表页上的其他视觉对象也会反映“矩阵”  视觉对象中选择的项。

![报表页上的矩阵 highighted 跨](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>复制 Power BI 中的值以供在其他应用程序中使用

矩阵或表可能具有你想要在其他应用程序中使用的内容，例如 Dynamics CRM、Excel、甚至其他 Power BI 报表。 通过右键单击 Power BI，可以将单个单元格或选定的单元格复制到剪贴板，并粘贴到其他应用程序。

![复制选项](media/desktop-matrix-visual/power-bi-cell-copy.png)

* 若要复制单个单元格的值，选择单元格，右键单击，并选择“复制值”  。 现在可以将此剪贴板上未格式化的单元格值粘贴到其他应用程序。

    ![复制选项](media/desktop-matrix-visual/power-bi-copy.png)

* 若要复制多个单元格，选择单元格范围或使用 CTRL 来选择一个或多个单元格。 复制将包括列标题和行标题。

    ![粘贴到 Excel](media/desktop-matrix-visual/power-bi-copy-selection.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>矩阵视觉对象的底纹和字体颜色
使用矩阵视觉对象，可以应用**条件格式设置**（颜色和底纹和数据条） 到矩阵中的单元格的背景可以将条件格式应用于文本和值本身。

若要应用条件格式设置，请选择矩阵可视化并打开**格式**窗格。 展开**条件格式设置**卡和**背景色**，**字体颜色**，或者**数据条**，将滑块移至**上**。 打开其中一个选项显示为链接*高级控件*，它允许你自定义的颜色和颜色格式设置的值。
  
  ![格式窗格，其中显示数据条控件](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

选择*高级控件*显示一个对话框，从中可以进行调整。 此示例中显示的对话框**数据条**。

![数据条窗格](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>后续步骤

[Power BI 中的散点图和气泡图](power-bi-visualization-scatter.md)

[Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)
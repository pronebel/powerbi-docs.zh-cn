---
title: 教程：在 Power BI Desktop 中创建你自己的度量值
description: 教程：在 Power BI Desktop 中创建你自己的度量值
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 8cfa3190acd4ef2ae2e1123f22d8f6221147afb1
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "34456079"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>教程：在 Power BI Desktop 中创建你自己的度量值
通过使用度量值，可以在 Power BI Desktop 中创建某些功能强大的数据分析解决方案。 度量值可在你与报表进行交互时帮助对数据执行计算。 本教程将引导你了解度量值并在 Power BI Desktop 中创建自己的基本度量值。

### <a name="prerequisites"></a>先决条件
- 本教程面向已熟悉使用 Power BI Desktop 创建更高级的模型的 Power BI 用户。 你应该已经熟悉使用“获取数据”和“查询编辑器”来导出数据、使用多个相关表和向报表画布添加字段。 如果刚开始使用 Power BI Desktop，请务必查看 [Power BI Desktop 入门](desktop-getting-started.md)。
  
- 下载 [Power BI Desktop 的 Contoso 销售示例](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip)文件，其中包含来自虚构公司 Contoso,inc. 的线上销售数据。因为该数据是从数据库导入的，用户将无法连接到数据源或在“查询编辑器”中查看。 在你自己的计算机上提取该文件，然后在 Power BI Desktop 中打开它。

## <a name="understand-measures"></a>了解度量值

通常会自动为用户创建度量值。 在 Contoso 销售示例文件中，在“字段”框的“Sales”表中，选中“SalesAmount”字段旁边的复选框，或将“SalesAmount”拖动到报表画布上。 随即将出现新列图表可视化效果，显示“Sales”表的“SalesAmount”列中所有值的总和。

![SalesAmount 图表](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

在“字段”框内，任何带有 sigma 图标 ![sigma 图标](media/desktop-tutorial-create-measures/meastut_sigma.png) 的字段都为数值字段，其值都可以进行聚合。 当 Power BI Desktop 检测到数字类型数据列时，它不会直接显示包含 200 万行 SalesAmount 值的表，而是自动创建度量值来计算聚合数据。 求和是数字类型数据的默认聚合方式，但可以轻松应用不同类型的聚合方式，如平均值或计数。 理解聚合是了解度量值的基础，因为每个度量值都将执行某种类型的聚合操作。 

要将图表聚合更改为平均值，在“可视化效果”窗格的“值”区域中，单击“SalesAmount”旁边的向下箭头，并选择“平均值”。 “SalesAmount”字段中的可视化效果将更改为所有销售值的平均值。

![SalesAmount 平均值图表](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

可以根据想要的结果来更改聚合的类型，但并非所有类型的聚合都能应用于所有数字类型数据。 例如，对于“SalesAmount”字段，总和和平均值是有意义的。 最小值和最大值也有它们的意义。 但是，计数对于“SalesAmount”字段则没有太大实际意义，因为虽然它的值是数值，但它们实际上代表的是货币。

度量值计算结果会随用户与报表的交互而发生变化。 例如，将“RegionCountryName”字段从“Geography”表拖动到图表，则会显示每个国家/地区的平均销售额。

![按国家/地区划分的销售额](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

由于与报表进行交互而导致度量值更改时，也会影响度量值的上下文。 每当与报表可视化效果交互时，都会改变度量值计算和显示其结果所在的上下文。

## <a name="create-and-use-your-own-measures"></a>创建和使用自己的度量值

在大多数情况下，Power BI 会根据所选择的字段和聚合的类型自动计算和返回值，但在某些情况下，你可能想要创建自己的度量值来执行更复杂的独特计算。 使用 Power BI Desktop，可以创建自己的具有数据分析表达式 (DAX) 公式语言的度量值。 

DAX 公式使用许多与 Excel 公式相同的函数、运算符和语法。 但是，DAX 函数用于在你与报表进行交互时处理关系数据，并执行更动态的计算。 超过 200 个 DAX 函数可以执行任何计算，从总和和平均值的简单聚合到更复杂的统计和筛选函数。 有许多资源可帮助你详细了解 DAX。 完成本教程后，请务必参阅 [Power BI Desktop 中的 DAX 基础知识](desktop-quickstart-learn-dax-basics.md)。

在创建你自己的度量值时，它会被添加到所选表的“字段”列表，并被称为“模型”度量值。 模型度量的一些优点包括：可以对其任意命名，使它们更容易识别；可以将它们用作其他 DAX 表达式中的参数；并且可以让它们快速地执行复杂的计算。

>[!TIP]
>从 Power BI Desktop 2018 年 2 月发行版开始，许多常见计算都可用作快速度量，它根据对话框中的输入内容编写 DAX 公式。 这些功能强大的快速计算对于学习 DAX 或发布你自己自定义的度量值也很有帮助。 若要创建或浏览快速度量，请在表的“更多选项”列表中或功能区“主页”选项卡的“计算”下选择“新建快速度量”。 请参阅[使用快速度量](desktop-quick-measures.md)，详细了解如何创建和使用快速度量。

### <a name="create-a-measure"></a>创建度量值

用户想要通过减去总销售额的折扣和收益来分析净销售额。 无论可视化效果中存在哪些上下文，都需要一个度量值，用于从 SalesAmount 总和中减去 DiscountAmount 和 ReturnAmount 的总和。 “字段”列表中没有“Net Sales”字段，但可以使用构建块创建度量值来计算净销售额。 

1.  在“字段”框中右键单击“Sales”表，或将鼠标悬停在该表上方并选择“更多选项”省略号 (...)，然后选择“新建度量值”。 这会将新建度量值保存在“Sales”表中，使其更易于查找。
    
    ![新建度量值](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    此外，还可以通过选择 Power BI Desktop 功能区“主页”选项卡上“计算”组中的“新建度量值”来创建新的度量值。
    
    ![从功能区新建度量值](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >从功能区创建度量值时，它可以在任何一个表中创建，但如果在计划使用它的位置创建它，则会更容易找到。 在这种情况下，首先选择“Sales”表，以使其处于活动状态，然后选择“新建度量值”。 
    
    公式栏出现在报表画布顶部，可以在此重命名度量值并输入一个 DAX 公式。
    
    ![公式栏](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
2.  默认情况下，新度量值的名称就是“度量值”。 如果不进行重命名，其他新度量值将被命名为“度量值 2”、“度量值 3”，依此类推。 如果你希望你的度量值更易于识别，请在公式栏中突出显示“度量值”，然后键入“Net Sales”。
    
3.  现在可以开始输入公式。 在等号后，开始键入“Sum”。 在键入时会出现一个下拉建议列表，其中显示以你键入的字母开头的所有 DAX 函数。 如有必要，向下滚动并选择列表中的“SUM”，然后按 Enter。
    
    ![选择 SUM](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    将会出现一个左括号和另一个建议下拉列表，其中包括可以传递到 SUM 函数的所有可用的列。
    
    ![选择列](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    表达式将始终出现在左括号和右括号之间。 你的表达式将包含一个单独的参数以传递给 SUM 函数：“SalesAmount”列。 开始键入“SalesAmount”，直到只有一个值留在列表中：Sales(SalesAmount)。 前面为表名称的列名称被称为列的“完全限定的名称”。 完全限定的列名称会使公式更易于读取。 
    
    ![选择 SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
4. 选择“Sales[SalesAmount]”，再键入右括号。
    
    > [!TIP]
    > 语法错误通常由缺少或错放右括号导致。
    
    
    
5.  去除其他两个列：
    1. 在第一个表达式的右括号后，依次键入一个空格、减号运算符 (-) 和另一个空格。 
    2. 输入另一个 SUM 函数，然后开始键入“DiscountAmount”，直到可以选择”Sales[DiscountAmount]”列作为参数。 添加右括号。 
    3. 依次键入一个空格、另一个减号运算符、空格、另一个以 Sales[ReturnAmount] 作为参数的 SUM 函数和右括号。
    
    ![完成公式](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
6.  按 Enter 或单击公式栏中的复选标记完成并验证公式。 经验证后的度量值已准备好在“Sales”表的“字段”列表中使用。 
    
    ![“字段”列表中的度量值](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
如果遇到用于输入公式的空间不足，或者希望它位于单独的行上，请选择公式栏右侧的向下 V 形图标以展开更多空间。

![公式 V 形图标](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

可以通过按 Alt-Enter 将不同行上的公式分成若干部分，或使用 Tab 空出位置。

![展开的公式](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>在报表中使用度量值
现在可以将“Net Sales”度量值添加到报表画布上，并根据添加到报表中的任何其他字段来计算净销售额。 按国家/地区查看净销售额：

1. 从“Sales”表中选择“Net Sales”度量值或将其拖动到报表画布。
    
2. 从“Geography”表中选择“RegionCountryName”字段，或将其拖到图表中。
    
    ![按国家/地区划分的净销售额](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
若要查看按国家/地区划分的净销售额和总销售额之间的差异，请选择“SalesAmount”字段或将其拖动到图表中。 

![按国家/地区划分的销售额和净销售额](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

图表现在使用两个度量值：已自动求和的 SalesAmount，和你创建的 Net Sales 度量值。 每个度量值在另一个字段 RegionCountryName 的上下文中进行计算。
    
### <a name="use-your-measure-with-a-slicer"></a>将度量值用于切片器

可以添加一个切片器，以便按日历年份进一步筛选净销售额和销售额。
    
1.  单击图表旁的空白区域，然后在“可视化效果”中，选择“表”可视化效果。 这会在报表画布中创建一个空白的表可视化效果。
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
2.  将“Year”字段从“Calendar”表拖动到新的空白表可视化效果。 因为“Year”是数值字段，Power BI Desktop 会对其值进行求和，但作为聚合没有多大意义。 
    
    ![年聚合](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3.  在“可视化效果”窗格中的“值”中，选择“Year”旁边的向下箭头，然后选择“不汇总”。 表现在列出了各个年份。
    
    ![不汇总](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  在“可视化效果”窗格中选择“切片器”图标，将表转换为切片器。

    ![更改为切片器](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  选择“Year”切片器中的任意值，以相应地筛选“按国家/地区划分的净销售额和销售额”图表。 Net Sales 和 SalesAmount 度量值会重新计算，并在所选“Year”字段的上下文中显示结果。 
    
    ![按年份切分的图表](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>在另一个度量值中使用度量值

如果想要知道哪些产品售出的每单位的净销售额最高，需要一个度量值，将净销售额除以销售单位的数量。 可以创建一个新的度量值，将 Net Sales 度量值的结果除以 Sales[SalesQuantity] 的总和。

1.  在“Sales”表中创建名为“Net Sales per Unit”的新度量值。
    
2.  在公式栏中，开始键入“Net Sales”。 建议列表将显示可以添加的内容。 选择 **[Net Sales]**。
    
    ![使用 Net Sales 的公式](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    此外，还可以参考度量值，键入一个左方括号 (**[**) 即可。 建议列表只显示添加到公式的度量值。
    
    ![括号仅显示度量值](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  依次输入一个空格、除号运算符 (/)、另一个空格、SUM 函数，然后键入“Quantity”。 建议列表将显示名称中包含 Quantity 的所有列。 选择“Sales [SalesQuantity]”、键入右括号，并按 ENTER 或选择复选标记来验证公式。 该公式应如下所示：
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
4. 从“Sales”表中选择“Net Sales per Unit”度量值，或将其拖到报表画布的空白区域。 图表显示了所有已售产品每单位的净销售额，但这并未提供多少有用信息。 
    
    ![每单位总体净销售额](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
5. 若要显示不同外观，将图表可视化效果类型更改为“树状图”。
    
    ![更改为树状图](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. 选择“Product Category”字段，或将其拖到树状图或“可视化效果”窗格中的“Group”字段。 现在就获得了一些有用信息！
    
    ![依据 Product Category 的树状图](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. 尝试删除“ProductCategory”字段，并将“ProductName”字段拖到图表中。 
    
    ![依据 Product Name 的树状图](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
好了，我们现在只是热身而已，但不得不承认，这真的很酷！ 体验以其他方式进行筛选可视化效果并设置其格式。

## <a name="what-youve-learned"></a>已了解的内容
度量值提供了许多功能，让用户能够从数据中获得想要的见解。 你已了解如何使用公式栏来创建度量值，以最具意义的方式为它们命名，并使用 DAX 建议列表找到并选择正确的公式元素。 本文还介绍了上下文，其中度量值中的计算结果会根据其他字段或公式中的其他表达式而发生更改。

## <a name="next-steps"></a>后续步骤
- 若要了解有关 Power BI Desktop 快速度量的详细信息（它为你提供了许多常见的度量值计算方法），请参阅[使用快速度量轻松执行常见的高效计算](desktop-quick-measures.md)。
  
- 如果想要深入了解 DAX 公式和创建更高级的度量值，请参阅 [Power BI Desktop 中的 DAX 基础知识](desktop-quickstart-learn-dax-basics.md)。 本文重点在于介绍 DAX 中的基本概念，如语法、函数和对上下文的透彻理解。
  
- 请务必将[数据分析表达式 (DAX) 参考](https://msdn.microsoft.com/library/gg413422.aspx)添加到收藏夹。 你可以在这里找到有关 DAX 语法、运算符和 200 多个 DAX 函数的详细信息。


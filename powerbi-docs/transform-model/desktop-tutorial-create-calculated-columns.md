---
title: 教程：创建 Power BI Desktop 中的计算列
description: 教程：创建 Power BI Desktop 中的计算列
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/26/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 858ecc07deabf5b91295220c2b92791b998ecf3a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349232"
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>教程：创建 Power BI Desktop 中的计算列

有时，当前分析的数据不包含获取期望结果所需的特定字段。 这就是计算列  的有用之处。 计算列使用数据分析表达式 (DAX) 公式来定义列值，可执行从组合几个不同列中的文本值到通过其他值来计算数值中涉及的任何操作。 例如，假设你的数据中含有“城市”和“州”两个字段，但你想要使用单一“位置”字段来同时含这两项内容，如“迈阿密，佛罗里达州”。    这正符合计算列的用途。

计算列类似于[度量值](desktop-tutorial-create-measures.md)，因为二者都基于 DAX 公式，但它们的区别在于使用方式。 通常会在可视化效果的“值”  区域中使用度量值，以基于其他字段计算结果。 可以将计算列用作可视化效果的行、轴、图例和组区域中的新字段。 

本教程将指导你了解和创建一些计算列，并在 Power BI Desktop 的报表可视化效果中使用它们。

## <a name="prerequisites"></a>必备组件

- 本教程面向已熟悉使用 Power BI Desktop 创建更高级的模型的 Power BI 用户。 应该已经了解如何使用“获取数据”和“Power Query 编辑器”来导出数据、使用多个相关表和向报表画布添加字段。 如果刚开始使用 Power BI Desktop，请务必查看 [Power BI Desktop 入门](../fundamentals/desktop-getting-started.md)。
  
- 本教程使用 [Power BI Desktop 的 Contoso 销售示例](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip)，与[在 Power BI Desktop 中创建你自己的度量值](desktop-tutorial-create-measures.md)教程中所用的示例相同。 这些来自虚构公司 Contoso,inc. 的销售数据从数据库导入，因此你将无法连接到数据源或在 Power Query 编辑器中查看。 请在你自己的计算机上下载并提取该文件，然后在 Power BI Desktop 中打开它。

## <a name="create-a-calculated-column-with-values-from-related-tables"></a>使用相关表中的值创建计算列

在销售报表中，你想要在一个单值内同时展示产品类别和子类别，如“手机 – 附件”、“手机 – 智能手机和 PDA”等等。 “字段”  列表中没有任何字段会提供该数据，但有一个“ProductCategory”  字段和“ProductSubcategory”  字段，每个字段都位于它自己的表中。 可以创建计算列以合并这两个列中的值。 DAX 公式可以利用已有模型的完整功能，包括使用不同的表之间已存在的关联关系。

 ![“字段”列表中的列](media/desktop-tutorial-create-calculated-columns/create1.png)

1. 若要在“ProductSubcategory”表中创建新列，请在“字段”窗格中的“ProductSubcategory”旁边右键单击或选择省略号“…”，然后从菜单中选择“新建列”      。

   ![新建列](media/desktop-tutorial-create-calculated-columns/create2.png)

   在选择“新建列”时，“公式栏”将出现在报表画布顶部，可以在此命名列并输入一个 DAX 公式   。

   ![公式栏](media/desktop-tutorial-create-calculated-columns/create3.png)

2. 默认情况下，新计算列命名为“列”  。 如果不进行重命名，其他新列将命名为“列 2”、“列 3”，依此类推   。 你希望列更易于识别，因此鉴于“列”名称已在公式栏中突出显示，可以通过键入“ProductFullCategory”来重命名，然后键入等号 ( **)**  **=** 。

3. 你希望新列中的值以“ProductCategory”字段中的名称开始  。 由于此列在不同但相关的表中，因此可以使用 [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) 函数来帮助获得它。

   在等号后键入“r”  。 下拉建议列表显示了以字母 R 开头的所有 DAX 函数。选中每个函数时都将显示其效果说明。 键入时，建议列表会更接近你所需的函数。 选择“RELATED”  ，然后按 Enter  。

   ![选择“RELATED”](media/desktop-tutorial-create-calculated-columns/create4.png)

   将出现一个左括号，以及另一个可传递给 RELATED 函数的相关列的建议清单，其中包含有关预期参数的说明和详细信息。

   ![选择“ProductCategory”](media/desktop-tutorial-create-calculated-columns/create5.png)

4. 你想要“ProductCategory”  表中的“ProductCategory”  列。 选择“ProductCategory [ProductCategory]”  ，按 Enter  ，然后键入右括号。

    > [!TIP]
    > 尽管有时 Power BI Desktop 会自动添加右括号，但语法错误通常由缺少或错放右括号导致。

5. 若要使用短划线和空格来分隔新值中的“ProductCategories”和“ProductSubcategories”，请在第一个表达式的右括号后，键入一个空格、& 号 ( **)、双引号 (")、空格、短划线 (** )、另一个空格、另一个双引号和另一个 & 号  **&**  **-** 。 该公式现在应如下所示：

    `ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &`

    > [!TIP]
    > 如需更多空间，请选择公式栏右侧的向下 V 形图标，展开公式编辑器。 在编辑器中，按 Alt + Enter  键，向下移动一行，并按 Tab  键来移动内容。

6. 输入一个左括号 ([  )，然后选择“[ProductSubcategory]”  列，从而完成公式。 

    ![选择“ProductSubcategory”](media/desktop-tutorial-create-calculated-columns/create6.png)

    不需要使用另一个 RELATED 函数在第二个表达式中调用 ProductSubcategory 表，因为你将在此表中创建计算列  。 可以输入带表名前缀（完全限定的）或不带表名前缀（非限定的）的 [ProductSubcategory]  。

7. 按 Enter  键或选择公式栏中的选中标记以完成该公式。 该公式将生效，并且“ProductFullCategory”列名将出现在“字段”窗格的“ProductSubcategory”表中    。

   ![完成的 ProductFullCategory 列](media/desktop-tutorial-create-calculated-columns/create7.png)

    >[!NOTE]
    >在 Power BI Desktop 中，计算列在“字段”窗格中由特殊图标进行标记，显示它们包含公式  。 在 PowerBI 服务（Power BI 网站）中，由于根本无法更改公式，所以计算列不会附带图标。

## <a name="use-your-new-column-in-a-report"></a>在报表中使用新列

现在可以使用新的“ProductFullCategory”列来依据“ProductFullCategory”查看“SalesAmount”    。

1. 从“ProductSubcategory”表选择“ProductFullCategory”列或将其拖放到报表画布，以创建一个显示所有“ProductFullCategory”名称的表    。

   ![ProductFullCategory 表](media/desktop-tutorial-create-calculated-columns/vis1.png)

2. 从“销售”表选择“SalesAmount”字段或将其拖动到表上，以显示每个“产品完整类别”的销售额     。

   ![按 ProductFullCategory 排列的 SalesAmount 表](media/desktop-tutorial-create-calculated-columns/vis2.png)

## <a name="create-a-calculated-column-that-uses-an-if-function"></a>创建使用 IF 函数的计算列

Contoso 销售示例包括针对活跃商店和非活跃商店的销售数据。 通过创建一个“Active StoreName”字段，可以确保报表中活跃商店的销售额与非活跃商店的销售额明确分离  。 在新的“Active StoreName”计算列，每个活跃商店将以商店的完整名称显示，而非活跃商店的销售额将被组合到名为“非活跃”的行项目中   。

幸运的是，“商店”表中有一个名为“状态”的列，其中值“开”用于活跃商店，而“关”则用于非活跃商店，我们可以使用该列创建新“Active StoreName”列的值    。 DAX 公式将使用逻辑 [IF](https://msdn.microsoft.com/library/ee634824.aspx) 函数来测试每个商店的“状态”，并根据结果返回特定值  。 如果商店状态为“开”，公式将返回商店名称  。 如果为“关”，则公式将为 Active StoreName 分配“非活跃”  。

1. 在“商店”  表中新建计算列，并在公式栏中将其命名为“Active StoreName”  。

2. 在 **=** 号后，开始键入“IF”  。 建议列表将显示可以添加的内容。 选择 **IF**。

    ![选择“IF”](media/desktop-tutorial-create-calculated-columns/if1.png)

3. “IF”第一个参数是商店状态是否为“开”的逻辑测试   。 键入一个左括号“[”，它会从“商店”表中列出列，然后选择“[Status]”    。

    ![选择“Status”](media/desktop-tutorial-create-calculated-columns/if2.png)

4. 在“[Status]”  后，键入“=’On’”  ，然后键入逗号 (,  ) 结束参数。 工具提示建议添加一个值以在结果为 TRUE 时返回。

    ![添加 TRUE 值](media/desktop-tutorial-create-calculated-columns/if3.png)

5. 如果商店处于“开”状态，则需要显示商店名称。 键入一个左方括号 ([  )，选择“[StoreName]”  列，然后再键入一个逗号。 现在，工具提示将指示你添加一个值以在结果为 FALSE 时返回。

    ![添加 FALSE 值](media/desktop-tutorial-create-calculated-columns/if4.png)

6. 如果希望值为“非活跃”，则键入“非活跃”，然后通过按“Enter”或在编辑栏中选择复选标记完成该公式   。 公式将生效，并且新列名称将出现在“字段”窗格的“商店”表中   。

    ![Active StoreNam 列](media/desktop-tutorial-create-calculated-columns/if5.png)

7. 和其他任何字段一样，可以在可视化效果中使用新的 Active StoreName 列  。 若要显示按“Active StoreName”排列的“SalesAmounts”，选择“Active StoreName”字段或将其拖至报表画布，然后选择“SalesAmount”字段或将其拖至表中     。 在此表中，活跃商店单独按名称显示，而非活跃商店以“非活跃”  组合到末尾。

    ![按 Active StoreName 排列的 SalesAmount 表](media/desktop-tutorial-create-calculated-columns/if6.png)

## <a name="what-youve-learned"></a>已了解的内容

计算列可丰富数据，提供更方便的见解。 你已了解如何在“字段”窗格和公式栏中创建计算列、如何使用建议列表和工具提示来帮助构造公式、如何使用适当的参数调用诸如 RELATED 和 IF 之类的 DAX 函数，以及如何在报表可视化效果中使用计算列  。

## <a name="next-steps"></a>后续步骤

如果想要深入了解 DAX 公式和使用更高级的公式创建计算列，请参阅 [Power BI Desktop 中的 DAX 基本信息](desktop-quickstart-learn-dax-basics.md)。 本文重点在于介绍 DAX 中的基本概念，如语法、函数和对上下文的透彻理解。

请务必将[数据分析表达式 (DAX) 参考](https://msdn.microsoft.com/library/gg413422.aspx)添加到收藏夹。 你可以在这里找到有关 DAX 语法、运算符和 200 多个 DAX 函数的详细信息。

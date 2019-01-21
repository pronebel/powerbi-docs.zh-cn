---
title: 调整和合并来自多个源的数据
description: 在本教程中，将了解如何在 Power BI Desktop 中调整和合并数据
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: f39f5ae569c757072a55647becb5697c881abbe2
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285660"
---
# <a name="tutorial-shape-and-combine-data-in-power-bi-desktop"></a>教程：在 Power BI Desktop 中调整和合并数据

借助 **Power BI Desktop**，可连接到多个不同类型的数据源，然后调整数据以满足你的需求，使你能够创建可与其他人共享的视觉对象报表。 *调整* 意味着转换数据 - 如重命名列或表格、将文本更改为数字、删除行、将第一行设为标题等等。 合并数据意味着连接到两个或多个数据源，根据需要调整它们，然后将其合并到一个有用的查询中。

在本教程中，将了解如何：

* 使用查询编辑器调整数据
* 连接到数据源
* 连接到其他数据源
* 合并这些数据源，以及创建要在报表中使用的数据模型

本教程演示了如何使用 Power BI Desktop 来调整查询，其中突出显示了一些最常见的任务。 有关此处所用查询的更多详细信息，包括如何从头开始创建查询，请参阅 [Power BI Desktop 入门](desktop-getting-started.md)。

有必要知道 Power BI Desktop 中的**查询编辑器**大量地使用右键单击菜单和功能区。 大部分可在**转换**功能区选择的内容也可通过右键单击项目（如某列）并从所显示的菜单中进行选择。

## <a name="shape-data"></a>调整数据
如果在查询编辑器中调整数据，你将在查询编辑器加载并呈现数据时提供分步说明（查询编辑器将为你执行此操作）以调整数据。 原始数据源不受影响，将仅调整或 *整理* 这一特定的数据视图。

查询编辑器会记录你指定的步骤（如重命名表格、转换数据类型或删除列），且每当此查询连接到数据源时，都会执行这些步骤，因此数据将始终按你指定的方式进行调整。 每当你使用 Power BI Desktop 的查询编辑器功能，或任何人使用你的共享查询（如在 **Power BI** 服务上）时，都会出现此过程。 这些步骤在“应用的步骤”下的“查询设置”窗格中按顺序捕获。

下图显示已调整查询的**查询设置**窗格，我们将于接下来几个段落中逐一说明每个步骤。

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished2.png)

借助 [Power BI Desktop 入门](desktop-getting-started.md)中的停用数据（通过连接到 Web 数据源找到），开始调整此数据以满足我们的需求。

首先，添加一个自定义列，在所有数据具有同等因素的前提下计算排名，并将其与现有列“排名”进行比较。  以下为“添加列”功能区，其中箭头指向“自定义列”按钮，可通过此按钮添加自定义列。

![](media/desktop-shape-and-combine-data/shapecombine_customcolumn.png)

在“自定义列”对话框中，请在“新列名”中输入“新排名”，然后在“自定义列公式”中输入以下内容：

    ([Cost of living] + [Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 8

确保状态消息显示为“未检测到任何语法错误。” 然后单击“确定”。

![](media/desktop-shape-and-combine-data/shapecombine_customcolumndialog.png)

为了保持列数据的一致性，请将新列值转换为整数。 只需右键单击列标题，然后选择“更改类型”\>“整数”对其加以更改。 

如需选择多列，请先选择一列然后按住 SHIFT，再选择其他相邻列，然后右键单击列标题以更改所有选中的列。 也可以使用 **CTRL** 键来选择不相邻的列。

![](media/desktop-shape-and-combine-data/shapecombine_changetype2.png)

还可以从“转换”功能区转换列数据类型。 **转换**功能区显示如下，其中箭头指向**数据类型**按钮，可用于将当前数据类型转换成其他数据类型。

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

请注意，在**查询设置**中，**应用的步骤**反映了应用到数据的所有调整步骤。 如果要删除调整过程中的任意步骤，只需选择步骤左侧的 **X**。 在下图中， **应用的步骤** 反映了至今为止使用的步骤：连接到网页（ **源** ）；选择表格（ **导航** ）；加载表格时，查询编辑器将基于文本的数字列从 *文本* 自动更改为 *整数* （ **更改类型** ）。 最后两个步骤演示了之前的“已添加自定义”和“已更改类型 1”操作。 

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly2.png)

我们需要先执行一些更改以将查询中的数据置于所需位置，才可以使用此查询：

* 通过删除列来调整排名 - 我们已决定结果中的“生活成本”是一个非因素。 删除此列后，我们发现数据保持不变的问题，尽管可以使用 Power BI Desktop 轻松修复此问题，且这样做演示了查询中“应用的步骤”的一个很酷的功能。
* 修复一些错误 - 由于我们删除了一个列，因此需要重新调整“新排名”列中的计算。 这涉及公式更改。
* 对数据进行排序 - 基于“新排名”和“排名”列。 
* 替换数据 - 我们将重点介绍如何替换特定值以及插入“应用的步骤”的要求。
* 更改表格名称 - “表格 0”不是有用的描述符，但更改它很简单。

若要删除“生活成本”列，只需选中此列并依次选择功能区中的“开始”选项卡和“删除列”，如下图所示。

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnscostofliving.png)

请注意，新排名值未发生更改；其原因在于步骤的顺序。 由于查询编辑器按顺序记录步骤，但各个步骤相互独立，因此可在序列中上下移动每个**所应用步骤**。 只需右键单击任意步骤，查询编辑器就会提供一个菜单，让你执行下述操作：重命名、删除、删除到末尾（删除当前步骤及所有后续步骤）、上移或下移。 请继续，并将最后一步“已删除列”上移至“已添加自定义”步骤的正上方。

![](media/desktop-shape-and-combine-data/shapecombine_movestep.png)

接下来，选择“已添加自定义”步骤。 请注意，此数据现在显示一个待处理的“错误”。 

![](media/desktop-shape-and-combine-data/shapecombine_error2.png)

可采用以下几种方法来获取每个错误的详细信息。 可选择单元格（无需单击**错误**一词），或直接单击**错误**这个词。 如果选择单元格而 *不* 在 **错误** 字词上直接单击，则查询编辑器在窗口底部显示错误信息。

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo2.png)

如果直接单击 *错误* 这个词，则查询将在 **查询设置** 中创建 **所应用步骤** ，并显示错误的相关信息。 我们不希望继续，所以选择“取消”。

若要修复错误，请选择“新排名”列，然后打开“视图”功能区并选择“公式栏”复选框来显示列的数据公式。 

![](media/desktop-shape-and-combine-data/shapecombine_formulabar.png)

现在可以删除“生活成本”参数并减少除数，方法是将公式更改为以下公式： 

    Table.AddColumn(#"Removed Columns", "New Rank", each ([Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 7)

选择公式框左侧的绿色复选标记或按 Enter，数据应替换为修改后的值，且“已添加自定义”步骤现应完成且未出错。

> [!NOTE]
> 还可以删除错误（使用功能区或右键单击菜单），这将删除具有错误的任意行。 这种情况下，它不会删除数据中的所有行，而且我们也不想这样做，我们想要所有数据，并希望将其保留在表格中。

现在需要基于“新排名”列对数据进行排序。 首先选择最后一个应用的步骤“已更改类型 1”以访问最新数据。 然后，选择“新排名”列标题旁边的下拉列表，并选择“升序排序”。

![](media/desktop-shape-and-combine-data/shapecombine_sort.png)

请注意，数据现在会根据“新排名”进行排序。  但是，如果查看“排名”列，将注意到在“新排名”值为一个并列值的情况下，数据未正确排序。 若要解决此问题，请选择“新排名”列并将“公式栏”中的公式更改为以下公式：

    = Table.Sort(#"Changed Type1",{{"New Rank", Order.Ascending},{"Rank", Order.Ascending}})

选择公式框左侧的绿色复选标记或按 Enter，行现在应同时根据“新排名”和“排名”进行排序。

此外，还可在列表的任何位置选择**所应用步骤**，然后继续在序列中此点处调整数据。 查询编辑器将在当前选定的**所应用步骤**后直接自动插入一个新步骤。 我们来试一试。

首先，选择“应用的步骤”，然后添加自定义列；这将是“已删除列”步骤。 我们将在此替换亚利桑那州的“天气”排名值。 右键单击包含亚利桑那州“天气”排名的相应单元格，然后从显示的菜单中选择“替换值...”。 记下当前选择的“应用的步骤”（“已添加自定义”步骤之前的步骤）。

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues2.png)

因为我们要插入步骤，所以查询编辑器提醒我们这样做的危险 - 后续步骤可能导致查询中断。 我们需要小心谨慎、深思熟虑！ 由于这是一个教程，而我们要重点介绍查询编辑器的一项炫酷功能以展示如何创建、删除、插入和记录步骤，所以我们将继续操作并选择**插入**。

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

将值更改为 51，随即会替换表示亚利桑那州的数据。 创建新的所应用步骤时，查询编辑器会根据操作对其命名 - 本例中，命名为**替换值**。 当查询中具有多个名称相同的步骤时，查询编辑器将对每个后续的**所应用步骤**添加一个编号（按顺序）以对其进行区分。

现在选择最后一个“应用的步骤”，“已排序行”，会发现有关亚利桑那州的新排名的数据已发生变化。  这是因为我们在“已添加自定义”步骤前，在正确的位置插入了“已替换值”步骤。

这有点复杂，但它很好地列举了查询编辑器是多么的功能强大、灵活通用。

最后，我们想将此表格的名称更改为描述性内容。 在开始创建报表时，具有描述性的表格名称尤其有用，特别是当连接到多个数据源，且它们均在**报表**视图的**字段**窗格中列出时。

可轻松更改表格名称：在**查询设置**的**属性**下，只需键入新的表格名称（如下图所示），然后点击 **Enter**。 让我们将此表命名为 *RetirementStats* 。

![](media/desktop-shape-and-combine-data/shapecombine_renametable2.png)

好了，我们已按所需的范围调整了数据。 接下来，让我们连接到其他数据源，然后合并数据。

## <a name="combine-data"></a>合并数据
有关各州的那份数据很有趣，而且适用于生成其他分析工作和查询。 但是有一个问题：大多数数据使用两个字母的州名代码缩写，而不是该州的完整名称。 我们需要某种方式来建立州名及其缩写的关联。

我们很幸运：有另一个公共数据源可执行该项工作，但还需要进行相当多的调整，才能连接到我们的退休表。 以下是州名缩写的 Web 资源：

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

从查询编辑器的“开始”功能区中，选择“新源”\>“Web”，然后键入地址并选择“连接”，随后导航器会显示其在此网页上找到的信息。

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator2.png)

我们选择“代码和缩写...”，因为它包含所需数据，但它需要大量调整才能将表格中的数据削减到我们想要的数据。

> [!TIP]
> 是否有更快或更容易的方法完成以下步骤？ 是，我们可以创建两个表之间的关系并基于该关系调整数据。 以下步骤对了解表的用法仍非常有用，但需知道关系可以帮助你快速使用来自多个表的数据。
> 
> 

若要调整此数据，我们需要执行以下步骤：

* 删除顶行 - 它包含网页表格创建方式的结果，不是所需的行。 从**开始**功能区中，选择**减少行 \> 删除行 \> 删除前几行**。

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

将显示**删除前几行**窗口，让你执行要删除几行。

>[!NOTE]
>如果 Power BI 意外导入表标题作为数据表中的行，可以从“主页”选项卡，或者从功能区的“转换”选项卡选择“将第一行用作标题”，以便修复表。

* 删除底部的 26 行 - 它们全是地区，无需包含在内。 从**开始**功能区中，选择**减少行 \> 删除行 \> 删除后几行**。

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* 由于 RetirementStats 表没有针对华盛顿特区的信息，我们需要将其从列表中筛选去除。 选择“区域状态”列旁边的下拉箭头，然后清除**联邦特区**旁边的复选框。

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* 删除一些不必要的列 – 只需将州映射到其两个字母的官方缩写，因此可以删除下面的数据列：列 1、列 3、列 4，然后删除列 6 到列 11。 首先选择“Column1”，然后按住 CTRL 键并选择要删除的其他列（可由此选择多个不相邻的列）。 从功能区的“开始”选项卡上，选择**删除列 \> 删除列**。

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

>[!NOTE]
>此时非常适合指出，查询编辑器中已应用步骤的序列很重要，可能会影响数据调整方式。 同时也必须考虑一个步骤对另一个后续步骤可能会有什么影响；如果你从“所应用步骤”中删除一个步骤，则由于查询中步骤序列的影响，后续步骤可能不会按原本所期望的进行操作。

>[!NOTE]
>如果将查询编辑器窗口大小重设为宽度缩小，部分功能区项会进行简缩，以充分利用可视空间。 在增加查询编辑器窗口的宽度时，功能区项将展开以充分利用已增加的功能区区域。

* 重命名列，然后重命名表格本身 - 同样的，有几种方式可用于重命名列；首先选择此列，然后选择功能区上**转换**选项卡中的**重命名**，或者右键单击并从显示的菜单中选择**重命名…** 。 下图具有指向这两个选项的箭头；只需任选其一。

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

让我们将其重命名为 *州名* 和 *州代码* 。 若要重命名表格，只需在**查询设置**窗格的**名称**框内键入名称。 让我们将此表命名为 *StateCodes* 。

我们已按所需方式调整了 StateCodes 表，接下来将这两个表或查询合并成一个；由于当前具有的表格是应用到数据的查询的结果，因此它们通常称为 *查询* 。

有两种主要方法可合并查询 – *合并* 和 *追加* 。

当你有一列或多列要添加到另一个查询时，你可**合并**这些查询。 当你有其他列要添加到现有查询时，你可**追加**查询。

本例中，我们要合并查询。 若要开始，请从查询编辑器的左窗格中选择想要其他查询合并 *到* 的查询，本例中为 *RetirementStats* 。 然后从功能区的**开始**选项卡中，选择**合并 \> 合并查询**。

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

系统可能会提示你设置隐私级别，以确保对数据进行合并，且不包括或不传输无需传输的数据。

接下来将显示**合并**窗口，提示我们选择想要合并到所需表中的表格，然后选择要用于合并的匹配列。 从 *RetirementStats* 表（查询）中选择州，然后选择 *StateCodes* 查询（本例中很简单，因为仅有一个其他查询 - 在连接到多个数据源时，存在可从中选择的多个查询）。 在选择正确的匹配列时（*RetirementStats* 中的**州**，*StateCodes* 中的**州名**），**合并**窗口如下所示，且**确定**按钮已启用。

![](media/desktop-shape-and-combine-data/shapecombine_merge2.png)

在查询的结尾会创建 **NewColumn**，它是与现有查询合并的表（查询）内容。 来自合并查询的所有列均压缩到 **NewColumn** 中，但可选择**展开**数据表并包含所需的任意列。

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

若要展开合并的表格，并选择要包含的列，请选择“展开”图标（![展开](media/desktop-shape-and-combine-data/icon.png)）。 **展开**窗口随即出现。

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

在此示例中，我们只需要**州代码**列，因此仅选择此列，然后选择**确定**。 清除“使用原始列名作为前缀”复选框，因此无需或不想要此操作；如果保留选择它，则合并的列将命名为 **NewColumn.State Code**（原始列名，或者 **NewColumn** 后接一个点，再接要带入查询的列名）。

>[!NOTE]
>想尝试了解如何引入此 NewColumn 表吗？ 你可以试验一下，如果不喜欢结果，只需从**查询设置**窗格中**所应用步骤**列表删除该步骤，你的查询便会回到应用**展开**步骤之前的状态。 这就像是个自由重做的机会，你可以不限次数地任意执行，直到展开过程看起来是你要的方式为止。

我们现在有合并两个数据源的单一查询 （表格），其中每个数据源都已经过调整以符合我们的需求。 此查询可以作为许多其他相关数据连线的基础 – 例如任何州的住房成本统计数据、人口统计数据或工作机会。

若要应用更改和关闭查询编辑器，请从“主页”功能区选项卡中选择“关闭并应用”。转换后的数据集将在 Power BI Desktop 中显示，可随时用于创建报表。

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>后续步骤
Power BI Desktop 可用于执行多种操作。 有关其功能的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 的查询概述](desktop-query-overview.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [连接到 Power BI Desktop 中的数据](desktop-connect-to-data.md)
* [Power BI Desktop 中的常见查询任务](desktop-common-query-tasks.md)   


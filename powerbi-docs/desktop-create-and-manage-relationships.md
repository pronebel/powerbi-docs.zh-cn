---
title: 在 Power BI Desktop 中创建和管理关系
description: 在 Power BI Desktop 中创建和管理关系
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 017a1b9b326842c5bcc483f77e0be1fa884c0270
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578189"
---
# <a name="create-and-manage-relationships-in-power-bi-desktop"></a>在 Power BI Desktop 中创建和管理关系
导入多个表时，你很可能要使用所有这些表中的数据来执行一些分析。 为准确计算结果并在报表中显示正确信息，这些表格之间的关系是必需的。 Power BI Desktop 可轻松创建这些关系。 事实上，在大多数情况下你无需执行任何操作，自动检测功能将替你执行。 但在某些情况下，你可能需要自行创建关系，或者可能需要对关系进行一些更改。 无论哪种方法，都有必要了解 Power BI Desktop 中的关系及其创建和编辑方式。

## <a name="autodetect-during-load"></a>在加载期间自动检测
如果你同时查询两个或多个表格，则在加载数据时，Power BI Desktop 将尝试为你查找并创建关系。 将自动设置基数、交叉筛选方向和活动属性。 Power BI Desktop 查看表格中你正在查询的列名，以确定是否存在任何潜在关系。 若存在，则将自动创建这些关系。 如果 Power BI Desktop 无法颇有自信地确定存在匹配项，则不会自动创建关系。 你仍可使用“关系关系”对话框来创建或编辑关系。

## <a name="create-a-relationship-by-using-autodetect"></a>使用自动检测功能创建关系
在**开始**选项卡上，单击**管理关系** \> **自动检测**。

![](media/desktop-create-and-manage-relationships/automaticrelationship.gif)

## <a name="create-a-relationship-manually"></a>手动创建关系
1. 在**开始**选项卡上，单击**管理关系** \> **新建**。
2. 在**创建关系**对话框的第一个表格下拉列表中，选择一个表格，然后选择要在关系中使用的列。
3. 在第二个表格下拉列表中，选择另一个要在关系中使用额表格，再选择要使用的其他列，然后单击**确定**。

![](media/desktop-create-and-manage-relationships/manualrelationship2.gif)

默认情况下，Power BI Desktop 会自动配置新关系的基数（方向）、交叉筛选器方向和活动属性；但必要时，可对其进行更改。 若要了解更多信息，请参阅本文后面的“了解其他选项”部分。

请注意：如果为关系选择的表均没有唯一值，会显示一条错误：其中一列必须有唯一值。 关系中至少有一个表必须具有密钥值的不同的唯一列表，该列表是对所有关系数据库技术的常见要求。 

如果遇到此错误，可采用以下方式修复：

* 使用“删除重复行”创建具有唯一值的列。 此方法的缺点是删除重复行时信息会丢失，而通常重复行是有用的。
* 将包含不同密钥值列表的中间表添加到模型，该模型会链接到关系中的两个原始列。

有关详细信息，请参阅[博客文章](https://blogs.technet.microsoft.com/cansql/2016/12/19/relationships-in-power-bi-fixing-one-of-the-columns-must-have-unique-values-error-message/)，该文章对此进行了详细介绍。


## <a name="edit-a-relationship"></a>编辑关系
1. 在**开始**选项卡上，单击**管理关系**。
2. 在**管理关系**对话框中，选择关系，然后单击**编辑**。

## <a name="configure-additional-options"></a>配置其他选项
创建或编辑关系时，可配置其他选项。  默认情况下，会根据最佳估计自动配置其他选项。 基于列中的数据，每个关系的此类选项可能不同。

## <a name="cardinality"></a>基数
**多对一 (\*:1)** - 这是最常见的默认类型。 这意味着一个表中的列可具有一个值的多个实例，而另一个相关表（常称为查找表）仅具有一个值的一个实例。

**一对一 (1:1)** -这意味着一个表中的列仅具有特定值的一个实例，而另一个相关表也是如此。

有关何时更改基数的更多详细信息，请参阅本文后面的“了解其他选项”部分。

## <a name="cross-filter-direction"></a>交叉筛选器方向
**双向** - 这是最常见的默认方向。 这意味着为进行筛选，两个表均被视为如同是一个表。  这非常适用于其周围具有多个查找表的单个表。  例如，具有部门查找表的实际销售额表。  这通常称为星型架构配置（一个具有多个查找表的中心表）。但是，如果你的两个或更多表格也具有查找表（部分查找表共有），则“双向”设置不适合。  继续讲之前的示例，在本例中你还一个预算销售表，它记录了每个部门的目标预算。  并且，部门表格同时连接到标售表和预算表。  对于这种配置，请避免“双向”设置。

**单向** - 这意味着连接表中的筛选选项适用于将求值总和的表格。 如果你在 Excel 2013 或更早的数据模型中导入了 Power Pivot，则所有关系都将具有单个方向。 

有关何时更改交叉筛选器方向的更多详细信息，请参阅本文后面的“了解其他选项”部分。

## <a name="make-this-relationship-active"></a>使此关系可用
勾选后，这意味着此关系用作活动的默认关系。  如果两个表格之间存在多个关系，则 Power BI Desktop 可通过活动关系自动创建包含这两个表的可视化效果。

有关何时激活特定关系的更多详细信息，请参阅本文后面的“了解其他选项”部分。

## <a name="understanding-relationships"></a>了解关系
使用一种关系将两个表连接在一起之后，就可如同单个表一样使用两个表中的数据，从而无需担忧关系详细信息，也不必在导入前将这些表合并成单个表。  很多情况下，Power BI Desktop 可自动为你创建关系，因此甚至可能无需再自行创建这些关系。 但如果 Power BI Desktop 无法颇有自信地确定两个表之间存在关系，则不会自动创建关系。 在此情况下，将需要由你来创建关系。   

我们稍微来演示一下，以更好地向你展示关系如何在 Power BI Desktop 进行操作。

>[!TIP]
>用户可自行学完此课程。 将下方的 ProjectHours 表复制到 Excel 工作表中，选择全部单元格，然后单击**插入** \> **表格**。 在**创建表格**对话框中，只需单击**确定**即可。 然后在**表名**中，键入 **ProjectHours**。 对 CompanyProject 表执行相同的操作。 然后可在 Power BI Desktop 中使用**获取数据**来导入数据。 选择工作薄和表格作为数据源。

第一个表 (ProjectHours) 是记录了某位员工在特定项目上工作的小时数的工作单记录。  

**ProjectHours**

| **工作单** | **提交者** | **小时数** | **项目** | **提交日期** |
| ---:|:--- | ---:|:--- | ---:|
| 1001 |Brewer, Alan |22 |蓝色 |2013/1/1 |
| 1002 |Brewer, Alan |26 |红色 |2013/2/1 |
| 1003 |Ito, Shu |34 |黄色 |2012/12/4 |
| 1004 |Brewer, Alan |13 |橙色 |2012/1/2 |
| 1005 |Bowen, Eli |29 |紫色 |2013/10/1 |
| 1006 |Bento, Nuno |35 |绿色 |2013/2/1 |
| 1007 |Hamilton, David |10 |黄色 |2013/10/1 |
| 1008 |Han, Mu |28 |橙色 |2012/1/2 |
| 1009 |Ito, Shu |22 |紫色 |2013/2/1 |
| 1010 |Bowen, Eli |28 |绿色 |2013/10/1 |
| 1011 |Bowen, Eli |9 |蓝色 |2013/10/15 |

第二个表 (CompanyProject) 列举了具有所配优先级（A、B 或 C）的项目。 

**CompanyProject**

| **项目名称** | **优先级** |
| --- | --- |
| 蓝色 |A |
| 红色 |B |
| 绿色 |C |
| 黄色 |C |
| 紫色 |B |
| 橙色 |C |

请注意，每个表都具有一个项目列。 每个列的命名略有不同，但其值看起来相同。 这很重要，我们呆会儿将回到这一点。

我们向一个模型导入了两个表，接下来创建报表。 首先我们要获取的是由项目优先级提交的小时数，因此选择字段中的**优先级**和**小时数**。

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfiltersnorel.png)

如果在报表画布中查看表格，会看到每个项目的小时数均为 **256.00**，这也是总数。 显然这是错误的。 为什么？ 这是因为如果这两个表之间不存在关系，则不能由一个表中的值（CompanyProject 表中的优先级）切分另一个表中的值（ProjectHours 表中的小时数）来计算后者值的总数。

因此，让我们在这两个表之间创建一个关系。

还记得两个表中具有项目名称但其值看似相似的那些列吗？ 我们将要使用这两列来创建表格之间的关系。

为什么是这些列？ 嗯，如果查看 ProjectHours 中的项目列，可看到蓝色、红色、黄色、橙色等。 事实上，显示了多个具有相同值的行。 项目实际上具有多个颜色值。

如果查看 CompanyProject 表中的项目名称列，可看到每个项目仅具有一个颜色值。 这个表中的每个颜色值都是唯一的，这一点很重要，因为我们可在这两个表之间创建关系。 此情况下，可创建多对一的关系。 在多对一的关系中，一个表中至少有一个列必须包含唯一值。 某些关系具有一些其他选项，我们将稍后探讨这一点；但现在，让我们来为每个表创建一个项目列之间的关系。

### <a name="to-create-the-new-relationship"></a>若要创建新关系
1. 单击**管理关系**。
2. 在**管理关系**中，单击**新建**。 这将打开“创建关系”对话框，可在其中选择表格、列以及要用于关系的任意其他设置。
3. 在第一个表中，选择 **ProjectHours**，然后选择**项目**列。 这是关系中的多方。
4. 在第二个表中，选择 **CompanyProject**，然后选择**项目名称**列。 这是关系中的单方。  
5. 继续操作并单击**创建关系**和**管理关系**这两个对话框中的**确定**。

![](media/desktop-create-and-manage-relationships/candmrel_create_compproj.png)

为了完全展示，你实际上以复杂的方式创建了这一关系。 你其实只需单击“管理关系”对话框中的“自动检测”按钮。 事实上，如果两个列的名称相同，则在加载数据时，自动检测功能就已为你执行了此操作。 但，其中面临的挑战是什么呢？

现在，我们再来看一下报表画布中的表格。

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfilterswithrel.png)

它现在整体看起来好得多，不是吗？

按优先级汇总小时数时，Power BI Desktop 将查询 CompanyProject 查找表中唯一颜色值的每个实例，然后查询 CompanyProject 表中这些值的每个实例，最后计算每个唯一值的总和。

事实上，如果使用自动检测功能，则非常容易，可能甚至无需执行此操作。

## <a name="understanding-additional-options"></a>了解其他选项
使用自动检测功能或手动创建关系时，Power BI Desktop 将基于表格中的数据自动配置其他选项。 可在“创建/编辑关系”对话框的底部配置这些其他关系属性。

 ![](media/desktop-create-and-manage-relationships/candmrel_advancedoptions2.png)

正如我们所言，这些选项通常会自动设置，无需你的参与；但是，存在很多你可能想要自行配置这些选项的情况。

## <a name="future-updates-to-the-data-require-a-different-cardinality"></a>将来更新数据需要其他基数
通常，Power BI Desktop 可自动确定用于关系的最佳基数。  如果由于知道数据将在未来更改，而确实需要重写自动设置，则可在基数控件中将其选中。 我们来看一个需要选择其他基数的示例。

下方的 CompanyProjectPriority 表列出了所有公司项目及其优先级。 而 ProjectBudget 表是一组其预算已获批准的项目。

**ProjectBudget**

| **已批准的项目** | **预算分配** | **分配日期** |
|:--- | ---:| ---:|
| 蓝色 |40,000 |2012/12/1 |
| 红色 |100,000 |2012/12/1 |
| 绿色 |50,000 |2012/12/1 |

**CompanyProjectPriority**

| **项目** | **优先级** |
| --- | --- |
| 蓝色 |A |
| 红色 |B |
| 绿色 |C |
| 黄色 |C |
| 紫色 |B |
| 橙色 |C |

如果在 CompanyProjectPriority 的项目列和 ProjectBudget 表的获准项目列之间创建一个关系，如下所示：

 ![](media/desktop-create-and-manage-relationships/candmrel_create_compproj_appproj2.png)

基数将自动设置为一对一 (1:1)，交叉筛选设为“双向”（如图所示）。  这是因为对于 Power BI Desktop，这两个表的最佳组合如下所示：

| **项目** | **优先级** | **预算分配** | **分配日期** |
|:--- | --- | ---:| ---:|
| 蓝色 |A |40,000 |2012/12/1 |
| 红色 |B |100,000 |2012/12/1 |
| 绿色 |C |50,000 |2012/12/1 |
| 黄色 |C |<br /> |<br /> |
| 紫色 |B |<br /> |<br /> |
| 橙色 |C |<br /> |<br /> |

这两个表之间存在一对一的关系，原因是组合表的项目列中没有重复值。 项目列是唯一的，因为每个值仅出现一次，因此这两个表中的行可直接合并且无任何重复项。

但是，假设你知道在下次刷新数据时，此数据会进行更改。 对于蓝色和红色项目，刷新后的 ProjectBudget 表现具有其他行：

**ProjectBudget**

| **已批准的项目** | **预算分配** | **分配日期** |
| --- | ---:| ---:|
| 蓝色 |40,000 |2012/12/1 |
| 红色 |100,000 |2012/12/1 |
| 绿色 |50,000 |2012/12/1 |
| 蓝色 |80,000 |2013/6/1 |
| 红色 |90,000 |2013/6/1 |

 这意味着实际上，这两个表的最佳组合现如下所示： 

| **项目** | **优先级** | **预算分配** | **分配日期** |
| --- | --- | ---:| ---:|
| 蓝色 |A |40,000 |2012/12/1 |
| 红色 |B |100,000 |2012/12/1 |
| 绿色 |C |50,000 |2012/12/1 |
| 黄色 |C |<br /> |<br /> |
| 紫色 |B |<br /> |<br /> |
| 橙色 |C |<br /> |<br /> |
| 蓝色 |A |80000 |2013/6/1 |
| 红色 |B |90000 |2013/6/1 |

在这个新的组合表中，项目列具有重复值。  刷新表格后，两个原始表将不再具有一对一的关系。 此情况下，由于我们知道将来的这些更新将导致项目列出现重复项，因此想要将基数设置额外多对一 (\*:1)，其中多方位于 ProjectBudget 表上，而单方位于 CompanyProjectPriority 表上。

## <a name="adjusting-cross-filter-direction-for-a-complex-set-of-tables-and-relationships"></a>为一组复杂的表和关系调整交叉筛选器方向
对于大多数关系，交叉筛选方向均设置为“双向”。  但在某些更不常见的情况下，你可能需要将其设置为非默认值，例如如果你正在从较旧版本的 Power Pivot 中导入模型，而该版本中每个关系均设置为单向。 

通过“双向”设置，Power BI Desktop 可将连接表的所有方面均视为如同是一个表。  然而在某些情况下，Power BI Desktop 无法将关系的交叉筛选方向设置为“双向”，同时还会保留一组可用于报表且语义不明的默认值。 如果关系的交叉筛选方向未设置为“双向”，这通常是因为它造成了多义性。  如果默认的交叉筛选设置不适用于你，请尝试将其设置为特定表格或“双向”。

单向交叉筛选适用于很多情况。  事实上，如果你在 Excel 2013 或更早版本中导入 Power Pivot 中的模型，则所有关系均将设置为单向。  单向是指连接表中的筛选选项适用于将进行聚合操作的表格。  有时，交叉筛选可能有点难以理解，因此我们来看一个示例。

 ![](media/desktop-create-and-manage-relationships/candmrel_singledircrossfiltering.png)

通过单向交叉筛选，如果你创建一个可汇总项目小时数的报表，则可选择按 CompanyProject 的优先级还是 CompanyEmployee 的城市进行汇总（或筛选）。   但如果你想计算每个项目的员工数（不太常见的问题），则不适用。 你将获取完全相同的一列值。  在下例中，两个关系的交叉筛选方向均设置为单向 - 指向 ProjectHours 表：

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfiltersingle.png)

筛选器规范将从 CompanyProject 流向 CompanyEmployee（如下图所示），但不会抵达 CompanyEmployee。  但若将交叉筛选方向设置为“双向”，则会起作用。  “双向”设置使筛选器规范可抵达员工。

 ![](media/desktop-create-and-manage-relationships/candmrel_bidircrossfiltering.png)

通过将交叉筛选方向设置为“双向”，报表现正确显示：

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilterbi.png)

双向交叉筛选非常适合类似于上述模式的表格关系模式。 这通常称为星型架构，如下所示：

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterstarschema.png)

交叉筛选不太适合数据库中常有的更常规模式，比如以下关系图中的模式：

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterwithloops.png)

如果你具有与此类似的表格模式，则交叉筛选会创建一组语义不明的关系。 例如，如果你求取 TableX 中某个字段的总和，然后选择按 TableY 中的某个字段进行筛选，则不清楚筛选器应如何流动，是通过顶部表还是底部表进行流动。 这种模式的一种常见示例是 TableX 为具有实际销售额数据的销售表，而 TableY 具有预算数据。 则中间的表格是这两个表所用的查找表，如部门或地区。 

和活动/非活动关系一样，如果会导致报表的多义性，则 Power BI Desktop 不允许将关系设置为“双向”。 有多种不同的方式可处理此问题，下面是最常见的两种方式：

* 删除关系或将其标记为“非活动”，以减少多义性。 然后，可能就能够将关系的交叉筛选设置为“双向”了。
* 导入表格两次（第二次使用其他名称）以消除循环。  这会产生类似于星型架构的关系模式。  借助星型架构，所有关系均可设置为“双向”。

## <a name="wrong-active-relationship"></a>错误的活动关系
Power BI Desktop 自动创建关系时，有时会在两个表之间遇到多个关系。  发生此情况时，仅其中一个关系会设置为“活动”。  活动关系用作默认关系，因此在从两个不同的表中选择字段时，Power BI Desktop 可自动为你创建可视化对象。  但在某些情况下，自动选定的关系可能是错误的。  可使用“管理关系”对话框将关系设置为“活动”或“非活动”，或者可在“编辑关系”对话框中设置活动关系。 

为确保存在默认关系，Power BI Desktop 仅允许两个表在给定时间存在单个活动关系。  因此，你必须先将当前关系设置为“非活动”，然后将想要的关系设置为“活动”。

我们来看一个示例。 第一个表是 ProjectTickets，而下一个表是 EmployeeRole。

**ProjectTickets**

| **工作单** | **开具者** | **提交者** | **小时数** | **项目** | **提交日期** |
| ---:|:--- |:--- | ---:|:--- | ---:|
| 1001 |Perham, Tom |Brewer, Alan |22 |蓝色 |2013/1/1 |
| 1002 |Roman, Daniel |Brewer, Alan |26 |红色 |2013/2/1 |
| 1003 |Roth, Daniel |Ito, Shu |34 |黄色 |2012/12/4 |
| 1004 |Perham, Tom |Brewer, Alan |13 |橙色 |2012/1/2 |
| 1005 |Roman, Daniel |Bowen, Eli |29 |紫色 |2013/10/1 |
| 1006 |Roth, Daniel |Bento, Nuno |35 |绿色 |2013/2/1 |
| 1007 |Roth, Daniel |Hamilton, David |10 |黄色 |2013/10/1 |
| 1008 |Perham, Tom |Han, Mu |28 |橙色 |2012/1/2 |
| 1009 |Roman, Daniel |Ito, Shu |22 |紫色 |2013/2/1 |
| 1010 |Roth, Daniel |Bowen, Eli |28 |绿色 |2013/10/1 |
| 1011 |Perham, Tom |Bowen, Eli |9 |蓝色 |2013/10/15 |

**EmployeeRole**

| **员工** | **角色** |
| --- | --- |
| Bento, Nuno |项目经理 |
| Bowen, Eli |项目主管 |
| Brewer, Alan |项目经理 |
| Hamilton, David |项目主管 |
| Han, Mu |项目主管 |
| Ito, Shu |项目主管 |
| Perham, Tom |项目发起人 |
| Roman, Daniel |项目发起人 |
| Roth, Daniel |项目发起人 |

实际上，这里存在两个关系。 一个是 ProjectTickets 表中的提交者和 EmployeeRole 表中的员工之间的关系，而另一个是 ProjectTickets 中的开具者和 EmployeeRole 表中的员工之间的关系。

 ![](media/desktop-create-and-manage-relationships/candmrel_activerelview.png)

如果将这两个关系添加到模型（先是开具者），则“管理关系”对话框将显示开具者处于活动状态：

 ![](media/desktop-create-and-manage-relationships/candmrel_managerelactive.png)

现在，如果创建一个报表，且该报表在报表画布的表格可视化对象中使用 EmployeeRole 中的“职位”和“员工”字段，以及 ProjectTickets 中的“小时数”字段，则只会显示项目发起人，因为他们是唯一开具项目单的人员。

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilteractive.png)

我们可更改活动关系并获取提交者，而不是开具者。 在“管理关系”中，取消勾选 ProjectTickets（开具者）到 EmployeeRole（员工）的关系，然后勾选 ProjectTickets（提交者）到 EmployeeRole（员工）的关系。

![](media/desktop-create-and-manage-relationships/candmrel_managerelactivesubmittedby.png)

## <a name="see-all-of-your-relationships-in-relationship-view"></a>在关系视图中查看所有关系
有时，模型具有多个表格，且各表格之间存在复杂关系。 Power BI Desktop 中的关系视图可显示模型中的所有关系及其方向和基数，是一种易于理解且可自定义的关系图。 若要了解更多信息，请参阅 [Power BI Desktop 中的关系视图](desktop-relationship-view.md)。


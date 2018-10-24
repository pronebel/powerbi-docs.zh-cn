---
title: 使用 Power BI Desktop 中的复合模型（预览）
description: 在 Power BI Desktop 中创建具有多个数据连接和多对多关系的数据模型
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/02/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 49540dd491d02c6a6b474ff80690a75eecfd27db
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336981"
---
# <a name="composite-models-in-power-bi-desktop-preview"></a>Power BI Desktop 中的复合模型（预览）

在以前的 Power BI Desktop 中，当在报表中使用 DirectQuery 时，该报表不允许其他数据连接，无论是 DirectQuery 还是导入都是如此。 有了复合模型后，便删除了该限制，并且一个报表可以在所选择的任何组合中无缝地包含来自多个 DirectQuery 或导入数据连接的数据连接。

![Power BI Desktop 中的复合模型](media/desktop-composite-models/composite-models_01.png)

Power BI Desktop 中的复合模型功能包括三个相关功能：

* 复合模型 - 允许报表在任何组合中有多个数据连接，包括 DirectQuery 连接或导入。
* 多对多关系 - 通过复合模型，可以在表之间建立多对多关系，进而删除表中的唯一值要求，并删除之前的解决办法，例如，引入新表只是为了建立关系。 
* 存储模式 - 现在，你可以指定哪些视觉对象需要对后端数据源进行查询，而那些不需要进行此查询的视觉对象则导入（即使是基于 DirectQuery），进而提升性能并减少后端负载。 在此之前，即使是像切片器这样的简单视觉对象，也会启动发送至后端源的查询。 

此复合模型的三个相关功能集合分别在不同文章中进行了说明：

* 本文详细介绍了复合模型。
* 多对多关系在其专属文章 [Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)中介绍。
* 存储模式在其专属文章 [Power BI Desktop 中的存储模式（预览）](desktop-storage-mode.md)中介绍。

## <a name="enabling-the-composite-models-preview-feature"></a>启用复合模型预览功能

复合模型为预览功能，必须在 Power BI Desktop 中启用。 若要启用复合模型，请选择“文件”>“选项和设置”>“选项”>“预览功能”，然后选中“复合模型”复选框。 

![启用预览功能](media/desktop-composite-models/composite-models_02.png)

需要重新启动 Power BI Desktop 才能启用该功能。

![需要重新启动，更改才会生效](media/desktop-composite-models/composite-models_03.png)


## <a name="using-composite-models"></a>使用复合模型

有了复合模型，使用 Power BI Desktop 或 Power BI 服务时，可以连接各种类型的数据源，并且可以通过不同的方式连接这些数据。 可以将数据导入 Power BI，这是获取数据最常见的方法，也可以使用 DirectQuery 在其原始源存储库中直接连接数据。 欲了解有关 DirectQuery 的详细信息，请参阅[在 Power BI 中使用 DirectQuery](desktop-directquery-about.md) 一文。

使用 DirectQuery 时，借助复合模型，便可以创建 Power BI 模型（如单个.pbix Power BI Desktop 文件），它可以执行以下操作：

* 合并来自一个或多个 DirectQuery 源的数据，和/或
* 合并来自 DirectQuery 源的数据和导入数据

例如，借助复合模型，便可以生成一个模型，将企业数据仓库中的销售数据与部门的 SQL Server 数据库中的销售目标数据及一些从电子表格中导入的数据合并。 将来自多个 DirectQuery 源的数据合并，或将 DirectQuery 与导入的数据相结合的模型称为“复合模型”。

> [!NOTE]
> 从 Power BI Desktop 的 2018 年 10 月版开始，用户可将复合模型发布到 Power BI 服务中。 对于计划的刷新和仪表板磁贴刷新，Power BI 服务中的复合模型的行为方式与导入模型的行为方式完全相同。 

你可以像往常一样创建表之间的关系，即使这些表来自不同的源，且包含以下限制：跨源的任何关系必须定义为具有一个基数的多对多，不管其实际基数是多少。 此类关系的行为便与多对多关系的行为一样正常，如[Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)中所述。 请注意，在复合模型的上下文中，不管导入的表实际是从哪个实际基础数据源导入，所有导入的表实际上都是一个单一源。   

## <a name="example-of-using-composite-models"></a>使用复合模型示例

作为复合模型的一个示例，请考虑一个已使用 DirectQuery 连接到企业数据仓库（在 SQL Server 中）的报表，其中数据仓库包含“Sales by Country”、“Quarter”和“Bike (Product)”数据，如下图所示。

![复合模型的关系视图](media/desktop-composite-models/composite-models_04.png)

此时，可以使用来自此源的字段构建简单的视觉对象。 例如，下面的视觉对象显示按“ProductName”排布的所选季度的销售总额。 

![基于数据的视觉对象](media/desktop-composite-models/composite-models_05.png)

但是，如果你有一些关于已分配到每个产品的产品经理的信息，并了解到市场营销优先级，那么是在 Excel 电子表格中的哪个位置对这些数据进行维护呢？ 你可能想要看到按“Product Manager”排布的“Sales Amount”，但将此本地数据添加到企业数据仓库可能不可行，或者理想情况下，需要几个月的时间。 尽管可能可以从数据仓库（而不是使用 DirectQuery）中导入此销售数据，届时可以将该数据与从电子表格导入的数据合并，但这种做法是不合理的，其原因包括在基础源中强制实施的一些安全规则组合、需要能够看到最新数据，以及数据的庞大规模，进而导致首先使用 DirectQuery。 

因此需要用到复合模型。 复合模型允许你使用 DirectQuery 连接到数据仓库，然后还可以使用 GetData 获取其他源。 在这种情况下，我们建立到企业数据仓库的 DirectQuery 连接，然后使用 GetData 并选择 Excel，导航到包含我们本地数据的电子表格，并且可以导入包含“ProductNames”、已分配的“SalesManager”和“Priority”的工作表。  

![导航器窗口](media/desktop-composite-models/composite-models_06.png)

现在，在“字段”列表中，我们可以看到原始“Bike”表（来自 SQL Server）和新的“Product Managers”表（使用从 Excel 导入的数据）。 

![表的字段视图](media/desktop-composite-models/composite-models_07.png)

同样，看一下 Power BI Desktop 中的“关系视图”，我们现在可以看到更多名为“Product Managers”的表。 

![表的关系视图](media/desktop-composite-models/composite-models_08.png)

现在，我们需要像往常那样将这些表关联到其他模型中的表，方法是在“Bike”表（在 SQL Server 中）和“Product Managers”表（即导入的表）之间创建关系，例如在 Bike[ProductName] 和 ProductManagers[ProductName] 之间创建关系。 如本文前面部分所述，通过源的所有关系必须具有基数多对多，这种情况下，这就是处于选中状态的默认基数。 

![“创建关系”对话框](media/desktop-composite-models/composite-models_09.png)

创建此关系后，关系会按照我们所期望的那样显示在 Power BI Desktop 的“关系视图”中。

![新关系视图](media/desktop-composite-models/composite-models_10.png)

建立这些表关系后，我们现在可以使用“字段”列表中的任何字段创建视觉对象，无缝组合来自多个源的数据。 例如，下面的视觉对象显示每个“Product Manager”的“Sales Amount”总计。 

![显示“字段”窗格的视觉对象](media/desktop-composite-models/composite-models_11.png)

此示例演示一个常见的维度表示例（如“Product”或“Customer”），该表通过从其他位置导入的一些额外数据进行扩展，也可以让表使用 DirectQuery 连接到不同源。 因此若要扩展我们的示例，假定每个“Country”和“Period”的“SalesTargets”都存储在一个单独的部门数据库中。 可以像往常那样使用 GetData 连接到该数据，如下图所示。 

![导航器对话框](media/desktop-composite-models/composite-models_12.png)

然后，类似于我们之前在此示例中所操作的，我们可以在模型中在新表和其他表之间创建关系，并创建合并其数据的视觉对象。 让我们再次看看“关系视图”，我们已在扩展示例方案中建立新关系。

![具有多表的关系视图](media/desktop-composite-models/composite-models_13.png)

如下图所示，它基于我们刚刚创建的新数据和关系，左下角的视觉对象显示“Sales Amount”总计和“Target”，包含显示差异的方差计算，其中“Sales Amount”和“Target”来自两个不同的 SQL Server 数据库。 

![视觉对象显示更多数据](media/desktop-composite-models/composite-models_14.png)

## <a name="setting-storage-mode"></a>设置存储模式

**复合模型**中的每个表都有一个**存储模式**，指示表是基于 DirectQuery 还是导入。 可以在“属性”窗格中查看和修改存储模式。 要进行此操作，请从“字段”列表选择“属性”，右键单击上下文菜单。 下图显示存储模式（由于窗格宽度，图中缩写为“存储...”）。

![存储模式设置](media/desktop-composite-models/composite-models_15.png)

也可以在每个表的工具提示上查看存储模式。

![工具提示和存储模式](media/desktop-composite-models/composite-models_16.png)

对于任何 Power BI Desktop 文件（.pbix 文件），其中包含一些来自 DirectQuery 的表和一些导入表，状态栏显示“混合”存储模式。 可以在状态栏中单击该术语，并轻松切换所有表以导入。

有关存储模式的详细信息，请参阅 [Power BI Desktop 中的存储模式（预览）](desktop-storage-mode.md)一文中的完整介绍。  

## <a name="calculated-tables"></a>计算表

计算表可以添加到使用 DirectQuery 的模型，定义计算表的 DAX 可以引用导入表或 DirectQuery 表或将两者结合引用。 

计算表始终导入，刷新表时，也将刷新这些表中的数据。 在这种情况下，如果计算表引用 DirectQuery 表，引用 DirectQuery 表的视觉对象始终在基础源中显示最新值，但引用计算表的视觉对象显示计算表最后一次刷新时的值。

## <a name="security-implications"></a>安全隐患 

复合模型有一些安全隐患。 发送到一个数据源的查询可以包括已从另一个不同源检索的数据值。 对于本文前面部分所述的示例，显示按“Product Manager”排布的“Sales Amount”的视觉对象会导致 SQL 查询发送到“Sales”关系数据库，其中此 SQL 查询可能包含“Product Managers”的名称及其关联“Products”。 

![脚本显示安全隐患](media/desktop-composite-models/composite-models_17.png)

因此，存储在电子表格中的信息现包含在发送到关系数据库的查询中。 如果为机密信息，则应考虑此安全隐患。 具体而言，应考虑以下隐患：

* 任何能够看到跟踪或审计日志的数据库管理员都能够看到这些信息，即使他们不具备对原始源中数据的权限（在本例中是对 Excel 文件的权限）。

* 应考虑每个源的加密设置，以避免使用加密连接从一个源检索信息，而然后无意中将它包含在一个使用未加密连接发送到另一个源的查询中。 

采取措施创建复合模型时，Power BI Desktop 会显示一条警告消息，以便确认已考虑任何安全隐患。  

出于类似原因，打开从不受信任的源发送的 Power BI Desktop 文件时必须小心谨慎。 如果该文件包含复合模型，则意味着从一个源中检索的信息（使用用户凭据打开文件）将发送到另一个数据源作为查询的一部分（Power BI Desktop 文件的恶意作者可能会看到它）。 因此，当第一次打开 Power BI Desktop 文件，如果它包含多个源，将显示警告。 此警告类似于打开包含本机 SQL 查询的文件时显示的警告。  

## <a name="performance-implications"></a>性能影响  

使用 DirectQuery 时应始终考虑性能，主要是为了确保后端源具有足够的资源来为用户提供良好体验。 良好的体验意味着视觉对象应在 5 秒或更短时间内刷新一次。 还应遵守[在 Power BI 中使用 DirectQuery](desktop-directquery-about.md) 一文中的性能建议。 使用复合模型会增加额外的性能注意事项，因为单个视觉对象可能会导致将查询发送到多个源，通常将结果从一个查询传递到另一个源。 这种情况可能会导致以下可能的执行形式：

* 包含大量文本值的 SQL 查询 - 例如，请求一组选定的“Product Managers”（来自从电子表格导入的相关表）的“Sales Amount”总计（来自 SQL 数据库）的视觉对象首先需要找出哪些产品由那些产品经理管理，然后再发送 WHERE 子句中包含的所有产品 ID 的 SQL 查询。

* 在较低级别粒度上查询的 SQL 查询，然后本地聚合数据 - 使用此列表中与上一项目符号项相同的示例，因为满足“Product Manager”上的筛选器的“Products”数量变得非常大，在某些时候变得无效或不可行，而无法将它们都包含在 WHERE 子句中。 相反，有必要在“Product”的较低级别查询关系源，然后在本地聚合结果。 如果“Products”基数超过 100 万限制，则查询失败。

* 多个 SQL 查询，按值一个组一个 - 当聚合使用 DistinctCount（按来自另一个源的某个列分组），如果外部源不支持有效传递定义分组的多个文本值，则需要按值每组发送一个 SQL 查询。 例如，请求按“Product Manager”（来自电子表格导入的相关表）排布的不同数量的 CustomerAccountNumber（来自 SQL Server 表）的视觉对象，需要在发送到 SQL Server 的查询中传递来自“Product Managers”表的详细信息。 在其他源上（例如 Redshift），这是不可行的，而是会针对每个销售经理发送一个 SQL 查询（直到某个实际的限制，这时查询就会失败）。 

每一种情况对性能都有其相应的影响，每个数据源的具体细节都有所不同。 一个很好的经验法则是，虽然在连接两个源的关系中使用的列的基数仍然很低（几千），但性能不应受到很大影响。 随着基数的增长，需要更多地考虑对结果性能的影响。 

此外，使用多对多关系意味着必须将单独查询发送到每个总计/小计级别的基础源，而不是在本地聚合详细值。 因此，一个带总计的简单表视觉对象将发送两个 SQL 查询，而不是一个。 

## <a name="limitations-and-considerations"></a>限制和注意事项

此版本的复合模型有一些限制。

以下 Live Connect（多维）源不能用于复合模型：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 数据集
* Azure Analysis Services

当使用 DirectQuery 连接到这些多维数据源时，不能同时连接到另一个 DirectQuery 源，也不能与导入的数据相结合。

在使用复合模型时，使用 DirectQuery 的现有限制仍然适用。 现在每个表都有许多这些限制，这取决于表的存储模式。 例如，导入表上的计算列可以引用其他表，但是 DirectQuery 表上的计算列仍限制为只能引用同一表上的列。 如果模型中的任何一个表都是 DirectQuery，则其他限制适用于整个模型。 例如，如果模型中有任何表具有 DirectQuery 的存储模式，则 QuickInsights 和问答功能在该模型上不可用。 

## <a name="next-steps"></a>后续步骤

以下文章提供了更多有关复合模型的信息，并详细介绍了 DirectQuery。

* [Power BI Desktop 中的多对多关系（预览）](desktop-many-to-many-relationships.md)
* [Power BI Desktop 中的存储模式（预览）](desktop-storage-mode.md)

DirectQuery 文章：

* [在 Power BI 中使用 DirectQuery](desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支持的数据源](desktop-directquery-data-sources.md)


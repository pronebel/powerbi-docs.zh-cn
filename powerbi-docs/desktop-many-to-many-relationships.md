---
title: Power BI Desktop 中的多对多关系（预览）
description: 使用 Power BI Desktop 的多对多关系
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 5c0c6fd619a2487f9c801200d732cda628a68055
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973991"
---
# <a name="many-to-many-relationships-in-power-bi-desktop-preview"></a>Power BI Desktop 中的多对多关系（预览）

通过 Power BI Desktop 的多对多关系功能，可以使用一个基数的多对多来联接表，并以更简单和直观的方式创建包含多个数据源的数据模型。 多对多关系功能是 Power BI Desktop 较大复合模型功能中的一部分。

![“编辑关系”对话框中的多对多](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Power BI Desktop 中的多对多关系功能是以下三个相关功能集合的一部分：

* 复合模型 - 允许报表在任何组合中有多个数据连接，包括 DirectQuery 连接或导入。
* 多对多关系 - 通过复合模型，可以在表之间建立多对多关系，进而删除表中的唯一值要求，并删除之前的解决办法，例如，引入新表只是为了建立关系。 
* 存储模式 - 现在，你可以指定哪些视觉对象需要对后端数据源进行查询，而那些不需要进行此查询的视觉对象则导入（即使是基于 DirectQuery），进而提升性能并减少后端负载。 在此之前，即使是像切片器这样的简单视觉对象，也会启动发送至后端源的查询。 

此复合模型的三个相关功能集合分别在不同文章中进行了说明：

* 复合模型在 [Power BI Desktop 中的复合模型（预览）](desktop-composite-models.md)一文中详细介绍。
* 本文介绍了多对多关系。
* 存储模式在其专属文章 [Power BI Desktop 中的存储模式（预览）](desktop-storage-mode.md)中介绍。

## <a name="enabling-the-many-to-many-relationships-preview-feature"></a>启用多对多关系预览功能

多对多关系功能是复合模型功能的一部分且处于预览阶段，必须在 Power BI Desktop 中启用。 若要启用复合模型，请选择“文件”>“选项和设置”>“选项”>“预览功能”，然后选中“复合模型”复选框。

![启用预览功能](media/desktop-composite-models/composite-models_02.png)

需要重新启动 Power BI Desktop 才能启用该功能。

![需要重新启动，更改才会生效](media/desktop-composite-models/composite-models_03.png)


## <a name="what-many-to-many-relationships-solves"></a>多对多关系可以解决的问题

在多对多关系可用之前，当在 Power BI 的两个表之间定义关系时，关系中所涉及的列至少有一个必须包含唯一值。 但在许多情况下，表中没有列包含唯一值。 

例如，两个表可能有一个列，其中包含“Country”，但“Country”的值在这两个表中都不是唯一的。 要在此类表之间进行联接，需要创建一种解决方法，例如在模型中引入其他表，其中包含所需的惟一值。 多对多关系功能提供了一种替代方法，使此类表可以直接使用与一个基数的多对多之间的关系进行联接。  

## <a name="using-many-to-many-relationships"></a>使用多对多关系

在 Power BI 中定义两个表之间的关系时，必须定义关系的基数。 例如，ProductSales 和 Product（使用列 ProductSales[ProductCode] 和 Product[ProductCode]）之间的关系将定义为“多对 1”，因为每个产品有多个销售，且“Product”表 (ProductCode) 中的列是唯一的。 当将关系基数定义为“多对 1”、“1 对多”，或“1 对 1”时，Power BI 将执行验证，以确保所选基数与实际数据匹配。

例如，查看下图中的简单模式。

![关系视图](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

然后假设“Product”表只包含两行。

![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

此外，假设“Sales”表只有四行，其中包括产品 C 的“Sales”，此行不存在于“Product”表中（因为出现了引用完整性错误）。

![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

显示“ProductName”和“Price”（来自“Product”表）及每个产品“Qty”总计（来自“ProductSales”表）的视觉对象将如下图所示： 

![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

如上图所示，视觉对象中有一行带空白 ProductName，该行与产品 C 的销售相关联。此空白行说明以下问题：

* “ProductSales”表中的任意行在“Product”表中均没有对应的行 - 存在一个引用完整性问题，正如本例中的产品 C 所示。

* “ProductSales”表中任意行的外键列为 Null。 

出于上述原因，在这两种情况下，空白行说明销售中的 ProductName 和 Price 均未知。

而有时是，表通过两个列连接起来，但这两列都不是惟一的。 例如下面的两个表：

* “Sales”表包含按“State”排布的销售数据，其中每个行包含该州（包括 CA、WA 和 TX）相应销售类型的销售额 

    ![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* “CityData”表包含有关城市的数据，包括人口和州（包括 CA、WA 和 New York）

    ![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

尽管两个表中均有一个“State”列，并且希望报告按“State”排布的“Sales”总计以及每个“State”的总人口，这都是合理的，但存在一个问题：“State”列在这两个表中都不是唯一的。 

## <a name="the-prior-workaround"></a>之前的解决方法

在 2018 年 7 月之前的 Power BI Desktop 版本中，无法直接在这些表之间创建关系。 此问题的常见解决方法是执行以下操作：

* 创建仅包含唯一 State id 的第三个表。 这可能是计算表（使用 DAX 定义），或者是使用查询编辑器中定义的查询定义的表，其中可能包含来自其中一个表的唯一 ID，或者是一个联结的完整集。

* 使用常见的*多对 1 关系，将这两个原始表关联到此新表。

该解决方法表可能保持可见或被隐藏，以此它不会出现在字段列表中。 在后一种情况下，多对 1 关系通常会设置为双向筛选，以便可以使用任一表中的“State”字段，同时后续交叉筛选传播到另一个表。 此解决方法如下图中的关系视图所示。

![关系视图](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

显示“State”（来自“CityData”表）以及“Population”总计和“Sales”总计的视觉对象将如下所示。

![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

请注意，鉴于在此解决方法中使用了“CityData”中的州，只会列出该表中的“State”（因此 TX 将排除在外）。 此外，与多对 1 关系情况不同，虽然总计行包含所有“Sales”（包括 TX 的“Sales”），详细信息并不包括涉及此类不匹配行的空白行。 同样，没有空白行会涵盖任何“Sales”，其中的“State”有一个 null 值。

如果“City” 也添加到该视觉对象，则当每个“City”的人口已知，为“City”显示的“Sales”只会重复相应“State”的“Sales”（当在一个与某个聚合度量没有关联的列上分组时，通常会出现这种情况），如下图所示。

![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

如果在此解决方法中新表“Sales”定义为所有“States”的联合，并使其在字段列表中可见，则显示“State”（在新表上）以及“Population”总计和“Sales”总计的相同视觉对象将如下所示。

![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

在此情况下，以及如视觉对象中所示的那样，TX（具有“Sales”但人口未知）和 New York（人口已知但无“Sales”）将包括在内。 

正如你所看到的，此解决方法并不是最理想的，且存在很多问题。 可以通过创建多对多关系解决这些问题，如以下部分所述。

## <a name="using-many-to-many-relationships-instead-of-the-workaround"></a>使用多对多关系而不是该解决方法

从 2018 年 7 月开始的 Power BI Desktop 版本中，可以直接关联前面部分所述的表，而无需采用此类解决方法。 现可将关系基数设置为“多对多”，指示两个表均不包含唯一值。 对于这种关系，仍可以控制哪个表筛选另一个表，或进行双向筛选，其中两个表进行相互筛选。  

> [!NOTE]
> 创建多对多关系的功能处于预览阶段，虽然为预览状态，但不能使用多对多关系将模型发布到 Power BI 服务。 

在 Power BI Desktop 中，当确定两个表在关系中均不包含列的唯一值，默认基数为多对多。 此类情况下将显示一条警告消息，以确认该关系设置为预期行为，而不是由数据问题导致的非预期效应。 

例如，直接在“CityData”和“Sales” 之间创建关系时，其中筛选器应从“CityData”流向“Sales”，关系对话框如下图所示。

![“编辑关系”对话框](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

产生的关系视图将包含两个表之间的直接多对多关系。 “字段”列表中的外观及创建视觉对象时的后续行为将与采用前面部分所述的工作方法相同，其中额外的表（包含非重复 States）不可见。 例如，和前面部分所述的解决方法一样，显示“States”和总人口及销售额的视觉对象将如下所示。

![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

因此，多对多关系和更为典型的多对 1 关系之间的主要区别如下。

* 显示的值不包括空白行，这说明另一个表中的任何不匹配行，或另一个表中在关系中使用的列所对应的行为 null。
* 不能使用 RELATED() 函数（因为可能有多个关联行）
* 在一个表上使用 ALL() 函数不会删除应用于其他表的筛选器，这些表通过多对多关系与此表关联。 例如，如以下在前面示例中定义的度量值不会删除相关“CityData”表的列上的筛选器：

    ![脚本示例](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    因为此类显示“State”、“Sales”和“Sales total” 的视觉对象会导致以下情况：

    ![表视觉对象](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

因此，应格外小心以确保使用 ALL(\<Table>) 的计算（如总计百分比）将返回预期结果。 


## <a name="limitations-and-considerations"></a>限制和注意事项

此版本的多对多关系和复合模型有一些限制。

以下 Live Connect（多维）源不能用于复合模型：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 数据集
* Azure Analysis Services

当使用 DirectQuery 连接到这些多维数据源时，不能同时连接到另一个 DirectQuery 源，也不能与导入的数据相结合。

在使用多对多关系时，使用 DirectQuery 的现有限制仍然适用。 现在每个表都有许多这些限制，这取决于表的存储模式。 例如，导入表上的计算列可以引用其他表，但是 DirectQuery 表上的计算列仍限制为只能引用同一表上的列。 如果模型中的任何一个表都是 DirectQuery，则其他限制适用于整个模型。 例如，如果模型中有任何表具有 DirectQuery 的存储模式，则 QuickInsights 和问答功能在该模型上不可用。 

## <a name="next-steps"></a>后续步骤

以下文章提供了更多有关复合模型的信息，并详细介绍了 DirectQuery。

* [Power BI Desktop 中的复合模型（预览）](desktop-composite-models.md)
* [Power BI Desktop 中的存储模式（预览）](desktop-storage-mode.md)

DirectQuery 文章：

* [在 Power BI 中使用 DirectQuery](desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支持的数据源](desktop-directquery-data-sources.md)


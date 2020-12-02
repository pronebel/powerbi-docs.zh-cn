---
title: 在 Power BI 中将 DirectQuery 用于 SAP HANA
description: 将 DirectQuery 用于 SAP HANA 时的注意事项
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 04/10/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: f6cb4fa1ee35754d8ffe468ddb845089f26045a9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411163"
---
# <a name="connect-to-sap-hana-data-sources-by-using-directquery-in-power-bi"></a>使用 Power BI 中的 DirectQuery 连接到 SAP HANA 数据源
可以使用 DirectQuery 直接连接到 SAP HANA 数据源。 连接到 SAP HANA 时存在两个选项：

* **将 SAP HANA 视为多维源（默认）：** 在这种情况下，该行为将类似于 Power BI 连接到其他多维源（如 SAP Business Warehouse 或 Analysis Services）时的行为。 使用此设置连接到 SAP HANA 时，会选择单个分析或计算视图，并且字段列表中将显示该视图的所有度量值、层次结构和属性。 创建视觉对象后，将始终从 SAP HANA 中检索聚合数据。 建议使用此方法，且 SAP HANA 中的新 DirectQuery 报表均默认采用此方法。

* **将 SAP HANA 视为关系源：** 此情况下，Power BI 将 SAP HANA 视为关系源。 这提供了更大的灵活性。 请务必谨慎使用此方法，确保按预期方式聚合度量值，并避免出现性能问题。

连接方法由全局工具选项确定，确定方式是选择“文件”>“选项和设置”，再选择“选项”>“DirectQuery”，然后选择“将 SAP HANA 视为关系源”选项，如下图所示  。 

![“选项”对话框的屏幕截图，其中显示了 DirectQuery 选项。](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

通过“将 SAP HANA 视为关系源”选项，可控制将 DirectQuery 用于 SAP HANA 的所有新报告所采用的方式。 该选项不影响当前报表中的任何现有 SAP HANA 连接，也不影响打开的任何其他报表中的连接。 因此，如果当前取消选中该选项，则在使用“获取数据”向 SAP HANA 添加新连接时，该连接会将 HANA 视为多维源。 但是，如果打开了另一个也连接到 SAP HANA 的报表，则该报表将根据创建时设置的选项继续运行，这意味着，在 2018 年 2 月之前创建的连接到 SAP HANA 的任何报表会继续将 SAP HANA 视为关系源。 

这两种方法的行为不同，而且不可能将现有报表从一种方法切换到另一种方法。 

我们依次来详细了解这两种方法。

## <a name="treat-sap-hana-as-a-multi-dimensional-source-default"></a>将 SAP HANA 视为多维源（默认）

默认情况下，到 SAP HANA 的所有新连接均使用此连接方法，即将 SAP HANA 视为多维源。 为了将到 SAP HANA 的连接视为关系源，必须选择“文件”>“选项和设置”>“选项”，再选择“直接查询”，然后选择“将 SAP HANA 视为关系源”下的复选框 。 虽然这是预览功能，但无法将使用多维方法创建的报表发布到 Power BI 服务，并且这样做将会导致在 Power BI 服务内打开报表时出现错误。  

连接到作为多维源的 SAP HANA 时，请注意以下事项：

* 在“获取数据导航器”中，可选择单个 SAP HANA 视图。 不能选择各个度量值或属性。 在连接时没有定义查询，这与数据导入操作不同，也与在将 SAP HANA 视为关系源的情况下使用 DirectQuery 时的操作不同。 这也意味着选择此连接方法时，不能直接使用 SAP HANA SQL 查询。

* 所选视图的所有度量值、层次结构和属性将显示在字段列表中。 

* 由于在视觉对象中使用度量值，因此将查询 SAP HANA，在视觉对象所需的聚合级别检索度量值。 这样一来，在处理非累加性度量值（计数器和比率等）时，所有聚合均由 SAP HANA 执行，且 Power BI 不进一步进行聚合。 

* 若要确保始终可从 SAP HANA 获得正确的聚合值，必须施加某些限制。 例如，不能添加计算的列，或者不能在同一报表中合并来自多个 SAP HANA 视图的数据。 

将 SAP HANA 视为多维源后，并不像替代关系方法一样能提升灵活性，但该方法更简单，在处理更复杂的 SAP HANA 度量值时可保证聚合值正确无误，而且通常可提高性能。 

“字段”列表将包括来自 SAP HANA 视图的所有度量值、属性和层次结构。 请注意使用此连接方法时应用的以下行为：

* 至少包含在一个层次结构中的任何属性都将默认隐藏。 但是，如果需要，可以通过从字段列表的上下文菜单中选择“查看隐藏”进行查看。 如果需要，可以从同一上下文菜单中使它们可见。

* 在 SAP HANA 中，可定义一个属性，它将采用其他属性作为其标签。 例如，Product（值为 1、2、3 等）可以使用 ProductName（值为 Bike、Shirt、Gloves 等）作为其标签。 在这种情况下，单个字段 Product 将显示在字段列表中，其值是标签 Bike、Shirt、Gloves 等，但它们将按键值 1、2、3 进行排序并由键值决定其唯一性。 另外，还会创建一个隐藏列 Product.Key，从而允许根据需要访问基础键值。 

连接时会显示基础 SAP HANA 视图中定义的所有变量，还可输入必要的值。 通过从功能区中选择“编辑查询”，然后从显示的下拉菜单中选择“管理参数”，可以随后更改这些值 。 

考虑到需要确保始终能够从 SAP HANA 获取正确的聚合数据，允许的建模操作比使用 DirectQuery 时的一般情况更具限制性。 但是，仍然可以执行许多添加和更改操作，包括定义度量值、重命名和隐藏字段以及定义显示格式。 所有这些更改将在刷新时保留，并会应用对 SAP HANA 视图所做的任何非冲突更改。 

### <a name="additional-modeling-restrictions"></a>其他建模限制

使用 DirectQuery（视为多维源）连接到 SAP HANA 时的主要其他建模限制如下所示： 

* **不支持计算列：** 创建计算列的功能处于禁用状态。 这也意味着创建计算列的“分组”和“聚类分析”功能不可用。
* **针对度量值的其他限制：** 对可在度量值中使用的 DAX 表达式规定有其他限制，以反映 SAP HANA 提供的支持级别。
* **不支持定义关系：** 在报表中只能查询单个视图，因此，不支持定义关系。
* **没有数据视图：** 数据视图通常在表格中显示详细信息级别数据。 鉴于 OLAP 源（如 SAP HANA）的性质，此视图不适用于 SAP HANA。
* **列和度量值详细信息是固定的：** 字段列表中所示的列和度量值列表由基础源固定，不能修改。 例如，不能删除列，也不能更改其数据类型（但是，可以将其重命名）。
* **DAX 中的其他限制：** DAX 中存在可在度量值定义中使用的其他限制，以反映源中的限制。 例如，不能在表中使用聚合函数。

### <a name="additional-visualization-restrictions"></a>其他可视化效果限制

使用 DirectQuery（视为多维源）连接到 SAP HANA 时，视觉对象中存在限制： 
* **没有列聚合：** 不能更改视觉对象上的列的聚合，而且它始终为“不汇总”。

## <a name="treat-sap-hana-as-a-relational-source"></a>将 SAP HANA 视为关系源 

当选择连接到作为关系源的 SAP HANA 时，可一定程度提升灵活性。 例如，可创建计算的列，添加来自多个 SAP HANA 视图的数据，还可在生成的表之间创建关系。 但是，以这种方式使用 SAP HANA 时，请务必了解如何处理连接的某些方面，以确保以下事项： 

* 当 SAP HANA 视图包含非累加性度量值（例如，非重复计数或平均值，而不是简单求和）时，结果与预期一致。
* 生成的查询是高效的

当“获取数据”或“查询编辑器”中定义的查询执行聚合时，最好先弄清关系源（如 SQL Server）的行为 。 在以下示例中，“查询编辑器”中定义的查询按 ProductID 返回平均价格。  

![显示在 Power Query 编辑器中定义的查询的示意图，该查询按产品 ID 返回均价。](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

如果要将数据导入到 Power BI（而不是使用 DirectQuery），将产生以下结果：

* 数据在查询编辑器中创建的查询所定义的聚合级别导入。 例如，按产品划分的平均价格。 这会导致一个表格具有两列：ProductID 和 AveragePrice，可以在视觉对象中使用它们。 
* 在视觉对象中，任何后续聚合（如 Sum、Average、Min 等）都在该导入的数据上执行。 例如，在视觉对象中包含 AveragePrice 时，将默认使用 Sum 聚合，并针对每个 ProductID 在 AveragePrice 上返回总和 - 本例中为 13.67。 这同样适用于视觉对象中使用的任何替代聚合函数（如 Min、Average 等）。 例如，AveragePrice 的 Average 返回 6.66、4 和 3 的平均值，即等于 4.56，而不是基础表中六个记录中的 Price 的平均值 5.17。
  
如果使用 DirectQuery（通过该相同的关系源）而不是 Import，则相同的语义适用并且结果将完全相同：  

* 对于相同的查询，逻辑上完全相同的数据会提供给报表层 - 即使没有实际导入数据。

* 在视觉对象中，任何后续聚合（Sum、Average、Min 等）再次通过查询中的逻辑表执行。 同样，一个包含 AveragePrice 的平均值的视觉对象返回相同的 4.56。
  
现在，在将连接视为关系源时，我们考虑 SAP HANA。 在 SAP HANA 中，Power BI 可以使用分析视图和计算视图，这两种视图都可以包含度量值。 但是现在，用于 SAP HANA 的方法在本部分中遵循如上所述的相同原则：“获取数据”或“查询编辑器”中定义的查询将确定可用数据，然后视觉对象中的任何后续聚合都在该数据上执行，这同样适用于导入和 DirectQuery。  
但是，鉴于 SAP HANA 的性质，初始“获取数据”对话框或“查询编辑器”中定义的查询始终是聚合查询，并且通常会包括度量值，要使用的实际聚合由 SAP HANA 视图定义 。

上述 SQL Server 示例相当于存在包含 ID、ProductID、DepotID 和度量值（包括视图中定义为 AveragePrice 的“平均价格”）的 SAP HANA 视图    。  
    
如果在“获取数据”体验中，所做的选择针对的是 ProductID 和 AveragePrice 度量值，则表示定义对该视图的查询，进而请求该聚合数据（在上例中，为简单起见，使用与 SAP HANA SQL 语法不完全相同的伪 SQL）  。 视觉对象中定义的任何更深入聚合都将进一步聚合此类查询的结果。 如上文针对 SQL Server 所述，这同时适用于导入和 DirectQuery 用例。 在 DirectQuery 用例中，将在发送到 SAP HANA 的单个查询的嵌套 select 语句中使用来自“获取数据”或“查询编辑器”的查询，因此实际上在进一步聚合之前，并不读入所有数据 。  

由于上述所有考虑事项和行为，因此在通过 SAP HANA 使用 DirectQuery 时需注意以下重要事项：  

* 每当 SAP HANA 中的度量值并非累加时（例如不是简单的 Sum、Min 或 Max），必须注意在视觉对象中执行的任何进一步聚合  。

* 在“获取数据”或“查询编辑器”中，只能包含所需的列以检索所需数据，这表示结果将为一个查询，而该查询必须是可发送到 SAP HANA 的合理查询 。 例如，如果选择了多个列，认为在后续视觉对象中可能需要这些列，那么即使是对于 DirectQuery，简单的视觉对象也将意味着嵌套 select 语句中使用的聚合查询将包含这些列，这样通常执行效果将较差。
  
我们来看一个示例。 下例中，在“获取数据”对话框中选择五个列（CalendarQuarter、Color、LastName、ProductLine、SalesOrderNumber），还选择度量值 OrderQuantity，该操作意味着以后创建包含 Min OrderQuantity 的简单视觉对象时会将以下 SQL 查询发送到 SAP HANA     。 阴影是嵌套 select 语句，其中包含“获取数据” / “查询编辑器”中的查询。 如果此嵌套 select 语句提供较高的基数结果，则可能造成 SAP HANA 性能非常不佳。  

![查询示例的屏幕截图，其中显示了对 SAP HANA 执行的 SQL 查询。](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
鉴于此行为，建议在“获取数据”或“查询编辑器”中选择的项仅用于所需项，同时仍然生成 SAP HANA 的合理查询 。  

## <a name="best-practices"></a>最佳做法 

对于这两种 SAP HANA 连接方法，同样建议 SAP HANA 使用 DirectQuery，尤其是要确保优良性能的情况。 [在 Power BI 中使用 DirectQuery](desktop-directquery-about.md) 一文中详细介绍了这些建议。
   
## <a name="limitations"></a>限制

以下列表介绍了使用 Power BI 时不完全支持的所有 SAP HANA 功能，或行为方式不同的功能。 

* **父子层次结构** - 父子层级结构在 Power BI 中将不可见。
这是因为 Power BI 使用 SQL 接口访问 SAP HANA，并且无法通过 SQL 完全访问父子层次结构。
* **其他层次结构元数据** - 层次结构的基本结构显示在 Power BI 中，但一些层次结构元数据（如控制不规则层次结构的行为）将不起作用。
同样，这是由 SQL 接口施加的限制导致的。
* **使用 SSL 连接** - 可以将导入和多维与 SSL 结合使用来进行连接，购买不能连接到配置为将 SSL 用于关系连接器的 SAP HANA 实例。
* **对属性视图的支持** - Power BI 可以连接到分析和计算视图，但不能直接连接到属性视图。
* **对目录对象的支持** - Power BI 无法连接到目录对象。
* **发布后更改变量** - 发布报表后，不能在 Power BI 服务中直接更改任何 SAP HANA 变量的值。 
 
## <a name="known-issues"></a>已知问题 
以下列表介绍了使用 Power BI 连接到 SAP HANA (DirectQuery) 时的所有已知问题。 

* **查询计数器和其他度量值时遇到的 SAP HANA 问题** - 如果连接到分析视图，且计数器度量值和其他一些比率度量值包含在同一视觉对象中，则从 SAP HANA 返回错误的数据。 这包括在 SAP 注释 2128928（查询计算列和计数器时的异常结果）中。 在这种情况下，比率度量值是不正确的。 

* **来自单个 SAP HANA 列的多个 Power BI 列** - 对于某些计算视图，如果某个 SAP HANA 列在多个层次结构中使用，SAP HANA 会将其公开为两个单独的属性。 这会导致在 Power BI 中创建两个列。  但是，这些列默认是隐藏的，所有直接涉及层次结构或列的查询都正确运行。 
 
## <a name="next-steps"></a>后续步骤

有关 DirectQuery 的详细信息，请查看以下资源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支持的数据源](power-bi-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [On-premises data gateway (本地数据网关)](service-gateway-onprem.md)

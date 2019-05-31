---
title: 教程：在 Power BI Desktop 中合并来自 Excel 和 OData 源的数据
description: 教程：合并来自 Excel 和 OData 源的数据
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 94e40681d065591db008f8a9062d851e0bd83f61
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61368229"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>教程：合并来自 Excel 和 OData 源的销售数据

数据遍布于多个数据源是很常见的，例如产品信息可能位于某个数据库，而销售信息则位于另一个数据库。 使用 Power BI Desktop  ，可以合并来自不同源的数据，以创建令人感兴趣的、引人注目的数据分析和可视化效果。 

在本教程中，你将了解如何合并来自两个数据源的数据：包含产品信息的 Excel 工作簿和包含订单数据的 OData 源。 导入每个数据集并执行转换和聚合步骤后，使用这两个源的数据生成具有交互式可视化效果的销售分析报表。 这些技术也可以应用于 SQL Server 查询、CSV 文件和 Power BI Desktop 中的任何其他数据源。

>[!NOTE]
>在 Power BI Desktop 中，有若干种完成任务的方法。 例如，许多功能区选择也可以通过右键单击或者列或单元格中的“更多选项”  菜单来获得。 以下步骤描述了几种备用方法。 

## <a name="import-the-product-data-from-excel"></a>从 Excel 导入产品数据

首先，将 Excel Products.xlsx 工作簿中的产品数据导入 Power BI Desktop。

1. [下载 Products.xlsx Excel 工作簿](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)，并将其保存为 Products.xlsx  。
   
2. 选择 Power BI Desktop 功能区“主页”选项卡中的“获取数据”旁的下拉箭头   ，然后从“最常用”下拉列表选择“Excel”   。 
   
   ![获取数据](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >你还可以选择“获取数据”  项本身，或者从 Power BI“开始”对话框中选择“获取数据”   ，再在“获取数据”对话框中选择“Excel”  或“文件”   > “Excel”   ，然后选择“连接”  。
   
3. 在“打开”  对话框中，导航到 Products.xlsx 文件并选择  该文件，然后选择“打开”  。
   
4. 在**导航器**窗格中，选择 **Products** 表，然后选择**编辑**。
   
   ![Excel 的导航器窗格](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
表的预览将在“Power Query 编辑器”中打开  ，你可以在其中应用转换以清理数据。 
   
![Power Query 编辑器](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>你也可以通过以下方法打开 Power Query 编辑器  ：从 Power BI Desktop 中的“主页”功能区选择“编辑查询”   > “编辑查询”   ，或者右键单击或选择报表视图中任何查询旁的“更多选项”   ，然后选择“编辑查询”  。

## <a name="clean-up-the-products-columns"></a>清理产品列

合并的报表将仅使用 Excel 工作簿中的“ProductID” **、** “ProductName”  、“QuantityPerUnit”  和“UnitsInStock”  列，以便可以删除其他列。 

1. 在 Power Query 编辑器  中，选择“ProductID”  、“ProductName”  、“QuantityPerUnit”  和“UnitsInStock”  列（通过按住 Ctrl  +单击  来选择多个列，或按住 Shift  并单击  来选择相邻的列）。
   
2. 右键单击任何所选标题并从下拉列表中选择“删除其他列”  以删除表中除所选列之外的所有列。 
   你还可以从“主页”  功能区选项卡中的“管理列”  组中选择“删除列”   > “删除其他列”  。 
   
   ![删除其他列](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>从 OData 源导入订单数据

接下来，从示例 Northwind 销售系统 OData 源导入订单数据。 

1. 在 Power Query 编辑器  中，选择“新源”  ，然后从“最常用”  下拉列表中选择“OData 源”  。 
   
   ![获取 OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. 在“OData 源”  对话框中，粘贴 Northwind OData 源的 URL`http://services.odata.org/V3/Northwind/Northwind.svc/`，然后选择“确定”  。
   
   ![OData 源对话框](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. 在“导航器”  窗格中，选择“订单”  表，然后选择“确定”  将数据加载到 Power Query 编辑器  。
   
   ![OData 的导航器窗格](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >在导航器中  ，选择任何表名称即可查看预览，而不必选中复选框。

## <a name="expand-the-order-data"></a>展开订单数据

当连接到具有多个表的数据源（例如关系数据库或 Northwind OData 源）时，可以使用表之间的引用生成查询。 “订单”  表包含对多个相关表的引用。 通过使用“展开”  操作，可以将相关“Order_Details”表  中的“ProductID”  、“UnitPrice”  和“数量”  列添加到主题（“订单”  ）表。 

1. 在“订单”  表中向右滚动，直到可以看到“Order_Details”  列。 请注意，它包含对另一个表的引用，而不是数据。
   
   ![Order_Details 列](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. 选择“Order_Details”  列标题中的“展开”  图标（展开图标![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)）。 
   
3. 在**展开**下拉列表中：
   
   1. 选择 **（选择所有列）** 以清除所有列。
      
   2. 选择“ProductID”  、“UnitPrice”  和“数量”  ，然后选择“确定”  。
      
      ![展开对话框](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

在展开“Order_Details”表后  ，“Order_Details”  列被嵌套表中的三个新列替换，并且从每个订单添加的数据表中都有新行。 

![展开的列](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>创建自定义的计算列

Power Query 编辑器可以用来创建计算和自定义字段以丰富你的数据。 你将创建自定义列，该列通过用单价乘以项数量来计算订单中每个行项的总价格。

1. 在 Power Query 编辑器的“添加列”  功能区选项卡中，选择“自定义列”  。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. 在“自定义列”  对话框中，在“新列名”字段中键入“LineTotal”   。

3. 在 = 后的“自定义列公式”  字段  中，输入 [Order_Details.UnitPrice]  \* [Order_Details.Quantity]  。 （你还可以从可用列  滚动框中选择字段名称，然后选择“<< 插入”  ，而不是键入它们。） 
3. 选择**确定**。
   
   ![自定义列对话框](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

新“LineTotal”  字段显示为“订单”表中的最后一列  。

## <a name="set-the-data-type-for-the-new-field"></a>设置新字段的数据类型

当 Power Query 编辑器连接到数据时，它确定每个字段的最佳数据类型，并相应地显示数据。 你可以通过标题中的图标，或在“主页”功能区选项卡的“转换”组中的“数据类型”    下，查看分配给字段的数据类型。 

新“LineTotal”列包含的数据类型为“任何”   ，但其值是货币。 要分配数据类型，请右键单击“LineTotal”  列标题，从下拉列表中选择“更改数据类型”  ，然后选择“定点十进制数”  。 

![更改数据类型](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>你还可以选择“LineTotal”  列，选择“主页”功能区选项卡的“转换”区域中“数据类型”旁的向下箭头    ，然后选择“定点十进制数”  。

## <a name="clean-up-the-orders-columns"></a>清理订单列

若要在报表中更轻松地使用模型，可以删除、重命名和重新排序某些列。

报表将仅使用“OrderDate”  、“ShipCity”  、“ShipCountry”  、“Order_Details.ProductID”  、“Order_Details.UnitPrice”  和“Order_Details.Quantity”  列。 可以像对 Excel 数据那样选择这些列并使用“删除其他列”  ，或者可以选择除列出列之外的所有列，右键单击所选列之一并选择“删除列”  删除它们。 

可以通过删除列名称的“Order_Details.”前缀  ，更轻松地识别“Order_Details.ProductID”  、“Order_Details.UnitPrice”  和“Order_Details.Quantity”  列。 若要将列分别重命名为“ProductID”  、“UnitPrice”  和“Quantity”  ，请执行下列操作：

1. 双击或者点击并按住每个列标题，或者右键单击列标题并从下拉列表中选择“重命名”  。 
2. 删除每个名称的“Order_Details.”  前缀，然后按 Enter  。

最后，若要更轻松地访问“LineTotal”  列，将其向左拖动，放到紧靠“ShipCountry”列的右侧  。

![清理表](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>查看查询步骤

在“Power Query 编辑器”中修整并转换数据后，每个步骤都记录到“Power Query 编辑器”右侧“查询设置”  窗格的“应用的步骤”  区域。 可以通过“应用的步骤”返回以查看所做的更改，并视需要编辑、删除或重新排列它们（尽管这样做可能存在风险，因为更改前面的步骤可能会中断后续步骤）。 

在 Power Query 编辑器左侧的“查询”列表中选择每个查询  ，在“查询设置”中查看“应用的步骤”   。 在应用以前的数据转换之后，两个查询的“应用的步骤”应如下所示：

![产品查询应用的步骤](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![订单查询应用的步骤](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>基本的“应用的步骤”是以 Power Query 语言  编写的公式，也称为 M  语言。 若要查看和编辑该公式，请选择功能区“主页”选项卡“查询”  组中的“高级编辑器”  。 

## <a name="import-the-transformed-queries"></a>导入转换的查询

如果对转换的数据感到满意，请在“主页”  功能区选项卡的“关闭”  组中选择“关闭并应用”   > “关闭并应用”  ，以将数据导入 Power BI Desktop“报表”视图。 

![关闭并应用](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

数据加载后，查询将出现在 Power BI Desktop“报表”视图的“字段”  列表中。

![字段列表中的查询](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>管理数据集之间的关系

Power BI Desktop 不需要合并查询来建立报表。 但是，你可以使用数据集之间的关系，基于它们共有的字段，扩展并丰富报表。 Power BI Desktop 可以自动检测关系，或者你可以在 Power BI Desktop“管理关系”  对话框中创建关系。 有关 Power BI Desktop 中的关系的更多详细信息，请参阅[创建并管理关系](desktop-create-and-manage-relationships.md)。

本教程中的“订单”和“产品”数据集共享公共“ProductID”  字段，因此基于该列在它们之间存在一定的关系。 

1. 在 Power BI Desktop“报表”视图中，在“主页”功能区选项卡的“关系”区域中选择“管理关系”    。
   
   ![管理关系功能区](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. 在“管理关系”  对话框中，注意 Power BI Desktop 已检测并列出“产品”和“订单”表之间的活动关系。 若要查看关系，请选择“编辑”  。 
   
   ![管理关系对话框](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   “编辑关系”  对话框打开，其中显示有关关系的详细信息。  
   
   ![编辑关系对话框](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. Power BI Desktop 已正确自动探测到关系，因此你可以选择“取消”  ，然后选择“关闭”  以退出关系对话框。

你还可以通过选择 Power BI Desktop 窗口左侧的“关系”  视图，查看并管理查询之间的关系。 双击连接两个查询的线上的箭头，以打开“编辑关系”  对话框并查看或更改关系。 

![关系视图](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

若要从“关系”视图返回到“报表”视图，选择“报表视图”  图标。 

![报表视图图标，](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>使用数据创建可视化效果

在 Power BI Desktop“报表”视图中，可以创建多种可视化效果，以深入探索你的数据。 你可以生成多页报表，而且每页可以有多个视觉效果。 你可以与他人就可视化效果进行交互，以帮助分析和了解你的数据。 有关查看和编辑 Power BI 服务（站点）中的报表的详细信息，请参阅[编辑报表](service-interact-with-a-report-in-editing-view.md)。

可以利用这两个数据集以及它们之间的关系，帮助可视化和分析销售数据。 

首先，创建堆积柱形图，该图使用这两个查询的字段来显示每个订购产品的数量。 

1. 从右侧“字段”窗格中的“订单”选择“数量”字段    ，或将其拖到画布上的空白区域。 这将创建一个显示所有订购产品的总数量的堆积柱形图。 
   
2. 从“字段”窗格中的“产品”选择“ProductName”    ，或将其拖放到图表，以显示每个订购产品的量排序。 
   
3. 若要按从最多订购到最少订购对产品排序，选择可视化效果右上角的“更多选项”  省略号 (...  )，然后选择“按数量排序”  。
   
4. 使用图表角部的图柄进行放大，使更多产品名称可见。 
   
   ![按 ProductName 显示数量条形图](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

接下来，创建一个图，显示随时间推移 (OrderDate  ) 的订单美元金额 (LineTotal  )。 

1. 在画布上未选择任何对象的情况下，从“字段”窗格中的“订单”选择“LineTotal”    ，或者将其拖到画布上的空白区域。 堆积柱形图显示所有订单的总美元金额。 
   
2. 在选择该图表的情况下，从“订单”选择“OrderDate”   ，或将其拖到该图表。 该图表现在显示每个订单日期的行合计。 
   
3. 通过拖动角调整可视化效果的大小，以便能够看到更多数据。 
   
   ![按 OrderDate 显示 LineTotals 折线图](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >如果你只在图表上看到“年份”（只有三个数据点），下拉“可视化效果”窗格的“轴”字段中“OrderDate”旁的箭头    ，然后选择“OrderDate”  而不是“日期层次结构”  。 

最后，创建显示每个国家/地区的订单数量的地图可视化效果。 

1. 在画布上未选择任何对象的情况下，从“字段”窗格中的“订单”选择“ShipCountry”    ，或者将其拖到画布上的空白区域。 Power BI Desktop 检测到数据是国家/地区名称，将自动创建地图可视化效果，针对具有订单的每个国家/地区显示一个数据点。 
   
2. 若要使数据点的大小反映每个国家/地区的订购量，将“LineTotal”  字段拖动到地图上（或将其拖动到“可视化效果”窗格下半部分中“大小”下的“将数据字段拖动到此处”    ）。 现在，地图上的圆圈大小反映每个国家/地区的订单美元金额。 
   
   ![按 ShipCountry 显示 LineTotals 地图可视化效果](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>与报表视觉效果进行交互以进一步分析

Power BI Desktop 使你可以与相互突出显示和筛选的视觉效果进行交互，从而发觉进一步的趋势。 有关详细信息，请参阅[在报表中进行筛选和突出显示](power-bi-reports-filters-and-highlighting.md)。 

由于查询之间的关系，与一个可视化效果交互将影响页上的所有其他可视化效果。 

在地图可视化效果中，选择“加拿大”  中间的圆圈。 请注意，其他两个可视化效果进行筛选，以仅突出显示加拿大的行总计和订单数量。

![为加拿大筛选的销售数据](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

如果在“按 ProductName 显示数量”图表中选择产品之一  ，则地图和日期图表进行筛选以反映该产品的数据；如果在“按 OrderDate 显示 LineTotal”图表中选择日期之一  ，则地图和产品图表进行筛选以显示该日期的数据。 
>[!TIP]
>若要取消选择所选内容，再次选择它，或者选择其他可视化效果之一。 

## <a name="complete-the-sales-analysis-report"></a>完成销售分析报表

完成的报表对 Products.xlsx Excel 文件与视觉对象中 Northwind OData 源的数据进行组合，帮助分析不同国家/地区、时间范围和产品的订单信息。 报表准备就绪后，可以[将其上传到 Power BI 服务](desktop-upload-desktop-files.md)，将其与其他 Power BI 用户共享。

## <a name="next-steps"></a>后续步骤
* [阅读其他 Power BI Desktop 教程](http://go.microsoft.com/fwlink/?LinkID=521937)
* [观看 Power BI Desktop 视频](http://go.microsoft.com/fwlink/?LinkID=519322)
* [访问 Power BI 论坛](http://go.microsoft.com/fwlink/?LinkID=519326)
* [阅读 Power BI 博客](http://go.microsoft.com/fwlink/?LinkID=519327)
---
title: 教程：从维度模型变为 Power BI Desktop 中的出色报表
description: 跟随本教程，你可以从维度模型入手，在 20 分钟内从头开始生成精美的报表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/11/2021
LocalizationGroup: Reports
ms.openlocfilehash: f5d35d7fc189f055a6f51e493fd313eb31f0564f
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565977"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>教程：从维度模型变为 Power BI Desktop 中的出色报表 

跟随本教程，你可以从维度模型入手，在 45 分钟内从头开始生成精美的报表。

你在 AdventureWorks 工作，而你的经理想要查看有关最新销售数据的报表。 经理要求提供关于以下内容的执行摘要： 

- 2019 年 2 月哪一天的销售额最高？ 
- 公司在哪个国家/地区取得了最大的成功？ 
- 公司应继续投资于哪些产品类别和经销商业务类型？ 

借助我们的 [AdventureWorks Sales 示例 Excel 工作簿](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx)，我们可以立即生成此报表。 下面是最终报表的外观。 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="完成的 AdventureWorks 报表。":::

想要查看成品？ 你还可以下载[完整的 Power BI .pbix 文件](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)。

让我们开始吧！ 

在本教程中，将了解如何：

> [!div class="checklist"]
> * 使用少量转换来准备数据
> * 生成包含标题、三个视觉对象和切片器的报表
> * 将报表发布到 Power BI 服务，以便与同事共享

## <a name="prerequisites"></a>先决条件

- 在开始之前，你需要[下载 Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)。 
- 如果你打算将报表发布到 Power BI 服务而尚未注册，请[注册免费试用版](../fundamentals/service-self-service-signup-for-power-bi.md)。 

## <a name="get-data-download-the-sample"></a>获取数据：下载示例 

1. 下载 [AdventureWorks Sales 示例 Excel 工作簿](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx)。 

1. 打开 Power BI Desktop。 

1. 在“开始”功能区的“数据”部分，选择“Excel”  。 

1. 导航到保存示例工作簿的位置，然后选择“打开”。 

## <a name="prepare-your-data"></a>准备数据 

在“导航器”窗格中，可以选择转换 ** 或加载 ** 数据  。 导航器提供数据预览，以便你可以验证数据范围是否正确。 数值数据类型显示为斜体。 在本教程中，我们将在加载前转换数据。

选择所有表，然后选择“转换数据” **** 。 确保不要选择工作表（标有 _data）。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="在导航器中加载表。":::

检查列的数据类型是否与下表中的数据类型匹配。 若要进行任何更改，请选择一个查询，然后选择一列或多列。

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="检查列的数据类型。":::

在“主页”选项卡上，选择“数据类型”，然后从表中选择适当的数据类型。

|查询  |列  |数据类型  |
|---------|---------|---------|
|客户  |  CustomerKey | 整数 |
|Date | DateKey |    整数     |
|     | Date | Date      |
|     | MonthKey  | 整数 |
|产品  | ProductKey | 整数  | 
|     | 标准成本 | 十进制数  | 
|     | 标价 | 十进制数  | 
|Reseller  | ResellerKey | 整数  | 
|Sales   | SalesOrderLineKey | 整数  | 
|     | ResellerKey  | 整数  | 
|     | CustomerKey | 整数  | 
|     | ProductKey  | 整数  | 
|     | OrderDateKey | 整数  | 
|     | DueDateKey  | 整数  | 
|     | ShipDateKey | 整数  | 
|     | SalesTerritoryKey | 整数  | 
|     | Order Quantity   | 整数  | 
|     | Unit Price  | 十进制数  | 
|     | Extended Amount  | 十进制数  | 
|     | Unit Price Discount Pct | 百分比  | 
|     | Product Standard Cost | 十进制数  | 
|     | Total Product Cost | 十进制数  | 
|     | Sales Amount | 十进制数  | 
| SalesTerritory  | SalesTerritoryKey | 整数  | 
|  订单   |  SalesOrderLineKey | 整数  | 

返回“主页” **** 选项卡，选择“关闭并应用” ****  。 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="Power Query 的“关闭并应用”按钮。":::

## <a name="model-your-data"></a>为你的数据建模 

加载的数据基本已经可用于报表。 让我们检查数据模型并进行一些更改。 

选择左侧的模型视图。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="在 Power BI Desktop 中选择模型视图。":::

数据模型应如下图所示，每个表都在一个方框中。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="用于开始的数据模型。":::

### <a name="create-relationships"></a>创建关系

此模型是你可能会在数据仓库中看到的典型星型架构：它像一颗星星。 星星的中心是事实数据表。 周围的表称为维度表，它们通过关系与事实数据表关联。 事实数据表包含有关销售事务的数字信息，例如销售额和产品标准成本。 维度提供上下文，因此可以进行以下分析： 

- 销售了哪个产品... 
- 销售给哪个客户... 
- 由哪个经销商销售... 
- 在哪个销售区域销售。  

如果仔细观察，你会发现除 Date 表外，所有维度表都通过某种关系与事实数据关联。 现在，让我们向 Date 添加一些关系。 将 DateKey 从 Date 表拖放到 Sales 表上的 OrderDateKey。 你已创建从 Date 到 Sales 的所谓“一对多”关系，由线条两端的 1 和星号 *（多）表示。  

该关系为“一对多”关系是因为给定日期有一个或多个销售订单。 如果每个日期只有一个销售订单，则该关系将为“一对一”关系。 线条中间的小箭头指示“交叉筛选方向”。 它指示可以使用 Date 表中的值来筛选 Sales 表，因此，该关系允许分析销售订单的下单日期。  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Sales 表和 Date 表之间的关系。":::

Sales 表包含有关与销售订单相关的日期的详细信息，例如截止日期和发货日期。 让我们通过拖动将另外两个关系添加到 Date 表： 

- DateKey 到 DueDateKey 
- DateKey 到 ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Sales 表和 Date 表之间的三个关系。":::

你会注意到，OrderDateKey 上的第一个关系处于活动状态，由实线表示。 其他两个关系处于非活动状态，由虚线表示。 默认情况下，Power BI 使用活动关系来关联 Sales 和 Date。 因此，SalesAmount 的总和按订单日期（而不是截止日期或发货日期）计算。 你可以影响此行为。 请参阅本教程稍后部分的[加分做法：使用 DAX 编写度量值](#extra-credit-write-a-measure-in-dax)。

### <a name="hide-key-columns"></a>隐藏键列

典型的星型架构包含多个保存事实数据和维度之间的关系的键。 通常情况下，我们不会在报表中使用键列。 让我们在视图中隐藏键列，以使字段列表显示的字段更少，且数据模型更易于使用。 

浏览所有表并隐藏名称以 Key 结尾的所有列： 

选择列旁边的眼睛图标，然后选择“在报表视图中隐藏”。

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="带眼睛图标的可见列。":::

还可以在“属性”窗格中选择列旁边的眼睛图标。

隐藏字段具有此图标，即眼睛上有一条线穿过。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="带隐藏眼睛图标的字段。":::
 
隐藏这些字段。

|表  |列  |
|---------|---------|
|客户  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|产品     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| 订单    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

你的数据模型现在应类似此数据模型，其中 Sales 和所有其他表之间的关系以及所有键字段都已隐藏： 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="具有隐藏键列的数据模型。":::

### <a name="create-hierarchies"></a>创建层次结构

现在，由于隐藏的列，我们的数据模型变得更易于使用，接下来我们可以添加一些层次结构让模型更加易于使用。 通过层次结构，可以更轻松地浏览分组。 例如，市在州或省中，而州或省在国家或地区中。 

创建以下层次结构。 

1. 右键单击层次结构中最高级别或最小粒度的字段，然后选择“创建层次结构”。 

1. 在“属性”窗格中，设置层次结构的“名称”并设置级别。 

1. 然后“应用级别更改”。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="层次结构“属性”窗格。":::

添加后，还可以在“属性”窗格中重命名层次结构的级别。 你需要在 Date 表中重命名 Fiscal 层次结构的 Yea 和 Quarter 级别。 

以下是需要创建的层次结构。

| 表 |层次结构名称 |级别  |
|---------|---------|---------|
|客户     | 地理位置   | 国家/地区  |
|     | | 省/市/自治区  |
|     |         | 城市 |
|Row4     |         | 邮政编码 |
|Row5     |         | 客户   |
|日期     | Fiscal  | Year (Fiscal Year)  |
|     |         | Quarter (Fiscal Quarter) |
|     |         | 月份 |
|     |         | 日期 |
| Product  | 产品 | 类别 |
|     |         | Subcategory |
|     |         | 建模 |
|     |         | Product |
| Reseller   | 地理位置 | 国家/地区 |
|     |         | 省/市/自治区 |
|     |         | 城市  |
|     |         | 邮政编码  |
|     |         | Reseller |
| 订单  | Sales Orders | 销售订单 |
|     |         | 销售订单行 |
| SalesTerritory    | Sales Territories | Group |
|     |         | Country |
|     |         | 区域 |
 
你的数据模型现在应类似以下数据模型。 它具有相同的表，但每个维度表都包含一个层次结构： 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="具有带层次结构的维度表的数据模型。":::

### <a name="rename-tables"></a>重命名表

若要完成建模，请在“属性”窗格中重命名以下表： 

|旧表名称  |新表名称  |
|---------|---------|
|SalesTerritory    |  销售区域   |
|订单  |  销售订单   |

此步骤是必需的，因为 Excel 表名称不能包含空格。

现在，最终数据模型已准备就绪。

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="具有重命名的表的完整数据模型。":::

## <a name="extra-credit-write-a-measure-in-dax"></a>加分做法：使用 DAX 编写度量值 

对于数据建模而言，使用 DAX 公式语言编写度量值的功能非常强大。 [Power BI 文档中有很多关于 DAX 的知识](/dax/)。 现在，让我们编写一个基本度量值，其按销售订单上的截止日期（而不是默认订购日期）来计算总销售额。 此度量值使用 [USERELATIONSHIP 函数](/dax/userelationship-function-dax)在度量值上下文中激活 Sales 和 Date on DueDate 之间的关系。 然后，它使用 [CALCULATE](/dax/calculate-function-dax) 在该上下文中计算销售额的总和。

1. 选择左侧的数据视图。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="选择左侧的数据视图。":::

1. 在“字段”列表中选择 Sales 表。

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="在“字段”列表中选择 Sales 表。":::

1. 在“主页” **** 功能区中，选择“新建度量值” ****  。 

1. 选择或键入此度量值，以按销售订单上的截止日期（而不是默认订购日期）来计算总销售额：

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. 选中复选标记以提交。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="选中复选标记以提交 DAX 度量值。":::

## <a name="build-your-report"></a>生成报表 

现在，你已对数据建模，接下来可以创建报表。 转到报表视图。 在右侧的“字段”窗格中，可以看到创建的数据模型中的字段。

让我们为视觉对象逐一生成最终报表。 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="完成的报表，每个视觉对象均标有数字":::

### <a name="visual-1-add-a-title"></a>视觉对象 1：添加标题 

1. 在“插入”功能区中选择“文本框” 。 键入“Executive Summary - Sales Report”。 

1. 选择键入的文本。 将字号设置为“20”并“加粗”。 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="设置 Executive Summary 文本的格式。":::

1. 在“可视化效果”窗格中，将“背景”切换为“关” 。 

1. 调整框的大小，使其显示在一行内。 

### <a name="visual-2-sales-amount-by-date"></a>视觉对象 2：按日期列出的销售额 

接下来，你将创建一个折线图，以查看哪个月份和年份的销售额最高。

1. 在“字段”窗格中，将“Sales Amount”字段从“Sales”表拖到报表画布上的空白区域。 默认情况下，Power BI 显示带有一列（即“Sales Amount”）的柱形图。 

1. 将“Month”字段从“Date”表中的“Fiscal”层次结构拖放到柱形图。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="创建每年对应一列的柱形图。":::

1. 在“可视化效果”窗格的“字段”部分，删除“Year”和“Quarter”字段： 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="在“可视化效果”窗格的“字段”部分，删除“Year”和“Quarter”字段。":::

1. 在“可视化效果”窗格中，将可视化类型更改为“分区图”。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="将柱形图更改为分区图。":::

1. 如果在上文的加分做法中添加了 DAX 度量值，也将其添加到“值”中。 
1. 打开“格式”窗格，然后打开“数据颜色”，并将“Sales Amount by Due Date”的颜色更改为更具对比度的颜色，例如红色。

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="Sales Amount by Due Date 分区图。":::

    如你所见，Sales Amount by Due Date 略落后于 Sales Amount。 这证明它使用了使用 DueDateKey 的 Sales 和 Date 表之间的关系。 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>视觉对象 3：按经销商国家/地区列出的订单数量 

现在，我们将创建一个地图，以查看经销商在哪个国家/地区拥有最高订购数量金额。

1. 在“字段”窗格中，将“Country-Region”字段从“Reseller”表拖到报表画布上的空白区域。 Power BI 创建地图。 

1. 从“Sales”表将“Order Quantity”字段拖放到地图上。 确保“Country-Region”在“Location”井中，且“Order Quantity”在“Size”井中。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="按国家/地区列出的订单数量地图。":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>视觉对象 4：按产品类别和经销商业务类型列出的销售额 

接下来，我们将创建一个柱形图，以调查哪些产品由哪些经销商业务类型销售。

1. 将你创建的两个图表并排拖动到画布的上半部分。 在画布的左侧保留一些空间。 

1. 在报表画布的下半部分选择一个空白区域。 

1. 在“字段”窗格中，从“Sales”中选择“Sales Amount”，从“Product”中选择“Product Category”，并从“Reseller”中选择“Business Type”。 

    Power BI 会自动创建簇状柱形图。 将可视化效果更改为“矩阵”： 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="将簇状柱形图更改为矩阵。":::

1. 在矩阵仍处于选中状态的情况下，在“筛选器”窗格中的“Business Type”下“全选”，然后取消选中“[不适用]”框。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="筛选出不适用的业务类型。":::

1. 拖动矩阵，使其足够宽以填充上方两个图表下方的空间。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="加宽矩阵以填充报表。":::

1. 在矩阵的“格式设置”窗格中，打开“条件格式设置”部分，然后打开“数据条”。 选择“高级控件”，然后为正值数据条设置较浅的颜色。 选择“确定”。 

1. 增加“Sales Amount”列的宽度，使其覆盖整个区域。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="带 Sales Amount 数据条的矩阵。":::

自行车的总销售额似乎较高，增值经销商的销售额最高，其次是仓库。 对于“组件”，仓库的销售额超过增值经销商。 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>视觉对象 5：会记日历切片器 

切片器是一种有价值的工具，可用于将报表页面上的视觉对象筛选为特定的一部分。 在本例中，我们可以创建一个切片器来缩小显示范围，仅显示每月、每季度和每年的业绩。 

1. 在“字段”窗格中，从“Date”表中选择“Fiscal”层次结构，并将其拖到画布左侧的空白区域。 

1. 在“可视化效果”窗格中，选择“切片器”。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="添加 Sales 报表日历切片器。":::

1. 在“可视化效果”窗格的“字段”部分，删除“Quarter”和“Date”，只留下“Year”和“Month”。 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="从 Fiscal 切片器中删除 Quarter 和 Date。":::

现在，如果经理要求仅查看特定月份的数据，则可以使用切片器在年份或每年的特定月份之间进行切换。 

## <a name="extra-credit-format-the-report"></a>加分做法：设置报表格式 

如果要对此报表进行少量格式设置以进行润色，请执行以下几个简单步骤。 

### <a name="theme"></a>主题 

- 在“视图” ****  功能区中，选择“主题”，然后将主题更改为“Executive” **** 。 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="选择“Executive”主题。":::

### <a name="spruce-up-the-visuals"></a>修饰视觉对象 

在“可视化效果”窗格的“格式” **** 选项卡中进行以下更改 。 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="“可视化效果”窗格中“格式”选项卡的屏幕截图。":::

**视觉对象 2，Sales Amount by Order Date**

1. 选择“视觉对象 2，Sales Amount by Order Date”。 
1. 在“标题” **** 部分，如果未添加 DAX 度量值，则将“标题文本” **** 更改为“Sales Amount by Order Date” 。 

    如果已添加 DAX 度量值，则将“标题文本”更改为“Sales Amount by Order Date/Due Date”。 

1. 将“文本大小”设置为“16 磅” **** 。 
1. 将“阴影” **** 切换为“开” ****  。 

**视觉对象 3，Order Quantity by Reseller Country**

1. 选择“视觉对象 3，Order Quantity by Reseller Country”。 
1. 在“地图样式” **** 部分，将“主题” **** 更改为“灰度” ****   。 
1. 在“标题” **** 部分，将“标题文本”更改为“Order Quantity by Reseller Country” 。
1. 将“文本大小”设置为“16 磅” ****  。 
1. 将“阴影” **** 切换为“开” ****  。  

**视觉对象 4，Sales Amount by Product Category and Reseller Business Type**

1. 选择“视觉对象 4，Sales Amount by Product Category and Reseller Business Type”。 
1. 在“标题” **** 部分，将“标题文本”更改为“Sales Amount by Product Category and Reseller Business Type” 。
1. 将“文本大小”设置为“16 磅” ****  。 
1. 将“阴影” **** 切换为“开” ****  。 

**视觉对象 5，会计日历切片器**

1. 选择“视觉对象 5，会计日历切片器”。
1. 在“选择控件” **** 部分，将“显示‘全选’” **** 选项切换为“开” ****  。 
1. 在“切片器标题” **** 部分，将“文本大小”设置为“16 磅” ****   。 

### <a name="add-a-background-shape-for-the-title"></a>为标题添加背景形状 

1. 在“插入” **** 功能区中，选择“形状” **** >“矩形” ****  。 
1. 将其放在页面顶部，然后将其拉伸为页面的宽度和标题的高度。 
1. 在“设置格式形状” **** 窗格的“行” **** 部分，将“透明度” **** 更改为“100%” ****    。 
1. 在“填充” **** 部分，将“填充颜色” **** 更改为“主题颜色 5 #6B91C9 (蓝色)” ****   。 
1. 在“格式” ****  选项卡中，选择“下移一层” **** >“置于底层” ****  。 
1. 选择视觉对象 1 中标题的文本，然后将“字体颜色”更改为“白色” **** 。 

## <a name="finished-report"></a>完成的报表 

在切片器中选择“FY2019”。

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="最终完成的报表。":::

总的来说，此报表回答了你经理提出的主要问题： 

- 2019 年 2 月哪一天的销售额最高？ 
    2 月 25 日，销售额为 253,915.47 美元。 

- 公司在哪个国家/地区取得了最大的成功？ 
    在美国，订单数量为 132,748。 

- 公司应继续投资于哪些产品类别和经销商业务类型？ 
    公司应继续投资于 Bikes 类别以及 Added Reseller 和 Warehouse 经销商业务。 

## <a name="save-your-report"></a>保存报表 

- 在“文件” **** 菜单中，选择“保存” ****  。 


## <a name="publish-to-the-power-bi-service-to-share"></a>发布到 Power BI 服务以便共享 

若要与经理和同事共享你的报表，请将其发布到 Power BI 服务。 当你与拥有 Power BI 帐户的同事共享时，他们可以与你的报表进行交互，但是无法保存更改。

1. 在 Power BI Desktop 中，在“主页” **** 功能区中选择“发布” ****  。 
1. 你可能需要登录 Power BI 服务。 如果还没有帐户，请 [注册免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)。 

1. 在 Power BI 服务中选择一个目标（例如“我的工作区”），然后选择“选择” **** 。 

1. 选择“在 Power BI 中打开‘你的文件名’” **** 。 已完成的报表将在浏览器中打开。 

1. 选择报表顶部的“共享” **** ，将报表与他人共享 。

## <a name="next-steps"></a>后续步骤 

- 下载[完整的 Power BI .pbix 文件](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)
- 详细了解 [Power BI Desktop 中的 DAX 和数据建模](/learn/modules/dax-power-bi-models/)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

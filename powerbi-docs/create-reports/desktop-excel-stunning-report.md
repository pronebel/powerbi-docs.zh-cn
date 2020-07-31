---
title: 教程：从 Excel 工作簿变为 Power BI Desktop 中的出色报表
description: 本教程介绍如何通过 Excel 工作簿快速创建出色的报表。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 07/21/2020
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: b628502ad5658388065a197c1c722a59dd9ad2b4
ms.sourcegitcommit: e9cd61eaa66eda01cc159251d7936a455c55bd84
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972731"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>教程：从 Excel 工作簿变为 Power BI Desktop 中的出色报表

跟随本教程，你可以在 20 分钟内从头开始生成精美的报表！ 

你的经理想要查看有关最新销售额的报表。 经理要求提供关于以下内容的执行摘要： 

- 哪年哪月的利润最大？ 
- 公司在哪个国家/地区取得了最大的成功？ 
- 公司应继续投资哪些产品和细分市场？ 

使用我们的示例财务工作簿，我们可以立即生成此报表。 下面是最终报表的外观。 让我们开始吧！ 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Power BI 服务中的 Power BI 报表的屏幕截图。"::: 

在本教程中，将了解如何：

> [!div class="checklist"]
> * 下载示例数据
> * 使用少量转换来准备数据
> * 生成包含标题、三个视觉对象和切片器的报表
> * 将报表发布到 Power BI 服务，以便与同事共享

## <a name="prerequisites"></a>先决条件

- 在开始之前，你需要[下载 Power BI Desktop](https://powerbi.microsoft.com/desktop/)。
- 如果你打算将报表发布到 Power BI 服务而尚未注册，请[注册免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)。

## <a name="download-the-sample"></a>下载示例

若要跟随操作，需要下载示例工作簿。 

1. 下载[财务示例 Excel 工作簿](https://go.microsoft.com/fwlink/?LinkID=521962)。
1. 打开 Power BI Desktop。
1. 在“开始”功能区的“数据”部分，选择“Excel”  。
1. 导航到保存示例工作簿的位置，然后选择“打开”。

## <a name="prepare-your-data"></a>准备数据 

在“导航器”中，可以选择“转换”或“加载”数据 。 导航器提供数据预览，以便你可以验证数据范围是否正确。 数值数据类型显示为斜体。 如果需要进行更改，请在加载数据前转换数据。 为了使可视化效果在稍后更易于阅读，我们希望立即转换数据。 进行每次转换时，你会看到它已添加到“应用步骤”中“查询设置”下的列表中  

1. 选择“财务”表，然后选择“转换数据” 。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="带有财务示例数据的 Power BI 导航器的屏幕截图。"::: 

1. 选择“销售量”列。 在“开始”选项卡上，选择“数据类型”，然后选择“整数”  。 选择“替换当前”以更改列类型。 

    用户最常执行的最重要的数据清理步骤是更改数据类型。 在本例中，销售量为小数形式。 销售量为 0.2 或 0.5 毫无意义，对吧？ 因此，我们将其更改为整数。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="将小数改为整数的屏幕截图。"::: 

1. 选择“细分市场”列。 在“转换”选项卡上，选择“格式”，然后选择“大写”  。

    我们还希望使这些细分市场稍后在图表中更易于查看。 我们来设置“细分市场”列的格式。 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="将小写标题更改为大写标题的屏幕截图。":::

1. 让我们将列名从“月份名称”缩短为“月份” 。 双击“月份名称”列，然后将其重命名为“月份” 。  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="缩短列名的屏幕截图。":::

1. 在“产品”列中，选择下拉列表，并取消选中“Montana”旁边的框 。 

     我们知道 Montana 产品在上个月已停产，因此我们希望从报表中筛选掉该数据，以避免混淆。 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="删除 Montana 值的屏幕截图。":::

1. 你会看到每个转换都已添加到“应用步骤”中“查询设置”下的列表中 。

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="应用步骤列表的屏幕截图。":::

1. 返回“开始”选项卡，选择“关闭并应用” 。 数据即将可用于生成报表。 

    “字段”列表中显示 Sigma 符号？ Power BI 检测到这些字段为数值字段。 Power BI 还使用日历符号指示日期字段。

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="包含数值字段和日期字段的字段列表的屏幕截图。":::

### <a name="extra-credit-write-a-measure-in-dax"></a>加分做法：使用 DAX 编写度量值

对于数据建模而言，使用 DAX 公式语言编写度量值功能非常强大 。 Power BI 文档中有很多关于 DAX 的知识。 现在，让我们编写一个基本度量值并将两个表联接起来。 

1. 选择左侧的“数据视图”。 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="“数据视图”图标的屏幕截图。":::

1. 在“开始”功能区中选择“新建表格” 。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="“新建表格”图标的屏幕截图。":::

1. 键入此度量值以生成一个日历表，日期范围介于 2013 年 1 月 1 日至 2014 年 12 月 31 日之间。  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. 选中复选标记以提交。

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="DAX 表达式的屏幕截图。":::

1. 现在，选择左侧的“模型视图”。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="“模型视图”图标的屏幕截图。":::

1. 将“日期”字段从“财务”表拖到“日历”表中的“日期”字段以联接表，并在它们之间创建关系 。  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="“日期”字段之间的关系的屏幕截图。":::

## <a name="build-your-report"></a>生成报表 

现在，你已经转换并加载了数据，可以创建报表了。 在右侧的“字段”窗格中，可以看到创建的数据模型中的字段。 

让我们为视觉对象逐一生成最终报表。 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="报表的所有元素（按编号排列）的屏幕截图。":::

### <a name="visual-1-add-a-title"></a>视觉对象 1：添加标题 

1. 在“插入”功能区中选择“文本框” 。 键入“执行摘要 - 财务报表”。 
1. 选择键入的文本。 将字号设置为“20”并加粗。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="格式设置标题的屏幕截图。":::

1. 在“可视化效果”窗格中，将“背景”切换为“关” 。 
1. 调整框的大小，使其显示在一行内。 

### <a name="visual-2-profit-by-date"></a>视觉对象 2：按日列出的利润 

现在创建一个折线图，以查看哪年哪月的利润最大。 

1. 从“字段”窗格中，将“利润”字段拖到报表画布上的空白区域。 默认情况下，Power BI 显示带有一列的柱形图（即“利润”）。 
1. 将“日期”字段拖至同一视觉对象。 Power BI 将更新柱形图以显示两年的利润。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="“利润”柱形图的屏幕截图。":::

1. 在“可视化效果”窗格的“字段”部分，选择“轴”值中的下拉列表 。 将“日期”从“日期层次结构”更改为“日期”  。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="将“日期层次结构”更改为“日期”的屏幕截图。":::

    Power BI 将更新柱形图以显示每个月的利润。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="按月份显示的柱形图的屏幕截图。":::

1. 在“可视化效果”窗格中，将可视化效果类型更改为“折线图”。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="将柱形图更改为条形图的屏幕截图。":::

    现在，可以轻松看到 2014 年 12 月的利润最大。

### <a name="visual-3-profit-by-country"></a>视觉对象 3：按国家/地区列出的利润 

创建一个地图，以查看利润最大的国家/地区。

1. 从“字段”窗格将“国家/地区”字段拖到报表画布上的空白区域，以创建一个地图。
1. 将“利润”字段拖到地图中。

    Power BI 将创建一个地图视觉对象，其中的气泡代表每个位置的相对利润。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="创建地图图表的屏幕截图。":::

    欧洲的利润比北美的利润更大。 

### <a name="visual-4-sales-by-product-and-segment"></a>视觉对象 4：按产品和细分市场列出的销售额 

创建条形图以确定要投资的公司和细分市场。

1. 将你创建的两个图表并排拖动到画布的上半部分。 在画布的左侧保留一些空间。 
1. 在报表画布的下半部分选择一个空白区域。 

1. 在“字段”窗格中，选择“销售”、“产品”和“细分市场”字段  。 

    Power BI 会自动创建簇状柱形图。 

1. 拖动图表，使其足够宽以填充上方两个图表下方的空间。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="簇状柱形图的屏幕截图。":::

    看起来公司应该继续投资 Paseo 产品并以小型企业和政府部门为目标消费者。  

### <a name="visual-5-year-slicer"></a>视觉对象 5：年份切片器 

切片器是一种有价值的工具，可用于将报表页面上的视觉对象筛选为特定的一部分。 在本例中，我们可以创建一个切片器来缩小显示范围，仅显示每月和每年的业绩。  

1. 在“字段”窗格中，选择“日期”字段并将其拖到画布左侧的空白区域。 
2. 在“可视化效果”窗格中，选择“切片器”。 
3. 在“可视化效果”窗格的“字段”部分，选择“字段”中的下拉列表。 删除“季度”和“天”，仅保留“年”和“月”。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="更改“日期层次结构”的屏幕截图。":::

4. 展开每年并调整视觉对象的大小，以显示所有月份。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="日期层次结构切片器的屏幕截图。":::

现在，如果经理要求仅查看 2013 年的数据，你可以使用切片器在年份或每年的特定月份之间进行切换。 

### <a name="extra-credit-format-the-report"></a>加分做法：设置报表格式

如果要对此报表进行少量格式设置以进行润色，请执行以下几个简单步骤。 

**主题**

- 在“查看”功能区上，将主题更改为“执行” 。  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="选择“执行”主题的屏幕截图。"::: 

**修饰视觉对象** 

在“可视化效果”窗格的“格式”选项卡上进行以下更改。

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="“可视化效果”窗格中“格式”选项卡的屏幕截图。":::

1. 选择视觉对象 2。 在“标题”部分，将“标题文本”更改为“按月和年划分的利润”，并将“文本大小”更改为“16 磅”   。 将“阴影”切换为“开” 。 

1. 选择视觉对象 3。 在“地图样式”部分，将“主题”更改为“灰度”  。 在“标题”部分，将标题“文本大小”更改为“16 磅”  。 将“阴影”切换为“开” 。

1. 选择视觉对象 4。 在“标题”部分，将标题“文本大小”更改为“16 磅”  。 将“阴影”切换为“开” 。

1. 选择视觉对象 5。 在“选择控件”部分，将“显示‘全选’选项”切换为“开”  。 在“切片器标头”部分，将“文本大小”增加为“16 磅”  。 

**为标题添加背景形状**

1. 在“插入”功能区中，选择“形状” > “矩形”  。 将其放在页面顶部，然后将其拉伸为页面的宽度和标题的高度。 
1. 在“格式形状”窗格的“行”部分，将“透明度”更改为“100％”   。 
1. 在“填充”部分，将“填充颜色”更改为“主题颜色 5 #6B91C9”（蓝色）  。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="主题颜色 5 的屏幕截图。":::

1. 在“格式”选项卡上，选择“下移一层” > “置于底层”  。 
1. 选择视觉对象 1 中的文本，并选择标题，然后将字体颜色更改为“白色”。 

**为视觉对象 2 和 3 添加背景形状**

1. 在“插入”功能区上，选择形状” > “矩形”，并将其拉伸为视觉对象 2 和 3 的宽度和高度  。 
1. 在“格式形状”窗格的“行”部分，将“透明度”更改为“100％”   。 
1. 在“格式”选项卡上，选择“下移一层” > “置于底层”  。 

### <a name="finished-report"></a>完成的报表

最终的精美报表外观如下所示：  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="格式设置后最终报表的屏幕截图。":::

总的来说，此报表回答了你经理提出的主要问题： 

- 哪年哪月的利润最大？ 

    2014 年 12 月 

- 公司在哪个国家/地区取得了最大的成功？ 

    欧洲，特别是法国和德国。 

- 公司应继续投资哪些产品和细分市场？ 

    公司应该继续投资 Paseo 产品并以小型企业和政府部门为目标消费者。 

## <a name="save-your-report"></a>保存报表

- 在“文件”菜单上，选择“保存” 。

## <a name="publish-to-the-power-bi-service-to-share"></a>发布到 Power BI 服务以便共享 

若要与经理和同事共享你的报表，请将其发布到 Power BI 服务。 当你与拥有 Power BI 帐户的同事共享时，他们可以与你的报表进行交互，但是无法保存更改。 

1. 在 Power BI Desktop 的“开始”功能区，选择“发布” 。 

    你可能需要登录 Power BI 服务。 如果还没有帐户，可以注册[免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)。

1. 在 Power BI 服务中选择一个目标（例如“我的工作区”），然后选择“选择” 。
1. 选择“在 Power BI 中打开‘你的文件名’”。

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="在 Power BI 服务中打开报表的屏幕截图。":::

    已完成的报表将在浏览器中打开。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Power BI 服务中的 Power BI 报表的屏幕截图。"::: 

1. 选择报表顶部的“共享”，将报表与他人共享。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="通过 Power BI 服务共享报表的屏幕截图。":::

## <a name="next-steps"></a>后续步骤

- [教程：分析来自 Excel 和 OData 源的销售数据](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)。

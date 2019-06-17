---
title: 立刻从 Excel 工作簿变为出色的报表
description: 立刻从 Excel 工作簿变为出色的报表
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: cd75aebb09c7b6c54c1ff3f68635bfd5033c7f80
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721464"
---
# <a name="from-excel-workbook-to-stunning-report-in-no-time"></a>立刻从 Excel 工作簿变为出色的报表
你的经理在下班前想要查看有关你最新的销售数据以及上一市场活动影响的报表。 但最新数据位于各种第三方系统上以及便携式计算机上的文件中。 以前，创建视觉对象和设置报表格式需要几个小时。 你开始感到焦虑。

别担心。 凭借 Power BI，你可以立刻创建出色的报表。

在此示例中，我们将从本地系统上传 Excel 文件、创建新报表，并将其与同事共享 - 所有操作均在 Power BI 内进行。

## <a name="prepare-your-data"></a>准备数据
让我们以一个简单的 Excel 文件作为示例。 在将 Excel 文件加载到 Power BI 之前，必须在平面表中组织数据。 这意味着每一列都包含相同的数据类型 - 例如，文本、日期、数字或货币。 应该有一个标题行，但不应存在任何显示总数的列或行。

![在 Excel 中组织的数据](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

接下来，将数据格式设置为表格。 在 Excel 中，在主页选项卡上的样式组中，选择**格式化为表**。 选择要应用到工作表的表格样式。 Excel 工作表现已准备好加载到 Power BI 中。

![格式化为表格的数据](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-into-power-bi"></a>将 Excel 文件上传到 Power BI
Power BI 将连接到多个数据源，包括位于计算机上的 Excel 文件。 若要开始，请登录到 Power BI 服务。 如果还未注册，[你可以免费注册](https://powerbi.com)。

你想要创建新仪表板。 打开“我的工作区”  ，然后选择“新建”  图标。

![创建图标](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

选择“仪表板”  ，输入名称，然后选择“创建”  。 随即显示新仪表板，但其中不包含任何数据。

![创建下拉列表](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

选择左侧导航窗格底部的“获取数据”  。 在“获取数据”页上，从“导入或连接到数据”下的“文件”框中选择**获取**。

![从文件中获取数据](media/service-from-excel-to-stunning-report/pbi_get_files.png)

在“文件”页中，选择**本地文件**。 导航到计算机上的 Excel 工作簿文件，然后选择它以加载到 Power BI 中。 选择“导入”  。

> **注意**：若要按照本教程其余部分的说明进行操作，请使用[财务示例工作簿](sample-financial-download.md)。
> 
> 

![“获取数据”>“文件”窗口](media/service-from-excel-to-stunning-report/pbi_local_file.png)

## <a name="build-your-report"></a>生成报表
Power BI 导入 Excel 文件后，将开始生成报表。 “你的数据集已就绪”  消息出现后，选择“查看数据集”  。  Power BI 在“编辑”视图中打开并显示报表画布。 “可视化效果”、“筛选器”和“字段”窗格位于右侧。

请注意，你的 Excel 工作簿表数据将在“字段”窗格中显示。 在表的名称下方，Power BI 会将列标题作为单个字段列出。

![哪些 Excel 数据看起来像“字段”窗格中的内容](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

现在可以开始创建可视化效果。 你的经理想要查看一段时间的利润。 在“字段”窗格中，将**利润**拖动到报表画布。 默认情况下，Power BI 将显示条形图。 接下来，将**日期**拖动到报表画布。 Power BI 将更新条形图以按日期显示利润。

![报表编辑器中的柱形图](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

> **提示**：如果图表外观与你的期望不符，请检查聚合。 例如，在“值”  上右键单击你刚才添加的字段，并确保数据以你期望的方式进行聚合。  在此示例中，我们使用 **Sum**。
> 
> 

你的经理想要知道哪个国家/地区的盈利最多。 使用地图可视化效果给她留下深刻印象。 选择画布上的空白区域，然后只需从“字段”窗格中将**国家/地区**和**利润**字段拖动到其中即可。 Power BI 将创建一个地图视觉对象，其中的气泡代表每个位置的相对利润。

![报表编辑器中的地图视觉对象](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

怎么显示按产品和市场细分显示销售额的视觉对象呢？ 简单。 在“字段”窗格中，选择“销售额”、“产品”和“细分市场”字段旁边的复选框。 Power BI 将立即创建一个条形图。 通过在“可视化效果”菜单中选择一个图标来更改图表的类型。 例如，将其更改为堆积条形图。  若要对图表进行排序，请选择省略号 (...) > **排序依据**。

![报表编辑器中的堆积柱形图](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

将所有视觉对象固定到仪表板。 现在便可以将其与同事共享。

![固定了 3 个视觉对象的仪表板](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>共享仪表板
你想要与经理 Paula 共享仪表板。 你可以与任何具有 Power BI 帐户的同事共享仪表板和基础报表。 他们可以与你的报表进行交互，但不能保存更改。

若要共享你的报表，可在仪表板顶部，选择**共享**。

![“共享”图标](media/service-from-excel-to-stunning-report/power-bi-share.png)

Power BI 将显示“共享仪表板”页面。 在顶部区域中，输入收件人的电子邮件地址。 在下面的字段中添加消息。 若要允许收件人将你的仪表板与他人共享，请选择**允许收件人共享仪表板**。 选择**共享**。

![共享仪表板窗口](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

后续步骤

* [Power BI 服务入门](service-get-started.md)
* [Power BI Desktop 入门](desktop-getting-started.md)
* [Power BI 服务中设计器的基本概念](service-basic-concepts.md)
* 更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


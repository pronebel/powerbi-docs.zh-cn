---
title: Power BI Premium 中的分页报表是什么？
description: 现在可以在 Power BI 服务中使用分页报表。 它们一直是 SQL Server Reporting Services 中的标准报表格式。 可以打印或共享这些报表。 用户可以精确控制报表布局。 例如，即使某个表跨多个页，分页报表也能显示表中的所有数据。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: jXTiYJKw1Rs
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 10/16/2020
ms.openlocfilehash: 2c136f4d81a9cb1c1904c3a06b58271391c76c23
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297757"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>Power BI Premium 中的分页报表是什么？

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

分页报表是设计用于打印或共享的报表。 它们被称为“分页”，因为它们已进行了格式化，以适应页面。 即使某个表跨多个页，分页报表也能显示表中的所有数据。 它们有时被称为“像素完美”，因为用户可以准确地控制其报表页面布局。 Power BI Report Builder 是用于创作 Power BI 服务的分页报表的独立工具。 

如果已准备好开始，可使用下面的一些快速链接：

- [从 Microsoft 下载中心安装 Power BI 报表生成器](https://aka.ms/pbireportbuilder)
- [教程：创建分页报表](paginated-reports-quickstart-aw.md)
- [Power BI 分页报表示例](paginated-reports-samples.md)
- 正在查找适用于 Power BI 报表服务器或 SQL Server Reporting Services 的 Report Builder 的信息吗？ 请参阅[安装 Report Builder - Power BI 报表服务器](../report-server/install-report-builder.md)。

分页报表通常有很多页。 例如，此报表有 563 页。 每页都采用精准布局，每个发票占一页，具有重复页眉和页脚。

![分页](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

你可以在 Report Builder 中预览报表，然后将其发布到 Power BI 服务 (app.powerbi.com)。 需要具有 Power BI Pro 许可证才能将报表发布到服务。 只要工作区处于 Power BI Premium 容量中，就可以在“我的工作区”或工作区中发布和共享分页报表。 另外，Power BI 管理员需要在 Power BI 管理门户的[高级容量部分](../admin/service-admin-premium-workloads.md#paginated-reports)中启用分页报表。 

## <a name="compare-power-bi-reports-and-paginated-reports"></a>比较 Power BI 报表和分页报表

分页报表的主要优点是能够打印表中的所有数据，而不考虑多长时间。 想象在 Power BI 报表中放入一个表。 页面上会显示表的部分行，并且有一个滚动条可查看其余部分。 如果打印该页面，或将其导出为 PDF，则打印的行仅是你在页面上看到的行。 

现在假设你在分页报表中放入同一个表。 打印该报表或将其导出为 PDF 时，分页报表有足够多的页面来打印表中的每一行。 

在下面的视频中，Microsoft 最有价值专家 - 数据平台 Peter Myers 和首席项目经理 Chris Finlan 演示了如何用这两种报表格式打印类似的表。 

<iframe width="560" height="315" src="https://www.youtube.com/embed/jXTiYJKw1Rs?list=PL1N57mwBHtN1icIhpjQOaRL8r9G-wytpT" frameborder="0" allowfullscreen></iframe>

此视频是基于八个模块的视频课程[一天玩转 Power BI 分页报表](../learning-catalog/paginated-reports-online-course.md)的一部分。 本课程旨在为报表作者提供创建、发布和分发 Power BI 分页报表所需的技术知识。

## <a name="create-reports-in-power-bi-report-builder"></a>在 Power BI 报表生成器中创建报表

分页报表具有其自己的设计工具，即 Power BI 报表生成器。 它是一款新工具，与以前用于为 Power BI 报表服务器或 SQL Server Reporting Services (SSRS) 创建分页报表的工具共享同一基础。 实际上，为 SSRS 2016 和 2017 或为本地 Power BI 报表服务器创建的分页报表与 Power BI 服务兼容。 Power BI 服务保持向后兼容性，因此，用户可以向前移动报表，并且可以升级任何旧版分页报表。 在发布时，并非所有报表功能都可用。 有关详细信息，请参阅本文中的[限制和注意事项](#limitations-and-considerations)。
     
## <a name="report-from-a-variety-of-data-sources"></a>来自各种数据源的报表

一个分页报表可能包含许多不同的数据源。 与 Power BI 报表不同的是，它没有基础数据模型。 对于 Power BI 服务中分页报表的初始发布，可以在报表本身创建嵌入数据源和数据集。 尚无法使用共享数据源或共享数据集。 可以在本地计算机上的报表生成器中创建报表。 如果报表连接到本地数据，则在将报表上传到 Power BI 服务后，需要创建网关并重定向数据连接。 以下是目前可以连接到的数据源：

- Azure SQL 数据库和数据仓库（通过 Basic 和 oAuth）
- Azure Analysis Services（通过 SSO）
- 通过网关连接的 SQL Server
- 通过网关连接的 SQL Server Analysis Services
- Power BI 数据集
- Oracle
- Teradata

## <a name="design-your-report"></a>设计报表  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>创建具有矩阵、图表和自由格式布局的分页报表

表格报表非常适用于基于列的数据。 矩阵报表（如交叉表或数据透视表报表）适用于汇总数据。 图表报表以图形格式显示数据，自由格式列表报表几乎可以显示任何其他内容，例如发票。 
  
可以从其中一个报表生成器向导开始操作。 表、矩阵和图表向导将引导用户创建嵌入数据源连接和嵌入数据集。 然后拖放字段以创建数据集查询，选择布局和样式，以及自定义报表。  
  
使用“地图”向导，可以创建根据地理或几何背景显示聚合数据的报表。 地图数据可能是来自 Transact-SQL 查询或美国环境系统研究所公司(ESRI) 形状文件的空间数据。 除此之外，还可以添加 Microsoft 必应地图图块背景。  

### <a name="add-more-to-your-report"></a>向报表添加更多内容

通过筛选、分组数据和对数据排序，或通过添加公式或表达式来修改数据。 添加图表、仪表、迷你图和指示器，以可视化格式汇总数据。  使用参数和筛选器筛选自定义视图的数据。 嵌入或引用图像和其他资源，包括外部内容。  

分页报表中的所有内容（包括从报表本身到每个文本框、图像、表格和图表）都有一系列属性，用户可以设置这些属性，使报表看起来完全符合自己的要求。

## <a name="creating-a-report-definition"></a>创建报表定义

在设计分页报表时，实际上要创建报表定义。 它不包含数据。 它指定获取数据的位置、要获取的数据以及如何显示数据。 运行报表时，报表处理器将获取用户指定的报表定义、检索数据，并将其与报表布局组合以生成报表。 可以将报表定义上传到 Power BI 服务：`https://app.powerbi.com`，以上传到“我的工作区”或与同事共享的工作区中。 如果报表数据源位于本地环境中，则在上传报表后，可以将数据源连接重定向到网关。 

## <a name="view-your-paginated-report"></a>查看分页报表
可以通过浏览器在 Power BI 服务中查看分页报表，也可以在 Power BI 移动应用中查看。 在 Power BI 服务中，可以将报表导出为多种格式，例如 HTML、MHTML、PDF、XML、CSV、TIFF、Word 和 Excel。 还可以与其他人共享它。  

## <a name="create-a-subscription-to-your-report"></a>创建报表订阅

现在可以在 Power BI 服务中为自己和他人设置分页报表的电子邮件订阅。 一般而言，该过程与在 Power BI 服务中订阅报表和仪表板的过程相同。 设置订阅时，可以选择接收电子邮件的频率：每天、每周或每小时。 订阅包含有关整个报表输出的 PDF 附件。

有关详细信息，请参阅[在 Power BI 服务中为自己和他人订阅分页报表](../consumer/paginated-reports-subscriptions.md)一文。 

## <a name="limitations-and-considerations"></a>限制和注意事项

以下是初始版本中不支持的一些其他功能：

- 将报表页或视觉对象固定到 Power BI 仪表板。 用户仍可以从 Power BI 报表服务器或 Reporting Services 报表服务器上的本地分页报表将可视化效果固定到 Power BI 仪表板。 有关详细信息，请参阅[将 Reporting Services 项目固定到 Power BI 仪表板](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)。
- 文档结构图。
- 钻取报表。  请考虑将 URL 参数与分页报表配合使用，从而实现钻取方案。
- 共享数据源和共享数据集。

 
## <a name="next-steps"></a>后续步骤

- [从 Microsoft 下载中心安装 Power BI 报表生成器](https://aka.ms/pbireportbuilder)
- [教程：创建分页报表](paginated-reports-quickstart-aw.md)
- [在线课程：一天玩转 Power BI 分页报表](../learning-catalog/paginated-reports-online-course.md)
- [Power BI 分页报表示例](paginated-reports-samples.md)
- [直接在分页报表中输入数据](paginated-reports-enter-data.md)
- [教程：在应用程序中为客户 ](../developer/embedded/embed-paginated-reports-customers.md) 嵌入 Power BI 分页报表
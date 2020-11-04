---
title: 直接在报表生成器的分页报表中输入数据
description: 本文介绍如何将数据直接输入到报表生成器的分页报表中。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 07/10/2020
ms.author: maggies
ms.openlocfilehash: 05da5fa050fc92ebae320af9e07fe6505b5790f4
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297957"
---
# <a name="enter-data-directly-in-a-paginated-report-in-report-builder---power-bi"></a>直接在报表生成器 - Power BI 的分页报表中输入数据

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

本文介绍了新版 Microsoft Power BI Report Builder 中的一项功能，你可以使用该功能将数据作为嵌入式数据集直接输入 RDL 报表。  此功能类似于 Power BI Desktop。 可以直接在报表的数据集中键入数据，也可从其他程序（如 Microsoft Excel）中粘贴数据。 通过输入数据创建数据集后，可像使用任何其他已创建的嵌入数据集一样使用它。 此外，可以添加多个表，并使用一个表作为另一个表的筛选器。 此功能对可能要用于报表的小型静态数据集（如报表参数）特别有用。
 
## <a name="prerequisites"></a>先决条件

- 要直接在分页报表中输入数据，请[下载并安装 Power BI Report Builder](https://aka.ms/pbireportbuilder)。 
- 若要将分页报表保存到 Power BI 服务，则需 [Power BI Pro 帐户](../fundamentals/service-self-service-signup-for-power-bi.md)，以及对 [Power BI 高级容量](../admin/service-premium-what-is.md)中的工作区的写入权限。
- 若要将分页报表保存到报表服务器，则需[编辑 RsReportServer.config 文件](#upload-the-paginated-report-to-a-report-server)的权限。

## <a name="create-a-data-source-and-dataset"></a>创建数据源和数据集

下载并安装报表生成器后，按照向报表添加嵌入数据源和数据集的相同工作流程操作。 在以下过程中，“数据源”下会出现一个新选项：“输入数据”。  只需在报表中设置一次此数据源。 之后，可创建多个输入数据表作为单独的数据集，数据集全部使用该单个数据源。

1. 在“报表数据”窗格中，选择“新建” > “数据集”  。

    ![Report Builder“新建”数据集的屏幕截图。](media/paginated-reports-enter-data/paginated-new-dataset.png)

1. 在“数据集属性”对话框中，选择“使用我的报告中嵌入的数据集” 。

1. 在“数据源”旁边，选择“新建” 。

    ![新建嵌入式数据源的屏幕截图。](media/paginated-reports-enter-data/paginated-new-data-source.png)

1. 在“数据源属性”对话框中，选择“使用我的报告中嵌入的连接” 。
2. 在“选择连接类型”框中，选择“输入数据” > “确定”  。

    ![“输入数据”数据源的屏幕截图。](media/paginated-reports-enter-data/paginated-data-source-properties-enter-data.png)

1. 返回“数据集属性”对话框，选择“查询设计器” 。
2. 在“查询设计器”窗格中，右键单击并在表中粘贴数据。

    ![“在查询设计器中输入数据”的屏幕截图。](media/paginated-reports-enter-data/paginated-enter-data.png)

1. 若要设置列名称，请双击每个“NewColumn”并键入列名称。

    ![“设置列名称”的屏幕截图。](media/paginated-reports-enter-data/paginated-column-name.png)

1. 如果第一行包含原始数据的列标题，请右键单击并将其删除。
    
9. 默认情况下，每列的数据类型为字符串。 若要更改数据类型，请右键单击列标题 >“更改类型”，然后将其设为其他数据类型，例如日期或浮点数。

    ![“更改数据类型”的屏幕截图。](media/paginated-reports-enter-data/paginated-data-type.png)

1. 表格创建完成后，选择“确定”。  

    生成的查询与使用 XML 数据源时的查询相同。 实际上，我们使用 XML 来提供数据。  我们已重新对其进行了调整，以启用此方案。

    ![XML 数据结构的屏幕截图。](media/paginated-reports-enter-data/paginated-xml-data.png)

12. 在“数据集属性”对话框中，选择“确定” 。

13. 可在“报表数据”窗格中看到数据源和数据集。

    ![“报表数据”窗格中的“数据集”的屏幕截图。](media/paginated-reports-enter-data/paginated-report-data-pane.png)

可使用数据集作为报表中数据可视化效果的基础。 此外，还可添加其他数据集并为其使用相同数据源。

## <a name="design-the-report"></a>设计报表

现在你已有数据源和数据集，接下来就可以创建报表了。 以下步骤将根据上一部分中的数据创建一个简单报表。

1. 在“插入”菜单中，选择“表格” > “表向导”  。

    :::image type="content" source="media/paginated-reports-enter-data/paginated-table-wizard.png" alt-text="选择“表向导”选项的屏幕截图。":::

1. 选择刚刚创建的数据集 >“下一步”。

    :::image type="content" source="media/paginated-reports-enter-data/paginated-choose-dataset.png" alt-text="“选择数据集”对话框的屏幕截图。":::

2.  在“排列字段”页中，将要用作分组依据的字段从“可用字段”框拖动到“行组”框 。 在本示例中：

    - CountryRegion
    - SalesYear

3.  将想要聚合的字段从“可用字段”框拖动到“值”框 。 在本示例中：

    - 销售额

    默认情况下，Report Builder 对“值”框中的字段求和，但你可以选择其他聚合方式。

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-aggregation.png" alt-text="不同聚合选项的屏幕截图。":::
 
1. 选择“下一步”。
4.  在“选择布局”页中，保留所有默认设置，但清除“展开/折叠组”。 一般而言，展开和折叠组是很好的，但这一次，我们想要查看所有数据。

5.  选择“下一步” > “完成”。 该表显示在设计图面上。

    :::image type="content" source="media/paginated-reports-enter-data/paginated-design-view-matrix.png" alt-text="在“设计”视图中报表的屏幕截图。":::

### <a name="run-the-report"></a>运行报表

要查看实际值并预览报表，请运行该报表。

1. 在“开始”功能区中选择“运行” 。

    :::image type="content" source="media/paginated-reports-enter-data/paginated-run-report.png" alt-text="在“开始”功能区中选择“运行”的屏幕截图。":::

    现在，你将看到这些值。 矩阵包含的行数比你在“设计”视图中看到的要多得多！  在保存到本地计算机或发布到服务之前，你可以设置页面的格式或决定使用默认设置。

1. 要查看报表的打印效果，请选择“打印布局”。

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-print.png" alt-text="选择“打印布局”的屏幕截图。":::

    现在，你会看到它在打印页上的外观。

    :::image type="content" source="media/paginated-reports-enter-data/paginated-print-layout.png" alt-text="打印布局视图中报表的屏幕截图。":::

## <a name="upload-the-paginated-report-to-the-power-bi-service"></a>将分页报表上传到 Power BI 服务

Power BI 服务现在支持分页报表，因此可将分页报表上传到高级容量。 有关详细信息，请参阅[上传分页报表](paginated-reports-save-to-power-bi-service.md)。

## <a name="upload-the-paginated-report-to-a-report-server"></a>将分页报表上传到报表服务器

还可将分页报表上传到 Power BI 报表服务器或 SQL Server Reporting Services 2016 或 2017 报表服务器。 在此之前，需将以下项添加到 RsReportServer.config 作为附加数据扩展。 如果遇到任何问题，请在进行更改前备份 RsReportServer.config 文件。

```xml
<Extension Name="ENTERDATA" Type="Microsoft.ReportingServices.DataExtensions.XmlDPConnection,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <ConfigName>ENTERDATA</ConfigName>
    </Configuration>
</Extension>
```

编辑完后，配置文件中的数据提供程序列表应如下所示：

![RsReportServer 配置文件的屏幕截图。](media/paginated-reports-enter-data/paginated-rsreportserver-config-file.png)

就这么简单！现在即可将使用此新功能的报表发布到报表服务器。

## <a name="next-steps"></a>后续步骤

- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)
- [什么是 Power BI 报表服务器？](../report-server/get-started.md)

---
title: Power BI 报表服务器中的新增功能
description: 了解 Power BI 报表服务器中的新增功能。 本文涉及主要功能方面，并会在新功能发布时随之进行更新。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2019
ms.openlocfilehash: 2a65baf94abcb79dac7bb9419ad67124f2b65bb8
ms.sourcegitcommit: 2c49a7cee9c77f46830ddfa59fdedbf30186d389
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54488928"
---
# <a name="whats-new-in-power-bi-report-server"></a>Power BI 报表服务器中的新增功能

了解 Power BI 报表服务器中的新增功能。 本文涉及主要功能方面，并会在新功能发布时随之进行更新。

若要下载最新版本的 Power BI 报表服务器和针对 Power BI 报表服务器进行了优化的 Power BI Desktop，请转到[使用 Power BI 报表服务器进行本地报告](https://powerbi.microsoft.com/report-server/)。

若要了解相关的 Power BI“新增功能”信息，请参阅：

* [Power BI 服务中的最近更新](../service-whats-new.md)
* [Power BI Desktop 中的新增功能](../desktop-latest-update.md)
* [Power BI 移动应用中的新增功能](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2019"></a>2019 年 1 月

Power BI 报表中支持以下功能：

[**行级别安全性**](row-level-security-report-server.md)使用 Power BI 报表服务器设置行级别安全性 (RLS) 可以限制指定用户的数据访问。 筛选器限制行级别的数据访问，你可以定义角色中的筛选器。

[**展开和折叠矩阵行标题**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse)我们添加了扩展和折叠单个行标题的功能，这是需求最大的可视化功能之一。

[**在 .pbix 文件之间复制和粘贴**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste)可以在 .pbix 文件之间复制视觉对象（从视觉对象的上下文菜单中复制，或者使用标准的 Ctrl+C 键盘快捷方式复制），然后使用 Ctrl+V 将其粘贴到另一个报告中。

[**智能对齐参考线**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides)在报表页面上移动对象时，可看到智能对齐参考线，如 PowerPoint 中所示的那样，有助于对齐页面上的所有内容。 只要在页面上拖动或调整某些内容，就会看到智能参考线。 将对象移动到另一个对象附近时，该参考线会快速移动到与另一个对象对齐的位置。

**辅助功能**要列出的辅助功能太多：例如，[字段列表窗格辅助功能支持](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList)。 字段列表窗格完全可供访问。 可以浏览窗格，仅需使用键盘和屏幕阅读器即可实现，还可以使用上下文菜单将字段添加到报告页面。

### <a name="administrator-settings"></a>管理员设置

管理员可以在服务器场的 SSMS 高级属性中设置以下属性：

**AllowedResourceExtensionsForUpload** 设置可以上传到报表服务器的资源扩展。 不要求包含内置文件类型的扩展，如 &ast;.rdl 和 &ast;.pbix。 默认为“&ast;、&ast;.xml、&ast;.xsd、&ast;.xsl、&ast;.png、&ast;.gif、&ast;.jpg、&ast;.tif、&ast;.jpeg、&ast;.tiff、&ast;.bmp、&ast;.pdf、&ast;.svg、&ast;.rtf、&ast;.txt、&ast;.doc、&ast;.docx、&ast;.pps、&ast;.ppt、&ast;.pptx”。 

**SupportedHyperlinkSchemes** 设置以逗号分隔的 URI 方案列表，这些方案可以在允许呈现的超链接操作上定义，或设置“&ast;”，启用所有超链接方案。 例如，设置“http,https”将允许指向“https://www. contoso.com”的超链接，但会删除指向“mailto:bill@contoso.com”或“javascript:window.open(‘www.contoso.com’, ‘_blank’)”的超链接。 默认为“&ast;”。

## <a name="august-2018"></a>2018 年 8 月

2018 年 8 月，针对 Power BI 报表服务器优化的 Power BI Desktop 版本中新增了很多新功能。 这些功能涉及不同的方面：

- [报告](#reporting)
- [分析](#analytics)
- [建模](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>2018 年 8 月版本的亮点

下面这些功能在大量新功能中脱颖而出，尤为值得关注。 有关详细信息，请参阅我们的[博客文章](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/)。

#### <a name="report-theming"></a>报表主题

2018 年 8 月版本的 Power BI 报表服务器中添加了报表主题，可快速为整个报表着色，以匹配主题或公司品牌。 导入主题时，所有图表都会自动更新为使用主题颜色，可从调色板访问主题颜色。 可使用“切换主题”按钮下的“导入主题”选项上传主题文件。

主题文件是一个 JSON 文件，其中包含想要在报表中使用的所有颜色以及要应用于视觉对象的任何默认格式。
这是一个简单的 JSON 主题示例，它只更新报表的默认颜色：

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>通过不同字段设置条件格式

通过模型中的不同字段设置列的格式是条件格式的一个重要改进。

#### <a name="conditional-formatting-by-values"></a>通过值设置条件格式

另一个新的条件格式类型是“按字段设置格式”值。 借助“按字段设置格式”值，可使用通过十六进制代码或名称指定颜色的度量值或列，并将该颜色应用于背景或字体颜色。

#### <a name="report-page-tooltips"></a>报告页工具提示

Power BI 报表服务器的 2018 年 8 月更新中加入了报表页工具提示功能。 通过此功能，可设计报表页，以用作报表中其他视觉对象的自定义工具提示。

#### <a name="log-axis-improvements"></a>对数轴改进

我们大幅改进了笛卡尔图表中的对数轴。 拥有的数据全部为正数或全部为负数时，现在应该可以为任何笛卡尔图表（包括组合图）的数值轴选择对数刻度。

#### <a name="sap-hana-sso-direct-query"></a>SAP HANA SSO 直接查询

Power BI 报表现在提供使用 Kerberos 的 SAP HANA SSO 直接查询支持。

>[!Note]
>仅当将 SAP HANA 视为具有在 Power BI Desktop 中创建的报表的关系数据源时，才支持此方案。  若要在 Power BI Desktop 中启用此功能，请在“选项”下的“DirectQuery”菜单中选中“将 SAP HANA 视为关系源”，然后单击“确定”。

#### <a name="custom-visuals"></a>自定义视觉对象

- 此版本附带的 API 版本为 1.13.0。

- 现在，自定义视觉对象可回退到与当前版本的服务器 API 兼容的先前版本（如果可用）。

### <a name="reporting"></a>报表 

- [报表主题](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [触发操作的按钮](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [组合图线条样式](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [改进了针对视觉对象的默认排序](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [数值切片器](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [高级切片器同步](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [对数轴改进](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [漏斗图的数据标签选项](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [将线条笔划宽度设置为零](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [报表的高对比度支持](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [圆环图半径控制](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [饼图和圆环图的详细信息标签位置控制](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [为组合图中的每个度量值单独设置数据标签格式](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [具有更多灵活性和格式设置的新视觉对象标头](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [壁纸格式设置](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [表和矩阵的工具提示](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [关闭视觉对象的工具提示](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [切片器辅助功能](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [格式设置窗格改进](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [线条和组合图的渐变线支持](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [排序体验改进](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [通过导出到 PDF 打印报表（在 Power BI Desktop 中）](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [创建书签组](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [切片器重述](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [报表页工具提示](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>分析

- [新的 DAX 函数：COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [度量值钻取](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [通过不同字段设置条件格式](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [通过值设置条件格式](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>建模

- [数据视图中的筛选和排序](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [改进的区域设置格式设置](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [度量值的数据类别](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [统计 DAX 函数](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>2018 年 5 月

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>为报表服务器远程配置 Power BI iOS 移动应用

作为 IT 管理员，你现在可以使用组织的 MDM 工具来远程配置 Power BI iOS 移动应用对报表服务器的访问权限。 有关详细信息，请参阅[远程配置 Power BI iOS 移动应用对报表服务器的访问权限](configure-powerbi-mobile-apps-remote.md)。

## <a name="march-2018"></a>2018 年 3 月

2018 年 3月，针对 Power BI 报表服务器优化的 Power BI Desktop 版本中新增了很多很多功能。 这些功能涉及不同的方面：

- [视觉对象](#visuals-updates)
- [报告](#reporting)
- [分析](#analytics)
- [性能](#performance)
- [报表服务器](#report-server)
- [其他](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>2018 年 3 月版本的亮点

下面这些功能在大量新功能中脱颖而出，尤为值得关注。

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[适用于表和矩阵的基于规则的条件格式](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

创建规则，以便根据表或矩阵中特定的业务逻辑，有条件地对某一列的背景和字体进行着色。

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[显示和隐藏页](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

你希望读者访问你的报表，但是部分页面尚未完成。 现在就可以隐藏这些页面，直到它们已准备就绪。 或者可以在常规导航中隐藏页面，读者可以通过书签或钻取来访问此页面。

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Bookmarking](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

说到添加书签，就是创建书签，用报表中的数据来传达信息。

- [书签交叉突出显示](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting)：书签维护并显示在创建书签时报告页的交叉突出显示状态。
- [更多书签灵活性](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility)：书签反映了你在报表中设置的属性，并且只影响你选择的视觉对象。

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[跨多个图表选择多个数据点](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

在多个图表中选择多个数据点，并将交叉筛选应用于整个页面。

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[跨报表的多个页面同步切片器](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

切片器可应用于报表中的一页、两页或多页。

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[快速度量](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

基于现有度量值和表中的数字列新建度量值。

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[向下钻取筛选其他视觉对象](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

在一个视觉对象的给定类别中向下钻取时，可以让其按相同的类别筛选所有视觉对象。

### <a name="visuals-updates"></a>视觉对象更新

- [适用于表和矩阵的单元格对齐方式](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [表和矩阵列的显示单位和精度控制](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [条形图和柱形图的溢出数据标签](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [控制笛卡尔和映射视觉对象的数据标签背景颜色](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [栏/列填充控制](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [增加图表中用于轴标签的区域](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [基于 x 轴和 y 轴分组的散点图视觉对象](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [地图基于纬度和经度的高密度抽样](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [响应式切片器](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [为相对日期切片器添加定位标记日期](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>报表

- [关闭报表读取模式中的视觉对象标头](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [适用于慢数据源的报表选项](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [改进了默认视觉对象布局](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [通过选择窗格控制视觉对象排序](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [锁定报表上的对象](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [搜索“格式化”和“分析”窗格](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [字段属性窗格和字段说明](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>分析

- [UTCNOW() 和 UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [标记自定义日期表](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [钻取筛选其他视觉对象](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [适用于多行卡片的多维 AS 模型的单元格级格式设置](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>性能

- [筛选功能性能改进](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [DirectQuery 性能改进](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [打开和保存性能改进](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [“显示不包含数据的项目”改进](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>报表服务器

#### <a name="export-to-accessible-pdf"></a>导出为可访问的 PDF

现在将分页 (RDL) 报表导出为 PDF 时，可以获取一个可访问/标记的 PDF 文件。 虽然该文件比较大，但更方便屏幕阅读器和其他辅助技术阅读和导航。 通过将 AccessiblePDF 设备信息设置设为“True”，启用可访问的 PDF。 请参阅 [PDF 设备信息设置](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings)和[更改设备信息设置](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings)。

### <a name="other-improvements"></a>其他改进

- [“从示例中添加列”的改进](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [“咨询服务”快速链接](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [错误报告已改进](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [查看之前遇到的错误](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>2017 年 10 月

### <a name="power-bi-report-data-sources"></a>Power BI 报表数据源

Power BI 报表服务器中的 Power BI 报表可以连接到各种数据源。 可以导入数据和计划数据刷新，或者直接使用 DirectQuery 或与 SQL Server Analysis Services 的实时连接查询数据。 请参阅支持计划的刷新和支持“Power BI 报表服务器中的 Power BI 报表数据源”中的 DirectQuery 的数据源列表。

### <a name="scheduled-data-refresh-for-imported-data"></a>导入的数据的计划数据刷新

在 Power BI 报表服务器中，可以设置计划的数据刷新，以使用嵌入式模型（而不是实时连接或 DirectQuery）使 Power BI 报表中的数据始终保持最新。 由于使用嵌入式模型导入数据，一次它会与原始数据源断开连接。 它需要更新以便数据保持最新状态，而计划的刷新就可以实现这一点。 详细了解“Power BI 报表服务器中 Power BI 报表的计划刷新”。

### <a name="editing-power-bi-reports-from-the-server"></a>从服务器编辑 Power BI 报表

可以从服务器打开和编辑 Power BI 报表 (.pbix) 文件，而且可以找回上传的原始文件。  这意味着，如果数据已由服务器刷新，则在首次打开该文件时将不会刷新数据。 需要在本地手动刷新才能查看更改。

### <a name="large-file-uploaddownload"></a>大型文件上传/下载

可以上传最大 2 GB 的文件（在 SQL Server Management Studio (SSMS) 的报表服务器设置中，此限制默认设置为 1 GB）。  这些文件存储在数据库中，就像它们适用于 SharePoint 一样，并且不需要对 SQL Server 目录进行任何特殊配置。  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>通过 OData 源访问共享数据集

可以使用 OData 源从 Power BI Desktop 访问共享数据集。 有关详细信息，请参阅[在 Power BI 报表服务器中通过 OData 源访问共享数据集](access-dataset-odata.md)。

### <a name="scale-out"></a>横向扩展

此版本支持横向扩展。使用负载均衡器并设置服务器关联以获得最佳体验。 请注意，该方案尚未针对横向扩展进行优化，因此，将看到模型可能会在多个节点之间复制。 该方案将在没有网络负载均衡器和粘性会话的情况下运行。 但是，加载模型 N 次时，不仅会看到跨节点的内存过度使用，而且连接之间的性能会下降，因为在模型抵达两个请求之间的新节点时会对其进行流式传输。  

### <a name="administrator-settings"></a>管理员设置

管理员可以在服务器场的 SSMS 高级属性中设置以下属性：

* EnableCustomVisuals：True/False
* EnablePowerBIReportEmbeddedModels：True/False
* EnablePowerBIReportExportData：True/False
* MaxFileSizeMb：默认值现在为 1000
* ModelCleanupCycleMinutes：检查并从内存中收回模型的频率
* ModelExpirationMinutes：根据上次使用时间，定义模型过期并被收回的时长
* ScheduleRefreshTimeoutMinutes：一个模型的数据刷新需要多长时间。 默认情况下，此值为两个小时。  没有固定上限。

**配置文件 rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>开发人员 API

为 SSRS 2017 引入的开发人员 API (REST API) 已针对 Power BI 报表服务器进行了扩展，以便处理 Excel 文件和 .pbix 文件。 一个可能的用例是以编程方式从服务器下载文件，对文件进行刷新，然后重新发布文件。 例如，这是使用 PowerPivot 模型刷新 Excel 工作簿的唯一方法。

请注意，有一个单独的新 API 适用于将在 Swagger 的 Power BI 报表服务器版本中进行更新的大型文件。 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) 和 Power BI 报表服务器的内存占用情况

Power BI 报表服务器现在可在内部托管 SQL Server Analysis Services (SSAS)。 这并非特定于计划的刷新。 托管 SSAS 可以极大地扩展报表服务器的内存占用情况。 AS.ini 配置文件在服务器节点上可用，因此，如果用户熟悉 SSAS，可能想要更新设置，其中包括最大内存限制和磁盘缓存等。有关详细信息，请参阅 [Analysis Services 中的服务器属性](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services)。

### <a name="viewing-and-interacting-with-excel-workbooks"></a>查看 Excel 工作簿并与之交互

Excel 和 Power BI 包含行业中独一无二的一套工具。 同时，它们使业务分析师更轻松地收集数据、构建数据模型、分析并以可视化方式浏览数据。 除了在 Web 门户中查看 Power BI 报表之外，企业用户现在也可以使用 Power BI 报表服务器中的 Excel 工作簿执行相同的操作，从而向用户提供单个位置来发布和查看其自助服务 Microsoft BI 内容。

我们已发布了[如何将 Office Online Server (OOS) 添加到 Power BI 报表服务器预览环境的演练](excel-oos.md)。 具有批量许可帐户的客户可以从批量许可服务中心免费下载 OOS，并且将具有仅查看功能。 配置后，用户可以查看具有以下特点的 Excel 工作簿并与之交互：

* 没有外部数据源依赖关系
* 实时连接到外部 SQL Server Analysis Services 数据源
* 具有 PowerPivot 数据模型

### <a name="support-for-new-table-and-matrix-visuals"></a>支持新的表和矩阵视觉对象

Power BI 报表服务器现在支持新的 Power BI 表和矩阵视觉对象。 若要创建具有这些视觉对象的报表，需要 2017 年 10 月发布的更新的 Power BI Desktop 版本。 它不能与 Power BI Desktop（2017 年 6 月）版本并行安装。 对于最新版本的 Power BI Desktop，请在 [Power BI 报表服务器下载页](https://powerbi.microsoft.com/report-server/)上选择“高级下载选项”。

## <a name="june-2017"></a>2017 年 6 月

* Power BI 报表服务器已正式发布 (GA)。

## <a name="may-2017"></a>2017 年 5 月

* Power BI 报表服务器预览版已发布
* 可以在本地发布 Power BI 报表
  * 支持自定义视觉对象
  * 仅支持 Analysis Services 实时连接，今后将会支持更多数据源。
  * Power BI 移动应用更新为显示在 Power BI 报表服务器中托管的 Power BI 报表
* 通过注释增强了报表协作

## <a name="next-steps"></a>后续步骤

查看下面这些源，以便随时了解 Power BI 报表服务器中的新增功能。

* [Microsoft Power BI 博客](https://powerbi.microsoft.com/blog/)
* [SQL Server Reporting Services 团队博客](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Guy in a Cube YouTube 频道](https://aka.ms/guyinacube)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
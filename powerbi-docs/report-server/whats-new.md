---
title: Power BI 报表服务器中的新增功能
description: 了解 Power BI 报表服务器中的新增功能。 本文包括主要功能区域，在发布新项时进行更新。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/23/2020
ms.openlocfilehash: 9b7ea090d7860de9ec4132b070bd1286085cc5f3
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819551"
---
# <a name="whats-new-in-power-bi-report-server"></a>Power BI 报表服务器中的新增功能

了解 Power BI 报表服务器中的新增功能以及针对 Power BI 报表服务器优化的 Power BI Desktop 中的新增功能。 本文涉及主要功能方面，并随每个新版本进行更新。

下载 [Power BI 报表服务器和针对 Power BI 报表服务器优化的 Power BI Desktop](https://powerbi.microsoft.com/report-server/)。

若要了解相关的 Power BI“新增功能”信息，请参阅：

* [Power BI 服务中的最近更新](../service-whats-new.md)
* [Power BI Desktop 中的新增功能](../desktop-latest-update.md)
* [Power BI 移动应用中的新增功能](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2020"></a>2020 年 1 月

有关更多详细信息，请参阅 Power BI 报表服务器 2020 年 1 月博客文章。

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>针对 Power BI 报表服务器优化的 Power BI Desktop

此发布引入了许多新功能，例如，按钮的条件格式设置、数据配置文件增强功能以及 KPI 和表格视觉对象的更多格式设置。 下面介绍汇总的更新列表：

**Reporting**

- 将表列或矩阵值设置为自定义 URL
- KPI 视觉对象格式设置
- 筛选器窗格体验更新

**分析**

- 有条件地设置按钮格式
- 加载更多内容以分析见解
- 新的 DAX 函数：季度

**数据准备**

- 数据事件探查增强功能

**其他**

- 新文件格式：.pbids
- 建模操作的性能改进

**Reporting**

*将表列或矩阵值设置为自定义 URL*

可以将表列或矩阵值设置为自定义 URL。 可以在“格式”窗格中的条件格式设置卡下找到此新选项。

*KPI 视觉对象格式设置*

在本月的发布中，KPI 具有新的格式设置选项：

- 指示器文本格式设置（字体系列、颜色和对齐方式）
- 趋势轴透明度
- 目标和距离文本格式设置（标签文本、字体系列、颜色和大小）
- 距离文本格式设置（标签文本、正方向、字体系列、颜色和大小）
- 添加带有格式设置（字体系列、颜色和大小）的日期标签

可以有条件地设置一些新格式设置选项：

- 指示器字体颜色
- 目标字体颜色和目标距离字体颜色
- 正常/错误/中性状态颜色
- 日期字体颜色

*筛选器窗格体验更新*

作为[最新发布](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane)中正式发布的新筛选器体验一部分，我们简化了将当前报表转换到新窗格的过程。 首次打开 Power BI 报表服务器时，将看到筛选器窗格自动更新对话框。 如果需要将报表迁移到新体验，这些更新还会在报表服务器中包括横幅。

**分析**

*按钮的条件格式设置*

这些条件格式设置更新与所有按钮相关。 现在可以为以下属性动态设置格式：

- 按钮文本字体颜色
- 按钮文本
- 图标线条颜色
- 轮廓颜色
- 填充颜色
- 按钮工具提示（在操作卡下）

*加载更多内容以分析见解*

当运行“分析”功能以在数据中查找见解时，例如“解释增长”，我们仅在一段固定时间内运行机器学习模型以便及时显示见解。 如果有大量数据要分析，现在可以选择在初始超时后继续运行分析。

*新的 DAX 函数：Quarter*

本月，我们将提供一个新的 DAX 函数 Quarter。 Quarter 函数返回特定日期对应的季度。

**数据准备**

*数据事件探查增强功能*

本月，我们将对 Power Query 编辑器中的数据事件探查功能引入一些重要的增强功能，包括：

- 除了现有的“按值”条件外，“列配置文件”窗格值分布可视对象的多个分组选项（具体参照列类型）。
- 文本：按文本长度（字符数）。
- 编号：按符号（正/负）和奇偶校验（偶数/奇数）。
- 日期/日期时间：按年、月、日、每年的某一周、每周的某一日、AM/PM 时间和一天中的某个小时。
- 还有更多其他数据类型，例如逻辑 True/False。

*筛选器选项*

已经可以在“列配置文件分配”窗格中利用多个类型特定的分组条件。 现在，在应用分组条件时，还可以从标注中筛选出分配图中的每个值。 例如，从“日期/日期时间”列的“数据配置文件”窗格中，可以排除给定月份中的所有值。

**其他**

*新文件格式：.pbids*

本月我们将发布新的文件格式 .pbids，以简化组织中报表创建者的“获取数据”体验。 建议管理员为常用连接创建这些文件。

报表创建者打开 .pbids 文件时，Power BI Desktop 会提示进行身份验证以连接到文件中指定的数据源。 然后，用户选择要加载到模型中的表。 如果未在文件中指定数据库，则他们可能还需要选择数据库。 现在，报表创建者可以开始生成可视化效果。

在“Power BI Desktop 中的数据源”一文的[使用 .pbids 文件获取数据](../desktop-data-sources.md#using-pbids-files-to-get-data)部分中找到详细信息和示例。

*建模操作的性能改进*

我们在 Analysis Services 引擎中进行了性能改进，以加快建模操作，例如，添加度量值或计算的列以及创建关系。 你看到的改进程度取决于模型，但是我们发现某些客户在执行诸如打开文件和添加度量值之类的操作时性能提升了 20 倍。

以上就是 2020 年 1 月发布的 Power BI 报表服务器的全部内容。 继续发送反馈，不要忘记[为你希望 Power BI 提供的功能进行投票](https://ideas.powerbi.com/forums/265200-power-bi)。

### <a name="power-bi-report-server"></a>Power BI 报表服务器

#### <a name="export-to-excel-from-power-bi-reports"></a>从 Power BI 报表导出到 Excel

现在，从 Power BI 报表服务器中的 Power BI 报表导出到 Excel 与从 Power BI 服务中的 Power BI 报表中导出到 Excel 相同。 可以直接导出为 Excel .xlsx 格式，导出限制为 15 万行。

#### <a name="azure-sql-managed-instance-support"></a>Azure SQL 托管实例支持

现在，可以在 VM 或数据中心中托管的 Azure SQL 托管实例 (MI) 中托管用于 Power BI 报表服务器的数据库目录。 支持仅限于使用数据库凭据连接到 SQL MI。

#### <a name="power-bi-premium-dataset-support"></a>Power BI Premium 数据集支持

可以使用 Microsoft 报表生成器或 SQL Server 数据工具 (SSDT) 连接到 Power BI 数据集。 然后，可以使用 SQL Server Analysis Services 连接将这些报表发布到 Power BI 报表服务器。 用户需要使用存储的 Windows 用户名和密码来启用方案。

#### <a name="alttext-alternative-text-support-for-report-elements"></a>报表元素支持 AltText（替代文本）

在创作报表时，可以使用工具提示为报告中的每个元素指定文本。 屏幕阅读器技术将使用这些工具提示。

#### <a name="azure-active-directory-application-proxy-support"></a>Azure Active Directory 应用程序代理支持

使用 Azure Active Directory 应用程序代理，你不再需要管理自己的 Web 应用程序代理即可允许通过 Web 或移动应用进行安全访问。 有关更多信息，请参阅[通过 Azure Active Directory 的应用程序代理对本地应用程序进行远程访问](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。

#### <a name="custom-headers"></a>自定义标头

为所有与指定的正则表达式模式匹配的 URL 设置标头值。 用户可以使用有效的 XML 更新自定义标头值，以设置所选请求 URL 的标头值。 管理员可以在 XML 中添加任意数量的标头。 有关详细信息，请参阅 Reporting Services“服务器属性高级页面”  一文中的[自定义标头](https://docs.microsoft.com/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#custom-headers)。

#### <a name="transparent-database-encryption"></a>透明数据库加密

Power BI 报表服务器现在为企业版和标准版的 Power BI 报表服务器目录数据库提供透明数据库加密支持。

#### <a name="microsoft-report-builder-update"></a>Microsoft 报表生成器更新

新发布的报表生成器版本与 Reporting Services 的 2016、2017 和 2019 版本完全兼容。 它还与 Power BI 报表服务器的所有发行版和受支持的版本兼容。

## <a name="september-2019"></a>2019 年 9 月

有关所有新功能的详细信息，请参阅 [Power BI 报表服务器 2019 年 9 月版](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/)博客文章。

Power BI 报表服务器的 2019 年 9 月更新包含大量 Power BI 报表功能。 以下是一些要点：

- **适用于切片器的视觉对象级别筛选器** 可向切片器添加视觉对象级别筛选器。 其工作方式与其他任何视觉对象级别筛选器一样，仅筛选切片器本身，而不筛选其他视觉对象。 此筛选器对于筛选出空白或使用度量值筛选器很有用。
- **适用于表和矩阵的图标集** 借助 KPI 图标，可以设置用于在表和矩阵中显示不同图标集的规则，类似于 Excel 中的图标集。
- **视觉对象分组** 现在，可以像在 PowerPoint 中一样，在报表页上对视觉对象、形状、文本框、图像和按钮进行分组。 将对象分组后，可以同时移动它们并调整它们的大小。 借助分组，可以更轻松地使用每个页面中层叠了大量对象的报表。
- **新的默认主题** 为了适应新主题 JSON 选项，我们将更新可用于报表的主题，并更改新报表的默认主题。 新的默认主题既可以更好地与 Microsoft 的设计语言保持一致，又可以遵循视觉对象的最佳设计做法。 
- **更新的窗格设计** 我们刷新了大部分界面。 我们已将所有窗格、页脚和视图切换器更新为较浅的颜色，同时更新了间距，并引入了新图标。 新设计是刷新整个界面的第一步。

以下是功能的完整列表。 

### <a name="reporting"></a>报表

- 更新的窗格设计
- 适用于切片器的视觉对象级别筛选器
- 适用于性能分析器窗格的排序功能
- 视觉对象标头工具提示
- 表和矩阵总计标签自定义
- 层次结构切片器的同步切片器支持
- 视觉对象之间的一致字体大小
- 适用于表和矩阵的图标集
- 按规则进行条件格式设置的百分比支持
- 新的筛选器窗格现已正式发布
- 在散点图上使用播放轴时的数据颜色支持
- 使用相对日期和下拉切片器时的性能改进
- 视觉对象分组
- 主题中的颜色和文本类
- 新的默认主题

### <a name="analytics"></a>Analytics

- 自定义格式字符串
- 格式设置选项的条件格式设置更新

    - 视觉对象背景和标题颜色
    - 卡片颜色
    - 仪表填充和颜色
    - 替换文本
    - 边框颜色

- 条件格式设置警告
- 钻取发现改进
- 新 DAX 表达式：REMOVEFILTERS 和 CONVERT
- 新 DAX 比较运算符：==

### <a name="data-preparation"></a>数据准备工作

- M Intellisense 改进
- 新的转换：按位置拆分列
- 从数据事件探查复制到剪贴板


## <a name="may-2019"></a>2019 年 5 月

### <a name="power-bi-desktop-for-power-bi-report-server"></a>适用于 Power BI 报表服务器的 Power BI Desktop

有关所有新功能的详细信息，请参阅 [Power BI 报表服务器 2019 年 5 月版](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/)博客文章。

以下是该版本的一些要点：

#### <a name="performance-analyzer"></a>性能分析器 

如果报表的运行速度比预期慢，请尝试使用 Power BI Desktop 中的性能分析器。 启动时，它会创建日志文件，其中包含有关在报表中执行的每个操作的信息。 详细了解[性能分析器](../desktop-performance-analyzer.md)。

#### <a name="new-modeling-view"></a>新的建模视图

在 Power BI Desktop 中的新建模视图中，可以查看和使用包含许多表的复杂数据集。 要点包括多种图表布局以及对列、度量值和表的批量编辑。 详细了解[建模视图](../desktop-modeling-view.md)。

#### <a name="accessible-visual-interaction"></a>可访问的视觉对象交互

现在，可以使用键盘导航访问许多内置视觉对象上的数据点。 详细了解 [Power BI 报表中的辅助功能](../desktop-accessibility.md)。

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>条件格式设置标题和 Web URL 操作

Power BI 报表为交互式报表。 报表中的标题为动态标题具有意义，因为可反映报表的当前状态。 可使用相同的表达式绑定格式来使按钮、形状和图像的 URL 动态化。 详细了解[基于表达式的标题](../desktop-conditional-format-visual-titles.md)。

#### <a name="cross-highlight-by-axis-labels"></a>通过轴标签交叉突出显示

选择视觉对象中的轴类别标签以交叉突出显示页面上的其他元素，就像选择视觉对象中的数据点一样。 详细了解[交叉突出显示](../power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting)。

#### <a name="all-the-new-features"></a>所有新功能

以下是所有新功能的列表：

#### <a name="reporting"></a>报表

- 折线图中对单个点的交叉突出显示 
- 标题上的自动换行 
- 更新用于交叉筛选的默认可视交互 ¬
- 视觉对象边框的圆角 
- 单项选择切片器  
- 必应地图的热度地图支持  
- 通过轴标签交叉突出显示  
- 默认工具提示格式设置  
- 按钮、形状和图像的静态 Web URL 支持  
- 页对齐选项   
- 选择窗格改进  
- 可访问的视觉对象交互  
- 视觉对象标题的条件格式设置  
- 按钮、形状和图像的 Web URL 操作的条件格式设置
- 性能分析器窗格
- 表和矩阵键盘导航
- 行数据标签位置控件
- KPI 可视指示器文本大小控件

#### <a name="analytics"></a>Analytics

- 将日期显示为层次结构现已正式发布  

#### <a name="modeling"></a>建模

- 新的建模视图现已正式发布
- 新的 DAX 函数
- ALLSELECTED DAX 函数更新
- 为新报表禁用自动日期表

### <a name="power-bi-report-server"></a>Power BI 报表服务器

#### <a name="support-for-trusted-visuals"></a>对信任视觉对象的支持

我们在 Power BI 报表服务器中添加了对信任视觉对象的支持。 目前，我们支持 Mapbox 和 PowerOn 视觉对象。 此版本不支持 ESRI、Visio 和 PowerApps。

#### <a name="improved-security-features"></a>改进的安全功能

**RestrictedResourceMimeTypeForUpload**，管理员可用于指定以逗号分隔的禁止 mime 类型的列表，例如 text/html。

## <a name="january-2019"></a>2019 年 1 月

Power BI 报表中支持以下功能：

[**行级别安全性**](row-level-security-report-server.md)使用 Power BI 报表服务器设置行级别安全性 (RLS) 可以限制指定用户的数据访问。 筛选器限制行级别的数据访问，你可以定义角色中的筛选器。

[**展开和折叠矩阵行标题**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse)我们添加了扩展和折叠单个行标题的功能，这是需求最大的可视化功能之一。

[**在 .pbix 文件之间复制和粘贴**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste)可以在 .pbix 文件之间复制视觉对象（从视觉对象的上下文菜单中复制，或者使用标准的 Ctrl+C 键盘快捷方式复制），然后使用 Ctrl+V 将其粘贴到另一个报告中。

[**智能对齐参考线**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides)在报表页面上移动对象时，可看到智能对齐参考线，如 PowerPoint 中所示的那样，有助于对齐页面上的所有内容。 只要在页面上拖动或调整某些内容，就会看到智能参考线。 将对象移动到另一个对象附近时，该参考线会快速移动到与另一个对象对齐的位置。

**辅助功能**要列出的辅助功能太多：例如，[字段列表窗格辅助功能支持](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList)。 字段列表窗格完全可供访问。 可以浏览窗格，仅需使用键盘和屏幕阅读器即可实现，还可以使用上下文菜单将字段添加到报告页面。

#### <a name="custom-visuals"></a>自定义视觉对象

- 此版本附带的 API 版本为 2.3。

### <a name="administrator-settings"></a>管理员设置

管理员可以在服务器场的 SSMS 高级属性中设置以下属性：

**AllowedResourceExtensionsForUpload** 设置可以上传到报表服务器的资源扩展。 不要求包含内置文件类型的扩展，如 &ast;.rdl 和 &ast;.pbix。 默认为“&ast;、&ast;.xml、&ast;.xsd、&ast;.xsl、&ast;.png、&ast;.gif、&ast;.jpg、&ast;.tif、&ast;.jpeg、&ast;.tiff、&ast;.bmp、&ast;.pdf、&ast;.svg、&ast;.rtf、&ast;.txt、&ast;.doc、&ast;.docx、&ast;.pps、&ast;.ppt、&ast;.pptx”。 

**SupportedHyperlinkSchemes** 设置以逗号分隔的 URI 方案列表，这些方案可以在允许呈现的超链接操作上定义，或设置“&ast;”，启用所有超链接方案。 例如，设置“http、https”将允许指向“https://www. contoso.com”的超链接，但将删除指向“mailto:bill@contoso.com”或“javascript:window.open(‘ www.contoso.com’, ‘_blank’)”的超链接。 默认为“&ast;”。

## <a name="august-2018"></a>2018 年 8 月

2018 年 8 月，针对 Power BI 报表服务器优化的 Power BI Desktop 版本中新增了很多新功能。 这些功能涉及不同的方面：

- [Reporting](#reporting)
- [分析](#analytics)
- [建模](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>2018 年 8 月版本的亮点

下面这些功能在大量新功能中脱颖而出，尤为值得关注。 有关详细信息，请参阅我们的[博客文章](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/)。

#### <a name="report-theming"></a>报表主题

2018 年 8 月版本的 Power BI 报表服务器中添加了报表主题，可快速为整个报表着色，以匹配主题或公司品牌。 导入主题时，所有图表都会自动更新为使用主题颜色，可从调色板访问主题颜色。 可使用“切换主题”按钮下的“导入主题”选项上传主题文件   。

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

另一个新的条件格式类型是“按字段设置格式”值  。 借助“按字段设置格式”值，可使用通过十六进制代码或名称指定颜色的度量值或列，并将该颜色应用于背景或字体颜色。

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

### <a name="analytics"></a>Analytics

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

## <a name="march-2018"></a>2018 年 3月

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

### <a name="analytics"></a>Analytics

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

现在将分页 (RDL) 报表导出为 PDF 时，可以获取一个可访问/标记的 PDF 文件。 虽然该文件比较大，但更方便屏幕阅读器和其他辅助技术阅读和导航。 通过将 AccessiblePDF 设备信息设置设为“True”，启用可访问的 PDF   。 请参阅 [PDF 设备信息设置](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings)和[更改设备信息设置](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings)。

### <a name="other-improvements"></a>其他改进

- [“从示例中添加列”的改进](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [“咨询服务”快速链接](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [错误报告已改进](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [查看之前遇到的错误](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>2017 年 10 月

### <a name="power-bi-report-data-sources"></a>Power BI 报表数据源

Power BI 报表服务器中的 Power BI 报表可以连接到各种数据源。 可以导入数据和计划数据刷新，或者直接使用 DirectQuery 或与 SQL Server Analysis Services 的实时连接查询数据。 请参阅支持计划的刷新和支持“Power BI 报表服务器中的 Power BI 报表数据源”中的 DirectQuery 的数据源列表。

### <a name="scheduled-data-refresh-for-imported-data"></a>导入的数据的计划数据刷新

在 Power BI 报表服务器中，可以设置计划的数据刷新，以使用嵌入式模型（而不是实时连接或 DirectQuery）使 Power BI 报表中的数据始终保持最新。 由于使用嵌入式模型导入数据，因此它会与原始数据源断开连接。 它需要更新以便数据保持最新状态，而计划的刷新就可以实现这一点。 详细了解“Power BI 报表服务器中 Power BI 报表的计划刷新”。

### <a name="editing-power-bi-reports-from-the-server"></a>从服务器编辑 Power BI 报表

可以从服务器打开和编辑 Power BI 报表 (.pbix) 文件，而且可以找回上传的原始文件。 **如果数据已由服务器刷新，则在首次打开该文件时将不会刷新数据**。 需要在本地手动刷新才能查看更改。

### <a name="large-file-uploaddownload"></a>大型文件上传/下载

可以上传最大 2 GB 的文件（在 SQL Server Management Studio (SSMS) 的报表服务器设置中，此限制默认设置为 1 GB）。  这些文件存储在数据库中，就像它们适用于 SharePoint 一样，并且不需要对 SQL Server 目录进行任何特殊配置。  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>通过 OData 源访问共享数据集

可以使用 OData 源从 Power BI Desktop 访问共享数据集。 有关详细信息，请参阅[在 Power BI 报表服务器中通过 OData 源访问共享数据集](access-dataset-odata.md)。

### <a name="scale-out"></a>横向扩展

此版本支持横向扩展。使用负载均衡器并设置服务器关联以获得最佳体验。 该方案尚未针对横向扩展进行优化，因此，将看到模型可能会在多个节点之间复制。 该方案将在没有网络负载均衡器和粘性会话的情况下运行。 但是，加载模型 N 次时，不仅会看到跨节点的内存过度使用，而且连接之间的性能会下降，因为在模型抵达两个请求之间的新节点时会对其进行流式传输。  

### <a name="administrator-settings"></a>管理员设置

管理员可以在服务器场的 SSMS 高级属性中设置以下属性：

* EnableCustomVisuals：True/False
* EnablePowerBIReportEmbeddedModels：True/False
* EnablePowerBIReportExportData：True/False
* MaxFileSizeMb：默认值现在为 1000
* ModelCleanupCycleMinutes：检查并从内存中收回模型的频率
* ModelExpirationMinutes：根据上次使用时间，定义模型过期并被收回的时长
* ScheduleRefreshTimeoutMinutes：一个模型的数据刷新需要多长时间。 默认为 2 小时。  没有固定上限。

**配置文件 rsreportserver.config**

```xml
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

有一个单独的新 API 适用于将在 Swagger 的 Power BI 报表服务器版本中进行更新的大型文件。 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) 和 Power BI 报表服务器的内存占用情况

Power BI 报表服务器现在可在内部托管 SQL Server Analysis Services (SSAS)。 这并非特定于计划的刷新。 托管 SSAS 可以极大地扩展报表服务器的内存占用情况。 AS.ini 配置文件在服务器节点上可用，因此，如果用户熟悉 SSAS，可能想要更新设置，其中包括最大内存限制和磁盘缓存等。有关详细信息，请参阅 [Analysis Services 中的服务器属性](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services)。

### <a name="viewing-and-interacting-with-excel-workbooks"></a>查看 Excel 工作簿并与之交互

Excel 和 Power BI 包含行业中独一无二的一套工具。 同时，它们使业务分析师更轻松地收集数据、构建数据模型、分析并以可视化方式浏览数据。 除了在 Web 门户中查看 Power BI 报表之外，企业用户现在也可以使用 Power BI 报表服务器中的 Excel 工作簿执行相同的操作，从而向用户提供单个位置来发布和查看其自助服务 Microsoft BI 内容。

我们已发布了[如何将 Office Online Server (OOS) 添加到 Power BI 报表服务器预览环境的演练](excel-oos.md)。 具有批量许可帐户的客户可以从批量许可服务中心免费下载 OOS，并且将具有仅查看功能。 配置后，用户可以查看具有以下特点的 Excel 工作簿并与之交互：

* 没有外部数据源依赖关系
* 实时连接到外部 SQL Server Analysis Services 数据源
* 具有 PowerPivot 数据模型

### <a name="support-for-new-table-and-matrix-visuals"></a>支持新的表和矩阵视觉对象

Power BI 报表服务器现在支持新的 Power BI 表和矩阵视觉对象。 若要创建具有这些视觉对象的报表，需要 2017 年 10 月发布的更新的 Power BI Desktop 版本。 它不能与 Power BI Desktop（2017 年 6 月）版本并行安装。 对于最新版本的 Power BI Desktop，请在 [Power BI 报表服务器下载页](https://powerbi.microsoft.com/report-server/)上选择“高级下载选项”  。

## <a name="june-2017"></a>2017 年 6 月

* Power BI 报表服务器已正式发布 (GA)。

## <a name="may-2017"></a>2017 年 5 月

* Power BI 报表服务器预览版已发布
* 可以在本地发布 Power BI 报表
  * 支持自定义视觉对象
  * 仅支持 Analysis Services 实时连接，今后将会支持更多数据源  。
  * Power BI 移动应用更新为显示在 Power BI 报表服务器中托管的 Power BI 报表
* 通过注释增强了报表协作

## <a name="next-steps"></a>后续步骤

查看下面这些源，以便随时了解 Power BI 报表服务器中的新增功能。

* [Microsoft Power BI 博客](https://powerbi.microsoft.com/blog/)
* [Guy in a Cube YouTube 通道](https://aka.ms/guyinacube)

更多疑问？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

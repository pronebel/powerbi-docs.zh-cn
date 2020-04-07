---
title: 适用于美国各州和地方政府的 COVID-19 跟踪示例
description: 下载并修改包含美国各州和地方 COVID-19 流行病数据的示例报表。
author: LukaszPawlowski-MS
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 432312b5ceb7632e0249d1d7dda6158bf97d0224
ms.sourcegitcommit: 3c51431d85793b71f378c4b0b74483dfdd8411b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2020
ms.locfileid: "80472051"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>适用于美国各州和地方政府的 COVID-19 跟踪示例

Power BI 团队创建了 COVID-19 跟踪示例，可便于美国各州和地方政府发布或自定义关于 COVID-19 的交互式报表。 使用 Power BI Desktop，他们可以分析和直观呈现 COVID-19 数据，以便在市、县、州和国家级别向社区提供信息。 然后，使用 Power BI 的“发布到 Web”，他们可以公开共享此报表，以告知公民。 本文介绍了在你自己的公共故事、博客或网站中使用 Power BI 交互式可视化效果的三种不同方法。

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="包含美国数据的 COVID-19 示例":::

本文介绍了如何：

- 复制嵌入代码，并将它置于你自己的网站上。 
- 进行自定义，如设置特定州的格式。
- 发布到 Power BI 服务。
- 发布到 Web。 
- 将此类数据与另一个源中的数据糅合在一起。 

## <a name="prerequisites"></a>先决条件

必须先满足以下先决条件，然后才能开始使用 Power BI 来呈现你要提供的信息：

- 下载免费的 [Power BI Desktop](https://powerbi.microsoft.com/desktop/) 应用。
- 注册 [Power BI 服务](https://powerbi.microsoft.com/get-started/)。

## <a name="option-1-pre-built-embed-code"></a>选项 1：预建的嵌入代码

Microsoft 已发布示例报表，并创建了“发布到 Web”嵌入代码。 你可以使用嵌入代码来嵌入完整示例（包括国家视图），并在你自己的网站中向下钻取到州和县级别。 建议在发布此类数据前先审阅这篇文章中的[免责声明](#disclaimers)。

若要在你的网站上添加交互式图形，请将以下嵌入代码复制并粘贴到你网页上的相应图形显示位置。  

```
<iframe width="800" height="600" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

嵌入代码是可以插入到任意 HTML 页中的 HTML iFrame 元素。 调整所提供 iFrame 的宽度和高度，以适应你网站的尺寸。 由于示例报表是按 16:9 比例创作，因此请选择维持此比例的尺寸。 正确实现后，显示的图形不带任何额外的灰色边框。 在进行这些更改时，[审阅 iFrame 大小调整提示和技巧](https://docs.microsoft.com/power-bi/service-publish-to-web#tips-and-tricks-for-iframe-height-and-width)会很有用。

## <a name="option-2-customize-the-sample-power-bi-file"></a>选项 2：自定义示例 Power BI 文件

Power BI 文件包含的数据和交互式图形采用 .pbix 文件格式，可以在 Power BI Desktop 中编辑。  

典型的自定义是，将此报表筛选为显示特定州的数据，然后为自定义报表创建你自己的“发布到 Web”嵌入代码。

USAFacts 数据是根据需要归属的 Creative Commons 许可证提供的。 发布此类数据前，请先审阅[免责声明](#disclaimers)。

首先，请[下载 .pbix 文件（单击此处）](https://go.microsoft.com/fwlink/?linkid=2125058)。

### <a name="update-your-report"></a>更新报表 

1. 下载最新版免费应用 [Power BI Desktop](https://powerbi.microsoft.com/desktop/)（如果尚未下载的话）。 

2. 下载 [.pbix 文件](https://go.microsoft.com/fwlink/?linkid=2125058)（如果尚未下载的话），并在 Power BI Desktop 中打开它。

3. 若要将报表筛选为显示特定州的数据，请选择箭头，以展开“筛选器”窗格。

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="展开“筛选器”窗格":::

4. 选中要查看数据的州。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="选中州":::

5. 若要保存文件，请依次选择“文件”   > “保存”  。 

### <a name="refresh-your-report"></a>刷新报表 

1. 选择“刷新”  按钮。

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="“刷新”按钮":::

2. 依次选择“匿名”   > “连接”  。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="选择“匿名”":::

 
3. 选中“忽略隐私级别”  （若显示），然后选择“保存”  。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="选中“忽略隐私级别”":::

### <a name="publish-your-report-to-the-power-bi-service"></a>将报表发布到 Power BI 服务

按照你自己的偏好自定义报表后，[请按照这篇文章中列出的步骤操作，以将报表发布到](../desktop-upload-desktop-files.md) Power BI 服务。

### <a name="configure-scheduled-refresh"></a>配置计划刷新

为了让报表中的数据不断更新，可以在发布报表后[配置计划刷新](../refresh-scheduled-refresh.md)。

按照这些步骤操作时，请选择以下选项：

1. 数据源凭据身份验证方法：匿名
2. 此数据源的隐私级别设置：公用

若要测试刷新设置，请选择[数据集项中提供的“立即刷新”选项](../refresh-data.md#data-refresh)。

每次运行计划刷新，都会加载刷新后的数据。 请注意，基础数据是由 USAFacts 提供的，可能不会像刷新计划一样频繁更新。 若要了解基础数据的上次更新时间，请查看 [USAFacts 网站](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)。 

若要在你的网站上发布自定义报表，最好将计划刷新配置为运行频率不低于 USAFacts 数据更新频率。 由于 USAFacts 可能在每天的不同时间刷新数据，因此你不妨配置为每天刷新多次。 

### <a name="create-a-publish-to-web-embed-code"></a>创建“发布到 Web”嵌入代码 

若要在你自己的网站中嵌入自定义报表，请按照[如何创建你自己的“发布到 Web”嵌入代码](../service-publish-to-web.md#how-to-use-publish-to-web)中的说明操作。

发布嵌入代码后，可以使用“确认”对话框中的 iFrame 将自定义报表嵌入到你的网站中。

如果在 Power BI Desktop 中对报表进行更改，可以在 Power BI 服务中发布并替换现有报表。 嵌入代码不会更改。 报表更改或刷新后的数据大约需要一小时才能显示在你的网站上。 

## <a name="option-3-mash-up-data-from-another-source"></a>选项 3：糅合另一个源中的数据 

还可以将此报表中的数据与另一个源中的数据糅合在一起。 下面的示例所依据的数据来自[约翰斯·霍普金斯大学](https://github.com/CSSEGISandData/COVID-19)。 建议在发布此类数据前先审阅这篇文章中的[免责声明](#disclaimers)。

1. 依次选择“获取数据”   > “Web”  。

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="“获取数据”按钮":::

2. 输入以下 URL：

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="从 Web 选择数据":::

3. 选择“确定”。  

    > [!NOTE]
    > 约翰斯·霍普金斯大学发布的链接可能会更改。 有关最新信息，请查看[约翰斯·霍普金斯大学 GitHub 页](https://github.com/CSSEGISandData/COVID-19)。

4. 选择“加载”  ，以加载全球总确诊病例的数据集。  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="从 Web 加载数据":::

    [从 Power BI Desktop 连接到网页](../desktop-connect-to-web.md)一文详细介绍了如何从 Web 加载数据。
    
然后，可以使用 Power BI Desktop 来直观呈现数据。 最后，按照“选项2：  [将报表发布到 Power BI 服务](#publish-your-report-to-the-power-bi-service)”中的步骤操作，以发布此报表并创建自定义嵌入代码。 


## <a name="about-the-data-source-for-this-report"></a>关于此报表的数据源
此交互式报表汇总了美国疾病控制与预防中心 (CDC) 以及州级和地方级公共卫生机构提供的数据。 县级数据是通过直接咨询州和地方机构（链接）来确认。

数据是由 USAFacts 提供。 鉴于数据更新频率，可能无法反映政府组织或新闻媒体报告的确切数字。 有关详细信息或下载数据，请访问 [USAFacts 网站](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)。 

## <a name="disclaimers"></a>免责声明

此报表和数据是“按原样”提供的，“不保证没有错误”，且没有任何形式的担保。 Microsoft 不提供任何明示担保或保证，并明确声明不提供任何默示担保，包括适销性、特定用途适用性以及不侵犯他人权利的默示担保。

USAFacts 数据是根据 Creative Commons 许可证提供的。 若要使用它，请将 USAFacts 引用为数据提供程序，并链接回 USAFacts。 有关确切的归属步骤，请参阅 USAFacts 页  [美国的冠状病毒疫情：绘制各州和县的 COVID-19 疫情地图](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)的“#MadewithUSAFacts”部分。

约翰斯·霍普金斯大学数据为，版权所有 2020 约翰斯·霍普金斯大学，保留所有权利。 这些数据仅出于教育和学术研究目的公开。 下面是糅合示例中所显示数据的完整[使用条款](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md)。 有关详细信息，请访问[约翰斯·霍普金斯大学网站](https://coronavirus.jhu.edu/map-faq.html)。

## <a name="next-steps"></a>后续步骤

[获取 Power BI 示例](../sample-datasets.md)
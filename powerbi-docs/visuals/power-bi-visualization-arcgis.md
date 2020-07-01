---
title: 创建 ArcGIS Maps for Power BI
description: '创建 Esri 提供的 ArcGIS Maps for Power BI '
author: mihart
ms.reviewer: willt
featuredvideoid: EKVvOZmxg9s
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/29/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: c7a959085ad2099588b182d94567d36281408343
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240354"
---
# <a name="create-arcgis-maps-in-power-bi-desktop"></a>在 Power BI Desktop 中创建 ArcGIS Maps

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

本教程是从 ArcGIS Map for Power BI 创建者的角度进行编写。 设计者与同事共享 ArcGIS Map for Power BI 地图后，此同事便可以查看相应的地图并与之交互，但无法保存更改。 若要详细了解如何查看 ArcGIS 地图，请参阅[与 ArcGIS Maps for Power BI 交互](power-bi-visualizations-arcgis.md)。

> [!NOTE]
> 与 Power BI 同事共享报表时，你和这位同事都应具有独立的 Power BI Pro 许可证，并且应将报表保存在 Premium 容量中。

ArcGIS 地图和 Power BI 的结合将超越地图点表示法的地图绘制技术提升到全新水平。 从基本地图、位置类型、主题、符号样式和引用层中进行选择，创建丰富多彩的信息性地图可视化效果。 地图上权威数据层与空间分析的结合可传达出可视化效果中数据的更深层次的理解。

 虽然无法在移动设备上创建 ArcGIS Maps for Power BI 地图，但可以查看它并与之交互。 请参阅[与 ArcGIS 地图交互](power-bi-visualizations-arcgis.md)。

> [!NOTE]
> Power BI 报表服务器当前无法使用 ArcGIS Maps for Power BI。

> [!TIP]
> GIS 指的是地理信息系统。


下面的示例使用深灰色画布针对 2016 年可支配收入中间值的人口统计层以热度地图形式显示区域销售情况。 随着你不断阅读本教程，你会发现使用 ArcGIS Maps for Power BI 可提供几乎无限制的改进的地图功能、人口数据和更炫的地图可视化功能，这样可以更加完美地讲述你的案例。

![ArcGIS 简介图像](media/power-bi-visualization-arcgis/power-bi-intro-arcgis.png)

> [!TIP]
> 访问 [Esri 的 ArcGIS Maps for Power BI 页面](https://www.esri.com/powerbi)，查看多个示例并阅读推荐证明。 然后查看 Esri 的 [ArcGIS Maps for Power BI 地图入门页](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm)。

## <a name="user-consent"></a>用户须知
ArcGIS Maps for Power BI 由 Esri (https://www.esri.com) 提供。 你使用 ArcGIS Maps for Power BI 必须遵守 Esri 的条款和隐私策略。 Power BI 用户如果希望使用适用于 Power BI 的 ArcGIS 地图视觉对象，则需要接受同意对话框。

资源

[条款](https://go.microsoft.com/fwlink/?LinkID=826322)

[隐私策略](https://go.microsoft.com/fwlink/?LinkID=826323)

[适用于 Power BI 的 ArcGIS 地图产品页](https://www.esri.com/powerbi)


## <a name="prerequisites"></a>先决条件

本教程使用 Power BI Desktop 和 PBIX [零售分析示例](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)。 还可以使用 Power BI 服务创建 ArcGIS Maps for Power BI。 

1. 在菜单栏的左上角，选择“文件”\>“打开” 
   
2. 查找本地计算机中保存的**零售分析示例 PBIX 文件**。

1. 在报表视图 ![报表视图图标的屏幕截图。](media/power-bi-visualization-kpi/power-bi-report-view.png) 中，打开“零售分析示例”。

1. 选择 ![黄色选项卡的屏幕截图。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) ，以添加新报表页。

   
## <a name="create-an-arcgis-maps-for-power-bi-map-visualization"></a>创建 ArcGIS Maps for Power BI 地图可视化效果

Watch 将创建几个不同的可视化效果，然后使用以下步骤通过[零售分析示例 .PBIX 文件](../create-reports/sample-datasets.md)亲自尝试一下。
    

   > [!NOTE]
   > 此视频使用较旧版本的 Power BI Desktop。
   > 

> [!VIDEO https://www.youtube.com/embed/EKVvOZmxg9s]


1. 从“可视化效果”窗格中选择 ArcGIS Maps for Power BI 图标。
   
    ![ArcGIS 地图的可视化效果窗格](media/power-bi-visualization-arcgis/power-bi-viz-pane.png)    

2. Power BI 向报表画布中添加空模板。 在本教程中我们将使用免费版本。
   
   ![ArcGIS 可视化效果占位符](media/power-bi-visualization-arcgis/power-bi-sign-in.png)


3. 从“**字段**”窗格中，拖动一个数据字段到“**位置**”或“**纬度**”和/或“**经度**”框。 在此示例中，我们使用“存储 > 城市”。
   
   > [!NOTE]
   > ArcGIS Maps for Power BI 会自动检测已选字段显示为地图上的形状或点是否是最佳方式。 可以调整设置中的默认值（如下所示）。
   > 
   > 
   
    ![ArcGIS 字段窗格](media/power-bi-visualization-arcgis/power-bi-fields-pane3new.png)

4. 从“字段”窗格中，拖动一个度量值到“大小”框，以调整数据的显示方式。 在本示例中，我们使用“销售额 > 去年销售额”。
   
    ![Esri 点图可视化效果](media/power-bi-visualization-arcgis/power-bi-esri-point-map-size2new.png)

你已为 Power BI 地图创建第一个 ArcGIS 地图。 现在，让我们使用基本地图、位置类型、主题等改进地图并设置其格式。

## <a name="settings-and-formatting-for-arcgis-maps-for-power-bi"></a>ArcGIS Maps for Power BI 设置和格式
若要访问 ArcGIS Maps for Power BI 的格式化功能，请执行以下操作：

1. 通过选择可视化效果右上角的“更多选项”(…)，然后选择“编辑”，访问其他功能 。
   
   ![ArcGIS 编辑窗格](media/power-bi-visualization-arcgis/power-bi-edit2.png)
   
   可视化效果将展开，且可用的功能显示在顶部。 当选择每个功能时，可打开相应的任务窗格，其中提供详细的选项。<br/>
   
   ![Esri 功能窗格](media/power-bi-visualization-arcgis/power-bi-esri-features-new.png)
   

> [!TIP]
> Esri 针对 ArcGIS Maps for Power BI 的功能集提供[综合文档](https://go.microsoft.com/fwlink/?LinkID=828772)。


### <a name="base-maps"></a>基本地图
提供了四个基本地图：暗灰色画布、浅灰色画布、OpenStreetMap 和街道。  街道是 ArcGIS 的标准基本地图。

若要应用基本地图，在任务窗格中选择它。

![Esri 基本地图视觉对象](media/power-bi-visualization-arcgis/power-bi-esri-base-maps-new.png)

### <a name="location-type"></a>位置类型
ArcGIS Maps for Power BI 自动检测在地图上显示数据的最佳方法。 从点或边界中进行选择。 可以使用位置类型选项微调这些选择。

![Esri 位置类型示例](media/power-bi-visualization-arcgis/power-bi-esri-location-types-new.png)

仅当数据包含标准地理位置值时，边界才可使用。 ArcGIS Maps for Power BI 自动找出要在地图上显示的形状。 标准地理位置值包括国家/地区、省、邮政编码等。但是和 GeoCoding 一样，默认情况下 Power BI 不会为数据检测字段是否为边界，或者找不到数据边界。  

### <a name="map-theme"></a>地图主题
提供了四个地图主题。 Power BI 根据添加到“位置”和“大小”存储桶的字段，自动选择“仅位置”或“大小”主题   。 由于我们已将字段添加到这两个存储桶，因此地图已默认为“大小”。 请先尝试其他主题并返回到“大小”，然后再继续下一步。  

![Esri 地图主题示例](media/power-bi-visualization-arcgis/power-bi-esri-map-theme-new.png)

<table>
<tr><th>主题</th><th>说明</th>
<tr>
<td>仅位置</td>
<td>基于添加到“位置”存储桶中的字段，在地图上绘制数据点或已填充的边界。</td>
</tr>
<tr>
<td>热图</td>
<td>在地图上绘制数据的热度。 活跃度或值较高的区域由更强更亮的颜色表示。 </td>
</tr>
<tr>
<td>大小</td>
<td>基于添加到“大小”存储桶中的字段，在地图上绘制数据点。</td>
</tr>
<tr>
<td>聚类</td>
<td>指定群集半径内的点统一归入一个符号，该符号表示该地图区域中的点数。 </td>
</tr>
</table>


### <a name="symbol-style"></a>符号样式
使用符号样式可以对地图上数据的显示方式进行精细调整。 根据所选的位置类型和地图主题，符号样式会有所不同。 以下示例演示如何将地图主题设置为“大小”，以及如何进行透明度、样式和大小的多个符号样式调整。 

![Esri 符号样式示例](media/power-bi-visualization-arcgis/power-bi-esri-symbol-style-new.png)

### <a name="pins"></a>固定
通过添加固定内容引起对地图上点的注意。  

1. 选择“固定内容”选项卡。
2. 在搜索框中键入关键字（如地址、地点和兴趣点），再从下拉列表中进行选择。 地图上会显示一个符号，并会自动缩放到相应位置。 搜索结果将会保存为“大头针”窗格中的位置卡。 最多可以保存 10 张位置卡。
   
   ![ArcGIS 地图固定示例](media/power-bi-visualization-arcgis/power-bi-southampton.png)
3. Power BI 将固定内容添加到该位置，你可以更改固定内容的颜色。
   
   ![固定颜色示例](media/power-bi-visualization-arcgis/power-bi-pins.png)
4. 添加和删除固定内容。
   
   ![固定添加和删除示例](media/power-bi-visualization-arcgis/power-bi-pins3.png)

### <a name="drive-time"></a>行驶时间
使用“驾驶时间”窗格，可以选择一个位置，然后确定在指定半径区域或驾驶时间内可用的其他地图功能。 下面的示例显示华盛顿方圆 50 英里范围。  按照以下步骤操作，创建自己的驾驶时间层。 
    ![驾驶时间示例](media/power-bi-visualization-arcgis/power-bi-esri-drive-time.png)

1. 选择单个选择工具，然后选择图钉或气泡。 在此示例中，我们为 Charlotte Douglas 机场选择了一个图钉

   ![单选固定示例](media/power-bi-visualization-arcgis/power-bi-clt.png)
   
   > [!TIP]
   > 如果放大地图，选择位置将更加容易。 可以使用“+”图标或通过鼠标滚动来放大。
   > 
   > 
2. 假设你在几天内将飞抵 Charlotte Douglas 机场，并想知道哪家连锁商店位于合理的驾驶距离以内。 将搜索区域更改为“驾驶时间”，将距离更改为 25 分钟 。 选择“确定”。    
   
    ![驾驶时间半径](media/power-bi-visualization-arcgis/power-bi-esri-drive-time-radius.png)

    

3. 25 分钟的驾驶距离以内有两家商店。 半径区域显示为紫色。 选择任何一个位置，显示它的详细信息。 （可选）更改颜色和边框，设置半径区域格式。
   
    ![带颜色和边框的半径格式示例](media/power-bi-visualization-arcgis/power-bi-drive.png)

### <a name="reference-layer"></a>引用层
#### <a name="reference-layer---demographics"></a>引用层 — 人口统计
ArcGIS Maps for Power BI 中可选择人口统计信息层，这些图层可以为 PowerBI的数据提供相关的对照信息。

1. 选择“引用层”选项卡，然后选择“人口统计”。
2. 所列出的每一个图层都带有一个复选框。 勾选图层即可将该图层添加到地图中。  在此示例中，我们已将家庭平均收入图层添加到地图中。<br/>
   
    ![引用层人口统计示例](media/power-bi-visualization-arcgis/power-bi-demographics.png)
3. 每一个图层都可以进行交互式操作。 将鼠标悬停在气泡上，查看详细信息。 单击阴影区域，以图表形式查看详细信息。 在此，我们选择邮政编码 28227，有两个图表可供我们查看。
   
    ![引用层详细信息示例](media/power-bi-visualization-arcgis/power-bi-esri-reference-details.png)

#### <a name="reference-layer---arcgis"></a>引用层 — ArcGIS
ArcGIS Online 允许组织发布公共的 Web 地图。 另外，Esri 还通过 Living Atlas 提供了一套精选的 Web 地图集。 在 ArcGIS 选项卡中，可以搜索所有的公共 Web 地图或 Living Atlas 地图，并将搜索到的地图作为引用层添加到地图中。

1. 选择“引用层”选项卡，然后选择“ArcGIS”。
2. 输入搜索词，然后选择一个地图图层。 在本例中我们选择美国参议院选区分布图。
   
    ![Esri 人口统计示例](media/power-bi-visualization-arcgis/power-bi-reference-details.png)
3. 若要查看详细信息，请选择阴影区域以打开“从引用层选择”：对引用层上的所选内容边界或对象使用引用层选择工具。

<br/>

## <a name="selecting-data-points"></a>选择数据点
ArcGIS Maps for Power BI 允许通过五种选择模式来帮助准确、快速地选择数据。

通过将光标悬停在下图所示的单选工具图标上，更改选择模式。 此操作将展开隐藏栏以显示其他工具：

![Esri 选择工具](media/power-bi-visualization-arcgis/power-bi-esri-selection-tools2.png)

每个工具在允许选择数据方面都具有独特的作用： 

![Esri 单选](media/power-bi-visualization-arcgis/power-bi-esri-selection-single2.png) 选择单个数据点。

![Esri 选择框](media/power-bi-visualization-arcgis/power-bi-esri-selection-marquee2.png) 在地图上绘制一个矩形框来选择包含的数据点。

![Esri 选择引用层](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-layer2.png) 利用引用层中的边界或多边形来选择所包含的数据点。

![Esri 选择缓冲层](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-buffer.png) 允许使用缓冲层选择数据。

![Esri 选择相似选择](media/power-bi-visualization-arcgis/power-bi-esri-selection-reference-similar.png) 允许选择彼此相似的数据点。

> [!NOTE]
> 一次最多可选择 250 个数据点。
> 
> 

<br/>

## <a name="getting-help"></a>获取帮助
Esri 针对 ArcGIS Maps for Power BI 的功能集提供[综合文档](https://go.microsoft.com/fwlink/?LinkID=828772)。

可以在 [Power BI 社区中与**适用于 Power BI 的 ArcGIS 地图**相关的帖子](https://go.microsoft.com/fwlink/?LinkID=828771)中提问题和查找最新信息，报告问题并查找答案。

如果有改进建议，可以将建议提交到 [Power BI 建议列表](https://ideas.powerbi.com)。

<br/>

## <a name="managing-use-of-arcgis-maps-for-power-bi-within-your-organization"></a>管理组织中的 ArcGIS Maps for Power BI 的使用方式
Power BI 允许设计者、租户管理员、IT 管理员设置 ArcGIS Maps for Power BI 的使用。 在下面可找到每个角色可执行的步骤。 

### <a name="designer-options"></a>设计者选项
在 Power BI Desktop 中，设计者可以在“安全”选项卡上禁用 ArcGIS Maps for Power BI。选择“文件” > “选项和设置”，然后选择“选项” > “安全”   。 禁用后，默认不会加载 ArcGIS Maps。

![桌面安全性对话框示例](media/power-bi-visualization-arcgis/power-bi-desktop-security-dialog2.png)

### <a name="tenant-admin-options"></a>租户管理员选项
在 PowerBI.com 中，租户管理员可以为所有用户禁用 ArcGIS Maps for Power BI。 选择“设置” > “管理门户” > “租户设置”  。 禁用后，Power BI 不再能在“可视化效果”窗格中显示 ArcGIS Maps for Power BI 图标。

![ArcGIS 管理门户示例](media/power-bi-visualization-arcgis/power-bi-arcgis-admin-portal2.png)

### <a name="it-administrator-options"></a>IT 管理员选项
Power BI Desktop 支持使用**组策略**在整个组织内的已部署计算机上禁用 ArcGIS Maps for Power BI。

<table>
<tr><th>属性</th><th>值</th>
</tr>
<tr>
<td>键</td>
<td>Software\Policies\Microsoft\Power BI Desktop</td>
</tr>
<tr>
<td>值名称</td>
<td>EnableArcGISMaps</td>
</tr>
</table>

值为 1（十进制），启用 ArcGIS Maps for Power BI。

值为 0（十进制），禁用 ArcGIS Maps for Power BI。

## <a name="considerations-and-limitations"></a>注意事项和限制
以下服务和应用支持适用于 Power BI 的 ArcGIS 地图：

<table>
<tr><th>服务/应用</th><th>是否支持</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>是</td>
</tr>
<tr>
<td>Power BI 服务 (app.powerbi.com)</td>
<td>是</td>
</tr>
<tr>
<td>Power BI 移动应用程序</td>
<td>是</td>
</tr>
<tr>
<td>Power BI 发布到 Web</td>
<td>否</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>否</td>
</tr>
<tr>
<td>Power BI 服务嵌入 (PowerBI.com)</td>
<td>否</td>
</tr>
</table>

在不支持适用于 Power BI 的 ArcGIS 地图的服务或应用中，可视化效果将显示为带 Power BI 徽标的空视觉对象。

对街道地址进行地理编码时，只会对前 1500 个地址进行地理编码。 对地名或国家/地区进行地理编码时，没有前 1500 个地址限制。

<br/>

**ArcGIS Maps for Power BI 如何运作？**
ArcGIS Maps for Power BI 由 Esri (https://www.esri.com) 提供。 使用 ArcGIS Maps for Power BI 时，必须遵守 Esri 的[条款](https://go.microsoft.com/fwlink/?LinkID=8263222)和[隐私策略](https://go.microsoft.com/fwlink/?LinkID=826323)。 Power BI 用户如果希望使用适用于 Power BI 的 ArcGIS 地图视觉对象，则需要接受同意对话框（有关详细信息，请参阅《用户同意》）。  使用 Esri 的 ArcGIS Maps for Power BI 时，必须遵守 Esri 的条款和隐私策略，同意对话框具有相关链接。 每个用户在首次使用 ArcGIS Maps for Power BI 之前，必须同意条款和隐私策略。 一旦用户接受同意，绑定到视觉对象的数据至少会发送到 Esri 的服务以进行地理编码，这意味着将位置信息转换为可以在地图中表示经度和纬度的信息。 应该假定可以将绑定到数据可视化效果的任意数据发送到 Esri 的服务。 Esri 提供基本地图、空间分析和地理编码之类的服务。ArcGIS Maps for Power BI 视觉对象与使用 SSL 连接的这些服务进行交互，该连接由 Esri 提供和维护的证书保护。 可以从 Esri 的 [ArcGIS Maps for Power BI 产品页](https://www.esri.com/powerbi)获取 ArcGIS Maps for Power BI 的其他信息。

当用户通过 ArcGIS Maps for Power BI 注册由 Esri 提供的 Plus 订阅时，他们与 Esri 建立了直接关系。 Power BI 不向 Esri 发送有关用户的个人信息。 用户使用自己的 AAD 身份登录并信任 Esri 提供的 AAD 应用程序。 通过此操作，用户直接与 Esri 共享其个人信息。 一旦用户将 Plus 内容添加到 ArcGIS Maps for Power BI 视觉对象，其他 Power BI 用户也需要 Esri 的 Plus 订阅才能查看或编辑该内容。 

有关 ArcGIS Maps for Power BI 的工作原理的详细技术问题，请通过其支持站点与 Esri 联系。

**向 Esri 发送哪些数据？**
可以在[文档站点](https://doc.arcgis.com/en/maps-for-powerbi/get-started/data-transfer.htm)中了解有关向 Esri 传输哪些数据的信息。

使用适用于 Power BI 的 ArcGIS 地图需要付费吗？

ArcGIS Map for Power BI 由 Esri 提供，无需额外付费。 你必须同意用户协议。  

**我在 Power BI Desktop 中看到关于缓存已满的错误消息**

我们正在修复此 bug。  在此期间，若要清除缓存，请尝试删除以下位置的文件：C:\Users\\AppData\Local\Microsoft\Power BI Desktop\CEF，然后重启 Power BI。

适用于 Power BI 的 ArcGIS 地图是否支持 Esri 形状文件？

ArcGIS Maps for Power BI 自动检测诸如国家/地区、州/省，以及邮政编码等标准边界。 如果需要提供自定义的形状，可以使用 [Shape Maps for Power BI Desktop](desktop-shape-map.md) 来操作。

是否能够离线查看 ArcGIS 地图？

否，Power BI 需要网络连接才能显示地图。

可以从 Power BI 连接我的 ArcGIS Online 帐户吗？

目前还不行。 [投票支持此建议](https://ideas.powerbi.com/forums/265200-power-bi-ideas/suggestions/9154765-arcgis-geodatabases)吧。等我们着手开发此功能时，我们会向你发送一封电子邮件。  

## <a name="next-steps"></a>后续步骤
[与已与你共享的 ArcGIS 地图交互](power-bi-visualizations-arcgis.md)

[宣布推出适用于 Power BI 的 ArcGIS 地图的博客文章](https://powerbi.microsoft.com/blog/announcing-arcgis-maps-for-power-bi-by-esri-preview/)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)



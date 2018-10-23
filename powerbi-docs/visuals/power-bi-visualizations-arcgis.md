---
title: 与已与你共享的 ArcGIS 地图交互
description: '在读取视图中使用 ArcGis 地图 '
author: mihart
manager: kvivek
ms.reviewer: ''
tags: power bi, service, desktop, mobile
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: mihart
ms.openlocfilehash: 2c7a9d5f6bdbbfff905f3faa8cec255c2b85a0d5
ms.sourcegitcommit: a3ce866caba24217bcdd011e892b9ea72f3d2400
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2018
ms.locfileid: "49396787"
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>在 Power BI 中与 ArcGIS 地图交互
本主题是从在 Power BI 服务、Power BI Desktop 或 Power BI 移动应用中使用 ArcGIS 地图的人员的角度进行编写。 创建者与你共享 ArcGIS 地图后，便可以通过多种方式与相应地图进行交互。  若要详细了解如何创建 ArcGIS 地图，请参阅 [ESRI ArcGIS 地图教程](../power-bi-visualization-arcgis.md)。

ArcGIS 地图和 Power BI 的结合将超越地图点表示法的地图绘制技术提升到全新水平。 可以使用“基本地图”、“位置类型”、“主题”、“符号样式”和“引用层”选项，创建极具描述性的地图可视化效果。 将地图上的权威数据层（如统计数据）与空间分析相结合，可以让用户更深入地了解可视化效果中的数据。

> [!TIP]
> GIS 指的是地理信息科学。
> 

我们使用的示例就是在 [ESRI ArcGIS 地图教程](../power-bi-visualization-arcgis.md)中创建的 ArcGIS 地图。 它按城市显示去年销售额，并使用街道基本地图、表示大小的气泡符号和平均家庭收入引用层。 此地图包含 3 个大头针和一个驾驶时间半径区域（紫色）。

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> 请访问 [ESRI 上的 Power BI 页面](https://www.esri.com/powerbi)，查看多个示例并阅读用户感言。 然后查看 ESRI 的[适用于 Power BI 的 ArcGIS 地图入门页](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm)。
> 
> 

<br/>

## <a name="user-consent"></a>用户须知
同事首次与你共享 ArcGIS 地图时，Power BI 会显示一条提示。 适用于 Power BI 的 ArcGIS 地图由 Esri(www.esri.com) 提供，使用 ArcGIS Maps for Power BI 时，必须遵守 Esri 的条款和隐私策略。 若要使用适用于 Power BI 的 ArcGIS 地图视觉对象，Power BI 用户必须接受同意对话框。

## <a name="selection-tools"></a>选择工具
ArcGIS Maps for Power BI 有三种选择模式。 一次最多可选择 250 个数据点。

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) 选择单个数据点。

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) 在地图上绘制一个矩形框来选择包含的数据点。 按 CTRL 可以选择多个矩形区域。

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) 利用引用层中的边界或多边形来选择所包含的数据点。

<br/>

## <a name="interacting-with-an-arcgis-map"></a>与 ArcGIS 地图交互
具体可以使用哪些功能取决于你是创建者（地图创建者）还是使用者（其他人与你共享了 ArcGIS 地图）。 如果是以使用者的身份与 ArcGIS 地图进行交互（亦称[阅读视图](../consumer/end-user-reading-view.md)），则可执行下列操作。

* 与其他可视化效果类型一样，可以[固定到仪表板](../service-dashboard-pin-tile-from-report.md)、[查看](../consumer/end-user-show-data.md)和/或[导出基础数据](power-bi-visualization-export-data.md)，并在[焦点模式](../consumer/end-user-focus.md)和[全屏模式](../service-fullscreen-mode.md)下查看地图。    
* 展开“筛选器”窗格，以使用筛选器浏览地图。 关闭报表时，不会保存所应用的筛选器。    
    ![](media/power-bi-visualizations-arcgis/power-bi-filter-newer.png)  
* 如果地图有引用层，请选择要在工具提示中显示详细信息的位置。 此时，我们选择的是亚当斯县，以查看创建者在地图中添加的平均家庭收入引用层中的数据。
  
    ![](media/power-bi-visualizations-arcgis/power-bi-reference-layer.png)  
  
    在此示例中，我们还看到一个图表。 选择图表的条形，以深入探究数据。 此时，我们看到亚当斯县 79 个家庭的收入不低于 200,000 美元。
  
    ![](media/power-bi-visualizations-arcgis/power-bi-tooltip-chart.png)
  
    选择箭头可以查看其他任何图表。
* 将鼠标悬停在基本地图位置符号之上，在工具提示中显示详细信息。     
  ![](media/power-bi-visualizations-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > 建议放大地图来选择特定位置。  否则，如果位置重叠，Power BI 可能会一次显示多个工具提示。 选择箭头可以切换工具提示
  > 
  > ![](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)
  > 
  > 
* 如果创建者已将信息图层添加到 ArcGIS 地图，地图右上角会显示其他数据。  例如，在此示例中，地图创建者添加了“未满 14 岁的儿童”。
  
    ![](media/power-bi-visualizations-arcgis/power-bi-demographics.png)

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

**ArcGIS Maps for Power BI 如何运作？**
ArcGIS Maps for Power BI 由 Esri (www.esri.com) 提供。 使用 ArcGIS Maps for Power BI 时，必须遵守 Esri 的[条款](https://go.microsoft.com/fwlink/?LinkID=8263222)和[隐私策略](https://go.microsoft.com/fwlink/?LinkID=826323)。 Power BI 用户如果希望使用适用于 Power BI 的 ArcGIS 地图视觉对象，则需要接受同意对话框（有关详细信息，请参阅《用户同意》）。  使用 Esri 的 ArcGIS Maps for Power BI 时，必须遵守 Esri 的条款和隐私策略，同意对话框具有相关链接。 每个用户在首次使用 ArcGIS Maps for Power BI 之前，必须同意条款和隐私策略。 一旦用户接受同意，绑定到视觉对象的数据至少会发送到 Esri 的服务以进行地理编码，这意味着将位置信息转换为可以在地图中表示经度和纬度的信息。 应该假定可以将绑定到数据可视化效果的任意数据发送到 Esri 的服务。 Esri 提供基本地图、空间分析和地理编码之类的服务。ArcGIS Maps for Power BI 视觉对象与使用 SSL 连接的这些服务进行交互，该连接由 Esri 提供和维护的证书保护。 可以从 Esri 的 [ArcGIS Maps for Power BI 产品页](https://www.esri.com/powerbi)获取 ArcGIS Maps for Power BI 的其他信息。

当用户通过 ArcGIS Maps for Power BI 注册由 Esri 提供的 Plus 订阅时，他们与 Esri 建立了直接关系。 Power BI 不向 Esri 发送有关用户的个人信息。 用户使用自己的 AAD 身份登录并信任 Esri 提供的 AAD 应用程序。 通过此操作，用户直接与 Esri 共享其个人信息。 一旦用户将 Plus 内容添加到 ArcGIS Maps for Power BI 视觉对象，其他 Power BI 用户也需要 Esri 的 Plus 订阅才能查看或编辑该内容。 

有关 ArcGIS Maps for Power BI 的工作原理的详细技术问题，请通过其支持站点与 Esri 联系。

**ArcGIS 地图未显示**    
在不支持适用于 Power BI 的 ArcGIS 地图的服务或应用中，可视化效果将显示为带 Power BI 徽标的空视觉对象。

**地图上并非显示我的所有地址**    
对街道地址进行地理编码时，只会对前 1500 个地址进行地理编码。 对地名或国家/地区进行地理编码时，没有前 1500 个地址限制。

使用适用于 Power BI 的 ArcGIS 地图需要付费吗？

所有 Power BI 用户都可以使用适用于 Power BI 的 ArcGIS 地图，无需额外付费。 此组件由 Esri 提供，应在本文前面所述的由 Esri 提供的使用条款及隐私政策的限制下使用此组件。

**我看到关于缓存已满的错误消息**

我们正在修复此 bug。  在此期间，请选择错误消息中的链接，了解如何清除 Power BI 缓存。

是否能够离线查看 ArcGIS 地图？

否，Power BI 需要网络连接才能显示地图。

## <a name="next-steps"></a>后续步骤
获取帮助：Esri 提供了有关适用于 Power BI 的 ArcGIS 地图功能集的[综合文档](https://go.microsoft.com/fwlink/?LinkID=828772)。

可以在 [Power BI 社区中与**适用于 Power BI 的 ArcGIS 地图**相关的帖子](https://go.microsoft.com/fwlink/?LinkID=828771)中提问题和查找最新信息，报告问题并查找答案。

如果有改进建议，可以将建议提交到 [Power BI 建议列表](https://ideas.powerbi.com)。

[适用于 Power BI 的 ArcGIS 地图产品页](https://www.esri.com/powerbi)


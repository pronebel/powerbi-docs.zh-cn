---
title: Power BI 中的着色地图（等值线图）
description: 有关在 Power BI 中创建着色地图（等值线图）的文档
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: ef03a562351b8f4487e4822ef28b89009ee5cbb4
ms.sourcegitcommit: 80961ace38ff9dac6699f81fcee0f7d88a51edf4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56223481"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Power BI 中的着色地图（等值线图）
着色地图使用明暗度、颜色或图案来显示不同地理位置或区域之间的值在比例上有何不同。  使用从浅（不太频繁/较低）到深（较频繁/较多）的明暗度快速显示这些相对差异。    

![美国地图](media/power-bi-visualization-filled-maps-choropleths/large_map.png)

## <a name="what-is-sent-to-bing"></a>发动到必应的数据
Power BI 与必应相集成，提供默认地图坐标（一个称为地理编码的过程）。 在 Power BI 服务或 Power BI Desktop 中创建地图可视化效果时，“位置”、“纬度”和“经度”存储桶中的数据（用于创建该可视化效果）将发送到必应。

你或管理员可能需要更新防火墙，以允许访问必应用来地理编码的 URL。  这些 URL 是：
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

有关发送到必应的数据的详细信息，以及提高地理编码成功率的提示，请参阅[地图可视化效果的提示和技巧](power-bi-map-tips-and-tricks.md)。

## <a name="when-to-use-a-filled-map"></a>何时使用着色地图
着色地图适用情况：

* 要在地图上显示定量信息。
* 要显示空间模式和关系。
* 你的数据已进行标准化处理。
* 处理社会经济数据时。
* 当定义的区域很重要时。
* 要获取跨地理位置的分布的概况。

### <a name="prerequisites"></a>先决条件
- Power BI 服务或 Power BI Desktop
- 销售和市场营销示例

若要继续，本教程使用 Power BI 服务，而非 Power BI Desktop。

## <a name="create-a-basic-filled-map"></a>创建基本的着色地图
在此视频中，Kim 将创建基本地图并将其转换为着色地图。

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="get-data-and-add-a-new-blank-page-to-the-report"></a>获取数据并在报表中添加新的空白页面
1. 若要创建你自己的着色地图，请[下载销售和市场营销示例](../sample-datasets.md)，具体方法是登录 Power BI，然后依次选择“获取数据”**\>“示例”“销售和市场营销”\>\>“连接”。**
2. 出现成功消息时，将其关闭并选择“报表”选项卡。然后选择“销售和市场营销示例”以打开报表。

   ![报表内容列表](media/power-bi-visualization-filled-maps-choropleths/power-bi-content-reports2.png)
3. Power BI 将打开报表。 选择“编辑报表”在[编辑视图](../service-interact-with-a-report-in-editing-view.md)中打开报表。

4. 通过选择报表画布底部的黄色加号添加新页面。

    ![“报告”选项卡](media/power-bi-visualization-filled-maps-choropleths/power-bi-new-page.png)

### <a name="create-a-filled-map"></a>创建着色地图
1. 从“字段”窗格中，选择“地区”\>“状态”字段。    

   ![“状态”旁的黄色复选标记](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
5. [将图表转换](power-bi-report-change-visualization-type.md)为着色地图。 请注意，州现在位于位置框中。 必应地图使用位置框中的字段创建地图。  该位置可以是各种有效位置：国家/地区、州、县、市、邮政编码或其他邮政编码等。必应地图可提供世界各地的着色地图形状。 如果“位置”框中没有有效的条目，则 Power BI 无法创建着色地图。  

   ![突出显示着色地图图标的模板](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. 筛选地图使其只显示美国大陆。

   a.  在“可视化效果”窗格底部，查找筛选器区域。

   b.  将鼠标悬停在州上方，然后单击 v 形展开图标  
   ![显示“状态(全部)”的视觉对象级别筛选器](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  在“全部”旁边添加复选标记，并删除 AK 旁边的复选标记。

   ![未选中“全部”和“AK”的“状态”下拉列表](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. 选择“销售数据”\>“消费意愿”以将其添加到“颜色饱和度”框中。 “颜色饱和度”中的字段可很好地控制地图明暗度。  
   ![“色彩饱和度”字段中的消费意愿](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map.png)
8. 着色地图为绿色和红色，其中红色代表较低的消费意愿数值，绿色代表较高、较积极的消费意愿。  此处我突出显示了怀俄明州 (WY)，可以看见该州的消费意愿很好，为 74。  
   ![显示状态和消费意愿的黑色对话框](media/power-bi-visualization-filled-maps-choropleths/power-bi-wy.png)
9. [保存报表](../service-report-save.md)。
##    <a name="adjust-the-color-formatting"></a>调整颜色格式
Power BI 让你可以充分控制着色地图的外观。
1. 选择滚动油漆刷图标，打开格式窗格。

    ![“格式设置”窗格](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-colors.png)

2. 选择“数据颜色”以显示颜色选项。
3. 将“最小值”和“最大值”颜色设置为黄色和蓝色。 并根据数据添加“最小值”和“最大值”。 使用这些控件，直到你获得所需的外观。 

    ![非散射色](media/power-bi-visualization-filled-maps-choropleths/power-bi-color.png)

## <a name="highlighting-and-cross-filtering"></a>突出显示和交叉筛选
有关使用筛选器窗格的信息，请参阅[向报表添加筛选器](../power-bi-report-add-filter.md)。

突出显示着色地图中的某个位置可交叉筛选报表页上的其他可视化效果，反之亦然。

1. 要继续操作，请先选择“文件”>“保存”以保存此报表。 

2. 使用 CTRL-C 复制着色地图。

3. 从报表画布的底部，选择“情绪”选项卡以打开“情绪”报表页面。

    ![选中的“情绪”选项卡](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. 移动页面上的可视化效果并调整大小以腾出一些空间，然后按 CTRL-V 粘贴上一报表中的着色地图。

   ![已添加到“情绪”页面的着色地图](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. 在着色地图中选择一个州。  这样可以突出显示页面上的其他可视化效果。 例如，选择德克萨斯州，显示“情绪”是 74，德克萨斯州在中区\# 23。   
   ![已选择德克萨斯州](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. 在“VanArsdel - 人气（按月份）”折线图上选择一个数据点。 这会筛选着色地图，以显示 VanArsdel 的情绪数据，而不是他们的竞争对手。  
   ![新的底纹](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
地图数据可以是模棱两可的。  例如，可以有法国的巴黎，但也可以有德克萨斯州的巴黎。 地理数据可能存储在单独的列中 – 城市名称的列、州或省名称的列，等等 — 因此必应可能无法区分巴黎是哪个巴黎。 如果数据集已经包含纬度和经度数据，那么 Power BI 可以提供特殊的字段使地图数据不再模棱两可。 只需将包含纬度数据的字段拖放到“可视化效果”\>“纬度”区域。  对经度数据执行相同操作。    

![“可视化效果”和“字段”窗格](media/power-bi-visualization-filled-maps-choropleths/pbi_latitude.png)

如果你具有编辑 Power BI Desktop 中的数据集的权限，则观看该视频有助于解决地图数据的模糊性。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

如果你没有访问纬度和经度数据的权限，则[按照这些说明来更新你的数据集](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7)。

有关地图可视化效果的更多帮助，请参阅 [Tips and tricks for map visualizations（地图可视化效果的提示和技巧）](../power-bi-map-tips-and-tricks.md)。

## <a name="next-steps"></a>后续步骤

[形状映射](desktop-shape-map.md)

[Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)
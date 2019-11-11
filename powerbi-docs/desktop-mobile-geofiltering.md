---
title: 在 Power BI Desktop 中为移动应用设置地理筛选器
description: 在 Power BI Desktop 的模型中设置地理位置筛选时，可以在 Power BI 移动应用中自动筛选你所在地理位置对应的数据。
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: c054bc933cb1eaac7475ac0c7649c7e0f77f503b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878084"
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>在 Power BI Desktop 中为移动应用设置地理筛选器
在 Power BI Desktop 中，可以针对列进行[地理数据分类](desktop-data-categorization.md)，以便 Power BI Desktop 知道如何处理报表中可视化对象的值。 还有一个好处就是，当你或你的同事在 Power BI 移动应用中查看相应的报表时，Power BI 会自动提供与你所在地理位置匹配的地理位置筛选器。 

比如说，你是一名需要会见客户的销售经理，那么你会想要快速筛选出目标客户的销售总额和收入。 你想要按省/自治区、城市或实际地址对当前位置的数据进行分类。 之后，如果还有时间，你会想要去拜访附近的其他客户。 可以[按你所在位置来筛选报表以查找这些客户](consumer/mobile/mobile-apps-geographic-filtering.md)。

> [!NOTE]
> 如果报表中的地理名称采用的是英语&#150;例如，“New York City” 或 “Germany”，那么只可在移动应用中按位置筛选。
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>标识报表中的地理数据
1. 在 Power BI Desktop 中切换到数据视图 ![数据视图图标](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png)。
2. 选择含地理数据的列&#151;，例如“城市”列。
   
    ![“城市”列](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. 在“建模”  选项卡上，选择“数据类别”  ，那么本示例中的正确类别&#151;为“城市”  。
   
    ![数据类别框](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. 在模型中为其他任何字段继续设置地理数据类别。 
   
   > [!NOTE]
   > 可以为模型中的每个数据类别设置多个列，但如果这样做，模型就无法在 Power BI 移动应用中筛选地理。 若要在移动应用中使用地理筛选，则为每个数据类别&#151;仅设置一列，例如一个“城市”  列、一个“省/自治区”  列和一个“国家/地区”  列。 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>使用地理数据创建视觉对象
1. 切换到报表视图 ![报表视图图标，](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png)然后创建使用数据中的地理字段的视觉对象。 
   
    ![带有地图的报表](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    在此示例中，该模型还包含计算列，该列将城市和州放在同一列。 阅读[在 Power BI Desktop 中创建计算列](desktop-calculated-columns.md)。
   
    ![城市 + 状态字段](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. 将报表发布到 Power BI 服务。

## <a name="view-the-report-in-power-bi-mobile-app"></a>在 Power BI 移动应用中查看报表
1. 在任意 [Power BI 移动应用](consumer/mobile/mobile-apps-for-mobile-devices.md)中打开报表。
2. 如果你位于报表中数据相关的地理位置，则可以自动筛选到该位置。
   
    ![移动应用中的地区筛选器](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

详细了解如何[在 Power BI 移动应用中按地理位置筛选报表](consumer/mobile/mobile-apps-geographic-filtering.md)。

## <a name="next-steps"></a>后续步骤
* [Power BI Desktop 中的数据分类](desktop-data-categorization.md)  
* 是否有任何问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


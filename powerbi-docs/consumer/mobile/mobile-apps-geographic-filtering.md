---
title: 在 Power BI 移动应用中按地理位置筛选报表
description: 了解如何在报表所有者设置地理位置标记的情况下在 Microsoft Power BI 移动应用中按地理位置筛选报表。
author: mshenhav
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 02/09/2018
ms.author: mshenhav
ms.openlocfilehash: 828dcb4aeb8b7c5e69292685470f112a2d85cb71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61348619"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>在 Power BI 移动应用中按地理位置筛选报表
适用于：

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android 手机](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android 平板电脑](./media/mobile-apps-geographic-filtering/android-tablet-logo-50-px.png) | ![Android 平板电脑](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android 手机 |Android 平板电脑 |Windows 10 手机 |

在移动设备上查看 Power BI 报表时，是否注意到右上角有一个小图钉图标？ 如果看到了，那么可以根据你的地理位置筛选该报表。

> [!NOTE]
> 如果报表中的地理名称采用的是英语&#150;例如，“New York City”或“Germany”，那么只可按位置进行筛选。 Windows 10 平板电脑和 PC 不支持地理位置筛选，但 Windows 10 手机支持。
> 
> 

## <a name="filter-your-report-by-your-geographic-location"></a>按地理位置筛选报表
1. 在移动设备上，在 Power BI 移动应用中打开报表。
2. 如果报表具有地理数据，则会看到一条消息，要求允许 Power BI 访问你的位置。 单击“允许”  ，然后再次点击“允许”  。
3. 点击图钉 ![推送固定图标](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png)。 可以对市/县、省/自治区/直辖市或国家/地区进行筛选，具体取决于报表中的数据。 筛选器只列出与你当前的位置相匹配的选项。
   
    ![推送固定筛选器](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>我为什么在报表上看不到位置标记？
这三个条件必须全部为 true 才能看到位置标记。 

* 在 Power BI Desktop 中，报表创建者[对至少一列的地理位置数据进行分类](../../desktop-mobile-geofiltering.md)，例如“城市”、“州/省/自治区/直辖市”或“国家/地区”。
* 位于在相应列中有数据的位置之一。
* 使用的是下面一种移动设备：
  * iOS（iPad、iPhone、iPod）。
  * Android 手机或平板电脑。
  * Windows 10 手机（其他 Windows 10 设备（如 PC 和平板电脑）不支持地理位置筛选）。

阅读有关在 Power BI Desktop 中[设置地理筛选](../../desktop-mobile-geofiltering.md)的详细信息。

### <a name="next-steps"></a>后续步骤
* 使用移动应用[从真实世界连接到 Power BI 数据](mobile-apps-data-in-real-world-context.md)
* [Power BI Desktop 中的数据分类](../../desktop-data-categorization.md) 
* 是否有任何问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)


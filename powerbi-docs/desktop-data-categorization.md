---
title: Power BI Desktop 中的数据分类
description: Power BI Desktop 中的数据分类
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 4ce9946672514d3d3f181c573789b256888a4372
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "82584840"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>在 Power BI Desktop 中指定数据类别
在 Power BI Desktop 中，你可以为列指定数据类别，以便让 Power BI Desktop 知道如何在可视化效果中处理其值  。

Power BI Desktop 导入数据时，它将获取除数据本身以外的其他信息，如表名称和列名称，以及数据是否为主键。 有了这些信息，Power BI Desktop 会进行某些假设，让你在创建可视化效果时可拥有较好的默认体验。
例如，当列具有数值时，你可能想以某种方式对其进行聚合，因此 Power BI Desktop 将其置于“可视化效果”窗格的“值”区域中   。 或者，对于折线图上具有日期/时间值的列，Power BI Desktop 假设你可能会将其用作时间层次结构轴。

但是，有些情况比较具有挑战性，如地理位置。 请思考下列来自 Excel 工作表的表：

![](media/desktop-data-categorization/datacategorizationtable.png)

Power BI Desktop 应将 GeoCode 列中的代码视为国家/地区或美国州名的缩写吗  ？  由于此类代码可能表示这两种意思中的任何一个，因此并不清楚。 例如，AL 可以表示阿拉巴马或阿尔巴尼亚，AR 可以表示阿肯色或阿根廷，CA 可以表示加利福尼亚州或加拿大。 当我们在地图上绘制 GeoCode 字段时，需要加以区分。 

Power BI Desktop 是否应显示一张世界图片，并突出显示各个国家/地区？ 或者是否应显示一张美国的图片，并突出显示各个州？  你可以为此类型的数据指定数据类别。 数据分类进一步改进 Power BI Desktop 可用于提供最佳可视化效果的信息。  

**指定数据类别**

1. 在“报表”视图或“数据”视图中的字段列表中，选择你想要按不同的分类进行排序的字段    。
2. 在功能区上，在“建模”选项卡的“属性”区域中，选择“数据类别”旁边的下拉箭头    。  此列表显示了可以为列选择的数据类别。 如果某些选项不适用于列的当前数据类型，它们可能会被禁用。  例如，如果列为日期或时间数据类型，Power BI Desktop 将不允许你选择地理数据类别。 
3. 选择所需类别。

   ![](media/desktop-data-categorization/desktop-data-categorization.png)

你可能还有兴趣了解[ Power BI 移动应用的地理筛选](desktop-mobile-geofiltering.md)。


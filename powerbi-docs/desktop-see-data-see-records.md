---
title: 在 Power BI Desktop 中查看视觉对象的数据和记录
description: 使用 Power BI Desktop 的“查看数据”和“查看记录”功能深入了解详细信息
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 667b6eac288d3be35eac619b669498b6d7381dc3
ms.sourcegitcommit: 2aa83bd53faad6fb02eb059188ae623e26503b2a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73019248"
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>使用 Power BI Desktop 的“查看数据”和“查看记录”功能
在 Power BI Desktop  中，可以深入了解可视化效果的详细信息，并能查看选定视觉对象的基础数据或单个数据记录的文本表示形式。 这些功能有时亦称为“单击后了解详细信息”  、“深入了解”  或“深入了解详细信息”  。

可以使用“查看数据”  功能查看选定可视化效果使用的值文本，也可以使用“查看记录”  功能查看某个选定记录或数据点的所有数据。 

![“查看数据”和“查看记录”](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>“查看数据”  和“查看记录”  仅支持以下可视化效果类型：
>  - 条形图
>  - 柱形图
>  - 环形图
>  - 着色地图
>  - 漏斗图
>  - 地图
>  - 饼图
>  - 树状图

## <a name="use-see-data-in-power-bi-desktop"></a>使用 Power BI Desktop 中的“查看数据”功能

“查看数据”  显示基础可视化效果数据。 在选择可视化效果后，“查看数据”  出现在功能区的“可视化工具”  部分中的“数据/钻取”  选项卡内。

![功能区中的“查看数据”](media/desktop-see-data-see-records/see-data1.png)

此外，还可以通过右键单击可视化效果，然后从显示的菜单中选择“显示数据”；或者通过选择可视化效果右上角的“更多选项”(…)，然后选择“显示数据”来查看数据    。

![右键单击显示数据](media/desktop-see-data-see-records/see-data2.png)&nbsp;&nbsp;![更多选项显示数据](media/desktop-see-data-see-records/see-data3.png)

> [!NOTE]
> 必须将鼠标悬停在视觉对象中的数据点上方，才能在右键单击后看到菜单。

当选择“查看数据”  或“显示数据”  ，Power BI Desktop 画布将显示视觉对象和数据的文本表示形式。 在“水平视图”  中，视觉对象显示在画布的上半部分，数据显示在下半部分。 

![水平视图](media/desktop-see-data-see-records/see-data4a.png)

可以通过选择画布右上角的图标，在“水平视图”和“垂直视图”  之间切换。

![垂直视图切换](media/desktop-see-data-see-records/see-data4.png)

若要返回报表，请选择画布左上角的“< 返回报表”  。

![返回报表](media/desktop-see-data-see-records/see-data5.png)

## <a name="use-see-records-in-power-bi-desktop"></a>使用 Power BI Desktop 中的“查看记录”功能

还可以重点关注可视化效果中的一个数据记录，然后深入了解此记录的数据。 若要使用“查看记录”  ，选择可视化效果，然后选择功能区“可视化工具”  部分“数据/钻取”  选项卡中的“查看记录”  ，然后选择数据点或可视化效果上的行。 

![功能区中的“查看记录”](media/desktop-see-data-see-records/see-record1.png)

> [!NOTE]
> 如果功能区中的“查看记录”  按钮处于禁用状态并灰显，则意味着所选可视化效果不支持“查看记录”  。

此外可以右键单击数据元素，并从显示的菜单中选择“查看记录”  。

![通过右键单击查看记录](media/desktop-see-data-see-records/see-record2.png)

当选择某个数据元素的“查看记录”  ，Power BI Desktop 画布会显示与所选元素相关联的所有数据。 

![](media/desktop-see-data-see-records/see-record3.png)

若要返回报表，请选择画布左上角的“< 返回报表”  。

![](media/desktop-see-data-see-records/see-record4.png)

> [!NOTE]
>“查看记录”  具有以下限制：
> - 无法更改“查看记录”  视图中的数据并将其保存回报表。
> - 如果视觉对象使用计算度量值，不能使用“**查看记录**”。
> - 连接到实时多维 (MD) 模型时无法使用“查看记录”  。

## <a name="next-steps"></a>后续步骤
**Power BI Desktop** 提供各种报表格式和数据管理功能。 请参阅下列资源，其中列举了部分示例：

* [在 Power BI Desktop 中使用分组和装箱](desktop-grouping-and-binning.md)
* [在 Power BI Desktop 报表中使用网格线、与网格对齐、z 顺序、对齐和分布](desktop-gridlines-snap-to-grid.md)


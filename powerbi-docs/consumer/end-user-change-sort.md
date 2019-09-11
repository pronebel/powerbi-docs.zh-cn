---
title: 更改报表中的图表排序方式
description: 更改 Power BI 报表中的图表排序方式
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 98a91b0651e7a357f0ba0462f6ba8734c64ab162
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302718"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>更改 Power BI 报表中的图表排序方式
在 Power BI 报表中，可以按图表中类别名称的字母顺序，或者每个类别的数值对大多数可视化对象排序。 例如，下图按“商店名称”类别排序。 

![按 X 轴的字母顺序排序的条形图](media/end-user-change-sort/pbi_chartsortcategory.png)

可以轻松地将排序依据从类别（商店名称）更改为值（每平方英尺销售额）。

1. 依次选择省略号 (…) 和“排序依据”>“每平方英尺销售额”  。
2. 如有必要，重新依次选择省略号和“降序排序”  。

   ![显示选择排序依据，然后选择升序、降序的视频](media/end-user-change-sort/sort.gif)

> [!NOTE]
> 并非所有视觉对象都可以进行排序。 例如，以下视觉对象无法排序：树状图、地图、着色地图、散点图、仪表图、卡片图、瀑布图。

## <a name="saving-changes-you-make-to-sort-order"></a>保存对排序顺序的更改
Power BI 报表可保留你对筛选器、切片器、排序和其他数据视图的更改。 因此，如果离开报表并在稍后返回，会保存你的更改。  如果想要将更改还原为报表设计者的设置，请选择上方菜单栏中的“重置为默认值”  。 

![持久性排序](media/end-user-change-sort/power-bi-reset.png)

但是，如果“重置为默认值”按钮灰显，则表示设计者已禁用保存（保留）更改的功能  。

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>使用其他条件排序
有时候，你想使用不同的字段或其他条件对视觉对象排序。  例如，你可能想按月份（而不是字母顺序）排序，或者按整个数值而不是数字排序（例如 0、1、9、20，而不是 0、1、20、9）。  

在某些情况下，你可以按照你想要的方式对视觉对象进行排序，例如按月。  但如果不是，可能是因为报表背后的数据集需要一些调整。 要求报表设计者更新数据集。

## <a name="next-steps"></a>后续步骤
[Power BI 报表中的可视化对象](end-user-visualizations.md)的详细信息。

[Power BI - 基本概念](end-user-basic-concepts.md)

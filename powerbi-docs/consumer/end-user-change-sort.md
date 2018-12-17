---
title: 更改 Power BI 报表中的图表排序方式
description: 更改 Power BI 报表中的图表排序方式
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: Conceptual
ms.date: 09/20/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: f4ca6633eb401e7df8041ea385284210c14995ad
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2018
ms.locfileid: "52979321"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>更改 Power BI 报表中的图表排序方式
在 Power BI 报表中，可以按图表中类别名称的字母顺序，或者每个类别的数值对大多数可视化对象排序。 例如，下图按“商店名称”类别排序。

![](media/end-user-change-sort/pbi_chartsortcategory.png)

可以轻松地将排序依据从类别（商店名称）更改为值（每平方英尺销售额）。

1. 选择省略号 (…)，然后选择“排序依据”>“每平方英尺销售额”。
2. 如有必要，再次选择省略号，然后选择“降序排序”。

   ![](media/end-user-change-sort/sort.gif)

   **注意**：并非所有视觉对象都可以进行排序。  例如，以下视觉对象不能进行排序：树状图、地图、着色地图、散点图、仪表、卡、多行卡、瀑布图。

## <a name="saving-changes-you-make-to-sort-order"></a>保存对排序顺序的更改
Power BI 报表可保留你对筛选器、切片器、排序和其他数据视图的更改。 因此，如果离开报表并在稍后返回，会保存你的更改。  如果想要将更改还原为报表创建者的设置，请选择顶部菜单栏中的“重置为默认值”。 

![持久性排序](media/end-user-change-sort/power-bi-reset-to-default.png)

但是，如果“重置为默认值”按钮灰显，则表示创建者已禁用保存（保留）更改的功能。

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>使用其他条件排序
有时候，你想使用不同的字段或其他条件对视觉对象排序。  例如，你可能想按月份（而不是字母顺序）排序，或者按整个数值而不是数字排序（例如 0、1、9、20，而不是 0、1、20、9）。  

在某些情况下，你可以按照你想要的方式对视觉对象进行排序，例如按月。  但如果不是，可能是因为报表背后的数据集需要一些调整。 要求报表创建者更新数据集。

## <a name="next-steps"></a>后续步骤
[Power BI 报表中的可视化对象](end-user-visualizations.md)的详细信息。

[Power BI - 基本概念](end-user-basic-concepts.md)
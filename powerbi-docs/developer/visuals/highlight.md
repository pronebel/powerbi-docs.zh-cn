---
title: 突出显示
description: 在 Power BI 视觉对象中突出显示数据点选择
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424806"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>突出显示 Power BI 视觉对象中的数据点

默认情况下，只要选择了某个元素，`dataView` 对象中的 `values` 数组就会被筛选为所选的值。 这将导致页面上的所有其他视觉对象仅显示所选数据。

![突出显示 `dataview` 默认行为](./media/highlight-dataview.png)

如果将 `capabilities.json` 中的 `supportsHighlight` 属性设置为 `true`，则会获得未经筛选的完整 `values` 数组和 `highlights` 数组。 `highlights` 数组的长度与 values 数组的长度相同，并且任何未选定的值都将设置为 `null`。 启用此属性后，视觉对象负责通过将 `values` 数组与 `highlights` 数组进行比较来突出显示相应的数据。

![突出显示 `dataview` supportshighlight](./media/highlight-dataview-supports.png)

在此示例中，你会注意到 1 栏处于选定状态。 它是突出显示数组中唯一的值。 另外，请务必注意，可能存在多个选择和部分突出显示。 值中有相应的数值，并且将存在突出显示数组，但会存在差异。

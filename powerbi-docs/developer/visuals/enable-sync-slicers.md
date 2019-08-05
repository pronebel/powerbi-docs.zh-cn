---
title: 启用同步切片器
description: 如何为 Power BI 视觉对象添加同步切片器功能
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425013"
---
# <a name="sync-slicers"></a>同步切片器

若要支持[同步切片器](https://docs.microsoft.com/power-bi/desktop-slicers)，自定义切片器视觉对象须使用 API 1.13 或更高版本。

第二个必要方面是 `capabilities.json` 中已启用的选项（请参阅下面的示例）。

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

在 `capabilities.json` 中进行更改后，单击自定义切片器视觉对象时会显示“同步切片器”选项面板。

> [!NOTE]
> 如果切片器中的字段超过 1 个字段（类别或度量值），将禁用该功能，因为“同步切片器”不支持多个字段。

![同步切片器面板](./media/sync-slicers-panel.png)

在面板中，可看到，切片器可见性及其筛选设置可能会应用于多个报表页。

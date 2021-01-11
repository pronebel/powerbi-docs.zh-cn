---
title: 在 Power BI 嵌入式分析的 Power BI 视觉对象中启用“同步切片器”功能以增强嵌入式 BI 见解
description: 本文介绍如何将同步切片器功能添加到 Power BI 视觉对象中。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: bd69e05bba3e9449f9fb6f07bd9625dfb1ea0c08
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885260"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Power BI 视觉对象中的同步切片器

要支持[同步切片器](../../visuals/power-bi-visualization-slicers.md)功能，自定义切片器视觉对象必须使用 API 版本 1.13.0 或更高版本。

此外，需在 capabilities.json 文件中启用该选项，如下所示：

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

更新 capabilities.json 文件后，可以在选择自定义切片器视觉对象时查看“同步切片器”选项窗格。

> [!NOTE]
> 同步切片器功能不支持多个字段。 如果切片器有多个字段（“类别”或“度量值”），则会禁用该功能 。

![“同步切片器”窗格](media/enable-sync-slicers/sync-slicers-panel.png)

在“同步切片器”窗格中，可以看到切片器可见性以及切片器筛选可能会应用于多个报表页。
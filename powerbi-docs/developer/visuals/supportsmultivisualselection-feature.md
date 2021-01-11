---
title: Power BI 嵌入式分析中用于增强嵌入式 BI 见解的 supportsMultiVisualSelection 功能
description: 本文介绍如何在 Power BI 视觉对象中使用 supportsMultiVisualSelection 功能及其要求。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 9e6b17a4576f2354a5cbecc0c3a965a5611784ee
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887928"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>使用 supportsMultiVisualSelection 功能

借助 `supportsMultiVisualSelection` 功能，可以在报表的多个视觉对象中使用所选内容。

## <a name="example"></a>示例

在具有多个视觉对象的报表中，选择两个值以使这些值应用于其他视觉对象。 例如，在[零售分析示例](../../create-reports/sample-retail-analysis.md)中，选择一个视觉对象中的“Fashions Direct”。 选择 ctrl，然后选择另一个视觉对象中的“一月”。 在报表中，你的选择应用于支持使用此功能的其他视觉对象。 其他视觉对象现在限定为“Fashions Direct”和“一月” 。

## <a name="requirements"></a>要求

此功能需要 API v3.2.0 或更高版本。

不能将此功能应用于图像视觉对象。 不能将其应用于某些高级视觉对象，例如关键驱动程序、分解树、问答视觉对象、文本框和仪表盘。

## <a name="usage"></a>使用情况

若要使用 `supportsMultiVisualSelection` 功能，请将以下代码添加到视觉对象的 `capabilities.json` 文件中。

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>后续步骤

若要了解 Power BI 概念，请参阅 [Power BI 中的视觉对象](power-bi-visuals-concept.md)。

若要试用 Power BI 开发，请参阅[开发 Power BI 圆形卡片](develop-circle-card.md)。

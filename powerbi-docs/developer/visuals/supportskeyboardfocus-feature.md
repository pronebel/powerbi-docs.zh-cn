---
title: Power BI 嵌入式分析中用于增强嵌入式 BI 见解的 supportsKeyboardFocus 功能
description: 本文介绍如何在 Power BI 视觉对象中使用 supportsKeyboardFocus 功能及其要求。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 5ba87db8118076de4bf13abc0280223f9f04f871
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887951"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>使用 supportsKeyboardFocus 功能

本文介绍了如何在 Power BI 视觉对象中使用 `supportsKeyboardFocus` 功能。
`supportsKeyboardFocus` 功能仅允许使用键盘浏览视觉对象的数据点。

若要了解有关视觉对象的键盘导航的详细信息，请参阅[键盘导航](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation)。

## <a name="example"></a>示例

打开使用 `supportsKeyboardFocus` 功能的视觉对象。 选择视觉对象中的任意数据点，然后选择 Tab 键。每次选择 Tab 键时，焦点将移到下一个数据点。选择 Enter 以选择突出显示的数据点。

![支持键盘焦点示例](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>要求

此功能需要 API v2.1.0 或更高版本。

此功能可以应用于除图像视觉对象之外的所有视觉对象。

## <a name="usage"></a>使用情况

若要使用 `supportsKeyboardFocus` 功能，请将以下代码添加到视觉对象的 *capabilities.json* 文件中。
此功能允许视觉对象通过键盘导航获得焦点。

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>后续步骤

若要了解有关辅助功能的详细信息，请参阅[为辅助功能设计 Power BI 报表](../../create-reports/desktop-accessibility-creating-reports.md)。

若要试用 Power BI 开发，请参阅[开发 Power BI 圆形卡片视觉对象](develop-circle-card.md)。

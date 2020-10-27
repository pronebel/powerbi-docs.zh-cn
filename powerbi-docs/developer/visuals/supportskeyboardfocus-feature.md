---
title: supportsKeyboardFocus 功能
description: 本文介绍如何在 Power BI 视觉对象中使用 supportsKeyboardFocus 功能及其要求。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 1e5a4cf8c80d8123d39fd2ab76898abc0c439ad9
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049375"
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

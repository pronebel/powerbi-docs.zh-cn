---
title: Power BI 嵌入式分析的 Power BI 视觉对象中用于增强嵌入式 BI 见解的高级编辑模式
description: 本文介绍如何在 Power BI 视觉对象中设置高级 UI 控件。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 02f02f23d3dfd7ec514e17d1bab17be715e9cd7d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889124"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Power BI 视觉对象中的高级编辑模式

如果在 Power BI 视觉对象中需要高级 UI 控件，可以使用高级编辑模式。 处于报表编辑模式时，请选择“编辑”按钮以将编辑模式设置为“高级”。 视觉对象可以使用 `EditMode` 标志来决定是否应显示此 UI 控件。

默认情况下，视觉对象不支持高级编辑模式。 如需其他行为，则可以通过设置 `advancedEditModeSupport` 属性，在视觉对象的 capabilities.json 文件中明确声明。

可能的值为：

- `0` - NotSupported

- `1` - SupportedNoAction

- `2` - SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>进入高级编辑模式

如果出现以下情况，则会显示“编辑”按钮：

* 在 capabilities.json 文件中将 `advancedEditModeSupport` 属性设置为 `SupportedNoAction` 或 `SupportedInFocus`。

* 在报表编辑模式下查看视觉对象。

如果 capabilities.json 文件中缺少属性 `advancedEditModeSupport` 或将其设置为 `NotSupported`，则不会显示“编辑”按钮。

![进入编辑模式](media/advanced-edit-mode/edit-mode.png)

选择“编辑”时，视觉对象将获取 update() 调用，并将 EditMode 设置为 `Advanced`。 根据 capabilities.json 文件中设置的值，将发生以下操作：

* `SupportedNoAction`：主机无需执行任何进一步操作。
* `SupportedInFocus`：主机以焦点模式弹出视觉对象。

## <a name="exit-advanced-edit-mode"></a>退出高级编辑模式

如果出现以下情况，则会显示“返回报表”按钮：

* 在 capabilities.json 文件中将 `advancedEditModeSupport` 属性设置为 `SupportedInFocus`。

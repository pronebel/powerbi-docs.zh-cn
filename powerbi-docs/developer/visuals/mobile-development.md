---
title: Power BI 嵌入式分析中用于增强嵌入式 BI 见解的移动开发
description: 如何创建适合移动的 Power BI 视觉对象。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 63d2366f91398878af231c8dbb6ed07e8e623a03
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885536"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>如何创建适合移动的 Power BI 视觉对象
移动使用在 Power BI 中具有重要角色。 它的一个优点在于可随时随地与数据保持连接。

作为创建 Power BI 视觉对象的开发人员，必须解决每个移动设备的独有约束，以尽可能多地吸引用户，并提供最佳移动体验。

使用[适用于 Windows、iOS 和 Android 的 Power BI 应用](../../consumer/mobile/mobile-apps-for-mobile-devices.md)可使业务用户只需轻触指尖，便可在移动中获得其数据的全面视图。

## <a name="requirements"></a>要求

以下要求对于适合移动的视觉对象开发非常重要：

- 呈现

  Power BI 视觉对象必须在所有受支持的移动设备（包括受支持的浏览器和应用程序）上呈现，并且在报表、仪表板中以及在“焦点”  模式下运行时没有错误。 

- 交互

  交互功能的提供方式必须与为桌面设备提供该功能的方式相同。 在桌面浏览器上处理的所有事件都必须受支持，或是有类似的事件处理程序用于移动设备。
  
  例如，基本导航和数据点选择应具有与桌面浏览器相同的功能。 如果视觉对象支持使用 Ctrl  进行多选，则开发人员需要考虑为移动设备添加类似的事件处理程序。

  下表提供了移动设备上的对应事件的列表。

  | 鼠标事件名称 | 触摸事件名称 |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | 使用外部库 |
  | `contextmenu` | 使用外部库 |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove`（或外部库） |
  | `wheel` | `NaN` |

  > [!NOTE]
  > 并非所有移动或触摸屏设备都支持鼠标（或具有 mouse  前缀的）事件。 在这种情况下，会同时处理鼠标  和触摸  事件。

## <a name="optional"></a>可选
以下被视为可选功能，用于创建更好的最终用户体验。

- 呈现

  若要支持较小的视觉对象大小，请尝试添加用户可以为调整每个元素大小而更改的格式选项。 例如，将格式选项添加到标签，以便在报表和仪表板中使用。 这使用户可以专门为其移动设备自定义视觉对象。
  
  相同设置也可以应用于桌面浏览器中的视觉对象，如果需要，可以进行替代以使视觉对象适应更小的屏幕。

  > [!NOTE]
  > 若要在“焦点”  模式下优化视觉对象，需要考虑纵向和横向屏幕大小方向，请参阅[在焦点模式下显示内容](../../consumer/end-user-focus.md)。

- 交互

  考虑添加特定于移动设备的事件处理程序，如拖动和滚动。

- 故障转移

  如果视觉对象无法在移动设备上呈现，则它应显示描述性错误。

## <a name="supported-browsers-and-devices"></a>支持的浏览器和设备
Power BI 视觉对象必须在支持 Power BI 应用的所有设备上呈现，有关详细信息，请参阅 [Power BI 支持的浏览器 ](../../fundamentals/power-bi-browsers.md)和 [Power BI 移动应用](../../consumer/mobile/mobile-apps-for-mobile-devices.md)。

针对最新型号的 Windows、iOS 和 Android 设备进行测试时，开发人员需要考虑其中大多数质量方面。

## <a name="next-steps"></a>后续步骤
若要开始，请参阅[开发 Power BI 圆形卡片视觉对象](./develop-circle-card.md)。
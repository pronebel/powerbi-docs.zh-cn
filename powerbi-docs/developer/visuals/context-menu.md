---
title: Power BI 视觉对象的功能和属性
description: 本文介绍 Power BI 视觉对象的功能和属性。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380746"
---
# <a name="add-context-menu-to-power-bi-visual"></a>将上下文菜单添加到 Power BI 视觉对象

可以将 `selectionManager.showContextMenu()` 与参数 `selectionId` 和位置（作为 `{x:, y:}` 对象）一起使用，以使 Power BI 为视觉对象显示上下文菜单。

> [!IMPORTANT]
> 视觉对象 API 2.2.0 中引入了 `selectionManager.showContextMenu()`。

通常会将其作为右键单击事件（对于触摸设备则为长按事件）上下文菜单添加到示例条形图以供参考：

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```

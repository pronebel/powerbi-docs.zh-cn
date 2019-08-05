---
title: 呈现事件
description: Power BI 视觉对象可以通知 Power BI，它们已可导出到 Power Point/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425082"
---
# <a name="event-service"></a>事件服务

新 API 包含三种方法（started、finished 或 failed），这些方法应在呈现过程中调用。

呈现开始时，自定义视觉对象代码调用 renderingStarted 方法以指示呈现进程已开始。

如果呈现已成功完成，自定义视觉对象代码将立即调用 `renderingFinished` 方法，通知侦听器（主要是“导出到 PDF”和“导出到 PowerPoint”）视觉对象的映像已准备就绪  。

如果呈现过程中出现问题，自定义视觉对象无法成功完成。 自定义视觉对象代码应调用 `renderingFailed` 方法，通知侦听器呈现过程尚未完成。 此方法还为失败原因提供可选字符串。

## <a name="usage"></a>使用情况

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>简单示例。 视觉对象没有呈现任何动画

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-with-animation"></a>示例。 带有动画的视觉对象

如果视觉对象带有用于呈现的动画或异步函数，则应在动画后或异步函数内调用 `renderingFinished` 方法。

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>视觉对象认证的呈现事件

视觉对象对呈现事件的支持是视觉对象认证的要求之一。 阅读有关[认证要求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)的详细内容

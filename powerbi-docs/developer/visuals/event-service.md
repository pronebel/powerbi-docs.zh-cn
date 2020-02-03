---
title: 在 Power BI 视觉对象中呈现事件
description: Power BI 视觉对象可以通知 Power BI，它们已可导出到 PowerPoint 或 PDF。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 873968a89a230171d8fecba81a7d528767ee7077
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819137"
---
# <a name="render-events-in-power-bi-visuals"></a>在 Power BI 视觉对象中呈现事件

新 API 包含三种方法（`started`、`finished` 或 `failed`），这些方法应在呈现过程中调用。

呈现开始时，Power BI 视觉对象代码调用 `renderingStarted` 方法以指示呈现进程已开始。

如果呈现已成功完成， Power BI 视觉对象代码将立即调用 `renderingFinished` 方法，通知侦听器（主要是“导出到 PDF”和“导出到 PowerPoint”）视觉对象的映像已准备好进行导出。

如果在此过程中出现问题，Power BI 视觉对象则无法成功呈现。 要通知侦听器呈现过程尚未完成，Power BI 视觉对象代码应调用 `renderingFailed` 方法。 此方法还提供可选字符串用于说明失败原因。

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
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>示例：视觉对象不显示动画

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

### <a name="sample-the-visual-displays-animations"></a>示例：视觉对象显示动画

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
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>视觉对象认证的呈现事件

视觉对象认证的要求之一是支持视觉对象呈现事件。 有关详细信息，请参阅[认证要求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)。

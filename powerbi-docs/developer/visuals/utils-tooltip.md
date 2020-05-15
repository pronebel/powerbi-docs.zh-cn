---
title: 关于在 Power BI 视觉对象中使用工具提示 Utils 的简介
description: 本文介绍了如何使用工具提示 Utils 简化 Power BI 视觉对象的工具提示自定义
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 67470ec405806f44fdb483e857d222ad4ff05a45
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379159"
---
# <a name="tooltip-utils"></a>工具提示 Utils
本文介绍了如何安装、导入和使用工具提示 Utils。 此 Utils 适用于 Power BI 视觉对象中的任何工具提示自定义。

## <a name="requirements"></a>要求
若要使用此包，应具备以下组件：
* [node.js](https://nodejs.org)（建议使用最新 LTS 版本）
* [npm](https://www.npmjs.com/)（支持的最低版本为 3.0.0）
* 通过 [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) 创建的自定义视觉对象

## <a name="installation"></a>安装

要安装包，应在目录中运行以下命令和当前的视觉对象：

```bash
npm install powerbi-visuals-utils-colorutils --save
```
上面的命令安装此包，并将它作为依赖项添加到 ```package.json```

## <a name="usage"></a>使用情况

> “使用指南”介绍了此包的公共 API。 其中包括此包的每个公共接口的说明和一些示例。

使用此包，可以创建有助于处理工具提示操作的 `TooltipServiceWrapper` 和方法。 它使用工具提示接口 `ITooltipServiceWrapper`、`TooltipEventArgs`、`TooltipEnabledDataPoint`。 

此外，它还包含与移动开发相关的特定方法（触控事件处理程序）`touchEndEventName`、`touchStartEventName`、`usePointerEvents`。

`TooltipServiceWrapper` 提供了控制工具提示的最简单方法。

此模块提供了以下接口和函数：
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [接口](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Touch events](#touch-events)

### `createTooltipServiceWrapper`
此函数创建 ITooltipServiceWrapper 实例。

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

[IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335) 提供 ```ITooltipService```。

 示例

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

可在[此处](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391)查看自定义视觉对象的示例代码。

### `ITooltipServiceWrapper`
此接口描述 TooltipService 的公共方法。

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

此方法将工具提示添加到当前选定对象。

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

 示例

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

可在[此处](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931)查看自定义视觉对象的示例代码。

还请注意以下示例：甘特图自定义视觉对象中的工具提示自定义（[单击此处](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)）

### `ITooltipServiceWrapper.hide`

此方法隐藏工具提示。

```typescript
hide(): void;
```

 示例

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
此接口在 TooltipServiceWrapper 创建和使用期间中使用。 另外，前面主题（[单击此处](#itooltipservicewrapperaddtooltip)）中的示例也提及了它们。

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

现在，工具提示 Utils 可以处理多个触控事件，非常适用于移动开发。

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
此方法返回触控开始事件名称。

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
此方法返回触控开始事件名称。

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
此方法返回当前 touchStart 事件是否与指针关联。

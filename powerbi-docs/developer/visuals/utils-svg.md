---
title: 关于在 Power BI 视觉对象中使用 SVG utils 的简介
description: 本文介绍如何使用 SVG utils 简化 Power BI 视觉对象的 SVG 操作
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: aa1ac8074e842a51b369c48f57c4b5016a80140c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377963"
---
# <a name="svg-utils"></a>SVG utils

SVG utils 是一组函数和类，用于简化 Power BI 视觉对象的 SVG 操作

## <a name="installation"></a>安装

要安装包，应在目录中运行以下命令和当前的视觉对象：

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

`CssConstants` 模块提供了用于处理类选择器的特殊函数和接口。

`powerbi.extensibility.utils.svg.CssConstants` 模块提供了以下函数和接口：

## <a name="classandselector"></a>ClassAndSelector

此接口描述类选择器的公共属性。

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

此函数使用类的给定名称创建 ClassAndSelector 的实例。

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

示例:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

`manipulation` 提供了一些特殊函数来生成字符串，以便与 SVG 转换属性结合使用。

该模块提供了以下函数：

### <a name="translate"></a>translate

此函数创建 translate 字符串，以便与 SVG 转换属性结合使用。

```typescript
function translate(x: number, y: number): string;
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

此函数创建 translateX 字符串，以便与 SVG 转换属性结合使用。

```typescript
function translateXWithPixels(x: number): string;
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

此函数创建 translate 字符串，以便与 SVG 转换属性结合使用。

```typescript
function translateWithPixels(x: number, y: number): string;
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

此函数创建 translate-rotate 字符串，以便与 SVG 转换属性结合使用。

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

此函数创建 scale 字符串，以便在 CSS 转换属性中使用。

```typescript
function scale(scale: number): string;
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

此函数创建 transform-origin 字符串，以便在 CSS transform-origin 属性中使用。

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

此函数强制完成 D3 的每个转换。

```typescript
function flushAllD3Transitions(): void;
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

此函数用值“translate(x,y)”解析 transform 字符串。

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

此函数创建一个箭头。

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

示例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

`Rect` 模块提供了一些用于操作矩形的特殊函数。

该模块提供了以下函数：

### <a name="getoffset"></a>getOffset

此函数返回矩形的偏移量。

```typescript
function getOffset(rect: IRect): IPoint;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

此函数返回矩形的大小。

```typescript
function getSize(rect: IRect): ISize;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

此函数修改矩形的大小。

```typescript
function setSize(rect: IRect, value: ISize): void;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

此函数返回矩形的右侧位置。

```typescript
function right(rect: IRect): number;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

此函数返回矩形的底部位置。

```typescript
function bottom(rect: IRect): number;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

此函数返回矩形的左上位置。

```typescript
function topLeft(rect: IRect): IPoint;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

此函数返回矩形的右上位置。

```typescript
function topRight(rect: IRect): IPoint;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

此函数返回矩形的左下位置。

```typescript
function bottomLeft(rect: IRect): IPoint;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

此函数返回矩形的右下位置。

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>示例

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>克隆

此函数创建矩形的副本。

```typescript
function clone(rect: IRect): IRect;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

此函数将矩形转换为字符串。

```typescript
function toString(rect: IRect): string;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

此函数对矩形应用给定的偏移量。

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

此函数将第一个矩形添加到第二个矩形。

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

此函数将矩形上最近的点返回到给定的点。

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

此函数对矩形进行比较，如果它们相同则返回 true。

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

此函数通过考虑值的精度来比较矩形。

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

此函数检查矩形是否为空。

```typescript
function isEmpty(rect: IRect): boolean;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

此函数检查矩形是否包含点。

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

此函数检查矩形是否相交。

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

此函数返回矩形的交点。

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

此函数合并矩形。

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

此函数返回矩形的中心点。

```typescript
function getCentroid(rect: IRect): IPoint;
```

示例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>指针 (pointer)

`pointer` 模块提供了用于获取指针位置的特殊函数。

该模块提供了以下函数：

### <a name="getcoordinates"></a>getCoordinates

此函数返回指针的位置。

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

示例:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```

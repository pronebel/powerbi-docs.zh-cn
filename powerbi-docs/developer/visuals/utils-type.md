---
title: 关于在 Power BI 嵌入式分析的 Power BI 视觉对象中使用类型使用工具以增强嵌入式 BI 见解的介绍
description: 本文介绍如何使用 SVG utils 扩展 Power BI 视觉对象的基本类型。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4f81f55f8d5cfc54020b3b4e02e8be55fb65b0d1
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888112"
---
# <a name="type-utils"></a>类型 utils

TypeUtils 是一组函数和类，用于扩展 Power BI 视觉对象的基本类型。

## <a name="installation"></a>安装

若要安装包，应在目录中运行以下命令和当前的自定义视觉对象：

npm install powerbi-visuals-utils-typeutils --save 此命令用于安装包并将包作为依赖项添加到 package.json

## <a name="double"></a>Double

`Double` 提供操纵数值精度的能力。

该模块提供了以下函数：

### <a name="pow10"></a>pow10

此函数返回 10 的幂。

```typescript
function pow10(exp: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

此函数返回数字以 10 为底的对数。

```typescript
function log10(val: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

此函数返回 10 的幂，表示数值的精度。

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

此函数检查两个数字之间的增量是否小于提供的精度。

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

此函数检查第一个值是否小于第二个值。

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

此函数检查第一个值是否小于或等于第二个值。

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

此函数检查第一个值是否大于第二个值。

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

此函数检查第一个值是否大于或等于第二个值。

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

此函数以提供的精度对数字进行向下取值。

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

此函数以提供的精度对数字进行 `ceils`。

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

此函数将数字向下取值至提供的精度。

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

此函数将数字 `ceils` 至提供的精度。

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

此函数将数字舍入至提供的精度。

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

此函数返回介于最小值和最大值之间的数字。

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

此函数对数字进行舍入。

```typescript
function round(x: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

此函数删除小数点干扰。

```typescript
function removeDecimalNoise(value: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

此函数检查数字是否为整数。

```typescript
function isInteger(value: number): boolean;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

此函数按所提供的数字递增数字，并返回舍入的数字。

```typescript
function toIncrement(value: number, increment: number): number;
```

示例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>原型

`Prototype` 提供了继承对象的能力。

该模块提供了以下函数：

## <a name="inherit"></a>inherit

此函数返回一个以提供的对象作为其原型的新对象。

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

示例：

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

当且仅当未设置原型时，此函数返回以提供的对象作为其原型的新对象。

```typescript
function inheritSingle<T>(obj: T): T;
```

示例：

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` 提供将像素转换为点以及将点转换为像素的功能。

该模块提供了以下函数：

## <a name="tostring"></a>toString

此函数将像素值转换为字符串。

```typescript
function toString(px: number): string;
```

示例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

此函数将提供的点值转换为像素值并返回字符串解释。

```typescript
function fromPoint(pt: number): string;
```

示例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

此函数将提供的点值转换为像素值。

```typescript
function fromPointToPixel(pt: number): number;
```

示例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

此函数将像素值转换为点值。

```typescript
function toPoint(px: number): number;
```

示例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```

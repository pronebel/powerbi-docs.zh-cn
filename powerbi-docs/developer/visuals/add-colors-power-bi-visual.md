---
title: 向 Power BI 视觉对象添加颜色以增强嵌入式 BI 见解
description: 本文介绍如何为 Power BI 视觉对象添加颜色以及如何通过颜色处理视觉对象的数据点。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: e6b6fb1dbc1397b93ac12692c8610e6f36d0b8bf
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887974"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>为 Power BI 视觉对象添加颜色

本文介绍如何为视觉对象添加颜色以及如何处理颜色视觉对象的数据点。

`IVisualHost` 将颜色公开为其服务之一。
本文中的示例代码修改了 [SampleBarChart 视觉对象](https://github.com/microsoft/PowerBI-visuals-sampleBarChart)。
有关源代码，请参阅 [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts)。

若要开始创建视觉对象，请参阅[开发 Power BI 圆形卡片视觉对象](develop-circle-card.md)。

## <a name="add-color-to-data-points"></a>为数据点添加颜色

每一种颜色表示一个数据点。
将该颜色添加到 `BarChartDataPoint` 接口，如以下示例中所示：

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>使用调色板服务

`colorPalette` 服务管理视觉对象中使用的颜色。
该服务的实例在 `IVisualHost` 上可用。

在 `update` 方法中进行定义。

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>为数据点分配颜色

接下来，指定 `dataPoints`。
在此示例中，每个 `dataPoints` 都包含值、类别和颜色。
`dataPoints` 还可以包含其他属性。

在 `SampleBarChart` 中，`visualTransform` 方法封装 `dataPoints` 计算。
该方法是条形图 viewmodel 的一部分。
由于方法会循环访问 `visualTransform` 中的 `dataPoints` 计算，因此它是分配颜色的理想位置，如以下代码中所示：

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

然后，将 `dataPoints` 上的数据应用于 `update` 方法中的 [d3](https://d3js.org/) 选择 `barSelection`：

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>后续步骤

要了解有关 Power BI 视觉对象的详细信息，请参阅 [Power BI 视觉对象的功能和属性](capabilities.md)。

要了解有关开发 Power BI 视觉对象的详细信息，请参阅[如何调试 Power BI 视觉对象](visuals-how-to-debug.md)和 [Power BI 视觉对象疑难解答](power-bi-custom-visuals-troubleshoot.md)。

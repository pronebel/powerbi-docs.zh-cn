---
title: 关于在 Power BI 嵌入式分析的 Power BI 视觉对象中使用图表 utils 以增强嵌入式 BI 见解的介绍
description: 本文介绍如何使用图表 utils 绘制轴和图例 Power BI 视觉对象。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 9094d639225eb82cbcf427346d1ad78943ddc90f
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887859"
---
# <a name="chart-utils"></a>图表 utils

ChartUtils 是用于在 Power BI 视觉对象中创建轴、数据标签和图例的一组接口和方法。

## <a name="installation"></a>安装

要安装包，应在包含当前视觉对象的目录中运行以下命令：

```bash
npm install powerbi-visuals-utils-chartutils --save
```

## <a name="axis-helper"></a>轴帮助程序

轴帮助程序（utils 中的 `axis` 对象）提供用于简化轴操作的函数。

该模块提供了以下函数：

### <a name="getrecommendednumberofticksforxaxis"></a>getRecommendedNumberOfTicksForXAxis

此函数根据图表的宽度返回建议的时钟周期数。

```typescript
function getRecommendedNumberOfTicksForXAxis(availableWidth: number): number;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForXAxis(1024);

// returns: 8
```

### <a name="getrecommendednumberofticksforyaxis"></a>getRecommendedNumberOfTicksForYAxis

此函数根据图表的高度返回建议的时钟周期数。

```typescript
function getRecommendedNumberOfTicksForYAxis(availableWidth: number);
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForYAxis(100);

// returns: 3
```

### <a name="getbestnumberofticks"></a>getBestNumberOfTicks

根据最小值、最大值、度量值元数据和最大滴答计数获取最佳时钟周期数；

```typescript
function getBestNumberOfTicks(
  min: number,
  max: number,
  valuesMetadata: DataViewMetadataColumn[],
  maxTickCount: number,
  isDateTime?: boolean
): number;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
var dataViewMetadataColumnWithIntegersOnly: powerbi.DataViewMetadataColumn[] = [
  {
    displayName: "col1",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  },
  {
    displayName: "col2",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  }
];
var actual = axis.getBestNumberOfTicks(
  0,
  3,
  dataViewMetadataColumnWithIntegersOnly,
  6
);

// returns: 4
```

### <a name="getticklabelmargins"></a>getTickLabelMargins

此函数返回时钟周期标签的边距。

```typescript
function getTickLabelMargins(
  viewport: IViewport,
  yMarginLimit: number,
  textWidthMeasurer: ITextAsSVGMeasurer,
  textHeightMeasurer: ITextAsSVGMeasurer,
  axes: CartesianAxisProperties,
  bottomMarginLimit: number,
  properties: TextProperties,
  scrollbarVisible?: boolean,
  showOnRight?: boolean,
  renderXAxis?: boolean,
  renderY1Axis?: boolean,
  renderY2Axis?: boolean
): TickLabelMargins;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.getTickLabelMargins(
  plotArea,
  marginLimits.left,
  TextMeasurementService.measureSvgTextWidth,
  TextMeasurementService.estimateSvgTextHeight,
  axes,
  marginLimits.bottom,
  textProperties,
  /*scrolling*/ false,
  showY1OnRight,
  renderXAxis,
  renderY1Axis,
  renderY2Axis
);

// returns:  xMax, yLeft, yRight, stackHeigh;
```

### <a name="isordinal"></a>isOrdinal

检查字符串是否为 null、未定义或为空。

```typescript
function isOrdinal(type: ValueTypeDescriptor): boolean;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
let type = ValueType.fromDescriptor({ misc: { barcode: true } });
axis.isOrdinal(type);

// returns: true
```

### <a name="isdatetime"></a>isDateTime

检查值是否为日期/时间类型。

```typescript
function isDateTime(type: ValueTypeDescriptor): boolean;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.isDateTime(ValueType.fromDescriptor({ dateTime: true }));

// returns: true
```

### <a name="getcategorythickness"></a>getCategoryThickness

使用 D3 刻度获取实际的类别粗细。

```typescript
function getCategoryThickness(scale: any): number;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let range = [0, 100];
let domain = [0, 10];
let scale = d3.scale
  .linear()
  .domain(domain)
  .range(range);
let actualThickness = axis.getCategoryThickness(scale);
```

### <a name="invertordinalscale"></a>invertOrdinalScale

此函数用于反转序号刻度。 如果 x < scale.range()[0]，则返回 scale.domain()[0]。
否则，返回 <= x 的 scale.domain() 中的最大项。

```typescript
function invertOrdinalScale(scale: d3.scale.Ordinal<any, any>, x: number);
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let domain: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
  pixelSpan: number = 100,
  ordinalScale: d3.scale.ordinal = axis.createOrdinalScale(
    pixelSpan,
    domain,
    0.4
  );

axis.invertOrdinalScale(ordinalScale, 49);

// returns: 4
```

### <a name="findclosestxaxisindex"></a>findClosestXAxisIndex

此函数查找并返回最近的 x 轴索引。

```typescript
function findClosestXAxisIndex(
  categoryValue: number,
  categoryAxisValues: AxisHelperCategoryDataPoint[]
): number;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

/**
 * Finds the index of the category of the given x coordinate given.
 * pointX is in non-scaled screen-space, and offsetX is in render-space.
 * offsetX does not need any scaling adjustment.
 * @param {number} pointX The mouse coordinate in screen-space, without scaling applied
 * @param {number} offsetX Any left offset in d3.scale render-space
 * @return {number}
 */
private findIndex(pointX: number, offsetX?: number): number {
    // we are using mouse coordinates that do not know about any potential CSS transform scale
    let xScale = this.scaleDetector.getScale().x;
    if (!Double.equalWithPrecision(xScale, 1.0, 0.00001)) {
        pointX = pointX / xScale;
    }
    if (offsetX) {
        pointX += offsetX;
    }

    let index = axis.invertScale(this.xAxisProperties.scale, pointX);
    if (this.data.isScalar) {
        // When we have scalar data the inverted scale produces a category value, so we need to search for the closest index.
        index = axis.findClosestXAxisIndex(index, this.data.categoryData);
    }

    return index;
}
```

### <a name="diffscaled"></a>diffScaled

此函数计算并返回刻度差值。

```typescript
function diffScaled(
  scale: d3.scale.Linear<any, any>,
  value1: any,
  value2: any
): number;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var scale: d3.scale.Linear<number, number>,
    range = [0, 999],
    domain = [0, 1, 2, 3, 4, 5, 6, 7, 8, 999];

scale = d3.scale.linear()
    .range(range)
    .domain(domain);

return axis.diffScaled(scale, 0, 0));

// returns: 0
```

### <a name="createdomain"></a>createDomain

此函数创建轴的值域。

```typescript
function createDomain(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

var domain = axis.createDomain(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="getcategoryvaluetype"></a>getCategoryValueType

此函数获取类别列的 `ValueType`。 如果该类型不存在，则默认值为 `Text`。

```typescript
function getCategoryValueType(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

axis.getCategoryValueType(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="createaxis"></a>createAxis

此函数创建一个包含刻度的 D3 轴。 可以垂直或水平，并且可以是日期/时间、数字或文本。

```typescript
function createAxis(options: CreateAxisOptions): IAxisProperties;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";
// ...

var dataPercent = [0.0, 0.33, 0.49];

var formatStringProp: powerbi.DataViewObjectPropertyIdentifier = {
  objectName: "general",
  propertyName: "formatString"
};
let metaDataColumnPercent: powerbi.DataViewMetadataColumn = {
  displayName: "Column",
  type: ValueType.fromDescriptor({ numeric: true }),
  objects: {
    general: {
      formatString: "0 %"
    }
  }
};

var os = axis.createAxis({
  pixelSpan: 100,
  dataDomain: [dataPercent[0], dataPercent[2]],
  metaDataColumn: metaDataColumnPercent,
  formatString: valueFormatter.getFormatString(
    metaDataColumnPercent,
    formatStringProp
  ),
  outerPadding: 0.5,
  isScalar: true,
  isVertical: true
});
```

### <a name="applycustomizeddomain"></a>applyCustomizedDomain

此函数设置自定义域，但在未设置任何内容时不会更改。

```typescript
function applyCustomizedDomain(customizedDomain, forcedDomain: any[]): any[];
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let customizedDomain = [undefined, 20],
  existingDomain = [0, 10];

axis.applyCustomizedDomain(customizedDomain, existingDomain);

// returns: {0:0, 1:20}
```

### <a name="combinedomain"></a>combineDomain

如果设置了其中一个值，则此函数会将强制域与实际域合并。
forcedDomain 处于第一优先级。 如果任何引用点需要，则扩展该域。

```typescript
function combineDomain(
  forcedDomain: any[],
  domain: any[],
  ensureDomain?: NumberRange
): any[];
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let forcedYDomain = this.valueAxisProperties
  ? [this.valueAxisProperties["secStart"], this.valueAxisProperties["secEnd"]]
  : null;

let xDomain = [minX, maxX];

axis.combineDomain(forcedYDomain, xDomain, ensureXDomain);
```

### <a name="poweroften"></a>powerOfTen

此函数指示数字是否为 10 的幂。

```typescript
function powerOfTen(d: any): boolean;
```

示例：

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.powerOfTen(10);

// returns: true
```

## <a name="datalabelmanager"></a>DataLabelManager

`DataLabelManager` 有助于创建和维护标签。 它使用锚点或矩形排列标签元素。 可以自动检测冲突以重新定位或隐藏元素。

`DataLabelManager` 类提供以下方法：

## <a name="hidecollidedlabels"></a>hideCollidedLabels

此方法根据标签大小和重叠排列画布上的标签位置和可见性。

```typescript
function hideCollidedLabels(
  viewport: IViewport,
  data: any[],
  layout: any,
  addTransform: boolean = false
): LabelEnabledDataPoint[];
```

示例：

```typescript
let dataLabelManager = new DataLabelManager();
let filteredData = dataLabelManager.hideCollidedLabels(
  this.viewport,
  values,
  labelLayout,
  true
);
```

## <a name="isvalid"></a>IsValid

此静态方法检查提供的矩形是否有效（具有正宽度和高度）。

```typescript
function isValid(rect: IRect): boolean;
```

示例：

```typescript
let rectangle = {
  left: 150,
  top: 130,
  width: 120,
  height: 110
};

DataLabelManager.isValid(rectangle);

// returns: true
```

## <a name="datalabelutils"></a>DataLabelUtils

`DataLabelUtils` 提供用于操作数据标签的 utils。

该模块提供了以下函数、接口和类：

### <a name="getlabelprecision"></a>getLabelPrecision

此函数根据给定格式计算精度。

```typescript
function getLabelPrecision(precision: number, format: string): number;
```

### <a name="getlabelformattedtext"></a>getLabelFormattedText

此函数根据给定格式返回格式精度。

```typescript
function getLabelFormattedText(options: LabelFormattedTextOptions): string;
```

示例：

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let options: LabelFormattedTextOptions = {
  text: "some text",
  fontFamily: "sans",
  fontSize: "15",
  fontWeight: "normal"
};

dataLabelUtils.getLabelFormattedText(options);
```

### <a name="enumeratedatalabels"></a>enumerateDataLabels

此函数返回数据标签的 VisualObjectInstance。

```typescript
function enumerateDataLabels(
  options: VisualDataLabelsSettingsOptions
): VisualObjectInstance;
```

### <a name="enumeratecategorylabels"></a>enumerateCategoryLabels

此函数将类别数据标签的 VisualObjectInstance 添加到枚举对象。

```typescript
function enumerateCategoryLabels(
  enumeration: VisualObjectInstanceEnumerationObject,
  dataLabelsSettings: VisualDataLabelsSettings,
  withFill: boolean,
  isShowCategory: boolean = false,
  fontSize?: number
): void;
```

### <a name="createcolumnformattercachemanager"></a>createColumnFormatterCacheManager

此函数返回用于快速访问格式化标签的缓存管理器

```typescript
function createColumnFormatterCacheManager(): IColumnFormatterCacheManager;
```

示例：

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let value: number = 200000;

labelSettings.displayUnits = 1000000;
labelSettings.precision = 1;

let formattersCache = DataLabelUtils.createColumnFormatterCacheManager();
let formatter = formattersCache.getOrCreate(null, labelSettings);
let formattedValue = formatter.format(value);

// formattedValue == "0.2M"
```

## <a name="legend-service"></a>图例服务

`Legend` 服务提供了帮助程序接口，用于创建和管理 Power BI 视觉对象的 PBI 图例

该模块提供了以下函数和接口：

### <a name="createlegend"></a>createLegend

此帮助程序函数可简化 Power BI 自定义视觉对象图例的创建。

```typescript
function createLegend(
  legendParentElement: HTMLElement, // top visual element, container in which legend will be created
  interactive: boolean, // indicates that legend should be interactive
  interactivityService: IInteractivityService, // reference to IInteractivityService interface which need to create legend click events
  isScrollable: boolean = false, // indicates that legend could be scrollable or not
  legendPosition: LegendPosition = LegendPosition.Top // Position of the legend inside of legendParentElement container
): ILegend;
```

示例：

```typescript
public constructor(options: VisualConstructorOptions) {
    this.visualInitOptions = options;
    this.layers = [];

    var element = this.element = options.element;
    var viewport = this.currentViewport = options.viewport;
    var hostServices = options.host;

    //... some other init calls

    if (this.behavior) {
        this.interactivityService = createInteractivityService(hostServices);
    }
    this.legend = createLegend(
        element,
        options.interactivity && options.interactivity.isInteractiveLegend,
        this.interactivityService,
        true);
}
```

### <a name="ilegend"></a>ILegend

此接口可实现创建图例所需的所有方法

```typescript
export interface ILegend {
  getMargins(): IViewport;
  isVisible(): boolean;
  changeOrientation(orientation: LegendPosition): void; // processing legend orientation
  getOrientation(): LegendPosition; // get information about current legend orientation
  drawLegend(data: LegendData, viewport: IViewport); // all legend rendering code is placing here
  /**
   * Reset the legend by clearing it
   */
  reset(): void;
}
```

### <a name="drawlegend"></a>drawLegend

此函数用给定的 SVG 文本属性来度量文本的高度。

```typescript
function drawLegend(data: LegendData, viewport: IViewport): void;
```

示例：

```typescript
private renderLegend(): void {
    if (!this.isInteractive) {
        let legendObjectProperties = this.data.legendObjectProperties;
        if (legendObjectProperties) {
            let legendData = this.data.legendData;
            LegendData.update(legendData, legendObjectProperties);
            let position = <string>legendObjectProperties[legendProps.position];
            if (position)
                this.legend.changeOrientation(LegendPosition[position]);

            this.legend.drawLegend(legendData, this.parentViewport);
        } else {
            this.legend.changeOrientation(LegendPosition.Top);
            this.legend.drawLegend({ dataPoints: [] }, this.parentViewport);
        }
    }
}
```

## <a name="next-steps"></a>后续步骤

- [阅读如何使用 InteractivityUtils 将选择添加到 Power BI 视觉对象](utils-interactivity-selections.md)

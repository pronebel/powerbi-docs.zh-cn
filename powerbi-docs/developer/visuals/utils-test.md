---
title: 关于在 Power BI 视觉对象中使用测试 utils 的简介
description: 本文介绍如何使用测试 Utils 在 Power BI 视觉对象的单元测试中简化模拟和特定方法使用
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196597"
---
# <a name="power-bi-visuals-test-utils"></a>Power BI 视觉对象测试 utils

本文将帮助你安装、导入和使用 Power BI 视觉对象测试 utils。 这些测试实用工具可用于单元测试，包括用于数据视图、选择和颜色架构等元素的模拟和方法。

## <a name="requirements"></a>要求

若要使用此包，需要安装以下各项：

* [node.js](https://nodejs.org)，建议使用 LTS 版本
* [npm](https://www.npmjs.com/)，版本 3.0.0 或更高版本
* [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools) 包

## <a name="installation"></a>安装

若要安装测试 utils 并将其依赖项添加到 package.json  ，请从 Power BI 视觉对象目录运行以下命令：

```bash
npm install powerbi-visuals-utils-testutils --save
```

下面提供有关测试 utils 公共 API 的说明和示例。

## <a name="visualbuilderbase"></a>VisualBuilderBase

由 VisualBuilder  在单元测试中与最常使用的方法 `build`、`update` 和 `updateRenderTimeout` 一起使用。 

`build` 方法返回视觉对象的已创建实例。

需要 `enumerateObjectInstances` 和 `updateEnumerateObjectInstancesRenderTimeout` 方法才能检查 Bucket 和格式设置选项的更改。

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> 有关更多示例，请参阅[编写 VisualBuilderBase 单元测试](./unit-tests-introduction.md#create-a-visual-instance-builder)和 [VisualBuilderBase 实际使用方案](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts)。

## <a name="dataviewbuilder"></a>DataViewBuilder

由 TestDataViewBuilder  使用，此模块提供 `createCategoricalDataViewBuilder` 方法中使用的 CategoricalDataViewBuilder  类。 它还指定在单元测试中处理模拟 DataView  所需的接口和方法。

* `withValues` 添加静态系列列，而 `withGroupedValues` 添加动态系列列

  请勿在视觉对象 DataViewCategorical  中同时应用动态系列和静态系列。 只能在 DataViewCategorical  查询中同时使用两者，在这种查询中，DataViewTransform  应将它们拆分为单独的视觉对象 DataViewCategorical  对象。

* `build` 返回具有元数据和 DataViewCategorical 的 DataView

  如果参数组合不合法（例如，在生成视觉对象 DataView  时同时包含动态和静态系列），则 `build` 返回 Undefined  。

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

用于在单元测试中创建 VisualData  。 将数据放入数据字段 Bucket 时，Power BI 会根据数据生成类别 DataView  对象。 TestDataViewBuilder  可帮助模拟分类 DataView  创建。

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  下表列出了创建 `testDataView` 时最常用的接口：

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> 有关更多示例，请参阅[编写 TestDataViewBuilder 单元测试](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests)和 [TestDataViewBuilder 实际使用方案](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts)。

## <a name="mocks"></a>模拟

### <a name="mockivisualhost"></a>MockIVisualHost

实现 IVisualHost  ，以测试不具有外部依赖项（如 Power BI 框架）的 Power BI 视觉对象。

有用的方法包括 `createSelectionIdBuilder`、`createSelectionManager`、`createLocalizationManager` 和 getter 属性。

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` 创建并返回 IVisualHost  的实例，实际为 MockIVisualHost 
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    示例
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> MockIVisualHost  是 IVisualHost  的虚设实现，只应与单元测试一起使用。

### <a name="mockicolorpalette"></a>MockIColorPalette

实现 IColorPalette  ，以测试不具有外部依赖项（如 Power BI 框架）的 Power BI 视觉对象。

MockIColorPalette  提供用于在单元测试中检查颜色架构或高对比度模式的有用属性。

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` 创建并返回 IColorPalette  的实例，实际为 MockIColorPalette 
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    示例
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> MockIColorPalette  是 IColorPalette  的虚设实现，只应与单元测试一起使用。

### <a name="mockiselectionid"></a>MockISelectionId

实现 ISelectionId  ，以测试不具有外部依赖项（如 Power BI 框架）的 Power BI 视觉对象。

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` 创建并返回 ISelectionId  的实例，实际为 MockISelectionId 
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    示例
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> MockISelectionId  是 ISelectionId  的虚设实现，只应与单元测试一起使用。

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

实现 ISelectionIdBuilder  ，以测试不具有外部依赖项（如 Power BI 框架）的 Power BI 视觉对象。 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` 创建并返回 ISelectionIdBuilder  的实例，实际为 MockISelectionIdBuilder 
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    示例
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> MockISelectionIdBuilder  是 ISelectionIdBuilder  的虚设实现，只应与单元测试一起使用。

### <a name="mockiselectionmanager"></a>MockISelectionManager

实现 ISelectionManager  ，以测试不具有外部依赖项（如 Power BI 框架）的 Power BI 视觉对象。 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` 创建并返回 ISelectionManager  的实例，实际为 MockISelectionManager 
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    示例
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> MockISelectionManager  是 ISelectionManager  的虚设实现，只应与单元测试一起使用。

### <a name="mockilocale"></a>MockILocale

  设置区域设置并在单元测试过程中根据需要进行更改。
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` 创建并返回 MockILocale  的实例
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
模拟 `TooltipService` 并在单元测试过程中根据需要进行调用。
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` 创建并返回 MockITooltipService  的实例
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` 创建并返回 MockIAllowInteractions  的实例
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
提供单元测试所需的 LocalizationManager  的基本功能。
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` 创建并返回 ILocalizationManager  的实例，实际为 MockILocalizationManager 
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    示例
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
模拟 TelemetryService  使用。
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  `MockITelemetryService` 的创建
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
通过提供模拟 AAD 令牌来模拟 AuthenticationService  的工作。
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` 创建并返回 IAuthenticationService  的实例，实际为 MockIAuthenticationService 
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
允许使用行为与 LocalStorage  相同的 ILocalVisualStorageService  。
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` 创建并返回 ILocalVisualStorageService  的实例，实际为 MockIStorageService 
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` 创建并返回 IVisualEventService  的实例，实际为 MockIEventService 
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utils

Utils 包括用于 Power BI 视觉对象单元测试的帮助程序方法，包括与颜色、数字和事件相关的帮助程序。

- `renderTimeout` 返回超时
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` 帮助在单元测试中设置装置
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  示例
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>与颜色相关的帮助程序方法

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  返回以下结构：

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` 比较从输入字符串分析的 RgbColor  对象
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` 从输入字符串分析颜色，并在指定接口 RgbColor  中返回
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>与数字相关的帮助程序方法

- `getRandomNumbers` 使用最小值和最大值生成随机数字。 可以指定 `exceptionList` 并为结果更改提供函数。
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` 提供使用指定最小值和最大值由 `getRandomNumber` 方法生成的随机数字数组
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>与事件相关的帮助程序方法
以下方法是针对单元测试中的网页事件模拟而编写的。

- `clickElement` 模拟对指定元素的单击
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` 返回 Touch  对象以帮助模拟触摸事件
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` 返回模拟触摸  事件的列表
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` 返回 MouseEvent 
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` 创建并返回 MouseEvent 
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>与 D3 事件相关的帮助程序方法

以下方法用于在单元测试中模拟 D3 事件。

- `flushAllD3Transitions` 强制完成所有 D3 转换

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > 通常，在瞬间延迟（< 10 毫秒）之后执行零延迟转换，但如果浏览器将页面呈现两次，则这可能会导致短暂的闪烁。 一次出现在第一个事件循环结束时，随后在第一个计时器回调时立即再次出现。
  >
  > 这些闪烁在 IE 上以及具有大量 Web 视图时更明显，不建议用于 iOS。
  > 
  > 通过在第一个事件循环结束时刷新计时器队列，可以立即运行任何零延迟转换，并避免闪烁。

还包括以下方法：
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>帮助程序接口
以下接口和枚举在帮助程序函数中使用。

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>后续步骤

若要为基于 webpack 的 Power BI 视觉对象编写单元测试，并对 `karma` 和 `jasmine` 进行单元测试，请参阅[教程：为 Power BI 视觉对象项目添加单元测试](./unit-tests-introduction.md)以获得示例。

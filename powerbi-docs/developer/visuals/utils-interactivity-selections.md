---
title: Power BI 视觉对象交互 utils
description: 本文介绍如何通过使用交互 utils 向 Power BI 视觉对象添加选择
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379251"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Power BI 视觉对象交互 utils

交互性 utils (`InteractivityUtils`) 是一组函数和类，可用于简化交叉选择和交叉筛选的实现。

> [!NOTE]
> 交互性 utils 的新更新只支持最新版工具（3.x.x 及更高版本）。

## <a name="installation"></a>安装

1. 若要安装此包，请在当前 Power BI 视觉对象项目所在目录中运行下面的命令。

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. 如果使用的工具是版本 3.0 或更高版本，请安装 `powerbi-models` 来解析依赖关系。

    ```bash
    npm install powerbi-models --save
    ```

3. 若要使用交互性 utils，请在 Power BI 视觉对象的源代码中导入必需组件。

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>添加 CSS 文件

若要将此包与 Power BI 视觉对象结合使用，请将下面的 CSS 文件导入 `.less` 文件。

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

之所以导入 CSS 文件作为 `.less` 文件是因为，Power BI 视觉对象工具包装外部 CSS 规则。

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint 属性

通常，数据点包含选择和值。 此接口扩展 `SelectableDataPoint` 接口。

`SelectableDataPoint` 已包含如下所述的属性。

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>定义数据点接口

1. 创建交互性 utils 实例，然后将对象另存为视觉对象的属性

    ```typescript
    export class Visual implements IVisual {
      // ...
      private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
      // ...
      constructor(options: VisualConstructorOptions) {
          // ...
          this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
          // ...
      }
    }
    ```

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }
    ```

2. 扩展 BaseBehavior 类。

    > [!NOTE]
    > `BaseBehavior` 是在 [5.6.x 版本交互性 utils](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0) 中引入。 如果使用的是旧版本，请通过下面的示例来创建行为类。

3. 定义行为类选项的接口。

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. 为 `visual behavior` 定义类。 或者，扩展 `BaseBehavior` 类。

    **定义 `visual behavior` 类**

    此类负责处理 `click` `contextmenu` 鼠标事件。

    如果用户单击数据元素，视觉对象会调用选择处理程序来选择数据点。 如果用户单击视觉对象的背景元素，视觉对象会调用清除选择处理程序。

    此类有以下对应方法：
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
        protected options: BaseBehaviorOptions<SelectableDataPointType>;
        protected selectionHandler: ISelectionHandler;
    
        protected bindClick() {
          // ...
        }
    
        protected bindClearCatcher() {
          // ...
        }
    
        protected bindContextMenu() {
          // ...
        }
    
        public bindEvents(
            options: BaseBehaviorOptions<SelectableDataPointType>,
            selectionHandler: ISelectionHandler): void {
          // ...
        }
    
        public renderSelection(hasSelection: boolean): void {
          // ...
        }
    }
    ```

    **扩展 `BaseBehavior` 类**

    ```typescript
    import powerbi from "powerbi-visuals-api";
    import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }

    export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
      // ...
    }
    ```

5. 若要处理元素单击，请调用 d3  选择对象 `on` 方法。 这也适用于 `elementsSelection` 和 `clearCatcherSelection`。

    ```typescript
    protected bindClick() {
      const {
          elementsSelection
      } = this.options;
    
      elementsSelection.on("click", (datum) => {
          const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
          mouseEvent && this.selectionHandler.handleSelection(
              datum,
              mouseEvent.ctrlKey);
      });
    }
    ```

6. 为 `contextmenu` 事件添加类似的处理程序，用于调用选择管理器的 `showContextMenu` 方法。

    ```typescript
    protected bindContextMenu() {
        const {
            elementsSelection
        } = this.options;
    
        elementsSelection.on("contextmenu", (datum) => {
            const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
            if (event) {
                this.selectionHandler.handleContextMenu(
                    datum,
                    {
                        x: event.clientX,
                        y: event.clientY
                    });
                event.preventDefault();
            }
        });
    }
    ```

7. 为了将函数分配给处理程序，交互性 utils 调用 `bindEvents` 方法。 将下面的调用添加到 `bindEvents` 方法中：
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

    ```typescript
      public bindEvents(
          options: BaseBehaviorOptions<SelectableDataPointType>,
          selectionHandler: ISelectionHandler): void {

          this.options = options;
          this.selectionHandler = selectionHandler;

          this.bindClick();
          this.bindClearCatcher();
          this.bindContextMenu();
      }
    ```

8. `renderSelection` 方法负责更新图表中的元素的视觉对象状态。 下面展示了 `renderSelection` 的示例实现。

    ```typescript
    public renderSelection(hasSelection: boolean): void {
        this.options.elementsSelection.style("opacity", (category: any) => {
            if (category.selected) {
                return 0.5;
            } else {
                return 1;
            }
        });
    }
    ```

9. 最后一步是，创建 `visual behavior` 实例，并调用交互性 utils 实例的 `bind` 方法。

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` 是 d3  选择对象，表示视觉对象的所有可选择元素。
    * `select(this.target)` 是 d3  选择对象，表示视觉对象的主要 DOM 元素。
    * `this.categories` 是包含元素的数据点，其中接口为 `VisualDataPoint` 或 `categories: VisualDataPoint[];`。
    * `this.behavior` 是在视觉对象的构造函数中新建的 `visual behavior` 实例，如下所示。

      ```typescript
      export class Visual implements IVisual {
        // ...
        constructor(options: VisualConstructorOptions) {
            // ...
            this.behavior = new Behavior();
        }
        // ...
      }
      ```
## <a name="next-steps"></a>后续步骤

* [阅读如何处理书签切换的选择](bookmarks-support.md#visuals-with-selection)

* [阅读如何为视觉对象数据点添加上下文菜单](context-menu.md)

* [阅读如何使用选择管理器将选择添加到 Power BI 视觉对象](selection-api.md)

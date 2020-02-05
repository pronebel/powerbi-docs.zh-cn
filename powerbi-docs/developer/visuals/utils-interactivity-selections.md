---
title: Power BI 视觉对象交互 utils
description: 本文介绍如何通过使用交互 utils 向 Power BI 视觉对象添加选择
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818677"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Microsoft Power BI 视觉对象交互 utils

InteractivityUtils 是一组函数和类，旨在简化 Power BI 自定义视觉对象的交叉选择和交叉筛选的实现。

## <a name="installation"></a>安装

> [!NOTE]
> 如果继续使用旧版本的 powerbi-visuals-tools（版本号小于 3.x.x 版），请安装新版本的工具 (3.x.x)。

> [!IMPORTANT]
> 交互实用工具的最新更新将仅支持最新版本的工具。 [阅读详细信息，如何更新视觉对象以使用最新工具](migrate-to-new-tools.md)

若要安装包，应在目录中运行以下命令和当前的自定义视觉对象：

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

在 3.0 或更高版本中，还需要安装 ```powerbi-models``` 来解析依赖项。

```bash
npm install powerbi-models --save
```

若要使用用户交互实用工具，必须在视觉对象的源代码中导入所需的组件。

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>将 CSS 项目包含到自定义视觉对象

若要将包与自定义视觉对象结合使用，应将以下 CSS 文件导入 `your.less` 文件：

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

因此，你将具有以下文件结构：

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> 你应将 .css 文件作为 less 文件导入，因为 Power BI 视觉对象工具会包装外部 CSS 规则。

## <a name="usage"></a>使用情况

### <a name="define-interface-for-data-points"></a>定义数据点接口

通常，数据点包含选择和值。 该接口会扩展 `SelectableDataPoint` 接口。 `SelectableDataPoint` 已包含属性：

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

使用交互实用工具的第一步是创建交互实用工具的实例，并将对象另存为视觉对象的属性

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

第二步是扩展基行为类：

> [!NOTE]
> [5.6 版交互 utils](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0)中引入了 BaseBehavior。 如果使用的是旧版本，请从以下示例创建行为类（`BaseBehavior` 类相同）：

为行为类的选项定义接口：

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

为 `visual behavior` 定义类。 负责处理 `click`、`contextmenu` 鼠标事件的类。
当用户单击数据元素时，视觉对象将调用选择处理程序来选择数据点。 如果用户单击视觉对象的背景元素，则视觉对象将调用清除选择处理程序。 类具有对应的方法： `bindClick`、`bindClearCatcher`、`bindContextMenu`。

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
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

也可以扩展 `BaseBehavior` 类：

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

若要处理单击元素，请调用 D3 选择对象的 `on` 方法（同样适用于 elementsSelection 和 clearCatcherSelection）：

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

为 `contextmenu` 事件添加类似的处理程序，以调用选择管理器的 `showContextMenu` 方法：

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

交互实用工具调用 `bindEvents` 方法将函数分配给处理程序，将 `bindClick`、`bindClearCatcher` 和 `bindContextMenu` 的调用添加到 `bindEvents` 方法中：

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

`renderSelection` 方法负责更新图表中的元素的视觉对象状态。

`renderSelection` 方法的实现示例：

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

最后一步是创建 `visual behavior` 的实例并调用交互实用工具实例的 `bind` 方法：

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` 是 D3 选择对象，表示视觉对象上的所有可选择元素。

* `select(this.target)` 是 D3 选择对象，表示视觉对象的主要 DOM 元素。

* `this.categories` 是具有元素的数据点，其中接口为 `VisualDataPoint`（或 `categories: VisualDataPoint[];`）

* `this.behavior` 是 `visual behavior` 的新实例

  （在视觉对象的构造函数中创建）：

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

现在，你的视觉对象已准备就绪，可处理选择。

## <a name="next-steps"></a>后续步骤

* [阅读如何处理书签切换的选择](bookmarks-support.md#visuals-with-selection)

* [阅读如何为视觉对象数据点添加上下文菜单](context-menu.md)

* [阅读如何使用选择管理器将选择添加到 Power BI 视觉对象](selection-api.md)

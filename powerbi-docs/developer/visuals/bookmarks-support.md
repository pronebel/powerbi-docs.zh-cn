---
title: 在 Power BI 嵌入式分析中为 Power BI 视觉对象添加书签支持以增强嵌入式 BI 见解
description: Power BI 视觉对象可以处理。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。 书签切换
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 6a4f0e8ad8890e85db54e8d77a2ec19bb0d02ea8
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889101"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>添加对 Power BI 视觉对象的书签支持

使用 Power BI 报表书签可捕获报表页的配置视图、选择状态、视觉对象的筛选状态。 但它需要来自 Power BI 视觉对象的其他操作来支持书签并对更改做出正确反应。

有关书签的详细信息，请参阅[使用书签在 Power BI 中共享见解和创建故事](../../create-reports/desktop-bookmarks.md)。

## <a name="report-bookmarks-support-in-your-visual"></a>视觉对象中的报表书签支持

如果视觉对象与其他视觉对象交互、选择数据点或筛选其他视觉对象，则需要从属性中还原状态。

## <a name="add-report-bookmarks-support"></a>添加报表书签支持

1. 安装（或更新）所需的实用程序 - [powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) 版本 3.0.0 或更高版本。 它包含使用状态选择或筛选器进行操作的其他类。 筛选器视觉对象和使用 `InteractivityService` 的任何视觉对象都需要它。

2. 将视觉对象 API 更新到版本 1.11.0，以便在 `SelectionManager` 的实例中使用 `registerOnSelectCallback`。 使用普通 `SelectionManager` 而非 `InteractivityService` 的非筛选器视觉对象都需要它。

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Power BI 视觉对象如何在报表书签中与 Power BI 进行交互

请考虑以下情景：你希望在报表页上创建多个书签，每个书签中都有不同的选择状态。

首先，在视觉对象中选择一个数据点。 视觉对象通过将选择传递给主机来与 Power BI 和其他视觉对象进行交互。 然后在“书签”窗格中选择“添加”，Power BI 将保存新书签的当前选择。

更改选择并添加新书签时，会重复发生此情况。 创建书签后，可以在它们之间进行切换。

选择书签时，Power BI 会还原已保存的筛选器或选择状态并传递给视觉对象。 根据书签中存储的状态突出显示或筛选其他视觉对象。 Power BI 主机负责执行操作。 视觉对象负责正确反映新的选择状态（例如，更改所呈现的数据点的颜色）。

新的选择状态通过 `update` 方法传达给视觉对象。 `options` 参数包含一个特殊属性 `options.jsonFilters`。 它的 JSONFilter 属性可以包含 `Advanced Filter` 和 `Tuple Filter`。

视觉对象应还原筛选器值，以显示所选书签的视觉对象的对应状态。 或者，如果视觉对象只使用选择，则你可以使用注册为 ISelectionManager 的 `registerOnSelectCallback` 方法的特殊回叫函数。

### <a name="visuals-with-selection"></a>带选择的视觉对象

如果视觉对象使用[选择](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md)与其他视觉对象交互，则可通过以下两种方式之一添加书签：

* 如果视觉对象尚未使用 [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts)，则你可以使用 `FilterManager.restoreSelectionIds` 方法。

* 如果视觉对象已使用 [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts) 来管理选择，则应使用 `InteractivityService` 实例中的 `applySelectionFromFilter` 方法。

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>使用 ISelectionManager.registerOnSelectCallback

选择书签时，Power BI 会使用相应的选择调用视觉对象的 `callback` 方法。 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

假设视觉对象中有一个数据点是在 [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74) 方法中创建的。

`datapoints` 如下所示：

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

现将 `visualDataPoints` 作为数据点，且将 `ids` 数组传递给 `callback` 函数。

此时，视觉对象应将 `ISelectionId[]` 的数组与 `visualDataPoints` 数组中的选择进行比较，并将相应的数据点标记为已选中。

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

更新数据点后，它们将反映存储在 `filter` 对象中的当前选择状态。 然后，当呈现数据点时，自定义视觉对象的选择状态将与书签的状态匹配。

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>使用 InteractivityService 控制视觉对象中的选择

如果视觉对象使用 `InteractivityService`，则无需执行任何其他操作来支持视觉对象中的书签。

选择书签时，该实用程序将处理视觉对象的选择状态。

### <a name="visuals-with-a-filter"></a>带筛选器的视觉对象

假设视觉对象创建了一个按日期范围筛选数据的筛选器。 将 `startDate` 和 `endDate` 作为范围的开始日期和结束日期。

视觉对象创建高级筛选器并调用主机方法 `applyJsonFilter` 按相关条件筛选数据。

目标是用于筛选的表。

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

每次选择书签时，自定义视觉对象都会获取 `update` 调用。

自定义视觉对象应检查对象中的筛选器：

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

如果 `filter` 对象不为 NULL，则视觉对象应从对象还原筛选条件：

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

在此之后，视觉对象应更改其内部状态来反映当前条件。 内部状态包括数据点和可视化对象（线条、矩形等）。

> [!IMPORTANT]
> 在报表书签情景中，视觉对象不应调用 `applyJsonFilter` 来筛选其他视觉对象。 它们已由 Power BI 筛选。

时间线切片器视觉对象会将范围选择器更改为相应的数据范围。

有关详细信息，请参阅[时间线切片器存储库](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df)。

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>筛选状态以在书签中保存视觉对象属性

`filterState` 属性构成筛选某部分的一个属性。 视觉对象可在书签中存储不同的值。

若要将属性值保存为筛选器状态，请在 capabilities.json 文件中将对象属性标记为 `"filterState": true`。

例如，时间线切片器将 `Granularity` 属性值存储在筛选器中。 通过该切片器可在更改书签时更改当前粒度。

有关详细信息，请参阅[时间线切片器存储库](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334)。
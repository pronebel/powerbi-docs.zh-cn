---
title: 从 Power BI 中提取更多数据
description: 本文介绍如何对 Power BI 视觉对象启用大数据集分段提取。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: b8be5b68603f818e26e7f731e4f163bc626b5053
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483687"
---
# <a name="fetch-more-data-from-power-bi"></a>从 Power BI 中提取更多数据

本文介绍如何通过使用 `fetchMoreData` 方法加载更多数据以绕过 30 KB 数据点的硬限制。 这种方法以区块的形式提供数据。 要提高性能，可以配置区块大小以适应用例。

## <a name="limitations-of-fetchmoredata"></a>fetchMoreData 的限制

* 窗口大小限制为 2 到 30,000 范围内。
* 数据视图总行数限制为 1,048,576 行。
* 在段聚合模式下，数据视图内存大小限制为 100 MB。

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>启用大数据集分段提取

对于 `dataview` 段模式，可以在视觉对象的 capabilities.json 文件中为所需的 `dataViewMapping` 定义 `dataReductionAlgorithm` 的窗口大小。 `count` 决定窗口大小，窗口大小可限制每次更新中可追加到 `dataview` 的新数据行数目。

在 capabilities.json 文件中添加以下代码：

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

将新的段追加到现有 `dataview` 并作为 `update` 调用提供给视觉对象。

## <a name="usage-in-the-power-bi-visual"></a>Power BI 视觉对象中的使用情况

在 Power BI 中，可以在默认段聚合模式或增量更新模式下使用 `fetchMoreData`。 

### <a name="using-segments-aggregation-mode-default"></a>使用段聚合模式（默认）

在此模式下，提供给视觉对象的数据视图会包含先前所有 `fetchMoreData requests` 的累积数据。 因此，数据视图的大小预计将随每次更新而增长。 例如，如果预期的总行数为 100,000 行，且窗口大小设置为 10,000，则第一个更新数据视图应包含 10,000 行，第二个更新数据视图应包含 20,000 行，依此类推。

通过使用 `aggregateSegments = true` 调用 `fetchMoreData` 来选择此模式。

可以通过检查是否存在 `dataView.metadata.segment` 来确定数据是否存在：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

还可以通过检查 `options.operationKind` 来检查它是第一次更新还是后续更新。 在以下代码中，`VisualDataChangeOperationKind.Create` 引用第一个段，`VisualDataChangeOperationKind.Append` 引用后续段。

有关示例实现，请参阅以下代码片段：

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

还可以从 UI 事件处理程序调用 `fetchMoreData` 方法，如下所示：

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

作为对调用 `this.host.fetchMoreData` 方法的响应，Power BI 使用新的数据段调用视觉对象的 `update` 方法。

> [!NOTE]
> 为避免客户端内存限制，Power BI 当前将总数据提取量限制为 100 MB。 可以看到 `fetchMoreData()` 返回 `false` 时已达到限制。

### <a name="using-incremental-updates-mode"></a>使用增量更新模式

在此模式下，提供给视觉对象的数据视图只包含增量数据。 因此，数据视图大小不会超过定义的窗口大小。 例如，如果预期的总行数为 101,000 行，且窗口大小设置为 10,000，则视觉对象将获得 10 个数据视图大小为 10,000 的更新，和一个 数据视图大小为 1,000 的更新。

通过使用 `aggregateSegments = false` 调用 `fetchMoreData` 来选择此模式。

可以通过检查是否存在 `dataView.metadata.segment` 来确定数据是否存在：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

还可以通过检查 `options.operationKind` 来检查它是第一次更新还是后续更新。 在以下代码中，`VisualDataChangeOperationKind.Create` 引用第一个段，`VisualDataChangeOperationKind.Segment` 引用后续段。

有关示例实现，请参阅以下代码片段：

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

还可以从 UI 事件处理程序调用 `fetchMoreData` 方法，如下所示：

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

作为对调用 `this.host.fetchMoreData` 方法的响应，Power BI 使用新的数据段调用视觉对象的 `update` 方法。

> [!NOTE]
> 尽管不同更新的数据视图数据之间大多是互斥的，但后续数据视图之间会有一些重叠。
> 对于表和分类数据映射，预计前 N 个数据视图行将包含从上一个数据视图复制的数据。
> N 可以通过以下方式确定：`(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`
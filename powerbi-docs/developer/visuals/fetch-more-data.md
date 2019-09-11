---
title: 从 Power BI 中提取更多数据
description: 本文介绍如何对 Power BI 视觉对象启用大数据集分段提取。
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7e5ecc0e317a21d10e76e9413926822ac4d6760b
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237136"
---
# <a name="fetch-more-data-from-power-bi"></a>从 Power BI 中提取更多数据

本文介绍如何加载更多数据以绕过 30 KB 数据点的硬限制。 这种方法以区块的形式提供数据。 要提高性能，可以配置区块大小以适应用例。  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>启用大数据集分段提取

对于 `dataview` 段模式，在视觉对象的 capabilities.json 文件中为所需的 dataViewMapping 定义 dataReductionAlgorithm 的“窗口”大小  。 `count` 决定窗口大小，窗口大小可限制每次更新中可追加到 `dataview` 的新数据行数目。

在 capabilities.json 文件中添加以下代码  ：

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

可以通过检查是否存在 `dataView.metadata.segment` 来确定数据是否存在：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

还可以通过选中 `options.operationKind` 来检查它是第一次更新还是后续更新。 在以下代码中，`VisualDataChangeOperationKind.Create` 引用第一个段，`VisualDataChangeOperationKind.Append` 引用后续段。

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
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

作为对调用 `this.host.fetchMoreData` 方法的响应，Power BI 使用新的数据段调用视觉对象的 `update` 方法。

> [!NOTE]
> 为避免客户端内存限制，Power BI 当前将总数据提取量限制为 100 MB。 可以看到 fetchMoreData() 返回 `false` 时已达到限制。

---
title: 提取更多数据
description: 对 Power BI 视觉对象启用大数据集分段提取
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425059"
---
# <a name="fetch-more-data-from-power-bi"></a>从 Power BI 中提取更多数据

加载更多数据 API，克服 30,000 个数据点的硬性限制。 它以区块形式加载数据。 可根据用例配置区块大小，以提升性能。  

## <a name="enable-segmented-fetch-of-large-datasets"></a>启用大数据集分段提取

对于 `dataview` 段模式，在视觉对象的 `capabilities.json` 中为所需 dataViewMapping 定义“窗口”dataReductionAlgorithm。
`count` 决定窗口大小，窗口大小可限制每次更新中追加到 `dataview` 的新数据行数目。

要添加到 capabilities.json 中的内容

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

## <a name="usage-in-the-custom-visual"></a>在自定义视觉对象中的用法

可以通过检查是否存在 `dataView.metadata.segment` 来确定是否存在指示数据：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

还可以通过检查 `options.operationKind` 来查看是首次更新还是后续更新。

`VisualDataChangeOperationKind.Create` 表示第一个段，`VisualDataChangeOperationKind.Append` 表示后续段。

有关示例实现，请参阅以下代码片段：

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

还可从 UI 事件处理程序中调用 `fetchMoreData` 方法

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI 将调用视觉对象的 `update` 方法，以新数据段作为响应来调用 `this.host.fetchMoreData` 方法。

> [!NOTE]
> Power BI 目前将总数据提取量限制为 100 MB，以避免客户端内存限制  。 fetchMoreData() 返回“false”即表明已达到该限制。*

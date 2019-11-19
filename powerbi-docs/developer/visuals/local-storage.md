---
title: Power BI 视觉对象中的本地存储 API
description: 本文介绍如何使用 Power BI 视觉对象 API 来获取对浏览器本地存储的访问权限
author: uve
ms.author: v-grniki
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: 3b6746b611a41ddfb471008f5aefa4f7dc391456
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432774"
---
# <a name="local-storage-api"></a>本地存储 API

本地存储 API 这一 API 可由自定义视觉对象用于请求主机保存或加载设备存储中的数据。 从某种意义上说，这是隔离式的，因为不同视觉对象类型之间的存储访问是分开的。

## <a name="sample"></a>示例

如果自定义视觉对象应在每次调用 update 方法时增加某些计数器，但也应保留计数器值，且不在每个视觉对象启动时重置：

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>已知限制和问题

默认情况下，不会为自定义视觉对象激活本地存储 API。 若要为自定义视觉对象激活它，请将请求发送到 Power BI 自定义视觉对象支持 `pbicvsupport@microsoft.com`

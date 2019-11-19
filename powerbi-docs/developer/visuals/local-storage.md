---
title: Power BI 视觉对象中的本地存储 API
description: 本文介绍如何使用 Power BI 视觉对象 API 来获取对浏览器本地存储的访问权限
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879887"
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

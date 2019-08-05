---
title: 视觉对象交互
description: 如何检查确定 Power BI 视觉对象是否应允许视觉对象交互
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424484"
---
# <a name="visuals-interactions"></a>视觉对象交互

视觉对象可以查询“allowInteractions”标志的值，该值指示视觉对象是否应允许视觉对象交互。
例如，在查看或编辑报表时，视觉对象是交互式的，但在仪表板中查看时则不是交互式的。
这些交互包括单击、平移、缩放、选择和其他交互。
请注意，无论此标志是什么，都应在所有方案中启用工具提示。

在视觉对象的初始化过程中，“allowInteractions”标志作为布尔值传递，充当 IVisualHost 接口的成员。

在任何要求视觉对象不是交互式的 Power BI 方案中（例如，仪表板磁贴）-“allowInteractions”标志设置为 false。
否则（例如，报表），“allowInteractions”设置为 true。

有关详细信息，请参阅 [SampleBarChart 视觉对象存储库](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```

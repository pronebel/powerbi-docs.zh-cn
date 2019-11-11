---
title: Power BI 视觉对象中的视觉对象交互
description: 本文介绍如何检查 Power BI 视觉对象是否应允许视觉对象进行交互。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b8b1a1a59ee9fae5a1c248548a14c5f91438edc9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875510"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Power BI 视觉对象中的视觉对象交互

视觉对象可以查询 `allowInteractions` 标志的值，该值指示视觉对象是否应允许视觉对象交互。 例如，在查看或编辑报表时，视觉对象是交互式的，但在仪表板中查看时则不是交互式的。 这些交互包括单击、平移、缩放、选择和其他交互     。 

> [!NOTE]
> 无论显示哪一个标志，都应在所有场景中启用工具提示。

在视觉对象的初始化过程中，`allowInteractions` 标志作为布尔值传递，充当 IVisualHost 接口的成员。

在任何要求视觉对象不是交互式的 Power BI 方案中（例如，仪表板磁贴），`allowInteractions` 标志设置为 `false`。 否则（例如，报表）`allowInteractions` 设置为 `true`。

有关详细信息，请参阅 [SampleBarChart 视觉对象存储库](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)。

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

---
title: Power BI API 将自动保留策略用于实时数据
description: 了解 Power BI 服务的自动保留策略
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b36a5f819ba39d5a77dafc670e440f3577014570
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635116"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>实时数据的自动保留策略

Power BI 服务中的自动保留策略是一个查询字符串参数，用于启用默认保留策略，以便在新数据不断进入仪表板时自动清除旧数据。 第一个保留策略称为先进先出 (FIFO)。  如果已启用，数据将收集在表中，直到它达到 200,000 行。 一旦数据超出 200,000 行，将从该数据集中删除最早的行。 这将使行数保持在 200,000 至 210,000 之间，仅包含最新数据。  
  
<center>

![保留策略](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

首次创建数据集时将启用保留策略。 只需将“default retention policy”查询参数添加到 POST 数据集调用并令其值等于“basicFIFO”即可  。  

```console
POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}
```

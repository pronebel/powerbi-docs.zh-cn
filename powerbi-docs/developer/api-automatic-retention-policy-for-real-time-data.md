---
title: Power BI API 将自动保留策略用于实时数据
description: 了解 Power BI 服务的自动保留策略
author: markingmyname
manager: kfile
ms.author: maghan
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 9b5923c7bd92b1fe53ebb7ab9416aca8cece3cfa
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54294371"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>实时数据的自动保留策略

Power BI 服务中的自动保留策略是一个查询字符串参数，用于启用默认保留策略，以便在新数据不断进入仪表板时自动清除旧数据。 第一个保留策略称为基本先进先出 (FIFO)。 如果已启用，数据将收集在表中，直到它达到 200,000 行。 一旦数据超出 200,000 行，将从该数据集中删除最早的行。 这将使行数保持在 200,000 至 210,000 之间，仅包含最新数据。  
  
<center>

![保留策略](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

首次创建数据集时将启用保留策略。 你只需将“defaultRetentionPolicy”查询参数添加到 POST 数据集调用并令其值等于“basicFIFO”即可。  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}
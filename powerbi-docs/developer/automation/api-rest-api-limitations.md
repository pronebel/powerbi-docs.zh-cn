---
title: Power BI REST API 限制
description: Power BI REST API 具有以下限制
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 5f4067e77631f22951844c0d4d64b06e5e2e30cc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79079568"
---
# <a name="power-bi-rest-api-limitations"></a>Power BI REST API 限制  
  
**POST 行**
  
* 最多 75 列
* 最多 75 个表
* 每个单个 POST 行请求最多 10,000 行  
* 每个数据集每小时添加了 1,000,000 行  
* 每个数据集最多 5 个挂起 POST 行请求  
* 每个数据集每分钟 120 个 POST 行请求
* 如果表的行数大于或等于 250,000，则每个数据集每小时 120 个 POST 行请求
* FIFO 数据集中每个表最多存储了 200,000 行
* “无保留策略”数据集中每表最多存储 5,000,000 行  
* POST 行操作中字符串列的每个值为 4,000 个字符
  
## <a name="see-also"></a>另请参阅

* [Azure AD 服务限制和局限性](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
* [Power BI REST API 概述](https://docs.microsoft.com/rest/api/power-bi/)
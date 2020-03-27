---
title: 在分页报表的 URL 中传递报表参数 - Power BI 报表生成器
description: 本主题介绍如何通过在分页报表 URL 中包含报表参数，向报表传递报表参数。
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 08/29/2019
ms.openlocfilehash: 7a5ec7ef1f66a4a5b6ec80c80e9fd37e19bb2813
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80113545"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>在 Power BI 分页报表的 URL 中传递报表参数 

可通过在分页报表 URL 中包含报表参数，向报表传递报表参数。 所有查询参数都可具有对应的报表参数。 因此，可通过传递相应报表参数来向报表传递查询参数。 需要为参数名称加上 `rp:` 前缀，以便 Power BI 在 URL 中识别它。 

报表参数区分大小写并使用以下特殊字符： 

- URL 的参数部分中的空格将替换为加号 (+)。  例如： 

    ```rp:Holiday=Christmas+Day```

- 字符串的任何部分中的分号将被替换为 `%3A` 字符。

浏览器应自动执行正确的 URL 编码。 不必手动对任何字符进行编码。 

要在 URL 内设置报表参数，请使用以下语法： 

```
rp:parameter=value
```

例如，要指定在“我的工作区”的报表中定义的两个参数“Salesperson”和“State”，请使用以下 URL： 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

要指定在应用中的报表中定义的两个相同参数，请使用以下 URL： 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

要为参数传递 null 值，请使用以下语法： 

```
parameter:isnull=true
```

例如：

```
rp:SalesOrderNumber:isnull=true
```

要传递布尔值，请使用 0 表示 false，使用 1 表示 true。 要传递浮点值，请包含服务器区域设置的小数分隔符。

> [!NOTE]
> 如果报表包含具有默认值的报表参数，并且“Prompt”属性的值为 false（即未在报表管理器中选择“Prompt User”属性），则不能在 URL 中为该报表参数传递值    。 这样，管理员就可以选择阻止最终用户添加或修改某些报表参数的值。
> 
> Power BI 不支持超过 2,000 个字符的查询字符串。  如果使用 url 参数查看分页报表，则可以超过此值。  如果使用多值参数，则更是如此。

## <a name="additional-examples"></a>其他示例 

以下 URL 示例包括一个多值参数“Salesperson”。 多值参数的格式为的是重复每个值的参数名称。 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

以下 URL 示例为本机模式报表服务器传递值为“7/1/2005”的单个参数 SellStartDate。

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>后续步骤

- [Power BI 的分页报表中的 URL 参数](report-builder-url-parameters.md)
- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)

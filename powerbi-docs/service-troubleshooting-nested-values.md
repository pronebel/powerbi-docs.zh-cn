---
title: 对 Power BI 服务中作为文本返回的嵌套值进行故障排除
description: 了解如何解决后述问题：使用不正确的数据源隐私设置时嵌套值转换为字符串
author: cpopell
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: ab40ca9c415dacf52f4d82eb2c157d57aef92f93
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2020
ms.locfileid: "73871292"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>对 Power BI 服务中作为文本返回的嵌套值进行故障排除

## <a name="cause"></a>原因

过去曾发生过这样的情况：Power BI 报表在桌面上可正常刷新，但在 Power BI 服务上刷新失败，并收到错误“无法将值‘[Table]’转换为 Table 类型”。 导致此错误的原因之一是，数据隐私防火墙缓冲数据源时，嵌套的非标量值（如表、记录、列表和函数）会自动转换为文本值（如“[Table]”或“[Record]”）。

现在 Power BI 服务支持设置隐私级别（或完全关闭防火墙），可以通过将 Power BI 服务中的[数据源隐私设置配置为](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/)非专用，避免发生此类错误。

从 6 月开始，防火墙缓冲嵌套表/记录/列表等时，Power BI 不会以无提示方式将此类值转换为文本，而会报以下错误： 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>对加载/刷新操作的影响

虽然这种变化是由防火墙缓冲引起的，但其影响也波及到加载/刷新操作。 为了解决防火墙缓冲行为，还必须将嵌套表/记录等的加载行为更改为 PQ for Excel 中的 Power BI 模型和 Excel 数据模型。 在此之前，嵌套表/记录等作为文本值加载（如“[Table]”或“[Record]”）。 现在这种方式被视为错误，会导致加载表中产生 NULL 值及加载结果中的错误计数增加。

由于这些错误仅在加载/刷新期间发生，因此它们不会出现在 Power Query 编辑器中。

### <a name="before"></a>先于

- 加载/刷新操作无错误
- 加载的表包含“[Table]”、“[Record]”等。
 

### <a name="after"></a>晚于

- 加载/刷新操作出错
- 加载的表包含 NULL（不包含“[Table]”、“[Record]”等）
 

## <a name="resolution"></a>解决方案

是否正在加载包含非标量值（如表、列表、记录等）的列？
如果正在加载，删除列应可消除错误。
如果无法删除列，应可通过添加一个自定义列并使用下例所示逻辑来复制之前的行为：

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

如果将所有数据源隐私设置设为专用，Power BI Desktop 中是否还会发生该问题？
如果还会发生，在 Power BI 服务中将[数据源隐私设置](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/)配置为非专用，应可消除该错误。

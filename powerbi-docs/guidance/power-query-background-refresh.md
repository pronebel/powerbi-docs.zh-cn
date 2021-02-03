---
title: 禁用 Power Query 后台刷新
description: 关于何时禁用 Power Query 后台刷新的指南。
author: peter-myers
ms.author: kfollis
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: e620841089cd7a039fc157fe8b3f8f0857773cb8
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087444"
---
# <a name="disable-power-query-background-refresh"></a>禁用 Power Query 后台刷新

本文主要面向使用 Power BI Desktop 的 Import 数据建模者。

默认情况下，当 Power Query 导入数据时，它还会为每个查询缓存多达 1000 行的预览数据。 预览数据可帮助你快速预览源数据，以及查询的每个步骤的转换结果。 它单独存储在磁盘上，而不是存储在 Power BI Desktop 文件中。

但是，当 Power BI Desktop 文件包含多个查询时，检索和存储预览数据会延长完成刷新所需的时间。

## <a name="recommendation"></a>建议

通过设置 Power BI Desktop 文件来更新后台的预览缓存，可以更快地进行刷新。 在 Power BI Desktop 中，通过选择“文件”>“选项和设置”>“选项”，然后选择“数据加载”页面来启用 。 然后可以打开“允许在后台下载数据预览”选项。 请注意，仅可为当前文件设置此选项。

![显示背景数据选项的 Power BI Desktop 的屏幕截图。](media/power-query-background-refresh/power-query-options-background-data.png)

启用后台刷新可能导致预览数据过期。 如果发生这种情况，Power Query 编辑器会通过以下警告通知你：

![Power BI Desktop 的屏幕截图，其中显示了关于旧预览数据的 Power Query 编辑器警告。](media/power-query-background-refresh/power-query-preview-data-old.png)

始终可以更新预览缓存。 可以通过使用“刷新预览”命令来针对单个查询或所有查询进行更新。 你将在 Power Query 编辑器窗口的“主页”功能区中找到它。

![Power BI Desktop 的屏幕截图，其中显示了用于刷新预览数据的 Power Query 编辑器命令。](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power Query 文档](/power-query/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)

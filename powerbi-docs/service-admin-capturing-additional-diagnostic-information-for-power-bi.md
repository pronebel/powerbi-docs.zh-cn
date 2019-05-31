---
title: 捕获其他诊断信息
description: 以下说明介绍了用于手动从 Power BI Web 客户端收集其他诊断信息的两种可能选择。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100247"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>捕获 Power BI 的其他诊断信息

本文提供了用于手动从 Power BI web 客户端收集其他诊断信息的说明。

1. 浏览到[Power BI](https://app.powerbi.com)与 Microsoft Edge 或 Internet 资源管理器。

1. 按**F12**以打开 Microsoft Edge 开发人员工具。

   ![屏幕截图的 Microsoft Edge 开发人员工具元素选项卡。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. 选择“网络”选项卡  。它将列出已捕获的流量。

   ![屏幕截图的 Microsoft Edge 开发人员工具网络选项卡。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    你可以：

    * 在窗口中浏览并重现您可能会遇到任何问题。

    * 隐藏和显示开发人员工具窗口在会话期间随时通过按 F12。

1. 若要停止分析会话，可以选择的红色方块上**网络**选项卡上的开发人员工具区域。

   ![屏幕截图的 Microsoft Edge 开发人员工具网络选项卡通过调用带停止按钮。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. 选择磁盘图标以将数据导出为 HTTP 存档 (HAR) 文件。

   ![屏幕截图的 Microsoft Edge 开发人员工具网络选项卡带有软盘图标的标注。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. 提供文件名称并保存该 HAR 文件。

    HAR 文件将包含有关浏览器窗口与 Power BI 包括之间的网络请求的所有信息：

    * 为每个请求活动 Id。

    * 每个请求的精确时间戳。

    * 任何错误信息返回到客户端。

    此跟踪还会包含用于填充屏幕上显示的视觉对象的数据。

1. 你可以提供该 HAR 文件以支持审阅。

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)

---
title: 比较 Power BI 报表服务器和 Power BI 服务
description: 本文将 Power BI 报表服务器和 Power BI 服务的功能进行比较。
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 11/06/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: a693eef85f7eafe7cfac2a02cbccc346201a6f13
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507683"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>比较 Power BI 报表服务器和 Power BI 服务

Power BI 报表服务器和 Power BI 服务有许多相似之处和一些关键区别。 此表对其分别进行介绍。

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Power BI 报表服务器和 Power BI 服务的功能

| 功能 | Power BI 报表服务器 | Power BI 服务 | 注意
|---------|---------|---------|---------|
| 部署 | 本地云或托管云 | 云 | 如果通过 Power BI Premium 获得许可，则可以在 Azure VM（托管云）中部署 Power BI 报表服务器
| 源数据 | 云和/或本地 | 云和/或本地 |  
| 许可证 | 带 SA 的 Power BI Premium 或 SQL Server EE | Power BI Pro 和/或 Power BI Premium |  
| 生命周期 | 现代生命周期策略 | 完全托管的服务 |  
| 发行周期 | 每 4 个月一次 | 每个月一次 | Power BI 服务中首先提供最新功能和修补程序。 Power BI 报表服务器在接下来的几个版本中提供了最核心功能；某些功能仅适用于 Power BI 服务。
| 在 Power BI Desktop 中创建 Power BI 报表 | 是 | 是 |  
| 在浏览器中创建 Power BI 报表 | 否 | 是 |  
| 是否需要网关 | 否 | 对于本地数据源，则为“是” |  
| 实时流式处理 | 否 | 是 | [Power BI 中的实时流式处理](../service-real-time-streaming.md)
| 仪表板 | 否 | 是 | [Power BI 服务中的仪表板](../consumer/end-user-dashboards.md) 
| 使用应用分发报表组 | 否 | 是 | [创建和发布包含仪表板和报表的应用](../service-create-distribute-apps.md) 
| 内容包 | 否 | 是 | [组织内容包：简介](../service-organizational-content-pack-introduction.md) 
| 连接到 Salesforce 等服务 | 否 | 是 | 使用 Power BI 服务[连接到所使用的服务](../consumer/end-user-connect-to-services.md)
| 问答 | 否 | 是 | [Power BI 服务和 Power BI Desktop 中的问答](../consumer/end-user-q-and-a.md) 
| 快速见解 | 否 | 是 | [通过 Power BI 自动生成数据见解](../consumer/end-user-insights.md) 
| 在 Excel 中分析 | 否 | 是 | [在 Excel 中分析](../service-analyze-in-excel.md) 
| 分页报表 | 是 | 是 | [Power BI 服务中提供的分页报表](../paginated-reports-report-builder-power-bi.md)处于预览状态
| Power BI 移动应用 | 是 | 是 | [Power BI 移动应用概述](../consumer/mobile/mobile-apps-for-mobile-devices.md) 
| ARC GIS 地图 | 否 | 是 | [Power BI 服务和 Power BI Desktop 中通过 Esri 实现的 ArcGIS 地图](../power-bi-visualization-arcgis.md)
| Power BI 报表的电子邮件订阅 | 否 | 是 | 在 Power BI 服务中[订阅报表或仪表板](../consumer/end-user-subscribe.md) 
| 分页报表的电子邮件订阅 | 是 | 否 | [Reporting Services 中的电子邮件传递](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| 数据警报 | 否 | 是 | Power BI 服务中的[数据警报](../service-set-data-alerts.md)
| 行级别安全性 | 只能通过 DirectQuery 模式下的数据源 | 在 DirectQuery（数据源）和导入模式下均可用 | Power BI [行级别安全性 (RLS)](../service-admin-rls.md) 
| 全屏模式 | 否 | 是 | Power BI 服务中的[全屏模式](../consumer/end-user-focus.md) 
| 高级 Office 365 协作 | 否 | 是 | 使用 Office 365 [在应用工作区中协作](../service-collaborate-power-bi-workspace.md) 
| R 视觉对象 | 否 | 是 | 在 Power BI 服务中[创建 R 视觉对象](../visuals/service-r-visuals.md)  
| 预览功能 | 否 | 是 | [选择使用 Power BI 服务预览](../consumer/end-user-preview-features.md)功能 
| 自定义视觉对象 | 是 | 是 | [在 Power BI 中自定义视觉对象](../power-bi-custom-visuals.md) 
| Power BI Desktop | 更适合报表服务器的版本，可使用报表服务器下载 | 更适合 Power BI 服务的版本，可从 Windows 应用商店下载 | [适用于报表服务器的 Power BI Desktop](https://powerbi.microsoft.com/report-server/) <br><br> [适用于 Power BI 服务的 Power BI Desktop](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>后续步骤
[安装 Power BI 报表服务器](install-report-server.md)  




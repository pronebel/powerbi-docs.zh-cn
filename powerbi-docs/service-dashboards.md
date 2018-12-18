---
title: Power BI 设计器的仪表板简介
description: 仪表板是 Power BI 服务的一个主要功能。 仪表板是通过可视化效果讲述故事的单个页面，常被称为画布。
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 7a1187373304387ac511053d241e5cfb31f7fcd9
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280572"
---
# <a name="intro-to-dashboards-for-power-bi-designers"></a>Power BI 设计器的仪表板简介

Power BI“仪表板”是通过可视化效果讲述故事的单个页面，常被称为画布。 因为它被限制为一页，设计精良的仪表板仅包含该故事的亮点。 读者可查看相关报表了解详细信息。

![仪表板](media/service-dashboards/power-bi-dashboard2.png)

仪表板是 Power BI 服务的一个功能。 Power BI Desktop 中无此功能。 无法在移动设备上创建仪表板，但可以[查看和共享](mobile-apps-view-dashboard.md)仪表板。

## <a name="dashboard-basics"></a>仪表板基础知识 

仪表板上的可视化效果称为“磁贴”。 从报表将磁贴“固定”到仪表板。 如果不熟悉 Power BI，可以通过阅读 [Power BI 基本概念](service-basic-concepts.md)详细了解基础知识。

> [!IMPORTANT]
> 需要 [Power BI Pro](service-free-vs-pro.md) 许可证方可创建仪表板。

仪表板上的可视化效果来自报表，并且每个报表基于一个数据集。 对于仪表板，一种看法是它是基础报表和数据集的入口。 选择一个可视化效果即可转到其所基于的报表（和数据集）。

![显示仪表板、报表、数据集之间的关系的图表](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>仪表板的优点
仪表板是监控业务，以及查看所有最重要指标的绝佳方法。 仪表板上的可视化效果可能来自一个或许多个基础数据集，也可能来自一个或多个基础报表。 仪表板将本地数据和云数据合并到一起，提供合并视图（无论数据源自哪里）。

仪表板不仅仅是美观的图片。 它具有高度互动性，并且磁贴随着基础数据的更改而更新。

## <a name="dashboards-versus-reports"></a>仪表板与报表
[报表](service-reports.md)与仪表板类似，这是因为二者都是填充可视化效果的画布。 但它们存在一些主要差异。

| **功能** | **仪表板** | **报表** |
| --- | --- | --- |
| 页面 |一个页面 |一个或多个页面 |
| 数据源 |每个仪表板的一个或多个报表和一个或多个数据集 |每个报表的单个数据集 |
| 可用于 Power BI Desktop |否 | 可在 Power BI Desktop 中生成和查看报表 |
| 订阅 |可订阅仪表板 |可以订阅报表页面 |
| 筛选 |无法筛选或切片 |许多不同的方式来筛选、突出显示和切片 |
| 特色 |可以将一个仪表板设置为“精选”仪表板 |无法创建精选报表 |
| 收藏夹 | 可将仪表板设置为“收藏夹” | 可将报表设置为“收藏夹”
| 设置警报 |可在某些情况下用于仪表板磁贴 |从报表不可用 |
| 自然语言查询（“问答”） |在仪表板中可用 | 在报表中可用 |
| 可以看到基础数据集表和字段 |不行。 可以导出数据，但看不到仪表板本身的表和字段。 |是的。 可以查看数据集表和字段以及值。 |


## <a name="next-steps"></a>后续步骤
* 通过参观我们的[示例仪表板](sample-tutorial-connect-to-the-samples.md)之一，轻松了解仪表板的使用。
* 了解[仪表板磁贴](service-dashboard-tiles.md)。
* 想要跟踪单个仪表板磁贴并在该磁贴达到某个阈值时接收电子邮件？ [在磁贴上创建警报](service-set-data-alerts.md)。
* 了解如何使用 [Power BI 问答](power-bi-tutorial-q-and-a.md)询问有关你的数据的问题，并以可视化效果的形式获得答案。

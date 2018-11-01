---
title: Power BI 服务中的仪表板
description: 仪表板是 Power BI 服务的一个主要功能。
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: b7f94d47452fb9d1ea24c950dba2988c6c80c053
ms.sourcegitcommit: 2c4a075fe16ccac8e25f7ca0b40d404eacb49f6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2018
ms.locfileid: "49473719"
---
# <a name="dashboards-in-the-power-bi-service"></a>Power BI 服务中的仪表板

Power BI ***仪表板***是单个页面，通常称为画布，使用可视化效果来讲述故事。 因为它被限制为一页，精心设计的仪表板仅包含该故事的最重要元素。

![仪表板](media/service-dashboards/power-bi-dashboard2.png)

仪表板是 Power BI 服务的一项功能，在 Power BI Desktop 中不可用。 无法在移动设备上创建仪表板，但可以[查看和共享](mobile-apps-view-dashboard.md)。

## <a name="dashboard-creators-and-dashboard-consumers"></a>仪表板创建者和仪表板使用者
根据你的角色，你可能会创建仪表板供你自己使用或与同事共享。 可在“创建者仪表板”中查找你的信息。 如果需要从其他人那里接收仪表板。 你想要了解如何了解并与仪表板进行交互。 请阅读这篇文章！


### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>如果你要接收和使用仪表板

仪表板上显示的可视化效果称为磁贴，由仪表板的创建者从报表固定到仪表板中。 如果不熟悉 Power BI，可以通过阅读 [Power BI 基本概念](service-basic-concepts.md)详细了解基础知识。

> [!IMPORTANT]
> 若要查看共享仪表板，需使用 [Power BI Pro](service-free-vs-pro.md)。

仪表板上的可视化效果来自报表，并且每个报表基于一个数据集。 事实上，一种想到仪表板的方法就是进入基础报表和数据集。 选择一个可视化效果可将你转到用于创建仪表板的报表（和数据集）。

![显示仪表板、报表、数据集之间的关系的图表](media/service-dashboards/power-bi-diagram.png)



## <a name="advantages-of-dashboards"></a>仪表板的优点
仪表板是监控你的业务、寻找答案以及查看所有最重要指标的绝佳方法。 仪表板上的可视化效果可能来自一个或许多个基础数据集，也可能来自一个或多个基础报表。 仪表板将本地数据和云数据合并到一起，提供合并视图（无论数据源自哪里）。

仪表板不仅仅是一张漂亮的图片；它具有高度互动性，并且磁贴随着基础数据的更改而更新。

## <a name="dashboards-versus-reports"></a>仪表板与报表
[报表](service-reports.md)经常与仪表板混淆，因为它们也是填充可视化效果的画布。 但对于 Power BI 使用者而言，它们存在一些较大的差异。

| **功能** | **仪表板** | **报表** |
| --- | --- | --- |
| 页面 |一个页面 |一个或多个页面 |
| 数据源 |每个仪表板的一个或多个报表和一个或多个数据集 |每个报表的单个数据集 |
| 可用于 Power BI Desktop |否 |是，创建者可在 Desktop 中生成和查看报表 |
| 订阅 |可订阅仪表板 |可以订阅报表页面 |
| 筛选 |无法筛选或切片 |许多不同的方式来筛选、突出显示和切片 |
| 特色 |可以将一个仪表板设置为“精选”仪表板 |无法创建精选报表 |
| 收藏夹 | 可将仪表板设置为“收藏夹” | 可将报表设置为“收藏夹”
| 设置警报 |可在某些情况下用于仪表板磁贴 |从报表不可用 |
| 自然语言查询 |从仪表板可用 |从报表不可用 |
| 可以看到基础数据集表和字段 |不行。 可以导出数据，但看不到仪表板本身的表和字段。 |是的。 可以查看数据集表和字段以及值。 |
| 自定义 |否 |在“阅读”视图中，你可以发布、嵌入、筛选、导出、下载为 .pbix，查看相关内容，生成 QR 码，在 Excel 中进行分析等。  |

## <a name="next-steps"></a>后续步骤
* 通过参观我们的[示例仪表板](sample-tutorial-connect-to-the-samples.md)之一，轻松了解仪表板的使用。
* 了解[仪表板磁贴](service-dashboard-tiles.md)，以及当你选择一个磁贴时将发生的情况。
* 想要跟踪单个仪表板磁贴并在该磁贴达到某个阈值时接收电子邮件？ [在磁贴上创建警报](service-set-data-alerts.md)。
* 随时询问你的仪表板相关问题。 了解如何使用 [Power BI 问答](power-bi-tutorial-q-and-a.md)询问有关你的数据的问题，并以可视化效果的形式获得答案。

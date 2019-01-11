---
title: Power BI Embedded 性能最佳做法
description: 本文提供嵌入式分析最佳做法相关指导
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: e28801a15cf50351d737af63bc48f655ca85d28f
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008157"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Power BI Embedded 性能最佳做法

本文提供在应用程序中更快呈现报表、仪表板和磁贴的相关建议

## <a name="embed-parameters"></a>嵌入参数

Powerbi.embed() 方法接收几个参数，用于嵌入报表、仪表板或磁贴。 这些参数会影响性能。

### <a name="embed-url"></a>嵌入 URL

避免自己生成嵌入 URL。 确保通过调用[获取报表](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Freports%2Fgetreportsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=22lkqRM2w1MQfrM8dooedaPqqIU8PufTq9TT4VDzRo0%3D&reserved=0)、[获取仪表板](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgetdashboardsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=nfWRgbSoXVF42Rg%2Ba9491u19uksXp%2FAyz%2Fa%2Ba7%2FCtdA%3D&reserved=0)或[获取磁贴](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgettilesingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256178318&sdata=LgZ27TynNpqQJDrb3aHWGQXIS%2FzichAO9De5M2uhF1Q%3D&reserved=0) API 来获取嵌入 URL。 我们将一个名为 config 的参数添加到了 URL，用于改进性能。

### <a name="permissions"></a>权限

如果不打算在“编辑模式”下嵌入报表，则提供“查看”权限。 通过这种方式，嵌入代码不会初始化用于“编辑”模式的组件。

### <a name="filters-bookmarks-and-slicers"></a>筛选器、书签和切片器

通常情况下，报表视觉对象会连同缓存数据一并保存。 缓存数据用于提供感知性能。 执行查询时，报表会呈现缓存数据。 如果提供了筛选器、书签或切片器，则缓存数据就没有作用了。 然后仅在运行视觉对象查询后呈现视觉对象。

如果使用相同筛选器来嵌入报表，为避免在加载配置中传入筛选器列表，请使用已应用的筛选器保存报表。

## <a name="preload"></a>预加载

使用预加载 JavaScript API 改进最终用户性能。
Powerbi.preload() 会下载 javascript、css 文件和其他项目，稍后会在报表中嵌入该方法。

如果不立即嵌入报表，请调用预加载。 例如，如果通过点击按钮嵌入报表，最好在加载上一页面时调用预加载。 这样，当应用程序用户点击按钮时，呈现速度会更快。

## <a name="measure-performance"></a>测量性能

若要测量性能，请使用：

1. 加载：报表初始化完成前的等待时间（用户看不到旋转）。
2. 呈现：使用实际数据呈现出完整报表所用的时间。 每次重新呈现报表（即应用筛选器后）时将触发呈现事件。 若要首先测量报表，请确保在第一个事件中执行了计算。

缓存数据会在可用时呈现，但是我们尚不具有此数据的事件。

## <a name="update-tools-and-sdk-packages"></a>更新工具和 SDK 包

使工具和 SDK 包保持最新。

* 始终使用最新版本的 [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/)。

* 安装最新版本的 [Power BI 客户端 SDK](https://github.com/Microsoft/PowerBI-JavaScript)。 我们将持续发布增强功能，请持续关注并跟进后续发布。

* 要安装的包：
    * Npm 包：powerbi-client
    * NuGet 包：Microsoft.PowerBI.JavaScript

> [!Note]
> 请记住，加载时间主要取决于与报表和数据本身相关的元素。 例如视觉对象数量、数据大小、查询复杂程度以及计算的度量值。 请按照[最佳做法](../power-bi-reports-performance.md)进行操作以缩短报表的加载时间。

## <a name="next-steps"></a>后续步骤

* [Power BI 报表性能最佳做法](../power-bi-reports-performance.md)
* [如何对 Power BI Embedded 问题进行故障排除](embedded-troubleshoot.md)
* [Power BI Embedded 常见问题解答](embedded-faq.md)

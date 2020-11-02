---
title: 更改 Power BI 报表的设置
description: 更改 Power BI 服务中报表的设置
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/14/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: dd87501a6865b9ea450e3154ee2ac56e0710a067
ms.sourcegitcommit: fddba666c6ea90d525a1c3188bbd3c4a03410cdc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2020
ms.locfileid: "92463026"
---
# <a name="change-settings-for-power-bi-reports"></a>更改 Power BI 报表的设置

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

通过 Power BI Desktop 和 Power BI 服务中的报表设置，可以控制报表读取者与报表的交互方式。 例如，可以允许他们保存报表的筛选器，对报表中的视觉对象进行个性化设置，或在报表底部（而不是沿侧面）以选项卡的形式显示报表页。

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Power BI 服务中“报表设置”窗格的屏幕截图。":::

首先阅读以下文章可能会有所帮助：

- [通过导入数据集在 Power BI 服务中创建报表](service-report-create-new.md) - 了解报表创建体验。
- [Power BI 中的报表](../consumer/end-user-reports.md) - 了解报表读取者的体验。

 让我们开始吧！

## <a name="prerequisites"></a>先决条件

- 有关使用 Power BI Desktop 创建报表的信息，请参阅 [Desktop 报表视图](desktop-report-view.md)。
- [注册 Power BI 服务](../fundamentals/service-self-service-signup-for-power-bi.md)。 
- 你需要对 Power BI 服务中的报表具有编辑权限。 有关权限的详细信息，请参阅[新工作区中的角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。
- 如果 Power BI 服务中还没有报表，则可以[安装示例内容包](sample-datasets.md#install-built-in-content-packs)，其中包含仪表板、报表和数据集。

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>在 Power BI Desktop 中打开“设置”窗格

1. 选择“文件” > “选项和设置” > “选项”。
1. 在“当前文件”下，选择“报表设置” 。

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Power BI 服务中“报表设置”窗格的屏幕截图。":::

    本文的其余部分将介绍某些特定的报表设置。

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>在 Power BI 服务中打开“设置”窗格

1. 在报表“阅读”视图中，选择“文件” > “设置” 。

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="Power BI 服务中“报表设置”窗格的屏幕截图。":::

1. 在“设置”窗格中，可以看到仅针对此报表可以设置的多个切换。 本文的其余部分将介绍其中的一些内容。

## <a name="set-featured-content"></a>设置特色内容

你可以特别仪表板、报表和应用，使其显示在同事的 Power BI 主页的“特别推荐”部分中。 详细了解[如何特别推荐内容](../collaborate-share/service-featured-content.md)。

## <a name="set-the-pages-pane"></a>设置“页面”窗格

目前只能更改 Power BI 服务中的“页面”窗格设置。 在你将“页面”窗格切换为开启时，报表读取者会在“阅读”视图中报表的底部（而不是侧面）看到报表页选项卡。 在“编辑”视图中，报表页选项卡已位于报表的底部。

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="Power BI 服务中“报表设置”窗格的屏幕截图。":::

## <a name="control-filters"></a>控制筛选器

报表的“设置”窗格具有三个设置，用于控制读取者与报表筛选器的交互。 有关每个设置的详细信息，请访问以下链接，转到[设计 Power BI 报表中的筛选器](power-bi-report-filter.md)。

- “永久性筛选器”允许读取者[保存报表的筛选器](power-bi-report-filter.md#allow-saving-filters)。
- “筛选体验”还有另外两项设置：
    
    允许报表读取者[更改筛选器类型](power-bi-report-filter.md#restrict-changes-to-filter-type)。

    [在筛选器窗格中启用搜索](power-bi-report-filter.md#filters-pane-search)。

## <a name="export-data"></a>导出数据

默认情况下，报表读取者可以从你的报表中的视觉对象[导出已汇总数据或基础数据](../consumer/end-user-export.md)。 通过“导出数据”，你可以使他们从你的报表中只导出已汇总数据，或者无法导出任何数据。

## <a name="personalize-visuals"></a>个性化视觉对象

允许读取者更改报表中的视觉对象并对其进行个性化设置。 详细了解如何[使报表读取者可以对视觉对象进行个性化设置](power-bi-personalize-visuals.md)。

## <a name="next-steps"></a>后续步骤

* [其他人主页上的特别推荐内容](../collaborate-share/service-featured-content.md)
* [使报表读取者可对报表中的视觉对象进行个性化设置](power-bi-personalize-visuals.md)
* 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

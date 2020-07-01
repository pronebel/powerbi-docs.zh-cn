---
title: Power BI 设计器的仪表板磁贴简介
description: 本文介绍 Power BI 中的仪表板磁贴，其中包括从 SQL Server Reporting Services (SSRS) 报表创建的磁贴。
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/17/2020
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 9a6db74384a9fa47d13eb36b0e64cb926600a191
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85219663"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Power BI 设计器的仪表板磁贴简介

磁贴就是固定到仪表板的数据快照。 可以从报表、数据集、仪表板、问答框、Excel 和 SQL Server Reporting Services (SSRS) 报表等位置创建磁贴。  此屏幕截图显示了固定到仪表板的许多不同的磁贴。

![Power BI 仪表板](media/service-dashboard-tiles/power-bi-dashboard.png)

仪表板和仪表板磁贴是 Power BI 服务的一项功能，而不是 Power BI Desktop 的功能。 无法在移动设备上创建仪表板，但可以[查看和共享](../consumer/mobile/mobile-apps-view-dashboard.md)仪表板。

除固定的磁贴以外，还可使用[添加磁贴](service-dashboard-add-widget.md)控件直接在仪表板上创建独立磁贴。 独立磁贴包含：文本框、图像、视频、流数据和 Web 内容。

需要有关理解构成 Power BI 的生成块的帮助？ 请参阅 [Power BI 服务中设计器的基本概念](../fundamentals/service-basic-concepts.md)。

> [!NOTE]
> 如果原始可视化效果用于创建磁贴更改，则磁贴不会更改。  例如，如果从报表固定一个折线图，然后将折线图更改为条形图，则仪表板磁贴将继续显示为折线图。 数据将会刷新，但可视化效果类型不会。
> 
> 

## <a name="pin-a-tile"></a>固定磁贴
向仪表板添加（固定）磁贴有多种不同的方法。 可根据从以下位置固定磁贴：

* [Power BI 问答](service-dashboard-pin-tile-from-q-and-a.md)
* [报表](service-dashboard-pin-tile-from-report.md)
* [其他仪表板](service-pin-tile-to-another-dashboard.md)
* [OneDrive for Business 上的 Excel 工作簿](service-dashboard-pin-tile-from-excel.md)
* [Quick Insights (快速见解)](service-insights.md)
* [Power BI 报表服务器或 SQL Server Reporting Services 中的本地分页报表](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

使用[添加磁贴](service-dashboard-add-widget.md)控件直接在仪表板上创建图像、文本框、视频、流数据和 Web 内容的独立磁贴。

  ![添加磁贴图标](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>与仪表板上的磁贴进行交互
将磁贴添加到仪表板之后，可以移动它、调整它的大小，或者更改它的外观和行为。

### <a name="move-and-resize-a-tile"></a>移动和重设磁贴大小
获取一个磁贴并[将它在仪表板上移动](service-dashboard-edit-tile.md)。 将鼠标悬停在图柄 ![磁贴图柄](media/service-dashboard-tiles/resize-handle.jpg) 上并选择它，以重设磁贴大小。

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>将鼠标悬停在磁贴上以更改外观和行为
1. 将鼠标悬停在磁贴上以显示省略号。
   
    ![磁贴省略号](media/service-dashboard-tiles/ellipses_new.png)
2. 选择省略号以打开磁贴操作菜单。
   
    ![省略号图标](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    此处你可以：
   
     * [将注释添加到仪表板](../consumer/end-user-comment.md)。
     * [打开用于创建此磁贴的报表](../consumer/end-user-reports.md)。  
     * [在焦点模式下查看](../consumer/end-user-focus.md)。   
     * [导出磁贴中使用的数据](../visuals/power-bi-visualization-export-data.md)。
     * [编辑标题和副标题以及添加超链接](service-dashboard-edit-tile.md)。 
     * [运行见解](service-insights.md)。 
     * [将磁贴固定到另一个仪表板](service-pin-tile-to-another-dashboard.md)。
     * [删除磁贴](service-dashboard-edit-tile.md)。

3. 若要关闭操作菜单，请选择仪表板中的空白区域。

### <a name="select-a-tile"></a>选择磁贴
选择磁贴时，出现的下一步取决于该磁贴的创建方式。 否则，选择磁贴将转到报表、Excel Online 工作簿、本地 Reporting Services 报表或用于创建该磁贴的问答问题。 或者，如果它有[自定义链接](service-dashboard-edit-tile.md)，则选择该磁贴将转到该链接。

> [!NOTE]
> 但在仪表板上直接使用“添加磁贴”创建的视频磁贴不适用。 选择视频磁贴（以这种方式创建的）将导致视频直接在仪表板上播放。   
> 
> 

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

* 如果未保存用于创建可视化效果的报表，则选择磁贴将不会产生任何操作。
* 如果是从 Excel Online 工作簿创建磁贴，则至少需要该工作簿的“读取”权限。 否则，选择磁贴将不会打开 Excel Online 工作簿。
* 假设使用“添加磁贴”直接在仪表板上创建磁贴，并为其设置自定义超链接。 这样在选择标题、副标题或磁贴时便会打开该 URL。 否则，默认情况下，选择直接在仪表板上创建的图像、Web 代码或文本框磁贴都不会产生任何反应。
* 磁贴可以从 Power BI 报表服务器或 SQL Server Reporting Services 中的本地分页报表创建。 如果无权访问本地报表，则选择磁贴将会转到一个页面，该页面显示没有访问权限 (rsAccessDenied)。
* 假设选择从 Power BI 报表服务器或 SQL Server Reporting Services 中的本地分页报表创建的磁贴。 如果没有报表服务器所在网络的访问权限，则选择从该分页报表创建的磁贴时，会出现一个页面，表明找不到服务器 (HTTP 404)。 设备需要具有对报表服务器的网络访问权限方可查看该报表。
* 即使用于创建磁贴的原始可视化效果发生更改，磁贴也不会更改。 例如，如果从报表固定一个折线图，然后将折线图更改为条形图，则仪表板磁贴会继续显示为折线图。 数据将会刷新，但可视化效果类型不会。

## <a name="next-steps"></a>后续步骤
- [为仪表板创建卡片（大数字磁贴）](../visuals/power-bi-visualization-card.md)
- [Power BI 设计器的仪表板简介](service-dashboards.md)  
- [Power BI 中的数据刷新](../connect-data/refresh-data.md)
- [Power BI 服务中设计器的基本概念](../fundamentals/service-basic-concepts.md)
- [Integrating Power BI tiles into Office documents](https://powerbi.microsoft.com/blog/integrating-power-bi-tiles-into-office-documents/)（将 Power BI 磁贴集成到 Office 文档）
- [将 Reporting Services 项目固定到 Power BI 仪表板](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)。

---
title: Power BI 服务中的仪表板磁贴
description: 关于 Power BI 中的仪表板磁贴的所有信息 这包括从 SQL Server Reporting Services (SSRS) 创建的磁贴。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/3/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 76b8eaff949ee56d57511eabea913363e6cdc3f6
ms.sourcegitcommit: 1e4fee6d1f4b7803ea285eb879c8d5a4f7ea8b85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "51717392"
---
# <a name="dashboard-tiles-in-power-bi"></a>Power BI 中的仪表板磁贴
仪表板和仪表板磁贴是 Power BI 服务的一项功能，而不是 Power BI Desktop 的功能。 虽然无法在 Power BI 移动设备中创建或固定仪表板磁贴，但可以[查看和共享](mobile-tiles-in-the-mobile-apps.md)这些磁贴。 在 Power BI 移动设备中，可以[使用 iPhone 应用将照片添加到仪表板](mobile-iphone-app-get-started.md)。

## <a name="dashboard-tiles"></a>在推入数据时
![Power BI 仪表板](media/service-dashboard-tiles/power-bi-dashboard.png)

磁贴就是固定到仪表板的数据快照。 磁贴可以从报表、数据集、仪表板、问答框、Excel 和 SQL Server Reporting Services (SSRS) 等中创建。  此屏幕截图显示了固定到仪表板的许多不同的磁贴。

除了固定，还可使用[添加磁贴](service-dashboard-add-widget.md)直接在仪表板上创建独立磁贴。 独立磁贴包含：文本框、图像、视频、流数据和 Web 内容。

是否需要了解构成 Power BI 的构建块的帮助？  请参阅 [Power BI - 基本概念](service-basic-concepts.md)。

> [!NOTE]
> 如果原始可视化效果用于创建磁贴更改，则磁贴不会更改。  例如，如果从报表固定一个折线图，然后将折线图更改为条形图，则仪表板磁贴将继续显示为折线图。 数据将会刷新，但可视化效果类型不会。
> 
> 

## <a name="pin-a-tile-from"></a>固定磁贴，从...
向仪表板添加（固定）磁贴有多种不同的方法。 可从以下位置固定磁贴：

* [Power BI 问答](service-dashboard-pin-tile-from-q-and-a.md)
* [报表](service-dashboard-pin-tile-from-report.md)
* [其他仪表板](service-pin-tile-to-another-dashboard.md)
* [OneDrive for Business 上的 Excel 工作簿](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher for Excel](publisher-for-excel.md)
* [快速见解](service-insights.md)
* [SSRS](https://msdn.microsoft.com/library/mt604784.aspx)

还可以直接在仪表板上使用“[添加磁贴](service-dashboard-add-widget.md)”创建图像、文本框、视频、流数据和 Web 内容的独立磁贴。

  ![添加磁贴图标](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interacting-with-tiles-on-a-dashboard"></a>与仪表板上的磁贴进行交互
### <a name="move-and-resize-a-tile"></a>移动和重设磁贴大小
获取一个磁贴并[将它在仪表板上移动](service-dashboard-edit-tile.md)。 将鼠标悬停在该图柄 ![图柄](media/service-dashboard-tiles/resize-handle.jpg)，并选择它重设磁贴大小。

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>将鼠标悬停在磁贴上以更改外观和行为
1. 将鼠标悬停在磁贴上以显示省略号。
   
    ![磁贴省略号](media/service-dashboard-tiles/ellipses_new.png)
2. 选择省略号以打开磁贴操作菜单。
   
    ![省略号图标](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    此处你可以：
   
   * [打开用于创建此磁贴的报表](service-reports.md) ![报表图标](media/service-dashboard-tiles/chart-icon.jpg)  
   
   * [打开用于创建此磁贴的工作表](service-reports.md) ![工作表图标](media/service-dashboard-tiles/power-bi-open-worksheet.png)  
     
    * [在焦点模式下查看](service-focus-mode.md) ![焦点图标](media/service-dashboard-tiles/fullscreen-icon.jpg)  
     * [导出磁贴中使用的数据](visuals/power-bi-visualization-export-data.md) ![导出数据图标](media/service-dashboard-tiles/export-icon.png)
     * [编辑标题和副标题、添加超链接](service-dashboard-edit-tile.md) ![编辑图标](media/service-dashboard-tiles/pencil-icon.jpg)
     * [运行见解](service-insights.md) ![见解图标](media/service-dashboard-tiles/power-bi-insights.png)
     * [将磁贴固定到另一个仪表板](service-pin-tile-to-another-dashboard.md) 
       ![固定图标](media/service-dashboard-tiles/pin-icon.jpg)
     * [删除图标](service-dashboard-edit-tile.md)
     ![删除图标](media/service-dashboard-tiles/trash-icon.png)
3. 若要关闭操作菜单，请在画布中选择空白区域。

### <a name="select-click-a-tile"></a>选择（单击）磁贴
选择磁贴时，下一步会发生什么情况取决于创建该磁贴的方式以及其是否有[自定义链接](service-dashboard-edit-tile.md)。 如果它有自定义链接，则选择该磁贴将转到该链接。 否则，选择磁贴将转到报表、Excel 联机工作簿、本地 SSRS 报表或用于创建该磁贴的问答问题。

> [!NOTE]
> 这对在仪表板上直接使用“**添加磁贴**”创建的视频磁贴不适用。 选择视频磁贴（以这种方式创建的）将导致视频直接在仪表板上播放。   
> 
> 

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
* 如果未保存用于创建可视化效果的报表，则选择磁贴将不会产生任何操作。
* 如果该磁贴从 Excel Online 中的工作簿创建，并且你甚至不具有此工作薄的读取权限，则选择该磁贴将不会在 Excel Online 中打开工作簿。
* 对于使用**添加磁贴**直接在仪表板上创建的磁贴，如果已经设置了自定义超链接，则选择标题、副标题或磁贴都将打开该 URL。  或者，默认情况下，选择直接在仪表板上创建的磁贴的图像、Web 代码或文本框都不会产生任何操作。
* 如果没有 SSRS 内的报表的权限，选择从 SSRS 创建的磁贴将出现一个页面，指示你没有访问权限 (rsAccessDenied)。
* 如果你没有 SSRS 服务器所在网络的访问权限，选择从 SSRS 创建的磁贴将出现一个页面，指示找不到服务器 (HTTP 404)。 你的设备需要具有对报表服务器的网络访问权限才能查看该报表。
* 如果原始可视化效果用于创建磁贴更改，则磁贴不会更改。  例如，如果从报表固定一个折线图，然后将折线图更改为条形图，则仪表板磁贴将继续显示为折线图。 数据将会刷新，但可视化效果类型不会。

## <a name="next-steps"></a>后续步骤
[为仪表板创建卡片（大数字磁贴）](power-bi-visualization-card.md)

[Power BI 中的仪表板](service-dashboards.md)  

[数据刷新](refresh-data.md)

[Power BI - 基本概念](service-basic-concepts.md)

[将磁贴导出到 Power Point](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)

[将 Reporting Services 项目固定到 Power BI 仪表板](https://msdn.microsoft.com/library/mt604784.aspx)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


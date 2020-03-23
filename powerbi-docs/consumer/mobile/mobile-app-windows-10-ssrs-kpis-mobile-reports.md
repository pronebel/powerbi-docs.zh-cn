---
title: 在 Power BI Windows 应用中查看本地报表和 KPI
description: 适用于 Windows 10 的 Power BI 移动应用提供对重要的本地业务信息的实时、可触控的移动访问。
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/09/2020
ms.author: painbar
ms.openlocfilehash: 67daafc0938216b135b31d3190c191402e9a10de
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79435366"
---
# <a name="view-on-premises-reports-and-kpis-in-the-power-bi-windows-app"></a>在 Power BI Windows 应用中查看本地报表和 KPI
使用适用于 Windows 10 的 Power BI 应用，可以通过触控实时移动访问 SQL Server 2016 Reporting Services 中的重要本地业务信息。 

![Reporting Services 移动报表](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>要做的第一件事
可以使用 SQL Server 2016 企业版移动报表发布服务器[生成 Reporting Services 移动报表](https://msdn.microsoft.com/library/mt652547.aspx)，然后将其发布到 [Reporting Services Web 门户](https://msdn.microsoft.com/library/mt637133.aspx)。 直接在 Web 门户中创建 KPI。 将其按文件夹进行整理并标记出你的收藏夹，以便轻松地找到它们。 

然后，在适用于 Windows 10 的 Power BI 应用中，查看已按文件夹整理或收集为收藏项的 KPS、移动报表和 Power BI 报表。 

> [!NOTE]
> 设备需要运行 Windows 10。 该应用在至少具有 1 GB RAM 和 8 GB 内部存储的设备上运行最佳。

>[!NOTE]
>我们将于 2021 年 3 月 16 日终止对使用 Windows 10 移动版的手机提供 Power BI 移动应用支持  。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>在没有 SQL Server 2016 Reporting Services 服务器的情况下浏览示例
即使你没有对 Reporting Services Web 门户的访问权限，仍可以浏览 Reporting Services 移动报表的功能。

1. 在 Windows 10 设备上打开 Power BI 应用。
2. 点击左上角的 ![全局导航按钮](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) 全局导航按钮。
3. 点击“设置”  图标 ![设置图标](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)，右键单击或点击并按住“连接到服务器”  ，再点击“查看示例”  。
   
   ![查看 SSRS 示例](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. 打开零售报表或销售报表文件夹，浏览 KPI 和移动报表。
   
   ![示例 KPI 和移动报表](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

浏览示例以与 KPI 和移动报表进行交互。

## <a name="connect-to-a-reporting-services-report-server"></a>连接到 Reporting Services 报表服务器
1. 在导航窗格底部，点击“设置”![“设置”图标](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) 
2. 点击“连接到服务器”  。
3. 填写服务器地址以及用户名和密码。 对服务器地址使用如下格式：
   
     `https://<servername>/reports` 或 `https://<servername>/reports`
   
   > [!NOTE]
   > 连接字符串的开头包括 http  或 https  。
   > 
   > 
   
    如果需要，点击“高级选项”  以指定服务器名称。
4. 点击复选标记进行连接。 
   
   现在会在导航窗格中看到服务器。
   
   ![导航窗格中的服务器](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >随时点击全局导航按钮 ![全局导航按钮](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png)，在 Power BI 服务中的 Reporting Services 移动报表和仪表板之间切换。 
   > 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>在 Power BI 应用中查看 Reporting Services KPI 和移动报表
Reporting Services KPI、移动报表和 Power BI 报表（预览版）显示在 Reporting Services Web 门户上的相同文件夹中。

![报表文件夹](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* 点击 KPI 以在焦点模式中看到它。
  
    ![焦点模式下的 KPI](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* 点击移动报表以在 Power BI 应用中打开并与其交互。
  
    ![Reporting Services 移动报表](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>查看你收藏的 KPI 和报表
可以在 Reporting Services Web 门户中将 KPI、移动报表和 Power BI 报表标记为收藏项，然后可以在 Windows 10 设备上的一个方便文件夹中查看它们，以及 Power BI 收藏的仪表板和报表。

* 点击**收藏夹**。
  
   ![“收藏夹”图标](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   你在 Web 门户上的收藏项都在此页上。
  
阅读有关 [Power BI 移动应用中的收藏夹](mobile-apps-favorites.md) 的更多信息。

## <a name="remove-a-connection-to-a-report-server"></a>删除与报表服务器的连接
在 Power BI 移动应用中一次只能连接到一个报表服务器。 如果想要连接到不同的服务器，需要断开与当前服务器的连接。

1. 在导航窗格底部，点击“设置”![“设置”图标](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)  。
2. 点击并按住不想连接到的服务器的名称。
3. 点击“删除服务器”  。
   
    ![删除服务器](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>创建 Reporting Services 移动报表和 KPI
不是在 Power BI 移动应用中创建 Reporting Services KPI 和移动报表。 而是在 SQL Server 移动报表发布服务器和 SQL Server 2016 Reporting Services Web 门户中创建它们。

* [创建自己的 Reporting Services 移动报表](https://msdn.microsoft.com/library/mt652547.aspx)并将其发布到 Reporting Services Web 门户。
* [在 Reporting Services Web 门户上创建 KPI](https://msdn.microsoft.com/library/mt683632.aspx)

## <a name="next-steps"></a>后续步骤
* [适用于 Windows 10 的 Power BI 移动应用入门](mobile-windows-10-phone-app-get-started.md)  
* [什么是 Power BI？](../../fundamentals/power-bi-overview.md)  
* 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)


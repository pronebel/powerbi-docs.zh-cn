---
title: 在 Power BI 移动应用中浏览报表
description: 了解如何在手机或平板电脑上查看 Power BI 移动应用中的报表，并与之交互。 可以在 Power BI 服务或 Power BI Desktop 中创建报表，然后在移动应用中与报表进行交互。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 08/17/2018
ms.author: maggies
ms.openlocfilehash: 694ae2cd6f77fbcf898a984b135fb65b9163a43b
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180981"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>在 Power BI 移动应用中浏览报表
适用于：

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Android 手机](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Android 平板电脑](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Windows 10 设备](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android 手机 |Android 平板电脑 |Windows 10 设备 |

Power BI 报表是交互式数据视图，使用视觉对象来表示不同的数据发现和见解。 在 Power BI 移动应用中查看报表是三步流程中的第三步。

1. [在 Power BI Desktop 中创建报表](../../desktop-report-view.md)。 甚至可以在 Power BI Desktop 中[优化报表，使之更适合在手机中显示](mobile-apps-view-phone-report.md)。 
2. 将这些报表发布到 Power BI 服务 [(https://powerbi.com)](https://powerbi.com) 或 [Power BI 报表服务器](../../report-server/get-started.md)。  
3. 然后，与 Power BI 移动应用中的报表进行交互。

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>在移动应用中打开 Power BI 报表
Power BI 报表存储在移动应用中的不同位置，具体取决于从何处获取。 可以位于“应用”、“与我共享”、“工作区”（包括“我的工作区”）或报表服务器中。 有时，可以通过相关仪表板转到报表；有时，其中也会列出报表。

* 在仪表板中，依次点击磁贴右上角的省略号 (...) 和“打开报表”。
  
  ![打开报表](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  并非所有磁贴都包含报表打开选项。 例如，通过在问答框中提问而创建的磁贴就无法在获得点击后打开报表。 
  
  在手机上，报表将在横向模式下打开，除非[经过优化，更适合在手机上查看](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones)。
  
  ![横向模式下的手机报表](./media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>查看针对手机优化后的报表
Power BI 报表作者可以创建专门针对手机进行优化的报表布局。 更适合在手机上展示的报表页新增了功能：例如，可以对视觉对象执行向下钻取和排序操作，并能访问[报表作者在报表页中添加的筛选器](mobile-apps-view-phone-report.md#filter-the-report-page-on-a-phone)。 在手机上打开的报表已筛选出网页版报表中筛选的值，并通过消息提示报表页上有活动筛选器。 可以在手机上更改筛选器。

在报表列表中，优化后的报表具有特殊图标 ![手机报表图标](./media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png)：

![打开手机报表](./media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

在手机上查看此类报表时，将在纵向视图中打开。

![纵向视图下的报表](./media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

 报表可能混合了针对或未针对手机进行优化的报表页。 如果是这样，浏览报表时，每个报表页的视图都会从纵向模式切换为横向模式。

阅读有关[针对手机视图进行优化的报表](mobile-apps-view-phone-report.md)的详细信息。

## <a name="use-slicers-to-filter-a-report"></a>使用切片器筛选报表
在 Power BI Desktop 或 Power BI 服务中设计报表时，请考虑[将切片器添加到报表页](../../visuals/power-bi-visualization-slicers.md)。 你和同事可以使用切片器在浏览器和移动应用中筛选页面。 在手机上查看报表时，可以在横向模式下和在针对手机的纵向模式进行了优化的页面中查看切片器并与之交互。 如果选择切片器中的值或在浏览器中进行筛选，那么在移动应用中查看报表页时，将会发现已选择相应值。 还会通过消息提示报表页上有活动筛选器。  

* 在报表页上的切片器中选择值后，便会筛选报表页上的其他视觉对象。
  
  ![报表切片器](./media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  在此插图中，切片器将在列图表中筛选出 7 月的值。

## <a name="cross-filter-and-highlight-a-report"></a>交叉筛选并突出显示报表
在视觉对象中选择值后，便不会筛选其他视觉对象。 而是会突出显示其他视觉对象中的相关值。

* 点击视觉对象中的值。
  
  ![交叉筛选页面](./media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  点击一个视觉对象中的大型列将突出显示其他视觉对象中的相关值。 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>在 iPad 或平板电脑上对视觉对象进行排序
* 点击图表，点击省略号 (**...**)，然后点击字段名。
  
   ![对视觉对象排序](./media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* 若要反向排序，请依次重新点击省略号 (...) 和相同的字段名称。

## <a name="drill-down-and-up-in-a-visual"></a>在视觉对象中向下钻取和向上钻取
如果报表作者已将向下钻取功能添加到视觉对象，则可以向下钻取视觉对象，查看其中所包含的值。 在 Power BI Desktop 或 Power BI 服务中[向视觉对象添加向下钻取功能](../end-user-drill.md)。 

* 点击并按住视觉对象中的特定栏或点以显示其工具提示。 如果它具有向下钻取功能，则工具提示底部具有可点击的箭头。 
  
  ![在视觉对象中向下钻取](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-tooltip.png)

* 要向上钻取，请点击工具提示中的向上箭头。
  
  ![向上钻取](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-tooltip.png)

* 还可在视觉对象中向下钻取所有数据点。 在焦点模式下打开数据点，点击“浏览”图标，然后选择显示所有下一级别，或将其展开以显示当前级别和下一级别。

   ![Power BI 向下钻取所有内容](./media/mobile-reports-in-the-mobile-apps/power-bi-drill-down-all.png)

## <a name="drill-through-from-one-page-to-another"></a>从某一页钻取到另一页

通过钻取，Power BI 会在你点击视觉对象的特定部分时，转到报表中的另一页，筛选出点击的值。 报表作者可定义一个或多个钻取操作，每个操作分别转到不同页面。 在这种情况下，可选择所需的钻取操作。 在以下示例中，点击仪表中的值时，可选择钻取“各业务领域的开销”或“各业务领域的计划”。

![Power BI 移动版钻取报表](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-through-it-spent-report.png)

钻取时，使用返回按钮即可返回到之前的报表页。

了解如何[在 Power BI Desktop 中添加钻取](../../desktop-drillthrough.md)。

## <a name="show-data-and-copy-values"></a>显示数据和复制值

通过选择手机报表中的可视化效果右上角的菜单选项省略号 (...)，然后选择“显示数据”，可以查看基础可视化效果数据。

![Power BI 移动版显示数据菜单选项](./media/mobile-reports-in-the-mobile-apps/copy-data-visual.png)

长时间点击显示的表中的单元格将会弹出本机选择和复制菜单，因此你将能够从表（或整个表）中选择复制数据。

![Power BI 移动版钻取报表](./media/mobile-reports-in-the-mobile-apps/copy-data-table.png)

## <a name="next-steps"></a>后续步骤
* [查看手机优化版 Power BI 报表并与之交互](mobile-apps-view-phone-report.md)
* [创建手机优化版报表](../../desktop-create-phone-report.md)
* 是否有任何问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)


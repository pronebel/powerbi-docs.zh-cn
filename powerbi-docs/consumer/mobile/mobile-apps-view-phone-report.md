---
title: 查看针对你的手机进行优化的 Power BI 报表
description: 阅读有关与经过优化，以便在 Power BI 手机应用中查看的报表页交互的信息。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 1db56c2844d217bf6bff633609893e5a97a6dae5
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114886"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>查看针对你的手机进行优化的 Power BI 报表

适用于：

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android 手机](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone |Android 手机 |

在自己的手机上查看 Power BI 报表时，Power BI 自动检测报表是否已针对手机进行优化。 如果是，Power BI 会自动以纵向视图打开优化后的报表。

![纵向模式的报表](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

如果没有更适合手机的报表，报表仍会打开，但是以非优化的横向视图显示。 即使是更适合在手机上查看的报表，如果翻转手机，报表也会按照原始报表布局，在未优化的视图中打开。 如果只优化了某些页，则你将在纵向视图中看到消息，指示该报表提供横向视图。

![报表页未优化](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Power BI 报表的所有其他功能对更适合在手机上查看的报表仍有效。 阅读可在以下机型中执行的操作的详细信息：

* [iPhone 上的报表](mobile-reports-in-the-mobile-apps.md)。 
* [Android 手机上的报表](mobile-reports-in-the-mobile-apps.md)。

## <a name="filter-the-report-page-on-a-phone"></a>筛选手机上的报表页
如果针对手机优化的报表已定义筛选器，则在手机上查看报表时可以使用这些筛选器。 在手机上打开的报表已筛选出网页版报表中筛选的值。 还会通过消息提示报表页上有活动筛选器。 可以在手机上更改筛选器。

1. 点击筛选器图标 ![页面底部的](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) 手机筛选器图标。 
2. 使用基本筛选或高级筛选查看你感兴趣的结果。
   
    ![Power BI 手机报表高级筛选器](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>交叉突出显示视觉对象
纵向视图中交叉突出显示视觉对象的工作方式与 Power BI 服务中的视觉对象相同，并且在横向视图下的手机中也是如此：在一个视觉对象中选择数据时，它会突出显示该页面上其他视觉对象中的相关数据。

阅读有关 [Power BI 中的筛选和突出显示](../../power-bi-reports-filters-and-highlighting.md)的详细信息。

## <a name="select-visuals"></a>选择视觉对象
在手机报表中选择视觉对象时，手机报表突出显示并专注于该视觉对象，以抵消画布笔势。

利用所选的视觉对象，可执行诸如在该视觉对象中滚动的操作。 要取消选择视觉对象，触摸视觉对象区域之外的任意位置即可。

## <a name="open-visuals-in-focus-mode"></a>在焦点模式下打开视觉对象
手机报表还提供焦点模式：可以更深入地查看单个视觉对象并更轻松地浏览它。

* 在手机报表中，点击视觉对象右上角的省略号 ( **...** ) >“**扩展至焦点模式**”。
  
    ![展开为焦点模式](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

在焦点模式下所执行的操作将传递到报表画布，反之亦然。 例如，如果突出显示视觉对象中的一个值，然后返回到整个报表，则该报表将筛选出你在视觉对象中突出显示的值。

由于屏幕大小的限制，一些操作仅在焦点模式下可用：

* **向下钻取**视觉对象中显示的信息。 阅读以下有关手机报表中[向下钻取和向上钻取](mobile-apps-view-phone-report.md#drill-down-in-a-visual)的详细信息。
* 对视觉对象中的值进行**排序**。
*  还原：清除针对视觉对象所采取的浏览步骤，并还原为报表创建时的定义集。
  
    若要清除视觉对象中的所有浏览，请点击省略号 ( **...** ) >“**还原**”。
  
    ![还原](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    可在报表级别或在视觉对象级别进行还原，前者将从所有视觉对象清除浏览，后者将从所选视觉对象清除浏览。   

## <a name="drill-down-in-a-visual"></a>在视觉对象中向下钻取
如果在视觉对象中定义了层次结构级别，则可以向下钻取视觉对象中显示的详细信息，然后备份。 在 Power BI 服务或 Power BI Desktop 中，[向视觉对象添加向下钻取功能](../end-user-drill.md)。

有几种类型的向下钻取功能：

### <a name="drill-down-on-a-value"></a>向下钻取值
1. 长按（点击并按住）视觉对象中的数据。
2. 将显示工具提示，如果定义了层次结构，则工具提示页脚将显示向下钻取功能和向上键。
3. 点击向下键以便向下钻取

    ![点击向下钻取](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. 点击向上键以便向上钻取。

### <a name="drill-to-next-level"></a>钻取到下一个级别
1. 在手机报表中，点击右上角的省略号 ( **...** ) >“**扩展至焦点模式**”。
   
    ![展开为焦点模式](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    在本示例中，柱线显示状态的值。
2. 点击左下角的“浏览”图标 ![“浏览”图标](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) （位于左下角）。
   
    ![浏览模式](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. 点击“**显示下一个级别**”或“**扩展至下一级别**”。
   
    ![扩展至下一级别](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    现在，柱线显示城市的值。
   
    ![扩展的级别](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. 如果点击左上角的箭头，则返回到值仍扩展至较低级别的手机报表。
   
    ![仍扩展至更低级别](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. 若要向上返回到原始级别，请再次点击省略号 ( **...** ) >“**还原**”。
   
    ![还原](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>从值中钻取
钻取将一个报表页中的值与其他报表页连接起来。 从数据点钻取到其他报表页时，数据点值用于筛选钻取页，或它将位于所选数据的上下文中。
报表作者可以在创建报表时[定义钻取](https://docs.microsoft.com/power-bi/desktop-drillthrough)。

1. 长按（点击并按住）视觉对象中的数据。
2. 将显示工具提示，如果定义了钻取，则工具提示页脚将显示钻取箭头。
3. 点击箭头以便进行钻取

    ![点击钻取](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. 选择要钻取的报表页

    ![选择报表页](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. 使用应用标头中的“返回”按钮，以返回到开始的页面。


## <a name="next-steps"></a>后续步骤
* [创建针对 Power BI 手机应用的优化报表](../../desktop-create-phone-report.md)
* [在 Power BI 中创建仪表板电话视图](../../service-create-dashboard-mobile-phone-view.md)
* [创建优化为适应任意大小的响应式视觉对象](../../visuals/desktop-create-responsive-visuals.md)
* 更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


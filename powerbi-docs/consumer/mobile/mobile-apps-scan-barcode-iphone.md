---
title: 使用 iPhone 上的 Power BI 移动应用扫描条形码
description: 扫描现实生活中的条形码，直接转到在 Power BI 移动应用中筛选后的 BI 信息。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: mshenhav
ms.openlocfilehash: 3fd2d4888f76490a01c0742e68e6820c7055326e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61137190"
---
# <a name="scan-a-barcode-with-your-iphone-from-the-power-bi-mobile-app"></a>使用 iPhone 上的 Power BI 移动应用扫描条形码
扫描现实生活中的条形码，直接转到在 Power BI 移动应用中筛选后的 BI 信息。

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

假设有一个同事已[标记 Power BI Desktop 报表中的条形码字段](../../desktop-mobile-barcodes.md)并与你共享该报表。 

当你使用 iPhone 上的 Power BI 应用中的扫描器扫描产品条形码时，可以看到具有该条形码的报表（或报表列表）。 你可以在 iPhone 上打开筛选为该条形码的报表。

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>使用 Power BI 扫描器扫描条形码
1. 在 Power BI 移动应用中打开左上方的主导航菜单 ![](media/mobile-apps-scan-barcode-iphone/pbi_iph_navmenu.png)。 
2. 向下滚动到“扫描程序”  并选择它。 
   
    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)
3. 如果未启用照相机，你需要许可 Power BI 应用使用照相机。 此许可为一次性的。 
4. 将扫描器指向产品上的条形码。 
   
    你将看到与该条形码相关联的报表列表。
5. 点击报表名称以在你的 iPhone 上打开自动为该条形码筛选的报表。

## <a name="filter-by-other-barcodes-while-in-a-report"></a>在报表中由其他条形码筛选
在 iPhone 上查看通过条形码筛选的报表时，你可能希望通过不同条形码筛选同一个报表。

* 如果条形码图标有筛选器 ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png)，筛选器将处于活动状态并且报表已通过条形码筛选。 
* 如果条码图标没有筛选器 ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png)，筛选器将不会处于活动状态并且报表未通过条形码筛选。 

无论哪种方式，点击该图标均可打开带有浮动扫描器的小菜单。

* 将扫描器对准新项目，以将报表的筛选器更改为不同的条形码值。 
* 选择“清除条形码筛选器”  以返回到未筛选的报表。
* 选择“按最近条形码筛选”  ，将报表筛选器更改为已在当前会话中扫描的一个条形码。

## <a name="issues-with-scanning-a-barcode"></a>扫描条形码时出现的问题
以下是在扫描产品上的条形码时可能会看到的一些消息。

### <a name="couldnt-filter-report"></a>“无法筛选报表...”
你选择进行筛选的报表基于的数据模型不包括此条形码值。 例如，报表不包含产品“矿泉水”。  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>报表中的所有/某些视觉对象不包含任何值
扫描的条形码值存在于你的模型中，但报表上的所有/某些视觉对象不包含此值，因此筛选将返回一个空状态。 请尝试查找其他报表页，或在 Power BI Desktop 中编辑报表，使其包含此值 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>“看起来你没有可按条形码筛选的任何报表。”
这意味着你没有任何已启用条形码的报表。 条形码扫描器只能筛选具有标记为 **条形码**的列的报表。  

请确保你或报告所有者在 Power BI Desktop 中已将某列标记为**条形码** 。 了解更多关于[在 Power BI Desktop 中标记条形码字段](../../desktop-mobile-barcodes.md)的信息

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>“无法筛选报表 - 似乎报表数据中无此条形码。”
你选择进行筛选的报表基于的数据模型不包括此条形码值。 例如，报表不包含产品“矿泉水”。 你可以扫描不同的产品，选择其他报表（如果提供了多个报表）或查看未筛选的报表。 

## <a name="next-steps"></a>后续步骤
* [在 Power BI Desktop 中标记条形码字段](../../desktop-mobile-barcodes.md)
* [Power BI 中的仪表板磁贴](../end-user-tiles.md)
* [Power BI 中的仪表板](../end-user-dashboards.md)


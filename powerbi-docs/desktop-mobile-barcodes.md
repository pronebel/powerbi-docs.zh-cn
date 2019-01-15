---
title: 在适用于移动应用的 Power BI Desktop 中标记条形码字段
description: 当你在 Power BI Desktop 的模型中标记条形码字段时，你可以在你的 iPhone 的 Power BI 应用中自动为条形码筛选数据。
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: 584947dcd92078ea025468f5a38fc7fed3e2616a
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54289891"
---
# <a name="tag-barcodes-in-power-bi-desktop-for-the-mobile-apps"></a>在适用于移动应用的 Power BI Desktop 中标记条形码
在 Power BI Desktop 中，你可以针对列进行[数据分类](desktop-data-categorization.md)，以便 Power BI Desktop 知道如何处理报表中可视化对象的值。 此外还可将列分类为**条形码**。 当你或你的同事通过 iPhone [使用 Power BI 应用扫描产品上的条形码](consumer/mobile/mobile-apps-scan-barcode-iphone.md)时，你将看到所有包含此条形码的报表。 在移动应用中打开报表时，Power BI 将自动筛选报表中与该条形码相关的数据。

1. 在 Power BI Desktop 中切换到数据视图。
2. 选择具有条形码数据的列。 请参阅以下[受支持的条形码格式](#supported-barcode-formats)列表。
3. 在“建模”选项卡上，选择“数据类别” > “条形码”。
   
    ![数据类别列表](media/desktop-mobile-barcodes/power-bi-desktop-barcode.png)
4. 在“报表”视图中，将此字段添加到要通过条形码筛选的视觉对象。
5. 保存报表并将其发布到 Power BI 服务。

现在当你打开 [iPhone 的 Power BI 应用](consumer/mobile/mobile-iphone-app-get-started.md)上的扫描器并扫描条形码时，你将在报表列表上看到此报表。 当你打开报表时，将按你扫描的产品条形码筛选报表的视觉对象。

## <a name="supported-barcode-formats"></a>受支持的条形码格式
如果你可以将以下条形码标记在 Power BI 报表中，Power BI 将可识别它们： 

* UPCECode 
* Code39Code  
* A39Mod43Code 
* EAN13Code 
* EAN8Code  
* 93Code  
* 128Code 
* PDF417Code 
* Interleaved2of5Code 
* ITF14Code 

## <a name="next-steps"></a>后续步骤
* [从你的 iPhone 上的 Power BI 应用中扫描条形码](consumer/mobile/mobile-apps-scan-barcode-iphone.md)
* [在 iPhone 上扫描条形码时遇到的问题](consumer/mobile/mobile-apps-scan-barcode-iphone.md#issues-with-scanning-a-barcode)
* [Power BI Desktop 中的数据分类](desktop-data-categorization.md)  
* 是否有任何问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)


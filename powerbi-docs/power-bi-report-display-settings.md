---
title: Power BI 报表中的页面显示设置
description: 页面显示报表的设置和页面视图设置
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 97df2d6910f0215bd01875c88ea5d81d5dcc2c7c
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66720847"
---
# <a name="page-display-settings-in-a-power-bi-report"></a>Power BI 报表中的页面显示设置
我们了解保持报表布局像素完美的重要性。 有时候这会有点困难，因为你和你的同事可能会使用纵横比和大小不同的屏幕查看这些报表。 

默认显示视图为**调整到页面大小**，而默认显示大小为 **16:9**。 如果你想要锁定不同的纵横比，或者想要用不同的方式调整报表，有两种工具可帮助你：“页面视图”设置和“页面大小”设置。


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>在哪里可以找到 Power BI 服务和 Power BI Desktop 中的页面视图设置
Power BI 服务和 Power BI Desktop 中都提供了页面视图设置，但界面稍有不同。 以下部分解释了可以在每个 Power BI 工具中的哪个位置找到视图设置。

### <a name="in-power-bi-desktop"></a>在 Power BI Desktop 中
在报表视图中，选择“视图”选项卡打开页面视图设置，以及手机布局设置。 

  ![桌面页面视图设置](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>在 Power BI 服务 (app.powerbi.com) 中
在 Power BI 服务中打开报表，然后从左上角菜单栏中选择“视图” 

![服务页面视图设置](media/power-bi-report-display-settings/power-bi-change-page-view.png)

[阅读视图和编辑视图](consumer/end-user-reading-view.md)中均提供了“页面视图”设置。 在“编辑视图”中，报表所有者可以将页面视图设置分配给个别报表页面，而这些设置会随报表一起保存。 当同事在“阅读视图”中打开该报表时，他们看到的是以所有者设置显示的报表页面。 在“阅读视图”中，同事可以更改某些页面视图设置，但退出报表时，所做的更改不会保存   。

## <a name="page-view-settings"></a>页面视图设置
第一组“页面视图”设置可以控制报表页面相对于浏览器窗口的显示。 可以选择：

* **调整到页面大小**（默认值）：将内容调整到最适合页面的程度
* **适应宽度**：将内容调整到适应页面的宽度
* **实际大小**：内容以完整大小显示

第二组“页面视图”设置控制对象在报表画布上的位置。 可以选择：

* **显示网格线**：打开网格，以帮助你在报表画布上定位对象。
* **网格线对齐**：与“显示网格线”配合使用，在报表画布上精确定位和对齐对象  。 
* **锁定对象**：锁定画布上的所有对象，以便可以移动或调整对象。
* **选择窗格**：“选择”窗格列出画布上的所有对象  。 你可以决定要显示和要隐藏的对象。

    ![选择窗格](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>“页面大小”设置
![更改“页面大小”设置](media/power-bi-report-display-settings/power-bi-page-size.png)

“页面大小”设置仅供报表所有者使用  。 在 Power BI 服务 (app.powerbi.com) 中，这意味着可在[编辑视图](consumer/end-user-reading-view.md)中打开报表。 “页面大小”设置位于“可视化效果”窗格中，并控制报表画布的显示比例和实际大小（以像素为单位）   ：   

* 4:3 比例
* 16:9 比例（默认值）
* Cortana
* Letter
* 自定义（以像素为单位的高度和宽度）

## <a name="next-steps"></a>后续步骤
[Power BI Desktop 中的报表视图](desktop-report-view.md)

[在自己的 Power BI 报表中更改“页面视图”和“页面大小”设置](consumer/end-user-report-view.md)

了解有关 [Power BI 中的报表](consumer/end-user-reports.md)的详细信息

[Power BI 服务中设计器的基本概念](service-basic-concepts.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


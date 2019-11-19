---
title: Power BI 服务中的报表
description: 面向使用者的 Power BI 服务中的报表
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/05/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 3f6f534b71ba6d8e8798418275c4758a95fc6fb5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73851227"
---
# <a name="reports-in-power-bi"></a>Power BI 中的报表

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Power BI 报表是对数据集的多角度审视，它使用视觉对象来表示数据集呈现的各种结果和见解。  报表可包含单个视觉对象，也可包含充满视觉对象的多个页面。 根据你的职位，你可能是报表设计人员  ， 也可能是报表使用人员  。 本文适用于使用者  。

![报表页的屏幕截图。](./media/end-user-reports/power-bi-report.png)

A. 此报表有 6 个页面（或标签页），你当前正在查看“情绪”页  。    
B. 此页面上有 5 个不同的视觉对象和 1 个页标题。    
C. “筛选器”窗格显示了一个应用于所有报表页的筛选器  。 要折叠“筛选器”窗格，请选择箭头 ( **>** )。    
D. Power BI 横幅显示了报表的名称和上次更新日期。 选择箭头以打开一个菜单，该菜单还显示了报表所有者的名称。    
E. 操作栏包含可对此报表执行的操作。  例如，可以添加注释、查看书签或导出报表中的数据。  选择“更多选项”(…) 以显示其他报表功能的列表  。    

如果你不熟悉 Power BI，可阅读[面向 Power BI 服务使用者的基本概念](end-user-basic-concepts.md)来详细了解基础知识。 可在移动设备上查看、共享和批注报表。 有关详细信息，请参阅[在 Power BI 移动应用中浏览报表](mobile/mobile-reports-in-the-mobile-apps.md)。

## <a name="advantages-of-reports"></a>报表的优点

Power BI 基于单个数据集的生成报表。 报表设计者在报表中创建表示信息块的视觉对象  。 视觉对象不是静态的。  它们随着基础数据的变化而更新。 你可在深入探究数据来发现见解和寻求答案时，与视觉对象和筛选器进行交互。 与仪表板一样，报表的交互性和可自定义性非常高。

### <a name="safely-interact-with-content"></a>安全地与内容交互

在你探索内容并与之交互时（例如筛选、切片、订阅和导出时），不能中断报表。 基础数据集或原始共享内容不受你的工作影响。 这适用于仪表板、报表和应用。

> [!NOTE]
> 请记住，不能损坏数据。 Power BI 是一个探索和试验的好位置，不用担心会损坏任何内容。

### <a name="save-your-changes-or-revert-to-the-default-settings"></a>保存更改或还原为默认设置

这并不意味着无法保存更改。 可进行保存，但这些更改仅影响内容视图。 要还原到报表的原始默认视图，请选择“重置为默认值”  。

![“还原为默认值”图标的屏幕截图。](./media/end-user-reports/power-bi-reset.png)

## <a name="dashboards-versus-reports"></a>仪表板与报表

[仪表板](end-user-dashboards.md)经常与报表混淆，因为它们也是填充了视觉对象的画布。 但它们存在一些主要差异。  

| **功能** | **仪表板** | **报表** |
| --- | --- | --- |
| 页面 |一个页面 |一个或多个页面 |
| 数据源 |每个仪表板的一个或多个报表和一个或多个数据集 |每个报表的单个数据集 |
| 筛选 |无法筛选或切片 |许多不同的方式来筛选、突出显示和切片 |
| 设置警报 |当仪表板满足某些条件时，可创建警报以向你发送电子邮件 |否 |
| 功能 |可将一个仪表板设置为精选仪表板 |无法创建精选报表 |
| 可以看到基础数据集表和字段 |否。 可导出数据，但看不到仪表板本身的数据集表和字段 |是。 可查看有权查看的数据集表、字段和值 |
| 自定义 |否  |可筛选、导出、查看相关内容，也可添加书签、生成 QR 码和在 Excel 中分析等等 |

<!--| Available in Power BI Desktop |No |Yes, can create and view reports in Desktop |
| Pinning |Can pin existing visuals (tiles) only from current dashboard to your other dashboards |Can pin visuals (as tiles) to any of your dashboards. Can pin entire report pages to any of your dashboards. | -->

## <a name="report-designers-and-report-consumers"></a>报表设计者和报表使用者

根据你的角色，你可能是设计者，负责创建报表供自己使用或与同事共享  。 你想了解如何创建和共享报表。

你也可能是使用者，从其他人那里接收报表  。 你想要了解如何理解报表并与之交互。 如果你是报表使用者，则以下链接适合你  ：

* 首先查看 [Power BI 服务教程](end-user-basic-concepts.md)，了解在何处查找报表和报表工具。
* 了解如何[打开报表](end-user-report-open.md)以及[使用者可用的所有交互](end-user-reading-view.md)。
* 通过查看我们的任一[示例](../sample-tutorial-connect-to-the-samples.md)轻松了解报表的使用。  
* 要查看报表正在使用哪个数据集及哪个仪表板显示来自报表的视觉对象（固定）  ，请参阅[在 Power BI 服务中查看相关内容](end-user-related.md)。

> [!TIP]
> 如果未在此处找到你所查找的内容，请按照左侧的目录浏览所有的报表文章  。

## <a name="next-steps"></a>后续步骤

[打开并查看报表](end-user-report-open.md)    
[Power BI 服务中的仪表板](end-user-dashboards.md)
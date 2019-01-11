---
title: 与同事共享筛选的 Power BI 报表
description: 了解如何筛选 Power BI 报表并与组织中的同事共享。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d5e05775d310af37b2c96c6e9e255de25fe5effe
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983430"
---
# <a name="share-a-filtered-power-bi-report-with-your-coworkers"></a>与同事共享筛选的 Power BI 报表
共享是一种使多人能够访问你的仪表板和报表的有效方式。 Power BI 还提供了[其他多种开展协作和分发报表的方式](service-how-to-collaborate-distribute-dashboards-reports.md)。

要进行共享，你和收件人都需要一个 [Power BI Pro 许可证](service-features-license-type.md)，或者内容需要位于[高级容量](service-premium.md)中。 

可以在同一电子邮件域中与同事共享报表（与在 Power BI 服务中的大多数位置一样）：收藏夹、最近浏览、与我共享（如果所有者允许该操作）、我的工作区或其他工作区。 共享报表时，与你共享的同事可查看该报表并与其交互，但不能编辑该报表。 除非应用[行级别安全性 (RLS)](service-admin-rls.md)，否则他们会看到你在报表中看到的相同数据。 

如果你想要共享筛选的报表版本，该怎么办？ 也许一个报表仅显示特定城市或销售人员或年份的数据。 请尝试创建自定义 URL。 收件人第一次打开报表时，将对其进行筛选。 他们可以通过修改 URL 来删除筛选器。

## <a name="filter-and-share-a-report"></a>筛选和共享报表

1. 打开[编辑视图](consumer/end-user-reading-view.md)中的报表、应用筛选器并保存报表。
   
   在此示例中，我们将筛选[零售分析示例](sample-tutorial-connect-to-the-samples.md)，以仅显示“区域”等于“NC”的值。
   
   ![报表筛选窗格](media/service-share-reports/power-bi-filter-report2.png)
2. 将以下代码添加到以下报表页 URL 的末尾：
   
   ?filter=*tablename*/*fieldname* eq *value*
   
    此字段必须是“字符串”类型。 “Tablename”或“fieldname”值不能包含空格。
   
   在本示例中，表的名称是 **Store**，字段的名称是 **Territory**，我们要筛选的依据值是 **NC**：
   
    ?filter=Store/Territory eq 'NC'
   
   ![已筛选的报表 URL](media/service-share-reports/power-bi-filter-url3.png)
   
   浏览器会添加特殊字符来表示斜杠、空格和撇号，因此最终会看到：
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

3. [共享报表](service-share-dashboards.md)，但清除“向收件人发送电子邮件通知”复选框。 

    ![共享报表对话框](media/service-share-reports/power-bi-share-report-dialog.png)

4. 使用前面创建的筛选器发送链接。

## <a name="next-steps"></a>后续步骤
* 想提供反馈？ 请转到 [Power BI 社区站点](https://community.powerbi.com/)提出你的建议。
* [应如何针对仪表板及报表开展协作并进行共享？](service-how-to-collaborate-distribute-dashboards-reports.md)
* [共享仪表板](service-share-dashboards.md)
* 更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)。


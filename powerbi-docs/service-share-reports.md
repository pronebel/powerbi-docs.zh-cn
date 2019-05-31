---
title: 筛选报表并将其与同事的 Power BI 中共享
description: 了解如何筛选 Power BI 报表并与组织中的同事共享。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770684"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>筛选的 Power BI 报表并与同事共享
共享  是一种使多人能够访问你的仪表板和报表的有效方式。 如果你想要共享筛选的报表版本，该怎么办？ 也许一个报表仅显示特定城市或销售人员或年份的数据。 请尝试筛选报表和共享，或创建自定义 URL。 收件人第一次打开报表时，将对其进行筛选。 他们可以通过修改 URL 来删除筛选器。 

Power BI 还提供了[其他多种开展协作和分发报表的方式](service-how-to-collaborate-distribute-dashboards-reports.md)。 要进行共享，你和收件人都需要一个 [Power BI Pro 许可证](service-features-license-type.md)，或者内容需要位于[高级容量](service-premium-what-is.md)中。 

## <a name="two-ways-to-filter-a-report"></a>两种方法来筛选报表

### <a name="set-a-filter"></a>设置筛选器

打开[编辑视图](consumer/end-user-reading-view.md)中的报表、应用筛选器并保存报表。
   
在此示例中，我们将筛选[零售分析示例](sample-tutorial-connect-to-the-samples.md)，以仅显示“区域”等于“NC”的值   。
   
![报表筛选窗格](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>在 URL 中创建一个筛选器

将以下代码添加到以下报表页 URL 的末尾：
   
?filter=*tablename*/*fieldname* eq *value*
   
此字段必须是类型的数字、 日期时间或字符串。 “Tablename”或“fieldname”值不能包含空格   。
   
在本示例中，表的名称是 **Store**，字段的名称是 **Territory**，我们要筛选的依据值是 **NC**：
   
?filter=Store/Territory eq 'NC'
   
![已筛选的报表 URL](media/service-share-reports/power-bi-filter-url3.png)
   
浏览器会添加特殊字符来表示斜杠、空格和撇号，因此最终会看到：
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

请参阅文章[筛选报表的 URL 中使用查询字符串参数](service-url-filters.md)的更多详细信息。

## <a name="share-the-filtered-report"></a>共享筛选的报表

1. 当您[共享报表](service-share-dashboards.md)，清除**发送给收件人的电子邮件通知**复选框。

    ![共享报表对话框](media/service-share-reports/power-bi-share-report-dialog.png)

4. 使用前面创建的筛选器发送链接。

## <a name="next-steps"></a>后续步骤
* 想提供反馈？ 请转到 [Power BI 社区站点](https://community.powerbi.com/)提出你的建议。
* [应如何针对仪表板及报表开展协作并进行共享？](service-how-to-collaborate-distribute-dashboards-reports.md)
* [共享仪表板](service-share-dashboards.md)
* 更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)。


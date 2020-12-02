---
title: Power BI 的刷新摘要
description: 了解如何使用 Power BI 中的刷新摘要
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/27/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: 285bc76ddb0a0afa571fba06096358c22781a121
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410772"
---
# <a name="refresh-summaries-for-power-bi"></a>Power BI 的刷新摘要

Power BI 管理门户中的 Power BI“刷新摘要”页提供对刷新计划、容量和潜在的刷新计划重叠的控制和见解。 可使用“刷新摘要”页确定是否应调整刷新计划，了解与刷新问题相关的错误代码以及正确管理数据刷新计划。 

“刷新摘要”页包含两种视图：

* **历史记录**- 显示你作为管理员的 Power BI Premium 容量的刷新摘要历史记录。

* **计划**- 显示计划刷新的计划视图，该视图还可发现超额订阅的时间段问题。

你还可将有关刷新事件的信息导出到 .CSV 文件，该文件可提供有关刷新事件或错误的重要信息和见解，这些事件或错误可能会影响计划的刷新事件的性能或完成。

下面的几个部分将依次介绍这些视图。 

## <a name="refresh-history"></a>刷新历史记录

可通过单击“刷新摘要”页上的“历史记录”来选择历史纪录视图 。

![刷新摘要中的“历史记录”视图](media/refresh-summaries/refresh-summaries-01a.jpg)

历史记录概述了你对其具有管理员权限的容量最近计划刷新的结果。 可以通过单击列将视图按任意列进行排序。 可选择按升序、降序或使用文本筛选器选择的列对视图进行排序。

![对“历史记录”视图进行排序](media/refresh-summaries/refresh-summaries-01b.jpg)

在“历史记录”视图中，与给定刷新关联的数据基于每个计划的刷新的最新 60 条记录。

你还可将任何计划的刷新信息导出到 .CSV 文件，其中包括详细信息，涵盖每个刷新事件的错误消息。 导出到 .CSV 文件后，可以根据任何列对文件进行排序，搜索单词，根据错误代码或所有者进行排序等。 下图显示了导出的 .CSV 文件示例。 

![导出有关刷新的信息](media/refresh-summaries/refresh-summaries-05.jpg)

使用导出文件中的信息，可以查看为刷新实例记录的容量、持续时间和任何错误消息。 


## <a name="refresh-schedule"></a>刷新计划

可通过单击“刷新摘要”中的“计划”来选择计划视图 。 “计划”视图显示一周的计划信息，细分为 30 分钟的时间段。 

![屏幕截图显示“刷新计划”页面的“计划”选项卡特写。](media/refresh-summaries/refresh-summaries-02a.jpg)

“计划”视图非常适用于确定计划的刷新事件是否具有适当间隔，以便在不重叠的情况下完成所有刷新，或确定是否计划了耗时太长并导致资源争用的刷新事件。 如果发现此类资源争用，则应调整刷新计划以避免冲突或重叠，以便计划的刷新可以成功完成。 

![屏幕截图显示“刷新计划”页面的“计划”选项卡。](media/refresh-summaries/refresh-summaries-02.jpg)

“刷新已预订时间(分钟)”列是对每个关联数据集的最多 60 条记录求平均值计算的结果。 每个 30 分钟时间段的数值是对计划在该时间段开始的所有计划刷新以及设置为在前一个时间段开始的任何计划刷新计算的分钟总和，但其平均持续时间会溢出到所选时间段。

“刷新空闲时间(分钟)”列是计算在每个时间段内可供刷新的分钟数减去已计划在该时间段内刷新的分钟数的结果。 例如，如果你的 P2 订阅提供 12 个并发运行的刷新，则你会有 12 个 30 分钟的时间段，因此 12 次刷新 x 每次 30 分钟 = 在该时间段内可供刷新 360 分钟。 如果在该时间段内预定了一次需要 20 分钟的刷新，则该时间段内的“刷新空闲时间(分钟)”为 340 分钟（总可用分钟数 360 减去已预定的分钟数 20 = 仍可用分钟数 340）。 

可以选择一个时间段，然后选择关联的“详细信息”按钮，以查看哪些计划的刷新事件会影响预定的刷新时间、其所有者以及完成时间。

让我们通过一个示例来了解其工作原理。 当我们为星期天选择“晚上 8:30”的时间段，并单击“详细信息”时，将显示以下对话框。

![屏幕截图显示所选时间的刷新的详细信息。](media/refresh-summaries/refresh-summaries-04.jpg)

此时间段内发生了三个计划的刷新事件。 

计划的刷新 #1 和 #3 均计划用于该“晚上 8:30”的时间段，我们可以通过查看“计划时间段”列中的值来确定。 它们的平均持续时间分别为 4 秒 39 和 6 秒 (0:06)。 大功告成。

不过，计划的刷新 #2 计划用于“晚上 8 点”的时间段，但由于其平均持续时间超过 48 分钟（可从“平均持续时间”列中看出来），刷新事件会溢出到下一个 30 分钟的时间段。 

这种做法不好。 在这种情况下，管理员应联系该计划刷新实例的所有者，并建议他们为该计划刷新找到不同的时间段，或者重新计划其他刷新以避免发生重叠，或查找其他解决方案来防止此类重叠。 


## <a name="next-steps"></a>后续步骤

- [Power BI 中的数据刷新](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [本地数据网关（个人模式）](service-gateway-onprem.md)  
- [本地数据网关故障排除](service-gateway-onprem-tshoot.md)  
- [Power BI Gateway - Personal 故障排除](service-admin-troubleshooting-power-bi-personal-gateway.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
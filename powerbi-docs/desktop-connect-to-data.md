---
title: 连接到 Power BI Desktop 中的数据
description: 连接到 Power BI Desktop 中的数据
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e0430455131b0669dfa744c7a1df6691bda4c782
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578143"
---
# <a name="connect-to-data-in-power-bi-desktop"></a>在 Power BI Desktop 中连接到数据
通过 Power BI Desktop，可以轻松连接到持续扩展的数据世界。 如果没有 Power BI Desktop，你可以[下载](http://go.microsoft.com/fwlink/?LinkID=521662)并进行安装。

Power BI Desktop 中有各种可用数据源。下图显示了如何通过依次选择“文件”功能区、“获取数据”\>“更多”来连接到数据。

![](media/desktop-connect-to-data/getdatavid_smallv2.gif)

在此示例中，我们将连接到 **Web** 数据源。

假设你即将退休 - 你希望居住到一个阳光充足、税制合理且具备良好卫生保健的地方。 或者... 也许你是一位数据分析人员，并且你需要该信息来帮助你的客户 - 例如，帮助你的雨衣制造客户将目标市场定位在 *经常* 下雨的地方。

无论哪种需求，你都可以在下列 Web 资源中找到与这些主题相关的有趣数据和详细信息：

[*http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx*](http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

选择**获取数据\> Web**，然后键入地址。

![](media/desktop-connect-to-data/connecttodata_3.png)

选择“确定”后，Power BI Desktop 的“查询”功能就会开始运行。 Power BI Desktop 会连接到 Web 资源，“导航器”窗口将返回它在该网页上找到的结果。 在本例中，它找到一个表（表格 0）和整份文档。 我们对该表有兴趣，因此我们从列表中选择它。 导“导航器”窗口会显示预览信息。

![](media/desktop-connect-to-data/datasources_fromnavigatordialog.png)

此时我们可以通过从窗口底部选择**编辑**，先编辑查询再加载表，或者我们可以直接加载表。

如果选择**编辑**，则会加载该表并启动查询编辑器。 会显示**查询设置**窗格（若未显示，可以从功能区选择**视图**，然后依次选择**显示 \> 查询设置**来显示**查询设置**窗格）。 以下是其外观。

![](media/desktop-connect-to-data/designer_gsg_editquery.png)

所有得分都是文本而非数字，而我们需要使用数字。 没问题 – 只需右键单击列标题，然后选择**更改类型 \> 整数**来对其进行更改。 若要选择多列，请先选择一列然后按住 **Shift**，再选择其他相邻列，然后右键单击列标题以更改所有选中的列。 使用 **Ctrl** 来选择不相邻的列。

![](media/desktop-connect-to-data/designer_gsg_changedatatype.png)

在**查询设置**中，**所应用步骤**会反映任何已做的更改。 对数据进行其他更改时，查询编辑器将在**所应用步骤**部分记录更改内容，你可以根据需要进行调整、重新访问、重新排列或删除。

![](media/desktop-connect-to-data/designer_gsg_appliedsteps_changedtype.png)

加载表后，仍可对其进行其他更改，但目前到此为止即可。 完成时，从**开始**功能区选择**关闭并应用**，Power BI Desktop 则会应用更改并关闭查询编辑器。

![](media/desktop-connect-to-data/connecttodata_closenload.png)

加载数据模型后，即可在 Power BI Desktop 的**报表**视图中通过将字段拖动到画布上开始创建可视化效果。

![](media/desktop-connect-to-data/connecttodata_dragontoreportview.png)

当然，这只具有单一数据连接的简单模型；大多数 Power BI Desktop 报表会连接到不同的数据源并根据需要调整各种关系以产生丰富的数据模型。 

### <a name="next-steps"></a>后续步骤
Power BI Desktop 可用于执行多种操作。 有关其功能的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 的查询概述](desktop-query-overview.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常见查询任务](desktop-common-query-tasks.md)   

要向我们提供反馈？ 请使用 Power BI Desktop 中的“提交想法”菜单项或访问[社区反馈](http://community.powerbi.com/t5/Community-Feedback/bd-p/community-feedback)。 我们期待收到你的留言！

![](media/desktop-connect-to-data/sendfeedback.png)


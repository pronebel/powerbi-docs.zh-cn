---
title: 面向 Power BI 使用者的问答
description: Power BI 问答自然语言查询的文档概述主题。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 9960ebe11271eea34245250ef5701e9a94bba744
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2019
ms.locfileid: "67408446"
---
# <a name="qa-for-power-bi-consumers"></a>面向 Power BI 使用者的问答 
## <a name="what-is-qa"></a>“问答”是什么？
有时从你的数据中获得答案的最快方法是使用自然语言提问。 例如，“去年的销售总额是多少”。

使用“问答”来利用直观、自然的语言功能浏览数据并接收图表和图形形式的答案。 “问答”与搜索引擎不同 --“问答”仅提供有关 Power BI 中的数据的结果。

使用专业版或高级版许可证可访问“Power BI 问答”  。  [Power BI 移动应用中的问答](mobile/mobile-apps-ios-qna.md)和 [Power BI Embedded 中的问答](../developer/qanda.md)通过单独的文章进行了介绍。 目前，Power BI 问答  只支持回答用英语询问的自然语言查询，尽管有西班牙语预览版问答可供 Power BI 管理员启用。


![问答创建树状图](media/end-user-q-and-a/power-bi-treemap.png)

提问仅仅是个开始。  在完善数据或扩展问题、发现可信的新信息、专注细节以及缩小以获得更宽广的视野的过程中找到乐趣吧。 你将会满意你的见解和发现。

体验是真正的交互式…并且快速！ 由内存存储提供支持，响应几乎瞬时完成。

## <a name="where-can-i-use-qa"></a>在哪里可以使用问答？
问答位于 Power BI 服务中的仪表板上，以及 Power BI 移动版的仪表板底部。 只有在设计者授予编辑权限后，才能使用 Power BI 问答浏览数据，但无法保存通过 Power BI 问答创建的任何可视化效果。

![问题框](media/end-user-q-and-a/powerbi-qna.png)

## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>在 Power BI 服务中的仪表板上使用问答
在 Power BI 服务 (app.powerbi.com) 中，由于仪表板包含从一个或多个数据集固定的磁贴，因此可以就其中任一数据集中的任何数据提问。 若要查看用于创建仪表板的报表和数据集，请选择菜单栏中的“查看相关项”  。

![顶部菜单栏中的“查看相关项”按钮](media/end-user-q-and-a/power-bi-view-related.png)

## <a name="how-do-i-start"></a>如何开始使用该功能？
首先，熟悉内容。 查看仪表板和报表中的视觉对象。 了解可用的数据类型和范围。 

例如：

* 如果视觉对象的坐标轴标签和值包括“销售额”、“帐户”、“月份”和“商机”，你可以有把握地提出以下问题：“哪个帐户  的商机  最大”或“以条形图的形式按月显示销售额  ”。

* 如果可以通过 Google Analytics（Google 分析）获取网站性能数据，则可以向“问答”提出关于花在网页上的时间、独特网页访问数以及用户参与度方面的问题。 如果你要查询地理数据，则可以按位置就年龄和家庭收入提问。

熟悉数据后，立即返回到仪表板，并将光标放在问题框中。 这会打开问答屏幕。

![问答屏幕](media/end-user-q-and-a/power-bi-screen.png) 

在开始键入前，“问答”会显示新的屏幕，上面有帮助你提问的一些建议。 你会看到，包含基础数据集中表名称的短语和问题，甚至还会看到由数据集所有者创建的特别推荐  *问题。

可以选择其中任一问题，将其添加到问题框中，然后优化问题，以找到具体答案。 

问答帮助你提问的另一种方式是通过提示、自动完成和视觉提示。 

![视频](media/end-user-q-and-a/qna4.gif) 


### <a name="which-visualization-does-qa-use"></a>问答使用哪些可视化效果？
问答会根据要显示的数据选取最佳的可视化效果。 有时，可将基础数据集中的数据定义为特定类型或类别，以帮助问答识别如何显示数据。 例如，如果数据被定义为日期类型，则该数据很有可能显示为线图。 如果将数据分类为城市，则很有可能显示为地图。

还可以将视觉对象添加到问题中，指示问答要使用哪个视觉对象。 但请注意，问答并非总能显示你请求使用的视觉对象类型中的数据。 问答会提示你提供可显示的视觉对象类型列表。


## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
**问题**：我在仪表板上未看到“问答”。    
**回答 1**：如果你没有看见问题框，首先应检查你的设置。 为此请在 Power BI 工具栏的右上角选择齿轮图标。   
![齿轮图标](media/end-user-q-and-a/power-bi-settings.png)

然后选择“设置” > “仪表板”   。 请确保“在此仪表板上显示问答搜索框”旁有复选标记  。    
![仪表板的问答设置](media/end-user-q-and-a/power-bi-turn-on.png)  


**回答 2**：有时仪表板设计者或你的管理员关闭了问答  。 与他们核实，了解是否可以重新打开问答。   

**问题**：输入问题时未得到希望看到的结果。    
**回答**：与仪表板设计者沟通  。 设计者可以执行许多操作来改善问答结果。 例如，设计者可以将数据集中的列重命名为易于理解的术语（`CustomerFirstName`而不是 `CustFN`）。 设计者非常了解数据集，因此，他也可以提出有用的问题并将其添加到问答画布中。


## <a name="next-steps"></a>后续步骤
[面向 Power BI 使用者的问答提示](end-user-q-and-a.md)

---
title: 将注释添加到仪表板和报表
description: 本文档介绍如何将注释添加到仪表板、报表或视觉对象，以及如何使用注释与协作者进行对话。
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 01/08/2021
LocalizationGroup: Consumer
ms.openlocfilehash: a4a89fd9db3ea3d92012bdaffdcaf248f7546c86
ms.sourcegitcommit: f791eef8e885f18c48997c9af63ab56211f1ceb8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2021
ms.locfileid: "98053457"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>将注释添加到仪表板或报表

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

添加个人注释或与同事开始有关仪表板或报表的对话。 “注释”功能只是业务用户与他人协作的方式之一。 

![“注释”视频](media/end-user-comment/comment.gif)

> [!NOTE]
> 与其他人协作（包括向共享报表添加注释）需要 Power BI Pro 许可证，或者需要将内容承载在 Power BI Premium 容量中。 [我有哪种许可证类型？](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>如何使用注释功能
可以将注释添加到整个仪表板、仪表板上的各个视觉对象、报表页、分页报表以及报表页上的各个视觉对象。 添加常规注释或添加针对特定同事的注释。  

将注释添加到报表时，Power BI 捕获当前筛选器和切片器值，并创建[书签](end-user-bookmarks.md)。 这意味着，在选择或响应注释时，报表页或报表视觉对象可能会发生更改，以显示首次添加该注释时处于活动状态的筛选器和切片器选择。  

![带筛选器的报表视频](media/end-user-comment/power-bi-comment.gif)

为什么这很重要？ 假设某位同事应用了一个筛选器，该筛选器显示了要与团队共享的有趣见解。 如果未选择该筛选器，则注释可能无意义。

如果使用的是分页报表，则只能对报表进行常规注释。  不支持对单个分页报表视觉对象进行注释。

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>将常规注释添加到仪表板或报表
将注释添加到仪表板和报表的过程类似。  在此示例中，我们使用仪表板。 

1. 打开 Power BI 仪表板或报表，然后选择“注释”图标。 这将打开“注释”对话框。

    ![菜单栏上的“注释”图标](media/end-user-comment/power-bi-comment-icon.png)

    在这里，我们可以看到仪表板创建者已经添加了常规注释。  有权访问此仪表板的任何人员都可以看到此注释。

    ![仪表板的屏幕截图，其中选定了“注释”部分](media/end-user-comment/power-bi-first-comments.png)

2. 若要进行答复，请选择“答复”，输入答复内容，然后选择“发布” 。  

    ![“选择答复”屏幕](media/end-user-comment/power-bi-comments-reply.png)

    默认情况下，Power BI 会将答复定向到启动注释线程的同事，在本例中为 Aaron。 

    ![包含答复的注释](media/end-user-comment/power-bi-respond.png)

 3. 如果要添加不属于现有线程的注释，请在上面部分的文本字段中输入注释。

    ![显示了新线程的屏幕截图](media/end-user-comment/power-bi-new-commenting.png)

    此仪表板的注释现在如下所示。

    ![注释对话](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>向特定仪表板或报表视觉对象添加注释
除了将注释添加到整个仪表板或整个报表页之外，还可以将注释添加到各个仪表板磁贴和各个报表视觉对象。 这些添加过程类似，在此示例中，我们使用报表。

1. 将鼠标指针悬停在视觉对象上，并选择“更多操作”(…)。    
2. 从下拉列表中，选择“添加注释”。

    ![“添加注释”是第一个选项](media/end-user-comment/power-bi-comment-reports.png)  

3.  “注释”对话框打开，且页上的其他视觉对象灰显。此视觉对象没有任何注释。 

    ![选定视觉对象的屏幕截图，其中打开了“注释”对话框](media/end-user-comment/power-bi-comments-column.png)  

4. 键入注释，然后选择“发布”。

    ![其中包含新消息的“注释”对话框](media/end-user-comment/power-bi-comment-spikes.png)  

    - 在报表页上，选择对某一视觉对象的注释即可突出显示该视觉对象（见下）。

    - 在仪表板上，图表图标 ![包含图表图标的注释](media/end-user-comment/power-bi-comment-chart-icon.png) 让我们知道注释已与特定视觉对象相关联。 应用于整个仪表板的注释没有特殊图标。 选择图表图标会突出显示仪表板上的相关视觉对象。
    

    ![突出显示的相关视觉对象](media/end-user-comment/power-bi-highlights.png)

5. 选择“关闭”返回仪表板或报表。

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>通过使用 @ 符号引起同事的注意
无论是创建仪表板、报表、磁贴还是视觉对象注释，都可以通过使用“\@”符号来吸引同事的注意。  当键入“\@”符号时，Power BI 会打开一个下拉菜单，你可以在其中搜索并从组织中选择单个人员。 任何以“\@”符号开头的经过验证的名称都会以蓝色字体显示。 @mentioned 个人会立即在其收件箱中收到一封电子邮件，如果他们使用 Power BI 移动应用，则将在其设备上收到推送通知。 他们可直接在通知中打开报表或仪表板、查看注释、查看数据集，并相应地回复。

下面是我与可视化效果设计人员的对话。 他们使用 @ 符号确保我可以看到这条注释。 我收到通知并选择链接打开此仪表板和相关对话。  

![添加提及注释](media/end-user-comment/power-bi-comment-conversation.png)  

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

- 回复对话时，不会捕获书签。 只有对话中的第一个注释会创建书签。
- 如果使用的是分页报表，则只能对报表进行常规注释。  不支持对单个分页报表视觉对象进行注释。

## <a name="next-steps"></a>后续步骤
返回[业务用户的可视化效果](end-user-visualizations.md)    
[选择可视化效果以打开报表](end-user-report-open.md)

---
title: 使用 Power BI 中的按钮
description: 借助 Power BI Desktop 中的按钮，可以制作出类似应用的报表和仪表板，并加深与用户的互动
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9d884df7fdfa6d0f16e7963c00a1100186d70546
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239496"
---
# <a name="using-buttons-in-power-bi"></a>使用 Power BI 中的按钮
使用 Power BI 中的“按钮”，可创建类似于应用的报表和仪表板，从而创建引人入胜的环境，以便用户可悬停鼠标在 Power BI 内容上、单击它并进一步与之交互  。 可将按钮添加到 Power BI Desktop 中的报表，并将这些报表共享或发布到 Power BI 服务，以创建为用户提供行为类似于应用的仪表板  。

![Power BI 中的按钮](media/desktop-buttons/desktop-buttons_01.png)

在 Power BI Desktop 中创建的按钮可用于在 Power BI 服务中发布的报表或仪表板   。

## <a name="creating-buttons-in-reports"></a>在报表中创建按钮
要在 Power BI Desktop 报表中创建按钮，请在“主页”功能区上选择“按钮”，然后会出现下拉菜单，可在其中的系列选项中选择所需按钮，如下图所示    。 

![在 Power BI Desktop 中添加按钮控件](media/desktop-buttons/desktop-buttons_02.png)

创建按钮并在报表画布上选择该按钮时，“可视化效果”窗格将提供众多途径助你自定义按钮来满足需要  。 例如，通过切换“可视化效果”窗格的卡片中的滑块，打开或关闭“按钮文本”   。 还可更改按钮的图标、按钮填充、标题、用户单击报表或仪表板中的按钮时所执行的操作和其他属性。

![在 Power BI Desktop 中设置按钮的格式](media/desktop-buttons/desktop-buttons_03.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>空闲、悬停或选中时设置按钮属性

Power BI 中的按钮有三种状态：默认状态（未悬停或选中时的显示方式）、悬停状态或选中状态（通常指“被单击”）  。 “可视化效果”窗格中的许多卡可以根据这三种状态单独修改，从而可灵活地自定义按钮  。

“可视化效果”窗格中的以下卡允许你根据按钮的三种状态调整按钮的格式或行为  ：

* 按钮文本
* 图标
* 轮廓
* 填充

要为每种状态选择按钮的显示方式，请展开其中一张卡，然后选择卡顶部的下拉列表。 在下图中，将看到已展开的“边框”卡，且选中了下拉列表显示出三种状态  ：

![Power BI Desktop 中按钮的三种状态](media/desktop-buttons/desktop-buttons_04.png)


## <a name="select-the-action-for-a-button"></a>选择按钮的操作

可选择用户在 Power BI 中选择按钮时所采取的操作。 可从“可视化效果”窗格中的“操作”卡访问按钮操作的选项   。

![Power BI 中按钮的操作](media/desktop-buttons/desktop-buttons_05.png)

按钮操作的选项如下：

* 返回
* 书签
* 问答

选择“返回”  会将用户返回到报表的上一页。 这对于下钻页面特别有用。

选择“书签”将显示与为当前报表定义的书签关联的报表页  。 可以[了解 Power BI 中书签的详细信息](desktop-bookmarks.md)。 

从下拉菜单中选择“问答”将显示“问答资源管理器”窗口   。 

某些按钮将自动选择默认操作。 例如，“问答”按钮类型会自动选择“问答”作为默认操作   。 通过查看[此博客文章](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer)，了解有关“问答资源管理器”的更多信息  。

通过单击想使用的按钮同时按 Ctrl，试用或测试为报表创建的按钮  。 

## <a name="next-steps"></a>后续步骤
若要详细了解与按钮类似或与其交互的功能，请参阅以下文章：

* [在 Power BI Desktop 中使用钻取](desktop-drillthrough.md)
* [在“焦点”模式下显示仪表板磁贴或报表视觉对象](consumer/end-user-focus.md)
* [在 Power BI 中使用书签共享见解和创建情景](desktop-bookmarks.md)


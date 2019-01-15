---
title: 什么是 Power BI Desktop？
description: 了解什么是 Power BI Desktop，以及如何开始使用它
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: d687e9ed9fac38dabf539a4f2fffbc89cf3a2bbb
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296106"
---
# <a name="what-is-power-bi-desktop"></a>什么是 Power BI Desktop？

Power BI Desktop 是一款可在本地计算机上安装的免费应用程序，可用于连接到数据、转换数据并实现数据的可视化效果。 借助 Power BI Desktop，可以连接到多个不同数据源并将它们（通常称为“建模”）合并到数据模型中，该模型允许用户生成可作为报表与组织内的其他人共享的视觉对象和视觉对象集合。 致力于商业智能项目的大多数用户使用 Power BI Desktop 创建报表，然后使用 Power BI 服务与其他人共享其报表。

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Power BI Desktop 的最常见用途如下：

* 连接到数据
* 转换和清除该数据，以创建数据模型
* 创建视觉对象，如提供数据的可视化表示形式的图表或图形
* 在一个或多个报表页上创建作为视觉对象集合的报表
* 使用 **Power BI 服务**与其他人共享报表

最常负责此类任务的人员通常被视为“数据分析师”（有时简称为“分析师”）或“商业智能专业人员”（通常称为“报表创建者”）。 但是，不将自己视为分析师或报表创建者的许多人使用 Power BI Desktop 创建引人注目的报表，或拉取来自各个源的数据并生成可与其同事和组织共享的数据模型。

借助 Power BI Desktop，可以使用来自多个源的数据创建复杂且视觉效果丰富的报表，即可与组织中的其他人共享的多合一报表。 

## <a name="connect-to-data"></a>连接到数据
要开始使用 Power BI Desktop，第一步为连接到数据。 可从 Power BI Desktop 连接到多个不同数据源。 要连接到数据，只需选择“主页”功能区，然后选择“获取数据”>“更多”。 下图显示出现的“获取数据”窗口，其中显示了 Power BI Desktop 可连接到的多个类别。

![在 Power BI Desktop 中获取数据](media/desktop-what-is-desktop/what-is-desktop_02.png)

选择数据类型时，系统会提示输入 Power BI Desktop 代表你连接到数据源所需的 URL 和凭据等信息。

![在 Power BI Desktop 中连接到 SQL Server 数据库](media/desktop-what-is-desktop/what-is-desktop_03.png)

连接到一个或多个数据源后，可能希望转换数据，因此这样做对你非常有用。

## <a name="transform-and-clean-data-create-a-model"></a>转换和清除数据、创建模型

在 Power BI Desktop 中，可以使用内置查询编辑器清除并转换数据。 使用查询编辑器可以对数据进行更改，如更改数据类型、删除列或合并来自多个源的数据。 这有点像雕刻，你可以从大块泥土（或数据）开始，然后进行刮削或根据需要添加其他，直到数据形状符合你的要求。 

![Power BI Desktop 中的查询编辑器](media/desktop-getting-started/designer_gsg_editquery.png)

查询编辑器会记录转换数据过程中采取的每个步骤（如重命名表格、转换数据类型或删除列），且每当此查询连接到数据源时，都会执行这些步骤，因此数据将始终按你指定的方式进行调整。

下图显示已调整并转换为模型的查询的“查询设置”窗格。

 ![](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

数据符合你的要求后，即可创建视觉对象。 

## <a name="create-visuals"></a>创建视觉对象 

拥有数据模型后，即可将字段拖动到报表画布上以创建视觉对象。 视觉对象是模型中的数据的图形表示形式。 以下视觉对象显示一个简单的柱形图。 

![Power BI Desktop 中的视觉对象](media/desktop-what-is-desktop/what-is-desktop_04.png)

可以在 Power BI Desktop 中选择多个不同类型的视觉对象。 若要创建或更改视觉对象，只需从“可视化效果”窗格中选择视觉对象图标。 如果已在报表画布上选择一个视觉对象，则选定的视觉对象将更改为所选的类型。 如果未选择任何视觉对象，将根据你的选择创建新的视觉对象。

![Power BI Desktop 中的“可视化效果”窗格](media/desktop-what-is-desktop/what-is-desktop_05.png)

## <a name="create-reports"></a>创建报表

通常，你会想要创建视觉对象集合，这些视觉对象可显示已用于在 Power BI Desktop 中创建模型的数据的各个方面。 一个 Power BI Desktop 文件中的视觉对象集合称为“报表”。 报表可以有一个或多个页面，就像 Excel 文件可以有一个或多个工作表。 在下图中，你将看到 Power BI Desktop 报表的首页，名为“概述”（你可以看到图像底部附近的选项卡）。 在此报表中，有十个页面。

![具有十个页面的 Power BI Desktop 报表](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>共享报表

准备好与其他人共享报表后，可以将报表发布到 Power BI 服务，并使其可供组织中拥有 Power BI 许可证的任何人使用。 若要发布 Power BI Desktop 报表，可在 Power BI Desktop 中从“主页”功能区选择“发布”按钮。

![从 Power BI Desktop 发布报表](media/desktop-what-is-desktop/what-is-desktop_06.png)

选择“发布”后，Power BI Desktop 会使用 Power BI 帐户连接到 Power BI 服务，然后提示你选择 Power BI 服务中想要共享报表的位置，例如，你的工作区、团队工作区或 Power BI 服务中的一些其他位置。 必须具有 Power BI 许可证才能将报表共享到 Power BI 服务。


## <a name="next-steps"></a>后续步骤

要开始使用 Power BI Desktop，首先需要下载并安装应用程序。 有两种方法可用于获取 Power BI Desktop：

* [从 Web 下载 Power BI Desktop](desktop-get-the-desktop.md)
* [通过 Windows 应用商店获取 Power BI Desktop](http://aka.ms/pbidesktopstore)

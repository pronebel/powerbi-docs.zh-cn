---
title: 通过 Power BI Desktop 连接到网页
description: 通过 Power BI Desktop 轻松连接并使用网页数据
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7a3444aca5f74dd54ba292548ac5fa1d848f5172
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85223980"
---
# <a name="connect-to-webpages-from-power-bi-desktop"></a>通过 Power BI Desktop 连接到网页

用户可以连接到网页，然后将其数据导入到 Power BI Desktop 并在视觉对象和数据模型中使用该数据。

在 Power BI Desktop 中，从“开始”  功能区选择“获取数据”>“Web”  。

![](media/desktop-connect-to-web/connect-to-web_1.png)

此时将出现一个对话框，要求提供想要从中导入数据的网页的 URL。

![](media/desktop-connect-to-web/connect-to-web_2.png)

键入（或粘贴）该 URL 后，请选择“确定”  。 Power BI Desktop 将连接到该页面，然后在“导航器”  窗口显示页面的可用数据。 当你选择了其中一个可用的数据元素（如整页的表）后，“导航器”  窗口将在右侧显示该数据的预览。

![](media/desktop-connect-to-web/connect-to-web_3.png)

你可以选择“编辑”  按钮，启动“编辑查询器”  ，在其中你可以在将数据导入 Power BI Desktop 前在网页上调整和转换该数据。 或者也可以选择“加载”  按钮，然后导入左窗格中所有选定的数据元素。

当我们选择“加载”时，  Power BI Desktop 将导入所选项目，并使其在 Power BI Desktop 中的报表视图右侧的“字段”  窗格中可用。

![](media/desktop-connect-to-web/connect-to-web_4.png)

连接到网页并将其数据导入 Power BI Desktop 的步骤就是这些。

接下来，你可以将这些字段拖到报表画布并创建所有想要的可视化效果。 你还可以同使用其他所有数据一样使用来自该网页的数据，例如调整该数据、在它与模型中其他数据源之间创建关系以及进行一切所需操作来创建你想要的 Power BI 报表。

若要更深入地了解连接到网页，请查看 [Power BI Desktop 入门指南](../fundamentals/desktop-getting-started.md)。

## <a name="next-steps"></a>后续步骤
你可以使用 Power BI Desktop 连接到各种数据。 有关数据源的详细信息，请参阅下列资源：

* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [通过 Power BI Desktop 连接到 CSV 文件](desktop-connect-csv.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   

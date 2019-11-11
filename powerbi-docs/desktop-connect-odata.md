---
title: 通过 Power BI Desktop 连接到 OData 数据源
description: 通过 Power BI Desktop 轻松连接并使用 OData 数据源
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3f825c3c7247cba41d574dccde2fc5eda49e70a2
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876435"
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>通过 Power BI Desktop 连接到 OData 数据源
在 Power BI Desktop 中，你可以连接到“OData 数据源”  并在 Power BI Desktop 中同使用其他所有数据源一样使用基础数据。

若要连接到 OData 数据源，请在 Power BI Desktop 的“开始”  功能区中，选择“获取数据”>“OData 数据源”  。

![](media/desktop-connect-odata/connect-to-odata_1.png)

在出现的“OData 数据源”  窗口中，将你的 OData 数据源 URL 键入或粘贴到框中，然后选择“确定”  。

![](media/desktop-connect-odata/connect-to-odata_2.png)

Power BI Desktop 将连接到 OData 数据源，并显示可用的表和“导航器”  窗口中的其他数据元素。 选择一个元素后，“导航器”  窗口的右窗格中将显示该数据的预览。 你可以选择导入任意数量的表。 “导航器”  窗口将显示当前所选表的预览。

![](media/desktop-connect-odata/connect-to-odata_3.png)

你可以选择“编辑”  按钮，启动“编辑查询器”  ，在其中你可以在将 OData 数据源中的数据导入 Power BI Desktop 前调整和转换该数据。 或者也可以选择“加载”  按钮，然后导入左窗格中所有选定的数据元素。

当我们选择“加载”  时，Power BI Desktop 将导入所选项目，并显示导入进度的“加载”窗口  。

![](media/desktop-connect-odata/connect-to-odata_4.png)

完成操作后，Power BI Desktop 会使所选表和其他数据元素在 Power BI Desktop 中报表  视图右侧的“字段”  窗格中可用。

![](media/desktop-connect-odata/connect-to-odata_5.png)

这样就大功告成了！

你现在已准备好在 Power BI Desktop 中使用从 OData 数据源导入的数据来创建视觉对象、报表或与你可能想要连接和导入的其他数据（如 Excel 工作簿、数据库或任何其他数据源）进行交互。

## <a name="next-steps"></a>后续步骤
你可以使用 Power BI Desktop 连接到各种数据。 有关数据源的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   


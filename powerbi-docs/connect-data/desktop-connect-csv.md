---
title: 通过 Power BI Desktop 连接到 CSV 文件
description: 通过 Power BI Desktop 轻松连接并使用 CSV 文件
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 3bb37d4ba3b3ca7d5fec3f8577b971432f5a9d0f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411370"
---
# <a name="connect-to-csv-files-in-power-bi-desktop"></a>通过 Power BI Desktop 连接到 CSV 文件
通过 Power BI Desktop 连接到以逗号分隔的值 (*CSV*) 文件同连接到 Excel 工作簿非常相似。 两者都很简单，这篇文章将对怎样连接到你有权访问的 CSV 文件进行指导。

首先，在 Power BI Desktop 中，从“开始”功能区选择“获取数据”>“CSV”。

![“获取数据”菜单的屏幕截图。](media/desktop-connect-csv/connect-to-csv_1.png)

从出现的“打开”对话框中选择 CSV 文件。

![“打开”对话框的屏幕截图。](media/desktop-connect-csv/connect-to-csv_2.png)

当你选择“打开”时，Power BI Desktop 将访问该文件，并确定某些文件属性（如文件来源、分隔符类型和用于检测文件数据类型的应有行数）。

这些文件属性和选项将显示在“CSV 导入”对话框窗口顶部的下拉选择列表中，如下所示。 你可以通过从下拉选择器中选择其他选项对所有检测到的设置进行手动更改。

![“CSV 导入”对话框窗口的屏幕截图。](media/desktop-connect-csv/connect-to-csv_3.png)

选择所需选项后，你可以选择“加载”将文件导入 Power BI Desktop，或者你可以选择“编辑”以打开“查询编辑器”，在导入前对数据进行进一步调整和转换。

将数据加载到 Power BI Desktop 后，你将在 Power BI Desktop 中的“报表”视图右侧的“字段”窗格中看到该表及其列（显示为 Power BI Desktop 中的字段）。

![显示“字段”窗格的 Power BI Desktop 窗口的屏幕截图。](media/desktop-connect-csv/connect-to-csv_4.png)

以上就是你需要操作的全部步骤 – 现在，CSV 文件中的数据全都在 Power BI Desktop 中了。

你可以在 Power BI Desktop 中使用该数据来创建视觉对象、报表或与你可能想要连接和导入的其他数据（如 Excel 工作簿、数据库或任何其他数据源）进行交互。

> [!IMPORTANT]
> 导入 CSV 文件时，Power BI Desktop 会在 Power Query 编辑器中生成一个 columns=x（其中，x 是 CSV 文件中的列数）作为一个步骤 。 如果随后添加更多列并且数据源设置为“刷新”，则不会刷新超出初始 x 列数的任何列。 


## <a name="next-steps"></a>后续步骤
你可以使用 Power BI Desktop 连接到各种数据。 有关数据源的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   

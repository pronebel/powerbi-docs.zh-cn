---
title: 将 Excel 工作簿导入 Power BI Desktop
description: 将 Excel 工作簿导入 Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 4a9fa542780beafdbb5313e9de5a4875a3f39cb8
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54274803"
---
# <a name="import-excel-workbooks-into-power-bi-desktop"></a>将 Excel 工作簿导入 Power BI Desktop
通过 Power BI Desktop，可将 Excel 工作簿轻松导入带有 Power Query 查询、Power Pivot 模型和 Power View 工作表的 Power BI Desktop。 报表和可视化效果均基于 Excel 工作簿自动创建，导入后，你可以使用 Power BI Desktop 的现有功能以及其每月更新的新功能继续改善和优化报表。

计划将在 Excel 和 Power BI Desktop 之间提供更多通信（如导入/导出）；借助当前将工作簿导入 Power BI Desktop 的功能，现有 Excel 用户可开始使用 Power BI Desktop。

## <a name="how-do-i-import-an-excel-workbook"></a>如何导入 Excel 工作簿？
若要导入工作簿，请在 Power BI Desktop 中选择**文件 -\> 导入 -\> Excel 工作簿内容**。

![](media/desktop-import-excel-workbooks/importexceltopbi_1.png)

随即将出现一个窗口，让你选择要导入的工作簿。 目前对于工作簿中对象的数量和大小没有限制，但在 Power BI Desktop 中分析和导入较大的工作簿会花费更长的时间。

> [!NOTE]
> 若要从共享 OneDrive for Business 文件夹或 Office 365 组文件夹加载或导入 Excel 文件文件夹，请使用 Excel 文件的 URL，并将其输入到 Power BI Desktop中的 Web 数据源。 需要遵循几个步骤来正确为**OneDrive for Business** URL 设置格式，因此请查看[在 Power BI Desktop 中使用 OneDrive for Business 链接](desktop-use-onedrive-business-links.md)，了解有关详细信息和正确的一系列步骤。
> 
> 

选择工作簿后，Power BI Desktop 将分析该工作簿并将其转换为 Power BI Desktop 文件 (.pbix)。 该操作只执行一次；通过这些步骤创建 Power BI Desktop 文件之后，Power BI Desktop 文件将与原始 Excel 工作簿毫无关联，可修改或更改（以及保存和共享）Power BI Desktop 文件且不影响原始工作簿。

![](media/desktop-import-excel-workbooks/importexceltopbi_2.png)

导入完成后，将显示**摘要**页面，页面上会描述已转换项目并列出不能导入的所有项目。

![](media/desktop-import-excel-workbooks/importexceltopbi_3.png)

选择**关闭**后，将在 Power BI Desktop 中加载该报表。 下图显示了导入 Excel 工作簿后的 Power BI Desktop：Power BI Desktop 根据工作簿内容自动加载了报表。

![](media/desktop-import-excel-workbooks/importexceltopbi_4.png)

由于已导入工作簿，你可以继续处理报表（例如创建新的可视化效果、添加数据或创建新的报表页）以及继续使用 Power BI Desktop 中的所有功能和特性。

## <a name="which-workbook-elements-are-imported"></a>导入了工作簿中的哪些元素？
Power BI Desktop 可导入以下元素，在 Excel 中通常称为*对象*。

| Excel 工作簿中的对象 | Power BI Desktop 文件中的最终结果 |
| --- | --- |
| Power Query 查询 |Excel 中的所有 Power Query 查询都会转换为 Power BI Desktop 中的查询。 如果 Excel 工作簿中已定义查询组，那么将在 Power BI Desktop 中复制相同组织。 除非已在 Excel 中设置为“仅创建连接”的查询，否则请加载其他所有查询。 可在 Power BI Desktop **查询编辑器**的**开始**选项卡中的**属性**对话框自定义加载行为。 |
| Power Pivot 外部数据连接 |所有 Power Pivot 外部数据连接将都转换为 Power BI Desktop 中的查询。 |
| 链接表或当前工作簿表 |如果 Excel 中有工作表数据表链接到数据模型或链接到查询（通过使用“从表格”或 M 中的 Excel.CurrentWorkbook() 函数），将显示下列选项： <ol><li>将表导入到 Power BI Desktop 文件。 该表格是数据的一次性快照，之后将不能编辑 Power BI Desktop 中的表数据。 使用此选项创建的表有大小限制，字数上限为 100 万个字符（总数，包括所有列标题和单元格）。</li><li>保留与原始工作簿的连接。 你还可以保留与原始 Excel 工作簿的连接，Power BI Desktop 每次刷新时都会检索表中的最新内容，就像在 Power BI Desktop 中针对 Excel 工作簿创建的其他查询一样。</li></ul> |
| 数据模型计算列、度量值、KPI、数据类别和数据关系 |这些数据模型对象将转换为 Power BI Desktop 中的等效对象。 注意：某些数据类别在 Power BI Desktop 中不可用，例如图像。 在这些情况下，将对有问题的相关列重置数据类别信息。 |
| Power View 工作表 |为每个 Power View Excel 工作表创建新报表页。 报表的名称和报表页面顺序与原始 Excel 工作簿匹配。 |

## <a name="are-there-any-limitations-to-importing-a-workbook"></a>导入工作簿是否有任何限制？
将工作簿导入 Power BI Desktop 时存在一些限制，如下所示：

* **Analysis Services 表格模型的外部连接：** 在 Excel 2013 中，无需导入数据就可创建 SQL Server Analysis Services 表格模型的连接，并在这些模型之上创建 Power View 报表。 目前不支持使用这种连接类型将 Excel 工作簿导入 Power BI Desktop。 解决方法是，必须在 Power BI Desktop 中重新建立这些外部连接。
* **层次结构：** Power BI Desktop 目前不支持这种数据模型对象类型。 因此，将 Excel 工作簿导入 Power BI Desktop 时会略过层次结构。
* **二进制数据列：** Power BI Desktop 目前不支持这种数据模型列类型。 Power BI Desktop 生成的表中已删除二进制数据列。
* **不支持的 Power View 元素：** Power BI Desktop 目前尚未提供 Power View 中的一些功能，例如布景主题或特定可视化效果类型（具有播放轴的散点图、向下钻取行为等）。 这些不支持的可视化效果会导致在 Power BI Desktop 报表中的对应位置出现*可视化效果不受支持*的消息，你可以根据需要删除或重新配置。
* **命名范围使用 Power Query 中的*****从表*****或使用 M 中的** ***Excel.CurrentWorkbook*****：** 目前不支持将这个名称范围数据导入 Power BI Desktop，但 Power BI Desktop 已计划此更新。 目前，这些名称范围会当做外部 Excel 工作簿的连接，加载到 Power BI Desktop。
* **PowerPivot 至 SSRS：** 由于 Power BI Desktop 目前不提供该数据源，因此目前不支持 SQL Server Reporting Services (SSRS) 的 PowerPivot 外部连接。


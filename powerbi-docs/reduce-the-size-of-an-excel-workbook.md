---
title: 减小 Excel 工作簿的大小以便在 Power BI 中进行查看
description: 减小 Excel 工作簿的大小以便在 Power BI 中进行查看
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: e0151931d0ad9f610c24dd9aedf8f06d79e167c3
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670091"
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>减小 Excel 工作簿的大小以便在 Power BI 中进行查看
你可以将任何小于 1 GB 的 Excel 工作簿上载到 Power BI。 Excel 工作簿包括两个部分：数据模型和报表的其余部分—核心的工作表内容。 如果报表满足下面的大小限制，那么可以将其保存到 **OneDrive for Business**、从 Power BI 中连接它，以及在 Excel Online 中查看它：

* 整个工作簿最大为 1 GB。
* 核心工作表内容最大为 10 MB。

## <a name="what-makes-core-worksheet-contents-larger-than-10-mb"></a>是什么会使核心工作表内容超过 10 MB
下面是一些可以使核心工作表内容大于 10 MB 的元素：

* 图像。
* 具有明暗度的单元格。 [删除单元格的明暗度格式](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e)。
* 有色工作表。 [删除工作表背景](https://support.office.com/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8)。
* 文本框。
* 剪贴画。

如有可能，请考虑删除这些元素。 

如果报表具有数据模型，则你可以选择其他一些选项： 

* 从 Excel 工作表中删除数据，并将其存储在数据模型中。 有关详细信息，请参阅下面的“从工作表中删除数据”。 
* [创建可以高效利用内存的数据模型](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)以减小报表的总体大小。

若要进行上述任何更改，需要在 Excel 中编辑工作簿。

阅读更多有关 [SharePoint Online 中 Excel 工作簿的文件大小限制](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e)的信息。

## <a name="remove-data-from-worksheets"></a>从工作表中删除数据
如果从“Power Query”选项卡或“Excel 数据”选项卡中将数据导入 Excel，那么 Excel 表和数据模型中的工作簿数据可能相同。 Excel 工作表中的大型表可能会使核心工作表内容超过 10 MB。 删除 Excel 中的表，以及将数据保存在数据模型中可以极大地降低报表的核心工作表内容。 

将数据导入 Excel 时，请遵循以下提示：

* **在 Power Query 中**：取消选中**加载至工作表**框。
  
  数据将只导入到数据模型中，Excel 工作表中不含数据。
* 如果之前在导入向导中勾选了**表格**，则在 **Excel 数据**选项卡中：转到**现有连接** \>单击“连接”\> **仅创建连接**。 删除在初始导入过程中创建的原始表或表。
* 在 **Excel 数据**选项卡中：请勿选中**导入数据**框中的**表**。

## <a name="workbook-size-optimizer"></a>工作簿大小优化器
如果工作簿包含数据模型，则可以运行工作簿大小优化器来减小工作簿的大小。 [下载工作簿大小优化器](https://www.microsoft.com/download/details.aspx?id=38793)。

## <a name="related-info"></a>相关的信息
[创建可以高效利用内存的数据模型](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[在 Power BI Desktop 中使用 OneDrive for Business 链接](desktop-use-onedrive-business-links.md)


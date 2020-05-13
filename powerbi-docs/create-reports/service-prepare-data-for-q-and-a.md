---
title: 通过 Power BI 中的问答功能有效利用 Excel 数据
description: 如何有效结合使用数据和 Power BI 问答
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 102145e8c5b2fd3ad19b6703710405d06da5a93a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83323220"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>通过 Power BI 中的问答功能有效利用 Excel 数据
如果你是创建数据模型或生成用于 Power BI 的 Excel 工作簿的人员，请阅读...

在 Power BI 中，“问答”可以搜索结构化数据，然后针对你的问选择合适的可视化效果 — 这让它成为一种极具吸引力的工具。   

“问答”适用于任何已上传的具有表格、范围或包含 PowerPivot 模型的 Excel 文件，但执行的优化和数据清理越多，“问答”性能就越可靠。  如果打算共享根据数据集创建而成的报表和仪表板，不妨方便同事能够轻松提问，并获取优质答案。

## <a name="how-qa-works-with-excel"></a>如何结合使用 Power BI 问答和 Excel
“问答”具有一套核心的自然语言理解功能，可以处理你的数据。 它还具有针对 Excel 表、列和计算的字段名称的上下文相关关键字搜索功能。 它还内置了有关如何筛选、排序、聚合、分组和显示数据的信息。 

例如，在名为“Sales”的 Excel 表中，其中含有“Product”、“Month”、“Units Sold”、“Gross Sales”和“Profit”列，你可以询问有关这些实体的问题。  你可以要求按月显示销售额和总利润、按销售件数对产品排序等其他功能。 详细了解[在仪表板和报表中使用问答](power-bi-tutorial-q-and-a.md)和[可以在 Power BI 问答查询中指定的可视化效果类型](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)。

## <a name="prepare-an-excel-dataset-for-qa"></a>准备 Excel 数据集以供 Power BI 问答使用
“问答”依靠表格、列和计算字段的名称来回答特定于数据的问题，这意味着，实体在工作簿中的命名很重要！

以下是有关充分利用工作簿中的“问答”的一些提示。

* 请确保你的数据在 Excel 表中。 下面是 [how to create an Excel table](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664)（如何创建 Excel 表）。
* 确保表、列和计算字段的名称通俗易懂。
  
  例如，如果表格中含有销售数据，请将此表命名为“Sales”。 像“Year”、“Product”、“Sales Rep”和“Amount”等列名称对“问答”也很适用。

* 如果你的工作簿具有 Power Pivot 数据模型，则可以执行更多优化操作。 详细阅读有关我们内部的自然语言专家所提供的 [Demystifying Power BI问答part 2](https://powerbi.microsoft.com/blog/demystifying-power-bi-q-amp-a-part-2/)（阐述 Power BI 问答（第 2 部））。

* 在 Power BI Desktop 中打开数据集，然后新建列、创建计算度量值、连接字段以创建唯一值、按类型（例如，日期、字符串、地理位置、图像、URL）对数据进行分类等。

## <a name="next-steps"></a>后续步骤

- [面向使用者的问答](../consumer/end-user-q-and-a.md)  
- [在仪表板和报表中使用问答](power-bi-tutorial-q-and-a.md)
- [准备本地数据集以供 Power BI 问答使用](service-q-and-a-direct-query.md)   
- [获取 Power BI 的数据](../connect-data/service-get-data.md)  

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

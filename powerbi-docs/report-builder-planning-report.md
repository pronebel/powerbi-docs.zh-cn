---
title: 在 Power BI 报表生成器中规划报表
description: 使用 Power BI 分页报表生成器，可创建多种类型的分页报表。 要创建有用且易于理解的报表，先进行规划会很有帮助。
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fd4a318d7a61f6f2298de6b9d5d23ad2ae063d28
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840501"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>在 Power BI 报表生成器中规划报表
  使用 Power BI 分页报表生成器，可创建多种类型的分页报表。 例如，可以创建显示摘要或详细销售数据、营销和销售趋势的报表、运营报表或仪表板。 还可以创建文本格式丰富的的报表，例如销售订单、产品目录或套用信函。 所有这些报表都是通过在报表生成器中使用相同基本构建基块的不同组合来创建的。 要创建有用且易于理解的报表，先进行规划会很有帮助。 在开始之前，可能需要考虑以下事项：  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>希望报表以何种格式显示？
  
可以在 Power BI 门户等浏览器中联机呈现报表，也可以将其导出为 Excel、Word 或 PDF 等其他格式。 报表的最终格式是一个重要的考虑因素，因为有些导出格式不支持某些功能。 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>要以哪种结构呈现数据？
  
可以选择表格、矩阵（类似于交叉表或数据透视表报表）、图表、自由格式结构或这些结构的任意组合来呈现数据。 有关详细信息，请参阅 [Power BI 报表生成器中的表、矩阵和列表](report-builder-tables-matrices-lists.md)。  
  
## <a name="how-do-you-want-your-report-to-look"></a>希望报表呈现哪种外观？
  
报表生成器提供了许多报表项，可以将其添加到报表中，以便于受众阅读、突出显示重要信息、帮助受众浏览报表等。 了解自己想以哪种方式显示报表，便可确定是否需要文本框、矩形、图像和线条等报表项。 可能会需要显示或隐藏某些项、添加文档结构图，包括钻取报表或子报表，或链接到其他报表。   
  
## <a name="should-the-data-be-filtered"></a>应对数据进行筛选吗？
  
可能会需要将报表的范围限定到特定用户或位置，或特定时间段。 要筛选报表数据，请使用参数来检索并仅显示所需数据。 有关详细信息，请参阅 [Power BI 报表生成器中的报表参数](paginated-reports-parameters.md)。  
  
## <a name="do-you-need-to-create-calculations"></a>需要创建计算吗？ 
  
     Sometimes, your data source and datasets do not contain the exact fields that you need for your report. In that situation, you might have to create your own calculated fields. For example, you might want to multiply the price per unit times the quantity to get a line item sales amount. Expressions are also used to provide conditional formatting and other advanced features. For more information, see [Expressions in Power BI Report Builder](report-builder-expressions.md).  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>需要在一开始隐藏报表项吗？
  
请考虑是否要在首次运行报表时隐藏报表项，包括数据区域、组和列。 例如，最开始可以显示摘要表，然后通过向下钻取获取详细数据。 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>计划如何交付报表？  
  
     You can save your report to your local computer and continue to work on it, or run it locally for your own information. However, to share your report with others, you need to save the report to Power BI. Saving it to Power BI lets others run it whenever they want to. Alternatively, you can set up a subscription and e-mail delivery of the report to other individuals. You can have the report delivered in a specific export format if you prefer. 
  
## <a name="next-steps"></a>后续步骤

- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)

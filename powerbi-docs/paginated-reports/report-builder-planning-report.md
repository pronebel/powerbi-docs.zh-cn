---
title: 在 Power BI 报表生成器中规划报表
description: 利用 Power BI Report Builder 可创建多种类型的分页报表。 要创建有用且易于理解的报表，先进行规划会很有帮助。
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 30ab632d11befd34ff9a234e441b345c696fb54d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "78922979"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>在 Power BI 报表生成器中规划报表

利用 Power BI Report Builder 可创建多种类型的分页报表。 例如，可以创建显示摘要或详细销售数据、营销和销售趋势的报表、运营报表或仪表板。 还可以创建文本格式丰富的的报表，例如销售订单、产品目录或套用信函。 所有这些报表都是通过在报表生成器中使用相同基本构建基块的不同组合来创建的。 要创建有用且易于理解的报表，先进行规划会很有帮助。 在开始之前，可能需要考虑以下事项：  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>希望报表以何种格式显示？
  
可以在 Power BI 门户等浏览器中联机呈现报表，也可以将其导出为 Excel、Word 或 PDF 等其他格式。 报表的最终格式是一个重要的考虑因素，因为有些导出格式不支持某些功能。 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>要以哪种结构呈现数据？
  
可以选择表格、矩阵（类似于交叉表或数据透视表报表）、图表、自由格式结构或这些结构的任意组合来呈现数据。 有关详细信息，请参阅 [Power BI 报表生成器中的表、矩阵和列表](report-builder-tables-matrices-lists.md)。  
  
## <a name="how-do-you-want-your-report-to-look"></a>希望报表呈现哪种外观？
  
报表生成器提供了许多报表项，可以将其添加到报表中，以便于受众阅读、突出显示重要信息、帮助受众浏览报表等。 了解自己想以哪种方式显示报表，便可确定是否需要文本框、矩形、图像和线条等报表项。 可能会需要显示或隐藏某些项、添加文档结构图，包括钻取报表或子报表，或链接到其他报表。   
  
## <a name="should-the-data-be-filtered"></a>应对数据进行筛选吗？
  
可能会需要将报表的范围限定到特定用户或位置，或特定时间段。 要筛选报表数据，请使用参数来检索并仅显示所需数据。 有关详细信息，请参阅 [Power BI 报表生成器中的报表参数](paginated-reports-parameters.md)。  
  
## <a name="do-you-need-to-create-calculations"></a>需要创建计算吗？ 
  
有时，数据源和数据集不包含报表需要的确切字段。 在这种情况下，可能需要创建自己的计算字段。 例如，可能要将单位价格乘以数量以获得行项销售金额。 还会使用表达式提供条件格式设置和其他高级功能。 有关详细信息，请参阅 [Power BI 报表生成器中的报表参数](report-builder-expressions.md)。  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>需要在一开始隐藏报表项吗？
  
请考虑是否要在首次运行报表时隐藏报表项，包括数据区域、组和列。 例如，最开始可以显示摘要表，然后通过向下钻取获取详细数据。 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>计划如何交付报表？  
  
可以将报表保存到本地计算机并继续处理它，或在本地运行它以获取自己的信息。 但是，若要与其他人共享报表，需要将报表保存到 Power BI。 通过将它保存到 Power BI，其他人可以在每次需要时运行它。 或者，可以设置订阅并将报表交付通过电子邮件发送给其他个人。 可以根据需要以特定导出格式交付报表。 
  
## <a name="next-steps"></a>后续步骤

- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)

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
ms.openlocfilehash: 3f075372436723cd8952decd68ecc764bd6e92a0
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297725"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>在 Power BI 报表生成器中规划报表

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

利用 Power BI Report Builder 可创建多种类型的分页报表。 例如，可以创建显示摘要或详细销售数据、营销和销售趋势的报表、操作报表或面板。 还可以为销售订单、产品目录或套用信函等创建利用丰富格式文本的报表。 所有这些报表都是在报表生成器中使用相同基本构造块的不同组合创建的。 若要创建有用且易于理解的报表，报表生成器可帮助首先进行规划。 开始创建报表之前最好考虑以下几个问题：  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>希望报表以何种格式显示？
  
可以在 Power BI 门户等浏览器中联机呈现报表，也可以将其导出为 Excel、Word 或 PDF 等其他格式。 报表采用的最终格式是需要考虑的重要因素，因为并非所有功能在所有导出格式中都可用。 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>要以哪种结构呈现数据？
  
您可以选择表格、矩阵（类似于交叉表或数据透视表）、图表、自由格式结构或以上几种结构的任意组合来呈现数据。 有关详细信息，请参阅 [Power BI 报表生成器中的表、矩阵和列表](report-builder-tables-matrices-lists.md)。  
  
## <a name="how-do-you-want-your-report-to-look"></a>希望报表呈现哪种外观？
  
报表生成器提供了许多报表项，您可以将其添加到报表中以使报表更易于阅读、突出显示关键信息、帮助用户导航报表等。 了解要如何显示报表才能确定是否需要文本框、矩形、图像和线条等报表项。 您还可能希望显示或隐藏项，添加文档结构图（包括钻取报表或子报表），或者链接到其他报表。   
  
## <a name="should-the-data-be-filtered"></a>应对数据进行筛选吗？
  
您可能希望将报表范围缩小到特定用户或位置，或者缩小到特定时间段。 若要筛选报表数据，请使用参数来检索并只显示所需的数据。 有关详细信息，请参阅 [Power BI 报表生成器中的报表参数](paginated-reports-parameters.md)。  
  
## <a name="do-you-need-to-create-calculations"></a>需要创建计算吗？ 
  
有时，数据源和数据集不包含报表需要的确切字段。 在这种情况下，您可能需要创建自己的计算字段。 例如，您可能要以单价乘以数量来获得行项的销售金额。 表达式还用于提供条件格式和其他高级功能。 有关详细信息，请参阅 [Power BI 报表生成器中的报表参数](report-builder-expressions.md)。  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>最初是否要隐藏报表项？
  
首次运行报表时，可考虑是否要隐藏报表项（包括数据区域、组和列）。 例如，最初可以呈现摘要表，然后深化到详细数据。 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>打算如何传递报表？  
  
您可以将报表保存到本地计算机，并继续在本地使用它或运行它，供自己参考。 但是，若要与其他人共享报表，需要将报表保存到 Power BI。 通过将它保存到 Power BI，其他人可以在每次需要时运行它。 或者，可以设置订阅并将报表交付通过电子邮件发送给其他个人。 您可以根据需要以特定导出格式传递报表。 
  
## <a name="next-steps"></a>后续步骤

- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)

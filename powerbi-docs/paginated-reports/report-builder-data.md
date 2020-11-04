---
title: Power BI 报表生成器中的报表数据
description: 在 Power BI Report Builder 中设计报表的第一步是创建表示基础报表数据的数据源和数据集。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 08/04/2020
ms.openlocfilehash: 97b93f23c8070af1b514032cea122b257097d664
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297932"
---
# <a name="report-data-in-power-bi-report-builder"></a>Power BI 报表生成器中的报表数据

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

报表数据可以来自组织中的多个数据源。 设计 Power BI 报表生成器报表的第一步是创建表示基础报表数据的数据源和数据集。 每个数据源都包含数据连接信息。 每个数据集都包含一个查询命令，用于定义要用作数据源数据的字段集。 要可视化每个数据集中的数据，请添加表、矩阵、图表或地图等数据区域。 处理报表时，将对数据源运行查询，并且每个数据区域都可以根据需要进行扩展，以便显示数据集的查询结果。  

了解如何[在 Power BI 报表生成器中为分页报表创建嵌入数据源](paginated-reports-embedded-data-source.md)。


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> 术语  
  
- **数据连接。** 也称为数据源  。 数据连接包括一个名称和取决于连接类型的连接属性。 数据连接设计为不包括凭证。 数据连接不指定要从外部数据源检索的数据。 为此，请在创建数据集时指定查询。  
  
- **连接字符串。** 连接字符串是连接到数据源所需的连接属性的字符串版本。 连接属性因数据连接类型而异。 

    > [!NOTE]
    > 数据源连接字符串不能基于表达式。
  
- **嵌入数据源。** 也称为 *特定于报表的数据源* 。 在报表中定义并只由该报表使用的数据源。  
  
- **凭据。** 凭据是身份验证信息，你必须提供这些信息才能访问外部数据。  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> 关于指定报表数据的提示

 使用以下信息可以设计您的报表数据策略。  
  
- **筛选数据** 可以在查询中或报表中筛选报表数据。 您可以使用数据集和查询变量来创建级联参数，并且使用户能够将成千上万种选择缩减为更为可控的数目。 您可以基于参数值或者您指定的其他值来筛选表或图表中的数据。  
  
- **参数** 包含查询变量的数据集查询命令将自动创建匹配的报表参数。 也可以手动创建参数。 当您查看报表时，报表工具栏将显示这些参数。 用户可以选择值，以便控制报表数据或报表外观。 若要为特定用户自定义报表数据，可以创建具有链接到相同报表定义的不同默认值的报表参数集，或者使用内置的 **UserID** 字段。 
  
- **对数据进行分组和聚合** 可在查询或报表中对报表数据进行分组和聚合。 如果您聚合查询中的值，则可以继续在有意义的约束内合并报表中的值。  
  
- **对数据排序** 可以在查询中或报表中对报表数据排序。 在表中，您还可以添加交互排序按钮，以便让用户控制排序顺序。  
  
- **基于表达式的数据** 因为大多数报表属性可以是基于表达式的，并且表达式可以包含对数据集字段和报表参数的引用，所以，可以编写功能强大的表达式来控制报表数据和外观。 您可以通过定义参数，使用户能够控制其所看到的数据。  
  
- **显示来自一个数据集的数据** 来自一个数据集的数据通常显示在一个或多个数据区域中，例如表和图表。  
  
- **显示来自多个数据集的数据**  可以在数据区域中基于一个数据集编写表达式，用于查找其他数据集中的值或聚合。 您可以基于一个数据集在表中包含子报表，以便显示来自其他数据源的数据。  
  
 使用以下列表可帮助定义报表的数据源。  
  
- 了解您的组织的软件数据层体系结构以及从数据类型导致的潜在问题。 了解数据扩展插件和数据处理扩展插件是如何影响查询结果的。 数据类型在数据源、数据访问接口以及在报表定义 (.rdl) 文件中存储的数据类型之间是不同的。  
  
- 数据源和数据集在报表中创作并发布到 Power BI 服务。 发布后，可以直接在 Power BI 服务或 Enterprise 网关中配置凭据。 

## <a name="next-steps"></a>后续步骤

- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)  
- [分页报表的数据检索指南](../guidance/report-paginated-data-retrieval.md)

---
title: 在分页报表中使用级联参数
description: 使用级联参数设计分页报表的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 35a62923ba69520c1197e7bb80114a22ec1d9a20
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214085"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>在分页报表中使用级联参数

本文面向设计 Power BI [分页报表](../paginated-reports/paginated-reports-report-builder-power-bi.md)的报表作者。 提供用于设计级联参数的方案。 级联参数是具有依赖关系的报表参数。 当报表用户选择某个参数值（或多个值）时，可使用它为另一个参数设置可用值。

> [!NOTE]
> 级联参数的介绍及其配置不在本文涵盖范围内。 如果你不完全了解级联参数，建议先阅读[将级联参数添加到报表（报表生成器和 SSRS）](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)。

## <a name="design-scenarios"></a>设计方案

有两种使用级联参数的设计方案。 它们可以有效地用于：

- 筛选大量项
- 显示相关项

### <a name="example-database"></a>示例数据库

本文中介绍的示例基于一个 Azure SQL 数据库。 该数据库记录销售运营信息，并包含用于存储经销商、产品和销售订单的各种表。

名称为 Reseller 的表为每个经销商存储一条记录，共包含数千条记录。 Reseller 表包含以下列：

- ResellerCode（整数）
- ResellerName
- 国家/地区
- 省/市/自治区
- 城市
- 邮政编码

还有一个名为 Sales 的表。 它存储销售订单记录，在 ResellerCode 列上与 Reseller 表之间具有外键关系。

### <a name="example-requirement"></a>示例要求

需要开发经销商个人资料报表。 该报表必须设计为显示单个经销商的信息。 让报表用户输入经销商代码是不合适的，因为他们很少记住这些代码。

## <a name="filter-large-sets-of-items"></a>筛选大量项

我们来看看三个示例，帮助你限制大量可用项，例如经销商。 它们分别是：

- [按相关列筛选](#filter-by-related-columns)
- [按分组列筛选](#filter-by-a-grouping-column)
- [按搜索模式筛选](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>按相关列筛选

在本示例中，报表用户与五个报表参数交互。 他们必须选择“国家/地区”、“省/市/自治区”、“城市”和“邮政编码”。 最后一个参数会列出位于该地理位置的经销商。

![Power BI 分页报表参数的屏幕截图，其中显示了“按相关列筛选”。](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

下面介绍了如何开发级联参数：

1. 创建五个报表参数，并按正确的顺序排列。
2. 使用以下查询语句，创建用于检索不同国家/地区值的 CountryRegion 数据集：

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. 使用以下查询语句创建用于检索所选国家/地区的不同省/市/自治区值的 StateProvince 数据集：

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. 使用以下查询语句创建用于检索所选国家/地区和省/市/自治区的不同城市值的 City 数据集：

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. 按同样的方法创建 PostalCode 数据集。
6. 使用以下查询语句，创建用于检索所选地理位置值的所有经销商的 Reseller 数据集：

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. 对于除第一个数据集之外的每个数据集，请将查询参数映射到相应的报表参数。

> [!NOTE]
> 这些示例中所示的所有查询参数（以 @ 符号为前缀）都可以嵌入 SELECT 语句或传递给存储过程。
>
> 通常，存储过程是一种更好的设计方法。 这是因为它们的查询计划会进行缓存以实现更快的执行，这样你就可以在需要时开发更复杂的逻辑。 但是，它们目前不支持用于网关关系数据源（即 SQL Server、Oracle 和 Teradata）。
>
> 最后，应始终确保存在适合的索引，以实现高效的数据检索。 否则，报表参数的填充速度可能会很慢，并且数据库可能会出现过载情况。 有关 SQL Server 索引的详细信息，请参阅 [SQL Server 索引体系结构和设计指南](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017)。

### <a name="filter-by-a-grouping-column"></a>按分组列筛选

在本示例中，报表用户与报表参数交互，以选择经销商的第一个字母。 然后，当名称以所选字母开头时，第二个参数会列出经销商。

![Power BI 分页报表参数的屏幕截图，其中显示了“按分组列筛选”。](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

下面介绍了如何开发级联参数：

1. 创建 ReportGroup 和 Reseller 报表参数，并按正确的顺序排列。
2. 使用以下查询语句，创建用于检索所有经销商使用的第一个字母的 ReportGroup 数据集：

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. 使用以下查询语句，创建用于检索以所选字母开头的所有经销商的 Reseller 数据集：

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. 将 Reseller 数据集的查询参数映射到相应的报表参数。

将分组列添加到 Reseller 表中会更高效。 经过持久化和索引后，它将提供最佳结果。 有关详细信息，请参阅 [Specify Computed Columns in a Table](/sql/relational-databases/tables/specify-computed-columns-in-a-table)。

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

这种技术可以发挥更大的潜力。 请考虑使用下面的脚本，该脚本添加了一个新的分组列，以便按预定义的字母组合来筛选经销商。 它还创建索引以有效地检索报表参数所需的数据。

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>按搜索模式筛选

在本示例中，报表用户与报表参数交互，以输入搜索模式。 然后，当名称包含该模式时，第二个参数会列出经销商。

![Power BI 分页报表参数的屏幕截图，其中显示了“按搜索模式筛选”。](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

下面介绍了如何开发级联参数：

1. 创建 Search 和 Reseller 报表参数，并按正确的顺序排列。
2. 使用以下查询语句，创建用于检索包含搜索文本的所有经销商的 Reseller 数据集：

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. 将 Reseller 数据集的查询参数映射到相应的报表参数。

> [!TIP]
> 可以根据此设计进行改进，为报表用户提供更多的控制。 用户可以定义自己的模式匹配值。 例如，搜索值“red%”将筛选出名称以“red”字符开头的经销商。
>
> 有关详细信息，请参阅 [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character)。

下面介绍了如何让报表用户定义自己的模式。

```sql
WHERE
  [ResellerName] LIKE @Search
```

但是，许多非数据库专业人员都不知道百分比 (%) 通配符。 相反，它们熟悉星号 (*) 字符。 通过修改 WHERE 子句，可以让他们使用此字符。

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>显示相关项

在此方案中，可以使用事实数据来限制可用值。 报表用户将看到已记录活动的项。

在本示例中，报表用户与三个报表参数交互。 前两个参数设置了销售订单日期的日期范围。 然后，第三个参数列出在该时间段内已创建其订单的经销商。

![Power BI 分页报表参数的屏幕截图，其中显示了三个报表参数：“订单开始日期”、“订单结束日期”和“经销商”。](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

下面介绍了如何开发级联参数：

1. 创建 OrderDateStart、OrderDateEnd 和 Reseller  报表参数，并按正确的顺序排列。
2. 使用以下查询语句，创建用于检索已在日期范围内创建订单的所有经销商的 Reseller 数据集：

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>建议

建议尽可能使用级联参数设计报表。 这是因为它们：

- 可以为你的报表用户提供直观且有用的体验
- 非常高效，因为它们检索较小的可用值集

请确保通过以下方式优化数据源：

- 尽可能使用存储过程
- 添加适当的索引以实现高效数据检索
- 具体化列值（甚至是行）以避免成本高昂的查询时间评估

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI 报表生成器中的报表参数](../paginated-reports/report-builder-parameters.md)
- [向报表添加级联参数（报表生成器和 SSRS）](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)

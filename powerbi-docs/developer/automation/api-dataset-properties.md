---
title: Power BI 嵌入式分析中用于增强嵌入式 BI 见解的 Power BI 数据集属性
description: 了解 Power BI 数据集 API 的属性。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b4bd173c2f3730a0a6082214afbfdf5760048102
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887675"
---
# <a name="dataset-properties"></a>数据集属性

当前版本 1 的数据集 API 仅允许使用一个名称和一个表集合创建的数据集。 每个表可以具有一个名称和一个列集合。 每个列具有一个名称和数据类型。 我们主要通过对度量值和表格间的关系的支持来极大地扩展这些属性。 此版本受支持的属性的完整列表如下：

> [!IMPORTANT]
> 可从[数据集操作组](/rest/api/power-bi/datasets)页进行访问。

## <a name="dataset"></a>数据集

名称  |类型  |说明  |只读  |必需
---------|---------|---------|---------|---------
id     |  Guid       | 数据集系统范围内的唯一标识符。        | 正确        | 错误        
name     | 字符串        | 用户定义的数据集的名称。        | False        | True        
表     | Table[]        | 表的集合。        |  False       | False        
关系     | Relationship[]        | 表之间的关系的集合。        | False        |  False  
defaultMode     | 字符串        | 确定是否使用“Push”和“Streaming”的值推送、流式处理或既推送又流式处理数据集。         | False        |  False

## <a name="table"></a>表

名称  |类型  |说明  |只读  |必需
---------|---------|---------|---------|---------
name     | 字符串        |  用户定义的表的名称。 还可用作该表的标识符。       | False        |  True       
列     |  column[]       |  列的集合。       | False        |  True       
度量值     | measure[]        |  度量值的集合。       | False        |  False       
isHidden     | 布尔        | 如果为 True，表将从客户端工具中隐藏。        | False        | False        

## <a name="column"></a>列

名称  |类型  |说明  |只读  |必需
---------|---------|---------|---------|---------
name     |  字符串        | 用户定义的列的名称。        |  False       | True       
dataType     |  字符串       |  受支持的 [EDM 数据类型](/dotnet/framework/data/adonet/entity-data-model-primitive-data-types)(#edm-数据类型) 和限制。 请参阅 [数据类型限制](#data-type-restrictions)(#数据类型限制)。      |  False       | True        
formatString     | 字符串        | 描述如何在显示值时对值进行格式化。 若要了解字符串格式化的详细信息，请参阅 [FORMAT_STRING 内容](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents)(#format_string-内容)。      | False        | False        
sortByColumn    | 字符串        |   在同一个表中用于排序当前列的某一列的字符串名称。     | False        | False       
dataCategory     | 字符串        |  用于描述了该列中数据的数据类别的字符串值。 一些公用值包括：Address、City、Continent、Country、Image、ImageUrl、Latitude、Longitude、Organization、Place、PostalCode、StateOrProvince、WebUrl       |  False       | False        
isHidden    |  布尔       |  指示视图中是否隐藏该列的属性。 默认值为 false。       | False        | False        
summarizeBy     | 字符串        |  列的默认聚合方法。 值包括：default、none、sum、min、max、count、average、distinctCount     |  False       | False

## <a name="measure"></a>度量值

名称  |类型  |说明  |只读  |必需
---------|---------|---------|---------|---------
name     | 字符串        |  用户定义的度量值的名称。       |  False       | True        
表达式     | 字符串        | 有效的 DAX 表达式。        | False        |  True       
formatString     | 字符串        |  描述如何在显示值时对值进行格式化。 若要了解字符串格式化的详细信息，请参阅 [FORMAT_STRING 内容](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents)(#format_string-内容)。       | False        | False        
isHidden     | 字符串        |  如果为 True，表将从客户端工具中隐藏。       |  False       | False       

## <a name="relationship"></a>Relationship

名称  |类型  |说明  |只读  |必需 
---------|---------|---------|---------|---------
name     | 字符串        | 用户定义的关系的名称。 还可用作该关系的标识符。        | False       | True        
crossFilteringBehavior     | 字符串        |    关系的筛选方向：OneDirection（默认）、BothDirections、Automatic       | False        | False        
fromTable     | 字符串        | 外键表的名称。        | False        | True         
fromColumn    | 字符串        | 外键列的名称。        | False        | True         
toTable    | 字符串        | 主键表的名称。        | False        | True         
toColumn     | 字符串        | 主键列的名称。        | False        | True        

## <a name="data-type-restrictions"></a>数据类型限制

这些限制适用于 dataType 属性。

数据类型  |限制  
---------|---------
Int64     |   不允许使用 Int64.MaxValue 和 Int64.MinValue。      
Double     |  不允许使用 Double.MaxValue 和 Double.MinValue 值。 NaN 某些函数（例如 Min、Max）中不支持使用正无穷和负无穷。       
布尔     |   判断正误。
datetime    |   在数据加载期间，我们将不足一天的值量化为 1/300 秒（3.33 毫秒）的整数倍。      
字符串     |  目前允许每个字符串值最多 4000 个字符。
小数|精度 = 28，小数位数 = 4

## <a name="example"></a>示例
以下代码示例包括以下多个属性：

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```
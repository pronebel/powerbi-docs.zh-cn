---
title: 视觉对象筛选器 API
description: Power BI 视觉对象如何筛选其他视觉对象
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425036"
---
# <a name="power-bi-visual-filters-api"></a>Power BI 视觉对象筛选器 API

视觉对象筛选器可以筛选数据。 它与选择的主要区别是可通过任意方式筛选其他视觉对象，尽管其他视觉对象支持突出显示。

若要对此视觉对象启用筛选，该视觉对象应在 capabilities.json 内容的 `general` 部分中包含有 `filter` 对象。

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

[`powerbi-models`](https://www.npmjs.com/package/powerbi-models) 包中提供有筛选器 API 接口。 该包还包含用于创建筛选器实例的类。

```cmd
npm install powerbi-models --save
```

如果使用旧版工具（低于 3.x.x 的版本），应将 `powerbi-models` 包含在视觉对象包中。 [有关如何添加包的简短指南](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

所有筛选器都会扩展 `IFilter` 接口。

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` - 数据源中的表列。

## <a name="basic-filter-api"></a>基本筛选器 API

基本筛选器接口如下

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` - 值为“In”、“NotIn”或“All”的枚举

`values` - 条件值

基本筛选器示例：

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

此筛选器表示“显示 `col1` 等于 1、2 或 3 的所有行”。

SQL 等效项为

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

要创建筛选器，可以使用 `powerbi-models` 中的 BasicFilter 类。

如果使用旧版工具，应通过 `window['powerbi-models']` 在窗口对象中获得模型实例：

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

该视觉对象通过对为构造函数中的视觉对象提供的主机接口 IVisualHost 应用 applyJsonFilter() 方法来调用筛选器。

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>高级筛选器 API

[高级筛选器 API](https://github.com/Microsoft/powerbi-models) 支持基于多条件（例如“LessThan”、“Contains”、“Is”和“IsBlank”）的跨视觉对象数据点的复杂选择/筛选查询。

视觉对象 API 1.7.0 中引入了此筛选器。

高级筛选器 API 还需要含 `table` 和 `column` 名称的 `target`。 但高级筛选器 API 运算符为 `"And" | "Or"`。 

此外，该筛选器在接口中使用条件而不是值：

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

`operator` 参数的条件运算符为 `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

SQL 等效项为

```sql
SELECT * FROM table WHERE col1 < 0;
```

有关使用高级筛选器 API 的完整示例代码可在[`Sampleslicer visual`存储库](https://github.com/Microsoft/powerbi-visuals-sampleslicer)中找到。

## <a name="tuple-filter-api-multi-column-filter"></a>元组筛选器 API（多列筛选器）

视觉对象 API 2.3.0 中引入了元组筛选器 API。

元组筛选器 API 类似于基本筛选器，但它允许为多个列和表定义条件。

筛选器具有接口： 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` 是由含有表名的列构成的数组：

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  筛选器可以处理来自不同表的列。

`$schema` 为“http://powerbi.com/product/schema#tuple”

`filterType` 为 `FilterType.Tuple`

`operator` 仅允许使用 `"In"` 运算符

`values` 是由值元组构成的数组，其中每个元组表示一个允许的目标列值组合 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

完整示例：

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**列名称的顺序和条件的值至关重要。**

SQL 等效项为

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>从数据视图还原 JSON 筛选器

从 API 2.2 开始，可以从 VisualUpdateOptions 还原 JSON 筛选器  

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

使用开关书签且视觉对象获取对应的 `filter` 对象时，Power BI 调用视觉对象的 `update` 方法。
[详细了解书签支持](bookmarks-support.md)

### <a name="sample-json-filter"></a>示例 JSON 筛选器

![JSON 筛选器屏幕截图](./media/json-filter.png)

### <a name="clear-json-filter"></a>清除 JSON 筛选器

进行重置或清除操作时，筛选器 API 接受筛选器的 `null` 值。

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```

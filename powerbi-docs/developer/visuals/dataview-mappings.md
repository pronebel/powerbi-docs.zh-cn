---
title: 数据视图映射
description: Power BI 如何在将数据传递给视觉对象之前转换数据
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ff70b2f12921694617a736164484df1326471eea
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425174"
---
# <a name="data-view-mappings-in-power-bi-visuals"></a>Power BI 视觉对象中的数据视图映射

`dataViewMappings` 描述数据角色如何彼此相关，并允许你为它们指定条件要求。
每个 `dataMappings` 都有一个部分。

每个有效映射都将生成 `DataView`，但目前仅支持对每个视觉对象执行一个查询，因此在大多数情况下，只能获取一个 `DataView`。 但是，可以提供多个设有不同条件的数据映射，这允许

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "single": { ... },
        "table": { ... },
        "matrix": { ... }
    }
]
```

> [!NOTE]
> 需要注意的是，当且仅当在 `dataViewMappings` 中填充了有效映射时，Power BI 才会创建到 DataView 的映射。

换句话说，如果 `dataViewMappings` 中定义了 `categorical`，但没有定义 `table`、`single` 等其他映射，如以下示例中所示：
```json
"dataViewMappings": [
    {
        "categorical": { ... }
    }
]
```

Power BI 将生成一个 `DataView`，其中具有单个 `categorical` 映射（`table` 和其他映射将为 `undefined`）：
```javascript
{
    "categorical": {
        "categories": [ ... ],
        "values": [ ... ]
    },
    "metadata": { ... }
}
```

## <a name="conditions"></a>条件

描述特定数据映射的条件。 可以提供多组条件，如果数据与所述的一组条件相匹配，则视觉对象会将数据作为有效数据来接受。

目前，对于每个字段，可以指定最小值和最大值。 它表示可以绑定到该数据角色的字段数。 

> [!NOTE]
> 如果条件中省略了数据角色，那么可以绑定任意数量的字段。

### <a name="example-1"></a>示例 1

可以将多个字段拖入每个数据角色。 在此示例中，类别限一个数据字段，度量值限两个数据字段。

```json
"conditions": [
    { "category": { "max": 1 }, "y": { "max": 2 } },
]
```

### <a name="example-2"></a>示例 2

在此示例中，需要满足以下两个条件之一。 有一个类别数据字段和两个度量值，或者两个类别和一个度量值。

```json
"conditions": [
    { "category": { "min": 1, "max": 1 }, "measure": { "min": 2, "max": 2 } },
    { "category": { "min": 2, "max": 2 }, "measure": { "min": 1, "max": 1 } }
]
```

## <a name="single-data-mapping"></a>单个数据映射

单个数据映射是数据映射的最简单形式。 它接受单个度量值字段并提供总计。 如果该字段为数值字段，则它将提供总和。 否则，它将提供非重复值的计数。

若要使用单个数据映射，需要定义要映射的数据角色的名称。 此映射仅适用于单个度量值字段。 如果分配了第二个字段，则不会生成任何数据视图。 因此，包括一个将数据限制为单个字段的条件也是一种很好的做法。

> [!NOTE]
> 此数据映射不能与任何其他数据映射结合使用。 它旨在将数据限制为单个数值。

### <a name="example-3"></a>示例 3

```json
"dataViewMappings": {
    "conditions": [
        { "Y": { "max": 1 } }
    ],
    "single": {
        "role": "Y"
    }
}  
```

生成的数据视图仍将包含其他类型（表、类别等），但每个映射将只包含单个值。 最佳做法是只访问单个值。

```JSON
{
    "dataView": [
        {
            "metadata": null,
            "categorical": null,
            "matrix": null,
            "table": null,
            "tree": null,
            "single": {
                "value": 94163140.3560001
            }
        }
    ]
}
```

## <a name="categorical-data-mapping"></a>类别数据映射

类别数据映射用于获取一个或两个独立的数据组别。

### <a name="example-4"></a>示例 4

下面是之前 DataRole 示例中的定义。

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    }
]
```

现在，对于映射：

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "select": [
                { "bind": { "to": "measure" } }
            ]
        }
    }
}
```

这是一个简单的示例，内容是“映射我的 `category` DataRole，以便我拖入 `category` 的每个字段的数据都映射到 `categorical.categories`。 同时将 `measure` DataRole 映射到 `categorical.values`”。

* **for...in** - 对于此数据角色中的所有项，将它们包含在数据查询中。
* **bind...to** - 生成与 for...in 相同的结果，但预期 DataRole 具有将其限制为单个字段的条件。

### <a name="example-5"></a>示例 5

在此示例中，我们将使用前面示例中的前两个 DataRole，另外定义 `grouping` 和 `measure2`。

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Grouping with",
        "name": "grouping",
        "kind": "Grouping"
    },
    {
        "displayName": "X Axis",
        "name": "measure2",
        "kind": "Grouping"
    }
]
```

现在，对于映射：

```json
"dataViewMappings":{
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "group": {
                "by": "grouping",
                "select":[
                    { "bind": { "to": "measure" } },
                    { "bind": { "to": "measure2" } }
                ]
            }
        }
    }
}
```

此处的差别在于映射类别值的方式。 现在内容是“映射我的 `measure` 和 `measure2` 数据角色，以按照数据角色 `grouping` 进行分组”。

### <a name="example-6"></a>示例 6

下面是 dataRole。

```json
"dataRoles": [
    {
        "displayName": "Categories",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measures",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Series",
        "name": "series",
        "kind": "Measure"
    }
]
```

下面是 dataViewMapping。

```json
"dataViewMappings": [
    {
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "group": {
                    "by": "series",
                    "select": [{
                            "for": {
                                "in": "measure"
                            }
                        }
                    ]
                }
            }
        }
    }
]
```

类别 `dataview` 可进行可视化，如下所示。

| 分类 |  |  | | | |
|-----|-----|------|------|------|------|
| | 年份 | 2013 | 2014 | 2015 | 2016 |
| 国家/地区 | | |
| 美国 | | x | x | 125 | 100 |
| 加拿大 | | x | 50 | 200 | x |
| 墨西哥 | | 300 | x | x | x |
| 英国 | | x | x | 75 | x |

Power BI 会将其生成为类别数据视图。 这是一组类别。

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "Mexico",
                    "UK",
                    "USA"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

每个类别也会映射到一组值。 其中每个值都按系列（即年份）归组。

例如，2013 年加拿大销售额为 null，2014 年加拿大销售额为 50。

```JSON
{
    "values": [
        {
            "source": {...},
            "values": [
                null,
                300,
                null,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                50,
                null,
                150,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                200,
                null,
                null,
                125
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                null,
                null,
                null,
                100
            ],
            "identity": [...],
        }
    ]
}
```

## <a name="table-data-mapping"></a>表数据映射

表数据视图是一种简单的数据映射。 实质上，它是数据点的列表，可在其中聚合数值数据点。

### <a name="example-7"></a>示例 7

如果给定功能：

```json
"dataRoles": [
    {
        "displayName": "Values",
        "name": "values",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                }
            }
        }
    }
]
```

表 `dataview` 可进行可视化，如下所示。  

| 国家/地区| 年份 | 销售 |
|-----|-----|------|
| 美国 | 2016 | 100 |
| 美国 | 2015 | 50 |
| 加拿大 | 2015 | 200 |
| 加拿大 | 2015 | 50 |
| 墨西哥 | 2013 | 300 |
| 英国 | 2014 | 150 |
| 美国 | 2015 | 75 |

Power BI 将生成表数据视图。 不要以为存在排序。

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                50
            ],
            [
                "Canada",
                2015,
                200
            ],
            [
                "Mexico",
                2013,
                300
            ],
            [
                "UK",
                2014,
                150
            ],
            [
                "USA",
                2015,
                100
            ],
            [
                "USA",
                2015,
                75
            ],
            [
                "USA",
                2016,
                100
            ]
        ]
    }
}
```

可以通过选择所需字段并单击总和来聚合数据。  

![数据聚合](./media/data-aggregation.png)

## <a name="matrix-data-mapping"></a>矩阵数据映射

矩阵数据映射与表数据映射类似，但前者按层次结构显示行。 其中一个 `dataRole` 值可用作列标题值。

```json
{
    "dataRoles": [
        {
            "name": "Category",
            "displayName": "Category",
            "displayNameKey": "Visual_Category",
            "kind": "Grouping"
        },
        {
            "name": "Column",
            "displayName": "Column",
            "displayNameKey": "Visual_Column",
            "kind": "Grouping"
        },
        {
            "name": "Measure",
            "displayName": "Measure",
            "displayNameKey": "Visual_Values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "rows": {
                    "for": {
                        "in": "Category"
                    }
                },
                "columns": {
                    "for": {
                        "in": "Column"
                    }
                },
                "values": {
                    "select": [
                        {
                            "for": {
                                "in": "Measure"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

Power BI 创建分层数据结构。 树的根包含 `Category` 数据角色第一列中的数据和数据角色第二列中的子级。

数据集：

| 父级 | 子级 | 孙级 | 列 | 值 |
|-----|-----|------|-------|-------|
| Parent1 | Child1 | Grand child1 | Col1 | 5 |
| Parent1 | Child1 | Grand child1 | Col2 | 6 |
| Parent1 | Child1 | Grand child2 | Col1 | 7 |
| Parent1 | Child1 | Grand child2 | Col2 | 8 |
| Parent1 | Child2 | Grand child3 | Col1 | 5 |
| Parent1 | Child2 | Grand child3 | Col2 | 3 |
| Parent1 | Child2 | Grand child4 | Col1 | 4 |
| Parent1 | Child2 | Grand child4 | Col2 | 9 |
| Parent1 | Child2 | Grand child5 | Col1 | 3 |
| Parent1 | Child2 | Grand child5 | Col2 | 5 |
| Parent2 | Child3 | Grand child6 | Col1 | 1 |
| Parent2 | Child3 | Grand child6 | Col2 | 2 |
| Parent2 | Child3 | Grand child7 | Col1 | 7 |
| Parent2 | Child3 | Grand child7 | Col2 | 1 |
| Parent2 | Child3 | Grand child8 | Col1 | 10 |
| Parent2 | Child3 | Grand child8 | Col2 | 13 |

Power BI 的核心矩阵视觉对象将其呈现为表。

![矩阵视觉对象](./media/matrix-visual-smaple.png)

视觉对象如下所述获取数据结构（仅显示前两行）：

```json
{
    "metadata": {...},
    "matrix": {
        "rows": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Parent1",
                        "identity": {...},
                        "childIdentityFields": [...],
                        "children": [
                            {
                                "level": 1,
                                "levelValues": [...],
                                "value": "Child1",
                                "identity": {...},
                                "childIdentityFields": [...],
                                "children": [
                                    {
                                        "level": 2,
                                        "levelValues": [...],
                                        "value": "Grand child1",
                                        "identity": {...},
                                        "values": {
                                            "0": {
                                                "value": 5 // value for Col1
                                            },
                                            "1": {
                                                "value": 6 // value for Col2
                                            }
                                        }
                                    },
                                    ...
                                ]
                            },
                            ...
                        ]
                    },
                    ...
                ]
            }
        },
        "columns": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col1",
                        "identity": {...}
                    },
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col2",
                        "identity": {...}
                    },
                    ...
                ]
            }
        },
        "valueSources": [...]
    }
}
```

## <a name="data-reduction-algorithm"></a>数据缩减算法

如果要控制 DataView 中接收到的数据量，可以应用 `DataReductionAlgorithm`。

默认情况下，所有自定义视觉对象都应用了顶级 DataReductionAlgorithm，并将“count”设置为 1000 个数据点。 这相当于在 capabilities.json 中设置了以下属性：

```json
"dataReductionAlgorithm": {
    "top": {
        "count": 1000
    }
}
```

可以将“count”值修改为不超过 30000 的任何整数值。 基于 R 的自定义视觉对象最多可支持 150000 行。

## <a name="data-reduction-algorithm-types"></a>数据缩减算法类型

有四种类型的 `DataReductionAlgorithm` 设置：

* `top` - 如果要将数据限制为从数据集顶部获取的值。 将从数据集中获取顶部第一个“count”值。
* `bottom` - 如果要将数据限制为从数据集底部获取的值。 将从数据集中获取最后一个“count”值。
* `sample` - 通过一个简单采样算法来限制数据集，该方法将项数限制为“count”的数量。 它意味着包含第一项和最后一项，以及具有相等间隔的一组“count”数量的项。
例如，如果你有一个数据集 [0, 1, 2, ...100] 和 `count: 9`，那么你将接收到以下值 [0, 10, 20 ...100]
* `window` - 一次加载一个“窗口”的数据点，其中包含“count”元素。 当前 `top` 和 `window` 等效。 正在运行的工作可完全支持窗口化设置。

## <a name="data-reduction-algorithm-usage"></a>数据缩减算法使用情况

`DataReductionAlgorithm` 可在类别、表或矩阵 `dataview` 映射中使用。

可以将其设置为 `categories` 和/或 `values` 的组部分，用于类别数据映射。

### <a name="example-8"></a>示例 8

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" },
            "dataReductionAlgorithm": {
                "window": {
                    "count": 300
                }
            }  
        },
        "values": {
            "group": {
                "by": "series",
                "select": [{
                        "for": {
                            "in": "measure"
                        }
                    }
                ],
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 100
                    }
                }  
            }
        }
    }
}
```

数据缩减算法可应用于表 `dataview` 映射的 `rows` 部分。

### <a name="example-9"></a>示例 9

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 2000
                    }
                } 
            }
        }
    }
]
```

数据缩减算法可应用于 `rows` 和/或 `matrix` `dataview` 映射的 `columns` 部分。

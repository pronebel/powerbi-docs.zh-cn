---
title: 功能
description: Power BI 视觉对象功能和属性
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425450"
---
# <a name="power-bi-visual-capabilities"></a>Power BI 视觉对象功能

功能向主机提供有关视觉对象的信息。 功能模型上的所有属性都是 `optional`

视觉对象功能的根对象是 `dataRoles`、`dataViewMappings` 等。

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>定义视觉对象所需的数据字段 - `dataRoles`

为了定义可绑定到数据的字段，我们使用采用 `DataViewRole` 对象数组的 `dataRoles`，这些对象定义了所有所需属性。

### <a name="properties"></a>属性

* **name** - 此数据字段的内部名称（必须是唯一的）
* **kind** - 字段类型：
    * `Grouping` - 用于对度量值字段进行分组的离散值
    * `Measure` - 数值数据值
    * `GroupingOrMeasure` - 可用作组别或度量值
* **displayName** - 在属性窗格中向用户显示的名称
* **description** - 字段的简短说明（可选）
* **requiredTypes** - 此数据角色所需的数据类型。 任何不匹配的值都将设置为 null（可选）
* **preferredTypes** - 此数据角色的首选数据类型（可选）

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>“requiredTypes”和“preferredTypes”中的有效数据类型

* **bool** - 一个布尔值
* **integer** - 一个整数值
* **numeric** - 一个数值
* **text** - 一个文本值
* **geography** - 一个地理数据

### <a name="example"></a>示例

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

上述数据角色将创建以下字段

![数据角色显示](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>定义数据映射的方式 - `dataViewMappings`

DataViewMapping 描述数据角色如何彼此相关，并允许你为它们指定条件要求。

大多数视觉对象提供单个映射，但你可以提供多个 dataViewMapping。 每个有效映射都将生成 DataView。 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[了解有关 DataViewMapping 的详细信息](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>定义属性窗格选项 - `objects`

对象描述与视觉对象关联的可自定义属性。
每个对象可以具有多个属性，每个属性都有与之关联的类型。
类型指示属性将是什么属性。 请参阅下文了解有关类型的详细信息。

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[了解有关对象的详细信息](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>处理部分突出显示 - `supportsHighlight`

默认情况下，此值设置为 false，这意味着当选择页上的某些内容时，将自动筛选“值”，而这反过来又会更新视觉对象，使其仅显示选定值。 如果要显示完整的数据，且只突出显示选定项，则需要在 capabilities.json 中将 `supportsHighlight` 设置为 true。

[了解有关突出显示的详细信息](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>处理高级编辑模式 - `advancedEditModeSupport`

视觉对象可以声明其高级编辑模式支持。
默认情况下，除非 capabilities json 中另有说明，否则视觉对象不支持高级编辑模式。

[了解有关 advancedEditModeSupport 的详细信息](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>视觉对象的数据排序选项 - `sorting`

视觉对象可通过其功能定义其排序行为。
默认情况下，除非 capabilities.json 中另有说明，否则视觉对象不支持修改其排序顺序。

[了解有关排序的详细信息](sort-options.md)

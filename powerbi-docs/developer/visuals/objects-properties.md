---
title: Power BI 视觉对象的对象和属性
description: 本文介绍 Power BI 视觉对象的可自定义属性。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ae548abd0d579414a69b0d970213ff9d69ff2f08
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "79205863"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Power BI 视觉对象的对象和属性

对象描述与视觉对象关联的可自定义属性。 对象可以具有多个属性，并且每个属性都具有描述属性的关联类型。 本文提供有关对象和属性类型的信息。

`myCustomObject` 是用于引用 `dataView` 和 `enumerateObjectInstances` 中的对象的内部名称。

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>显示名

`displayName` 是将显示在属性窗格中的名称。

## <a name="properties"></a>属性

`properties` 是开发者定义的属性的映射。

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` 是一个特殊属性，允许通过开关来切换对象。

示例:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>属性类型

具有两种属性类型：`ValueTypeDescriptor` 和 `StructuralTypeDescriptor`。

#### <a name="value-type-descriptor"></a>值类型描述符

`ValueTypeDescriptor` 类型大多为基元类型，通常用作静态对象。

下面是一些常见 `ValueTypeDescriptor` 元素：

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>结构类型描述符

`StructuralTypeDescriptor` 类型主要用于数据绑定对象。
最常见的 `StructuralTypeDescriptor` 类型为填充  。

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>渐变属性

渐变属性不能设置为标准属性。 相反，需要设置一个规则，以替代颜色选取器属性（填充类型）  。

以下代码中显示了一个示例：

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

请注意填充和 fillRule 属性   。 第一个属性是颜色选取器，第二个属性是在满足规则条件时将替代“填充”属性 `visually` 的渐变替代规则  。

填充属性和替代规则之间的此链接在 fillRule 属性的 `"rule"`>`"output"` 部分中设置   。

`"Rule"`>`"InputRole"` 属性设置触发规则（条件）的数据角色。 在此示例中，如果数据角色 `"Gradient"` 包含数据，将为 `"fill"` 属性应用该规则。

下面的代码显示了触发填充规则 (`the last item`) 的数据角色的示例：

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>enumerateObjectInstances 方法

若要有效使用对象，需要使用自定义视觉对象中名为 `enumerateObjectInstances` 的函数。 此函数使用对象填充属性窗格，并决定对象在 dataView 中的绑定位置。  

典型设置如下所示：

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>属性

`enumerateObjectInstances` 中的属性反映在功能中定义的属性。 有关示例，请参阅本文末尾。

### <a name="objects-selector"></a>对象选择器

`enumerateObjectInstances` 中的选择器决定每个对象在 dataView 中的绑定位置。 有四种不同选项。

#### <a name="static"></a>静态

此对象绑定到元数据 `dataviews[index].metadata.objects`，如下所示。

```typescript
selector: null
```

#### <a name="columns"></a>列

此对象绑定到具有匹配 `QueryName` 的列。

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>选择器

此对象将绑定到你为其创建了 `selectionID` 的元素。 在此示例中，假设已为某些 dataPoint 创建 `selectionID`，并且正在循环遍历它们。

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>作用域标识

此对象绑定到组交集处的特定值。 例如，如果具有类别 `["Jan", "Feb", "March", ...]` 和系列 `["Small", "Medium", "Large"]`，可能会需要在匹配 `Feb` 和 `Large` 的值的交集上有一个对象。 为实现此目的，可以获取这两个列的 `DataViewScopeIdentity`，将它们推送到变量 `identities`，然后再结合使用此语法与选择器。

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>示例

以下示例显示具有一个属性（“填充”）的 customColor 对象的 objectEnumeration 的外观  。 我们希望将此对象静态绑定到 `dataViews[index].metadata.objects`，如下所示：

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```

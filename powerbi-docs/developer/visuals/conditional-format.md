---
title: 条件格式
description: 了解如何将条件格式应用于 Power BI 视觉对象项目
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 10/27/2020
ms.openlocfilehash: 5243d1eda3fef2c7b82350fb0ca2669eb43c7623
ms.sourcegitcommit: b5365df7fc32b7c49f8a2bf2cf75b5edd6bda9b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513819"
---
# <a name="add-conditional-formatting"></a>添加条件格式

[条件格式](../../visuals/service-tips-and-tricks-for-color-formatting.md#conditional-formatting-for-visualizations)允许报表创建者根据数值指定在报表中显示颜色的方式。

本文介绍如何将条件格式功能添加到 Power BI 视觉对象。

条件格式只能应用于以下属性类型：
* 颜色
* 文本
* 图标
* Web URL

## <a name="add-conditional-formatting-to-your-project"></a>向项目添加条件格式

本部分说明如何向现有 Power BI 视觉对象添加条件格式。 本文中的示例代码基于 [SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) 视觉对象。 可以检查 [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts) 中的源代码。

### <a name="add-a-conditional-color-formatting-entry-in-the-format-pane"></a>在“格式”窗格中添加条件颜色格式条目

在本部分中，你将了解如何在“格式”窗格中向数据点添加条件颜色格式条目。

1. 你将在 `VisualObjectInstance` 中使用 `propertyInstanceKind` 数组，该数组由 `powerbi-visuals-api` 公开。 第一步是验证文件是否包含此导入：

    ```typescript
    import powerbiVisualsApi from "powerbi-visuals-api";
    ```

2. 若要指定适当的格式类型（Constant、ConstantOrRule 或 Rule），请使用 `VisualEnumerationInstanceKinds` 枚举。 将以下导入添加到文件：

    ```typescript
    import VisualEnumerationInstanceKinds = powerbiVisualsApi.VisualEnumerationInstanceKinds;
    ```

3. 在 `propertyInstanceKind` 数组下列出要支持条件格式的所有属性。 在 `enumerateObjectInstances` 方法中定义这些属性。

    ```typescript
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
            …
            case 'colorSelector':
                …
                    objectEnumeration.push({
                        objectName: objectName,
                        displayName: barDataPoint.category,
                        properties: {
                            fill: {
                                solid: {
                                    color: barDataPoint.color
                                }
                            }
                        },
                        selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),
                        altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                        // List your conditional formatting properties
                        propertyInstanceKind: {
                            fill: VisualEnumerationInstanceKinds.ConstantOrRule
                        }
                    });
                }
            …
    }

    ```

    `VisualEnumerationInstanceKinds.ConstantOrRule` 将创建条件格式 UI 条目和常量格式 UI 元素。

    >[!div class="mx-imgBorder"]
    >![“条件格式”按钮的屏幕截图，它显示在 Power BI 的“常规颜色”按钮旁。](media/conditional-formatting/conditional-formatting-ui.png)

### <a name="define-how-conditional-formatting-behaves"></a>定义条件格式的行为方式

定义格式应用于数据点的方式。

使用 `powerbi-visuals-utils-dataviewutils` 下声明的 `createDataViewWildcardSelector` 来指定是否将条件格式应用于实例和/或总计。 有关详细信息，请参阅 [DataViewWildcard](utils-dataview.md#)。

在 `enumerateObjectInstances` 中，对要应用条件格式的对象进行以下更改：

 * 使用 `dataViewWildcard.createDataViewWildcardSelector(dataViewWildcardMatchingOption)` 调用替换值 `selector`。 `DataViewWildcardMatchingOption` 定义是否将条件格式应用于实例和/或总计。

* 添加具有之前为 `selector` 属性定义的值的 `altConstantValueSelector` 属性。

```typescript
case 'colorSelector':
         …
            objectEnumeration.push({
                objectName: objectName,
                displayName: barDataPoint.category,
                properties: {
                    fill: {
                        solid: {
                            color: barDataPoint.color
                        }
                    }
                },

                // Define whether the conditional formatting will apply to instances, totals, or both
                selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),

                // Add this property with the value previously defined for the selector property
                altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                propertyInstanceKind: { 
                    fill: VisualEnumerationInstanceKinds.ConstantOrRule
                }
            });
        }

```

## <a name="next-steps"></a>后续步骤

查看 [DataViewUtils](utils-dataview.md) 一文。
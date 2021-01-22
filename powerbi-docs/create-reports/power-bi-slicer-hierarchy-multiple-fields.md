---
title: 向层次结构切片器添加多个字段
description: 了解如何创建在层次结构中包含多个字段的层次结构切片器。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Create reports
ms.openlocfilehash: abed7e9f6da352d5461868e6371ffefb814eb3ff
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597632"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>向层次结构切片器添加多个字段

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

如果要在单个切片器中对多个相关字段进行筛选，可以通过构建所谓的“层次结构”切片器来实现。 可以在 Power BI Desktop 或 Power BI 服务中创建这些切片器。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI 中的层次结构切片器的屏幕截图。":::

向切片器添加多个字段时，默认情况下，切片器会在可以展开的项旁边显示一个箭头或者 V 形符号，展开这些项可以显示下一级别中的项。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI 中的层次结构切片器下拉列表的屏幕截图。":::
 
 
为某个项选择一个或多个子级时，将看到顶级项的半选圆圈。
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI 中的单选层次结构切片器的屏幕截图。":::

## <a name="format-the-slicer"></a>设置切片器格式

切片器的行为没有更改。 还可以根据需要对切片器进行样式设定。 例如，可以将它设置为单选模式。 也可以在列表和下拉列表之间进行交换。 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="格式设置为下拉切片器的层次结构切片器的屏幕截图。":::

还可以进行以下格式更改。

### <a name="change-the-title"></a>更改标题

可以编辑任何切片器的标题，此功能对层次结构切片器特别有用。 默认情况下，层次结构切片器的名称是层次结构中的一组字段名称。

在此示例中，切片器的标题列出了层次结构中的三个字段：类型、平台和名称。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="具有类型、平台和名称字段的层次结构切片器的屏幕截图。":::

若要更改名称，请选择切片器，然后选择“格式”窗格。 将在“切片器标头”下的“标题文本”框中看到切片器的当前名称。 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="“格式”窗格的屏幕截图，其中包含当前标题。":::

选择相应文本并添加新名称。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="层次结构切片器的新标题的屏幕截图。":::


### <a name="change-the-expandcollapse-icon"></a>更改展开/折叠图标

层次结构切片器具有一些其他格式设置选项。 可以将展开/折叠图标从默认箭头更改为加号/减号或插入符号。

1. 选择切片器，然后选择“格式”。
1. 展开项并选择展开/折叠图标。
1. 选择 V 形符号、加号/减号或插入符号。
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="选择层次结构切片器的展开/折叠图标的屏幕截图。":::
 
### <a name="change-the-indentation"></a>更改缩进

如果报表中的空间较为紧密，你可能希望减少子项的缩进量。 默认情况下，缩进为 15 像素，但可以增加或减少。 

1. 选择切片器，然后选择“格式”。
1. 展开项，然后拖动“渐变布局缩进”进行放大或缩小。 还可以在框中键入一个数字。

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="设置层次结构切片器缩进的屏幕截图。":::
    
## <a name="limitations-and-considerations"></a>限制和注意事项

- 对于表格模型，此功能需要 SQL Server Analysis Services 2017 或更高版本。
- 对于多维模型，此功能需要启用了 SuperDAXMD 的 SQL Server Analysis Services 2019 CU5 或更高版本。 详细了解 [SuperDAXMD](/analysis-services/multidimensional-models/dax-for-multidimensional-models#superdaxmd)。

## <a name="next-steps"></a>后续步骤

- [Power BI 中的切片器](../visuals/power-bi-visualization-slicers.md)
- 更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

---
title: 向切片器添加多个字段
description: 了解如何创建在层次结构中包含多个字段的切片器。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: c41fa1e0c8510f64f9c6e53c83fe9ee8a2e75e67
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "81006884"
---
# <a name="add-multiple-fields-to-a-slicer-preview"></a>向切片器添加多个字段（预览）

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

如果要在单个切片器中跨多个相关字段进行筛选，可以通过构建所谓的“层次结构”切片器来实现  。 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI 中的层次结构切片器":::

要启用此预览功能，请在“文件”菜单中，依次选择“选项和设置” > “选项”    。 在“全局”下，转到“预览功能”部分，并确保选中“层次结构切片器”    。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-preview.png" alt-text="选择层次结构切片器预览功能":::

向切片器添加多个字段时，切片器会在可以展开的项目旁边显示一个箭头或者 V 形符号，展开这些项目可以显示下一级别中的项目  。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI 中的层次结构切片器下拉列表":::
 
切片器的行为没有更改。 你仍可以在列表和下拉列表之间进行切换，还可以根据需要设置切片器的样式。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="格式设置为下拉切片器的层次结构切片器":::
 
你可以将它设置为单选模式。 对于选择了某些子元素的项目，你会看到一个半边选中的圆圈。
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI 中的单选层次结构切片器":::

## <a name="next-steps"></a>后续步骤

- [Power BI 中的切片器](../visuals/power-bi-visualization-slicers.md)
- 更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
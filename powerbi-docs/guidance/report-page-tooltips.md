---
title: 用报表页工具提示扩展视觉对象
description: 关于使用报表页工具提示的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: e3af0828afcc7c085b896fe9e1b99f3b10bfdd5f
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277838"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>用报表页工具提示扩展视觉对象

本文面向设计 Power BI 报表的报表作者。 该文章提供创建[报表页工具提示](../create-reports/desktop-tooltips.md)的意见和建议。

## <a name="suggestions"></a>建议

报表页工具提示可以增强报表用户的体验。 借助页面工具提示，报表用户可快速高效地从视觉对象获取更深刻的见解。 这些工具提示可与不同的报表对象相关联：

- **视觉对象：** 在逐个视觉对象的基础上，可配置将显示页面工具提示的视觉对象。 对于每个视觉对象，都可以使其不显示任何工具提示，默认为视觉对象工具提示（在“视觉对象字段”窗格中进行配置）或使用特定的页面工具提示。
- **视觉对象标头：** 可以将特定视觉对象配置为显示页面工具提示。 当报表用户将光标悬停在视觉对象标头图标上时，可显示页面工具提示，请务必向用户介绍此图标。

> [!NOTE]
> 如果工具提示页筛选器与视觉对象的设计兼容，则报表视觉对象只能显示页面工具提示。 例如，按产品分组的视觉对象与按产品筛选的工具提示页兼容   。
>
> 页面工具提示不支持交互。 如果希望报表用户进行交互，请改为创建[钻取页](../create-reports/desktop-drillthrough.md)。
>
> Power BI 视觉对象不支持页面工具提示。

下面是一些建议的设计方案：

- [不同的透视](#different-perspective)
- [添加详细信息](#add-detail)
- [添加帮助](#add-help)

### <a name="different-perspective"></a>不同的透视

页面工具提示可以直观显示与源视觉对象相同的数据。 这是通过使用相同的视觉对象和透视组，或通过使用不同的视觉对象类型来完成的。 页面工具提示还可以应用与应用于源视觉对象的那些筛选器不同的筛选器。

以下示例显示了报表用户将光标悬停在 EnabledUsers 值上时发生的情况  。 该值的筛选器上下文为 Yammer（2018 年 11 月）。

![矩阵视觉对象显示行上按年和月分组的值网格。 报表用户已将光标悬停在单个值上。 已显示页面工具提示。](media/report-page-tooltips/suggestion-different-perspective.png)

将显示页面工具提示。 它呈现了不同的数据视觉对象（折线图和簇状柱形图），并应用了对比时间筛选器。 请注意，数据点的筛选器上下文为 2018 年 11 月。 然而，页面工具提示会显示一整年的月份的趋势  。

### <a name="add-detail"></a>添加详细信息

页面工具提示可显示其他详细信息并添加上下文。

以下示例显示了当报表用户将光标悬停在邮政编码 98022 的“Average of Violation Points”值上时发生的情况  。

![表视觉对象显示网格值，该表包含三列。 已显示页面工具提示。](media/report-page-tooltips/suggestion-add-details.png)

将显示页面工具提示。 它提供了邮政编码 98022 的特定属性和统计信息。

### <a name="add-help"></a>添加帮助

可将视觉对象标头配置为向视觉对象标头显示页面工具提示。 可使用格式丰富的文本框将帮助文档添加到页面工具提示。 也可以添加图像和形状。

有趣的是，按钮、图像、文本框和形状也可以显示视觉对象标头页工具提示。

以下示例显示了报表用户将光标悬停在[“视觉对象标头”图标](../create-reports/desktop-visual-elements-for-reports.md)上时会发生的情况。

![报表用户已将其光标悬停在视觉对象标头图标（问号图标）上。 已显示格式丰富的工具提示。](media/report-page-tooltips/suggestion-add-help.png)

将显示页面工具提示。 它在四个文本框以及一个形状（行）中显示格式丰富的文本。 页面工具提示通过描述视觉对象中显示的每个首字母缩略词来传达帮助。

## <a name="recommendations"></a>建议

在报表设计阶段，建议采用以下做法：

- **页面大小：** 将页面工具提示配置为小。 可使用内置的“工具提示”选项（宽 320 像素，高 240 像素）  。 也可以设置自定义尺寸。 注意不要使用太大的页面，否则，源页面的视觉对象可能变得模糊。
- **页面视图：** 在报表设计器中，将页面视图设置为“实际大小”（页面视图默认设置为“调整到页面大小”）   。 以便在设计时查看页面工具提示的真实大小。
- **样式：** 请考虑将页面工具提示设计为使用与报表相同的主题和样式。 这样一来，用户就会感觉他们在使用同一报表。 或者，为工具提示设计一种称赞的样式，并确保将此样式应用于所有页面工具提示。
- **工具提示筛选器：** 将筛选器分配给页面工具提示，以便在设计时预览实际效果。 在发布报表之前，请务必删除这些筛选器。
- **页面可见性：** 请始终隐藏工具提示页，用户不应直接导航到这些页面。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [根据 Power BI Desktop 中的报表页创建工具提示](../create-reports/desktop-tooltips.md)
- [在 Power BI Desktop 中自定义工具提示](../create-reports/desktop-custom-tooltips.md)
- [使用视觉对象元素增强 Power BI 报表](../create-reports/desktop-visual-elements-for-reports.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

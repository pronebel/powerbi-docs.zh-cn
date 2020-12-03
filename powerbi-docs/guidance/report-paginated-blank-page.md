---
title: 打印分页报表时避免出现空白页
description: 设计分页报表以在打印时避免出现空白页的指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 0fa886973105bdb4bc8a35f145168c1775ca12cb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418454"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>打印分页报表时避免出现空白页

本文面向设计 Power BI [分页报表](../paginated-reports/paginated-reports-report-builder-power-bi.md)的报表作者。 它提供了相关建议，以帮助你在将报表导出到硬分页格式（如 PDF 或 Microsoft Word）或打印时避免出现空白页。

## <a name="page-setup"></a>页面设置

报表页面大小属性可确定页面方向、尺寸和边距。 通过以下方式访问这些报表属性：

- 使用报表“属性页”  ：右键单击报表画布外的深灰色区域，然后选择“报表属性”  。
- 使用[“属性”窗格](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane)  ：单击报表画布外的深灰色区域以选择报表对象。 确保“属性”窗格处于打开状态  。

报表“属性页”的“页面设置”页提供了一个用户友好的界面，可查看和更新页面设置属性   。

![图像显示了“报表属性”窗口，突出显示“页面设置”页。](media/report-paginated-blank-page/report-page-setup-properties.png)

确保所有页面大小属性均已正确配置：

|属性|建议|
|---------|---------|
|页单位|选择相关单位：英寸或厘米。|
|方向|选择正确的选项：纵向或横向。|
|纸张大小|选择纸张大小，或分配自定义宽度和高度值。|
|Margins|为左边距、右边距、上边距和下边距设置相应的值。|
|||

## <a name="report-body-width"></a>表体宽度

页面大小属性可确定报表对象的可用空间。 报表对象可以是数据区域、数据可视化或其他报表项。

输出空白页的常见原因是，表体宽度超出了可用页面空间  。

只能使用“属性”  窗格来查看和设置表体宽度。 首先，单击表体空白区域中的任意位置。

![图像显示了“属性”窗格，突出显示表体宽度属性。](media/report-paginated-blank-page/report-body-properties-width.png)

确保宽度值不会超出可用页面宽度。 使用以下公式：

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> 如果空间中已存在要删除的报表对象，则不能减小表体宽度。 在减小宽度之前，必须先对这些对象重新定位或调整大小。
>
> 此外，当你添加新对象，或者对现有对象调整大小或重新定位时，表体宽度可能会自动增加。 报表设计器始终扩大表体，以容纳其所含对象的位置和大小。

## <a name="report-body-height"></a>表体高度

输出空白页的另一个原因是，最后一个对象之后的表体中有多余空间。

我们建议你始终减小表体高度以删除任何尾随空格。

![图像显示了报表设计。 Tablix 数据区域下方的空间将突出显示，并标记为不必要。](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>分页符选项

每个数据区域和数据可视化都有分页符选项。 可以在其属性页或“属性”  窗格中访问这些选项。

确保不必要地启用“在组件后面添加分页符”  属性。

![图像显示了 Tablix 属性窗口。 已启用“在组件后面添加分页符”属性。](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>使用容器空格

如果空白页问题仍然存在，也可以尝试禁用报表 ConsumeContainerWhitespace 属性  。 只能在“属性”窗格中设置该属性  。

![图像显示了“属性”窗格，突出显示 ConsumeContainerWhitespace 属性。](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

默认启用。 它指示是否应使用容器中的最小空格，如表体或矩形。 只有内容右侧和下方的空格才受到影响。

## <a name="printer-paper-size"></a>打印机纸张大小

最后，如果要将报表打印到纸张上，请确保打印机已加载正确的纸张。 物理纸张大小应与[报表纸张大小](#page-setup)相对应。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI Premium 中的分页报表是什么？](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Power BI 分页报表中的分页](../paginated-reports/paginated-reports-pagination.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)

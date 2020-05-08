---
title: 使用报表页钻取
description: 关于使用报表页钻取的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: d5599db57ef7b105575dcb7ee4b4342f374624f0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "78290567"
---
# <a name="use-report-page-drillthrough"></a>使用报表页钻取

本文面向设计 Power BI 报表的报表作者。 该文章提供创建[报表页钻取](../desktop-drillthrough.md)的意见和建议。

建议将报表设计为允许报表用户实现以下流程：

1. 查看报表页。
2. 标识视觉对象元素以进行更深入的分析。
3. 右键单击要钻取的视觉对象元素。
4. 执行补充分析。
5. 返回到源报表页。

## <a name="suggestions"></a>建议

建议考虑两种类型的钻取方案：

- [额外的深度](#additional-depth)
- [更广泛的透视](#broader-perspective)

### <a name="additional-depth"></a>额外的深度

当报表页显示汇总结果时，钻取页可向报表用户呈现事务级别的详细信息。 这种设计方法使用户可以仅在需要时查看支持事务。

以下示例显示了当报表用户从每月销售汇总中钻取时发生的情况。 钻取页包含特定月份的详细订单列表。

![标题为“Sales Summary”的矩阵视觉对象按行上的年份和月份以及列上的国家/地区对销售进行分组。 还将显示钻取页。](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>更广泛的透视

钻取页可以达到与额外的深度相反的效果。 此方案非常适用于钻取整体视图。

以下示例显示了当报表用户从邮政编码中钻取时发生的情况。 钻取页显示有关邮政编码的一般信息。

![表视觉对象有三列：Zip Code、Average of Violation Points 和 Average of Grade Rating。 还将显示钻取页。](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>建议

在报表设计阶段，建议采用以下做法：

- **样式：** 请考虑将钻取页设计为使用与报表相同的主题和样式。 这样一来，用户就会感觉他们在使用同一报表。
- **钻取筛选器：** 设置钻取筛选器，以便在设计钻取页时预览实际效果。 在发布报表之前，请务必删除这些筛选器。
- **附加功能：** 钻取页与任何报表页都一样。 甚至可以通过其他交互功能（包括切片器或筛选器）来增强钻取页。
- **空白：** 避免添加可能显示为 BLANK 或在应用钻取筛选器时产生错误的视觉对象。
- **页面可见性：** 请考虑隐藏钻取页。 如果决定使钻取页保持可见状态，请确保添加一个按钮，该按钮使用户可以清除任何先前设置的钻取筛选器。 为该按钮分配[书签](../desktop-bookmarks.md)。 应将该书签配置为删除所有筛选器。
- **返回按钮：** 分配钻取筛选器时，将自动添加后退[按钮](../desktop-buttons.md)。 最好保留该按钮。 以便报表用户可以轻松地返回到源页。
- **发现：** 通过设置视觉对象标题图标文本或向文本框添加说明来增强对钻取页的认识。 你还可以设计覆盖，如[此博客文章](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/)中所述。

> [!TIP]
> 也可以配置对 Power BI 分页报表的钻取。 此操作可通过添加 Power BI 报表链接来完成。 链接可定义 [URL 参数](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/)。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [在 Power BI Desktop 中使用钻取](../desktop-drillthrough.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

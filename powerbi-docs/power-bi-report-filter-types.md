---
title: Power BI 报表中的筛选器类型
description: 在 Power BI 中将页面筛选器、可视化效果筛选器或报表筛选器添加到报表
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c96b4ebae574a3b6a6fa54c5f5dc99b5bc948a90
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874421"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Power BI 报表中的筛选器类型

筛选器的行为方式并不完全相同，因为他们的创建方式不同。 筛选器的创建方式影响它们在编辑模式下新“筛选器”窗格中的行为方式。 本文将介绍不同种类的筛选器：因筛选器的不同创建方式及其不同用途而异。 详细了解如何[向报表添加筛选器](power-bi-report-add-filter.md)。 

![筛选器窗格](media/power-bi-report-filter-types/power-bi-filter-pane.png)

首先来看看两种最常见的筛选器类型：手动筛选器和自动筛选器。

## <a name="manual-filters"></a>手动筛选器 

手动筛选器是报表创建者在新“筛选器”窗格中拖放到任意位置的筛选器。 有权编辑报表的用户可以在新窗格中编辑、删除、清除、隐藏、锁定、重命名或排序此类筛选器。

## <a name="automatic-filters"></a>自动筛选器 

自动筛选器是在视觉对象生成时自动添加到“筛选器”窗格的视觉对象级别的筛选器。 此类筛选器以组成视觉对象的字段为依据。 有权编辑报表的用户可以在新窗格中编辑、清除、隐藏、锁定、重命名或排序此类筛选器。 但无法删除自动筛选器，因为视觉对象引用这些字段。

## <a name="more-advanced-filters"></a>更多高级筛选器

接下来介绍的筛选器类型不太常见，但了解它们仍很重要（如果它们出现在报表中的话）。 此外，你可能还会发现它们非常适用于为报表创建合适的筛选器。

## <a name="include-and-exclude-filters"></a>包含筛选器和排除筛选器

如果你对视觉对象使用包含或排除功能，包含筛选器和排除筛选器就会自动添加到“筛选器”窗格中。 有权编辑报表的用户可以在新窗格中删除、锁定、隐藏或排序此类筛选器。 但无法编辑、清除或重命名包含筛选器或排除筛选器，因为此类筛选器与视觉对象的包含和排除功能相关联。

![排除筛选器](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>向下钻取筛选器

如果你对报表中的视觉对象使用向下钻取功能，向下钻取筛选器就会自动添加到“筛选器”窗格中。 有权编辑报表的用户可以在新窗格中编辑或清除此类筛选器。 但无法删除、隐藏、锁定、重命名或排序此类筛选器，因为此类筛选器与视觉对象的向下钻取功能相关联。 若要删除向下钻取筛选器，请单击视觉对象的向上钻取按钮。

![向下钻取筛选器](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>交叉钻取筛选器

如果向下钻取筛选器通过交叉筛选或交叉突出显示功能传递到报表页上的另一个视觉对象，交叉钻取筛选器就会自动添加到新窗格中。 有权编辑报表的用户无法删除、清除、隐藏、锁定、重命名或排序此类筛选器，因为此类筛选器与视觉对象的向下钻取功能相关联。 而且也无法编辑此类筛选器，因为此类筛选器源自另一个视觉对象中的向下钻取。 若要删除交叉钻取筛选器，请单击传递此类筛选器的视觉对象的向上钻取按钮。

## <a name="drillthrough-filters"></a>钻取筛选器

钻取筛选器通过钻取功能从一个报表页传递到另一个报表页。 此类筛选器显示在“钻取”窗格中。 钻取筛选器分为两种类型。 第一种类型是调用钻取的筛选器。 报表编辑人员可以编辑、删除、清除、隐藏或锁定此类筛选器。 第二种类型是根据源报表页的报表页级别筛选器传递到目标的钻取筛选器。 报表编辑人员可以编辑、删除或清除此类暂时钻取筛选器。 但无法为最终用户锁定或隐藏此类筛选器。

## <a name="url-filters"></a>URL 筛选器

通过添加 URL 查询参数，可以将 URL 筛选器添加到新窗格中。 有权编辑报表的用户可以在新窗格中编辑、删除或清除此类筛选器。 但无法隐藏、锁定、重命名或排序此类筛选器，因为此类筛选器与 URL 参数相关联。 若要删除此类筛选器，请从 URL 中删除参数。 下面是包含参数的示例 URL：

app.powerbi.com/groups/me/apps/app-id  /reports/report-id  /ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![URL 筛选器](media/power-bi-report-filter-types/power-bi-filter-url.png)

详细了解 [URL 筛选器](service-url-filters.md)。

## <a name="pass-through-filters"></a>直通筛选器

直通筛选器是通过问答创建的视觉对象级别筛选器。 作者可以在新窗格中删除、隐藏或排序此类筛选器。 但无法重命名、编辑、清除或锁定此类筛选器。

![通过问答创建的直通筛选器](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>比较筛选器类型

下表比较了作者可以对不同类型筛选器执行的操作。

| 筛选器类型 | 编辑 | 清除 | 删除 | 隐藏 | 锁定 | 排序 | 重命名 |
|----|----|----|----|----|----|----|----|
| 手动筛选器 | Y | Y | Y | Y | Y | Y | Y |
| 自动筛选器 | Y | Y | N | Y | Y | Y | Y |
| 包括/排除筛选器 | N | N | Y | Y | Y | Y | N |
| 向下钻取筛选器 | Y | Y | N | N | N | N | N |
| 交叉钻取筛选器 | N | N | N | N | N | N | N |
| 钻取筛选器（调用钻取） | Y | Y | Y | Y | Y | N | N |
| 钻取筛选器（暂时） | Y | Y | Y | N | N | N | N |
| URL 筛选器 - 暂时 | Y | Y | Y | N | N | N | N |
| 直通筛选器 | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>后续步骤

[向报表添加筛选器](power-bi-report-add-filter.md)

[导览报表的“筛选器”窗格](consumer/end-user-report-filter.md)

[报表中的筛选器和突出显示](power-bi-reports-filters-and-highlighting.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


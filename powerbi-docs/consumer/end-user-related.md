---
title: 从仪表板、报表和数据集查看相关内容
description: 使用导航这一预览功能，可以更轻松地查看仪表板、报表和数据集中的相关内容
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Get started
ms.custom: video-B2vd4MQrz4M#t
ms.openlocfilehash: c3672433675bd2c44de8e9005a3c46d592d51452
ms.sourcegitcommit: 0bf42b6393cab7a37d21a52b934539cf300a08e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96781787"
---
# <a name="see-related-content-in-the-power-bi-service"></a>查看 Power BI 服务中的相关内容

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


“相关内容”窗格显示了 Power BI 服务内容（仪表板、报表和数据集）的互连方式。 此外，“相关内容”窗格还是执行某个操作的启动面板。 可以在这里执行以下操作：打开仪表板、打开报表、生成见解、分析 Excel 中分析数据等。  

在 Power BI 服务中，报表是在数据集的基础之上生成的，报表视觉对象固定到仪表板中，仪表板视觉对象可以链接回报表。 不过，如何知道哪些仪表板在托管“市场营销”报表中的视觉对象？ 如何查找这些仪表板？ “采购”仪表板是否在使用多个数据集中的视觉对象？ 如果是，这些数据集的名称是什么？该如何打开并编辑这些数据集？ “人力资源”数据集是否用于任何报表或仪表板？ 能否移动此数据集，而又不断开任何链接？ 所有这些问题全都可以在“相关内容”窗格中找到答案。  在此窗格中，不仅可以查看相关内容，还可以对内容执行操作，并轻松地在相关内容之间进行导航。

![相关内容](./media/end-user-related/power-bi-see-related-pane.png)

> [!NOTE]
> “相关内容”功能不适用于流数据集。
> 
> 

## <a name="see-related-content-for-a-dashboard-or-report"></a>查看仪表板或报表的相关内容
观看 Will 查看仪表板的相关内容。 然后，按照视频下方的分步说明操作，用“采购分析”示例自行尝试。

> [!NOTE]
> 此视频基于较旧版本的 Power BI 服务。 

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M#t=3m05s" frameborder="0" allowfullscreen></iframe>

打开仪表板或报表，选择菜单栏中的“更多选项”(…)，然后从下拉列表中选择“查看相关内容” 。

![省略号下拉列表](./media/end-user-related/power-bi-see-related.png)

此时，“相关内容”窗格会打开。 对于仪表板，它显示将可视化效果固定到此仪表板的所有报表及其关联的数据集。 对于此仪表板，有多个仅从一个报表固定的可视化效果，并且该报表仅基于一个数据集。 如果你查看本文开头部分的图像，你会看到一个仪表板的相关内容，其中包含来自四个报表的固定的可视化效果，以及两个数据集。

![“相关内容”窗格](./media/end-user-related/power-bi-view-related-dashboard.png)

在此窗格中，你可以直接对相关内容执行操作，具体取决于你的权限。  例如，选择报表或仪表板名称即可将其打开。  对于列出的报表，请选择一个图标以打开并编辑报表设置、[获取见解](end-user-insights.md)，等等。 对于数据集，可以查看上次刷新日期和时间、[在 Excel 中进行分析](../collaborate-share/service-analyze-in-excel.md)、[获取见解](end-user-insights.md)、进行刷新，等等。  



<!-- ## See related content for a dataset
You'll need at least *view* permissions to a dataset to open the **Related content** pane. In this example, we're using the [Procurement Analysis sample](../create-reports/sample-procurement.md).

From the nav pane, locate the **Workspaces** heading and select a workspace from the list. If you have content in a workspace, it will display in the canvas to the right. 

![workspaces in nav pane](./media/end-user-related/power-bi-workspace.png)


In a workspace, select the **Datasets** tab and locate the **See related** icon ![See related icon](./media/end-user-related/power-bi-view-related-icon-new.png).

![Datasets tab](./media/end-user-related/power-bi-related-dataset.png)

Select the icon to open the **Related content** pane.

![Related content pane opens on top of Power BI content view](media/end-user-related/power-bi-dataset.png)

From here, you can take direct action on the related content. For example, select a dashboard or report name to open it.  For any dashboard in the list, select an icon to [share the dashboard with others](../collaborate-share/service-share-dashboards.md) or to open the **Settings** window for the dashboard. For a report, select an icon to [analyze in Excel](../collaborate-share/service-analyze-in-excel.md), [rename](../create-reports/service-rename.md), or [get insights](end-user-insights.md).  -->

## <a name="limitations-and-troubleshooting"></a>限制和疑难解答
* 若未看到“查看相关内容”，请改为查找图标 ![“查看相关内容”图标](./media/end-user-related/power-bi-view-related-icon-new.png)。 选择此图标，可以打开“相关内容”窗格。
* 必须在[“阅读”视图](end-user-reading-view.md)中，才能打开报表的相关内容。
* “相关内容”功能不适用于流数据集。

## <a name="next-steps"></a>后续步骤
* [Power BI 服务入门](../fundamentals/service-get-started.md)
* 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

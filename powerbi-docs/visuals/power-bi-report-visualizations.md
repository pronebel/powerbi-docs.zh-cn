---
title: Power BI 服务和 Power BI Desktop 中的报表可视化效果概述
description: Microsoft Power BI 中的报表可视化效果（视觉对象）概述。
author: mihart
ms.author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: SYk_gWrtKvM
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/01/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: aabc58e34e5ba61f44673905450c8feb8d6ace47
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532262"
---
# <a name="visualizations-in-power-bi-reports"></a>Power BI 报表中的可视化效果

可视化效果（简称为“视觉对象”）会显示在数据中发现的见解。 在 Power BI 报表中，既可能一个页面上只有一个视觉对象，也可能页面上有大量视觉对象。 在 Power BI 服务中，可以将视觉对象[从报表固定到仪表板](../service-dashboard-pin-tile-from-report.md)。

有必要在报表设计者与报表使用者之间进行区分   。  如果你是生成或修改报表的人员，则你是设计者。  设计者有权编辑报表及其基础数据集。 在 Power BI Desktop 中，这意味着，可以在数据视图中打开数据集，并在报表视图中创建视觉对象。 在 Power BI 服务中，这意味着可使用报表编辑器在[编辑视图](../consumer/end-user-reading-view.md)中打开数据集或报表。 如果有人将某个报表或仪表板[与你共享](../consumer/end-user-shared-with-me.md)，你就是报表的一个使用者  。 可查看报表及其视觉对象并与之交互，但无法保存重大更改。

Power BI 的“可视化效果”窗格中还有其他许多视觉对象类型，可供直接使用。

![](media/power-bi-report-visualizations/power-bi-templates.png)

如需有更多选择，请访问 [Microsoft AppSource 社区网站](https://appsource.microsoft.com)，查找并[下载](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) Microsoft 和社区提供的[自定义视觉对象](../developer/custom-visual-develop-tutorial.md)。

<iframe width="560" height="315" src="https://www.youtube.com/embed/SYk_gWrtKvM?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


如果初次接触 Power BI 或需复习，请利用以下链接了解 Power BI 可视化效果的基础知识。  也可使用（本文左侧的）目录查找更多有用信息。

## <a name="add-a-visualization-in-power-bi"></a>在 Power BI 中添加一个可视化效果

在报表页上[创建可视化效果](power-bi-report-add-visualizations-i.md)。 浏览[可用的可视化效果和可用的可视化效果教程的列表。](power-bi-visualization-types-for-reports-and-q-and-a.md) 

## <a name="upload-a-custom-visualization-and-use-it-in-power-bi"></a>上载自定义可视化效果并在 Power BI 中使用

添加自己创建或在 [Microsoft AppSource 社区网站](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)中找到的自定义可视化效果。 有创造性的点子？ 深入了解我们的源代码，使用我们的[开发工具](../developer/custom-visual-develop-tutorial.md)创建新的可视化效果类型，并[将它与社区共享](../developer/office-store.md)。 若要详细了解如何开发自定义视觉对象，请访问[开发 Power BI 自定义视觉对象](../developer/custom-visual-develop-tutorial.md)。

## <a name="personalize-your-visualization-pane-preview"></a>个性化可视化效果窗格（预览）

如果你发现自己在许多报表中使用相同的自定义视觉对象，则可将自定义可视化效果固定到可视化效果窗格。 要固定可视化效果，请右键单击视觉对象，将其固定到窗格。

![固定到可视化效果窗格](media/power-bi-report-visualizations/power-bi-pin-custom-visual-option.png)

视觉对象一经固定，就会向上移动到其他内置视觉对象的位置。 此视觉对象现绑定到你的已登录帐户，因此如果你已登录，则生成的任何新报表都将自动包含此视觉对象。 这样，无需将添加到每个报表，就能很轻松地在特定视觉对象上进行标准化。

![个性化的可视化效果窗格](media/power-bi-report-visualizations/power-bi-personalized-visualization-pane.png)

此功能处于预览状态，你只会在 Power BI Desktop 中看到固定的视觉对象。 此外，必须登录才能使用此功能。

## <a name="change-the-visualization-type"></a>更改可视化效果类型

请尝试[更改可视化效果的类型](power-bi-report-change-visualization-type.md)以查看哪种类型最适合你的数据。

## <a name="pin-the-visualization"></a>固定可视化效果

在 Power BI 服务中，若有所需的可视化效果，可以将它作为磁贴[固定到仪表板](../service-dashboard-pin-tile-from-report.md)。 如果在固定报表后更改其中正在使用的可视化效果，仪表板上的磁贴并不会更改。也就是说，如果之前是折线图，即使在报表中将它更改为环形图，它也仍为折线图。

## <a name="limitations-and-considerations"></a>限制和注意事项
- 根据数据源和字段数（度量值或列），视觉对象可能加载很慢。  出于可读性和性能原因，建议将视觉对象限制为 10 到 20 个字段。 

- 视觉对象的上限是 100 个字段（度量值或列）。 如果你的视觉对象加载失败，请减少字段数。   

## <a name="next-steps"></a>后续步骤

* [Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [自定义视觉对象](../power-bi-custom-visuals.md)

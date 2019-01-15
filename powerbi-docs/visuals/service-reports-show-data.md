---
title: 显示用于创建 Power BI 可视化效果的数据
description: 本文介绍了如何显示用于创建 Power BI 视觉对象的数据，以及如何将此类数据导出到 .csv 文件中。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0ffb0a2e7bee17d71ca2037c8a233c2443ff1120
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292789"
---
# <a name="show-the-data-that-was-used-to-create-the-visualization"></a>显示用于创建可视化效果的数据
## <a name="show-data"></a>显示数据
Power BI 可视化效果是使用数据集中的数据创建的。 如果你对幕后感兴趣，可以使用 Power BI *显示* 用于创建视觉对象的数据。 在用户选择“显示数据”后，Power BI 在可视化效果下方（或旁边）显示数据。

还可以导出正在用于创建为.xlsx 或.csv 文件的可视化效果的数据，并在 Excel 中查看该数据。 有关详细信息，请参阅[从 Power BI 可视化效果导出数据](power-bi-visualization-export-data.md)。

> [!NOTE]
> “显示数据”和“导出数据”在 Power BI 服务和 Power BI Desktop 中均可用。 不过，Power BI Desktop 还进一步提供了其他详细信息；[显示记录显示数据集中的实际行](../desktop-see-data-see-records.md)。
> 
> 

## <a name="using-show-data-in-power-bi-service"></a>使用 Power BI 服务中的“显示数据”功能
1. 在 Power BI 服务中，以[阅读视图或编辑视图](../service-interact-with-a-report-in-editing-view.md)打开报表，然后选择一个视觉对象。  在 Power BI Desktop 中，打开“报表”视图。
2. 若要显示视觉对象背后的数据，请依次选择“浏览” > “显示数据”。
   
   ![选择“显示数据”](media/service-reports-show-data/power-bi-show-data.png)
3. 默认情况下，该数据将显示以下视觉对象。
   
   ![垂直显示视觉对象和数据](media/service-reports-show-data/power-bi-explore-show-data.png)
4. 若要更改方向，可从可视化效果的右上角选择垂直布局 ![](media/service-reports-show-data/power-bi-vertical-icon-new.png)。
   
   ![水平显示视觉对象和数据](media/service-reports-show-data/power-bi-explore-show-data2.png)
5. 若要将数据导出到 .csv 文件中，请依次选择省略号和“**导出数据**”。
   
    ![选择“导出数据”](media/service-reports-show-data/power-bi-export-data-new.png)
   
    有关将数据导出到 Excel 的详细信息，请参阅[从 Power BI 可视化效果导出数据](power-bi-visualization-export-data.md)。
6. 若要隐藏数据，请依次取消选择“浏览” > “显示数据”。

## <a name="next-steps"></a>后续步骤
[从 Power BI 可视化效果导出数据](power-bi-visualization-export-data.md)    
[Power BI 报表中的可视化效果](power-bi-report-visualizations.md)    
[Power BI 报表](../consumer/end-user-reports.md)    
更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


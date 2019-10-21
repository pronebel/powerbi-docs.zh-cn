---
title: 从 Power BI 视觉对象导出数据
description: 从报表视觉对象和仪表板视觉对象导出数据并在 Excel 中查看此数据。
author: mihart
manager: kvivek
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/11/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 80033cafbe66303a1d6f55bba61f7d19449dc45b
ms.sourcegitcommit: f34acbf9fb1ab568fd89773aaf412a847f88dd34
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589533"
---
# <a name="export-data-from-a-visual"></a>从视觉对象导出数据

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

若要查看用于创建视觉对象的数据，可以[在 Power BI 中显示该数据](end-user-show-data.md)或将这些数据导出到 Excel。 导出数据的选项需要某种类型或许可证以及对此内容的编辑权限。 如果无法导出，请与 Power BI 管理员联系。 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Power BI 仪表板上的视觉对象

1. 启动 Power BI 仪表板。 这里，我们使用的是“市场营销和销售示例”应用中的仪表板。 可以[从 AppSource.com 下载此应用](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282)。

    ![添加仪表板](media/end-user-export/power-bi-dashboards.png)

2. 将鼠标悬停在视觉对象上方以显示省略号 (...)，然后单击以显示“操作”菜单。

    ![选择省略号时显示的菜单](media/end-user-export/power-bi-action-menu.png)

3. 选择“导出到 Excel”  。

4. 接下来发生的情况取决于所使用的浏览器。 系统可能会提示你保存文件，或者你可能会在浏览器底部看到指向已导出文件的链接。 

    ![显示已导出文件链接的 Chrome 浏览器](media/end-user-export/power-bi-dashboard-exports.png)

5. 在 Excel 中打开该文件。  

    ![Excel 中的年初至今总单位数](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>从报表中的视觉对象
你可以从报表中的视觉对象以 .csv 或 .xlsx (Excel) 格式导出数据。 

1. 在仪表板上，选择磁贴以打开基础报表。  在此示例中，我们选择与上面相同的视觉对象，即“年初至今总单位数差额百分比”  。 

    ![突出显示的仪表板磁贴](media/end-user-export/power-bi-export-reports.png)

    由于此磁贴是从“销售和市场营销示例”  报表创建的，即打开的报表。 此外，其将打开包含选定磁贴视觉对象的页面。 

2. 在报表中选择该磁贴。 注意右侧的“筛选器”  窗格。 此视觉对象已应用筛选器。 若要了解有关筛选器的详细信息，请参阅[在报表中使用筛选器](end-user-report-filter.md)。

    ![选定的筛选器窗格](media/end-user-export/power-bi-export-filter.png)


3. 选择可视化效果右上角的省略号。 选择“导出数据”  。

    ![导出从下拉列表中选择的数据](media/end-user-export/power-bi-export-report.png)

4. 你将看到用于导出汇总数据或基础数据的选项。 如果你使用的是“销售和市场营销示例”  应用，将禁用“基础数据”  。 但你可能会遇到同时启用这两个选项的报表。 下面是有关不同点的说明。

    **汇总数据**：希望导出在视觉对象中看到的数据时可选择此选项。  这种类型的导出仅显示用于创建视觉对象的数据。 如果对视觉对象应用了筛选器，则也将筛选导出的数据。 例如，对于此视觉对象，导出将仅包括 2014 和中心区域的数据，并且仅包含以下四个制造商的数据：VanArsdel、Natura、Aliqui 和 Pirum。
  

    **基础数据**：如果你想要导出在视觉对象中看到的数据和  基础数据集中的其他数据，请选择此选项。  这可能包括数据集内包含但未在视觉对象中使用的数据。 

    ![从中选择基础或汇总数据的菜单](media/end-user-export/power-bi-export-option.png)

5. 接下来发生的情况取决于所使用的浏览器。 系统可能会提示你保存文件，或者你可能会在浏览器底部看到指向已导出文件的链接。 

    ![在 Microsoft Edge 浏览器中显示的已导出文件](media/end-user-export/power-bi-export-edge-browser.png)


6. 在 Excel 中打开该文件。 将导出的数据量与从仪表板上的同一个视觉对象导出的数据进行比较。 不同之处在于，此导出包括基础数据  。 

    ![示例 Excel](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>后续步骤

[显示用于创建视觉对象的数据](end-user-show-data.md)
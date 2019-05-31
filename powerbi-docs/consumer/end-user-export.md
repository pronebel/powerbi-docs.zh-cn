---
title: 从 Power BI 视觉对象导出数据
description: 从报表视觉对象和仪表板视觉对象导出数据，并在 Excel 中查看。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 4/9/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: d4384db8e05a69b138e76377e7c7b845867fa881
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61063622"
---
# <a name="export-data-from-visual"></a>从 visual 中导出数据
如果你想要查看的数据，用于创建视觉对象，[可以在 Power BI 中显示该数据](end-user-show-data.md)或将这些数据导出到 Excel。 导出数据的选项需要特定类型或许可证和编辑内容的权限。 如果不能导出，请与你的 Power BI 管理员。 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>从 Power BI 仪表板上的视觉对象

1. 开始在 Power BI 仪表板上。 此处我们使用从仪表板***市场营销和销售示例***应用。 你可以[下载此应用程序从 AppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282)。

    ![](media/end-user-export/power-bi-dashboard.png)

2. 悬停在视觉对象以显示省略号 （...），然后单击以显示操作菜单。

    ![](media/end-user-export/power-bi-dashboard-export-visual.png)

3. 选择**导出到 Excel**。

4. 接下来发生什么取决于您所使用的浏览器。 您可能会提示保存文件或您可能看到的浏览器的底部导出的文件的链接。 

    ![](media/end-user-export/power-bi-export-browser.png)

5. 在 Excel 中打开该文件。  

    ![](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>从报表中视觉对象
您可以将数据从报表中视觉对象导出为.csv 或.xlsx (Excel) 格式。 

1. 在仪表板中，选择磁贴以打开基础报表。  在此示例中，我们选择相同的版本按上面所述*总单位 ytd*。 

    ![](media/end-user-export/power-bi-export-report.png)

    由于从创建此磁贴*销售和市场营销示例*报表，即打开的报表。 它会打开包含所选磁贴视觉对象的页。 

2. 在报表中选择该磁贴。 请注意**筛选器**右侧的窗格。 此视觉对象已应用的筛选器。 若要了解有关筛选器的详细信息，请参阅[在报表中使用筛选器](end-user-report-filter.md)。

    ![](media/end-user-export/power-bi-export-filters.png)


3. 选择可视化效果右上角的省略号。 选择**导出数据**。

    ![](media/end-user-export/power-bi-export-report2.png)

4. 您将看到用于导出基础数据或汇总数据的选项。 如果您使用的*销售和市场营销示例*应用程序中，**基础数据**将被禁用。 但可能会遇到的报表中启用这两个选项。 下面是差异的说明。

    **汇总数据**： 如果你想要导出数据以供在视觉对象中看到的内容，请选择此选项。  这种类型的导出显示仅用于创建视觉对象的数据。 如果视觉对象已应用的筛选器，然后导出的数据也将进行筛选。 例如，此视觉对象导出将仅包含 2014 数据和中部地区和四个制造商的唯一数据：VanArsdel、 Natura、 Aliqui 和 Prirum。
  

    **基础数据**： 选择此选项，如果你想要导出数据以供在视觉对象中看到的内容**加上**来自基础数据集的其他数据。  这可能包括在数据集中包含但不是使用视觉对象中的数据。 

    ![](media/end-user-export/power-bi-export-report3.png)

5. 接下来发生什么取决于您所使用的浏览器。 您可能会提示保存文件或您可能看到的浏览器的底部导出的文件的链接。 

    ![](media/end-user-export/power-bi-export-edge.png)


7. 在 Excel 中打开该文件。 将数据导出到我们从仪表板上的相同视觉对象导出的数据量进行比较。 不同之处是此导出中包括**基础数据**。 

    ![](media/end-user-export/power-bi-underlying.png)


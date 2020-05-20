---
title: 如何从 Excel 将磁贴固定到 Power BI 仪表板
description: 在 OneDrive for Business 上从 Excel 将磁贴固定到 Power BI 仪表板 固定范围、图表、表
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: l8JoB7w0zJA
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 283b43ef60d88df64b66812956e79bdcce1f16e9
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565778"
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-excel"></a>从 Excel 将磁贴固定到 Power BI 仪表板
若要从 Excel 工作簿固定磁贴，请将该工作簿连接到 Power BI 服务 (app.powerbi.com)。 实际上，连接工作簿会将该工作簿链接的只读版本引入 Power BI 服务，并允许用户将区域固定到仪表板。 甚至可以将整个工作表固定到仪表板。  
如果已与你共享工作簿，你将能够查看由所有者固定的磁贴，但无法自行创建任何仪表板磁贴。 

有关 Excel 和 Power BI 如何协同工作的详细信息，请参阅[从 Excel 工作簿文件获取数据](https://go.microsoft.com/fwlink/?LinkID=521962)。

视频将演示几个从 Excel 工作簿导入数据并连接至此的方法。

<iframe width="560" height="315" src="https://www.youtube.com/embed/l8JoB7w0zJA" frameborder="0" allowfullscreen></iframe>

## <a name="connect-your-excel-workbook-from-onedrive-for-business-to-power-bi"></a>从 OneDrive for Business 将 Excel 工作簿连接到 Power BI
当你选择“连接”  时，你的工作簿将显示在 Power BI 中，就像在 Excel Online 中那样。 但与 Excel Online 不同，你会有一些出色的功能，可帮助你将各元素从你的工作表固定仪表板中。

不能在 Power BI 中编辑你的工作簿。 但如果需要进行一些更改，可以从工作区的“工作簿”  选项卡中选择“铅笔”图标，然后选择是在 Excel Online 中编辑工作簿，还是在计算机上的 Excel 中打开工作簿。 你所作的任何更改都会保存到 OneDrive 上的工作簿中。

1. 将你的工作簿上载到你的 OneDrive for Business。

2. 在 Power BI 中，[连接到该工作簿](../connect-data/service-excel-workbook-files.md)，方法是：选择“获取数据 > 文件 > OneDrive - Business”  并导航到保存 Excel 文件的位置。 选择该文件并选择“连接 > 连接”  。

    ![“OneDrive for Business”对话框](media/service-dashboard-pin-tile-from-excel/power-bi-connect.png)

3. 在 Power BI 中，该工作簿添加到工作区的“工作簿”  选项卡。  ![工作簿图标](media/service-dashboard-pin-tile-from-excel/pbi_workbookicon.png) 图标指示这是 Excel 工作簿，黄色星号指示这是新工作簿。
    
    ![“工作簿”选项卡](media/service-dashboard-pin-tile-from-excel/power-bi-workbooks.png)
4. 通过选择工作簿名称，在 Power BI 中打开工作簿。

    对 Power BI 中工作簿所做的更改不会被保存，并且不会影响 OneDrive for Business 上的原始工作簿。 如果在 Power BI 中排序、筛选或更改值，则无法保存或固定这些更改。 如需进行更改（将被保存），请选择右上角的“编辑”  将其打开，以便在 Excel Online 或 Excel 中进行编辑。 以这种方式进行的更改可能需要几分钟的时间来更新仪表板上的磁贴。
   
    ![Power BI 中的 Excel Online](media/service-dashboard-pin-tile-from-excel/power-bi-opened.png)

## <a name="pin-a-range-of-cells-to-a-dashboard"></a>将单元格的区域固定到仪表板
添加新[仪表板磁贴](../consumer/end-user-tiles.md)的一种方法是从 Power BI 中的 Excel 工作簿内部进行添加。 可从已保存至你的 OneDrive for Business 或另一个组共享的文档库中的 Excel 工作簿中固定范围。 范围可包含数据、图表、表、数据透视表、数据透视图和其他 Excel 部分。

1. 突出显示你想要固定到仪表板的单元格。
   
    ![选择 Excel 工作簿中的单元格](media/service-dashboard-pin-tile-from-excel/pbi_selectrange.png)
2. 选择固定 ![“固定”图标](media/service-dashboard-pin-tile-from-excel/pbi_pintile_small.png) 图标。 
3. 将磁贴固定到现有仪表板或新仪表板。 
   
   * 现有仪表板：从下拉列表中选择仪表板的名称。
   * 新仪表板：键入新仪表板的名称。
   
     ![“固定到仪表板”对话框](media/service-dashboard-pin-tile-from-excel/pbi_dashdialog1.png)
4. 选择**固定**。 一条成功消息（右上角附近）会告知你已将范围以磁贴的形式添加到你的仪表板中。 
   
    ![“已固定到仪表板”对话框](media/service-dashboard-pin-tile-from-excel/power-bi-go-to-dashboard.png)
5. 选择“转到仪表板”  。 在此处可以对已固定的可视化效果执行[重命名、重设大小、添加链接和移动](service-dashboard-edit-tile.md)操作。 默认情况下，选择固定的磁贴将在 Power BI 中打开工作簿。

## <a name="pin-an-entire-table-or-pivottable-to-a-dashboard"></a>将整个表或数据透视表固定到仪表板
按照上述步骤操作，只不过不选择单元格的区域，而是选择整个表或数据透视表。

要固定表，请选择表的整个区域，并确保包含标头。  要固定数据透视表，请确保包含数据透视表的每个可见部分，包括筛选器（如果使用的话）。

 ![选择单元格](media/service-dashboard-pin-tile-from-excel/pbi_selecttable.png)

从表或数据透视表创建的磁贴将显示整个表。  如果你在原始工作簿中添加/删除/筛选行或列，则也将在磁贴中添加/删除/筛选它们。

## <a name="view-the-workbook-linked-to-the-tile"></a>查看链接到磁贴的工作簿
选择工作簿磁贴将在 Power BI 中打开链接的工作簿。 由于工作簿文件位于该所有者的 OneDrive for Business 上，因此查看工作簿要求具有对该工作簿的读取权限。 如果没有权限，将收到一条错误消息。  

 ![视频](media/service-dashboard-pin-tile-from-excel/pin-from-excel.gif)

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
不支持的功能：Power BI 使用 Excel Services 来检索工作簿磁贴。 因此，由于 Excel 中的某些功能在 Excel Services REST API 中不受支持，因此将不会在 Power BI 中的磁贴上看到这些功能。 例如：迷你图、图标集条件格式设置和时间切片器。 有关不支持的功能的完整列表，请参阅 [Excel Services REST API 中不支持的功能](/sharepoint/dev/general-development/unsupported-features-in-excel-services-rest-api)

## <a name="next-steps"></a>后续步骤
[共享具有 Excel 工作簿链接的仪表板](../collaborate-share/service-share-dashboard-that-links-to-excel-onedrive.md)

[从 Excel 工作簿获取数据](../connect-data/service-excel-workbook-files.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

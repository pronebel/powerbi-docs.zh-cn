---
title: '在 Power BI 服务中通过 Excel 文件创建报表 '
description: 在 Power BI 服务中通过 Excel 文件创建 Power BI 报表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: 806198b783785a06562411b53f7bd6f644b16918
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388186"
---
# <a name="create-a-report-from-an-excel-file-in-the-power-bi-service"></a>在 Power BI 服务中通过 Excel 文件创建报表
你已经阅读了 [Power BI 中的报表](../consumer/end-user-reports.md)，并且现在想要创建你自己的仪表板。 有不同的方法可创建报表。 在本文中，我们首先通过 Excel 文件在 Power BI 服务中创建基本报表。 了解创建报表的基础知识后，请查看结尾处的[后续步骤](#next-steps)，以获取更高级的报表主题。  

## <a name="prerequisites"></a>必备组件
- [注册 Power BI 服务](../fundamentals/service-self-service-signup-for-power-bi.md)。 
- [下载零售分析示例 Excel 文件](https://go.microsoft.com/fwlink/?LinkId=529778)并将其保存到 OneDrive for Business 或本地。

## <a name="import-the-excel-file"></a>导入 Excel 文件
此创建报表的方法从文件和空白报表画布开始。 可从零售分析示例 Excel 文件中开始操作。

1. 在导航窗格中，选择“我的工作区”。
   
   :::image type="content" source="media/service-report-create-new/power-bi-select-my-workspace.png" alt-text="选择“我的工作区”的屏幕截图。":::
2. 从导航窗格底部，选择“获取数据”。
   
   ![获取数据](media/service-report-create-new/power-bi-get-data3.png)
3. 选择“文件”并导航到你保存零售分析示例的位置。
   
    ![选择“文件”](media/service-report-create-new/power-bi-select-files.png)
4. 对于此练习，请选择“导入”  。
   
   ![选择“导入”](media/service-report-create-new/power-bi-import.png)
5. 选择“打开”  。

   导入 Excel 文件后，该文件将作为数据集列于工作区列表中。

1. 选择数据集旁边的“更多选项(…)”，并选择“创建报表” 。
   
   :::image type="content" source="media/service-report-create-new/power-bi-dataset-create-report.png" alt-text="选择“创建报表”的屏幕截图。":::
6. 此时将打开报表编辑器。 
   
   ![报表编辑器的屏幕截图。](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> 选择菜单图标以隐藏导航窗格，从而留出更多空间。
> 
> :::image type="content" source="../media/power-bi-hide-navigation-pane.png" alt-text="选择菜单图标以隐藏导航窗格的屏幕截图。":::


## <a name="add-a-radial-gauge-to-the-report"></a>向报表添加径向仪表
在导入数据集后，我们来回答一些问题。  我们的首席营销官 (CMO) 想要知道我们距离本年度的销售目标还有多远。 仪表是用于显示此类信息的一个[不错的可视化效果选择](../visuals/power-bi-report-visualizations.md)。

1. 在“字段”窗格中，选择“**销售额**” > “**本年度销售额**” > “**值**”。
   
    ![报表编辑器中的条形图](media/service-report-create-new/power-bi-report-step1.png)
2. 从“可视化效果”窗格中，选择仪表模板![仪表图标](media/service-report-create-new/powerbi-gauge-icon.png)，将视觉对象转换为仪表。
   
    ![报表编辑器中的仪表视觉对象](media/service-report-create-new/power-bi-report-step2.png)
3. 将“销售额” > “本年度销售额” > “目标”拖动到“目标值”框。 似乎已经非常接近我们的目标。
   
    ![将目标作为目标值的仪表视觉对象](media/service-report-create-new/power-bi-report-step3.png)
4. 现在就可以保存报表了。
   
   ![“文件”菜单](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>向报表添加区域图表和切片器
CMO 还需要我们回答一些其他问题。 他们还希望了解本年度销售额与去年销售额的对比情况。 而且还希望按地区查看结果。

1. 首先，我们在画布上腾出一些空间。 选择仪表，并将它移动到右上角。 然后拖拽任一角并使其变小。
2. 取消选中仪表。 在“字段”窗格中，选择“销售额” > “本年度销售额” > “值”，然后选择“销售额” > “去年销售额”。
   
    ![具有仪表和条形图的报表编辑器](media/service-report-create-new/power-bi-report-step4.png)
3. 从“可视化效果”窗格中，选择区域图表模板![图表图标](media/service-report-create-new/power-bi-areachart-icon.png)，将视觉对象转换为区域图表。
4. 选择“时间” > “时间段”以将其添加到“轴”框。
   
    ![区域图表处于活动状态的报表编辑器](media/service-report-create-new/power-bi-report-step5.png)
5. 若要对可视化效果按时间段排序，请选择省略号，然后选择“按时间段排序”。
6. 现在添加切片器。 选择画布上的空白区域，然后选择“切片器”。 ![切片器图标](media/service-report-create-new/power-bi-slicer-icon.png) 模板。 现在画布上有一个空切片器。
   
    ![报表画布](media/service-report-create-new/power-bi-report-step6.png)    
7. 从“字段”窗格中，选择“地区” > 地区”。 移动切片器并重设切片器大小。
   
    ![报表编辑器，添加“地区”](media/service-report-create-new/power-bi-report-step7.png)  
8. 使用切片器按地区查找模式和见解。
   
   ![使用切片器的视频](media/service-report-create-new/power-bi-slicer-video2.gif)  

继续浏览数据并添加可视化效果。 当你发现尤为值得关注的见解时，[将它们固定到仪表板](service-dashboard-pin-tile-from-report.md)。

## <a name="next-steps"></a>后续步骤

* [将可视化对象固定到仪表板](service-dashboard-pin-tile-from-report.md)
* [更改 Power BI 服务中的报表设置](power-bi-report-settings.md)
* 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

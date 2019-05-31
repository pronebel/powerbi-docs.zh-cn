---
title: 从数据集中创建报表
description: 从数据集创建 Power BI 报表。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 6b69c2b1fa811d395a26403de852c44af33491c7
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770235"
---
# <a name="create-a-report-in-the-power-bi-service-by-importing-a-dataset"></a>通过导入数据集在 Power BI 服务中创建报表
你已经阅读了 [Power BI 中的报表](consumer/end-user-reports.md)，并且现在想要创建你自己的仪表板。 有不同的方式创建报表。 在本文中，我们将首先从 Excel 数据集在 Power BI 服务中创建基本报表。 一旦您了解创建报表的基础知识，请查看[后续步骤](#next-steps)末尾的详细信息高级报表主题。  

## <a name="prerequisites"></a>先决条件
- [注册 Power BI 服务](service-self-service-signup-for-power-bi.md)。 有关创建使用 Power BI Desktop 报表，请参阅[Desktop 报表视图](desktop-report-view.md)。 
- [下载零售分析示例 Excel 数据集](http://go.microsoft.com/fwlink/?LinkId=529778)并将其保存到 OneDrive for Business 中还是在本地。

## <a name="import-the-dataset"></a>导入数据集
此创建报表方法从数据集和空白报表画布开始。 您可以继续在零售分析示例 Excel 数据集。

1. 我们将在 Power BI 服务工作区中创建报表，因此选择现有的工作区或创建一个。
   
   ![应用工作区列表](media/service-report-create-new/power-bi-workspaces2.png)
2. 从左侧的导航窗格的底部，选择**获取数据**。
   
   ![获取数据](media/service-report-create-new/power-bi-get-data3.png)
3. 选择“文件”  并导航到你保存零售分析示例的位置。
   
    ![选择“文件”](media/service-report-create-new/power-bi-select-files.png)
4. 对于此练习，请选择“导入”  。
   
   ![选择“导入”](media/service-report-create-new/power-bi-import.png)
5. 在导入数据集后，选择“查看数据集”  。
   
   ![选择“查看数据集”](media/service-report-create-new/power-bi-view-dataset.png)
6. 查看数据集实际上将打开报表编辑器。  你将看到一个空白画布和报表编辑工具。
   
   ![报表编辑器](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> 如果熟悉报表编辑画布，或需复习，[的报表编辑器教程](service-the-report-editor-take-a-tour.md)然后再继续。 > 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>向报表添加径向仪表
在导入数据集后，我们来回答一些问题。  我们的首席营销官 (CMO) 想要知道我们距离本年度的销售目标还有多远。 仪表是用于显示此类信息的一个[不错的可视化效果选择](visuals/power-bi-report-visualizations.md)。

1. 在“字段”窗格中，选择“销售额”   > “本年度销售额”   > “值”  。
   
    ![报表编辑器中的条形图](media/service-report-create-new/power-bi-report-step1.png)
2. 从“可视化效果”窗格中，选择仪表模板![仪表图标](media/service-report-create-new/powerbi-gauge-icon.png)，将视觉对象转换为仪表  。
   
    ![报表编辑器中的仪表视觉对象](media/service-report-create-new/power-bi-report-step2.png)
3. 将“销售额”   > “本年度销售额”   > “目标”  拖动到“目标值”  框。 似乎已经非常接近我们的目标。
   
    ![将目标作为目标值的仪表视觉对象](media/service-report-create-new/power-bi-report-step3.png)
4. 现在可以保存您的报表的好时机。
   
   ![文件菜单](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>向报表添加区域图表和切片器
CMO 还需要我们回答一些其他问题。 她还希望了解本年度销售额与去年销售额的对比情况。 而且她希望按地区查看结果。

1. 首先，我们在画布上腾出一些空间。 选择仪表，并将它移动到右上角。 然后拖拽任一角并使其变小。
2. 取消选中仪表。 在“字段”窗格中，选择“销售额”   > “本年度销售额”   > “值”  ，然后选择“销售额”   > “去年销售额”  。
   
    ![具有仪表和条形图的报表编辑器](media/service-report-create-new/power-bi-report-step4.png)
3. 从“可视化效果”窗格中，选择区域图表模板![图表图标](media/service-report-create-new/power-bi-areachart-icon.png)，将视觉对象转换为区域图表  。
4. 选择“时间”   > “时间段”  以将其添加到“轴”  框。
   
    ![区域图表处于活动状态的报表编辑器](media/service-report-create-new/power-bi-report-step5.png)
5. 若要对可视化效果按时间段排序，请选择省略号，然后选择“按时间段排序”  。
6. 现在添加切片器。 选择画布上的空白区域，然后选择“切片器”。 ![切片器图标](media/service-report-create-new/power-bi-slicer-icon.png) 模板。 现在，我们在画布上了空的切片器。
   
    ![报表画布](media/service-report-create-new/power-bi-report-step6.png)    
7. 从“字段”窗格中，选择“地区”   > 地区”  。 移动切片器并重设切片器大小。
   
    ![报表编辑器，添加“地区”](media/service-report-create-new/power-bi-report-step7.png)  
8. 使用切片器按地区查找模式和见解。
   
   ![使用切片器的视频](media/service-report-create-new/power-bi-slicer-video2.gif)  

继续浏览数据并添加可视化效果。 当你发现尤为值得关注的见解时，[将它们固定到仪表板](service-dashboard-pin-tile-from-report.md)。

## <a name="next-steps"></a>后续步骤

* 了解如何[将可视化效果固定到仪表板](service-dashboard-pin-tile-from-report.md)   
* 更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


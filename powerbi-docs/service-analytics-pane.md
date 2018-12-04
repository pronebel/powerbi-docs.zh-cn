---
title: 创建视觉对象的动态参考行
description: 在 Power BI 服务中创建视觉对象的动态参考行
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: f3653404bb89674ce838cc326daefbaeaab4c8b8
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2018
ms.locfileid: "52830164"
---
# <a name="create-dynamic-reference-lines-for-visuals-in-the-power-bi-service"></a>在 Power BI 服务中创建视觉对象的动态参考行

通过 **Power BI 服务**的“**分析**”窗格，可以向可视化效果添加动态参考行，并重点关注重要趋势或见解。

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> 仅当在报表画布上选择视觉对象时才会显示“分析”窗格。
> 
> 

## <a name="use-the-analytics-pane"></a>使用“分析”窗格
通过“**分析**”窗格，可以创建以下类型的动态参考行（并非所有的行都适用于所有视觉对象类型）：

* X 轴恒线
* Y 轴恒线
* 最小值线
* 最大值线
* 平均线
* 中线
* 百分位数线


若要查看视觉对象的可用动态参考行，请按照下列步骤操作：

1. 选择或创建视觉对象，然后从“**可视化效果**”窗格选择“**分析**”图标 ![](media/service-analytics-pane/power-bi-analytics-icon.png)。

2. 为想要创建的行类型选择向下箭头以展开其选项。 本示例中将选择“**平均线**”。
   
   ![添加平均线](media/service-analytics-pane/power-bi-add.png)

3. 若要创建新行，请选择“+ 添加”并确定用于创建行的度量值。  “度量值”下拉列表中会自动填充来自选定可视化对象的可用数据。 让我们使用“打开商店计数”。

5. 对于线条提供了各种选项，例如可以颜色、透明度、样式和位置（与视觉对象的数据元素相关）。 若要为线条添加标签，请为它提供一个标题，然后将“数据标签”滑块移至“开”。  在本示例中，我们为该线条指定标题“平均# 打开商店”，并对其他几个选项进行自定义，如下所示。
   
   ![自定义平均线分析](media/service-analytics-pane/power-bi-average-line2.png)

1. 请注意“**分析**”窗格中的“**平均线**”项旁显示的数目。 它指出目前在视觉对象上所拥有的动态行的数量和类型。 如果添加了“常量行”作为商店数目标 9，则可以看到“分析”窗格显示现在也有适用于此视觉对象的“常量行”参考。
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   

通过使用“**分析**”窗格创建动态参考行，可以突出显示各种有趣的见解。

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

如果所选择的视觉对象不能具有对其适用的动态参考行（本示例中为**映射**视觉对象），则会在选择“**分析**”窗格时看到以下信息。
   
![分析不可用](media/service-analytics-pane/power-bi-no-lines.png)

是否能使用动态参考行取决于正在使用的视觉对象的类型。 下表显示动态行当前适用的视觉对象：

动态行完全适用于以下视觉对象：

* 分区图
* 折线图
* 散点图
* 簇状柱形图
* 簇状条形图

以下视觉对象仅能使用“**分析**”窗格中的恒线：

* 堆积面积图
* 堆积条形图
* 堆积柱形图
* 百分比堆积条形图
* 百分比堆积柱形图

对于以下视觉对象，趋势线是当前仅有的选项：

* 非堆积折线图
* 簇状柱形图

最后，非笛卡尔视觉对象当前无法应用“**分析**”窗格中的动态行，例如：

* 矩形图
* 饼图
* 圆环图
* 表

## <a name="next-steps"></a>后续步骤
[Power BI Desktop 中的分析窗格](desktop-analytics-pane.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


---
title: Power BI 支持的见解类型
description: 使用 Power BI 查看快速见解和视图见解。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 75462c2414854d0848254a36b89bcdd1de365ec5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863488"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Power BI 支持的见解类型

Power BI 服务可以在仪表板或报表中自动查找见解。

## <a name="how-does-insights-work"></a>见解的工作原理
Power BI 快速搜索数据集的不同子集。 在搜索时，Power BI 会应用一组复杂的算法来发现可能有意义的见解。 Power BI 会在预定时间内扫描数据集中尽可能多的内容。

可以针对数据集或仪表板磁贴运行见解。   

## <a name="what-types-of-insights-can-we-find"></a>我们可以发现哪些类型的见解？
以下是我们所使用的一些算法：

## <a name="category-outliers-topbottom"></a>类别离群值（上/下）
针对模型中的度量值，突出显示维度的一或两个成员值远大于维度的其他成员值的情况。  

![类别离群值示例](./media/end-user-insight-types/pbi-auto-insight-types-category-outliers.png)

## <a name="change-points-in-a-time-series"></a>更改时序中的点
突出显示数据时序中的趋势明显变化的情况。

![更改时序示例中的点](./media/end-user-insight-types/pbi-auto-insight-types-changepoint.png)

## <a name="correlation"></a>关联
检测当根据数据集中的某个维度绘制多个度量值时，多个度量值彼此之间显示关联的情况。

![关联示例](./media/end-user-insight-types/pbi-auto-insight-types-correlation.png)

## <a name="low-variance"></a>低方差
检测数据点不偏离平均值的情况。

![低方差示例](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>多数（主要因素）
查找当总值由另一个维度分解时，其多数可能归因于单一因素的情况。  

![主要因素示例](./media/end-user-insight-types/pbi-auto-insight-types-majority.png)

## <a name="overall-trends-in-time-series"></a>时序中的整体趋势
检测时序数据中的向上或向下趋势。

![时序示例中的整体趋势](./media/end-user-insight-types/pbi-auto-insight-types-trend.png)

## <a name="seasonality-in-time-series"></a>时序中的季节性
查找时序数据中的周期模式，例如每周、每月或每年的季节性。

![季节性示例](./media/end-user-insight-types/pbi-auto-insight-types-seasonality-new.png)

## <a name="steady-share"></a>稳定份额
突出显示子值的份额相对于跨连续变量的整体父值有父子关联的情况。

![稳定份额示例](./media/end-user-insight-types/pbi-auto-insight-types-steadyshare.png)

## <a name="time-series-outliers"></a>时序离群值
针对跨时序的数据，检测特定日期或时间值明显不同于其他日期/时间值的情况。

![时序离群值示例](./media/end-user-insight-types/pbi-auto-insight-types-time-series-outliers.png)

## <a name="next-steps"></a>后续步骤
[Power BI 见解](end-user-insights.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


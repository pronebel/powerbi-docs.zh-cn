---
title: Power BI 的 IT 支出分析示例：参观
description: Power BI 的 IT 支出分析示例：参观
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/20/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 3fc93f255d6645ffa6f15676b9a70f24326fcfdc
ms.sourcegitcommit: a2c4f912af1729fdfdf20369bf3eff67c3927eec
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67349282"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Power BI 的 IT 支出分析示例：参观

## <a name="overview-of-the-it-spend-analysis-sample"></a>“IT 支出分析示例”概述
IT 支出分析示例内容包中有仪表板、报表和数据集，分析了 IT 部门的计划成本与实际成本。 这种比较可以帮助我们了解公司年度计划的效果如何并调查与计划有巨大偏差的区域。 此示例中的公司经历了一个年度计划周期，然后按季度生成新的最新估计 (LE)，以帮助分析会计年度中的 IT 支出变化。

![IT 支出分析示例仪表板](media/sample-it-spend/it1.png)

此示例是一系列示例的一部分，展示了如何将 Power BI 与面向业务的数据、报表和仪表板结合使用。 它是使用 [obviEnce](http://www.obvience.com/) 提供的真实数据（已经过匿名处理）进行创建。 数据可采用以下几种格式：内容包/应用、.pbix Power BI Desktop 文件或 Excel 工作簿。 请参阅[用于 Power BI 的示例](sample-datasets.md)。 

本教程使用 Power BI 服务和 IT 支出分析示例内容包。 由于报表体验非常相似，因此也可以使用 Power BI Desktop 和示例 .pbix 文件跟着本教程一起操作。

## <a name="prerequisites"></a>先决条件

 必须先将示例下载为[内容包](#get-the-content-pack-for-this-sample)、[.pbix 文件](#get-the-pbix-file-for-this-sample)或 [Excel 工作簿](#get-the-excel-workbook-for-this-sample)，然后才能使用它。

### <a name="get-the-content-pack-for-this-sample"></a>获取内容包形式的此示例

1. 打开并登录 Power BI 服务 (app.powerbi.com)，然后打开要在其中保存此示例的工作区。

2. 选择左下角的“获取数据”  。
   
   ![选择“获取数据”](media/sample-datasets/power-bi-get-data.png)
3. 在随即显示的“获取数据”  页上，选择“示例”  。
   
4. 依次选择“IT 支出分析示例”  和“连接”  。  
  
   ![连接到示例](media/sample-it-spend/it-connect.png)
   
5. 此时，Power BI 导入内容包，然后向当前工作区添加新的仪表板、报表和数据集。
   
   ![IT 支出分析示例条目](media/sample-it-spend/it-spend-analysis-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>获取 .pbix 文件形式的此示例

也可以将此 IT 支出分析示例下载为 [.pbix 文件](http://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix)，这是专用于 Power BI Desktop 的文件格式。

### <a name="get-the-excel-workbook-for-this-sample"></a>获取 Excel 工作簿形式的此示例

若要查看此示例的数据源，还可以将它下载为 [Excel 工作簿](http://go.microsoft.com/fwlink/?LinkId=529783)。 该工作簿包含你可以查看和修改的 Power View 工作表。 若要查看原始数据，请启用“数据分析”加载项，再依次选择“Power Pivot”>“管理”  。 若要启用 Power View 和 Power Pivot 加载项，请参阅[从 Excel 本身内查看 Excel 示例](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself)，以了解详细信息。

## <a name="it-spend-analysis-sample-dashboard"></a>IT 支出分析示例仪表板
仪表板左侧有两个数字磁贴，分别为“与计划差异(%)”  和“与第 3 季度最新估计差异(%)”  ，它们提供了与计划和最新季度估计（LE3 = 第 3 季度最新估计）相比的实际支出概况。 总体上，我们与计划大约有 6% 的差异。 接下来，将探索导致此差异产生的原因：时间、地点和类别。

## <a name="ytd-it-spend-trend-analysis-page"></a>“年初至今 IT 支出趋势分析”页
选择“与计划差异(%)(按销售区域)”  仪表板磁贴后，便会看到“IT 支出分析示例”报表的“年初至今 IT 支出趋势分析”  页。 一目了然的是，在美国和欧洲，差异为正；在加拿大、拉丁美洲和澳大利亚差异为负。 美国大约有 6% 的正 LE 差异，而澳大利亚则大约有 7% 的负 LE 差异。

![差额计划百分比（按销售区域）](media/sample-it-spend/it2.png)

不过，只查看此图而得出的结论可能会造成误导。 我们需要查看实际的美元金额，才可透彻地了解状况。

1. 选择“与计划差异(%)(按销售区域)”  图中的“澳大利亚和新西兰”  ，然后观察“与计划差异(按 IT 领域)”  图。

   ![“年初至今 IT 支出趋势分析”页](media/sample-it-spend/it3.png)
2. 现在，请选择**美国**。 我们注意到，与美国相比，澳大利亚和新西兰只占总支出的很小一部分。

    接下来，将探索是美国的哪个类别造成了差异。

## <a name="ask-questions-of-the-data"></a>提出有关数据的问题
1. 选择顶部导航栏中的“IT 支出分析示例”  ，以返回到示例仪表板。
2. 选择“询问数据相关问题”  。
3. 在左侧的“入门问题”  列表中，选择“什么是‘计划成本(按 IT 领域)’”  。

   ![“计划成本(按 IT 领域)”图](media/sample-it-spend/it-area-chart.png)

4. 在问答框中，清除旧条目，并输入“显示‘与计划差异(%)和与 LE3 差异(%)(按 IT 领域)’条形图”  。

   ![“与计划差异(%)和与 LE3 差异(%)(按 IT 领域)”图](media/sample-it-spend/it4.png)

   在第一个 IT 领域“基础设施”  中，我们注意到，与计划初始差异百分比和与计划最新估计差异百分比相差非常大。

## <a name="ytd-spend-by-cost-elements-page"></a>“年初至今支出(按成本元素)”页

1. 返回到仪表板，并查看“与计划差异(%)和与第 3 季度最新估计差异(%)”  仪表板磁贴。

   ![“与计划差异(%)和与 LE3 差异(%)”磁贴](media/sample-it-spend/it5.png)

   我们注意到，“基础设施”领域因为与计划有很大正差异而凸显出来。

1. 选择此磁贴，以打开报表并查看“年初至今支出(按成本元素)”  页。
2. 选择右下角“与计划差异(%)和与 LE3 差异(%)(按 IT 领域)”  图中的“基础设施”  条形，并观察左下角“与计划差异(%)(按销售区域)”  图中的与计划差异值。

    ![“年初至今支出(按成本元素)”页](media/sample-it-spend/it6.png)
3. 依次选择“成本元素组”  切片器中的每个名称，以找到差异最大的成本元素。
4. 选择“其他”  后，选择“IT 领域”  切片器中的“基础设施”  ，并选择“IT 子领域”  切片器中的子领域，以找到差异最大的子领域。  

   我们注意到，“网络”  的差异大。 显然，这家公司决定了为员工提供电话服务福利，尽管这项举措并不在计划中。

## <a name="plan-variance-analysis-page"></a>“分析与计划差异”页

1. 选择页面底部的“分析与计划差异”  选项卡。

2. 在左侧的“与计划差异和与计划差异(%)(按业务领域)”  图中，选择“基础设施”  柱形，以在页面的其余部分中突出显示基础设施业务领域值。

    ![“分析与计划差异”页](media/sample-it-spend/it7.png)

   我们注意到，在“与计划差异(%)(按月份和业务领域)”  图中，基础设施业务领域在 2 月开始出现正差异。 另外，我们还注意到，与其他所有业务领域相比，基础设施业务领域的与计划差异值因国家/地区而异。 

3. 使用右侧的“IT 领域”  和“IT 子领域”  切片器，以筛选页面剩余部分中的值，并浏览数据。 

## <a name="edit-the-report"></a>编辑报表
选择左上角的“编辑报表”  ，以在编辑视图中进行探索：

* 了解报表页的组成部分、每个图表中有哪些字段、报表页上有哪些筛选器。
* 添加基于相同数据的报表页和图表。
* 更改每个图表的可视化效果类型。
* 将相关图表固定到仪表板。

可以在此环境中安全操作，因为能够选择不保存更改。 不过，如果确实保存了更改，可随时选择“获取数据”  来获取此示例的新副本。

## <a name="next-steps-connect-to-your-data"></a>后续步骤：连接到数据
我们希望本教程介绍了 Power BI 仪表板、问题解答和报表如何能够帮助深入了解 IT 支出数据。 现在轮到你了；立即连接到你自己的数据。 借助 Power BI，可以连接到各种数据源。 若要了解详细信息，请参阅 [Power BI 服务入门](service-get-started.md)。

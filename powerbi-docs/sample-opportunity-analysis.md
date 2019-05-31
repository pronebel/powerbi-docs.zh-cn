---
title: Power BI 的机会分析示例：参观
description: Power BI 的机会分析示例：参观
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 7f7b9d09b3761a5a02bdf4f706c6470b7d8cf2b6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61231207"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Power BI 的机会分析示例：参观

## <a name="overview-of-the-opportunity-analysis-sample"></a>“机会分析示例”概述
“机会分析示例”  包含采用以下 2 种销售渠道的软件公司的仪表板（和关联报表）：直接销售  和合作伙伴销售  。 销售经理创建此仪表板以按照区域、成交额和渠道来跟踪商机和收入。

销售管理系统依赖于两个收入度量值：

* **收入** – 这是销售人员对他认为的未来收入的估计值。
* **系数收入** – 该收入按“收入 X 概率百分比”计算，普遍认为这是对实际销售收入更为准确的预测指标。 概率由交易的当前***销售阶段***所决定。
  * 潜在客户 – 10%  
  * 授予资格 – 20%  
  * 解决方案 – 40%  
  * 提议 – 60%  
  * 达成 – 80%

  ![](media/sample-opportunity-analysis/opportunity1.png)

此示例是一系列教程的一部分，该系列教程阐明如何将 Power BI 与面向业务的数据、报表及仪表板搭配使用。 这些来自 obviEnce [(www.obvience.com)](http://www.obvience.com/) 的真实数据都已进行匿名处理。

## <a name="prerequisites"></a>先决条件

 必须先将示例下载为[内容包](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample)、[.pbix 文件](http://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix)或 [Excel 工作簿](http://go.microsoft.com/fwlink/?LinkId=529782)，然后才能使用它。

### <a name="get-the-content-pack-for-this-sample"></a>获取内容包形式的此示例

1. 打开并登录 Power BI 服务 (app.powerbi.com)。
2. 在左下角，选择“**获取数据**”。
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. 在显示的“获取数据”页上选择“**示例**”图标。
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. 依次选择“机会分析示例”  和“连接”  。  
  
   ![获取数据](media/sample-opportunity-analysis/opportunity-connect.png)
   
5. Power BI 导入内容包，并将新的仪表板、报表和数据集添加到当前工作区。 新的内容会以黄色星号标记。 
   
   ![星号](media/sample-opportunity-analysis/opportunity-asterisk.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>获取 .pbix 文件形式的此示例

也可以将此示例下载为 .pbix 文件，这是专为 Power BI Desktop 量身定制的文件格式。 

 * [机会分析示例](http://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>获取 Excel 工作簿形式的此示例
还可以针对此示例[仅下载该数据集（Excel 工作簿）](http://go.microsoft.com/fwlink/?LinkId=529782)。 该工作簿包含你可以查看和修改的 Power View 工作表。 若要查看原始数据，请选择“Power Pivot”>“管理”  。


## <a name="what-is-our-dashboard-telling-us"></a>仪表板告诉我们什么？
我们的销售经理已创建了一个仪表板，用于跟踪对她而言至关重要的这些指标。 当她看到感兴趣的内容时，她可以选择磁贴以进一步研究该数据。

1. 公司收入为 20 亿美元，系数收入为 46100 万美元。
2. 机会计数和收入遵循熟悉的漏斗模式，总计在每个后一阶段递减。
3. 大多数机会都在东部区域。
4. 大型机会比中小型机会获得的收入更多。
5. 合作伙伴大型交易能产生更多收入：平均 800 万美元对比直接销售的 600 万美元。

由于无论交易被划分为大型、中型还是小型，达成交易所做的工作都是一样的，因此公司应深入挖掘数据，以更多地了解大型机会。

选择**合作伙伴驱动的机会计数和销售阶段**磁贴以打开报表的第 1 页。  
![](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>浏览报表中的各页
### <a name="page-1-of-our-report-is-titled-opportunity-count-overview"></a>报表的第 1 页标题为“机会计数概述”。
![](media/sample-opportunity-analysis/opportunity3.png)

* 就机会计数而言，东部是我们最大的区域。  
* 在饼图上，每次选择一个区域以筛选页面。 对于每个区域，合作伙伴都在寻找显著更多的大型机会。   
* “合作伙伴驱动的机会计数和机会大小”柱形图清楚表明，大部分大型机会都是合作伙伴驱动的，而大部分中小型机会则不是。
* 选择左下方条形图中的每个销售阶段，查看区域计数中的差异。请注意，就计数而言，虽然东部是我们最大的区域，但“解决方案”、“提议”和“达成”阶段这所有 3 个区域的计数也不相上下。 这意味着我们在中部和西部的成交百分比更高。

### <a name="page-2-of-our-report-is-titled-revenue-overview"></a>报表的第 2 页标题为“收入概述”。
此页使用收入方面而非计数来研究相似数据。  
![](media/sample-opportunity-analysis/opportunity4.png)

* 东部是我们最大的区域，这不仅体现在机会计数方面，而且还体现在收入方面。  
* 按合作伙伴驱动筛选（选择图例右上方的**是**）显示的收入是 15 亿美元和 29400 万美元。 将此与非合作伙伴驱动的 6440 亿美元和 16600 万美元收入进行对比。  
* 如果机会是合作伙伴驱动的，那么针对大客户的平均收入（800 万）比非合作伙伴驱动的收入（600 万）更高。  
* 对于合作伙伴驱动的业务，大型机会的平均收入几乎是中型机会（400 万）的两倍。  
* 但合作伙伴驱动的和非合作伙伴驱动的小型和中型这两种业务的平均收入却大致相当。   

很明显，合作伙伴在销售给顾客这方面表现得更好。  这样就很容易理解漏斗图中通过合作伙伴的交易更多了。

### <a name="page-3-of-our-report-is-titled-region-stage-counts"></a>报表第 3 页标题为“区域阶段计数”。
此页研究相似数据，但是是按区域和阶段细分说明的。  
![](media/sample-opportunity-analysis/opportunity5.png)

* 按东部筛选（选择饼图中的**东部**）显示的是，东部机会在合作伙伴驱动和非合作伙伴驱动之间几乎相等。
* 大型机会在中部区域最常见，小型机会在东部区域最常见，而中型机会在西部区域最常见。

### <a name="page-4-of-our-report-is-titled-upcoming-opportunities"></a>报表的第 4 页标题为“即将到来的机会”。
同样，我们也会采用相似的数据，但这一次是从日期/时间的角度来研究。  
![](media/sample-opportunity-analysis/opportunity6.png)

我们的 CFO 使用此页来管理工作负荷。 通过查看按销售阶段和月份划分的收入机会，她可以进行适当规划。

* “达成”阶段的平均收入最高。 达成这些交易是第一优先。
* 按月份筛选（通过选择左扇区中的月份名称）显示的是，在“达成”阶段，1 月的大型交易比例较高，系数收入为 7500 万美元。 另一方面，在“解决方案”和“提议”阶段，2 月大部分都是中型交易。
* 一般来说，系数收入额会基于销售阶段、机会数和交易大小而波动。 针对这些方面添加筛选器（使用右侧的筛选器窗格），进一步研究这些数据。

这是一个安全的试验环境。 你可以始终选择不保存所做的更改。 但是，如果保存更改，则可以始终转到**获取数据**来获取本示例的新副本。

## <a name="next-steps-connect-to-your-data"></a>后续步骤：连接到数据
本教程讨论了 Power BI 仪表板、问答和报表如何能够帮助深入了解机会跟踪数据。 现在轮到你了 — 连接到你自己的数据 借助 Power BI，你可以连接到各种数据源。 了解 [Power BI 入门](service-get-started.md)的详细信息。

[下载示例](sample-datasets.md)  

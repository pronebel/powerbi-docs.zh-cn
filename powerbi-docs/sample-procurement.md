---
title: 采购分析示例：参观
description: Power BI 的采购分析示例：参观
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 0998ebec15a4e02262ab54a3b08593a65f37af4e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873855"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Power BI 的采购分析示例：参观

“采购分析示例”内容包包含一个仪表板、报告和数据集，按类别和位置分析制造公司对供应商的支出。 本示例探讨以下几方面：

* 首选供应商有哪些
* 我们在哪些类别上的支出最多
* 哪些供应商给我们最高折扣以及在何时给我们最高折扣

![采购分析示例仪表板](media/sample-procurement/procurement1.png)

此示例是一系列示例的一部分，展示了如何将 Power BI 与面向业务的数据、报表和仪表板结合使用。 它是使用 [obviEnce](http://www.obvience.com/) 依据真实数据（已经过匿名处理）进行创建的。 数据可采用以下几种格式：内容包、.pbix Power BI Desktop 文件或 Excel 工作簿。 请参阅[用于 Power BI 的示例](sample-datasets.md)。 

本教程探讨了 Power BI 服务中的采购分析示例内容包。 由于报表体验在 Power BI Desktop 和服务中非常相似，因此也可以使用 Power BI Desktop 中的示例 .pbix 文件跟着本教程一起操作。 

不需要 Power BI 许可证即可在 Power BI Desktop 中查看示例。 如果没有 Power BI Pro 许可证，可以将该示例保存到 Power BI 服务中的“我的工作区”。 

## <a name="get-the-sample"></a>获取示例

必须先将示例下载为[内容包](#get-the-content-pack-for-this-sample)、[.pbix 文件](#get-the-pbix-file-for-this-sample)或 [Excel 工作簿](#get-the-excel-workbook-for-this-sample)，然后才能使用它。

### <a name="get-the-content-pack-for-this-sample"></a>获取内容包形式的此示例

1. 打开并登录 Power BI 服务 (app.powerbi.com)，然后打开要在其中保存此示例的工作区。 

    如果没有 Power BI Pro 许可证，可以将该示例保存到“我的工作区”。

2. 选择左下角的“获取数据”  。

    ![选择“获取数据”](media/sample-datasets/power-bi-get-data.png)
3. 在随即显示的“获取数据”  页上，选择“示例”  。

4. 依次选择“采购分析示例”  和“连接”  。  
  
   ![连接到示例](media/sample-procurement/procurement1a.png)
   
5. 此时，Power BI 导入内容包，然后向当前工作区添加新的仪表板、报表和数据集。
   
   ![采购分析示例条目](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>获取 .pbix 文件形式的此示例

也可以将此采购分析示例下载为 [.pbix 文件](https://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix)，这是专用于 Power BI Desktop 的文件格式。 

### <a name="get-the-excel-workbook-for-this-sample"></a>获取 Excel 工作簿形式的此示例

若要查看此示例的数据源，还可以将它下载为 [Excel 工作簿](https://go.microsoft.com/fwlink/?LinkId=529784)。 该工作簿包含你可以查看和修改的 Power View 工作表。 若要查看原始数据，请启用“数据分析”加载项，再依次选择“Power Pivot”>“管理”  。 若要启用 Power View 和 Power Pivot 加载项，请参阅[从 Excel 本身内查看 Excel 示例](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself)，以了解详细信息。


## <a name="spending-trends"></a>支出趋势
我们先来看按类别和位置划分的支出趋势。  

1. 在保存示例的工作区中，打开“仪表板”  选项卡，然后找到“采购分析示例”  仪表板，并选择它。 
2. 选择仪表板磁贴，“按国家/地区划分的发票总计”  ，将打开“采购分析示例”  报表的“支出概况”  页。

    ![“支出概况”页](media/sample-procurement/procurement2.png)

请注意下列详细信息：

* 在“按月份和类别划分的发票总计”  折线图中，“直接”  类别的支出相当一致，“物流”  的支出高峰为十二月，而“其他”  支出在二月有所激增。
* 在“按国家/地区划分的发票总计”  地图中，我们大部分的支出都是在美国。
* 在“按子类别划分的发票总计”  柱形图中，“硬件”  和“间接货物与服务”  是最大的支出类别。
* 在“按层划分的发票总计”  条形图中，我们大多数的业务都是与第 1 层（前 10 大）供应商合作完成的。 这样做使我们能够管理更好的供应商关系。

## <a name="spending-in-mexico"></a>墨西哥的支出
让我们来浏览墨西哥的支出部分。

1. 在“按国家/地区划分的发票总计”  地图中，选择“墨西哥”  气泡。 请注意，在“按子类别划分的发票总计”  柱形图中，大部分支出都在“间接货物与服务”  子类别中。

   ![在“支出概况”页中选择“墨西哥”](media/sample-procurement/pbi_procsample_spendmexico.png)
2. 向下钻取到**间接货物与服务**列：

   * 在“按子类别划分的发票总计”  图表中，选择图表右上角的向下钻取箭头![向下钻取箭头](media/sample-procurement/pbi_drilldown_icon.png)。
   * 选择**间接货物与服务**列。

      如你所见，目前为止最高支出为“销售和市场营销”  子类别。
   * 在地图上再次选择**墨西哥**。

      对于墨西哥，最大支出为“维护与修复”  子类别。

      ![墨西哥“间接货物与服务”向下钻取](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. 选择图表左上角的向上箭头，以重新向上钻取。
4. 再次选择向下钻取箭头，即可关闭向下钻取。  
5. 在顶部导航窗格中选择“采购分析示例”以返回到仪表板  。

## <a name="evaluate-different-cities"></a>评估不同的城市
我们可以使用突出显示来评估不同的城市。

1. 选择仪表板磁贴，“按月份划分的发票总计、折扣百分比”  ，将打开“采购分析示例”  报表的“折扣分析”  页。
2. 在“按城市划分的发票总计”  树状图中，依次选择每个城市，以查看城市的比较结果。 请注意，几乎所有迈阿密的发票都来自第 1 层供应商。

   ![按层划分的城市和折扣百分比](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>供应商折扣
接着，我们来探索供应商提供的折扣和我们获得最多折扣的时间段：
* 每个月的折扣是不同的还是保持不变？
* 部分城市的折扣比其他城市多吗？

![“折扣分析”页](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>按月份划分的折扣
如果查看“按月份划分的发票总计与折扣百分比”  组合图时，我们发现二月是最繁忙的月份，而九月是最不忙的月份。 

查看这些月份期间的折扣百分比：当交易量增加时，折扣减少，当交易量减少时，折扣增加。 在我们越需要折扣时，交易反而越不划算。

![按月份划分的发票总计和折扣百分比图表](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>按城市划分的折扣
另一个要浏览的部分是按城市划分的折扣。 依次选择树状图中的每个城市，并查看其他图表有哪些变化：

* 圣路易斯的二月发票总计大增，并在四月因为折扣节省而大降。
* 墨西哥城享有最高折扣率 (11.05%)，而亚特兰大折扣率最低 (0.08%)。

![墨西哥城折扣关系图](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>编辑报表
选择左上角的“编辑报表”  ，并在“编辑”视图中浏览：

* 了解如何制作页面。
* 根据相同的数据添加页面和图表。
* 更改图表的可视化效果类型；例如，将树状图更改为环形图。
* 将图表固定到仪表板。

## <a name="next-steps-connect-to-your-data"></a>后续步骤：连接到数据
可以在此环境中安全操作，因为能够选择不保存更改。 不过，如果确实保存了更改，可随时选择“获取数据”  来获取此示例的新副本。

我们希望本教程已经演示 Power BI 仪表板、问答和报表如何能够帮助深入了解示例数据。 现在轮到你了；立即连接到你自己的数据。 借助 Power BI，可以连接到各种数据源。 若要了解详细信息，请参阅 [Power BI 服务入门](service-get-started.md)。


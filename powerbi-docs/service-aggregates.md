---
title: 使用 Power BI 服务中的聚合函数（求和、平均值等）
description: 了解如何在 Power BI 服务中更改图表中的聚合函数（求和、平均值、最大值等）。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "65710651"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>使用 Power BI 服务中的聚合函数（求和、平均值等）

## <a name="what-is-an-aggregate"></a>什么是聚合函数？

有时需要通过数学方式合并数据中的值。 数学运算可以是求和、平均值、最大值、计数等。 当合并数据中的值时，就称为聚合  。 该数学运算的结果是聚合  。

当 Power BI 服务和 Power BI Desktop 创建可视化效果时，可聚合数据。 通常聚合函数就是你所需的，但有些时候可能需要以不同的方式聚合这些值。  例如，求和与求平均值。 有多种不同的方式来管理和更改在可视化效果中 Power BI 使用的聚合函数。

首先，让我们看一看数据类型，因为数据类型决定了 Power BI 聚合数据的方式以及是否可聚合  。

## <a name="types-of-data"></a>数据类型

大多数数据集都具有多种数据类型。 按照最基本的级别，数据要么是数值要么是其他。 Power BI 可以使用求和、平均值、计数、最小值、方差及其他方式聚合数值数据。 该服务甚至可以聚合文本数据（通常称为分类数据）  。 如果尝试聚合分类字段（将其放置在“值”或“工具提示”等仅限数值的存储桶中），Power BI 可以计算每个类别的出现次数或非重复出现次数   。 日期等特殊类型的数据有其自带的几个聚合选项：最早、最新、第一个和最后一个。

在下面的示例中：

- “销售量”  和“生产价格”  为包含数值数据的列

-  “分段”、  “国家/地区”、  “产品”、  “月份”和  “月份名称”包含分类数据

   ![示例数据集的屏幕截图。](media/service-aggregates/power-bi-aggregate-chart.png)

当在 Power BI 中创建可视化效果时，该服务将通过某些分类字段聚合数值字段（默认值为求和）  。  例如，“按产品的销售量”、“按月份的销售量”和“按市场分区的生产价格”。 Power BI 将引用一些数值字段作为度量值  。 在 Power BI 报表编辑器中很容易识别度量值 - 在“字段”列表中显示的度量值带有 ∑ 符号  。 有关详细信息，请参阅[报表编辑器...教程](service-the-report-editor-take-a-tour.md)。

![标出“字段”列表的 Power BI 屏幕截图。](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>为什么聚合不按我希望的方式运行？

在 Power BI 服务中使用聚合可能会令人困惑。 也许你有一个数字字段，但 Power BI 不允许更改聚合函数。 或者，你可能有一个字段（如年份），但你并不希望进行聚合，只是想计算它的出现次数。

通常情况下，根本问题是数据集中的字段定义。 数据集所有者可能将该字段定义为文本，这就解释了 Power BI 无法求和或求平均值的原因。 遗憾的是，[只有数据集所有者才能更改字段的分类方式](desktop-measures.md)。 因此，如果你具有数据集所有者权限，则在 Desktop 或用于创建数据集的程序（如 Excel）中均可解决此问题。 否则，请联系数据集的所有者，以寻求帮助。  

本文结尾部分特别提供了[注意事项和故障排除](#considerations-and-troubleshooting)  一节。 该小节提供了提示和指导。 如果在该节仍没有获得答案，请在 [Power BI 社区论坛](http://community.powerbi.com)中发布问题。 Power BI 团队将快速回复你。

## <a name="change-how-a-numeric-field-is-aggregated"></a>更改数值字段的聚合方式

假设你有一个计算各种产品销量总和的图表，但你想要求平均值。

1. 创建使用度量值和类别的簇状柱形图  。 在本示例中，我们使用的是“按产品的销售量”。  默认情况下，Power BI 将为每个产品（将类别拖到“轴”中）创建求和销售量（将度量值拖到“值”中）的图表   。

   ![标出“求和”且包含图表、可视化效果窗格和“字段”列表的屏幕截图。](media/service-aggregates/power-bi-aggregate-sum.png)

1. 在“可视化效果”窗格中，右键单击度量值，然后选择所需的聚合类型  。 在此情况下，我们选择的是“平均值”  。 如果未找到所需的聚合，请参阅[注意事项和故障排除](#considerations-and-troubleshooting)  一节。

   ![已选择并标出平均值的聚合列表屏幕截图。](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > 下拉列表中显示的选项视以下因素而定：1) 所选的字段以及 2) 数据集所有者对该字段进行分类的方式。

1. 现在，你的可视化效果采用的是按平均值聚合的方式。

   ![当前显示按产品的销售量平均值的图表屏幕截图。](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>聚合数据的方法

聚合字段时可用的某些选项：

- **不求和**。 如果选择此选项，Power BI 将单独处理该字段中的每个值，而不会对其求和。 如果存在该服务不应求和的数值 ID 列，请使用此选项。

- **求和**。 对该字段中的所有值求和。

- **平均值**。 求出值的算术平均值。

- **最小值**。 显示最小的值。

- **最大值**。 显示最大的值。

- **计数（非空白）** 。 计算该字段中非空白值的数目。

- **计数（非重复）** 。 计算该字段中不同值的数目。

- **标准偏差**。

- **方差**。

- **中值**。  显示中间值。 此值的上下项数相同。  如果有两个中值，Power BI 会取其平均值。

例如，下列数据：

| 国家/地区 | 数量 |
|:--- |:--- |
| 美国 |100 |
| 英国 |150 |
| 加拿大 |100 |
| 德国 |125 |
| 法国 | |
| 日本 |125 |
| 澳大利亚 |150 |

将得到下列结果：

- **不求和**：分别显示每个值

- **求和**：750

- **平均值**：125

- **最大值**：150

- **最小值**：100

- **计数(非空白)** ：6

- **计数(非重复)** ：4

- **标准偏差**：20.4124145...

- **方差**：416.666...

- **中值**：125

## <a name="create-an-aggregate-using-a-category-text-field"></a>使用类别（文本）字段创建聚合

你还可以聚合非数字字段。 例如，如果有产品名称字段，则可以将其作为值来添加，然后设置为  “计数”、  “非重复计数”、“第一个”或“最后一个”   。

1. 将“产品”字段拖到“值”中   。 这些“值”通常用于数字字段  。 Power BI 识别其属于文本字段，将聚合设置为“不求和”，并提供一个单列的表  。

   ![“值”中的“产品”字段的屏幕截图。](media/service-aggregates/power-bi-aggregate-value.png)

1. 如果将聚合函数从默认的“不求和”更改为“计数(非重复)”，则 Power BI 会计算各种产品的数目   。 在本例中，有四种不同的产品。
  
   ![不同产品计数的屏幕截图。](media/service-aggregates/power-bi-aggregate-count.png)

1. 如果将聚合函数更改为**计数**，Power BI 会计算总数。 在本例中，该“产品”有 7 项  。

   ![产品计数的屏幕截图。](media/service-aggregates/power-bi-aggregate-count-2.png)

1. 通过将同一字段（在本例中为“产品”）拖放到“值”中，并保留默认聚合函数“不求和”，Power BI 可按产品细分计数    。

   ![产品和产品计数的屏幕截图。](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

问：为什么我看不到“不求和”  选项？

答：已选择的字段可能是计算度量值或在 Excel 或 [Power BI Desktop](desktop-measures.md) 中创建的高级度量值。 各个计算度量值都有自己的硬编码公式。 无法更改 Power BI 使用的聚合函数。 例如，如果它是求和，则只能进行求和。 在“字段”列表中，计算度量值与计算器符号一起显示   。

问：我有  数值字段，为什么我只能选择“计数”  和“非重复计数”  ？

答 1：较为合理的解释是，数据集所有者未将字段归类为数值字段。  例如，如果数据集具有“年”字段，则数据集所有者可以将值归类为文本  。 Power BI 更有可能对“年”字段进行计数（例如，生于 1974 年的人数）  。 Power BI 不太可能对其求和或求平均值。 如果你是所有者，可以在 Power BI Desktop 中打开数据集，然后使用“建模”选项卡更改数据类型  。

答 2：如果字段有计算器图标，则表示它是计算度量值  。 每个计算度量值都有自己的硬编码公式，只有数据集所有者才能更改。 Power BI 使用的计算可能是简单的聚合函数，如求平均值或求和。 它也可能是较为复杂的聚合函数（如“在父类别中所占百分比”或“自年初累计总和”）。 Power BI 不会对结果求和或求平均值。 相反，它只是（使用硬编码公式）重新计算每个数据点。

答 3：另一种可能的原因是，你已将字段放入只允许分类值的存储桶中。   在这种情况下，只能选择“计数”和“非重复计数”选项。

答 4：第四种可能的原因是，你要对坐标轴使用此字段。 例如，在条形图坐标轴上，Power BI 每条显示一个非重复值，完全不会聚合字段值。

>[!NOTE]
>上述规则有一个例外，就是散点图，这种图表需要 X 轴和 Y 轴的聚合值。 

问：为什么无法聚合 SQL Server Analysis Services (SSAS) 数据源的文本字段？

答：与 SSAS 多维模型的实时连接不允许任何客户端的聚合函数，包括第一个、最后一个、平均值、最小值、最大值和求和。

问：我有一个散点图，但希望不  聚合字段。  如何操作？

答：请将字段添加到“详细信息”  存储桶，而不是 X 轴或 Y 轴存储桶中。

问：向可视化效果添加数值字段时，大多数情况下默认聚合为求和，但在一些情况下默认聚合为计算平均值/计数或其他一些聚合。  为什么默认聚合并不总是相同？

答：数据集所有者可设置每个字段的默认求和。 如果你是数据集所有者，则可以在 Power BI Desktop 的“建模”选项卡中更改默认求和  。

问：我是数据集所有者，我想确保字段永不进行聚合。该怎么办？

答：请在 Power BI Desktop 的“建模”  选项卡中，将“数据类型”  设置为“文本”  。

问：我在下拉列表中看不到“不求和”选项，该怎么办  ？

答：请尝试删除字段，然后重新添加。

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)
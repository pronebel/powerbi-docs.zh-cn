---
title: 使用 Power BI 服务中的聚合 （sum、 average 等）
description: 了解如何更改 Power BI 服务中的图表 （总和、 平均值、 最大值和等等。） 中的聚合函数。
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
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710651"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>使用 Power BI 服务中的聚合 （sum、 average 等）

## <a name="what-is-an-aggregate"></a>什么是聚合函数？

有时需要通过数学方式合并数据中的值。 数学运算可以是总和、 平均值、 最大值、 计数和等等。 在你的数据组合值，这就称为*聚合*。 该数学运算的结果是聚合  。

当 Power BI 服务和 Power BI Desktop 创建可视化效果时，可聚合数据。 通常聚合函数就是你所需的，但有些时候可能需要以不同的方式聚合这些值。  例如，求和与求平均值。 有几种不同的方法来管理和更改 Power BI 可视化效果中使用的聚合。

首先，让我们看看数据*类型*因为的数据类型确定方式以及是否，Power BI 可以聚合。

## <a name="types-of-data"></a>数据类型

大多数数据集都具有多种数据类型。 在最基本级别的数据是数值或它不是。 Power BI 可以聚合数字数据使用总和、 平均值、 计数、 最小值、 方差，以及更多内容。 服务甚至可以聚合文本数据，通常称为*分类*数据。 如果尝试聚合分类字段通过将其放置在类似的仅数字存储桶**值**或**工具提示**，Power BI 将每个类别的出现次数进行计数或每个非重复出现次数进行计数类别。 特殊类型的数据，像日期，有几个他们自己的聚合选项： 最早、 最新、 名字和姓氏。

在下面的示例中：

- “销售量”  和“生产价格”  为包含数值数据的列

-  “分段”、  “国家/地区”、  “产品”、  “月份”和  “月份名称”包含分类数据

   ![示例数据集的屏幕截图。](media/service-aggregates/power-bi-aggregate-chart.png)

该服务时在 Power BI 中创建可视化效果，将聚合数值字段 (默认值是*之和*) 通过一些分类字段。  例如，"Units Sold***按产品***"，"Units Sold***按月***"和"生成价格***按细分市场***"。 Power BI 指的是作为部分数值字段**度量值**。 很容易地标识 Power BI 报表编辑器-中的度量值**字段**列表显示了带有 ∑ 符号旁边的度量值。 请参阅[报表编辑器...浏览](service-the-report-editor-take-a-tour.md)的详细信息。

![屏幕截图的 Power BI 与调出字段列表。](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>为什么聚合不按我希望的方式运行？

使用 Power BI 中的聚合服务可以是令人困惑。 你可能有一个数值字段，Power BI 不会让你更改聚合。 或者，你可能有一个字段（如年份），但你并不希望进行聚合，只是想计算它的出现次数。

通常情况下，这一基本问题是在数据集中的字段定义。 数据集所有者可能定义为文本的字段，来解释为什么 Power BI 无法求和或计算其平均值。 遗憾的是，[只有数据集所有者才能更改字段的分类方式](desktop-measures.md)。 因此如果你具有所有者权限到数据集，在桌面或用来创建数据集 (例如 Excel) 的程序中可以解决此问题。 否则，请联系数据集的所有者，以寻求帮助。  

本文末尾的特殊部分[**注意事项和故障排除**](#considerations-and-troubleshooting)。 它提供的提示和指导。 如果找不到答案在这里，将您的问题发布在[Power BI 社区论坛](http://community.powerbi.com)。 直接从 Power BI 团队会快速响应。

## <a name="change-how-a-numeric-field-is-aggregated"></a>更改数值字段的聚合方式

假设你有一个计算各种产品销量总和的图表，但你想要求平均值。

1. 创建**簇状柱形图**使用度量值和类别。 在本示例中，我们使用的是“按产品的销售量”。  默认情况下，Power BI 将创建求和销售量的图表 (将到度量值拖**值**好) 的每个产品 (拖到类别**轴**也)。

   ![调出的总和的图表、 可视化效果窗格和字段列表的屏幕截图。](media/service-aggregates/power-bi-aggregate-sum.png)

1. 在中**可视化效果**窗格中，右键单击该度量值，然后选择所需的聚合类型。 在这种情况下，我们选择**平均**。 如果看不到聚合所需，请参阅[**注意事项和故障排除**](#considerations-and-troubleshooting)部分。

   ![聚合列表与平均值选择和标注的屏幕截图。](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > 在下拉列表中可用的选项将有所不同具体取决于所选 1） 的字段和数据集所有者 2） 的方式分类该字段。

1. 现在，你的可视化效果采用的是按平均值聚合的方式。

   ![图表现在显示按产品平均销售单位的屏幕截图。](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>聚合数据的方法

聚合字段时可用的某些选项：

- **不求和**。 选择此选项，Power BI 单独将该字段中的每个值，并不会进行汇总。 如果具有该服务不应该求和的数值 ID 列，请使用此选项。

- **求和**。 对该字段中的所有值求和。

- **平均值**。 求出值的算术平均值。

- **最小值**。 显示最小的值。

- **最大值**。 显示最大的值。

- **计数（非空白）** 。 计算该字段中不能为空的值的数目。

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

1. 拖动**产品**字段**值**良好。 **值**也通常用于数字字段。 Power BI 识别此字段是文本字段，将聚合设置为**不求和**，并为您提供一个单列的表。

   ![好的值中的产品字段的屏幕截图。](media/service-aggregates/power-bi-aggregate-value.png)

1. 如果从默认的更改的聚合**不求和**到**计数 （非重复）** ，Power BI 会计算不同的产品数。 在这种情况下，有四个。
  
   ![产品的非重复计数的屏幕截图。](media/service-aggregates/power-bi-aggregate-count.png)

1. 如果将聚合函数更改为**计数**，Power BI 会计算总数。 在这种情况下，有七个项**产品**。

   ![产品计数的屏幕截图。](media/service-aggregates/power-bi-aggregate-count-2.png)

1. 通过拖动同一个字段 (在这种情况下**产品**) 到**值**，并保留默认聚合**不汇总**，Power BI 将分解的计数产品。

   ![产品和产品计数的屏幕截图。](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

问：为什么我看不到“不求和”  选项？

答：已选择的字段可能是计算度量值或在 Excel 或 [Power BI Desktop](desktop-measures.md) 中创建的高级度量值。 各个计算度量值都有自己的硬编码公式。 不能更改 Power BI 使用的聚合。 例如，如果它是求和，则只能进行求和。 **字段**列表显示*计算度量值*与计算器符号。

问：我有  数值字段，为什么我只能选择“计数”  和“非重复计数”  ？

答 1：合理的解释是数据集所有者已*不*归类为数字字段。 例如，如果数据集包含**年**字段中，数据集所有者可能会对分类为文本值。 很有可能，Power BI 将算作**年**字段 （例如，1974 年出生的人员的数量）。 它不太可能，Power BI 将求和或求其平均值。 如果你是所有者，你可以在 Power BI Desktop 中打开数据集，并使用**建模**选项卡以更改数据类型。

答 2：如果字段有计算器图标，表明它是*计算的度量值*。 每个计算度量值都有其自己的硬编码公式，只有数据集所有者可以更改。 Power BI 使用的计算可能会如平均值或总和的简单聚合。 它也可能会面对更复杂的如种"父类别中所占百分比"或"运行总计由于启动的年份之前"。 Power BI 不会进行求和或计算平均值。 相反，它将只需重新计算 （使用硬编码公式） 为每个数据点。

答 3：另一种可能的原因是，你已将字段放入只允许分类值的存储桶中。   在这种情况下，只能选择“计数”和“非重复计数”选项。

答 4：和第四种可能是你使用的字段为轴。 例如，在条形图坐标轴上，Power BI 每条显示一个非重复值，完全不会聚合字段值。

>[!NOTE]
>上述规则有一个例外，就是散点图，这种图表需要 X 轴和 Y 轴的聚合值。 

问：为什么无法聚合 SQL Server Analysis Services (SSAS) 数据源的文本字段？

答：与 SSAS 多维模型的实时连接不允许任何客户端的聚合函数，包括第一个、最后一个、平均值、最小值、最大值和求和。

问：我有一个散点图，但希望不  聚合字段。  如何操作？

答：请将字段添加到“详细信息”  存储桶，而不是 X 轴或 Y 轴存储桶中。

问：向可视化效果添加数值字段时，大多数情况下默认聚合为求和，但在一些情况下默认聚合为计算平均值/计数或其他一些聚合。  为什么默认聚合并不总是相同？

答：数据集所有者可以设置每个字段的默认汇总。 如果你是数据集所有者，更改在默认汇总**建模**选项卡上的 Power BI Desktop。

问：我是数据集所有者，我想确保字段永不进行聚合。该怎么办？

答：请在 Power BI Desktop 的“建模”  选项卡中，将“数据类型”  设置为“文本”  。

问：我看**不求和**作为我的下拉列表中的一个选项。

答：请尝试删除字段，然后重新添加。

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)
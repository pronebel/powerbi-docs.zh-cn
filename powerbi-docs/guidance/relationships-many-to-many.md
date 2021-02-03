---
title: 多对多关系指导
description: 对开发多对多模型关系的指导。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 654c5ad71d7629fba1bf17b28e9e21370ebee0c3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087950"
---
# <a name="many-to-many-relationship-guidance"></a>多对多关系指导

本文面向使用 Power BI Desktop 的数据建模者。 它将介绍三种不同的多对多建模场景。 还将指导你如何在模型中成功设计这些场景。

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

实际上，有三种多对多场景。 可根据需要应用这些场景：

- [关联二维类型表](#relate-many-to-many-dimensions)
- [关联两个事实类型表](#relate-many-to-many-facts)
- 当事实类型表存储的行比维度类型表行的粒度高时，[关联更高粒度的事实类型表](#relate-higher-grain-facts)

## <a name="relate-many-to-many-dimensions"></a>关联多对多维度

让我们通过一个示例来看一下第一种多对多场景类型。 典型的情况是将两个实体相关联：银行客户和银行帐户。 要考虑到，客户可以有多个帐户，帐户也可以有多个客户。 如果某个帐户有多个客户，这些客户通常会被称为“联合帐户持有人”。

可以直接对这些实体进行建模。 一个维度类型表存储帐户，另一个维度类型表存储客户。 与维度类型表的特征一样，每个表中都有一个 ID 列。 若要对这两个表之间的关系进行建模，则需要使用第三个表。 此表通常称为“桥接表”。 此示例的目的是为每个客户帐户关联存储一行。 有趣的是，如果此表只包含 ID 列，则称之为 [_无事实的事实数据表_](star-schema.md#factless-fact-tables)。

下面是这三个表的简单模型图。

![显示包含三个表的模型的示意图。 下一段内容将介绍如何进行设计。](media/relationships-many-to-many/bank-account-customer-model-example.png)

第一个表的名称为“Account”，其中包含以下两列：“AccountID”和“Account”。 第二个表的名称为“AccountCustomer”，其中包含以下两列：“AccountID”和“CustomerID” 。 第三个表名称为“Customer”，其中包含以下两列：“CustomerID”和“Customer” 。 任何这些表之间都不存在关系。

可添加两个一对多关系来关联这些表。 下面是更新后的关联表的模型关系图。 其中添加了名为“Transaction”的事实类型表。 该表用于记录帐户交易。 桥接表和所有 ID 列都已隐藏。

![显示该模型现在包含四个表的示意图。 添加了一对多关系来关联所有表。](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

为了帮助说明关系筛选器的传播方式，已修改模型关系图以显示表行。

> [!NOTE]
> 本来是不可以在 Power BI Desktop 模型关系图中显示表行的。 本文显示出来为的是通过提供清晰的示例来支持讨论。

![显示该模型现在显示所有表行的示意图。 下面的段落描述了四个表的行详细信息。](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

下面的项目符号列表描述了四个表的行详细信息：

- “Account”表有两行：
  - “AccountID”1 表示帐户 01
  - “AccountID”2 表示帐户 02
- “Customer”表有两行：
  - “CustomerID”91 表示客户 91
  - “CustomerID”92 表示客户 92
- “AccountCustomer”表有三行：
  - “AccountID”1 与“CustomerID”91 相关联 
  - “AccountID”1 与“CustomerID”92 相关联 
  - “AccountID”2 与“CustomerID”92 相关联
- “Transaction”表包含三行：
  - “Date”为 2019 年 1 月 1 日、“AccountID”为 1、“Amount”为 100  
  - “Date”为 2019 年 2 月 2 日、“AccountID”为 2、“Amount”为 200  
  - “Date”为 2019 年 3 月 3 日、“AccountID”为 1、“Amount”为 25  

我们来看看查询模型后出现的情况。

以下两个视觉对象对“Transaction”表中的“Amount”列进行了汇总 。 第一个视觉对象按帐户分组，因此“Amount”列的总和表示“帐户余额”。 第二个视觉对象按客户分组，因此“Amount”列的总和表示“客户余额”。

![显示两个报表视觉对象并排对齐的示意图。 下一段内容介绍这两个视觉对象。](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

第一个视觉对象的标题为“Account Balance”，其中包含以下两列：“Account”和“Amount” 。 显示结果如下：

- 帐户 01 的余额为 75
- 帐户 02 的余额为 200
- 总计为 275

第二个视觉对象的标题为“**Customer Balance**”，其中包含以下两列：“Customer”和“Amount” 。 显示结果如下：

- 客户 91 的余额为 275
- 客户 92 的余额为 275
- 总计为 275

快速查看表行和“Account Balance”视觉对象就可以发现，对于每个帐户和总金额，结果都是正确的。 这是因为对每个帐户进行分组都会使筛选器传播到该帐户的“Transaction”表。

但是，“Customer Balance”视觉对象似乎不太正确。 “Customer Balance”视觉对象中的每个客户都具有与总余额相同的余额。 只有每个客户都是每个帐户的共同持有人，这个结果才可能是正确的。 而此示例却不是这种情况。 此问题与筛选器传播有关。 它没有一直流向“Transaction”表。

而是按照关系筛选器方向，从“Customer”表传递到“Transaction”表的 。 很明显，“Account”和“AccountCustomer”表之间的关系正在以错误的方向进行传播 。 此关系的筛选器方向必须设置为“双向”。

![显示该模型已更新的示意图。 现在，它在两个方向上进行筛选。](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![显示两个相同的报表视觉对象并排对齐的示意图。 第一个视觉对象尚未更改，而第二个视觉对象已更改。](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

如预期，“Account Balance”视觉对象没有变化。

而“Customer Balance”视觉对象显示的结果如下：

- 客户 91 的余额为 75
- 客户 92 的余额为 275
- 总计为 275

“Customer Balance”视觉对象现在显示的结果正确。 你可以自行按照筛选器的方向进行操作，了解如何计算客户余额。 另请注意，直观合计是针对所有客户而言。

不熟悉模型关系的人可能会认为结果不正确。 他们可能会问：为什么“客户 91”和“客户 92”的总余额不等于 350 (75 + 275)__？

要回答他们的问题，关键在于理解多对多的关系。 每个客户余额都可表示多个帐户余额的相加，因此客户余额不可累加。

### <a name="relate-many-to-many-dimensions-guidance"></a>关于关联多对多维度的指导

当维度类型表之间存在多对多关系时，我们提供以下指导：

- 将每个多对多关联的实体添加为模型表，确保其具有唯一标识符 (ID) 列
- 添加桥接表以存储关联的实体
- 在三个表之间创建一对多关系
- 配置一个双向关系以允许筛选器继续传播到事实类型表
- 当不适合具有缺失 ID 值时，可将 ID 列的“Is Nullable”属性设置为 FALSE - 如果获取缺失值，数据刷新将失败
- 隐藏桥接表（除非它包含报表所需的其他列或度量值）
- 隐藏不适用于报表的任何 ID 列（例如，ID 是代理键时）
- 如果需要显示 ID 列，请确保它位于关系的“一”侧（始终隐藏“多”侧列）。 这样可使筛选器的性能达到最佳。
- 为避免混淆或误解，请向你的报表用户传达说明 - 你可以添加包含文本框或[视觉对象标头工具提示](report-page-tooltips.md)的说明

建议不要将多对多维度类型表直接关联起来。 此设计方法需要使用多对多基数配置关系。 从概念上讲，这是可以实现的，但这意味着相关联的列将包含重复的值。 但这是一种广为接受的设计做法，即，使维度类型表包含一个 ID 列。 维度类型的表应始终使用 ID 列作为关系的“一”侧。

## <a name="relate-many-to-many-facts"></a>关联多对多事实

第二个多对多场景类型涉及两个事实类型表。 可以直接关联两个事实类型的表。 这种设计技术对于快速简单的数据浏览非常有用。 不过，需要说明的是，通常不建议采用这种设计方法。 我们将在本部分稍后解释原因。

假设有一个包含两个事实类型表的示例：“Order”和“Fulfillment” 。 “Order”表每个订单行包含一行，而“Fulfillment”表每个订单行可以包含零行或多行。 “Order”表中的行表示销售订单。 “Fulfillment”表中的行表示已发货的订单项目。 多对多关系将两个“OrderID”列关联起来，其中筛选器仅从“Order”表中传播（在“Order”中筛选“Fulfillment”）   。

![显示包含下面两个表的模型的示意图：“Order”和“Fulfillment”。](media/relationships-many-to-many/order-fulfillment-model-example.png)

关系基数设置为多对多以支持在两个表中存储重复的“OrderID”值。 在“Order”表中，可能存在重复的“OrderID”值，因为一个订单可以有多行。 在“Fulfillment”表中，可能存在重复的“OrderID”值，因为订单可能有多行，并且许多发货可履行订单行。

现在，让我们看一下表行。 请注意，在“Fulfillment”表中，多个发货可履行订单行。 （缺少订单行意味着尚未履行该订单。）

![显示该模型现在显示所有表行的示意图。 下面的段落描述了两个表的行详细信息。](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

下面的项目符号列表描述了两个表的行的详细信息：

- “Order”表有五行：
  - “OrderDate”为 2019 年 1 月 1 日、“OrderID”为 1、“OrderLine”为 1、“ProductID”为 Prod-A、“OrderQuantity”为 5、“Sales”为 50     
  - “OrderDate”为 2019 年 1 月 1 日、“OrderID”为 1、“OrderLine”为 2、“ProductID”为 Prod-B、“OrderQuantity”为 10、“Sales”为 80     
  - “OrderDate”为 2019 年 2 月 2 日、“OrderID”为 2、“OrderLine”为 1、“ProductID”为 Prod-B、“OrderQuantity”为 5、“Sales”为 40     
  - “OrderDate”为 2019 年 2 月 2 日、“OrderID”为 2、“OrderLine”为 2、“ProductID”为 Prod-C、“OrderQuantity”为 1、“Sales”为 20     
  - “OrderDate”为 2019 年 3 月 3 日、“OrderID”为 3、“OrderLine”为 1、“ProductID”为 Prod-C、“OrderQuantity”为 5、“Sales”为 100     
- “Fulfillment”表有四行：
  - “FulfillmentDate”为 2019 年 1 月 1 日、“FulfillmentID”为 50、“OrderID”为 1、“OrderLine”1、“FulfillmentQuantity”为 2    
  - “FulfillmentDate”为 2019 年 2 月 2 日、“FulfillmentID”为 51、“OrderID”为 2、“OrderLine”为 1、“FulfillmentQuantity”为 5    
  - “FulfillmentDate”为 2019 年 2 月 2 日、“FulfillmentID”为 52、“OrderID”为 1、“OrderLine”为 1、“FulfillmentQuantity”为 3    
  - “FulfillmentDate”为 2019 年 1 月 1 日、“FulfillmentID”为 53、“OrderID”为 1、“OrderLine”为 2、“FulfillmentQuantity”为 10    

我们来看看查询模型后出现的情况。 下表视觉对象通过“Order”表“OrderID”列直观比较了订单和履行数量 。

![显示包含三列的表视觉对象的示意图：OrderID、OrderQuantity 和 FulfillmentQuantity。](media/relationships-many-to-many/order-fulfillment-model-queried.png)

视觉对象显示了准确的结果。 不过，模型的有用性是有限的 - 只能按“Order”表“OrderID”列进行筛选或分组 。

### <a name="relate-many-to-many-facts-guidance"></a>关于关联多对多事实的指导

通常，我们不建议直接使用多对多基数来关联两个事实类型表。 主要原因是，该模型无法在报表视觉对象筛选或分组的方式上提供灵活性。 在此示例中，视觉对象只能按“Order”表“OrderID”列进行筛选或分组 。 另外一个原因与数据的质量有关。 如果数据存在完整性问题，则可能是在查询期间由于“有限关系”性质而省略了一些行。 有关详细信息，请参阅 [Power BI Desktop 中的模型关系（关系计算）](../transform-model/desktop-relationships-understand.md#relationship-evaluation)。

我们建议采用[星型架构](star-schema.md)设计原则，而不是直接关联事实类型表。 可以通过添加维度类型表来实现。 然后，维度类型表通过使用一对多关系与事实类型表关联。 此设计方法非常可靠，因为它提供了灵活的报表选项。 通过这种设计方法，可使用任何维度类型列进行筛选或分组，并汇总任何相关联的事实类型表。

让我们考虑一个更好的解决方案。

![显示包含六个表的模型的示意图：OrderLine、OrderDate、Order、Fulfillment、Product 和 FulfillmentDate。](media/relationships-many-to-many/order-fulfillment-model-improved.png)

请注意以下设计更改：

- 现在，该模型有四个附加表：“OrderLine”、“OrderDate”、“Product”和“FulfillmentDate”   
- 这四个附加表都是维度类型表，一对多关系将这些表与事实数据表类型相关联
- “OrderLine”表包含一个“OrderLineID”列，它表示“OrderID”值乘以 100，加上“OrderLine”值（每个订单行的唯一标识符）   
- “Order”和“Fulfillment”表现在包含一个“OrderLineID”列，且它们不再包含“OrderID”和“OrderLine”列    
- “Fulfillment”表现在包含“OrderDate”和“ProductID”列  
- “FulfillmentDate”表仅与“Fulfillment”表关联 
- 所有唯一标识符列都已隐藏

花时间应用星型架构设计原则具有以下优势：

- 报表视觉对象可以对维度类型表中的任何可见列进行“筛选或分组”
- 报表视觉对象可以汇总维度类型表中的任何可见列
- 应用于“OrderLine”、“OrderDate”或“Product”表的筛选器将传播到两个事实类型表  
- 所有关系都是一对多，每个关系都是常规关系。 不会屏蔽数据完整性问题。 有关详细信息，请参阅 [Power BI Desktop 中的模型关系（关系计算）](../transform-model/desktop-relationships-understand.md#relationship-evaluation)。

## <a name="relate-higher-grain-facts"></a>关联更高粒度的事实

此多对多场景与本文中所述的其他两个场景大不相同。

让我们看一个涉及四个表的示例：“Date”、“Sales”、”Product”和“Target”   。 “Date”和“Product”为维度类型表 ，一对多关系分别将其与“Sales”事实类型表关联。 到目前为止，这种星型架构设计还不错。 但“Target”表尚未与其他表相关联。

![显示包含四个表的模型的示意图：“Date”、“Sales”、”Product”和“Target”。](media/relationships-many-to-many/sales-targets-model-example.png)

“Target”表包含三列：“Category”、“TargetQuantity”和“TargetYear”  。 表行显示了年份和产品类别的粒度。 换句话说，每年都会为每个产品类别设定衡量销售业绩的目标。

![显示“Target”表有三列的示意图：“TargetYear”、“Category”和“TargetQuantity”。](media/relationships-many-to-many/sales-targets-model-target-rows.png)

由于“Target”表存储数据的级别高于维度类型表，因此不能创建一对多关系。 只有一种关系是这样的。 让我们了解一下“Target”表如何与维度类型表相关联。

### <a name="relate-higher-grain-time-periods"></a>关联更高粒度时间段

“Date”和“Target”表之间的关系应该为一对多关系。 这是因为“TargetYear”列值为日期。 在此示例中，每个“TargetYear”列值都是目标年份的第一个日期。

> [!TIP]
> 当以较高的时间粒度存储事实数据时，请将列数据类型设置为“日期”（如果使用日期键，则设置为“整数”） 。 在该列中，存储表示时间段的第一天的值。 例如，年时间段记录为该年的 1 月 1 日，月时间段则记录为该月的第一天。

但是，必须注意确保月份或日期级别的筛选器能得到有意义的结果。 如果没有任何特殊的计算逻辑，报表视觉对象可能会报告目标日期是每年的第一天。 其他所有日期（一月除外的所有月份）都将目标数量汇总为空白。

下面的矩阵视觉对象显示了报表用户从年份细化到月份后会发生的情况。 该视觉对象将汇总“TargetQuantity”列。 （矩阵行已启用[显示不含数据的项](../create-reports/desktop-show-items-no-data.md)选项。）

![显示矩阵视觉对象显示 2020 年的目标数量为 270 的示意图。](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

若要避免此情况，建议使用度量值来控制事实数据的汇总。 可控制汇总的一种方法是在查询较低级别时间段时返回空白。 另一种方法（用一些复杂的 DAX 定义）是在较低级别的时间段内分配值。

请考虑以下使用 [ISFILTERED](/dax/isfiltered-function-dax) DAX 函数的度量值定义。 仅当没有筛选“Date”或“Month”列时 ，它才会返回值。

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

以下矩阵现在使用“**Target Quantity**”度量值。 它显示所有每月目标数量均为空白。

![展示了矩阵视觉对象的图，其中 2020 年的目标数量为 270，且每月都为空白值。](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>关联更高粒度（非日期）

将非日期列从维度类型表关联到事实类型表时（其粒度比维度类型表的粒度更高），需要不同的设计方法。

“Product”和“Target”表中的“Category”列都包含重复的值  。 因此，对于一对多关系，没有“一”。 在这种情况下，需要创建多对多关系。 关系应以单一方向（从维度类型表到事实类型表）传播筛选器。

![显示“Target”和“Product”表模型的示意图。 多对多关系将两个表相关联。](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

现在，让我们看一下表行。

![显示包含下面两个表的模型的示意图：“Target”和“Product”。 多对多关系将两个“Category”列相关联。](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

在“Target”表中，有四行：两个目标年份行（2019 和 2020）和两个类别行（“Clothing”和“Accessories”）。 在“Product产品”表中，有三种产品。 有两种属于“服饰”类别，另外一种属于“配件”类别。 其中有一种衣服的颜色为绿色，其余两种颜色为蓝色。

按“Product”表中的“Category”列进行分组的视觉对象生成以下结果 。

![显示包含两个列的表视觉对象的示意图：“Category”和“TargetQuantity”。 配件为 60，服饰为 40，总数为 100。](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

此视觉对象生成的结果正确。 现在让我们想一想当用“Product”表中的“Color”列对目标数量进行分组时会发生什么 。

![显示包含两个列的表视觉对象的示意图：“Color”和“TargetQuantity”。 蓝色为 100，绿色为 40，总数为 100。](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

该视觉对象生成的数据错误。 发生了什么情况？

在“Product”表的“Color” 列上进行筛选，得到了两行。 其中一行表示服饰类别，另一个表示配件类别。 这两个类别值作为筛选器传播到了“Target”表。 换句话说，因为两个类别的产品使用了蓝色，所以将使用这些类别筛选目标。

若要避免此情况，如前文所述，建议使用度量值来控制事实数据的汇总。

请考虑下面的度量值定义。 请注意，类别级别以下的所有“Product”表列都将进行测试，以便于筛选。

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

以下表视觉对象现在使用“**Target Quantity**”度量值。 它显示所有颜色目标数量均为空白。

![显示包含两个列的表视觉对象的示意图：“Color”和“TargetQuantity”。 蓝色为空白，绿色为空白，总数为 100。](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

最终模型设计如以下所示。

![显示包含“Date”和“Target”表的模型以一对多关系关联的示意图。](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>关于关联更高粒度事实的指导

如果需要将维度类型表与事实数据表类型相关联，并且事实类型表存储的行比维度类型表行的粒度高，可参考以下指导：

- 对于更高粒度的事实日期：
  - 在事实类型表中，存储时间段的第一个日期
  - 在日期表和事实类型表之间创建一对多关系
- 对于其他更高粒度的事实：
  - 在维度类型表和事实类型表之间创建多对多关系
- 对于这两种类型：
  - 使用度量值逻辑控制汇总 - 当较低级别的维度类型列用于筛选或分组时返回空白
  - 隐藏汇总的事实类型表列 - 这样一来，只有度量值才能用于汇总事实类型表

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI Desktop 中的模型关系](../transform-model/desktop-relationships-understand.md)
- [了解星型架构及其对 Power BI 的重要性](star-schema.md)
- [关系故障排除指南](relationships-troubleshoot.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

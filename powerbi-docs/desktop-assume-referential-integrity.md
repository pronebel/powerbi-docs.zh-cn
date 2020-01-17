---
title: Power BI Desktop 中的假设引用完整性设置
description: 了解如何设置 Power BI Desktop 假设引用完整性（与 DirectQuery 一起使用）
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 4d478396f88a1443c0d23d64199d84f0b615b1da
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761809"
---
# <a name="apply-the-assume-referential-integrity-setting-in-power-bi-desktop"></a>在 Power BI Desktop 中应用假设引用完整性设置
当连接到使用 **DirectQuery** 的数据源时，你可以使用“假设引用完整性”  ，以对数据源运行更高效的查询。 此功能对基础数据有要求，并且仅在使用 **DirectQuery** 时可用。

设置“假设引用完整性”  允许数据源上的查询使用 **INNER JOIN** 语句而不是 **OUTER JOIN** 语句，从而提高查询效率。

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

## <a name="requirements-for-using-assume-referential-integrity"></a>使用假设引用完整性的要求
此设置为高级设置，并且仅在连接到使用 **DirectQuery** 的数据时才可用。 若要使“假设引用完整性”  正常工作，必须满足以下要求：

* 关系中 **From** 列中的数据始终不能为 *Null*  或 *空白*
* **From** 列中的每个值在 **To** 列中都有对应的值

在此上下文中， **From** 列是 *一对多* 关系中的 *多* ，或是 *一对一* 关系中第一个表中的列。

## <a name="example-of-using-assume-referential-integrity"></a>使用假设引用完整性的示例
下面的示例演示了在数据连接中使用“假设引用完整性”时，“假设引用完整性”  的行为方式。 该示例连接到包含**订单**表、**产品**表和**仓库**表的数据源。

1. 下图显示了 **Orders** 表和 **Products** 表，请注意引用完整性存在于 **Orders[ProductID]** 和 **Products[ProductID]** 之间。 **Orders** 表中的 **[ProductID]** 列始终不能为 *Null* ，所有值也会出现在 **Products** 表中。 在这种情况下，应设置“假设引用完整性”  以获得更高效的查询（使用此设置不会更改视觉对象中显示的值）。
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_2.png)
2. 在下一个图像中，请注意 Orders[DepotID] 和 Depots[DepotID] 之间不存在引用完整性，因为某些 Orders 的 DepotID 为 Null      。 在这种情况下， *不* 应设置“假设引用完整性”  。
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_3.png)
3. 最后，在下面的表中，Orders[CustomerID] 和 Customers[CustID] 之间不存在引用完整性；CustomerID 中包含 Customers 表中不存在的值（此例中为 CustX）      。 在这种情况下， *不* 应设置“假设引用完整性”  。
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_4.png)

## <a name="setting-assume-referential-integrity"></a>设置假设引用完整性
若要启用此功能，请选中“**假设引用完整性**”旁边的复选框（如下图所示）。

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

选中后，将对数据验证此设置，以确保没有 *Null* 或不匹配的行。 *但是* ，在值的数量非常大的情况下，验证不能保证没有引用完整性问题。

此外，验证将在编辑关系时执行，并且 *不* 反映数据的任何后续更改。

## <a name="what-happens-if-you-incorrectly-set-assume-referential-integrity"></a>如果错误地设置了假设引用完整性，会发生什么？
如果在数据中有引用完整性问题时设置“假设引用完整性”，此设置不会导致错误  。 但是，将导致数据明显不一致。 例如，在上述**仓库**表的关系的情况下，会导致以下结果：

* 视觉对象显示总的 *订单数量* 值为 40
* 视觉对象显示总的 *按仓库城市的订单数量* 值仅为 *30* ，因为它不包含订单 ID 1（其 **DepotID**  为 *Null* ）。

## <a name="next-steps"></a>后续步骤
了解有关 [DirectQuery](desktop-use-directquery.md) 的详细信息

获取有关 [Power BI 中的关系](desktop-create-and-manage-relationships.md)的详细信息

了解有关 [Power BI Desktop 中的关系视图](desktop-relationship-view.md)的详细信息。


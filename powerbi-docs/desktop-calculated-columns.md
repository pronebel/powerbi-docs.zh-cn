---
title: 使用 Power BI Desktop 中的计算列
description: Power BI Desktop 中的计算列
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 425bf50ad6eb4da9b50f7d9cdc760ef71cb7bff2
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753255"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>创建 Power BI Desktop 中的计算列
凭借计算列，你可以将新数据添加到模型中已存在的表。 但请勿从数据源查询并将值加载到新列中，而是创建用于定义列值的数据分析表达式 (DAX) 公式。 在 Power BI Desktop 中，使用“报表”  视图中的“新建列”功能创建计算列。

与使用查询编辑器中的“添加自定义列”创建为查询的一部分的自定义列不同，在“报表”视图或“数据”视图中创建的计算列以你已加载到模型中的数据为基础    。 例如，可以选择连接两个不同但相关的表中的值、执行添加或提取子字符串。

像任何其他字段一样，你创建的计算列将显示在“字段”  列表中，但它们将带有特殊图标，显示其值为公式的结果。 你可以随意对列进行命名，并将其像其他字段一样添加到报表可视化效果。

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

计算列使用 DAX 计算结果，该表达式是一个旨在处理关系数据（如 Power BI Desktop 中的）的公式语言。 DAX 包括一个超过 200 个函数、运算符和构造的库。 它为创建公式提供了巨大的灵活性，几乎可以计算任何数据分析所需的结果。 若要了解有关 DAX 的详细信息，请参阅 [Power BI Desktop 中的 DAX 基本概念](desktop-quickstart-learn-dax-basics.md)。

DAX 公式类似于 Excel 公式。 事实上，DAX 有着许多与 Excel 相同的功能。 但是，DAX 函数旨在处理以交互方式切片或筛选的报表中的数据，例如 Power BI Desktop 中的数据。 在 Excel 中，可以为表中的每行使用不同的公式。 在 Power BI 中，为新列创建 DAX 公式时，它会为表中的每行计算结果。 将在必要时（例如刷新基础数据或更改值时）重新计算列值。

## <a name="lets-look-at-an-example"></a>我们来看一个示例
Jeff 是 Contoso 的货运经理，他想创建一个报表，显示去往不同城市的货运数量。 他有包含城市和州分隔字段的“地理”  表。 但是，Jeff 希望他的报表能够将城市和州值作为单个值显示在同一行。 现在，Jeff 的“地理”  表中没有所需字段。

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

但凭借计算列，Jeff 可以将来自“城市”  列的城市与来自“州”  列的州组合起来。

Jeff 右键单击“地理”  表，然后选择“新建列”  。 然后，Jeff 在公式栏中输入以下 DAX 公式：

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

此公式只创建名为 CityState  的新列。 对于“地理”  表中的每行，取“城市”  列的值，添加逗号和空格，然后连接“州”  列的值。

现在，Jeff 具有所需的字段。

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

现在 Jeff 可以将它与货运数量一起添加到报表画布中。 仅需一点努力，Jeff 现在有了“CityState”  字段，可以将其添加到几乎任何类型的可视化效果中。 在 Jeff 创建新地图时，Power BI Desktop 已经知道如何读取新建列中的城市和州值。

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>后续步骤
我们在此仅提供了关于计算列的快速介绍。 有关详细信息，请参阅下列资源：

* 若要下载示例文件并获取有关如何创建更多列的逐步课程，请参阅[教程：创建 Power BI Desktop 中的计算列](desktop-tutorial-create-calculated-columns.md)

* 若要了解有关 DAX 的详细信息，请参阅 [Power BI Desktop 中的 DAX 基本概念](desktop-quickstart-learn-dax-basics.md)。

* 若要了解有关作为查询的一部分创建的列的详细信息，请参阅 [Power BI Desktop 中的常见查询任务](desktop-common-query-tasks.md)中的“创建自定义列”  部分。  


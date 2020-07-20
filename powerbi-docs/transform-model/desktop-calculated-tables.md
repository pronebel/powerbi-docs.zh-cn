---
title: 使用 Power BI Desktop 中的计算表
description: Power BI Desktop 中的计算表
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/06/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 8c22b040a1767d616ce1f4d0e4e7fa26e55bfe19
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214295"
---
# <a name="create-calculated-tables-in-power-bi-desktop"></a>在 Power BI Desktop 中创建计算表
大多数情况下，你都是通过将数据从外部数据源导入模型来创建表。 但借助“计算表”，你可以根据已加载到模型中的数据添加新表。 你可以创建定义表值的[数据分析表达式 (DAX)](/dax/index) 公式，而非从数据源中查询值，并将值加载到新表的列中。

在 Power BI Desktop 中，DAX 是一种用于处理关系数据的公式语言。 DAX 包括一个超过 200 个函数、运算符和构造的库，这个库可为创建度量值提供巨大的灵活性，几乎可以计算任何数据分析所需的结果。 计算表最适合于你希望将其作为模型的一部分而存储的中间计算和数据，而非在运行中计算的或作为查询结果而存储的中间计算和数据。 例如，你可以选择合并或交叉联接两个现有表 。

与其他 Power BI Desktop 表一样，计算表也能与其他表建立关系。 计算表列具有数据类型、格式设置，并能归属于数据类别。 你可以随意对列进行命名，并将其像其他字段一样添加到报表可视化效果。 如果刷新或更新它们从中提取数据的任何表，除非表使用的数据来自使用 DirectQuery 的表，否则重新计算经过计算的表；在使用 DirectQuery 的情况下，此表仅会在刷新数据集后反映更改。 如果表需要使用 DirectQuery，则最好 DirectQuery 中的表也经过计算。

## <a name="create-a-calculated-table"></a>创建计算表

使用 Power BI Desktop 的报表视图或数据视图中的“新建表”功能创建计算表。

例如，假设你是一个人事经理，并且有一个“西北部员工”表和一个“西南部员工”表 。 你想要将这两个表合并为一个名为“西部地区员工”的表。

**西北部员工**

 ![显示西北员工表格数据的 Power BI Desktop 的屏幕截图。](media/desktop-calculated-tables/calctables_nwempl.png)

**西南部员工**

 ![显示西南员工表格数据的 Power BI Desktop 的屏幕截图。](media/desktop-calculated-tables/calctables_swempl.png)

在 Power BI Desktop 的报表视图或数据视图中，在“建模”选项卡的“计算”组中，选择“新建表”  。 这在数据视图中操作起来比较简单，因为这样可以立即看到新的计算表。

 ![在数据视图中新建表](media/desktop-calculated-tables/calctables_formulabarempty.png)

在公式栏中输入以下公式：

```dax
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

创建了名为“西部地区员工”的新表，该表的显示方式与“字段”窗格中的任何其他表相同 。 你可以创建与其他表之间的关系、添加度量值和计算列，并将字段添加到报表中，就像任何其他表一样。

 ![新的计算表](media/desktop-calculated-tables/calctables_westregionempl.png)

 ![“字段”窗格中的新表](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>计算表的函数

可以通过任何会返回表（包括对另一个表的简单引用）的 DAX 表达式来定义计算表。 例如：

```dax
New Western Region Employees = 'Western Region Employees'
```

本文仅提供计算表的简单介绍。 可以协同使用计算表和 DAX 来解决许多分析问题。 下面是一些你可能使用的常见 DAX 表函数：

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

有关这些函数和其他返回表的 DAX 函数的信息，请参阅 [DAX 函数引用](/dax/dax-function-reference)。


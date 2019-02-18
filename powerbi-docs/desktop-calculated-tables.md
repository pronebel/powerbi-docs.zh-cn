---
title: 使用 Power BI Desktop 中的计算表
description: Power BI Desktop 中的计算表
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ffa49cc65c28e0fafb8ca72cb7a1a5bbde798861
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216323"
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>使用 Power BI Desktop 中的计算表
借助计算表，可以将新表添加到模型中。 但是，你会创建定义表值的数据分析表达式 (DAX) 公式，而非从数据源中查询值，并将值加载到新表的列中。 在 Power BI Desktop 中，计算表是通过使用报表视图或数据视图中的“新建表”功能创建的。

大多数情况下，你都要从外部数据源将数据导入模型。 但是，计算表具备某些优势。 通常，计算表最适合于你希望将其作为模型的一部分而存储的中间计算和数据，而非在运行中计算的或作为查询的一部分而存储的中间计算和数据。

与作为查询的一部分而创建的表不同，在报表视图或数据视图中创建的计算表是以你已加载到模型中的数据为基础的。 例如，你可以选择合并或交叉联接两个表。

与普通表一样，计算表也能与其他表建立关系。 计算表中的列具有数据类型、格式设置，并能归属于数据类别。 你可以随意对列进行命名，并将其像其他字段一样添加到报表可视化效果。 如果计算表从其中提取数据的任何表以任何形式进行了刷新或更新，则将重新计算计算表。

计算表使用[数据分析表达式](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) 计算结果，它是一个旨在处理如 Power BI Desktop 中的关系数据的公式语言。 DAX 包括一个超过 200 个函数、运算符和构造的库，在创建公式时提供巨大的灵活性，可以计算几乎任何数据分析需求的结果。

## <a name="lets-look-at-an-example"></a>我们来看一个示例
Jeff，Contoso 的项目经理，拥有一个西北部员工的表和一个西南部员工的表。 Jeff 希望将这两个表合并成单个表。

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

SouthwestEmployees

 ![](media/desktop-calculated-tables/calctables_swempl.png)

使用计算表将这两个表合并非常容易。 尽管 Jeff 可以在报表视图或数据视图中创建计算表，但是在数据视图中创建会稍微容易一点，因为在此之中，他可以立即查看新的计算表。

在**数据视图**的**建模**选项卡上，Jeff 单击**新建表**。 出现一个公式栏。

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

然后 Jeff 输入了以下公式：

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

名为 Western Region Employees 的新表就创建完成了。

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

Jeff 的 Western Region Employees 新表的显示方式与字段列表中的其他任何表相同。 他可以创建与其他表之间的关系、添加计算列和度量值，并将其中任何字段添加到报表中，就像任何其他表一样。

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>计算表的函数
可以通过任何会返回表（包括对另一个表的简单引用）的 DAX 表达式定义计算表。 例如：

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

可以协同使用计算表和 DAX 来解决许多分析问题。 我们在此处只提供了关于计算表的简单介绍。 开始使用计算表时，你可以在此处找到一些有用的更常见 DAX 表函数：

* DISTINCT
* 值
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

有关这些函数以及返回 DAX 函数的其他表的信息，请参阅 [DAX 函数引用](https://msdn.microsoft.com/ee634396.aspx)。


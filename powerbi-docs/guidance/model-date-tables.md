---
title: 在 Power BI Desktop 中创建日期表
description: 有关在 Power BI Desktop 中创建日期表的方法和指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/24/2020
ms.openlocfilehash: 9040fb54e51dfeecad853e5ba980f423ab48e908
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417833"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>在 Power BI Desktop 中创建日期表

本文面向使用 Power BI Desktop 的数据建模者。 介绍在数据模型中创建日期表的良好设计做法。

若要使用数据分析表达式 (DAX) [时间智能函数](/dax/time-intelligence-functions-dax)，需要具备以下必备模型：模型中必须至少有一个日期表。 日期表必须满足以下要求：

> [!div class="checklist"]
> - 它必须包含一个数据类型为“日期”（或“日期/时间”）的列（日期列）。
> - 日期列必须包含唯一值。
> - 日期列不能包含空白。
> - 日期列不能缺少任何日期。
> - 日期列必须跨越全部年份。 年份不一定是日历年（1 月 - 12 月）。
> - 日期表必须[标记为日期表](../transform-model/desktop-date-tables.md#setting-your-own-date-table)。

可以使用任一方法将日期表添加到模型中：

- 使用自动日期/时间选项
- 使用 Power Query 连接到日期维度表
- 使用 Power Query 生成日期表
- 使用 DAX 生成日期表
- 使用 DAX 克隆一个现有日期表

> [!TIP]
> 日期表可能是你将添加到任何模型的最一致的功能。 更重要的是，在一个组织内，日期表的定义应该是一致的。 因此，无论你决定使用哪种方法，我们都建议创建一个 [Power BI Desktop 模板](../create-reports/desktop-templates.md)，其中包括完全配置的日期表。 与组织中的所有建模者共享模板。 这样的话，每当有人开发新的模型时，他们就可以从一个一致定义的日期表开始。

## <a name="use-auto-datetime"></a>使用自动日期/时间

[“自动日期/时间”](../transform-model/desktop-auto-date-time.md)选项可提供方便、快捷且易于使用的时间智能。 报表作者可以在筛选、分组和向下钻取日历时间段时使用时间智能。

建议仅在使用日历时间段时，并且对时间的模型要求比较简单时，才启用“自动日期/时间”选项。 在创建临时模型或执行数据浏览或分析时，使用此选项也很方便。 但是，这种方法不支持可将筛选器传播到多个表的单个日期表设计。 有关详细信息，请参阅 [Power BI Desktop 中的自动日期/时间指南](auto-date-time.md)。

## <a name="connect-with-power-query"></a>使用 Power Query 进行连接

如果数据源已有日期表，建议将其用作模型日期表的源。 当你连接到数据仓库时，通常可以这样做，因为它将有一个日期维度表。 这使模型可以利用组织中的单一时间事实来源。

如果要开发 DirectQuery 模型，而数据源不包含日期表，则强烈建议向数据源添加日期表。 它应满足日期表的所有建模要求。 然后，可以使用 Power Query 连接到日期表。 通过这样的方式，模型计算就可以利用 DAX 时间智能函数了。

## <a name="generate-with-power-query"></a>使用 Power Query 生成

可以使用 Power Query 生成日期表。 下面两条博客内容介绍了具体步骤：

- [使用 Power Query 脚本创建日期维度](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/)，作者：Matt Masson
- [在 Power Query 中生成日期维度表](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/)，作者：Chris Webb

> [!TIP]
> 如果组织中没有数据仓库或其他一致的定义，请考虑使用 Power Query 发布[数据流](../transform-model/dataflows/dataflows-introduction-self-service.md)。 然后，让所有数据建模者连接到数据流，以便将日期表添加到其模型中。 数据流将成为组织中的单一时间事实来源。

如果需要生成一个日期表，请考虑使用 DAX 来实现。 你可能会发现这样更简便。 另外，这种方法可能更便捷，因为 DAX 包括一些内置智能，可简化创建和管理日期表的操作。

## <a name="generate-with-dax"></a>通过 DAX 生成

可以使用 [CALENDAR](/dax/calendar-function-dax) 或 [CALENDARAUTO](/dax/calendarauto-function-dax) DAX 函数创建一个计算表，用于在模型中生成日期表。 每个函数都返回一个单列日期表。 然后，可以使用计算列扩展计算表，以支持日期间隔筛选和分组要求。

- 如果要定义日期范围，请使用 CALENDAR 函数。 传入两个值：“开始日期”和“结束日期”。 这些值可由其他 DAX 函数（如 `MIN(Sales[OrderDate])` 或 `MAX(Sales[OrderDate])`）定义。
- 如果需要将日期范围自动包含存储在模型中的所有日期，请使用 **CALENDARAUTO** 函数。 可以传入一个可选参数，该参数是一年的结束月份（如果你的年份是日历年，以 12 月为结束月份，则无需传入值）。 这个函数很有用，它可以确保返回完整年份的日期，而标记的日期表需要达到这个要求。 而且，无需将表日期延长到未来的几年：数据刷新完成后，将触发表的重新计算。 当新年份的日期加载到模型中时，重新计算将自动延长表的日期范围。

## <a name="clone-with-dax"></a>使用 DAX 克隆

如果模型中已经有一个日期表，但还需要一个日期表，可以轻松地克隆现有日期表。 当日期是[角色扮演维度](star-schema.md#role-playing-dimensions)时可以这样做。 可以通过创建计算表来克隆表。 计算表表达式只是现有日期表的名称。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI Desktop 中的自动日期/时间](../transform-model/desktop-auto-date-time.md)
- [Power BI Desktop 中的自动日期/时间指南](auto-date-time.md)
- [在 Power BI Desktop 中设置和使用日期表](../transform-model/desktop-date-tables.md)
- [Power BI 中的自助服务数据准备](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [CALENDAR 函数 (DAX)](/dax/calendar-function-dax)
- [CALENDARAUTO 函数 (DAX)](/dax/calendarauto-function-dax)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)
---
title: Power BI Desktop 中的自动日期/时间指南
description: 使用 Power BI Desktop 中的自动日期/时间功能的指南。
author: peter-myers
ms.author: kfollis
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 10/23/2019
ms.openlocfilehash: e7fcab58dc61735639689c4574a9ce89757882ca
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088663"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的自动日期/时间指南

本文面向在 Power BI Desktop 中开发导入或复合模型的数据建模人员。 在特定情况下使用 Power BI Desktop 自动日期/时间时，可以参考本文提供的指导、建议和注意事项。 有关自动日期/时间的概述和一般简介，请参阅 [Power BI Desktop 中的自动日期/时间](../transform-model/desktop-auto-date-time.md)。

“自动日期/时间”选项可提供方便、快捷且易于使用的时间智能。 报表作者可以在筛选、分组和向下钻取日历时间段时使用时间智能。

## <a name="considerations"></a>注意事项

下面的项目符号列表说明了与“自动日期/时间”选项相关的注意事项和可能的限制。

- **全部适用或全部不适用：** 启用“自动日期/时间”选项后，它将适用于“导入”表中非关系的“多”方的所有日期列。 不能逐列选择性地启用或禁用它。
- **仅日历时间段：** “年”和“季度”列与日历期间相关。 它表示年份从 1 月 1 日开始，在 12 月 31 日结束。 不能自定义年份的开始（或完成）日期。
- **自定义：** 不能自定义用于描述时间段的值。 此外，不能添加其他列来描述其他时间段，例如，“星期”。
- **年份筛选：** “季度”、“月份”和“日”列的值不包含年份值。 例如，“月份”列只包含月份名称（即，一月、二月等）。 这些值不是完全自描述的，在某些报表设计中可能无法传达年份筛选器上下文。

    因此，请务必在“年份”列上进行筛选或分组，这一点很重要。 使用层次结构向下钻取时，将筛选年份，除非有意删除了“年份”级别。 例如，如果没有按年份进行筛选或分组，那么按月份分组将能够汇总所有年份该月的值。
- **单一表日期筛选：** 由于每个日期列都会生成自己的（隐藏的）自动日期/时间表，因此无法对一个表应用时间筛选器，也无法将它传播到多个模型表。 在报告多个主题（事实类型表）（例如销售额和销售预算）时，以这种方式进行筛选是常见的建模要求。 使用自动日期/时间时，报表作者需要将筛选器应用于每个不同的日期列。
- **模型大小：** 对于生成隐藏的自动日期/时间表的每个日期列，这将导致模型大小增加，并且还会延长数据刷新时间。
- **其他报告工具：** 在以下情况下，无法使用自动日期/时间表：
  - 使用[在 Excel 中分析](../collaborate-share/service-analyze-in-excel.md)。
  - 使用 Power BI 分页报表 Analysis Services 查询设计器。
  - 使用非 Power BI 报表设计器连接到模型。

## <a name="recommendations"></a>建议

建议仅在使用日历时间段时，并且对时间的模型要求比较简单时，才启用“自动日期/时间”选项。 在创建临时模型或执行数据浏览或分析时，使用此选项也很方便。

如果你的数据源已定义日期维度表，则应使用此表来一致地定义组织中的时间。 如果你的数据源是数据仓库，肯定会是这种情况。 否则，可以使用 DAX [CALENDAR](/dax/calendar-function-dax) 或 [CALENDARAUTO](/dax/calendarauto-function-dax) 函数在模型中生成日期表。 然后，可以添加计算列来支持已知的时间筛选和分组要求。 使用这种设计方法，可以创建一个可传播到所有事实类型表的单一日期表，这可能会生成一个表来应用时间筛选器。 有关创建日期表的详细信息，请阅读[在 Power BI Desktop 中设置和使用日期表](../transform-model/desktop-date-tables.md)一文。

如果“自动日期/时间”选项与你的项目无关，建议禁用全局“自动日期/时间”选项。 这将确保创建的所有新 Power BI Desktop 文件都不会启用“自动日期/时间”选项。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [在 Power BI Desktop 中创建日期表](model-date-tables.md)
- [Power BI Desktop 中的自动日期/时间](../transform-model/desktop-auto-date-time.md)
- [在 Power BI Desktop 中设置和使用日期表](../transform-model/desktop-date-tables.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

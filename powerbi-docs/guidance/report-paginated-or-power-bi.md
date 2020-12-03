---
title: 何时使用 Power BI 中的分页报表
description: 有关何时使用 Power BI 分页报表的指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/04/2020
ms.openlocfilehash: 2a13e5d697d4e0bda32068a3b6eb908959ce0643
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418983"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>何时使用 Power BI 中的分页报表

本文适用于设计 Power BI 报表的报表作者。 它提供了一些建议，帮助你选择何时开发 [Power BI 分页报表](../paginated-reports/paginated-reports-report-builder-power-bi.md)。

> [!NOTE]
> 发布 Power BI 分页报表需要 Power BI Premium 订阅。 仅当报表位于[启用了分页报表工作负载](../admin/service-admin-premium-workloads.md#paginated-reports)的容量的工作区中时，才会呈现这些报表。

Power BI 分页报表已针对“打印”或“PDF 生成”进行了优化   。 它们还使你能够生成高度格式化、像素完美的布局。 因此，分页报表是销售发票等操作报表的理想选择。

相比之下，Power BI 报表针对“浏览和交互性”进行了优化  。 此外，它们还可以使用各种广泛的超新式视觉对象来呈现你的数据。 因此，Power BI 报表是分析报表的理想选择，使报表用户能够浏览数据，并发现关系和模式。

建议在以下情况下考虑使用 Power BI 分页报表：

- 你知道必须打印报表，或将其作为 PDF 文档输出。
- 数据网格布局可以扩展和溢出。 请注意，Power BI 报表中的表或矩阵无法动态调整大小以显示所有数据，而是提供滚动条。 但是，如果打印，将无法滚动显示任何视图外数据。
- Power BI 分页特性和功能可满足你的需求。 本文稍后将介绍许多此类报表方案。

## <a name="legacy-reports"></a>旧报表

如果已具有 SQL Server Reporting Services (SSRS) [报表定义语言 (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) 报表，可以选择将它们重新开发为 [Power BI 报表](../consumer/end-user-reports.md)，或者将它们作为分页报表迁移到 Power BI。 有关详细信息，请参阅[将 SQL Server Reporting Services 报表迁移到 Power BI](migrate-ssrs-reports-to-power-bi.md)。

在发布到 Power BI 工作区后，分页报表将与 Power BI 报表一起提供。 然后，可以使用 [Power BI 应用](../collaborate-share/service-create-distribute-apps.md)轻松地分发它们。

可以考虑重新开发 SSRS 报表，而不是迁移它们。 对于旨在提供分析体验的报表，尤其如此。 在这些情况下，Power BI 报表可能会提供更好的报表用户体验。

## <a name="paginated-report-scenarios"></a>分页报表方案

在倾向于开发 Power BI 分页报表时，有许多引人注目的方案。 许多是 Power BI 报表不支持的特性或功能。

- **打印就绪**：分页报表已针对“打印”或“PDF 生成”进行了优化。 必要时，数据区域可以以受控方式扩展和溢出到多个页面。 报表布局可以定义边距、页眉和页脚。
- **呈现格式**：Power BI 可以呈现不同格式的分页报表。 这些格式包括 Microsoft Excel、Microsoft Word、Microsoft PowerPoint、PDF、CSV、XML 和 MHTML。 （Power BI 服务使用 MHTML 格式呈现报表。）报表用户可以决定采用适合的格式导出。
- **精确布局**：可以设计确切大小和位置（以英寸或厘米为单位）的高度格式化、像素完美的布局。
- **动态布局**：通过将许多报表属性设置为使用 VB.NET 表达式，可以生成高响应性布局。 表达式可以访问许多核心 .NET Framework 库。
- **特定于呈现的布局**：可以使用表达式根据应用的呈现格式修改报表布局。 例如，当报表使用非交互格式（如 PDF）呈现时，可以将其设计为禁用切换可见性（以实现向下钻取和向上钻取）。
- **本机查询**：不需要首先开发 Power BI 数据集。 可以为任何[受支持的数据源](../paginated-reports/paginated-reports-data-sources.md)编写本机查询（或使用存储过程）。 查询可以包含参数化。
- **图形查询设计器**：Power BI 报表生成器包括图形查询设计器，可助你编写和测试数据集查询。
- **静态数据集**：你可以定义一个数据集，并直接在报表定义中输入数据。 此功能对于支持演示或提供概念验证 (POC) 特别有用。
- **数据集成**：可以合并来自不同数据源的数据，或将其与静态数据集进行合并。 此操作通过使用 VB.NET 表达式创建自定义字段完成。
- **参数化**：你可以设计高度定制的参数化体验，包括数据驱动和级联参数。 还可以定义参数默认值。 这些体验可用于帮助报表用户快速设置适当的筛选器。 此外，参数无需筛选报表数据；它们可以用于支持模拟方案、动态筛选或样式设置。
- **图像数据**：当图像以二进制格式存储在数据源中时，报表可以呈现图像。
- **自定义代码**：你可以在报表中开发 VB.NET 函数的代码块，并将其用于任何报表表达式。
- **子报表**：可以将其他 Power BI 分页报表（来自同一工作区）嵌入到报表中。
- **灵活的数据网格**：通过使用 tablix 数据区域，可以对网格布局进行精细控制。 它还支持复杂的布局，包括嵌套组和相邻组。 而且，可以将其配置为在多个页面上打印时重复标题。 此外，它还可以嵌入子报表或其他可视化效果，包括数据条、迷你图和指示器。
- **空间数据类型**：地图数据区域可以可视化 [SQL Server 空间数据类型](/sql/relational-databases/spatial/spatial-data-sql-server)。 因此，GEOGRAPHY 和 GEOMETRY 数据类型可用于可视化点、线或多边形。 还可以可视化在 ESRI 形状文件中定义的多边形。
- **新式仪表**：径向仪表和线性仪表可用于显示 KPI 值和状态。 它们甚至可以嵌入到网格数据区域中，在组中重复。
- **HTML 呈现**：当以 HTML 格式存储时，可以显示格式丰富的文本。
- **邮件合并**：可以使用文本框占位符将数据值插入文本。 这样，就可以生成邮件合并报表了。
- **交互功能**：交互功能包括切换可见性（实现向下钻取和向上钻取）、链接、交互式排序和工具提示。 还可以添加钻取到 Power BI 报表或其他 Power BI 分页报表的链接。 链接甚至可以跳转到同一报表中的其他位置。
- **订阅**：Power BI 可以按计划将分页报表作为电子邮件发送，报表附件可以采用任何支持的格式。
- **每用户布局**：可以基于打开报表的已验证用户创建响应式报表布局。 可以将报表设计为以不同方式筛选数据、隐藏数据区域或可视化效果、应用不同格式或设置特定于用户的参数默认值。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI Premium 中的分页报表是什么？](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [将 SQL Server Reporting Services 报表迁移到 Power BI](migrate-ssrs-reports-to-power-bi.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

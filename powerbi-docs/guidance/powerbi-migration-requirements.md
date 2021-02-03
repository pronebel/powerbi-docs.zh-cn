---
title: 收集迁移到 Power BI 的要求
description: 有关迁移到 Power BI 时收集要求和确定其优先级的指南。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 13cac1198010b9cd53d9fd3af2b9575d2f9b3809
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087122"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>收集迁移到 Power BI 的要求

本文介绍“阶段 1”，涉及在迁移到 Power BI 时收集要求和确定其优先级的过程。

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="显示了 Power BI 迁移各阶段的图像。本文重点介绍阶段 1。":::

> [!NOTE]
> 有关上图的完整说明，请参阅 [Power BI 迁移概述](powerbi-migration-overview.md)。

阶段 1 的重点在于针对要迁移到 Power BI 的单个解决方案收集信息和进行规划。

阶段 1 的输出包括已确定优先级的详细要求。 但是，必须完成阶段 2 和阶段 3 中的其他活动才能充分估计工作量。

> [!IMPORTANT]
> 阶段 1 - 5 表示与一个特定解决方案相关的活动。 组织/租户级别有一些决策和活动会影响解决方案级别的进程。 [Power BI 迁移概述](powerbi-migration-overview.md)一文中介绍了其中一些较高级别的计划活动。 适当时，应遵从组织级别的决策以提高效率和一致性。

> [!TIP]
> 本文中讨论的大多数主题也适用于标准 Power BI 实现项目。

## <a name="compile-requirements"></a>编译要求

在[预迁移步骤](powerbi-migration-pre-migration-steps.md)中编译的现有 BI 项目的清单成为要在 Power BI 中创建的新解决方案要求的输入。 收集要求是指了解当前状态以及在 Power BI 中重新设计报表时用户要更改或重构哪些项。 提供详细的要求会非常有利于[阶段 2](powerbi-migration-planning.md) 中的解决方案部署计划、[阶段 3](powerbi-migration-proof-of-concept.md) 中的概念证明创建过程以及[阶段 4](powerbi-migration-create-validate-content.md) 中的生产就绪解决方案的创建。

### <a name="gather-report-requirements"></a>收集报表要求

编译详尽、易于引用的报表信息，例如：

- **用途、受众和预期操作：** 确定每个报表的用途和适用的业务流程，以及受众、分析工作流和报表使用者将执行的预期操作。
- **使用者如何使用报表：** 考虑与现有报表使用者交流，了解他们对报表执行的具体操作。 你有可能获知可在新的 Power BI 版本中取消或改进哪些报表元素。 此过程需要投入额外时间，但对于重要报表或经常使用的报表非常有价值。
- **所有者和主题专家：** 确定报表所有者和与报表或数据域相关的主题专家。 他们今后可能会成为新的 Power BI 报表的所有者。 包括任何特定的更改管理要求（通常在 IT 人员管理的解决方案和企业管理的解决方案之间有所不同）以及将来更改报表时需获取的批准和签核。
- **内容交付方法：** 明确报表使用者对内容交付的期望。 交付的形式可有多种：按需、交互式执行、嵌入到自定义应用程序中或使用电子邮件订阅按计划交付。 可能还会有触发警报通知的要求。
- **交互性需求：** 确定“必须满足”和“建议满足”的交互性要求，例如筛选器、向下钻取或钻取 。
- **数据源：** 确保已找到报表所需的所有数据源，并了解数据延迟需求（数据新鲜度）。 确定每个报表的历史数据、趋势和数据快照要求，以便它们能够与数据要求保持一致。 在以后使用源数据对新报表进行数据验证时，也可以借助数据源文档。
- **安全要求：** 明确安全要求（如允许的查看器、允许的编辑器和任何行级别安全性要求），包括正常组织安全性的任何例外情况。 记录任何数据敏感级别、数据隐私或法规/符合性要求。
- **计算、KPI 和业务规则：** 确定并记录现有报表中当前定义的所有计算、KPI 和业务规则，以便它们能够与数据要求保持一致。
- **可用性、布局和修饰要求：** 确定与数据可视化、分组和排序要求以及条件可见性相关的特定可用性、布局和修饰要求。 包括与移动设备交付相关的任何特定注意事项。
- **打印和导出需求：** 确定是否存在与打印、导出或像素完美布局相关的任何特定要求。 这些需求将对评估最合适的报表类型产生影响（例如 Power BI、Excel 或分页报表）。 请注意，报表使用者往往非常倚赖于其一贯的行事和思考方式，因此不要害怕挑战他们的思维方式。 请确保从增强功能而不是改变的角度进行探讨 。
- **风险或问题：** 确定报表是否有其他技术或功能要求，以及报表中呈现的信息是否存在任何风险或问题。
- **未决问题和积压工作 (backlog) 项：** 确定当前要添加到积压工作 (backlog) 的任何将来的维护、已知问题或延迟的请求。

> [!TIP]
> 考虑将要求归类为“必须满足”或“建议满足”，由此确定其优先级 。 通常，使用者会预先提出可能需要满足的所有要求，因为他们认为这可能是提出请求的唯一时机。 此外，在多个迭代中处理优先级时，应使积压工作 (backlog) 可供利益干系人使用。 这有助于进行通信、决策制定和跟踪待完成的承诺。

### <a name="gather-data-requirements"></a>收集数据要求

编译与数据有关的详细信息，例如：

- **现有查询：** 确定是否存在可供 [DirectQuery 模型](../connect-data/desktop-use-directquery.md)或 [复合模型](../transform-model/desktop-composite-models.md)使用或可转换为导入模型的现有报表查询或存储过程。
- **数据源的类型：** 编译必用类型的数据源，包括集中式数据源（例如企业数据仓库）以及非标准数据源（例如出于报告目的用于扩充企业数据源的平面文件或 Excel 文件）。 考虑到[数据网关](../connect-data/service-gateway-onprem.md)连接性，查找数据源所在的位置也很重要。
- **数据结构和清理需求：** 确定每个必备数据源的数据结构，以及 [数据清理](../transform-model/desktop-query-overview.md)活动的必要性。
- **数据集成：** 评估当有多个数据源时如何处理数据集成，以及如何定义每个模型表之间的 [关系](../transform-model/desktop-create-and-manage-relationships.md)。 确定用于简化模型和[减小其大小](import-modeling-data-reduction.md)的特定数据元素。
- **可接受的数据延迟：** 确定每个数据源的数据延迟需求。 它将影响有关使用哪些[数据存储模式](../transform-model/desktop-storage-mode.md)的决策。 还应了解导入模型表的数据刷新频率。
- **数据量和可伸缩性：** 预估数据量，这会影响有关 [大型模型支持](../admin/service-premium-large-models.md)和设计 DirectQuery 或 [复合模型](../transform-model/desktop-composite-models.md)的决策。 了解与历史数据需求相关的注意事项也很有必要。 对于较大的数据集，还需要确定[增量数据刷新](../admin/service-premium-incremental-refresh.md)规则。
- **度量值、KPI 和业务规则：** 评估对度量值、KPI 和业务规则的需求。 它们将对有关逻辑应用时机的决策产生影响：是在数据集还是数据集成过程中应用。
- **主数据和数据目录：** 考虑是否存在需要注意的主数据问题。 确定与企业数据目录的集成对于提高可发现性、访问定义或生成组织接受的一致术语是否合适。
- **安全性和数据隐私：** 确定是否有需要考虑的有关数据集的任何特定的安全性或数据隐私的注意事项，包括 [行级别安全性](../admin/service-admin-rls.md)要求。
- **未决问题和积压工作 (backlog) 项：** 当前将任何已知的问题、已知的数据质量缺陷、将来的维护或延迟请求添加到积压工作 (backlog)。

> [!IMPORTANT]
> 可以通过[共享数据集](../connect-data/service-datasets-share.md)来实现数据可重用性，可选择对其进行[认证](../collaborate-share/service-endorse-content.md)，以指示可信度并提高可发现性。 可以通过[数据流](../transform-model/dataflows/dataflows-introduction-self-service.md)来实现数据准备可重用性，以减少多个数据集中的重复逻辑。 数据流还可以显著减少源系统上的负载，因为检索数据的频率降低了，多个数据集便可以从数据流导入数据。

## <a name="identify-improvement-opportunities"></a>确定改进可能性

在大多数情况下，可进行一些修正和改进。 在不进行任何重构或改进的情况下，很少发生直接的一对一迁移。 可以考虑三种类型的改进，包括：

- **报表合并：** 可以使用筛选器、书签或个性化设置等技术来合并类似的报表。 减少报表数量同时提升每个报表的灵活性可以显著改善报表使用者的体验。 请考虑优化用于[问答（自然语言查询）](../natural-language/q-and-a-best-practices.md)的数据集，以便为报表使用者提供更大的灵活性，使他们能够创建自己的可视化效果。
- **效率改进：** 在收集要求的过程中，通常可以确定需要改进的地方。 例如，当分析人员手动编译数字或可以简化工作流的情况下。 [Power Query](../transform-model/desktop-query-overview.md) 对于替换当前执行的手动活动，可以发挥重要作用。 如果业务分析人员发现自己定期执行相同的活动来清理和准备数据，就可以借助可重复执行的 Power Query 数据准备步骤来大幅节省操作时间并减少错误。
- **数据模型集中化：** 提供权威和经过认证的数据集充当托管的自助服务 BI 的主干数据集。 在这种情况下，数据只需托管一次，分析人员可以灵活地使用和扩充这些数据，来满足报表和分析需求。

> [!NOTE]
> 有关数据模型集中化的详细信息，请参阅[核心管控](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)和[边缘灵活性](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)。

## <a name="prioritize-and-assess-complexity"></a>确定优先级并评估复杂性

在此阶段，有初始清单可用，可能包含特定的要求。 在确定准备迁移的初始 BI 项目集的优先级时，既要结合考虑报表和数据，又要分别考虑。

确定高优先级报表，其中可能包括以下报表：

- 为企业带来巨大价值的报表。
- 经常执行的报表。
- 高级领导或主管人员需要的报表。
- 涉及到合理复杂程度（在初始迁移迭代期间提高成功的可能性）的数据。

确定高优先级数据，其中可能包含以下数据：

- 包含关键数据元素的数据。
- 要在许多用例中使用的一般组织数据。
- 可用于创建供报表和多个报表作者重复使用的共享数据集的数据。
- 涉及到合理复杂程度（在初始迁移迭代时提高成功的可能性）的数据。

## <a name="next-steps"></a>后续步骤

在此 [Power BI 迁移系列的下一篇文章](powerbi-migration-planning.md)中，了解阶段 2，该阶段要做的是规划单个 Power BI 解决方案的迁移。

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。
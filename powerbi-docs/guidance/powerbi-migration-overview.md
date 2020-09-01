---
title: Power BI 迁移概述
description: 了解如何计划和执行从另一个第三方 BI 工具到 Power BI 的迁移。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: aa17e6293a4bd946b1d6b7acad45623fa2393c57
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803155"
---
# <a name="power-bi-migration-overview"></a>Power BI 迁移概述

客户越来越多地利用 Power BI 标准化来驱动形成数据文化，包括实现托管自助商业智能 (SSBI)、企业 BI 交付合理化和应对经济压力。 本系列 Power BI 迁移文章的目的是提供有关如何计划和执行从第三方 BI 工具到 Power BI 的迁移的指南。

Power BI 迁移系列中的文章包括：

1. Power BI 迁移概述（本文）
1. [准备迁移到 Power BI](powerbi-migration-pre-migration-steps.md)
1. [收集有关迁移到 Power BI 的要求（阶段 1）](powerbi-migration-requirements.md)
1. [规划有关迁移到 Power BI 的部署（阶段 2）](powerbi-migration-planning.md)
1. [进行概念证明以迁移到 Power BI（阶段 3）](powerbi-migration-proof-of-concept.md)
1. [创建要迁移到 Power BI 的内容（阶段 4）](powerbi-migration-create-validate-content.md)
1. [部署到 Power BI（阶段 5）](powerbi-migration-deploy-support-monitor.md)
1. [学习客户 Power BI 迁移的经验](powerbi-migration-learn-from-customers.md)

存在两个假设：你的组织当前有一个旧的 BI 平台，并且已决定将内容和用户正式迁移到 Power BI。 迁移到 Power BI 服务是本系列文章的重点。 除本系列文章中讨论的内容外，可能还有其他注意事项是国家云客户需要考虑的。

下图显示了在组织中部署 Power BI 的四个高级阶段。

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="该图显示下表中所述的四个高级阶段。":::

|阶段|说明|
|--------|-----------|
|![阶段 1.](media/common/icon-01-red-30x30.png)|**设置并评估 Power BI。** 第一阶段涉及建立初始 Power BI 体系结构。 此阶段规划初步部署和治理，以及 Power BI 评估，包括投资回报和/或成本收益分析。|
|![阶段 2：](media/common/icon-02-red-30x30.png)|**在 Power BI 中快速创建新解决方案。** 在第二阶段，自助服务 BI 作者可以开始根据自己的需要来使用和评估 Power BI，并可以快速从 Power BI 中获取价值。 阶段 2 中的活动重视敏捷性和快速业务价值，这对于让人们接受新 BI 工具（如 Power BI）至关重要。 因此，关系图反映了阶段 2 中的活动与阶段 3 中的迁移活动并行发生的情况。|
|![阶段 3。](media/common/icon-03-red-30x30.png)|**将 BI 资产从旧的平台迁移到 Power BI。** 第三阶段完成迁移到 Power BI 的过程。 这是本系列 Power BI 迁移文章的重点。 下一节将讨论五个具体的迁移阶段。|
|![阶段 4。](media/common/icon-04-red-30x30.png)|**采用、治理和监视 Power BI。** 最后一个阶段包括正在进行的活动，例如培植数据文化、沟通和培训。 这些活动会极大影响 Power BI 的有效实施。 制定适合组织的治理和安全策略与流程，并进行审核和监视，以便你能够扩展、增长和持续改进，这一点非常重要。|

> [!IMPORTANT]
> 向 Power BI 的正式迁移几乎总是与新 Power BI 解决方案的开发同时进行。 Power BI 解决方案是一个宽泛术语，包括数据和报表的使用。 单个 Power BI Desktop (.pbix) 文件可能包含数据模型或报表，或者两者都包括。 出于数据可重用性的目的，建议[将报表与数据模型分离](../guidance/report-separate-from-model.md)，但这并不是必需的。
>
> 在计划和执行正式迁移时，使用 Power BI 编写新的要求有助于获得支持。 并行阶段可为内容作者提供实用真实的 Power BI 经验。

## <a name="five-stages-of-a-power-bi-migration"></a>Power BI 迁移的五个阶段

关系图中的阶段 3 完成迁移到 Power BI 的过程。 在此阶段中，有五个常见阶段。

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="图像显示了 Power BI 迁移阶段，将在接下来的部分进行介绍。":::

前一个关系图中显示了以下阶段：

- [迁移前步骤](#pre-migration-steps)
- [阶段 1：收集需求和确定优先级](#stage-1-gather-requirements-and-prioritize)
- [阶段 2：规划部署](#stage-2-plan-for-deployment)
- [阶段 3：进行概念证明](#stage-3-conduct-proof-of-concept)
- [阶段 4：创建并验证内容](#stage-4-create-and-validate-content)
- [阶段 5：部署、支持和监视](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>迁移前步骤

预迁移步骤包括在开始项目之前将内容从旧的 BI 平台迁移到 Power BI 可能考虑的操作。 它通常包括初始租户级部署规划。 有关这些活动的详细信息，请参阅[准备迁移到 Power BI](powerbi-migration-pre-migration-steps.md)"。

### <a name="stage-1-gather-requirements-and-prioritize"></a>阶段 1：收集要求和确定优先级

阶段 1 的重点是收集信息并规划单个解决方案的迁移。 此过程应是迭代的，并应投入合理的工作量。 阶段 1 的输出包括确定了优先级的、要迁移的报表和数据的清单。 需要完成阶段 2 和阶段 3 中的其他活动才能充分估计工作量。 有关阶段 1 中活动的详细信息，请参阅[收集有关迁移到 Power BI 的要求](powerbi-migration-requirements.md)。

### <a name="stage-2-plan-for-deployment"></a>阶段 2：规划部署

阶段 2 的重点是如何针对每种特定解决方案实现阶段 1 中定义的要求。 阶段 2 的输出应包含用于指导该过程的尽可能多的细节信息，虽然这是迭代的非线性进程。 概念证明的创建（在阶段 3 中）可能会与此阶段并行进行。 即使是在创建解决方案时（在阶段 4 中），也可能会发现其他影响部署规划决策的信息。 阶段 2 中的此类部署规划侧重于在解决方案级别进行，同时遵从组织级别已做出的决策。 有关阶段 2 中活动的详细信息，请参阅[规划有关迁移到 Power BI 的部署](powerbi-migration-planning.md)。

### <a name="stage-3-conduct-proof-of-concept"></a>阶段 3：进行概念证明

阶段 3 的重点是尽早解决未知问题并降低风险。 技术概念证明 (POC) 对验证假设非常有用，并且可与部署计划（阶段 2）一起迭代完成。 此阶段的输出是窄范围的 Power BI 解决方案。 注意，我们不希望 POC 成为一次性工作。 但是，很可能需要在阶段 4 中执行其他工作才能在生产环境中执行它。 在此方面，在你的组织中，可以将此活动称为原型、试点、样品、快速启动或最小可行性产品 (MVP)。 并非一定要进行 POC，而且可以非正式地完成。 有关阶段 3 中活动的详细信息，请参阅[进行概念证明以迁移到 Power BI](powerbi-migration-proof-of-concept.md)。

### <a name="stage-4-create-and-validate-content"></a>阶段 4：创建并验证内容

阶段 4 是完成将 POC 转换为生产就绪解决方案的实际工作。 此阶段的输出是已完成的 Power BI 解决方案，该解决方案已在开发环境中进行验证。 它应已能够在阶段 5 中进行部署。 有关阶段 4 中活动的详细信息，请参阅[创建要迁移到 Power BI 的内容](powerbi-migration-create-validate-content.md)。

### <a name="stage-5-deploy-support-and-monitor"></a>阶段 5：部署、支持和监视

阶段 5 的重点是将新的 Power BI 解决方案部署到生产环境中。 此阶段的输出是业务用户使用的生产解决方案。 使用敏捷方法时，规划一些要在将来的迭代中交付的优化措施是可接受的。 根据你的 Power BI 体验的舒适度（例如最大程度地降低风险和用户中断），可以选择进行分阶段部署。 或者，最初可能会部署到小规模试点用户组。 支持和监视在现阶段和后续阶段也很重要。 有关阶段 5 中活动的详细信息，请参阅[迁移到 Power BI](powerbi-migration-deploy-support-monitor.md)。

> [!TIP]
> 本系列 Power BI 迁移文章中讨论的大多数概念也适用于标准 Power BI 实施项目。

## <a name="consider-migration-reasons"></a>考虑迁移原因

培植高效和健康的数据文化是许多组织的主要目标之一。 Power BI 是实现此目标的极佳工具。 可能考虑迁移到 Power BI 的三个常见原因可以归结为：

- 通过引入可增强自助服务 BI 用户社区性能的新功能来实现托管自助服务 BI。 Power BI 使更多的人能够获取信息和制定决策，同时减少对难以获取的专业技能的依赖。
- 合理实现企业 BI 的交付，以满足现有 BI 工具无法满足的需求，同时降低复杂性级别，降低拥有成本，和/或通过当前使用的多个 BI 工具实现标准化。
- 利用更少的资源、时间和人员来解决经济压力，从而提高生产力。

## <a name="achieve-power-bi-migration-success"></a>实现 Power BI 迁移成功

每次迁移都略有不同。 它可能取决于组织结构、数据策略、数据管理成熟度和组织目标。 但是，我们发现成功实现 Power BI 迁移的客户会有一些相同的实践。

- **执行支持：** 在过程的早期确定执行支持人。 此支持人应积极支持 BI 在组织中的采用，并亲自参与实现积极的迁移结果。 理想情况下，执行支持人对与 Power BI 相关的结果具有终极权限和责任。
- **培训、支持和沟通：** 认识到这不仅仅是一项技术计划。 任何 BI 或分析项目也是一项人员计划，因此请考虑尽早投资用户培训和支持。 另外，创建沟通计划，以透明方式向所有利益干系人解释所发生的情况、原因，并制定切合实际的期望。 确保在沟通计划中加入反馈循环，以捕获利益干系人的输入。
- **速效方案：** 一开始，优先完成具有实际业务价值且紧迫的高价值项目。 在处理重新设计的报表时，不要总是严格地按照报表在旧 BI 平台中的呈现方式来迁移报表，而是要关注报表试图解答的业务问题（包括要采取的措施）。
- **现代化和改进：** 愿意重新思考事情一直以来的执行方式。 迁移可提供改进的机会。 例如，它可以去除手工数据准备的过程，或者调整局限于单个报告的业务规则。 在工作量合理的情况下，请考虑重构、现代化和合并现有解决方案。 它可包括将多个报表合并为一个报表，或去除一段时间内未使用的旧项目。
- **持续学习：** 准备好使用分阶段的方法，同时不断学习和调整。 工作时采用短迭代周期可快速带来价值。 经常实践完成小型 POC，以最大程度地减少未知风险、验证假设并了解新功能。 由于 Power BI 是一项每月更新的云服务，因此必须及时了解进展情况并在适当的时候调整路线。
- **变更的阻力：** 了解可能存在不同级别的变更阻力；一些用户会抵制学习新工具。 此外，一些花费了大量时间和精力获取了其他 BI 工具的专业知识的专业人员可能会有被取代的危机感。 要做好准备，因为它可能会导致内部政治斗争，尤其是在高度去中心化的组织中。
- **约束：** 迁移计划要切合实际，包括资金、时间估算以及涉及的人员的角色和职责。

## <a name="acknowledgments"></a>致谢

此系列文章由数据平台 MVP 和 [Coates 数据策略](https://www.coatesdatastrategies.com/)的所有者 Melissa Coates 编写。 参与编写者和审阅者包括 Marc Reguera、Venkatesh Titte、Patrick Baumgartner、Tamer Farag、Richard Tkachuk、Matthew Roche、Adam Saxton、Chris Webb、Mark Vaillancourt、Daniel Rubiolo、David Iseminger 和 Peter Myers。

## <a name="next-steps"></a>后续步骤

在[此 Power BI 迁移系列的下一篇文章中](powerbi-migration-pre-migration-steps.md)，了解迁移到 Power BI 时的预迁移步骤。

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI Enterprise 部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- [将 SSRS 报表迁移到 Power BI](migrate-ssrs-reports-to-power-bi.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

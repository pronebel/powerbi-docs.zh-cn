---
title: 准备迁移到 Power BI
description: 迁移到 Power BI 时的预迁移步骤指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 9a5ed3d2a4798332de2394e1ad5be6fdbdb6eeae
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803118"
---
# <a name="prepare-to-migrate-to-power-bi"></a>准备迁移到 Power BI

本文介绍在迁移到 Power BI 之前可以考虑的操作。

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="显示了 Power BI 迁移各阶段的图像。本文重点介绍预迁移步骤。":::

> [!NOTE]
> 有关上图的完整说明，请参阅 [Power BI 迁移概述](powerbi-migration-overview.md)。

预迁移步骤强调预先计划，这是在进入五个迁移阶段之前的重要准备。 大多数预迁移步骤只执行一次，但对于较大的组织，某些部分对于每个业务单元或部门区域可能是迭代的。

预迁移步骤的输出包括初始治理模型、初始高级部署规划以及要迁移的报表和数据的清单。 从第 1、2 和 3 阶段的活动中获取更多信息对于完整全面地评估迁移单个解决方案的工作量是必要的。

> [!TIP]
> 本文中讨论的大多数主题也适用于标准 Power BI 实现项目。

## <a name="create-costbenefit-analysis-and-evaluation"></a>创建成本/收益分析和评估

初始评估期间的几个首要考虑事项包括：

- 为达到特定的预期未来状态，进行相应的业务论证和明确 BI 策略。
- 明确什么是成功，以及如何衡量迁移计划的进度和成功。
- 成本估算和投资回报率 (ROI) 计算结果。
- 范围和复杂性级别较小的多个生产性 Power BI 计划获得成功成果。

## <a name="identify-stakeholders-and-executive-support"></a>识别利益相关者和行政支持

识别利益相关者的几个考虑因素包括：

- 确保在业务论证和 BI 策略上与利益相关者保持一致。
- 将所有业务单元的代表纳入考虑（即使他们的内容计划在以后迁移），以便了解他们的动机和顾虑。
- 尽早让成功利用 Power BI 的支持者参与进来。
- 制定并执行面向利益相关者的沟通计划。

> [!TIP]
> 如果你担心出现了过度沟通，很可能确实如此。

## <a name="generate-initial-governance-model"></a>生成初始治理模型

在 Power BI 的实现过程中，初期需要解决的几个关键问题包括：

- Power BI 采用的特定目标以及如何将 Power BI 融入组织的整体 BI 策略中。
- 如何处理 Power BI 管理员角色，特别是在去中心组织中。
- 与获取可信数据相关的策略：使用权威数据源、解决数据质量问题、使用一致的术语和通用定义。
- 与数据源、数据模型、报表以及要向内部和外部用户提供的内容相关的安全和数据隐私策略。
- 如何满足内部和外部合规性、法规和审计要求。

> [!IMPORTANT]
> 最有效的治理模型会力图平衡用户权限和必要的控制程度。 有关详细信息，请参阅[核心管控](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)和[边缘灵活性](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)。

## <a name="conduct-initial-deployment-planning"></a>规划初始部署

初始部署规划涉及为组织的 Power BI 实现定义标准、策略和首选项。

请注意，[阶段 2](powerbi-migration-planning.md) 引用解决方案级别的部署规划。 阶段 2 活动应尽可能遵循组织级别的决策。

Power BI 实现初期需要解决的一些关键事项包括：

- [Power BI 租户管理设置](admin-tenant-settings.md)决策，应记录下来。
- [工作区管理](../collaborate-share/service-new-workspaces.md)决策，应记录下来。
- 与数据和[内容分发方法](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md)相关的考虑因素和首选项，例如应用、工作区、共享、订阅和内容嵌入。
- 与[数据集模式](../connect-data/service-dataset-modes-understand.md)相关的首选项，例如使用“导入”模式、DirectQuery 模式或通过[复合模型](composite-model-guidance.md)来组合使用这两种模式。
- [确保数据和访问安全](../admin/service-admin-power-bi-security.md)
- 使用[共享数据集](../connect-data/service-datasets-share.md)来实现可重用性。
- 应用[数据认证](../connect-data/service-datasets-certify.md)来推荐权威和可信数据的使用。
- 使用不同的[报表类型](../create-reports/index.yml)，包括 Power BI 报表、Excel 报表或面向不同用例或业务单元的分页报表。
- 用于管理集中式 BI 项目和业务管理 BI 项目的变更管理方法。
- 面向使用者、数据建模人员、报表作者和管理员的培训计划。
- 通过 [Power BI Desktop 模板](../create-reports/desktop-templates.md)、[自定义视觉效果](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/)，以及文档化的报表设计标准，为内容作者提供支持。
- 用于管理用户需求的程序和流程，例如请求新许可证、添加新网关数据源、获得对网关数据源的权限、请求新工作区、工作区权限更改以及其他定期可能遇到的常见需求。

> [!IMPORTANT]
> 部署规划是一个迭代过程。 随着组织在 Power BI 方面的经验的增长以及 Power BI 的发展，部署决策将经历多次改进和优化。 在这个过程中所做的决策将在解决方案级别的部署规划（在迁移过程的[阶段 2](powerbi-migration-planning.md) 中探讨）中使用。

## <a name="establish-initial-architecture"></a>建立初始体系结构

你的 [BI 解决方案体系结构](center-of-excellence-business-intelligence-solution-architecture.md)将随时间推移不断优化和完善。 现在就要完成的 Power BI 设置任务包括：

- Power BI 租户设置以及与 Azure Active Directory 的集成。
- 定义 [Power BI 管理员](../admin/service-admin-role.md)。
- 获取并分配初始[用户许可证](../admin/service-admin-licensing-organization.md)。
- 配置并查看 [Power BI 租户管理设置](admin-tenant-settings.md)。
- 设置[工作区角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)，并分配对 Azure Active Directory 安全组和用户的访问权限。
- 配置初始的[数据网关](../connect-data/service-gateway-deployment-guidance.md)集群，并计划定期更新。
- 获得初始[高级容量许可证](../admin/service-admin-premium-purchase.md)（如果适用）。
- 配置[高级容量工作负载](../admin/service-admin-premium-workloads.md)并制定一个持续管理的计划。

## <a name="define-success-criteria-for-migration"></a>定义迁移的成功条件

第一个任务是了解成功迁移单个解决方案是什么效果。 你可能会问的问题包括：

- **迁移的具体动机和目标是什么？** 有关详细信息，请参阅 [Power BI 迁移概述（考虑迁移原因）](powerbi-migration-overview.md#consider-migration-reasons)。 本文介绍迁移到 Power BI 的最常见原因。 当然，应在组织层面明确目标。 除此之外，迁移有些旧 BI 解决方案可能会获得极大节约成本的好处，而迁移另一些旧 BI 解决方案可能会获得工作流优化的好处。
- **这次迁移的预期成本/收益或 ROI 是多少？** 明确理解与成本、功能增加、复杂性降低或敏捷性提高相关的期望值，有助于对成功进行衡量。 它可以为迁移过程中的决策提供指导原则。
- **将使用哪些关键绩效指标 (KPI) 来衡量成功？** 下表列出了一些关键绩效指标示例：
    - 旧 BI 平台呈现的报表数，逐月减少。
    - Power BI 呈现的报表数，逐月增加。
    - Power BI 报表的使用者数量，逐季增加。
    - 按目标日期迁移到生产环境的报表的百分比。
    - 许可成本同比下降。

> [!TIP]
> 可使用 [Power BI 活动日志](../admin/service-admin-auditing.md)作为衡量 KPI 进度的源。

## <a name="prepare-inventory-of-existing-reports"></a>准备现有报表的清单

准备旧 BI 平台中现有报表的清单是了解现有报表的关键步骤。 此步骤的结果是迁移工作量评估步骤的输入。 与“准备清单”有关的活动可能包括：

1. **报表清单：** 编译迁移候选报表和仪表板的列表。
2. **数据源清单：** 编译现有报表访问的所有数据源的列表。 它应同时包括企业数据源以及部门和个人数据源。 这个过程可能会发现 IT 部门以前不知道的数据源，通常称“影子 IT”。
3. **审核日志：** 从旧 BI 平台审核日志中获取数据，以了解使用模式并帮助确定优先级。 要从审计日志中获取的重要信息包括：
    - 每周/每月/每季度执行每个报表的平均次数。
    - 每周/每月/季度每个报表的平均使用者数。
    - 每个报表的使用者，特别是执行官使用的报表。
    - 每个报表执行的最近日期。

> [!NOTE]
> 在许多情况下，内容并没有完全按原样迁移到 Power BI。 迁移为重新设计数据架构和/或改进报告交付提供了机会。 编译报表清单对于理解当前存在的内容至关重要，这样你就可以开始评估需要进行哪些重构。 本系列的其余文章将更详细地介绍可能的改进。

## <a name="explore-automation-options"></a>探索自动化选项

完全自动化的端到端 Power BI 转换过程是不太可能实现的。

如果你有现成的工具可帮助实现自动化，一个可能的自动化部署是编译现有数据和报表清单。 可在多大程度上实现迁移过程某些部分（例如编译现有的清单）的自动化，这在很大程度上取决于你所拥有的工具。

## <a name="next-steps"></a>后续步骤

在[本 Power BI 迁移系列的下一篇文章](powerbi-migration-requirements.md)中，了解阶段 1，它涉及在迁移到 Power BI 时收集需求并确定其优先级的过程。

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

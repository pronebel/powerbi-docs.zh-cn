---
title: 进行概念证明，以迁移到 Power BI
description: 有关迁移到 Power BI 时进行概念证明的指南。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: a51aaee15fc2a5e8d8facc1d34c0724dfa71d663
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086501"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>进行概念证明，以迁移到 Power BI

本文介绍 **阶段 3**，该阶段与进行概念证明 (POC) 以在迁移到 Power BI 时降低风险并尽早解决未知问题有关。

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="显示 Power BI 迁移阶段的图像。本文重点介绍阶段 3。":::

> [!NOTE]
> 有关上图的完整说明，请参阅 [Power BI 迁移概述](powerbi-migration-overview.md)。

阶段 3 的重点是尽早解决未知问题并降低风险。 技术 POC 有助于验证假设。 它可以与解决方案部署计划（在[阶段 2](powerbi-migration-planning.md) 中介绍）一起迭代完成。

此阶段的输出是窄范围的 Power BI 解决方案，该方案解决了初始的未决问题，并为[阶段 4](powerbi-migration-create-validate-content.md) 中的其他工作做好准备以便可以投入生产。

> [!IMPORTANT]
> 我们不希望 POC 成为一次性工作。 相反，我们希望它成为生产就绪解决方案的早期迭代。 在你的组织中，可以将此活动称为原型、试点、样品、快速入门或最小可行性产品 (MVP)。 并非一定要进行 POC，而且可以非正式地完成。

> [!TIP]
> 本文中讨论的大多数主题还适用于标准 Power BI 实现项目。 随着你的组织对 Power BI 的使用经验越来越丰富，进行 POC 的需求将减少。 不过，由于 Power BI 发布节奏快并且不断引入新功能，你可能会出于学习目的定期进行技术 POC。

## <a name="set-poc-goals-and-scope"></a>设置 POC 目标和范围

在进行 POC 时，请重点关注以下目标：

- 验证有关功能的工作原理的假设。
- 了解与旧的 BI 平台相比 Power BI 的工作方式有何差异。
- 与主题专家一起验证对某些要求的初始理解。
- 使用实际数据创建一个小型数据集，用于了解并检测数据结构、关系、数据类型或数据值的任何问题。
- 试验并验证模型计算所使用的 [DAX 语法](/dax/)表达式。
- 使用网关（如果它是网关源）测试数据源的连接性。
- 使用网关（如果它是网关源）测试刷新。
- 验证安全性配置，包括行级别安全性（如果适用）。
- 试验布局和外观决定。
- 验证 Power BI 服务中的所有功能是否按预期方式工作。

POC 范围取决于未知因素是什么，或需要与同事确认哪些目标。 为了降低复杂性，请尽量缩小 POC 的范围。

大多数情况下，对于迁移，需求是众所周知的，因为有一个现有的解决方案可以作为起点。 但是，根据预定的改进程度或现有 Power BI 技能，POC 仍可提供巨大价值。 此外，利用使用者反馈进行快速原型设计可能适合于快速阐明需求，尤其是在进行优化的情况下。

> [!IMPORTANT]
> 即使 POC 仅包括数据的子集，或仅包含有限的视觉对象，但完整执行它通常也很重要。 也就是说，从 Power BI Desktop 中的开发到 Power BI 服务中的开发工作区的部署。 这是完整实现 POC 目标的唯一方法。 如果 Power BI 服务必须提供你以前未使用过的重要功能（如使用单一登录的 DirectQuery 数据集），则更是如此。 在 POC 过程中，请将精力集中在不确定的方面，或者需要向他人寻求验证的方面。

## <a name="handle-differences-in-power-bi"></a>处理 Power BI 中的差异

Power BI 可以作为基于模型的工具或基于报表的工具来使用 。 基于模型的解决方案涉及开发数据模型，而基于报表的解决方案会连接已部署的数据模型。

由于灵活性极高，因此 Power BI 的一些方面可能与要从其迁移的旧 BI 平台完全不同。

### <a name="consider-redesigning-the-data-architecture"></a>考虑重新设计数据体系结构

如果要从具有其自己的语义层的旧 BI 平台进行迁移，则创建导入数据集可能是一个不错的选择。 Power BI 功能最适合采用[星型架构](star-schema.md)表设计。 因此，如果旧语义层不是星型架构，则可能需要进行一些重新设计才能充分利用 Power BI。 努力定义遵循星型架构设计原则（包括关系、常用度量值和友好的组织术语）的语义层是成为自助报表作者的一个很好的起点。

如果要从旧 BI 平台进行迁移，如果其中的报表使用 SQL 查询或存储过程来引用关系数据源，并且你计划在 [DirectQuery 模式](../connect-data/desktop-use-directquery.md)下使用 Power BI，则有可能可实现接近一对一的数据模型迁移。

> [!CAUTION]
> 如果发现创建了大量包含单个导入表的 Power BI Desktop 文件，则通常表明该设计不是最佳的。 如果你注意到这种情况，应调查使用通过[星型架构](star-schema.md)设计创建的[共享数据集](../connect-data/service-datasets-across-workspaces.md)是否可以达到更好的结果。

### <a name="decide-how-to-handle-dashboard-conversions"></a>决定如何处理仪表板转换

在 BI 行业中，仪表板是在单个页面上显示关键指标的视觉对象的集合。 但是，在 Power BI 中，仪表板表示只能在 Power BI 服务中创建的特定的可视化功能。 从旧的 BI 平台迁移仪表板时，有两种选择：

1. 可以将旧的仪表板重新创建为 Power BI 报表。 大多数报表都是通过 Power BI Desktop 创建的。 分页报表和 Excel 报表也是候选选项。
2. 可以将旧的仪表板重新创建为 Power BI 仪表板。 [仪表板](../fundamentals/service-basic-concepts.md#dashboards)是 Power BI 服务的一个可视化功能。 仪表板视觉对象通常是通过固定来自一个或多个报表、Q&A 或快速见解的视觉对象创建的。

> [!TIP]
> 由于仪表板是 Power BI 内容类型，因此请避免在报表或仪表板名称中使用“仪表板”一词。

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>重新创建视觉对象时，应重点关注宏观层面

每个 BI 工具都有其优势和重点适用领域。 因此，你在旧 BI 平台中依赖的具体报表视觉对象可能与 Power BI 中的视觉对象不尽相同。

重新创建报表视觉对象时，请更多地关注报表处理的宏观层面的业务问题。 它消除了以完全相同的方式复制每个视觉对象的设计的压力。 虽然在使用迁移的报表时，内容使用者非常重视一致性，但请不要陷入有关小细节的耗时争论中。

## <a name="next-steps"></a>后续步骤

在本 [Power BI 迁移系列的下一篇文章](powerbi-migration-create-validate-content.md)中，了解阶段 4，该阶段与迁移到 Power BI 时创建和验证内容有关。

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

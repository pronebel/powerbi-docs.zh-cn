---
title: 学习客户 Power BI 迁移的经验
description: 迁移到 Power BI 时从客户处获取反馈。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 7982598ac7a475cae4f0524c8d3d914b4f1a6341
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086754"
---
# <a name="learn-from-customer-power-bi-migrations"></a>学习客户 Power BI 迁移的经验

本文对有关迁移到 Power BI 的系列文章内容进行了总结，并分享了已成功迁移到 Power BI 的两个客户的关键经验。

## <a name="international-consumer-goods-company"></a>国际消费品公司

一家销售数百种产品的国际消费品公司在 2017 年决定采用云优先策略。 选择 Power BI 作为其商业智能 (BI) 平台的主要原因之一是其与 Azure 和 Microsoft 365 的深度集成。

### <a name="conduct-a-phased-migration"></a>进行分阶段迁移

2017 年，该公司开始使用 Power BI。 最初的组织级目标是引入 Power BI 作为第二个 BI 工具。 该决策为内容作者、使用者和 IT 提供了时间来适应新的 BI 交付方式。 他们还能积累和提升有关 Power BI 的专业技能。

2018 年下半年，该公司正式宣布 Power BI 是其认可的 BI 工具。 相应的，要使用 Power BI 开展和完成所有新的 BI 开发工作。 Power BI Premium 的可用性是推动作出此决策的关键因素之一。 目前，组织不鼓励使用以前的 BI 平台，并开始计划过渡。

到 2019 年底，开始将现有内容从旧的 BI 平台迁移到 Power BI。 一些早期采用者迅速迁移了他们的内容。 这推进了 Power BI 在组织内的采用速度。 随后组织要求内容所有者和作者开始准备迁移，争取在 2020 年底之前完全迁移到 Power BI。 该组织仍面临着与技能、时间和资金相关的挑战，尽管这些挑战都与技术平台本身无关。

> [!IMPORTANT]
> 在组织要求业务部门正式从以前的 BI 平台开始迁移之前，Power BI 已成功在组织中扎根。

### <a name="prepare-to-handle-varying-responses"></a>为提供不同响应做好准备

在这个大型的去中心化组织中，人们对采用 Power BI 有不同程度的接受度和意愿度。 除了时间和预算方面的问题外，有一些员工花费了大量精力积累有关以前 BI 平台的技能。 因此，并不是人人都欢迎在组织中实施 Power BI 标准化。 由于每个业务部门都有自己的预算，因此有的业务部门可能会质疑这样的决策。 由于 IT 工具决策是集中制定的，因此这给执行支持人和 BI 负责人带来了一些挑战。

> [!IMPORTANT]
> 与所有业务部门的领导团队进行沟通是至关重要的，可以确保他们都能理解在高层面上 Power BI 标准化带来的组织优势。 随着迁移的进展和旧 BI 平台退役日期的临近，有效沟通变得更加重要。

### <a name="focus-on-the-bigger-picture"></a>关注宏观层面

公司发现，尽管某些已迁移的报表可以原样复制原始设计，但不是每个单独的报表都可以在 Power BI 中原样复制。 尽管这是意料之中的：因为 BI 平台各不相同。 它确实需要一种不同的设计思维方式。

组织向内容作者提供了指导：专注于在 Power BI 中创建可满足所需用途的报表，而不是尝试创建旧报表的精确副本。 因此，在迁移过程中，需要主题专家积极参与咨询和验证。 组织在报表设计上投入了大量工作，并在适当的时候加以改进。

> [!IMPORTANT]
> 有时更好的方法是在迁移过程中进行改进。 在其他时候，更好的选择是在不进行重大改进的情况下交付与之前一样的成果，以避免影响迁移时间线的进度。

### <a name="cautiously-assess-priorities"></a>谨慎评估优先级

组织对以前的 BI 平台进行了分析，以充分了解其使用情况。 以前的 BI 平台有成千上万份已发布的报表，其中大约一半是在去年被使用的。 当评估哪些报表被视为向组织提供了重要价值时，该数字可能会再次减半。 这些重要报表优先进行了迁移。

> [!IMPORTANT]
> 人们很容易高估报表的实际重要性。 对于不经常使用的报表，评估是否可以彻底停用。 有时，最省成本和最容易的事情就是什么都不做。

### <a name="cautiously-assess-complexity"></a>谨慎评估复杂性

对于最重要的那批报表，所需时间是根据工作难易程度（简单、中等或复杂）来估算的。 尽管这听起来是一个相对简单的过程，但不要指望各个报表的时间估算都是准确的。 可能会出现非常不准确的估算。 例如，该公司认为一个报表非常复杂。 顾问们估算需要 50 天的转换时间。 但是，在 Power BI 中重新设计的报表大约在 50 小时内就完成了。

> [!IMPORTANT]
> 尽管通常需要基于时间估算来分配投资和人员，但时间估算可能在聚合中发挥的价值最大。

### <a name="decide-how-change-management-is-handled"></a>决定如何实施变更管理

由于 BI 资产量如此之大，因此对企业拥有的报表进行变更管理是一大挑战。 IT 管理的报表已根据标准的变更管理实践进行管理。 不过，由于数量庞大，因此无法集中为企业拥有的内容执行变更处理。

> [!IMPORTANT]
> 如果只依赖一个中心团队来管理变更是不切实际的，则需要业务部门参与完成某些相关职责。

### <a name="create-an-internal-community"></a>创建内部社区

公司建立了卓越中心 (COE) 来提供内部培训课程和资源。 COE 还充当内部咨询团队，随时准备帮助内容作者解决技术问题、清扫过程中的障碍和提供最佳实践指南。

还有一个内部 Power BI 社区，该社区取得了巨大成功，成员人数超过 1,600。 该社区在 Yammer 中进行管理。 成员可以询问内部相关问题，并获得遵循最佳做法且符合组织规范的答案。 这类型的“用户到用户”交互大大减轻了 COE 的支持负担。 不过，COE 确实会监视问题和解答，并在适当的时候参与对话。

内部社区的一个扩展是更新的 Power BI 专家网络。 它包括组织内部的少量预选 Power BI 支持者。 他们是业务部门中的高技能 Power BI 使用者，是热情的拥护者，会积极地应对企业中的挑战。 Power BI 专家网络的成员应遵循 COE 建立的最佳做法和指导原则，并帮助更广泛的内部 Power BI 社区成员了解和实施这些要求。 尽管 Power BI 专家网络成员与 COE 协作，并可能接受专门培训，但 Power BI 专家独立于 COE 进行操作。 每个 Power BI 专家都可以定义操作方式的参数，同时要记住他们在自己的官方角色中还有其他职责和重要任务。

> [!IMPORTANT]
> 明确定义 COE 的职能范围，例如：采用、治理、指导、最佳做法、培训、支持，甚至实际开发。 尽管 COE 具有很高价值，但要衡量其投资回报可能很困难。

### <a name="monitor-migration-progress-and-success"></a>监视迁移进度和成功情况

在迁移到 Power BI 期间，将持续监视关键绩效指标 (KPI)。 它们帮助公司了解报表访问量、活动报表数以及每月不同用户数等指标的趋势。 同时对 Power BI 使用量的增加与前 BI 平台使用量的减少进行衡量，目的是实现逆关系。 每月更新目标以适应变化。 如果使用未达到预期的速度，会出现瓶颈，这时可采取适当的措施。

> [!IMPORTANT]
> 利用具有操作性的商业智能创建迁移记分卡，以监视迁移工作是否成功。

## <a name="large-transportation-and-logistics-company"></a>大型运输和物流公司

北美一家大型运输和物流公司正在积极投资其数据基础架构和分析系统的现代化。

### <a name="allow-a-period-of-gradual-growth"></a>允许一段时间的逐步增长

该公司于 2018 年开始使用 Power BI。 到 2019 年年中，Power BI 成为所有新 BI 用例的首选平台。 然后，在 2020 年，该公司专注于逐步淘汰其现有的 BI 平台，以及各种自定义开发的 ASP.NET BI 解决方案。

> [!IMPORTANT]
> 在开始淘汰其旧版 BI 平台和解决方案之前，Power BI 在整个组织中拥有许多活跃用户。

### <a name="balance-centralized-and-distributed-groups"></a>平衡集中式和分布式组

在公司中，有两种类型的 BI 团队：中央 BI 团队和分布在整个组织中的分析团队。 中央 BI 团队对作为平台的 Power BI 负有所有权责任，但它不拥有任何内容。 这样，中央 BI 团队就是一个为分布式分析团队提供支持的技术支持和授权中心。

每个分析团队服务于特定的业务部门或实现共享服务职能。 一个小型团队可能只有一个分析师，而大型团队可能有 10-15 个分析师。

> [!IMPORTANT]
> 分布式分析团队由熟悉日常业务需求的主题专家组成。 这种职责划分使中央 BI 团队可以专注于提供 BI 服务和工具的技术授权和支持。

### <a name="focus-on-dataset-reusability"></a>专注于数据集可重用性

依赖自定义 ASP.NET BI 解决方案曾是开发新 BI 解决方案的障碍。 要求具备的技能意味着自助服务内容作者的数量会很少。 由于 Power BI 是非常易于使用的工具（专门为自助服务 BI 所设计），因此一旦发布，它很容易在整个组织中迅速普及。

在助力公司内部数据分析师方面带来了立竿见影的积极成果。 但是，Power BI 开发的最初重点是可视化效果。 尽管它生成了宝贵的 BI 解决方案，但这会导致产生大量 Power BI Desktop 文件，每个文件都含有报表和其数据集之间的一对一关系。 它导致产生了许多数据集以及重复的数据和业务逻辑。 为减少重复的数据、逻辑和工作量，公司提供了培训并为内容作者提供了支持。

> [!IMPORTANT]
> 在内部培训工作中传达数据可重用性的重要性。 尽早解决重要概念。

### <a name="test-data-access-multiple-ways"></a>用多种方式测试数据访问

该公司的数据仓库平台是 DB2。 根据当前的数据仓库设计，该公司发现 DirectQuery 模型（而不是 Import 模型）最适合他们的需求。

> [!IMPORTANT]
> 进行技术性概念证明，以评估最有效的模型存储模式。 此外，向数据建模人员介绍模型存储模式，以及如何为项目选择适当的模式。

### <a name="educate-authors-about-premium-licensing"></a>向作者介绍有关高级许可的知识

由于 Power BI （与旧的 BI 平台相比）更容易上手，许多早期使用者都是不具有以前 BI 工具许可证的人员。 正如预期的那样，内容作者的数量大幅增长。 可以理解的是，这些内容作者希望与他人共享其内容，从而导致需要额外的 Power BI Pro 许可证。

该公司对高级工作区进行了大量投资，最明显的是将 Power BI 内容分发给多个拥有 Power BI 免费许可证的用户。 支持团队与内容作者合作，以确保他们在适当的时候能使用高级工作区。 当用户只需要使用内容时，可避免不必要地分配 Power BI Pro 许可证。

> [!IMPORTANT]
> 经常会出现许可问题。 做好准备，培训和帮助内容作者解决许可问题。 验证用户对 Power BI Pro 许可证的请求是否合理。

### <a name="understand-the-data-gateways"></a>了解数据网关

早期，该公司有许多个人网关。 使用本地数据网关群集将管理工作转移给中央 BI 团队，使内容作者社区能够专注于生成内容。 中央 BI 团队与内部 Power BI 用户社区合作，从而减少了个人网关的数量。

> [!IMPORTANT]
> 制定用于创建和管理本地数据网关的计划。 决定允许谁安装和使用个人网关，并使用网关策略强制实施。

### <a name="formalize-your-support-plan"></a>制定正式的支持计划

随着 Power BI 在组织内的采用，公司发现多层支持方法行之有效：

- **层 1：团队内部：** 人们在日常工作中互相学习和指导。
- **层 2：Power BI 社区：** 人们向内部团队社区提出问题，相互学习和交流重要信息。
- **层 3：中央 BI 团队和 COE：** 用户提交电子邮件请求以获取帮助。 每周举行两次 _办公时间_ 会话，共同讨论问题并分享想法。

> [!IMPORTANT]
> 尽管前两层不那么正式，但它们与第三层支持同等重要。 经验丰富的用户往往主要依赖于他们认识的人，而新用户（或者是业务部门或共享服务的单个数据分析人员）可能会更多地依赖于正式支持。

### <a name="invest-in-training-and-governance"></a>投资于培训和管理

在过去一年中，公司改进了内部培训套餐，并增强了数据管理计划。 管理委员会包括来自各个分布式分析团队的重要成员，以及 COE。

现在在其内部目录中有六门内部 Power BI 课程。 [仪表板一日之旅](https://powerbi.microsoft.com/diad/)课程一直是深受初学者欢迎的热门课程。 为了帮助用户加深技能，他们提供了三门 Power BI 课程和两门 DAX 课程。

最重要的数据治理决策之一与高级容量的管理有关。 该公司选择让其容量与业务部门和共享服务中的关键分析领域保持一致。 因此，如果存在效率低下的情况，则只有该区域内会受到影响，并且分散的容量管理员能够根据需要管理容量。

> [!IMPORTANT]
> 注意如何使用高级容量，以及如何为它们分配工作区。

## <a name="next-steps"></a>后续步骤

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI Enterprise 部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- [仪表板一日之旅](https://powerbi.microsoft.com/diad/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

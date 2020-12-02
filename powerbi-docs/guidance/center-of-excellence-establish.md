---
title: 建立卓越中心
description: 了解卓越中心如何帮助 Microsoft 创建标准化分析和数据平台，以通过正确的操作模型、利益干系人参与以及共享和专用投资来发现见解。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: 90de33f85c0ede28b14e651414c311e4986a2172
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394557"
---
# <a name="establish-a-center-of-excellence"></a>建立卓越中心

本文面向 IT 专业人员和 IT 管理员。 你将了解如何在组织中设置 BI 和分析卓越中心 (COE) 以及 Microsoft 如何对其进行设置。

某些人抱有一种误解，他们认为 COE 只是一种技术支持，实际上并不是这样。

通常，BI 和分析 COE 是由负责建立和维护 BI 平台的专业人员组成的团队。 它还负责创建单一事实来源，并定义一组一致的公司范围内的指标以发现和加速见解转化。 然而，COE 是一个宽泛的术语。 因此，可以通过不同的方式实现和管理它，并且其结构和范围可能会因组织而异。 从其核心来看，它始终是一种可靠的平台，可在正确的时间向适当的用户提供适当的数据和见解功能。 理想情况下，它还可促进推广、培训和支持。 在 Microsoft 中，它被称为[核心准则](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)，并作为 BI 平台和单一事实来源提供。

在较大的组织中，你可以找到多个 COE，其核心 COE 通常由附属 COE 在部门级别扩展。 这样一来，附属 COE 是一组熟悉分类和定义的专家，他们知道如何将核心数据转换为对他们的部门有意义的数据。 部门分析师具有核心数据的权限，并且他们相信可以在自己的报告中使用这些核心数据。 他们生成依赖于精心准备的核心维度、事实和业务逻辑的解决方案。 有时，他们还可以使用更小的、特定于部门的数据集和业务逻辑对其进行扩展。 重要的是，附属 COE 从不会断开连接，也不会孤立运行。 在 Microsoft，附属 COE 可以提升 _[边缘灵活性](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

若要使此扩展方案获得成功，各部门必须付费。 换句话说，各部门必须在财务上对核心 COE 进行投资。 这样一来，他们就不必担心“没有获得合理的份额”或他们的需求没有受到优先考虑。

若要支持此方案，核心 COE 必须进行缩放以满足部门投资需求。 几个数据集加入后，规模经济便产生了。 在 Microsoft，集中式工作性价比更高并且能更快取得结果，这一点很快就变得显而易见。 当每个新的主题区域加入时，我们就会经历更大的规模经济，从而能够在整个平台上进行利用和参与，从而加强基础数据文化。

请看一个示例：我们的 BI 平台为财务、销售和营销提供核心维度、事实和业务逻辑。 它还定义了数百个关键绩效指标 (KPI)。 现在，Power Platform 业务的分析人员需要准备领导力仪表板。 一些 KPI（例如收入和管道）直接来自 BI 平台。 然而，其他 KPI 则基于业务更精细的需求。 其中一个这样的需求是用户采用特定于 Power BI 功能的 KPI：数据流。 因此，分析师会生成一个 Power BI [组合模型](composite-model-guidance.md)，将核心 BI 平台数据与部门数据集成。 然后添加业务逻辑来定义其部门的 KPI。 最后，他们基于新的模型创作其领导力仪表板，该模型利用本地知识和数据放大的公司范围内的 COE 资源。

重要的是，核心和附属 COE 之间的责任划分使部门分析师可以专注于开拓新领域，而不是管理数据平台。 有时，附属 COE 和核心 COE 之间甚至可能存在互惠互利的关系。 例如，附属 COE 可以定义新的指标（已证明对他们的部门有益），并最终成为对整个公司都有益的核心指标，可以从核心 COE 获得并受其支持。

## <a name="bi-platform"></a>BI 平台

在组织中，COE 可以通过不同的名称（如 BI 团队或组）识别。 名称的含义不如其用途重要。 如果你没有正式的团队，我们建议你培养一支由核心 BI 专家组成的团队，以建立 BI 平台。

在 Microsoft，COE 称为 BI 平台。 它有多个利益干系人组，表示公司内的不同部门，如财务、销售和营销。 将其组织起来以运行[共享功能](#shared-capabilities)和[专用交付](#dedicated-deliveries)。

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="图中显示共享功能和专用交付，这将在以下各节中进行说明。":::

### <a name="shared-capabilities"></a>共享功能

建立和操作 BI 平台需要共享功能。 它们支持为平台提供资金的所有利益干系人组。 他们包括以下团队：

- **核心平台工程：** 我们以工程思维设计了 BI 平台。 它实际上是一组框架，支持数据引入、处理以扩充数据，并在 BI 语义模型中提供这些数据以供分析师使用。 工程师负责核心 BI 平台功能的技术设计和实现。 例如，他们设计和实现数据管道。
- **基础结构和托管：** IT 工程师负责预配和管理所有 Azure 服务。
- **支持和操作：** 此团队使平台保持运行。 支持处理用户需要，如数据权限。 运营使平台保持运行、确保满足服务级别协议 (SLA) 并传达延迟或故障。
- **发布管理：** 技术项目经理 (PM) 发布更改。 更改范围包括从平台框架更新到对 BI 语义模型发出的更改请求。 它们是确保更改不会造成任何破坏的最后一道防线。

### <a name="dedicated-deliveries"></a>专用交付

每个利益干系人组都有一个专用交付团队。 它通常由数据工程师、分析工程师和技术 PM 组成，均由其利益干系人组投资。

## <a name="bi-team-roles"></a>BI 团队角色

在 Microsoft，我们的 BI 平台由可缩放的专业团队运营。 团队与专用和共享资源保持一致。 现在，我们有以下角色：

- **项目经理：** PM 是专用资源。 他们充当 BI 团队和利益干系人之间的主要联系人。 他们的工作是将利益干系人的业务需求转换为技术规范。 他们还管理利益干系人可交付结果的优先级。
- **数据库领导：** 他们是专用资源，负责将新的数据集加入到集中的数据仓库中。 加入数据集可能涉及到设置一致的维度、添加业务逻辑和自定义属性以及标准名称和格式。
- **分析领导：** 他们是负责设计和开发 BI 语义模型的专用资源。 他们努力使用标准命名和格式来应用一致的体系结构。 性能优化是其角色的重要组成部分。
- **运营和基础结构：** 他们是负责管理作业和数据管道的共享资源。 他们还负责管理 Azure 订阅、Power BI 容量、虚拟机和数据网关。
- **支持人员：** 他们是一种共享资源，负责编写文档、组织培训、传达 BI 语义模型更改以及回答用户问题。

## <a name="governance-and-compliance"></a>管理和符合性

对于每个利益干系人组，PM 领导进行跨计划治理和监督。 其首要目标是确保对 IT 的投资能产生业务价值并降低风险。 指导委员会定期召开会议，以审查进度并批准主要计划。

## <a name="grow-your-own-community"></a>发展你自己的社区

通过以下方式在组织内建立和发展社区：

- 定期举行“办公时间”活动，留出时间与 BI 团队交流，让人们提出问题、提出建议、分享想法，甚至提出不满之处。
- 创建一个团队渠道来提供支持，鼓励任何人提出问题和回应问题。
- 运营和推广非正式用户群组，并鼓励员工参加。
- 举行有关特定产品和 BI 平台本身的更正式的培训活动。 考虑提供 [Power BI 仪表板一日之旅](https://powerbi.microsoft.com/diad/)课程，并作为免费课程工具包提供，这是首次向员工介绍 Power BI 的绝佳方式。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [COE 中的 BI 解决方案体系结构](center-of-excellence-business-intelligence-solution-architecture.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

在[本系列的下一篇文章](center-of-excellence-business-intelligence-solution-architecture.md)中，了解 COE 中的 BI 解决方案体系结构以及所采用的不同技术。

### <a name="professional-services"></a>专业服务

经过认证的 Power BI 合作伙伴可帮助你的组织在设置 COE 时取得成功。 他们可为你提供经济高效的培训或对你的数据进行审核。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

你还可以与经验丰富的咨询合作伙伴合作。 它们可帮助你[评估](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL)、[计算](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL)或[实现](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI。

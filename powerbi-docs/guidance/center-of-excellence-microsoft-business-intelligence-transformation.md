---
title: Microsoft 的 BI 转换
description: 了解 Microsoft 如何成功推动业务决策制定的数据文化。 本文介绍了他们的 BI 策略和愿景。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: fa3f8c553fd55e77e92b4a933df332bdd8c4dc6d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394442"
---
# <a name="microsofts-bi-transformation"></a>Microsoft 的 BI 转换

本文面向 IT 专业人员和 IT 管理员。 你将了解我们的 BI 策略和愿景，这使我们能够不断地将数据作为资产加以利用。 你还将了解如何使用 Power BI 来成功推动业务决策制定的数据文化。

首先了解一些背景：如今，数据的爆炸式增长以惊人的速度影响着消费者和企业。 要在这种数据密集型环境中取得成功，要求分析师和管理人员能够将大量数据提炼成简洁的见解。 Microsoft BI 工具的变革改变了 Microsoft 自身探索数据以及获取扩大公司影响力所需的正确见解的方式。

那么，你的组织如何彻底改变使用数据的方式呢？ 让我们分享 BI 转换之旅的故事，帮助你理解。

## <a name="microsoft-journey"></a>Microsoft 之旅

几年前，在 Microsoft，我们的组织文化鼓励个人追求数据和见解的完全所有权。 这遭到了强烈的文化抵制，反对以标准化的方式行事。 因此，组织文化导致了报告和分析方面的难题。 具体而言，它导致了以下问题：

- 不一致的数据定义、层次结构、指标和关键绩效指标 (KPI)。 例如，每个国家/地区都有自己的新收入报告方式。 它们缺乏一致性，而且很混乱。
- 分析师花费 75% 的时间收集和编译数据。
- 78% 的报告是在“脱机环境”中创建的。
- 超过 350 种集中式财务工具和系统。
- 每年约有 3000 万美元用于“影子应用程序”。

这些难题促使我们思考如何才能改进。 财务和其他内部团队获得了执行支持，以转变业务评审流程，从而建立统一的 BI 平台作为我们的单一事实来源。 （我们稍后将在本文中详细介绍 BI 平台。）最终，这些创新使业务评审从密集的表格视图转变为更简单、更富有见解、聚焦于关键业务主题的视觉对象。

我们是如何取得这样的成果的？ 我们提供由 IT 管理的集中式 BI，并使用自助服务 BI (SSBI) 将其扩展，从而取得成功。 我们用两种具有创造性的方式来描述它：核心管控和边缘灵活性 。

### <a name="discipline-at-the-core"></a>核心管控

核心管控指的是 IT 通过管理单个主数据源来保留控制权。 提供标准化的公司 BI 并定义一致的 KPI 分类和层次结构是管控的一部分。 重要的一点是，数据权限是集中强制执行的，以确保我们的人员只能读取所需数据。

首先，我们了解到 BI 转换不是技术问题。 为了获得成功，我们学会了首先定义成功，然后将其转换为关键指标。 对于我们而言，实现数据定义的一致性非常重要。

我们的转换并非一次完成。 我们对包含大约 30 个 KPI 的子公司记分卡的交付进行了优先排序。 然后，经过几年时间，我们逐渐扩展了主题领域的数量和深度，并构建了更复杂的 KPI 层次结构。 如今，它使我们能够将客户级别的较低 KPI 汇总到公司级别的较高 KPI。 我们的 KPI 总数现已超过 2000，每一个都是成功的关键度量值，并与公司目标保持一致。 现在在整个公司中，公司报告和 SSBI 解决方案提供定义完善、一致且安全的 KPI。

### <a name="flexibility-at-the-edge"></a>边缘灵活性

在核心的边缘，财务、销售和营销团队的分析师变得更加灵活敏捷。 他们现在能够更快地分析数据。 更正式地说，此方案称为托管的自助服务 BI (SSBI)。 现在，我们了解到，托管 SSBI 关系到 IT 和分析师的共同利益。 重要的是，我们通过推动标准化、知识以及数据和 BI 解决方案的重用来实现优化。 而且，作为一家公司，我们在集中式 BI 和托管 SSBI 之间找到了恰当的平衡，从而协同获得了更多价值。

### <a name="our-solution"></a>我们的解决方案

Starlight 是我们内部数据统一和分析平台的名称，该平台支持财务、销售、营销和工程。 它的任务是提供可靠、共享且可缩放的数据平台。 该平台完全由财务团队构建，并且现在使用最新的 Microsoft 产品持续运营。

KPI Lake 不是 Azure Data Lake。 但它是使用 Microsoft SQL Server Analysis Services 在 Azure IaaS 中托管的 Starlight 支持的表格 BI 语义模型。 BI 语义模型提供来自 100 多个内部源的数据，并定义大量的层次结构和 KPI。 其任务是支持跨财务、营销和销售团队的业务绩效报告和分析。 这样做是为了通过来自相关来源的统一 BI 语义模型，获得及时、准确和性能良好的见解。

首次部署是个激动人心的时刻，因为表格 BI 语义模型带来了直接且可度量的好处。 第一版集中式 C+E 财务和营销 BI 平台。 然后，在过去六年中，它已经过扩展以合并其他业务见解解决方案。 现在，它持续发展，为我们的全球和商业业务评审以及标准报告和 SSBI 提供支持。 自发布以来，其采用率飙升了 5 倍，远远超出了我们最初的预期。

下面总结了它的主要优势：

- 它为我们的子公司记分卡、全球业务评审以及财务、营销、销售报告和分析提供支持。
- 它支持自助服务分析，使分析师能够发现数据中隐藏的见解。
- 它推动对激励薪酬、营销和运营分析、销售绩效指标、高级领导评审和年度计划流程的报告和分析。
- 它从单一事实来源提供自动化和动态的报告和分析。

KPI Lake 是一个很好的成功案例。 我们经常将其展示给客户，作为如何有效使用我们最新技术的示例。 它会引起很多人的高度共鸣，这并不令人吃惊。

#### <a name="how-it-works"></a>工作原理

Starlight 平台管理从获取到处理，再到发布的数据流：

1. 可靠敏捷的数据集成按计划进行，从而合并来自 100 多个不同原始源的数据。 源数据系统包括关系数据库、Azure Data Lake Storage 和 Azure Synapse 数据库。 主题区域包括财务、营销、销售和工程。
2. 暂存后，将使用主数据和业务逻辑对数据进行整合和扩充。 然后，将其加载到数据仓库表中。 然后刷新表格 BI 语义模型。
3. 公司内的分析师使用 Excel 和 Power BI 从表格 BI 语义模型中提供见解和分析。 而且，它使业务所有者能够支持自己的业务指标定义。 必要时，可使用具有负载均衡的 Azure IaaS 来实现缩放。

## <a name="deliver-success"></a>实现成功

有趣的是，每个人都想要自己版本的事实。 但对于某些组织来说，这是他们的现实。 由于个人追求对数据和见解的完全所有权，他们具有多个版本的事实。 对于这些组织而言，这种非托管方法不太可能成为业务成功的路径。

这就是我们认为你需要卓越中心 (COE) 的原因。 COE 是负责定义公司范围内的指标和定义等内容的中心团队。 它也是一种业务功能，可将人员、流程和技术组件组织到一组全面的业务能力中。

我们发现，有很多证据可支持全面可靠的 COE 对于实现价值和最大化业务成功至关重要这一观点。 它可以包括更改计划、标准流程、角色、准则、最佳做法、支持和培训等。

我们邀请你阅读此 COE 系列中的文章，了解更多信息。 让我们帮助你了解你的组织可以如何接受变革以实现成功。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [建立卓越中心](center-of-excellence-establish.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

在[本系列的下一篇文章](center-of-excellence-establish.md)中，了解 COE 如何帮助我们在 Microsoft 创建标准化的分析和数据平台，以从我们的数据中发掘见解。

### <a name="professional-services"></a>专业服务

经过认证的 Power BI 合作伙伴可帮助你的组织在设置 COE 时取得成功。 他们可为你提供经济高效的培训或对你的数据进行审核。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

你还可以与经验丰富的咨询合作伙伴合作。 他们可帮助你[评估](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL)、[计算](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL)或[实现](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI。

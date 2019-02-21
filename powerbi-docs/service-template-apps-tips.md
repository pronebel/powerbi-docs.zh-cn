---
title: 在 Power BI（预览）中创作模板应用的提示
description: 有关创建查询、数据模型、报表和仪表板以制作优秀模板应用的提示
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/05/2019
ms.author: maggies
ms.openlocfilehash: 282638c7c1c8a60ee93292602766d63fd0fe436e
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249541"
---
# <a name="tips-for-authoring-template-apps-in-power-bi-preview"></a>在 Power BI（预览）中创作模板应用的提示

在 Power BI 中[创作模板应用](service-template-apps-create.md)时，其中一部分是创建工作区、测试和生产的后勤工作。 但其他重要的部分显然是创作报表和仪表板。 我们可以将创作过程细分为四个主要部分。 使用这些组件有助于创建最佳模板应用：

* 通过“查询”，[连接](desktop-connect-to-data.md)和[转换](desktop-query-overview.md)数据，并定义[参数](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)。 
* 在“数据模型”中，可以创建[关系](desktop-create-and-manage-relationships.md)[度量值](desktop-measures.md)和问答的改进。  
* [报表页](desktop-report-view.md)中包括视觉对象和筛选器，以帮助洞察数据。  
* [仪表板](consumer/end-user-dashboards.md)和[磁贴](service-dashboard-create.md)提供对内含见解的概览。  

你可能熟悉其中每个部分（作为现有 Power BI 功能）。 在构建模板应用时，每个部分还有其他考虑事项。 请参阅下面的每个部分以获取更多详细信息。

<a name="queries"></a>

## <a name="queries"></a>查询
对于模板应用，在 Power BI Desktop 中开发的查询用于连接数据源和导入数据。 必须使用这些查询返回一致的架构，并且它们受支持以用于计划的数据刷新（不支持 DirectQuery）。

### <a name="connect-to-your-api"></a>连接到 API
需要从 Power BI Desktop 连接到你的 API 才能开始生成查询。

可以使用 Power BI Desktop 中现成可用的数据连接器连接到 API。 可以使用 Web 数据连接器（获取数据 -> Web）连接到 Rest API 或 OData 连接器（获取数据 -> OData 数据源）来连接到 OData 数据源。 这些连接器只有在你的 API 支持基本身份验证时才是现成可用的。

> [!NOTE]
> 如果你的 API 使用任何其他身份验证类型，如 OAuth 2.0 或 Web API 密钥，则需要开发你自己的数据连接器，以允许 Power BI Desktop 成功连接到 API，并对其进行身份验证。 有关如何为模板应用开发你自己的数据连接器的详细信息，请查看[数据连接器文档](https://aka.ms/DataConnectors)。 
>
>

### <a name="consider-the-source"></a>考虑源
查询可定义包含在数据模型中的数据。 根据你系统的大小，这些查询还应包括筛选器以确保客户处理适合你业务方案的可管理的查询量。

Power BI 模板应用可并行执行多个查询，也可同时为多个用户执行查询。  请提前规划你的限制条件和并发策略，并就如何使你的模板应用具备容错能力向我们寻求帮助。

### <a name="schema-enforcement"></a>架构实施
确保你的查询能够弹性应对系统中发生的更改，刷新时的架构变更可破坏模型。 如果源可能为某些查询返回 NULL 或架构缺失结果，请考虑返回空表或有意义的自定义错误消息。

### <a name="parameters"></a>参数
Power BI Desktop 中的[参数](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)允许你的用户提供用于自定义数据（由用户检索）的输入值。 提前考虑这些参数以避免在耗费时间生成详细的查询或报表之后返工。

> [!NOTE]
> 模板应用支持除 Any 和 Binary 之外的所有参数。
>

### <a name="additional-query-tips"></a>其他查询提示

* 确保正确键入所有列。
* 列具有描述性名称（请参阅[问答](#qa)）。  
* 对于共享逻辑，请考虑使用函数或查询。  
* 目前，该服务不支持隐私级别。 如果收到有关隐私级别的提示，则可能需要重写查询以使用相对路径。  

## <a name="data-models"></a>数据模型

定义明确的数据模型可确保客户可轻松直观地与模板应用进行交互。 在 Power BI Desktop 中创建数据模型。

> [!NOTE]
> 应在[查询](#queries)中执行大部分基本建模（键入功能、列名）。
>


### <a name="qa"></a>问答
建模还影响问答为客户提供结果的能力。 确保将同义词添加到常用列，并在[查询](#queries)中为列正确命名。

### <a name="additional-data-model-tips"></a>其他数据模型提示

请确保已完成以下操作：
* 将格式应用于所有值列。 在查询中应用类型。  
* 将格式应用于所有度量值。 
* 设置默认汇总。 特别是“不汇总”（如果适用）（例如，对于唯一值的情况）。  
* 设置数据类别（如果适用）。  
* 根据需要设置关系。  

## <a name="reports"></a>报表
报表页提供了对更多模板应用中包含的数据的见解。 使用报表中的页面来回答模板应用正尝试解决的关键业务问题。 使用 Power BI Desktop 创建报表。

> [!NOTE]
> 只能在模板应用中包含一个报表，因此请利用不同的页面调出方案的特定部分。
>
>

### <a name="additional-report-tips"></a>其他报表提示

* 每页使用多个视觉对象进行交叉筛选。  
* 仔细使各视觉对象对齐（不重叠）。  
* 页面设置为“4:3”或“16:9”布局模式。  
* 所提供的全部聚合将使数字有意义（平均值、唯一值）。  
* 切片产生合理结果。  
* 徽标至少位于报表顶部。  
* 元素最尽可能地位于客户端的的配色方案中。  

<a name="dashboard"></a>

## <a name="dashboards"></a>仪表板
仪表板是与客户的模板应用交互的主要位置。 它应包括所含内容（尤其是你业务方案的重要指标）的概述。

要为模板应用创建仪表板，只需通过“获取数据”>“文件”上传 PBIX 或者直接从 Power BI Desktop 进行发布即可。

> [!NOTE]
> 模板应用目前需要对每个模板应用使用单个报表和数据集。 请勿将多个报表/数据集的内容固定到模板应用所使用的仪表板中。
>
>

### <a name="additional-dashboard-tips"></a>其他仪表板提示

* 在固定时保持相同的主题，以便仪表板上的磁贴保持一致。  
* 将徽标固定到主题，以便使用者知道包的来源。  
* 建议用于多数屏幕分辨率的布局是 5-6 个小磁贴的宽度。  
* 所有仪表板磁贴应具有适当的标题/副标题。  
* 考虑在仪表板中为不同的方案分组（垂直或水平）。  

## <a name="known-limitations"></a>已知限制

| 功能 | 已知限制 |
|---------|---------|
|目录：数据集   | 应存在一个完整的数据集。 仅支持在 Power BI Desktop（.pbix 文件）中构建的数据集。 <br>不支持：来自其他模板应用、跨工作区数据集、分页报表（.rdl 文件）、Excel 工作簿的数据集 |
|目录：报表     | 最多一个报表    |
| 目录：仪表板 | 最多一个非空仪表板 <br>不支持：实时磁贴（即，不支持 PushDataset 或 pubnub） |
| 目录：数据流 | 不支持：数据流 |
| 文件内容 | 仅支持 PBIX 文件。 <br>不支持：.rdl 文件（分页报表）、Excel 工作簿   |
| 数据源 | 可支持云“计划数据”刷新的数据源。 <br>不支持： <br>DirectQuery <br>实时连接（无 Azure AS） <br>本地数据源（不支持个人和企业网关） <br>实时（不支持 pushdataset） <br>复合模型 |
| 数据集：跨工作区 | 不支持跨工作区的数据集  |
| 内容：仪表板 | 不支持使用实时磁贴（即，不支持 PushDataset 或 pubnub） |
| 查询参数 | 不支持：用于数据集的“Any”或“Binary”类型块刷新操作的参数 |
| 自定义视觉对象 | 仅支持公开可用的自定义视觉效果。 不支持[组织自定义视觉效果](power-bi-custom-visuals-organization.md) |

## <a name="next-steps"></a>后续步骤

[什么是 Power BI 模板应用？（预览）](service-template-apps-overview.md)

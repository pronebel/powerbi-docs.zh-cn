---
title: Power BI 中的作者模板内容包
description: 模板内容包创作
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: ab80739b64a3fc72fec0af000b7678bfad585c6c
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285061"
---
# <a name="author-template-content-packs-in-power-bi"></a>Power BI 中的作者模板内容包
在创作模板内容包时需使用 Power BI Desktop 和 PowerBI.com。 内容包具有四个组件︰

* 查询功能允许你[连接](desktop-connect-to-data.md)和[转换](desktop-query-overview.md)数据，以及定义[参数](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)  
* 用于创建[关系](desktop-create-and-manage-relationships.md)、[度量值](desktop-measures.md)和问题解答的改进的数据模型  
* 报表[页](desktop-report-view.md)中包括视觉对象和筛选器，以帮助洞察你的数据  
* [仪表板](consumer/end-user-dashboards.md)和[磁贴](service-dashboard-create.md)提供对内含见解的概览  

你可能熟悉其中每个部分（作为现有 Power BI 功能）。 在生成内容包时，还需考虑其中每个方面的其他一些事项。请参阅下一节了解有关详细信息。

<a name="queries"></a>

## <a name="queries"></a>查询
对于模板内容包，在 Power BI Desktop 中开发的查询用于连接数据源和导入数据。 必须使用这些查询返回一致的架构，并且它们受支持以用于计划的数据刷新（不支持直接查询）。

对于每个内容包，模板内容包仅支持一个数据源，因此请认真定义你的查询。 将单个数据源定义为需要相同的身份验证的源。 如果所有调用针对的是相同的 API 终结点且使用相同的身份验证，则可以在不同的查询中进行多次 API 调用。 Power BI 内容包不支持需要不同身份验证的多个源。

### <a name="connect-to-your-api"></a>连接到 API
需要从 Power BI Desktop 连接到你的 API 才能开始生成查询。

可以使用 Power BI Desktop 中现成可用的数据连接器连接到 API。 可以使用 Web 数据连接器（获取数据 -> Web）连接到 Rest API 或 OData 连接器（获取数据 -> OData 数据源）来连接到 OData 数据源。 请注意，这些连接器只有在你的 API 支持基本身份验证时才是现成可用的。

> [!NOTE]
> 如果你的 API 使用任何其他身份验证类型，如 OAuth 2.0 或 Web API 密钥，则需要开发你自己的数据连接器，以允许 Power BI Desktop 成功连接到 API，并对其进行身份验证。 有关如何为内容包开发你自己的数据连接器的详细信息，请查看[此处](https://aka.ms/DataConnectors)的数据连接器文档。 
>
>

### <a name="consider-the-source"></a>考虑源
查询可定义将包含在数据模型中的数据。 根据你系统的大小，这些查询还应包括筛选器以确保客户处理适合你业务方案的可管理的查询量。

Power BI 内容包可并行执行多个查询，也可同时为多个用户执行查询。  请提前规划你的限制条件和并发策略，并就如何使你的内容包具备容错能力向我们需求帮助。

### <a name="schema-enforcement"></a>架构实施
确保你的查询能够弹性应对系统中发生的更改，刷新时的架构变更可破坏模型。 如果源可能为某些查询返回 null/架构缺失结果，请考虑返回一个空表，或者引发一条对你的用户有意义的自定义错误消息。

### <a name="parameters"></a>参数
Power BI Desktop 中的[参数](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)允许你的用户提供用于自定义数据（由用户检索）的输入值。 提前考虑这些参数以避免在耗费时间生成详细的查询或报表之后返工。

> [!NOTE]
> 模板内容包目前仅支持文本参数。 在开发过程中可以使用其他参数类型，但在[测试](template-content-pack-testing.md#templates)部分中中用户所提供的所有值将为文字内容。
>
>

### <a name="additional-query-tips"></a>其他查询提示

* 确保正确键入所有列
* 列具有描述性名称（请参阅问题解答）  
* 对于共享逻辑，请考虑使用函数或查询  
* 隐私级别目前在服务中不受支持 - 如果显示有关隐私级别的提示，你可能需要重新编写查询以使用相对路径  

## <a name="data-model"></a>数据模型

已进行完善定义的数据模型将确保你的客户可轻松直观地与内容包交互。 在 Power BI Desktop 中创建数据模型。

> [!NOTE]
> 大部分基本建模（键入功能、列名）应在[查询](#queries)中完成。
>
>

### <a name="qa"></a>问题解答
建模还将影响问题解答为客户提供结果的能力。 确保将同义词添加到常用列，并在[查询](#queries)中为你的列正确命名。

### <a name="additional-data-model-tips"></a>其他数据模型提示
* 所有值列已应用格式设置
    >[!NOTE]
    >应在查询中应用类型。  
* 所有度量值已应用格式  
* 已设置“默认摘要”。 特别是“不汇总”（如果适用）（例如，对于唯一值的情况）  
* 已设置数据类别（如果适用）  
* 已设置关系（根据需要）  

## <a name="reports"></a>报表
报表页提供了更多关于你内容包中数据的见解。 使用报表中的页面来回答你的内容包正尝试解决的关键业务问题。 使用 Power BI Desktop 创建报表。

> [!NOTE]
> 内容包中只能包含一个报表，可以利用不同页面调出你方案的特定部分。
>
>

### <a name="additional-report-tips"></a>其他报表提示
* 对每个页面使用多个视觉对象以进行交叉筛选  
* 仔细使各视觉对象对齐（不重叠）  
* 页面设置为“4:3”或“16:9”布局模式  
* 所提供的全部聚合将使数字有意义（平均值、唯一值）  
* 切片产生合理结果  
* 徽标至少位于报表顶部  
* 元素最尽可能地位于客户端的的配色方案中  

<a name="dashboard"></a>

## <a name="dashboard"></a>仪表板
仪表板是与你客户的内容包交互的主要位置。 它应包括所含内容（尤其是你业务方案的重要指标）的概述。

要为模板内容包创建仪表板，只需通过“获取数据”>“文件”上载你的 PBIX 或者直接从 Power BI Desktop 进行发布即可。

> [!NOTE]
> 模板内容包目前需要对每个内容包使用单个报表和数据集。 不要将多个报表/数据集的内容固定到内容包所使用的仪表板中。
>
>

### <a name="additional-dashboard-tips"></a>其他仪表板提示
* 在固定时保持相同的主题，以便你仪表板上的磁贴保持一致  
* 将徽标固定到主题，以便使用者知道包的来源  
* 建议用于多数屏幕分辨率的布局是 5-6 个小磁贴的宽度  
* 所有仪表板磁贴应具有适当的标题/副标题  
* 考虑在仪表板中为不同的方案分组（垂直或水平）  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>限制条件摘要
如前面几节中所列，模板内容包目前存在一组限制 ︰  

| 受支持 | *不支持* |
| --- | --- |
| 在 PBI 桌面中生成的数据集 |*来自其他内容包或输入（如 Excel 文件）的数据集* |
| 可支持云“计划数据”刷新的数据源 |不支持直接查询和本地连接 |
| 将返回一致的架构或错误的查询（在适当时） |*动态架构或自定义架构* |
| 每个数据集一个数据源 |*多个数据源（例如被检测为多个数据源的混合 Web 应用程序或 URL）* |
| 文本类型的参数 |*其他参数类型（例如日期）或者“列出允许的值”* |
| 一个仪表板、报表和数据集 |*多个仪表板、报表或数据集* |

## <a name="next-step"></a>下一步
[内容包测试和提交](template-content-pack-testing.md)
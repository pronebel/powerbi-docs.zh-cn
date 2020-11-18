---
title: 卓越中心的 BI 解决方案体系结构
description: 了解设计和开发强大的 BI 平台时需要考虑的事项。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/11/2020
ms.author: v-pemyer
ms.openlocfilehash: d84f6a4fcf7ff531b76b6e731f165aa6e0df764f
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512116"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>卓越中心的 BI 解决方案体系结构

本文面向 IT 专业人员和 IT 管理员。 你将了解 COE 中的 BI 解决方案体系结构以及所采用的不同技术。 技术包括 Azure、Power BI 和 Excel。 可以同时利用它们来提供可缩放的数据驱动型云 BI 平台。

设计强大的 BI 平台类似于搭建一座桥梁；一座将已转换的丰富源数据连接到数据使用者的桥梁。 设计如此复杂的结构需要工程思维，但它可能是你所能设计的最有创造性且最有价值的 IT 体系结构之一。 在大型组织中，BI 解决方案体系结构可以包含：

- 数据源
- 数据引入
- 大数据/数据准备
- 数据仓库
- BI 语义模型
- 报表

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="显示了一个 BI 平台体系结构图的图表，从数据源到数据引入、大数据、存储、数据仓库、BI 语义建模、报告和机器学习。":::

平台必须支持特定需求。 具体来说，它必须进行缩放并可以满足业务服务和数据使用者的期望。 同时，它必须在本质上是安全的。 而且，它还必须具有足够的弹性以适应变化，因为新的数据和主题领域必须适时处于联机状态。

## <a name="frameworks"></a>框架

在 Microsoft，从一开始我们就通过投资框架开发来采用类似系统的方法。 技术和业务流程框架增加了设计和逻辑的重用，并提供了一致的结果。 它们还提供了利用多种技术的体系结构灵活性，并且通过可重复的过程简化和减少了工程开销。

我们了解到，设计良好的框架可以增加对数据世系、影响分析、业务逻辑维护、管理分类和简化治理的了解。 此外，开发变得更快，大型团队间的协作变得更敏捷、更有效。

本文介绍了几个框架。

## <a name="data-models"></a>数据模型

数据模型为你提供了对数据构造和访问方式的控制。 对于业务服务和数据使用者来说，数据模型是其在 BI 平台的接口。

BI 平台可以提供三种不同类型的模型：

- 企业模型
- BI 语义模型
- 机器学习 (ML) 模型

### <a name="enterprise-models"></a>企业模型

企业模型由 IT 架构师构建和维护。 它们有时被称为维度模型或数据市场。 通常，数据以关系格式存储为维度表和事实表。 这些表存储了由许多系统合并而来的已清理的和丰富的数据，它们表示报表和分析的权威来源。

企业模型为报表和 BI 提供了一致且单一的数据源。 它们只构建一次，并作为企业标准进行共享。 治理策略确保数据是安全的，因此根据需要限制对敏感数据集（如客户信息或财务数据）的访问。 它们采用命名约定来确保一致性，从而进一步建立数据和质量的可信度。

在云 BI 平台中，企业模型可以部署到 [Azure Synapse 中的 Synapse SQL 池](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse)。 然后，Synapse SQL 池就成为组织可以依靠的唯一事实版本，以获取快速和强大的见解。

### <a name="bi-semantic-models"></a>BI 语义模型

BI 语义模型表示企业模型之上的语义层。 它们由 BI 开发人员和业务用户构建和维护。 BI 开发人员创建核心 BI 语义模型，用于从企业模型中获取数据。 业务用户可以创建更小规模的独立模型，也可以使用部门或外部资源扩展核心 BI 语义模型。 BI 语义模型通常专注于单个主题领域，并且经常被广泛共享。

业务功能不是由数据单独实现的，而是由描述概念、关系、规则和标准的 BI 语义模型来实现的。 通过这种方式，它们表示直观且易于理解的结构，这些结构定义数据关系并将业务规则封装为计算。 它们还可以强制执行细化的数据权限，确保适当的人能够访问适当的数据。 重要的是，它们加快了查询性能，提供了响应速度极快的交互式分析，甚至超过了 TB 级数据。 与企业模型一样，BI 语义模型采用命名约定来确保一致性。

在云 BI 平台中，BI 开发人员可以将 BI 语义模型部署到 [Azure Analysis Services](/azure/analysis-services/) 或 [Power BI Premium 容量](../admin/service-premium-what-is.md#reserved-capacities)。 我们建议在 Power BI 用作报告和分析层时部署到 Power BI。 这些产品支持不同的存储模式，允许数据模型表缓存其数据或使用 [DirectQuery](directquery-model-guidance.md)，这是一种将查询传递到基础数据源的技术。 如果模型表表示大数据量或需要交付近实时结果，那么 DirectQuery 是一种理想的存储模式。 两种存储模式可以组合在一起：[复合模型](composite-model-guidance.md)组合在单个模型中使用不同存储模式的表。

对于频繁执行查询的模型，[Azure 负载均衡器](/azure/load-balancer/load-balancer-overview)可用于在模型副本之间均匀分布查询负载。 它还支持扩展应用程序并创建高度可用的 BI 语义模型。

### <a name="machine-learning-models"></a>机器学习模型

[机器学习 (ML) 模型](/windows/ai/windows-ml/what-is-a-machine-learning-model)由数据科学家构建和维护。 它们大多是从数据湖的原始源中开发而来。

经过训练的 ML 模型可以揭示数据中的模式。 在许多情况下，这些模式可以用来进行预测，从而丰富数据。 例如，购买行为可以用来预测客户流失或细分客户。 可以将预测结果添加到企业模型中，以便按客户细分进行分析。

在云 BI 平台中，可以使用 [Azure 机器学习](/azure/machine-learning/overview-what-is-azure-ml)来训练、部署、自动化、管理和跟踪 ML 模型。

## <a name="data-warehouse"></a>数据仓库

BI 平台的核心是数据仓库，它托管企业模型。 它是受约束的数据来源（作为记录系统和中心），为企业模型提供报表、BI 和数据科学。

许多业务服务（包括业务线 (LOB) 应用程序），都可以依赖数据仓库作为企业知识的权威和受管控的来源。

在 Microsoft，我们的数据仓库托管在 [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction) (ADLS Gen2) 和 Azure Synapse Analytics 上。

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="图中显示了连接到 Azure Data Lake Storage Gen2 的 Azure Synapse Analytics。":::

- ADLS Gen2 使 Azure 存储成为在 Azure 上构建企业 Data Lake 的基础。 它设计为处理多个 PB 量级的信息，同时保持数百 GB 的吞吐量。 而且它还提供低成本的存储容量和事务。 此外，它还支持 Hadoop 兼容访问，允许你管理和访问数据，就像在 Hadoop 分布式文件系统 (HDFS) 中一样。 事实上，[Azure HDInsight](/azure/hdinsight/)、[Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) 和 Azure Synapse Analytics 都可以访问 ADLS Gen2 中存储的数据。 因此，在 BI 平台中，存储原始源数据、半处理或临时数据以及可直接用于生产的数据都是不错的选择。 我们使用它来存储所有的业务数据。
- Azure Synapse Analytics 是一种分析服务，它将企业数据仓库和大数据分析结合在一起。 借助它可以使用无服务器的按需资源或预配资源，任意执行自己定义的大规模数据查询。 Synapse SQL 是 Azure Synapse Analytics 的一个组件，支持完整的基于 T-SQL 的分析，因此它非常适合托管包含维度和事实表的企业模型。 可以使用简单的 [Polybase T-SQL](/sql/relational-databases/polybase/polybase-guide) 查询从 ADLS Gen2 高效地加载表。 然后，可以使用 [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) 来运行高性能分析。

### <a name="business-rules-engine-framework"></a>业务规则引擎框架

我们开发了一个业务规则引擎 (BRE) 框架来对可以在数据仓库层实现的任何业务逻辑进行编目。 BRE 可能意味着很多情况，但是在数据仓库的上下文中，它对于在关系表中创建计算列非常有用。 这些计算列通常使用条件语句表示为数学计算或表达式。

目的是从核心 BI 代码拆分业务逻辑。 传统上，业务规则是硬编码到 SQL 存储过程中的，因此当业务需求发生更改时，通常需要花费大量精力来维护它们。 在 BRE 中，业务规则定义一次，并在应用于不同的数据仓库实体时多次使用。 如果计算逻辑需要更改，则只需在一个位置更新，而不需要在多个存储过程中进行更新。 还有一个附带好处：BRE 框架提高了实现的业务逻辑的透明度和可见性，可以通过一组创建自更新文档的报表来公开这些逻辑。

## <a name="data-sources"></a>数据源

数据仓库可以合并来自几乎任何数据源的数据。 它主要基于 LOB 数据源构建，这些数据源通常是用于存储销售、市场营销、财务等特定主题数据的关系数据库。这些数据库可以是云托管的，也可以驻留在本地。 其他数据源可以基于文件，尤其是源自设备的 web 日志或 IOT 数据。 此外，数据可以从软件即服务 (SaaS) 供应商处获得。

在 Microsoft，我们的一些内部系统使用原始文件格式将操作数据直接输出到 ADLS Gen2。 除了数据湖之外，其他源系统包括关系 LOB 应用程序、Excel 工作簿、其他基于文件的源、主数据管理 (MDM) 和自定义数据存储库。 通过 MDM 存储库，可以管理主数据，以确保数据的权威、标准化和验证版本。

## <a name="data-ingestion"></a>数据引入

根据业务的节奏，定期从源系统引入数据并将其加载到数据仓库中。 可以是一天一次，也可以是更频繁的间隔。 数据引入与提取、转换和加载数据有关。 或者，也可以反过来：提取、加载，然后转换数据。 不同之处在于转换发生的位置。 转换应用于清理、符合、集成和标准化数据。 有关详细信息，请参阅[提取、转换和加载 (ETL)](/azure/architecture/data-guide/relational-data/etl)。

最终，目标是尽可能快速、高效地将正确的数据加载到企业模型中。

在 Microsoft，我们会使用 [Azure 数据工厂](/azure/data-factory/introduction)。 该服务用于计划和编排数据验证、转换和从外部源系统到数据湖的大容量加载。 它由自定义框架管理，以大规模并行处理数据。 此外，还进行了全面的日志记录，以支持故障排除、性能监视，并在满足特定条件时触发警报通知。

与此同时，[Azure Databricks](/azure/azure-databricks/what-is-azure-databricks)（一个基于 Apache Spark 的分析平台，针对 Azure 云服务平台进行了优化）执行专门针对数据科学的转换。 它还使用 Python 笔记本来构建和执行 ML 模型。 这些 ML 模型的分数将加载到数据仓库中，以便将预测与企业应用程序和报表集成。 由于 Azure Databricks 会直接访问数据湖文件，所以它消除或最大程度降低了复制或获取数据的需要。

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="图像显示了 Azure 数据工厂在 Azure Data Lake Storage Gen2 上使用 Azure Databricks 来获取数据和编排数据管道。":::

### <a name="ingestion-framework"></a>引入框架

我们开发了一个引入框架，作为一组配置表和过程。 它支持数据驱动的方法，使用最少的代码高速获取大量数据。 简而言之，该框架简化了数据采集的过程，以加载数据仓库。

该框架依赖于存储数据源和数据目标相关的信息（如源类型、服务器、数据库、架构和表相关详细信息）的配置表。 这种设计方法意味着我们不需要开发特定的 ADF 管道或 [SQL Server Integration Services (SSIS) ](/sql/integration-services/sql-server-integration-services) 包。 相反，程序是用我们选择的语言编写的，以创建在运行时动态生成和执行的 ADF 管道。 因此，数据采集变成了一种易于操作的配置练习。 传统上，它需要大量的开发资源来创建硬编码的 ADF 或 SSIS 包。

引入框架用于简化处理上游源架构更改的过程。 如果检测到架构更改以获取源系统中新添加的属性，手动或自动更新配置数据很容易。

### <a name="orchestration-framework"></a>业务流程框架

我们开发了一个业务流程框架来操作和编排数据管道。 它使用依赖于一组配置表的数据驱动设计。 这些表存储描述管道依赖项以及如何将源数据映射到目标数据结构的元数据。 开发这种自适应框架的投资可以收回成本；不再需要硬编码每个数据移动。

## <a name="data-storage"></a>数据存储

数据湖可以存储大量的原始数据，供以后使用以及暂存数据转换。

在 Microsoft，我们使用 ADLS Gen2 作为单个事实来源。 它将原始数据与暂存数据和可直接用于生产的数据一起存储。 它为大数据分析提供了一个高度可扩展、高性价比数据湖解决方案。 它结合了大规模高性能文件系统的强大功能，针对数据分析工作负载进行了优化，从而加快转化为见解的速度。

ADLS Gen2 提供了两个方面的优点：它是 BLOB 存储和一个高性能的文件系统命名空间，我们使用细化的访问权限对其进行了配置。

然后，经过优化的数据会存储在关系数据库中，以便为企业模型提供高性能、高度可缩放的数据存储，并提供安全性、管控性和可管理性。 特定于主题的数据市场存储在 Azure Synapse Analytics 中，它由 Azure Databricks 或 Polybase T-SQL 查询加载。

## <a name="data-consumption"></a>数据使用

在报告层，业务服务使用源自数据仓库的企业数据。 它们还直接访问数据湖中的数据，以便执行临时分析或数据科学任务。

细化权限在所有层（数据湖、企业模型和 BI 语义模型）强制执行。 这些权限确保数据使用者只能看到他们有权访问的数据。

在 Microsoft，我们使用 Power BI 报表和仪表板以及 [Power BI 分页报表](../paginated-reports/paginated-reports-report-builder-power-bi.md)。 一些报表和临时分析是在 Excel 中完成的，特别是财务报表。

我们发布了数据字典，提供关于数据模型的参考信息。 用户可以使用它们来发现有关 BI 平台的信息。 字典文档模型设计，提供有关实体、格式、结构、数据世系、关系和计算的说明。 我们使用 [Azure 数据目录](/azure/data-catalog/overview)使数据源易于发现和理解。

通常，数据使用模式因角色而异：

- 数据分析师直接连接到核心 BI 语义模型。 当核心 BI 语义模型包含所需的所有数据和逻辑时，他们使用实时连接来创建 Power BI 报表和仪表板。 当他们需要用部门数据扩展模型时，将创建 Power BI [复合模型](composite-model-guidance.md)。 如果需要电子表格样式的报表，他们使用 Excel 根据核心 BI 语义模型或部门 BI 语义模型生成报表。
- BI 开发人员和操作报表作者直接连接到企业模型。 他们使用 Power BI Desktop 创建实时连接分析报表。 他们还可以编写操作类型的 BI 报表作为 Power BI 分页报表，使用 T-SQL 编写原生 SQL 查询来访问来自 Azure Synapse Analytics 企业模型的数据，或者使用 DAX 或 MDX 编写 Power BI 语义模型。
- 数据科学家直接连接到数据湖中的数据。 他们使用 Azure Databricks 和 Python 笔记本来开发 ML 模型，这些模型通常是实验性的，需要专业技能才能用于生产。

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="图像显示了用于 Power BI、Excel 和 Azure 机器学习的 Azure Synapse Analytics 的使用情况。":::

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [通过 Azure Synapse Analytics 实现 Azure 中的企业 BI](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

### <a name="professional-services"></a>专业服务

经过认证的 Power BI 合作伙伴可帮助你的组织在设置 COE 时取得成功。 他们可为你提供经济高效的培训或对你的数据进行审核。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

你还可以与经验丰富的咨询合作伙伴合作。 他们可帮助你[评估](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL)、[计算](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL)或[实现](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI。

---
title: 创建要迁移到 Power BI 的内容
description: 有关在迁移到 Power BI 时创建和验证内容的指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 03a55f2f414ca8af7ca86f51dcafb0258efc88b7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418592"
---
# <a name="create-content-to-migrate-to-power-bi"></a>创建要迁移到 Power BI 的内容

本文介绍“阶段 4”，涉及在迁移到 Power BI 时创建和验证内容的过程。

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="显示了 Power BI 迁移各阶段的图像。本文重点介绍阶段 4。":::

> [!NOTE]
> 有关上图的完整说明，请参阅 [Power BI 迁移概述](powerbi-migration-overview.md)。

阶段 4 的重点是执行实际工作，将概念证明 (POC) 转换为生产就绪解决方案。

此阶段的输出是一个 Power BI 解决方案，该解决方案已在开发工作区中进行了验证，并已准备好部署到生产环境。

> [!TIP]
> 本文中讨论的大多数主题也适用于标准 Power BI 实现项目。

## <a name="create-the-production-solution"></a>创建生产解决方案

此时，执行 POC 的同一人员可以继续产出生产准备就绪 Power BI 解决方案。 也可让其他人员参与进来。 如果不影响时间线，最好让将来负责 Power BI 开发的人员参与进来。 这样，他们可以主动学习。

> [!IMPORTANT]
> 尽可能地重用 POC 中的工作。

### <a name="develop-new-import-dataset"></a>开发新的导入数据集

如果还没有可满足需求的现有 Power BI 数据集，或者无法优化现有数据集以满足需求时，可以选择创建新的导入数据集。

理想情况下，从一开始就考虑将数据和报表的开发工作分离开来。 [分离数据和报表](report-separate-from-model.md)有助于在分派了不同人员来负责数据建模和报表时分离工作和权限。 它提供了更具缩放性的方法，并鼓励数据可重用性。

与开发导入数据集相关的基本活动包括：

- 从一个或多个数据源（可以是 Power BI 数据流）[获取数据](../connect-data/desktop-quickstart-connect-to-data.md)。
- [调整、组合和准备](../connect-data/desktop-shape-and-combine-data.md)数据。
- 创建[数据集模型](../transform-model/desktop-modeling-view.md)，包括[日期表](../transform-model/desktop-date-tables.md)。
- 创建并验证[模型关系](../transform-model/desktop-create-and-manage-relationships.md)。
- 定义[度量值](../transform-model/desktop-measures.md)。
- 如有必要，设置[行级别安全性](../admin/service-admin-rls.md)。
- 配置同义词并[优化问答](../natural-language/q-and-a-best-practices.md)。
- 规划可伸缩性、性能和并发性，这可能会影响有关数据存储模式的决策，如使用[复合模型](../transform-model/desktop-composite-models.md)或[聚合](../transform-model/desktop-aggregations.md)。

> [!TIP]
> 如果具有不同的开发/测试/生产环境，请考虑对数据源进行[参数化](/power-query/power-query-query-parameters)。 这可以极大简化[阶段 5](powerbi-migration-deploy-support-monitor.md) 中所述的部署。

### <a name="develop-new-reports-and-dashboards"></a>开发新报表和仪表板

与 Power BI 报表或仪表板的开发相关的基本活动包括：

- 确定是使用与现有数据模型的实时连接还是创建新的数据模型
- 创建新的数据模型时，确定模型表的[数据存储模式](../transform-model/desktop-storage-mode.md)（导入、DirectQuery 或复合）。
- 确定最满足要求的数据可视化工具：Power BI Desktop、分页报表生成器或 Excel。
- 确定最能传达报表要传达的信息并解决报表需要回答的问题的[最合适的视觉对象](../consumer/end-user-visual-type.md)。
- 确保所有视觉对象采用清晰、简洁和有利于业务的术语。
- 解决交互要求。
- 使用实时连接时，添加[报表级别度量值](../transform-model/desktop-tutorial-create-measures.md)。
- 在 Power BI 服务中创建[仪表板](../create-reports/service-dashboards.md)，尤其是在使用者需要简单的方法来监视关键指标时。

> [!NOTE]
> 其中的许多决策会在规划的早期阶段或技术 POC 期间做出。

## <a name="validate-the-solution"></a>验证解决方案

Power BI 解决方案的验证主要有以下四个方面：

1. 数据准确性
2. 安全性
3. 功能
4. 性能

### <a name="validate-data-accuracy"></a>验证数据准确性

作为迁移过程中的一次性工作，你需要确保新报表中的数据与旧报表中显示的数据匹配。 或者，如果存在差异，应能够解释出原因。 旧解决方案中发现的错误在新解决方案中得到解决比你想象的要更常见。

作为正在进行的数据验证工作的一部分，通常需要将新报表与原始源系统进行交叉检查。 理想情况下，每次发布报表更改时，都应再次执行此验证。

### <a name="validate-security"></a>验证安全性

验证安全性时，需要考虑两个主要方面：

- 数据权限
- 对数据集、报表和仪表板的访问

在导入数据集中，通过定义[行级别安全性](../admin/service-admin-rls.md) (RLS) 来应用数据权限。 使用 DirectQuery 存储模式（可能使用[单一登录](../connect-data/service-gateway-sso-overview.md)）时，源系统还可能会强制执行数据权限。

授予对 Power BI 内容的访问权限的主要方法有：

- [工作区角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)（适用于内容编辑器和查看器）。
- [应用权限](../collaborate-share/service-create-distribute-apps.md#publish-your-app)应用于一组打包的工作区内容（适用于查看器）。
- [共享](../collaborate-share/service-share-dashboards.md)单个报表或仪表板（适用于查看器）。

> [!TIP]
> 建议就如何有效地管理安全性对内容作者进行训练。 实施可靠的测试、审核和监视也很重要。

### <a name="validate-functionality"></a>验证功能

此时应仔细检查数据集的细节信息，如字段名称、格式、排序和默认摘要行为。 还应验证交互式报表功能（如[切片器](../visuals/power-bi-visualization-slicers.md)、[向下钻取](../consumer/end-user-drill.md)、[钻取](../create-reports/desktop-drillthrough.md)、[表达式](../create-reports/desktop-conditional-format-visual-titles.md)、[按钮](../create-reports/desktop-buttons.md)或[书签](../create-reports/desktop-bookmarks.md)）。

在开发过程中，应定期将 Power BI 解决方案发布到 Power BI 服务中的开发工作区。 验证所有功能是否按预期方式在服务中正常工作，如自定义视觉对象的呈现。 此时还很适合执行进一步的测试。 测试[计划的刷新](../connect-data/refresh-scheduled-refresh.md)、[问答](../consumer/end-user-q-and-a.md)，并查看报表和仪表板在[移动设备](../consumer/mobile/mobile-apps-for-mobile-devices.md)上的呈现效果。

### <a name="validate-performance"></a>验证性能

Power BI 解决方案的性能对于使用者的体验非常重要。 大多数报表在 10 秒内应显示视觉对象。 如果报表的加载时间较长，请暂停并重新考虑可能导致延迟的原因。 除了 Power BI Desktop 之外，还应定期在 Power BI 服务中评估报表性能。

许多性能问题都是由未达标准的 [DAX（数据分析表达式）](../transform-model/desktop-quickstart-learn-dax-basics.md)、糟糕的数据集设计或欠佳的报表设计（例如，尝试在单个页上呈现过多的视觉对象）引起的。 技术环境问题（例如网络、过载的数据网关）或配置高级容量的方式也会导致性能问题。 有关详细信息，请参阅 [Power BI 优化指南](power-bi-optimization.md)和 [Power BI 中的报表性能疑难解答](report-performance-troubleshoot.md)。

## <a name="document-the-solution"></a>记录解决方案

对于 Power BI 解决方案，主要有两种有用的文档类型：

- 数据集文档
- 报表文档

文档可以存储在目标受众最容易访问的任何位置。 常用选项包括：

- **在 SharePoint 站点中：** 可为“卓越中心”或内部 Power BI 社区站点设立一个 SharePoint 站点。
- **在应用中：** 发布 Power BI 应用时可以配置 URL，以引导使用者获得详细信息。
- **在单个 Power BI Desktop 文件中：** 模型元素（如表和列）可以定义描述信息。 创作报表时，这些描述信息会作为工具提示显示在“字段”窗格中。

> [!TIP]
> 如果创建一个站点充当 Power BI 相关文档的中心，请考虑使用其 URL 位置来[自定义“获取帮助”菜单](../admin/service-admin-portal.md#publish-get-help-information)。

### <a name="create-dataset-documentation"></a>创建数据集文档

数据集文档面向将来要管理数据集的用户。 应包括以下有用信息：

- 设计决策及其原因。
- 谁拥有、维护和认证数据集。
- 数据刷新要求。
- 数据集中定义的自定义业务规则。
- 特定数据集安全性或数据隐私要求。
- 未来的维护需求。
- 已知的未决问题或延迟的积压工作 (backlog) 项。

还可以选择创建一个更改日志，用于汇总一段时间内数据集发生的最重要的更改。

### <a name="create-report-documentation"></a>创建报表文档

报表文档（通常是面向报表使用者的演示内容）可帮助使用者从报表和仪表板获取更多价值。 一个简短的视频教程通常会有很好的效果。

还可以选择在报表的隐藏页上包含其他报表文档。 它可能包括设计决策和更改日志。

## <a name="next-steps"></a>后续步骤

在本 [Power BI 迁移系列的下一篇文章](powerbi-migration-deploy-support-monitor.md)中，了解阶段 5，该阶段涉及在迁移到 Power BI 时部署、支持和监视内容的过程。

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

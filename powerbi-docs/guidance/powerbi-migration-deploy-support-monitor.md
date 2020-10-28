---
title: 部署到 Power BI
description: 有关在迁移到 Power BI 时部署、支持和监视内容的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: f9268409977b3aa78e1ebda6f1f6b2e732451455
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92681019"
---
# <a name="deploy-to-power-bi"></a>部署到 Power BI

本文介绍“阶段 5”，涉及在迁移到 Power BI 时部署、支持和监视内容的过程。

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="显示了 Power BI 迁移各阶段的图像。本文重点介绍阶段 5。":::

> [!NOTE]
> 有关上图的完整解释，请参阅 [Power BI 迁移概述](powerbi-migration-overview.md)。

阶段 5 的重点是将新的 Power BI 解决方案部署到生产环境中。

这个阶段的输出是一个可供业务使用的生产解决方案。 在使用敏捷方法时，可以规划一些要在将来的迭代中交付的增强功能。 支持和监视对于现阶段和后续阶段而言也很重要。

> [!TIP]
> 除了下面讨论的并行运行新旧报表和停用旧报表外，本文中讨论的主题也适用于标准的 Power BI 实现项目。

## <a name="deploy-to-test-environment"></a>部署到测试环境

对于 IT 管理的解决方案或对业务效率而言至关重要的解决方案，通常都有一个测试环境。 测试环境位于开发环境和生产环境之间，但并非对所有 Power BI 解决方案都是必要的。 测试工作区可以充当一个与开发环境分离的稳定位置，以便可以在发布到生产环境之前进行用户验收测试 (UAT)。

如果你的内容已发布到高级容量中的工作区，可通过[部署管道](../create-reports/deployment-pipelines-overview.md)简化部署到开发、测试和生产工作区的过程。 或者，可以手动或使用 [PowerShell 脚本](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/)进行发布。

### <a name="deploy-to-test-workspace"></a>部署到测试工作区

部署到测试工作区期间的关键活动通常包括：

- **字符串和参数：** 如果开发环境和测试环境的数据源不同，请调整数据集连接字符串。 可利用[参数化](../connect-data/service-parameters.md)有效管理连接字符串。
- **工作区内容：** 将数据集和报表发布到测试工作区，并创建仪表板。
- **应用。** 使用测试工作区中的内容发布一个[应用](../consumer/end-user-apps.md)，前提是它将构成 UAT 过程的一部分。 通常，应用权限仅限于参与 UAT 的少数人。
- **数据刷新：** 为 UAT 进行期间的任何导入数据集 [安排数据集刷新](../connect-data/refresh-scheduled-refresh.md)。
- **安全性：** 更新或验证 [工作区角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。 测试工作区访问的过程包括参与 UAT 的少数人。

> [!NOTE]
> 有关部署到开发环境、测试环境和生产环境的选项的详细信息，请参阅[规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)的第 9 节。

### <a name="conduct-user-acceptance-testing"></a>执行用户验收测试

UAT 涉及的业务用户通常是主题专家。 经过验证后，他们将批准确认新内容是准确的、符合要求的，可以部署供更多人使用。

此 UAT 过程的正式程度（包括书面签核），取决于变更管理实践。

## <a name="deploy-to-production-environment"></a>部署到生产环境

在部署到生产环境时有几个注意事项。

### <a name="conduct-a-staged-deployment"></a>执行分阶段部署

如果想最小化风险和用户中断（或者还有其他顾虑），可以选择执行分阶段部署。 第一次部署到生产环境中可能会涉及一个小规模试点用户组。 通过试点操作，可以主动请试验用户提供反馈。

逐步扩展生产工作区或应用中的权限，直到所有目标用户都有权使用新的 Power BI 解决方案。

> [!TIP]
> 使用 [Power BI 活动日志](../admin/service-admin-auditing.md)了解使用者如何采用和使用新的 Power BI 解决方案。

### <a name="handle-additional-components"></a>处理其他组件

在部署过程中，你可能需要与 Power BI 管理员合作，以满足支持整个解决方案所需达到的其他要求，例如：

- **网关维护：** 可能需要在数据网关中进行 [新数据源](../connect-data/service-gateway-data-sources.md)注册。
- **网关驱动程序和连接器：** 新的专有数据源可能要求在网关群集中的每个服务器上安装新的驱动程序或自定义连接器。
- **创建新的高级容量：** 可能可以使用现有的 [高级容量](../admin/service-premium-capacity-manage.md)。 也可能需要提供新的高级容量。 如果有意将部门工作负载分开，就可能会出现这种情况。
- **设置 Power BI 数据流：** 可在 [Power BI 数据流](../transform-model/service-dataflows-overview.md)中使用 Power Query Online 设置数据准备活动。 这有助于避免复制许多不同 Power BI Desktop 文件中的数据准备工作。
- **注册新的组织视觉对象：** 可以在管理门户中为不是来自 AppSource 的自定义视觉对象完成 [组织视觉对象](../developer/visuals/power-bi-custom-visuals-organization.md)注册。
- **设置特色内容：** 有一个租户设置可用于控制谁可以在 Power BI 服务主页中使用 [功能内容](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)。
- **设置敏感度标签：** 所有 [敏感度标签](../admin/service-security-data-protection-overview.md) 都可以与 Microsoft 信息保护集成。

### <a name="deploy-to-production-workspace"></a>部署到生产工作区

部署到生产工作区期间的关键活动通常包括：

- **变更管理：** 如果需要，请获得部署批准，并使用标准变更管理实践将部署信息传达给用户群体。 可能会有一个经批准的变更管理时段，在此期间允许生产环境部署。 它通常用于 IT 管理的内容，而很少用于自助服务内容。
- **回滚计划：** 对于迁移，预期是第一次迁移新解决方案。 如果内容已经存在，明智的做法是规划将内容还原为以前的版本（如果需要）。 保有以前版本的 Power BI Desktop 文件（使用 SharePoint 或 OneDrive 版本控制）可以很好地实现这一目的。
- **字符串和参数：** 如果测试环境和生产环境的数据源不同，请调整数据集连接字符串。 可以有效使用[参数化](../connect-data/service-parameters.md)来帮助实现此目的。
- **数据刷新：** 为任何导入的数据集 [安排数据集刷新](../connect-data/refresh-scheduled-refresh.md)。
- **工作区内容：** 将数据集和报表发布到生产工作区，并创建仪表板。 如果你的内容已发布到高级容量中的工作区，可通过[部署管道](../create-reports/deployment-pipelines-overview.md)简化部署到开发、测试和生产工作区的过程。
- **应用：** 如果应用是内容分发策略的一部分，请使用生产工作区中的内容发布一个 [应用](../consumer/end-user-apps.md)。
- **安全性：** 基于你的内容分发和协作策略更新并验证 [工作区角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。
- **数据集设置：** 更新并验证每个数据集的设置，包括：
  - [认可](../collaborate-share/service-endorse-content.md)（如认证或升级）
  - 网关连接或数据源凭据
  - 计划的刷新
  - [精选问答](../create-reports/service-q-and-a-create-featured-questions.md)
- **报表和仪表板设置：** 更新并验证每个报表和仪表板的设置。 最重要的设置包括：
  - 说明
  - 联系人或组
  - [敏感度标签](../admin/service-security-apply-data-sensitivity-labels.md)
  - [特别推荐的内容](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **订阅：** 如果需要，请设置报表订阅。

> [!IMPORTANT]
> 此时，你已完成了一个重要里程碑。 庆祝完成迁移。

### <a name="communicate-with-users"></a>与用户沟通

向使用者宣布新的解决方案。 让他们知道在何处可以找到内容，以及相关的文档、常见问题解答和教程。 若要引入新内容，请考虑举办一次午餐交流会形式的会议或准备一些点播视频。

应确保包括有关如何请求帮助以及提供反馈的说明。

### <a name="conduct-a-retrospective"></a>进行回顾

请考虑进行回顾，以检查迁移中哪些方面做得好，哪些方面可以在下一次迁移中改进。

## <a name="run-in-parallel"></a>并行运行

在许多情况下，新的解决方案将在预先确定的时间段内与旧有解决方案并行运行。 并行运行的优点包括：

- 降低风险，特别是在将报表视为关键任务的情况下。
- 让用户有时间了解和适应新的 Power BI 解决方案。
- 允许 Power BI 中显示的信息对旧报表内容进行交叉引用。

## <a name="decommission-the-legacy-report"></a>正式停止使用旧报表

当到达某个时点后，应在旧 BI 平台中禁用迁移到 Power BI 的报表。 可能会在以下情况下正式停止使用旧报表：

- 到达预先确定的并行运行时间（应已传达给用户群体）。 通常为 30-90 天。
- 旧系统的所有用户都有权访问新的 Power BI 解决方案。
- 旧报表上不再发生重要活动。
- 新的 Power BI 解决方案没有出现会影响用户生产力的问题。

## <a name="monitor-the-solution"></a>监视解决方案

可借助 [Power BI 活动日志](../admin/service-admin-auditing.md)中的事件（或部署到 Power BI 报表服务器的内容的[执行日志](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view)）了解对新解决方案的使用模式。 分析活动日志有助于确定实际使用是否与预期不同。 它还可以验证解决方案是否得到充分支持。

以下是一些可以通过查看活动日志来解决的问题：

- 内容查看频率有多高？
- 谁在查看内容？
- 通常是通过应用还是工作区来查看内容？
- 大多数用户是使用浏览器还是移动应用程序？
- 是否使用了订阅？
- 是否基于此解决方案创建了新报表？
- 内容更新频率有多高？
- 如何定义安全性？
- 是否会经常发生问题，例如数据刷新失败？
- 是否发生了意味着需要提供更多培训的相关活动（例如，大规模导出活动或大量个人报表共享）？

> [!IMPORTANT]
> 请确保有人定期查看活动日志。 即使只捕获和存储历史记录，对审核或合规性目的而言也是有价值的。 但是，真正的价值在于何时可以主动采取措施。

## <a name="support-the-solution"></a>支持解决方案

虽然迁移已经完成，但是迁移后的时期对于解决问题和处理任何性能问题至关重要。 随着时间的推移，迁移的解决方案很可能会随着业务需求的发展而发生改变。

根据在整个组织中如何管理自助式 BI，所提供的支持可能会有所不同。 企业和业务中所有成功利用 Power BI 的人员通常会成为潜在的一线支持人员。 尽管这是一个非正式角色，但它至关重要，应予以鼓励。

设置正式的支持流程并由 IT 人员通过支持工单提供支持，对于处理面向系统的例行请求和实现升级也至关重要。

你可能还会设置一个[卓越中心 (COE)](center-of-excellence-establish.md)，其作用类似于内部顾问，在组织中提供与 Power BI 相关的支持、培训和管理服务。 可部署 COE，负责在内部门户中策划有用的 Power BI 内容。

最后，应使内容使用者能够清楚了解谁来处理关于内容的问题，并制定一个机制来提供关于问题或改进的反馈。

## <a name="next-steps"></a>后续步骤

[本系列的最后一篇文章](powerbi-migration-learn-from-customers.md)介绍如何在客户迁移到 Power BI 时请其提供反馈。

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

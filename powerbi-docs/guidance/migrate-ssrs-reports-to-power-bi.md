---
title: 将 SQL Server Reporting Services 报表迁移到 Power BI
description: 有助于将 SQL Server Reporting Services (SSRS) 报表迁移到 Power BI 的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: b87848953722d33235a11729a3643c627cca7234
ms.sourcegitcommit: 646d2de454a2897dc52cbc02b7743aaa021bac04
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525605"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>将 SQL Server Reporting Services 报表迁移到 Power BI

本文适用于 SQL Server Reporting Services (SSRS) 报表作者和 Power BI 管理员。 它为你提供指导，帮助将[报表定义语言 (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) 报表迁移到 Power BI。

> [!NOTE]
> 只能迁移 RDL 报表。 在 Power BI 中，RDL 报表称为分页报表  。

指南分为四个阶段。 建议你先阅读整篇文章，然后再迁移报表。

1. [开始之前](#before-you-start)
1. [预迁移阶段](#pre-migration-stage)
1. [迁移阶段](#migration-stage)
1. [迁移后阶段](#post-migration-stage)

你可以在不停机的情况下实现到 SSRS 服务器的迁移，或者在无中断的情况下实现到报表用户的迁移。 请务必了解，无需删除任何数据或报表。 这意味着在准备好停用当前环境之前，可以保持该环境。

## <a name="before-you-start"></a>开始之前

在开始迁移之前，应验证你的环境是否满足某些先决条件。 我们将介绍这些先决条件，并向你介绍有用的迁移工具。

### <a name="preparing-for-migration"></a>准备迁移

在准备将报表迁移到 Power BI 时，请首先验证你的组织是否具有 [Power BI Premium](../service-premium-what-is.md) 订阅。 托管和运行 Power BI 分页报表将需要此订阅。

### <a name="supported-versions"></a>支持的版本

你可以迁移在本地或云提供商（如 Azure）托管的虚拟机上运行的 SSRS 实例。

以下列表描述了支持迁移到 Power BI 的 SQL Server 版本：

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

也可以从 Power BI 报表服务器进行迁移。

### <a name="migration-tool"></a>迁移工具

建议使用 [RDL 迁移工具](https://github.com/microsoft/RdlMigration)来帮助准备和迁移报表。 此工具由 Microsoft 开发，可帮助客户将 RDL 报表从其 SSRS 服务器迁移到 Power BI。 它在 GitHub 上提供，并记录了迁移方案的端到端演练。

该工具自动执行以下任务：

* 检查[不支持的数据源](../paginated-reports/paginated-reports-data-sources.md)和[不支持的报表功能](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
* 将任何共享资源转换为嵌入资源   ：
  * 共享数据源成为嵌入数据源 
  * 共享数据集成为嵌入数据集 
* 将（通过检查的）报表作为分页报表发布到指定的 Power BI 工作区（在高级容量中）

它不会修改或删除现有报表。 完成后，该工具将输出已完成的所有操作（无论成功与否）的摘要。

Microsoft 可能会随时间对该工具进行改进。 并且还鼓励社区促进并帮助对其进行改进。

## <a name="pre-migration-stage"></a>预迁移阶段

验证你的组织是否满足先决条件后，就可以开始预迁移阶段了  。 此阶段分为三个阶段：

1. 发现
1. 评估
1. 准备

### <a name="discover"></a>发现

“发现”阶段的目标是识别现有的 SSRS 实例  。 此过程包括扫描网络以识别组织中的所有 SQL Server 实例。

你可以使用 [Microsoft 评估和计划工具包](https://www.microsoft.com/download/details.aspx?id=7826)。 该工具包也称为“MAP 工具包”，可以发现和报告 SQL Server 实例、版本和已安装的功能。 它是一种功能强大的清单、评估和报告工具，可简化迁移计划流程。

### <a name="assess"></a>评估

在发现 SSRS 实例之后，“评估”阶段的目标就是了解无法迁移的任何 SSRS 报表或服务器项  。

仅 RDL 报表可以从 SSRS 服务器迁移到 Power BI。 每个已迁移的 RDL 报表都将成为 Power BI 分页报表。

但是，以下 SSRS 项类型无法迁移到 Power BI：

- 共享数据源 <sup>1</sup>
- 共享数据集 <sup>1</sup>
- 图像文件等资源
- KPI（SSRS 2016 或更高版本 - 仅限 Enterprise Edition）
- 移动报表（SSRS 2016 或更高版本 - 仅限 Enterprise Edition）
- 报表模型（已弃用）
- 报表部件（已弃用）

<sup>1</sup> [RDL 迁移工具](https://github.com/microsoft/RdlMigration)自动转换共享数据源和共享数据集，前提是它们使用受支持的数据源。

如果 RDL 报表依赖于 [Power BI 分页报表尚不支持的功能](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)，则可以计划将其重新开发为 [Power BI 报表](../consumer/end-user-reports.md)。 即使你的 RDL 报表可以迁移，我们也建议你在有意义的情况下考虑将它们现代化为 Power BI 报表。

如果 RDL 报表需要从本地数据源  检索数据，则它们不能使用单一登录 (SSO)。 目前，将使用网关数据源用户帐户  的安全上下文来从这些源检索所有数据。 SQL Server Analysis Services (SSAS) 不可能基于每个用户强制执行行级别安全性 (RLS)。

一般来说，Power BI 分页报表已针对“打印”或“PDF 生成”进行了优化   。 Power BI 报表已针对“浏览和交互性”进行了优化  。 有关更多详细信息，请参阅[何时使用 Power BI 中的分页报表](report-paginated-or-power-bi.md)。

### <a name="prepare"></a>准备

“准备”阶段的目标是准备好一切事情  。 它包括设置 Power BI 环境、计划如何保护和发布报表，以及重新开发不会迁移的 SSRS 项的想法。

1. 确保为 Power BI Premium 容量启用了[分页报表工作负荷](../service-admin-premium-workloads.md#paginated-reports)，并且该工作负荷具有足够的内存。
1. 验证对报表[数据源](../paginated-reports/paginated-reports-data-sources.md)的支持，并设置 [Power BI 网关](../service-gateway-onprem.md)以允许与任何本地数据源连接。
1. 熟悉 Power BI 安全性，并计划如何通过 [Power BI 工作区和工作区角色](../service-new-workspaces.md)[复制 SSRS 文件夹和权限](/sql/reporting-services/security/secure-folders)。
1. 熟悉 Power BI 共享，并计划如何通过发布 [Power BI 应用](../service-create-distribute-apps.md)来分发内容。
1. 考虑使用[共享 Power BI 数据集](../service-datasets-build-permissions.md)来代替 SSRS 共享数据源。
1. 使用 [Power BI Desktop](../desktop-what-is-desktop.md) 来开发移动优化报表，可以使用 [Power KPI 自定义视觉对象](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview)来代替 SSRS 移动报表和 KPI。
1. 重新计算报表中 UserID  内置字段的使用。 如果依赖于 UserID  来保护报表数据，则请注意，对于分页报表（在 Power BI 服务中托管时），它会返回用户主体名称 (UPN)。 因此，内置字段将返回诸如  m.blythe&commat;adventureworks.com 的内容，而不会返回 NT 帐户名称，例如 AW\mblythe  。 你将需要修订数据集定义，可能还需要修订源数据。 修订并发布后，建议全面测试报表，以确保数据权限按预期方式工作。
1. 重新计算报表中 ExecutionTime  内置字段的使用。 对于分页报表（在 Power BI 服务中托管时），内置字段以协调世界时（或 UTC）  返回日期/时间。 这可能会影响报表参数默认值和报表执行时间标签（通常被添加到报表页脚）。
1. 如果你的数据源是 SQL Server（本地），请验证报表是否未使用地图可视化效果。 地图可视化效果依赖于 SQL Server 空间数据类型，网关不支持这些数据类型。 有关详细信息，请参阅[分页报表的数据检索指南（SQL Server 复杂数据类型）](report-paginated-data-retrieval.md#sql-server-complex-data-types)。
1. 确保你的报表作者已安装 [Power BI 报表生成器](../paginated-reports/report-builder-power-bi.md)，并且可以轻松地在组织中分发更高版本。

## <a name="migration-stage"></a>迁移阶段

准备好 Power BI 环境和报表之后，就可以开始“迁移”阶段了  。

有两种迁移选项：手动和自动   。 手动迁移适用于少量报表或迁移前需要修改的报表。 自动迁移适用于大量报表的迁移。

### <a name="manual-migration"></a>手动迁移

任何具有访问 SSRS 实例和 Power BI 工作区权限的人都可以手动将报表迁移到 Power BI。 下面是需要遵循的步骤：

1. 打开包含要迁移的报表的 SSRS 门户。
1. 下载每个报表定义，将 .rdl 文件保存在本地。
1. 打开 Power BI 报表生成器的最新版本，并使用 Azure AD 凭据连接到 Power BI 服务  。
1. 在 Power BI 报表生成器中打开每个报表，然后：
   1. 验证所有数据源和数据集是否都嵌入到了报表定义中，以及它们是否是[受支持的数据源](../paginated-reports/paginated-reports-data-sources.md)。
   1. 预览报表以确保其正确呈现。
   1. 选择“另存为”选项，然后选择“Power BI 服务”   。
   1. 选择将包含报表的工作区。
   1. 确认报表已保存。 如果报表设计中的某些功能尚不受支持，则保存操作将失败。 你将收到有关原因的通知。 然后需要修改报表设计，并再次尝试保存。

### <a name="automated-migration"></a>自动迁移

自动迁移有两种选择。 可用工具如下：

- RDL 迁移工具
- 适用于SSRS 和 Power BI 的公开可用 API

本文已介绍了 [RDL 迁移工具](#migration-tool)。

你还可以使用公开可用的 SSRS 和 Power BI API 来自动迁移内容。 虽然 RDL 迁移工具已经使用了这些 API，但是你可以开发适合你具体需求的自定义工具。

有关 API 的详细信息，请参阅：

- [Power BI REST API 引用](../developer/automation/rest-api-reference.md)
- [SQL Server Reporting Services REST API](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>迁移后阶段

成功完成迁移后，就可以进入迁移后阶段了  。 此阶段包括完成一系列迁移后任务，以确保一切正常有效地运行。

### <a name="configure-data-sources"></a>配置数据源

将报表迁移到 Power BI 之后，需要确保正确设置其数据源。 它可以包括分配给网关数据源，以及[安全地存储数据源凭据](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication)。 RDL 迁移工具不会执行这些操作。

### <a name="review-report-performance"></a>查看报表性能

我们强烈建议你完成以下操作，以确保获得尽可能最佳的报表用户体验：

1. 在 [Power BI 支持的每个浏览器](../power-bi-browsers.md)中测试报表，以确认报表呈现正确。
1. 运行测试以比较 SSRS 和 Power BI 中的报表呈现时间。 检查 Power BI 报表是否能够在可接受的时间内呈现。
1. 如果 Power BI 报表由于内存不足而无法呈现，[请为 Power BI Premium 容量分配其他资源](../service-admin-premium-workloads.md#paginated-reports)。
1. 对于长时间呈现的报表，请考虑让 Power BI 将它们作为[带有报表附件的电子邮件订阅](../consumer/paginated-reports-subscriptions.md)传递给报表用户。
1. 对于基于 Power BI 数据集的 Power BI 报表，请查看模型设计，以确保它们已完全优化。

### <a name="reconcile-issues"></a>协调问题

迁移后阶段对于协调任何问题以及解决任何性能问题都至关重要。 将分页报表工作负荷添加到容量中可能会导致分页报表和存储在容量中的其他内容的性能降低  。

有关这些问题的更多信息，包括了解和缓解这些问题的具体步骤，请参阅以下文章：

- [优化 Premium 容量](../service-premium-capacity-optimize.md)
- [使用应用监视 Premium 容量](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI Premium 中的分页报表是什么？](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [分页报表的数据检索指南](report-paginated-data-retrieval.md)
- [何时使用 Power BI 中的分页报表](report-paginated-or-power-bi.md)
- [Power BI 中的分页报表：常见问题解答](../paginated-reports/paginated-reports-faq.md)
- [在线课程：一天玩转分页报表](../paginated-reports/paginated-reports-online-course.md)
- [Power BI Premium 常见问题解答](../service-premium-faq.md)
- [RDL 迁移工具](https://github.com/microsoft/RdlMigration)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)

Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。

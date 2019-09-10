---
title: Power BI 中的分页报表：常见问题解答
description: 本文将解答有关分页报表的常见问题。 这些报表是高度格式化且像素效果完美的输出，已针对打印或 PDF 生成进行了优化。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 09/04/2019
ms.openlocfilehash: 2be953c31ba3090e83e58f8e5626bb83e249556e
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302694"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Power BI 中的分页报表：常见问题解答 

本文将解答有关分页报表的常见问题。 这些报表是高度格式化且像素效果完美的输出，已针对打印或 PDF 生成进行了优化。 它们被称为“分页”，因为它们已进行了格式化，以适应多个页面。 分页报表基于 SQL Server Reporting Services 中的 RDL 报表技术。 

本文将解答人们有关 Power BI Premium 中的分页报表和有关报表生成器（用于创作分页报表的独立工具）的许多常见问题。 需要具有 Power BI Pro 许可证才能将报表发布到服务。 只要工作区处于 Power BI 高级容量中，就可以在“我的工作区”或应用工作区中发布和共享分页报表。 

## <a name="administration"></a>管理

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>用于分页报表的的高级容量的大小是多少？

分页报表工作负荷可用于 P1 - P3 SKU。  你也可以将它与 A4-A6 SKU 一起用于嵌入或测试/开发场景。

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>可以在我的容量中为分页报表保留的最大内存阈值是多少？

最多可以将全部内存用于此工作负荷。

### <a name="how-does-user-access-work-for-paginated-reports"></a>用户如何访问分页报表中的工作？

用户访问分页报表的方法与用户访问 Power BI 服务中的所有其他内容相同 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>我如何打开/关闭我的分页报表工作负载？

容量管理员可以在容量管理门户页面启用或禁用分页报表工作负载。  默认情况下，此工作负荷对你新建的任何容量都处于启用状态。  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>我如何在我的租户中监视分页报表的使用？

Office 365 审核日志在以下活动下详细记录此报表类型的使用情况： 

- 查看 Power BI 报表
- 删除 Power BI 报表
- 创建 Power BI 报表
- 已下载 Power BI 报表

字段 ReportType 使用“PaginatedReport”值来标识分页，这与 Power BI 报表不同。

此外，审核日志为分页报表提供以下事件：

- 将 Power BI 数据集绑定到网关
- 发现 Power BI 数据源
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>我可以通过高级容量监视应用来监视此工作负载吗？

可以，已增添了新的选项卡“监视”，其中包含了 Power BI 数据集的相关详细信息。

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>我是否需要具有 Pro 许可证才能创建和发布分页报表？

可以在没有 Pro 许可证的情况下，将分页报表上传到“我的工作区”，但前提是在高级容量中。  对于其他工作区，必须有 Pro 许可证，才能创作内容并发布到工作区中。 建议下载和使用 Power BI 报表生成器（即使没有 Pro 许可证），但无法发布在没有 Pro 许可证的情况下创建的分页报表。 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>如果我在工作区中有一个分页报表但分页报表工作负载已关闭，该如何处理？

你将收到一条错误消息，且在工作负载重新打开前，你将无法查看你的报表。 你仍然可以从工作区中删除报表。

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>每个高级 SKU 支持的分页报表的默认内存是多少？

每个高级 SKU 支持的分页报表的默认内存为：

- **P1/A4**：默认为 20%，最低为 10%
- **P2/A5**：默认为 20%，最低为 5%
- **P3/A6**：默认为 20%，最低为 2.5%

## <a name="general"></a>常规

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>我如何在分页报表和 Power BI 报表之间选择？

分页报表最适合于要求针对打印或 PDF 生成进行优化的高度格式化且像素效果完美的输出的应用场景。  例如，损益表就是你想要创建为分页报表的报表类型示例。  

Power BI 报表针对浏览和交互性进行了优化。  例如，对于销售报表（其中不同的销售人员想要在同一区域针对其特定区域/行业/客户切分数据并查看数字的变化情况），Power BI 报表将是最理想的选择。

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>文档中提到 Power BI 报表生成器是首选创作工具。 我可以在适用于 Power BI 的 SQL Server Data Tools 中创建分页报表吗？

可以，但 Power BI 服务仅允许你一次上传一个项目，因此，作者使用 SQL Server Data Tools (SSDT) 的许多应用场景尚未受支持。 在此常见问题解答中查看以后提供的完整的[不受支持的功能的列表](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)。  

### <a name="what-versions-of-report-builder-do-you-support"></a>支持哪些报表生成器版本？

我们最近发布了 Power BI 报表生成器，作为 Power BI 服务中分页报表的主要创作工具。 [从 Microsoft 下载中心安装 Power BI 报表生成器](https://go.microsoft.com/fwlink/?linkid=2086513)。

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>我如何将保存在 SQL Server Reporting Services 中的报表移动到 Power BI？

你需要从服务器下载报表，然后通过门户将其上传到 Power BI。  目前还没有可供使用的迁移工具，但我们正计划在完成公共预览版并在两种产品之间实现相应的一致性后创建一个迁移工具。

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>我可以打开报表并直接发布到服务吗？

是。 我们最近开始支持，在 Power BI 报表生成器中打开报表，并将报表直接发布到 Power BI 服务中。

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Power BI 中有哪些在 SSRS 中尚不支持的分页报表功能？

目前，分页报表不支持以下项：

- 共享数据源
- 共享的数据集
- 子报表
- 钻取到和单击后到达其他报表
- 链接报表
- 必应地图层
- 自定义字体

如果你尝试上传具有在 Power BI 服务中不受支持的功能的文件，则将收到一条错误消息，而不是切换/排序。

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>分页报表当前支持的数据源有哪些？

支持以下数据源 - 

- Power BI 数据集（通过单一登录 (SSO)）
- Azure Analysis Services（通过单一登录 (SSO) 和 oAuth）
- Azure SQL 数据仓库
- Azure SQL 数据库（用户名/密码，SSO 和 oAuth）
- SQL Server*
- SQL Server Analysis Services (SSAS) 表格 (DAX) 和多维 (MDX) 模型* 
- Oracle* 
- Teradata* 

* 需要本地网关。

通过网关访问 SSAS 时，存储凭据的用户需要 SSAS 中提升的权限才能通过网关。

### <a name="what-authentication-methods-do-you-support"></a>支持的身份验证方法有哪些？

Azure Analysis Services、Azure SQL 数据库和 Power BI 数据源支持 SSO。  Azure SQL 数据库和 Azure Analysis Services 还支持 OAuth。  对于其他数据源，目前需要将用户名和密码与数据源一起存储在门户或网关中。  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>我可以将 Power BI 数据集用作我的分页报表的数据源吗？

能，支持将 Power BI 数据集用作分页报表的数据源。

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>我可以在通过网关时使用存储的过程吗？

可以在通过网关时使用存储过程，但如果存储过程具有参数，在某些情况下可能会出现问题。

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Power BI 服务中针对我的报表提供的导出格式有哪些？

可以导出为 Microsoft Excel、Microsoft Word、Microsoft PowerPoint、PDF、.CSV、XML 和 MHTML。

### <a name="can-i-print-paginated-reports"></a>我可以打印分页报表吗？

能，打印功能可用于分页报表，包括经过改进的全新打印预览体验。 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>电子邮件订阅能用于分页报表吗？

能，分页报表完全支持电子邮件订阅，并支持六个不同的文件格式和参数值。

### <a name="can-i-run-custom-code-in-my-report"></a>我可以在我的报表中运行自定义代码吗？

可以，支持在你的报表中运行代码，这与在 SSRS 中一样。

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>我可以使用 Power BI Embedded 将我的分页报表嵌入到我正在管理的应用中吗？

已支持 SaaS 嵌入。 当前不支持 PaaS 嵌入。

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>我是否可以从 Power BI 报表钻取到分页报表？

可以，可通过将 URL 参数与分页报表一起使用来实现此目的。

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>我可以通过 Power BI 应用共享我的分页报表内容吗？

能，支持使用 v1 和 v2 工作区内的应用部署分页报表。 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Power BI 中的其他特定于报表的功能（例如，将报表磁贴固定到仪表板）也适用于分页报表吗？

我们计划尽可能让报表在服务中支持相同的主要方案。  理想情况下，尽管创作它们的工具不同，但从使用者的角度来看，它只是门户中其列表中的另一个报表。 他们并不关心它是如何创建的，只要他们能够完成他们需要的操作即可。  此功能奇偶一致性的一个很好的示例是计划的注释支持。 尽管功能本身针对每种报表类型的工作方式略有不同，但你可以为两者使用注释。

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>是否计划了迁移工具以便 SSRS 客户可以将其现有报表和资产移动到 Power BI？

我们正在评估各种选项，以实现通过自动化方式将内容移动到 Power BI，但在正式上市之前尚无法提供此功能。

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Power BI 服务中是否有针对分页报表的报表查看器控件？

没有，报表查看器控件尚不可用。

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>可以在 Power BI 服务中的新主页体验中搜索分页报表吗？

能，现在可以从“主页”搜索分页报表。  还可以在新“主页”体验的其他部分中看到它们。

## <a name="next-steps"></a>后续步骤

- [从 Microsoft 下载中心安装 Power BI 报表生成器](https://go.microsoft.com/fwlink/?linkid=2086513)
- [教程：创建分页报表](paginated-reports-quickstart-aw.md)

---
title: Power BI 中的分页报表：常见问题解答（预览）
description: 本文将解答有关分页报表的常见问题。 这些报表是高度格式化且像素效果完美的输出，已针对打印或 PDF 生成进行了优化。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: 0ddf95563c52af135ac7ae4fe71aeddcd2ce7313
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51266638"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Power BI 中的分页报表：常见问题解答（预览）

本文将解答有关分页报表的常见问题。 这些报表是高度格式化且像素效果完美的输出，已针对打印或 PDF 生成进行了优化。 它们被称为“分页”，因为它们已进行了格式化，以适应多个页面。 分页报表基于 SQL Server Reporting Services 中的 RDL 报表技术。 

本文将解答人们有关 Power BI Premium 中的分页报表和有关报表生成器（用于创作分页报表的独立工具）的许多常见问题。 需要具有 Power BI Pro 许可证才能将报表发布到服务。 只要工作区处于 Power BI 高级容量中，就可以在“我的工作区”或应用工作区中发布和共享分页报表。 

## <a name="administration"></a>管理

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>用于分页报表的的高级容量的大小是多少？

分页报表工作负载在公共预览版的 P1 – P3 SKU 上可用。  你还可以在 A4 – A6 SKU 中将其用于测试/开发应用场景。

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>可以在我的容量中为分页报表保留的最大内存阈值是多少？

当前，仅能为此工作负载保留 50% 的内存。 

### <a name="how-does-user-access-work-for-paginated-reports"></a>用户如何访问分页报表中的工作？

用户访问分页报表的方法与用户访问 Power BI 服务中的所有其他内容相同 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>我如何打开/关闭我的分页报表工作负载？

容量管理员可以在容量管理门户页面启用或禁用分页报表工作负载。  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>我如何在我的租户中监视分页报表的使用？

Office 365 审核日志在以下事件下详细记录此报表类型的使用情况： 

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

目前还不行。 我们将在公共预览版中提供监视功能，作为现有报表中的新选项卡，它具有与 Power BI 数据集中相同的相关详细信息。

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>我是否需要具有 Pro 许可证才能创建和发布分页报表？

是。 在没有 Pro 许可证的情况下，你将无法将报表上传到工作区。 你可以在没有 Pro 许可证的情况下下载和试用报表生成器，但不发布你创建的分页报表。 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>如果我在工作区中有一个分页报表但分页报表工作负载已关闭，该如何处理？

你将收到一条错误消息，且在工作负载重新打开前，你将无法查看你的报表。 你仍然可以从工作区中删除报表。

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>每个高级 SKU 支持的分页报表的默认内存是多少？

每个高级 SKU 支持的分页报表的默认内存为：

- P1/A4：默认为 20%，最低为 10%
- P2/A5：默认为 10%，最低为 5%
- P3/A6：默认为 5%，最低为 2.5%

## <a name="general"></a>常规

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>我如何在分页报表和 Power BI 报表之间选择？

分页报表最适合于要求针对打印或 PDF 生成进行优化的高度格式化且像素效果完美的输出的应用场景。  例如，损益表就是你想要创建为分页报表的报表类型示例。  

Power BI 报表针对浏览和交互性进行了优化。  例如，对于销售报表（其中不同的销售人员想要在同一区域针对其特定区域/行业/客户切分数据并查看数字的变化情况），Power BI 报表将是最理想的选择。

### <a name="the-documentation-says-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>文档中提到报表生成器是首选创作工具。 我可以在适用于 Power BI 的 SQL Server Data Tools 中创建分页报表吗？

可以，但 Power BI 服务仅允许你一次上传一个项目，因此，作者使用 SQL Server Data Tools (SSDT) 的许多应用场景尚未受支持。 在此常见问题解答中查看以后提供的完整的[不受支持的功能的列表](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)。  

### <a name="what-versions-of-report-builder-do-you-support"></a>支持哪些报表生成器版本？

使用最新版本的 SQL Server 2016 报表生成器来创作你的报表并将其发布到 Power BI 服务。 安装 [Microsoft 下载中心的报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)。

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>我如何将保存在 SQL Server Reporting Services 中的报表移动到 Power BI？

你需要从服务器下载报表，然后通过门户将其上传到 Power BI。  目前还没有可供使用的迁移工具，但我们正计划在完成公共预览版并在两种产品之间实现相应的一致性后创建一个迁移工具。

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>我可以打开报表并直接发布到服务吗？

目前还不行。 我们将在某个时间点添加对打开报表并将其从报表生成器直接发布到服务的支持，就像你在 Power BI Desktop 中实现的功能那样。

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Power BI 中有哪些在 SSRS 中尚不支持的分页报表功能？

目前，分页报表不支持以下项：

- 共享数据源
- 共享的数据集
- 子报表
- 单击和钻取操作
- 链接报表
- 书签
- 必应地图层
- 自定义字体
- 隐藏参数

尚不支持切换和交互式排序，但预计不久就会推出这些功能。    

如果你尝试上传具有在 Power BI 服务中不受支持的功能的文件，则将收到一条错误消息，而不是切换/排序。

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>分页报表当前支持的数据源有哪些？

我们支持 Azure SQL 数据库以及使用本地网关的 SQL Server 和 SQL Server Analysis Services (SSAS) 表格模型。 我们当前不支持 SSAS 多维 (MDX) 模型。

通过网关访问 SSAS 时，存储凭据的用户需要 SSAS 中提升的权限才能通过网关。

### <a name="what-authentication-methods-do-you-support"></a>支持的身份验证方法有哪些？

当前，需要在门户或网关中存储含有数据源的用户名和密码。  支持行级别安全性等其他身份验证方法将在预览版中推出。

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>我可以将 Power BI 数据集用作我的分页报表的数据源吗？

目前还不行，但我们很快会计划推出此功能。

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>我可以在通过网关时使用存储的过程吗？

你可以在通过网关时使用存储过程，但如果存储的过程含有参数，则无法执行此操作。

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Power BI 服务中针对我的报表提供的导出格式有哪些？

可以导出为 Microsoft Excel、Microsoft Word、Microsoft PowerPoint、PDF、.CSV、XML 和 MHTML。

### <a name="can-i-print-paginated-reports"></a>我可以打印分页报表吗？

目前可以导出为 PDF 并打印文件。 将很快推出从分页报表直接打印的功能。 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>分页报表目前提供电子邮件订阅吗？

不，将在以后提供电子邮件订阅。

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>Power BI 服务中会支持 SSRS 中的哪些功能？

我们的计划是尽可能提供这两种产品之间的功能的互通性。  尝试更改有关 SSRS 和 Power BI 的某些事项以适应现有 SSRS 模式可能没有太大意义，例如 Power BI 中不同的权限模型，但我们会了解来自客户和合作伙伴的反馈，以做出此类决策。

### <a name="can-i-run-custom-code-in-my-report"></a>我可以在我的报表中运行自定义代码吗？

可以，支持在你的报表中运行代码，这与在 SSRS 中一样。

### <a name="does-this-mean-ssrs-is-going-away"></a>这是否意味着 SSRS 将被弃用？

完全不会。  这一新的产品/服务为客户提供了针对其分页报表的基于云的选项。  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>我可以使用 Power BI Embedded 将我的分页报表嵌入到我正在管理的应用中吗？

我们计划在现有的 Power BI API 中支持此方案，但我们尚不确定何时推出此方案。

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>我是否可以从 Power BI 报表钻取到分页报表？

目前还不行，但我们一定会计划支持此方案。

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>我可以通过 Power BI 应用共享我的分页报表内容吗？

目前，你可以通过门户中的共享操作将个人的分页报表与其他用户共享。 我们尚不支持在应用中共享，但计划很快推出此功能。 我们也将在工具栏中设置共享按钮。

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Power BI 中的其他特定于报表的功能（例如，将报表磁贴固定到仪表板）也适用于分页报表吗？

我们计划尽可能让报表在服务中支持相同的主要方案。  理想情况下，尽管创作它们的工具不同，但从使用者的角度来看，它只是门户中其列表中的另一个报表。 他们并不关心它是如何创建的，只要他们能够完成他们需要的操作即可。  此功能奇偶一致性的一个很好的示例是计划的注释支持。 尽管功能本身针对每种报表类型的工作方式略有不同，但你可以为两者使用注释。

### <a name="are-you-planning-to-create-a-new-authoring-tool-for-paginated-reports-in-the-power-bi-service--we-cant-do-everything-we-need-to-with-report-builder-today"></a>你是否计划在 Power BI 服务中为分页报表创建一个新的创作工具？  我们现在还不能使用报表生成器实现所有功能。

我们仍在探索各种不同的理想工具，但请放心，我们将提供对各功能的支持，例如 ALM、自定义扩展等功能，以及可能仅在 SSRS 的其中一个创作工具中包含的其他功能。 

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>是否计划了迁移工具以便 SSRS 客户可以将其现有报表和资产移动到 Power BI？

是，但我们将在 Power BI 服务中的一组核心的支持的功能完成后计划此迁移工具。

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>我可以在单个创作工具中同时创建分页报表和 Power BI 报表吗？

我们当前还没有计划单个创作工具，但我们正在探索方法，以将创作工具一起分发为单个 BI 套件或具有单独下载/品牌打造。

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Power BI 服务中是否有针对分页报表的报表查看器控件？

没有，报表查看器控件尚不可用。

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>可以在 Power BI 服务中的新主页体验中搜索分页报表吗？

不可以，目前还不能从主页搜索分页报表。  但可以在新主页体验的其他部分看到它们。

## <a name="next-steps"></a>后续步骤

- [安装 Microsoft 下载中心的报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)
- [教程：创建分页报表](paginated-reports-quickstart-aw.md)
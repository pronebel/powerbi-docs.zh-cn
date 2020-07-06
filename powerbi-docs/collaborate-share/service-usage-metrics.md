---
title: 监视仪表板和报表的使用情况指标
description: 如何查看、保存和使用 Power BI 仪表板和报表的使用情况指标。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/21/2019
LocalizationGroup: Dashboards
ms.openlocfilehash: b5f4d615c04583e59b618b415c8c239c9295c8a8
ms.sourcegitcommit: 0b1e96de184caf2371adedcc3ee43bcb88048187
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85299586"
---
# <a name="monitor-usage-metrics-for-power-bi-dashboards-and-reports"></a>监视 Power BI 仪表板和报表的使用情况指标

如果你创建仪表板和报表，使用指标可帮助你了解它们的影响。 运行仪表板使用指标或报表使用指标时，可查看整个组织使用这些仪表板和报表的情况 - 使用人员以及使用目的。  

使用指标报表是只读的。 但是，可以复制使用指标报表。 复制会创建可编辑的标准 Power BI 报表。 此外还可以在 Power BI Desktop 中基于基础数据集生成自己的报表，其中包含工作区中所有仪表板或所有报表的使用指标。 一开始，复制的报表仅显示所选仪表板或报表的指标。 可以删除默认筛选器，并且有权访问包含所选工作区的所有使用指标的基础数据集。 甚至可以看到特定用户的名称（如果管理员允许）。

![使用情况指标报表](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

> [!NOTE]
> 使用情况指标跟踪 SharePoint Online 中嵌入的报表的使用情况。 但是，使用指标不会跟踪通过“用户拥有凭据”或“应用拥有凭据”流嵌入的仪表板和报表。 使用指标也不会跟踪通过[发布到 Web](service-publish-to-web.md) 嵌入的报表的使用情况。

## <a name="why-usage-metrics-are-important"></a>使用指标为何如此重要

了解内容的使用方式有助于说明影响，并划分工作的优先级。 使用指标可能会显示组织的大部分部门每天会使用其中一个报表，还可能会显示根本没人查看你创建的某个仪表板。 这种类型的反馈在指导工作方面极其重要。

只能在 Power BI 服务中运行使用指标报表。 但是，如果保存使用情况指标报表或将其固定到仪表板，则可在移动设备上打开该报表并与其交互。

## <a name="prerequisites"></a>先决条件

- 需要有 Power BI Pro 许可证才能运行和访问使用指标数据。 但是，使用指标功能可捕获所有用户的使用情况信息，无论用户分配的许可证为何。
- 要访问特定仪表板或报表的使用指标，必须有权访问编辑相应的仪表板或报表。
- Power BI 管理员必须已启用内容创建者的使用指标。 Power BI 管理员可能还支持收集使用指标中的每个用户数据。 了解如何[在管理门户中启用这些选项](../admin/service-admin-portal.md#control-usage-metrics)。 

## <a name="view-a-usage-metrics-report"></a>查看使用情况指标报表

1. 首先，转到包含仪表板或报表的工作区。
2. 在“工作区”内容列表或仪表板/报表本身中，选择“使用情况指标”图标 ![使用情况指标](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png)。

    ![“仪表板”选项卡](media/service-usage-metrics/power-bi-run-usage-metrics-report.png)

    ![选择使用情况指标](media/service-usage-metrics/power-bi-run-usage-metrics-report2.png)
3. 首次执行此操作时，Power BI 会创建使用情况指标报表，并在创建完成后通知你。

    ![指标已准备就绪](media/service-usage-metrics/power-bi-usage-metrics-ready.png)
4. 要查看结果，请选择“查看使用指标”。

    在部署或维护 Power BI 仪表板和报表时，使用情况指标是非常有用的帮手。 想知道报表的哪些页面最有用，哪些页面应该逐渐淘汰？ 按“报表页”进行切片，即可找到答案。想知道是否应为仪表板生成移动布局？ 按“平台”进行切片，了解通过移动应用与通过 Web 浏览器访问内容的用户数。

5. （可选）将鼠标悬停在可视化效果之上，再选择“固定”图标，将可视化效果添加到仪表板。 也可以选择顶部菜单栏中的“固定活动页面”，将整个页面添加到仪表板。 在仪表板中，可以更轻松地监视使用指标，或将它们与其他人共享。

    > [!NOTE]
    > 如果将使用指标报表中的磁贴固定到仪表板，则无法将该仪表板添加到应用。

### <a name="dashboard-usage-metrics-report"></a>仪表板使用情况指标报表

![仪表板使用情况指标报表](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

### <a name="report-usage-metrics-report"></a>报表使用情况指标报表

![报表使用情况指标报表](media/service-usage-metrics/power-bi-report-usage-metrics-update.png)

## <a name="about-the-usage-metrics-report"></a>关于使用情况指标报表

选择“使用指标”或仪表板或报表旁边的图标![使用指标图标](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png)时，Power BI 会生成一个预生成报表，其中包含相应内容在过去 90 天内的使用指标。  此报表看起来与你已经熟悉的 Power BI 报表非常类似。 基于最终用户接收访问权限的方式以及他们是通过 Web 还是移动应用等方式访问，可以进行切片。仪表板和报表发生更改时，使用情况指标报表也会随之更改（使用情况指标报表每天更新新数据）。  

使用指标报表不会显示在“最新动态”、“工作区”、“收藏夹”或其他内容列表中  。 不能将使用指标报表添加到应用。 如果将使用指标报表中的磁贴固定到仪表板，则无法将该仪表板添加到应用。

若要深入了解报表数据，或基于基础数据集生成自己的报表，有以下两个选项： 

- 在 Power BI 服务中创建报表的副本。 有关详细信息，请参阅本文稍后介绍的[保存使用指标报表的副本](#save-a-copy-of-the-usage-metrics-report)。
- 从 Power BI Desktop 连接到数据集。 每个工作区的数据集都具有“报表使用指标模型”这一名称。 有关详细信息，请参阅[建立与已发布数据集的连接](../connect-data/desktop-report-lifecycle-datasets.md#establish-a-power-bi-service-live-connection-to-the-published-dataset)。

    ![连接到使用情况报表数据集](media/service-usage-metrics/power-bi-usage-dataset.png)

## <a name="which-metrics-are-reported"></a>报表中包含哪些指标？

| 指标 | 仪表板 | 报表 | 说明 |
| --- | --- | --- | --- |
| 分发方法切片器 |是 |是 |用户获取内容访问权限的方式。 用户访问仪表板或报表的方式可能有以下 3 种：成为[工作区](../consumer/end-user-experience.md)的成员、将内容[与他们共享](service-share-dashboards.md)或安装内容包/应用。  请注意，通过应用的查看数被视为“内容包”。 |
| 平台切片器 |是 |是 |是通过 Power BI 服务 (powerbi.com)，还是通过移动设备访问仪表板或报表？ 移动应用包括所有 iOS、Android 和 Windows 应用。 |
| 报表页切片器 |否 |是 |如果报表有多页，按已查看的一个或多个报表页对报表进行切片。 如果看到列表选项为“空白”，这意味着报表页为最近添加（新页的实际名称会在 24 小时内显示在切片器列表中），并且/或者报表页已删除。 “空白”可捕获此类情况。 |
| 每日查看次数 |是 |是 |每日总查看次数 - 查看的定义为用户加载报表页或仪表板。 |
| 每日的唯一身份查看者 |是 |是 |查看了仪表板或报表的唯一身份用户数（以 AAD 用户帐户为依据）。 |
| 每用户查看次数 |是 |是 |过去 90 天内的查看次数，按各用户细分。 |
| 每日共享次数 |是 |否 |仪表板与其他用户或组进行共享的次数。 |
| 总查看次数 |是 |是 |过去 90 天内的查看次数。 |
| 查看者总数 |是 |是 |过去 90 天内的唯一身份查看者人数。 |
| 总共享次数 |是 |否 |仪表板或报表在过去 90 天内的共享次数。 |
| 组织中的总数 |是 |是 |最近 90 天里整个组织中至少被查看过一次的所有仪表板或报表的计数。  用于计算级别。 |
| 排名：总查看次数 |是 |是 |根据过去 90 天内组织中所有仪表板或报表的总查看次数，确定此仪表板或报表的级别。 |
| 排名：总共享次数 |是 |否 |根据过去 90 天内组织中所有仪表板的总共享次数，确定此仪表板或报表的级别。 |

## <a name="save-a-copy-of-the-usage-metrics-report"></a>保存使用指标报表的副本

使用“另存为”将使用指标报表转换为可进行自定义以满足特定需求的常规 Power BI 报表。 还可以使用 Power BI Desktop 基于基础数据集生成自定义使用指标报表。 有关详细信息，请参阅[建立与已发布数据集的连接](../connect-data/desktop-report-lifecycle-datasets.md#establish-a-power-bi-service-live-connection-to-the-published-dataset)。

更好的一点是，基础数据集包含工作区中所有仪表板或报表的使用情况详细信息。 这带来更多可能性。 例如，可以创建基于使用情况对工作区中的所有仪表板进行对比的报表。 或者，通过聚合 Power BI 应用中所有分发内容的使用情况，为此应用创建使用指标仪表板。  请参阅后文中介绍的如何删除筛选器以及[查看工作区中的所有使用指标](#see-all-workspace-usage-metrics)。

### <a name="create-a-copy-of-the-usage-report"></a>创建使用情况报表的副本

创建预生成的只读使用情况报表的副本时，Power BI 将创建可编辑的报表副本。 从表面看，报表看上去相同。 但是，现在能在编辑视图中打开报表，添加新的可视化效果、筛选器和页面，以及修改或删除现有可视化效果等。 Power BI 将新报表保存到当前工作区中。

1. 在预生成的使用情况指标报表中，依次选择“文件”>“另存为”。 Power BI 将创建可编辑的 Power BI 报表，并保存到当前工作区中。

    ![另存为](media/service-usage-metrics/power-bi-save-as.png)
2. 在编辑视图中打开报表，[与报表进行交互，就像与其他任何 Power BI 报表进行交互一样](../create-reports/service-interact-with-a-report-in-editing-view.md)。 例如，添加新页面和生成新的可视化效果、添加筛选器、设置字体和颜色等。

    ![在“编辑”视图中打开报表](media/service-usage-metrics/power-vi-editing-view.png)
3. 新建的报表会保存到当前工作区的“报表”选项卡中，还会添加到“最新动态”内容列表中。

    ![“报表”选项卡](media/service-usage-metrics/power-bi-new-report.png)

## <a name="see-all-workspace-usage-metrics"></a>查看所有工作区使用指标

若要查看工作区中所有仪表板或所有报表的指标，必须删除筛选器。 默认情况下，报表会进行筛选，仅显示用于创建它的仪表板或报表的指标。

1. 选择“编辑报表”在“编辑”视图中打开可编辑的新报表。

    ![选择“编辑”报表](media/service-usage-metrics/power-bi-editing-view.png)
2. 在“筛选器”窗格中，找到“报表级别筛选器”桶，然后选择 ReportGuid 旁边的橡皮擦将筛选器删除 。

    ![删除筛选器](media/service-usage-metrics/power-bi-usage-report-clear-filter.png)

    现在报表将显示整个工作区的指标。

## <a name="power-bi-admin-controls-for-usage-metrics"></a>Power BI 管理员对使用指标的控制

使用指标报表是全局管理员或 Power BI 管理员可以启用或禁用的一项功能。 管理员可以精确控制哪些用户可以访问使用指标；默认情况下，对于组织中的所有用户，它们都处于“启用”状态。

> [!NOTE]
> 只有 Power BI 租户的管理员才能看到管理门户和编辑设置。 

默认情况下，每个用户的数据都启用了使用指标并在指标报表中包含内容使用者帐户信息。 如果管理员不希望某些或所有用户公开此信息，则可以为特定安全组或整个组织禁用此功能。 帐户信息随后会在报表中显示为“未命名”。

当禁用其整个组织的使用指标时，管理员可以使用“删除所有现有的使用指标内容”选项删除通过使用指标报表和数据集构建的所有现有报表和仪表板磁贴。 此选项可以删除组织中可能已在使用的所有用户对使用指标数据的所有访问内容。 删除现有的使用指标内容是不可逆转的操作。

有关这些设置的详细信息，请参阅“管理门户”一文中的[控制使用指标](../admin/service-admin-portal.md#control-usage-metrics)。 

## <a name="usage-metrics-in-national-clouds"></a>国家云中的使用情况指标

Power BI 在单独的国家云中可用。 这些云提供与全球版本 Power BI 相同级别的安全性、隐私、合规性和透明度，并结合了有关服务交付、数据驻留、访问和控制的本地法规的唯一模式。 由于本地法规的这种唯一模式，使用指标不适用于国家/地区云。 有关详细信息，请参阅[国家云](https://powerbi.microsoft.com/clouds/)。

## <a name="considerations-and-limitations"></a>注意事项和限制

### <a name="discrepancies-between-audit-logs-and-usage-metrics"></a>审核日志与使用指标间的差异

在比较使用指标和审核日志时，可能会出现差异，了解这一点及其原因很重要。 审核日志是使用 Power BI 服务中的数据收集的，而使用指标是在客户端上收集的。 审核日志中的活动聚合计数可能并非总是匹配使用指标，原因如下：

* 由于网络连接不一致、广告拦截器或可能中断从客户端发送事件的其他问题，使用指标有时可能少计算活动数。
* 某些类型的视图未包含在使用指标中，如本文中所述。
* 对于客户端刷新而无需发送回 Power BI 服务的请求的情况，使用指标有时可能多计算活动数。
* 已为使用情况指标报表禁用共享。 若要向用户授予对报表的读取访问权限，你需要先向他们授予对工作区的访问权限。

### <a name="other-considerations"></a>其他注意事项

你至少需要在工作区中查看该工作区中的内容一次。 如果工作区本身至少有一次没有内容视图，则不会从使用指标报表中的应用程序视图中关联数据。 要取消阻止对此报告的数据处理，只需至少查看一次工作区中的内容。


## <a name="frequently-asked-questions"></a>常见问题解答

除了使用指标和审核日志之间的潜在差异以外，有关使用指标的以下问题和解答还可能对用户和管理员有所帮助：

**问：**  我无法在仪表板或报表上运行使用情况指标

**答：**  你只能看到自己拥有或有权编辑的内容的使用情况指标。

**问：**  使用情况指标是否从嵌入的仪表板和报表中捕获视图？

**答：**  使用指标目前不支持捕获嵌入的仪表板、报表和[发布到 Web](service-publish-to-web.md) 流的使用情况。 在这些情况下，我们建议使用现有的 Web 分析平台来跟踪托管应用或门户的使用情况。

**问：**  我根本无法对任何内容生成使用情况指标。

**答 1：**  管理员可以为组织关闭此功能。  请联系管理员以确定是否属于这种情况。

**答 2：**  使用指标是 Power BI Pro 的一项功能。

**问：**  数据好像不是最新的。 例如，没有显示分发方法、缺少报表页等。

**答：**  数据更新最长可能需要 24 小时才能完成。

**问：**  工作区中有 4 个报表，但使用情况指标报表只显示 3 个。

**答：**  使用情况指标报表仅包括在过去 90 天内访问过的报表（或仪表板）。  如果不显示某个报表（或仪表板），很可能此报表已超过 90 天未被使用。

## <a name="next-steps"></a>后续步骤

[在管理门户中管理 Power BI](../admin/service-admin-portal.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

---
title: Power BI 管理门户
description: 通过管理门户允许对组织中的 Power BI 进行租户管理。 它包括诸如使用情况指标、对 Microsoft 365 管理中心的访问以及设置这类项目。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/12/2020
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 460ab380798975065eb90bf904b2b5bacd1edd2c
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315962"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>在管理门户中管理 Power BI

借助管理门户，用户可以管理组织中的 Power BI 租户。 门户包括诸如使用情况指标、对 Microsoft 365 管理中心的访问以及设置这类项目。

所有全局管理员或分配有 Power BI 服务管理员角色的所有用户都可以访问完整的管理门户。 如果你不是这些角色之一，则只能在门户中看到“容量设置”。 若要详细了解 Power BI 服务管理员角色，请参阅[了解 Power BI 管理员角色](service-admin-role.md)。

## <a name="how-to-get-to-the-admin-portal"></a>如何访问管理门户

帐户必须标记为 Microsoft 365 或 Azure Active Directory (Azure AD) 中的全局管理员，或者已分配 Power BI 服务管理员角色，才能获取对 Power BI 管理门户的访问权限。 若要详细了解 Power BI 服务管理员角色，请参阅[了解 Power BI 管理员角色](service-admin-role.md)。 若要访问 Power BI 管理门户，请执行以下操作。

1. 在 Power BI 服务右上角选择设置齿轮。

1. 选择“管理门户”。

    ![管理门户的设置](media/service-admin-portal/powerbi-admin-settings.png)

门户中有九个选项卡。 本文的其余部分提供了有关每个选项卡的信息。

![管理门户导航](media/service-admin-portal/powerbi-admin-landing-page.png)

* [使用情况指标](#usage-metrics)
* [用户](#users)
* [审核日志](#audit-logs)
* [租户设置](#tenant-settings)
* [容量设置](#capacity-settings)
* [嵌入代码](#embed-codes)
* [组织视觉对象](#organizational-visuals)
* [数据流存储（预览版）](#dataflowStorage)
* [工作区](#workspaces)
* [自定义品牌](#custom-branding)

## <a name="usage-metrics"></a>使用情况指标

通过“使用情况指标”，你可以监视组织的使用情况。 通过它还可以查看对于组织，哪些用户和组在 Power BI 中最活跃。 

> [!NOTE]
> 首次访问仪表板时，或在长时间未查看仪表板后再次进行访问之后，你可能会在我们加载仪表板时看到加载屏幕。

仪表板加载之后，你会看到两个部分的磁贴。 第一个部分包含单个用户的使用情况数据，第二个部分包含有关组织中的组的类似信息。

下面是每个磁贴中显示的内容的细分：

* 用户工作区中的所有仪表板、报表和数据集的非重复计数。
  
    ![仪表板、报表和数据集的非重复计数](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* 按可以进行访问的用户数划分的使用量最大的仪表板。 例如，如果你将 1 个仪表板与 3 个用户共享，并且还将它添加到 2 个不同用户连接到的内容包，计数为 6 (1 + 3 + 2)。
  
    ![使用最多的仪表板](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* 用户连接到的最受欢迎内容。 这是用户可以通过“获取数据”过程访问的任何内容，如 SaaS 内容包、组织内容包、文件或数据库。
  
    ![使用最多的包](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* 基于用户具有的仪表板数（他们自己创建的仪表板以及与他们共享的仪表板）的排名靠前用户视图。
  
    ![主要用户 - 仪表板](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* 排名靠前的用户视图（以用户拥有的报表数为依据）。
  
    ![主要用户 - 报表](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

第二个部分显示相同类型的信息，不过是基于组。 这样，就可以查看组织中最活跃的组以及它们所使用的内容种类。

借助此信息，你可以真正地深入了解用户在组织中如何使用 Power BI，并能够识别在组织中非常活跃的用户和组。

## <a name="control-usage-metrics"></a>控制使用指标

使用指标报表是 Power BI 或全局管理员可以启用或禁用的一项功能。 管理员可以对哪些用户有权访问使用指标进行精细控制。 对于组织中的所有用户，默认情况下处于“打开”状态。

管理员还可以确定内容创建者是否可以查看使用指标中的每个用户数据。 

有关报表本身的详细信息，请参阅[监视 Power BI 仪表板和报表的使用指标](../collaborate-share/service-usage-metrics.md)。

### <a name="usage-metrics-for-content-creators"></a>内容创建者的使用指标

1. 在“管理门户”中，选择“租户设置” > “内容创建者的使用指标”。

    ![管理门户租户设置使用指标](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. 启用（或禁用）使用指标 >“应用”。

    ![已启用使用情况指标](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)


### <a name="per-user-data-in-usage-metrics"></a>使用指标中的每个用户数据

默认情况下，每个用户的数据都启用了使用指标并在指标报表中包含内容使用者帐户信息。 如果不希望某些或所有用户包含此信息，请为特定安全组或整个组织禁用此功能。 帐户信息随后会在报表中显示为“未命名”。

![每个用户使用数据](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>删除所有现有的使用指标内容

当禁用整个组织的使用指标时，管理员还可以选择以下一个或两个选项：

- **删除所有现有的使用指标内容**，可删除通过使用指标报表和数据集构建的所有现有报表和仪表板磁贴。 此选项可以删除组织中可能已在使用的所有用户对使用指标数据的所有访问内容。 
- **删除当前使用指标内容中的所有现有每个用户数据** 此选项可以删除组织中可能已在使用的所有用户对使用指标数据的所有访问内容。 

请谨慎操作，因为删除现有的使用指标内容和每个用户指标内容是不可逆转的操作。

## <a name="users"></a>用户

可以在 Microsoft 365 管理中心中管理 Power BI 用户、组和管理员。 “用户”选项卡为租户提供指向管理中心的链接。

![转到 Microsoft 365 管理中心](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>审核日志

可以在 Office 365 安全与合规中心中管理 Power BI 审核日志。 “审核日志”选项卡为租户提供指向安全与合规中心的链接。 [了解详细信息](service-admin-auditing.md)

若要使用审核日志，请确保[**创建内部活动审核和合规性的审核日志**](#create-audit-logs-for-internal-activity-auditing-and-compliance)设置已启用。

## <a name="tenant-settings"></a>租户设置

“租户设置”选项卡可以对组织可用的功能进行细粒度控制。 如果你担心敏感数据、我们的某些功能可能不适合你的组织，或者你只需要为特定组提供特定的功能。

> [!NOTE]
> 控制 Power BI 用户界面中功能可用性的租户设置可帮助建立治理策略，但它们并不是一种安全措施。 例如，“导出数据”设置不会限制 Power BI 用户对数据集的权限。 对数据集具有读取访问权限的 Power BI 用户具有查询此数据集的权限，并且可以在不使用 Power BI 用户界面“导出数据”功能的情况下保留结果。

下图显示了“租户设置”选项卡上的几个设置。

![租户设置](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> 可能需要 10 分钟才会使设置更改对租户中的每个人生效。

设置可以有三种状态：

* **已为整个组织禁用**：组织中无人可以使用此功能。

    ![禁用所有设置](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **已为整个组织启用**：组织中每个人均可以使用此功能。

    ![启用所有设置](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **针对组织的子集启用**：组织中特定子集的用户或组可以使用此功能。

    可以为除特定用户组之外的整个组织启用此功能。

    ![启用子集设置](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    还可以仅为特定用户组启用功能，也可以为某个用户组禁用功能。 使用此方法确保即使某些用户属于允许的组，但仍没有访问该功能的权限。

    ![启用除外设置](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

接下来的几节概述了不同类型的租户设置。

## <a name="help-and-support-settings"></a>帮助和支持设置

### <a name="publish-get-help-information"></a>发布“获取帮助”信息

组织中的用户可以通过 Power BI 帮助菜单获取内部帮助和支持资源。 具体而言，这些参数更改“Learn”、“社区”和“获取帮助”菜单项的行为。

此外，通过指定授权请求的 URL，可以自定义“升级帐户”按钮的目标 URL。 没有 Power BI Pro 许可证的用户将在“更新到 Power BI Pro”对话框和“管理个人存储”页中看到此按钮 。 此外，Power BI 不再提供此对话框或存储页中的“免费试用 Pro”按钮。 这可确保 Power BI 通过许可证管理解决方案可靠地引导用户完成在组织中定义的流程。

![启用除外设置](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>接收与服务故障或突发事件相关的电子邮件通知

如果此租户受到服务中断或突发事件的影响，已启用邮件的安全组将收到电子邮件通知。 了解有关[服务中断通知](service-interruption-notifications.md)的详细信息。

## <a name="workspace-settings"></a>工作区设置

在“租户设置”中，管理门户有两部分用于控制工作区：

- 创建新的工作区体验。
- 跨工作区使用数据集。

### <a name="create-the-new-workspaces"></a>创建新工作区

工作区是用户可在仪表板、报表和其他内容上开展协作的地方。 管理员使用“创建工作区(新工作区体验)”设置，指明组织中的哪些用户可以创建工作区。 管理员可以允许组织中的每个人都可以创建新工作区体验的工作区，也可以不允许任何人进行创建。 管理员还可以限制特定安全组的成员进行创建。 详细了解[工作区](../collaborate-share/service-new-workspaces.md)。

:::image type="content" source="media/service-admin-portal/power-bi-admin-workspace-settings.png" alt-text="创建新的工作区体验":::

对于基于 Microsoft 365 组的经典工作区，管理工作继续在管理门户和 Azure Active Directory 中进行。

> [!NOTE]
> “创建工作区(新工作区体验)”设置默认为：仅允许能够创建 Microsoft 365 组的用户创建新的 Power BI 工作区。 请务必在 Power BI 管理门户中设置值，以确保相应用户能够创建它们。

工作区列表

管理门户还有另一个设置部分是关于租户中的工作区。 在此部分中，可以对工作区列表进行排序和筛选，并显示每个工作区的详细信息。 有关详细信息，请参阅本文中的[工作区](#workspaces)。

发布内容包和应用

在管理门户中，还可以控制哪些用户有权将应用分发给组织。 有关详细信息，请参阅本文中的[向整个组织发布内容包和应用](#publish-content-packs-and-apps-to-the-entire-organization)。

### <a name="use-datasets-across-workspaces"></a>跨工作区使用数据集

管理员可以控制组织中的哪些用户可以跨工作区使用数据集。 如果启用此设置，则用户仍然需要具有特定数据集的必需生成权限。

:::image type="content" source="media/service-admin-portal/power-bi-admin-datasets-workspaces.png" alt-text="跨工作区使用数据集":::

有关详细信息，请参阅[跨工作区使用数据集简介](../connect-data/service-datasets-across-workspaces.md)。


## <a name="export-and-sharing-settings"></a>导出和共享设置

### <a name="share-content-with-external-users"></a>与外部用户共享内容

组织中的用户可以与组织外部的用户共享仪表板、报表和应用。 详细了解[外部共享](../collaborate-share/service-share-dashboards.md#share-a-dashboard-or-report-outside-your-organization)。

![外部用户设置](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

下图显示了与外部用户共享时会显示的消息。

![与外部用户共享](media/service-admin-portal/powerbi-admin-sharing-external.png)  

> [!IMPORTANT]
> 此选项控制 Power BI 中的用户是否可以通过 Power BI 邀请外部用户成为组织的 Azure Active Directory B2B (Azure AD B2B) 来宾用户。 启用后，在共享报表、仪表板和 Power BI 应用时，具有 Azure AD 来宾邀请者角色的用户可以添加外部电子邮件地址。 将邀请外部收件人作为 Azure AD B2B 来宾用户加入组织。 重要的是，如果禁用此设置，Power BI 的人员选取器 UI 继续显示已是组织的 Azure AD B2B 来宾用户的外部用户，并且可以向他们提供项目、工作区和应用的访问权限。

### <a name="publish-to-web"></a>发布到 Web

作为 Power BI 租户的管理员，“发布到 Web”设置提供了用户可以为其创建嵌入代码以将报表发布到 Web 的选项。 此功能使报表及其数据可供 Web 上的任何用户使用。 详细了解如何[发布到 Web](../collaborate-share/service-publish-to-web.md)。

> [!NOTE]
> 只有 Power BI 管理员才能允许创建新的“发布到 Web”嵌入代码。 组织可能具有现有嵌入代码。 请参阅管理门户的[嵌入代码](service-admin-portal.md#embed-codes)部分，以查看当前发布的报表。

下图显示了启用“发布到 Web”设置时报表的“更多选项 (...)”菜单。

![“更多选项”菜单中的“发布到 Web”](media/service-admin-portal/power-bi-more-options-publish-web.png)

管理门户中的“发布到 Web”设置提供了用户可以为其创建嵌入代码的选项。

![发布到 Web 设置](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

管理员可以将“发布到 Web”设置为“已启用”，并将“选择嵌入代码的工作方式”设置为“仅允许现有嵌入代码”。 在这种情况下，用户可以创建嵌入代码，但必须与 Power BI 管理员联系以允许他们这样做。

![发布到 Web 提示符](../collaborate-share/media/service-publish-to-web/publish_to_web_admin_prompt.png)

根据“发布到 Web”设置的内容，用户会在 UI 中看到不同的选项。

|功能 |为整个组织启用 |为整个组织禁用 |特定安全组   |
|---------|---------|---------|---------|
|报表“更多选项 (...)”菜单下的“发布到 Web” |为所有对象启用|向所有对象隐藏|仅向已授权的用户或组显示。|
|“设置”下的“管理嵌入代码” |为所有对象启用|为所有对象启用|为所有对象启用<br><br>仅向已授权的用户或组显示“删除”选项。* <br>为所有对象启用“获取代码”。* |
|管理门户中的“嵌入代码”|“状态”反映以下状态之一：<br>* 活动<br>* 不支持<br>* 已阻止|状态显示“已禁用”|“状态”反映以下状态之一：<br>* 活动<br>* 不支持<br>* 已阻止<br><br>如果未根据租户设置为某个用户授权，状态将显示为“侵权”。|
|现有的已发布报表|全部已启用|全部已禁用|继续向所有对象呈现报表。|

### <a name="export-data"></a>导出数据

组织中的用户可以从磁贴或可视化效果导出数据。 这会控制 Excel 中的“分析”、“导出到 .csv”、数据集下载 (.pbix) 和 Power BI 服务 Live Connect 功能。 详细了解如何[从磁贴或视觉对象导出数据](../visuals/power-bi-visualization-export-data.md)。

>[!NOTE]
> 在引入“导出至 Excel”设置之前，此设置还控制了将数据导出到 Excel 文件的操作。 有关详细信息，请参阅 [“导出至 Excel”下的注释](#export-to-excel)。

![导出数据设置](media/service-admin-portal/powerbi-admin-portal-export-data-setting.png)

下图显示了从磁贴导出数据的选项。

![从磁贴导出数据](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> 禁用“导出数据”还会阻止用户使用[“在 Excel 中分析”](../collaborate-share/service-analyze-in-excel.md)功能，同时也会阻止用户使用 Power BI 服务实时连接。

### <a name="export-to-excel"></a>导出到 Excel

组织中的用户可将数据从可视化效果导出到 Excel 文件。

![“导出至 Excel”设置](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

>[!IMPORTANT]
> 在引入“导出至 Excel”设置之前，导出到 Excel 文件的操作由“导出数据”设置进行控制。 因此，对于引入“导出至 Excel”设置之前就已存在的租户，在租户管理员首次查看“导出至 Excel”设置时，他们会看到该设置具有未应用的更改。 他们必须应用这些更改才能使新设置生效。 否则，导出到 Excel 文件的操作将继续由“导出数据”设置进行控制。

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>将报表导出为 PowerPoint 演示文稿或 PDF 文档

组织中的用户可以将 Power BI 报表导出为 PowerPoint 文件或 PDF 文档。 [了解详细信息](../consumer/end-user-powerpoint.md)

下图显示了在启用“将报表导出为 PowerPoint 演示文稿或 PDF 文档”设置时报表的“文件”菜单 。

![将报表导出为 PowerPoint 演示文稿](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>打印仪表板和报表

组织中的用户可以打印仪表板和报表。 [了解详细信息](../consumer/end-user-print.md)

下图展示了“打印仪表板”选项。

![打印仪表板](media/service-admin-portal/powerbi-admin-print-dashboard.png)

下图展示了在“打印仪表板和报表”设置已启用时报表的“文件”菜单。

![打印报表](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>允许外部来宾用户编辑和管理组织中的内容

Azure AD B2B 来宾用户可以编辑和管理组织中的内容。 [了解详细信息](service-admin-azure-ad-b2b.md)

下图显示用于允许外部来宾用户编辑和管理组织中内容的选项。

![允许外部来宾用户编辑和管理组织中的内容](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

在管理门户中，还可以控制哪些用户有权邀请外部用户加入组织。 有关详细信息，请参阅本文的[与外部用户共享内容](#export-and-sharing-settings)部分。

### <a name="email-subscriptions"></a>电子邮件订阅
组织中的用户可以创建电子邮件订阅。 详细了解[订阅](../collaborate-share/service-publish-to-web.md)。

![启用电子邮件订阅](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>特别推荐的内容

允许组织中的部分或全部报表作者在 Power BI 主页的“特别推荐”部分中特别推荐其内容。 新用户可在 Power BI 主页的顶部看到特别推荐的内容。 当用户添加“收藏夹”、“最常访问”和“最新动态”时，特别推荐的内容会使“主页”向下移动  。 

我们建议先从少量的推广开始。 允许整个组织在“主页”上特别推荐内容可能会使你难以跟踪所有推广的内容。 

启用特别推荐的内容后，还可以在管理门户中对其进行管理。 请参阅本文中的[管理特别推荐的内容](#manage-featured-content)，了解如何在域中控制特别推荐的内容。

## <a name="content-pack-and-app-settings"></a>内容包和应用设置

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>向整个组织发布内容包和应用

管理员使用此设置，以确定哪些用户可以向整个组织发布内容包和应用，而不仅仅是特定组。 详细了解[如何发布应用](../collaborate-share/service-create-distribute-apps.md)。

下图展示了创建内容包时可用的“我的整个组织”选项。

![向组织发布内容包](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>创建模板应用和组织内容包

组织中的用户可以创建模板应用和组织内容包，它们使用基于 Power BI Desktop 中一个数据源生成的数据集。 详细了解[模板应用](../connect-data/service-template-apps-create.md)。

### <a name="push-apps-to-end-users"></a>将应用推送给最终用户

报表创建者可以直接与最终用户共享应用，而无需从 [AppSource](https://appsource.microsoft.com) 安装。 详细了解[如何自动为最终用户安装应用](../collaborate-share/service-create-distribute-apps.md#automatically-install-apps-for-end-users)。

## <a name="integration-settings"></a>集成设置

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>结合使用“在 Excel 中分析”功能和本地数据集

组织中的用户可以使用 Excel 查看本地 Power BI 数据集，并与其进行交互。 [了解详细信息](../collaborate-share/service-analyze-in-excel.md)

> [!NOTE]
> 禁用“导出数据”还会阻止用户使用“在 Excel 中分析”功能。

### <a name="use-arcgis-maps-for-power-bi"></a>使用 ArcGIS Maps for Power BI

组织中的用户可以使用 Esri 提供的 ArcGIS Maps for Power BI 可视化效果。 [了解详细信息](../visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>使用 Power BI（预览版）的全局搜索

组织中的用户可以使用依赖于 Azure 搜索的的外部搜索功能。

## <a name="featured-tables-settings"></a>精选表设置

在“租户设置”下，“允许连接到精选表”租户设置允许 Power BI 管理员控制组织中的哪些用户可以使用 Excel 数据类型库中的精选表。 

:::image type="content" source="media/service-admin-portal/admin-allow-connections-featured-tables.png" alt-text="与精选表的所有连接":::

如果将“导出数据”租户设置设置为“禁用”，则还会禁用与精选表的连接。

详细了解 [Excel 中的 Power BI 精选表](../collaborate-share/service-excel-featured-tables.md)。

## <a name="power-bi-visuals-settings"></a>Power BI 视觉对象设置

### <a name="add-and-use-power-bi-visuals"></a>添加和使用 Power BI 视觉对象

组织中的用户可以共享 Power BI 视觉对象并与之交互。 [了解详细信息](../developer/visuals/power-bi-custom-visuals.md)

> [!NOTE]
> 此设置可以应用于整个组织，也可以限制为特定组。

Power BI Desktop（2019 年 3 月版及更高版本）支持通过“组策略”禁止在组织部署的计算机上使用 Power BI 视觉对象。

<table>
<tr><th>属性</th><th>值</th>
</tr>
<td>键</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>值名称</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

十进制值 1 允许在 Power BI 中使用 Power BI 视觉对象（这是默认值）。

十进制值 0 禁止在 Power BI 中使用 Power BI 视觉对象。

### <a name="allow-only-certified-visuals"></a>仅允许已认证的视觉对象

组织中已获得添加和使用 Power BI 视觉对象权限的用户（由“添加和使用 Power BI 视觉对象”设置表示）只能使用[认证的 Power BI 视觉对象](https://go.microsoft.com/fwlink/?linkid=2002010)（未经认证的视觉对象将受阻，并在使用时显示错误消息）。 


Power BI Desktop（2019 年 3 月版及更高版本）支持通过“组策略”禁止在组织部署的计算机上使用未经认证的 Power BI 视觉对象。

<table>
<tr><th>属性</th><th>值</th>
</tr>
<td>键</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>值名称</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

十进制值 1 允许在 Power BI 中使用未经认证的 Power BI 视觉对象（这是默认值）。

十进制值 0 禁止在 Power BI 中使用未经认证的 Power BI 视觉对象（该选项只允许使用[认证的 Power BI 视觉对象](https://go.microsoft.com/fwlink/?linkid=2002010)）。

## <a name="r-visuals-settings"></a>R 视觉对象设置

### <a name="interact-with-and-share-r-visuals"></a>与 R 视觉对象进行交互并共享

组织中的用户可以与使用 R 脚本创建的视觉对象进行交互并共享。 [了解详细信息](../visuals/service-r-visuals.md)

> [!NOTE]
> 此设置应用于整个组织，并且不能限制为特定组。

## <a name="audit-and-usage-settings"></a>审核和使用情况设置

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>为内部活动审核和符合性创建审核日志

组织中的用户可以使用审核来监视组织中的其他用户在 Power BI 中执行的操作。 [了解详细信息](service-admin-auditing.md)

必须启用此设置，才能记录审核日志条目。 启用审核后，最多可能会延迟 48 小时才能查看审核数据。 如果无法立即查看数据，请稍后检查审核日志。 获取查看审核日志的权限和得以访问日志之间也存在类似的延迟。

> [!NOTE]
> 此设置应用于整个组织，并且不能限制为特定组。

### <a name="usage-metrics-for-content-creators"></a>内容创建者的使用指标

组织中的用户可以查看自己创建的仪表板和报表的使用情况指标。 [了解详细信息](../collaborate-share/service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>内容创建者的使用指标中的每个用户数据

内容创建者的使用指标将公开正在访问内容的用户的显示名称和电子邮件地址。 [了解详细信息](../collaborate-share/service-usage-metrics.md)

默认情况下，每个用户的数据都启用了使用指标并在指标报表中包含内容创建者帐户信息。 如果不希望对所有用户收集此信息，请为指定安全组或整个组织禁用此功能。 已排除用户的帐户信息随后会在报表中显示为“未命名”。

## <a name="dashboard-settings"></a>仪表板设置

### <a name="data-classification-for-dashboards"></a>仪表板的数据分类

组织中的用户可以为仪表板标记指明仪表板安全级别的分类。 [了解详细信息](../create-reports/service-data-classification.md)

> [!NOTE]
> 此设置应用于整个组织，并且不能限制为特定组。

## <a name="developer-settings"></a>开发人员设置

### <a name="embed-content-in-apps"></a>在应用中嵌入内容

组织中的用户可以在软件即服务 (SaaS) 应用程序中嵌入 Power BI 仪表板和报表。 禁用此设置会阻止用户使用 REST API 将 Power BI 内容嵌入到其应用程序中。 [了解详细信息](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>允许服务主体使用 Power BI API

在 Azure Active Directory (Azure AD) 中注册的 Web 应用将使用已分配的服务主体来访问 Power BI API，而无需用户登录。 若要允许应用使用服务主体身份验证，必须包含在允许的安全组中添加它的服务主体。 [了解详细信息](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> 服务主体继承其安全组中的所有 Power BI 租户设置的权限。 若要限制权限，请为服务主体创建专用的安全组并将其添加到相关已启用 Power BI 设置的“除特定安全组以外”列表。

## <a name="dataflow-settings"></a>数据流设置

### <a name="create-and-use-dataflows"></a>创建和使用数据流

组织中的用户可以创建和使用数据流。 若要概览数据流，请参阅 [Power BI 中的自助式数据准备](../transform-model/service-dataflows-overview.md)。 若要启用高级容量中的数据流，请参阅[配置工作负载](service-admin-premium-workloads.md)。

> [!NOTE]
> 此设置应用于整个组织，并且不能限制为特定组。

## <a name="template-apps-settings"></a>模板应用设置

三种模板应用设置控制能否发布或安装模板应用。

![Power BI 管理门户模板应用设置](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>发布模板应用

组织中的用户可以创建模板应用工作区。 控制哪些用户可以通过 [AppSource](https://appsource.microsoft.com) 或其他分发方法，将模板应用发布或分发给组织外部客户端。

![Power BI 管理门户的创建模板应用设置](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>安装 AppSource 上列出的模板应用

组织中的用户只能从 [AppSource](https://appsource.microsoft.com) 下载并安装模板应用。 控制哪些特定用户或安全组可以安装 AppSource 中的模板应用。

![Power BI 管理门户中的“安装模板应用”设置](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>安装 AppSource 上未列出的模板应用

控制组织中哪些用户可以下载并安装 [AppSource](https://appsource.microsoft.com) 上未列出的模板应用。

![Power BI 管理门户中的“安装模板应用”设置](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>容量设置

### <a name="power-bi-premium"></a>Power BI Premium

使用“Power BI Premium”选项卡，可以管理已为组织购买的任何 Power BI Premium 容量（EM 或 P SKU）。 组织中的所有用户都可以看到“Power BI Premium”选项卡；但如果用户被分配为容量管理员或拥有分配权限，则只能看到其中的内容。 如果用户没有任何权限，则显示以下消息。

![无权访问 Premium 设置](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

使用“Power BI Embedded”选项卡，可以查看已为客户购买的 Power BI Embedded (A SKU) 容量。 由于只能从 Azure 购买 A SKU，因此是在 Azure 门户中[管理 Azure 中的嵌入容量](../developer/embedded/azure-pbie-create-capacity.md)。

有关如何管理 Power BI Embedded (A SKU) 设置的详细信息，请参阅[什么是 Power BI Embedded](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)。

## <a name="embed-codes"></a>嵌入代码

管理员可以查看针对其租户生成的用于公开共享报表的嵌入代码。 此外，还可以撤消或删除代码。 [了解详细信息](../collaborate-share/service-publish-to-web.md)

![在 Power BI 管理门户中嵌入代码](media/service-admin-portal/embed-codes.png)

 ## <a name=""></a><a name="organizational-visuals">组织视觉对象</a> 

使用“组织视觉对象”选项卡，可以部署和管理组织内的 Power BI 视觉对象。 使用组织视觉对象，可以在组织中轻松部署专有的视觉对象，以便报表作者能够从 Power BI Desktop 中发现这些视觉对象，并将它们导入自己的报表中。 [了解详细信息](../developer/visuals/power-bi-custom-visuals-organization.md)

> [!WARNING]
> 自定义视觉对象可能包含存在安全或隐私风险的代码；请务必先信任自定义视觉对象的作者和来源，再将它们部署到组织存储库。

下图展示了目前在组织存储库中部署的所有 Power BI 视觉对象。

![组织管理员视觉对象](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>添加新的自定义视觉对象

若要向列表添加新的自定义视觉对象，请按以下步骤操作。 

1. 在右窗格中，选择“添加自定义视觉对象”。

    ![Power BI 视觉对象窗体](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. 填写“添加自定义视觉对象”表单：

    * **选择 .pbiviz 文件**（必填）：选择要上传的自定义视觉对象文件。 仅支持经版本控制的 API Power BI 视觉对象（阅读此处内容了解其含义）。

    在上传自定义视觉对象之前，应查看有关视觉对象的安全和隐私，确保它符合组织的标准。

    * **命名自定义视觉对象**（必填）：为视觉对象命名简短标题，以便 Power BI Desktop 用户能够轻松理解它的用途

    * **图标**：显示在 Power BI Desktop UI 中的图标文件。

    * **说明**：视觉对象的简短说明，用于向用户提供更多上下文和说明

1. 选择“添加”，以发起上传请求。 如果成功，可以在列表中看到新项目。 如果失败，会收到相应的错误消息

### <a name="delete-a-custom-visual-from-the-list"></a>从列表中删除自定义视觉对象

若要永久删除视觉对象，请选择存储库中视觉对象的回收站图标。

> [!IMPORTANT]
> 删除操作无法撤消。 一旦删除，此视觉对象会立即停止在现有报表中呈现。 即使重新上传同一个视觉对象，它也不会替换之前删除的视觉对象。 不过，用户可以重新导入新视觉对象，并替换报表中的现有实例。

### <a name="disable-a-custom-visual-in-the-list"></a>在列表中禁用自定义视觉对象

若要禁用组织存储区中的视觉对象，请选择齿轮图标。 在“访问”部分中，禁用自定义视觉对象。

禁用视觉对象后，视觉对象将不会在现有报表中呈现，并显示下面的错误消息。

此自定义视觉对象不再可用。有关详细信息，请联系租户管理员。

但是，设为书签的视觉对象仍正常工作。

进行任何更新或管理员更改后，Power BI Desktop 用户应重新启动应用程序或刷新 Power BI 服务中的浏览器以查看更新。

### <a name="update-a-visual"></a>更新视觉对象

若要更新组织存储中的视觉对象，请选择齿轮图标。 浏览并上传新版视觉对象。

确保视觉对象 ID 保持不变。 新文件将替换整个组织中所有报表的旧文件。 但是，如果新版本的视觉对象可能会破坏以前版本的视觉对象的任何使用情况或数据结构，则它们不会取代以前的版本。 相反，应创建新版本视觉对象的新列表。 例如，向新列出的视觉对象的标题添加新版本号（版本 X.X）。 通过这种方式，很明显可以看到，它还是相同的版本，只不过更新了版本号，因此现有报表不会破坏它们的功能。 同样，确保视觉对象 ID 保持不变。 然后，下一次用户从 Power BI Desktop 进入组织存储库时，他们就可以导入新版本，系统会提示他们替换报表中存在的当前版本。

有关详细信息，请访问[关于组织的 Power BI 视觉对象的常见问题解答](../developer/visuals/power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)

## <a name=""></a><a name="dataflowStorage">数据流存储（预览版）</a>

默认情况下，Power BI 中使用的数据存储在由 Power BI 提供的内部存储中。 通过数据流与 Azure Data Lake Storage Gen2 (ADLS Gen2) 的集成，可将数据流存储在组织的 Azure Data Lake Storage Gen2 帐户中。 有关详细信息，请参阅[数据流和 Azure Data Lake 集成（预览）](../transform-model/service-dataflows-azure-data-lake-integration.md)。

## <a name="workspaces"></a>工作区

作为管理员，可以查看租户中存在的工作区。 可以对列表中的工作区进行排序和筛选并显示每个工作区的详细信息。 表列对应于由 [Power BI 管理员 Rest API](/rest/api/power-bi/admin) 为工作区返回的属性。 个人工作区的类型是“PersonalGroup”，经典工作区的类型是“Group”，提供新工作区体验的工作区的类型是“Workspace”。 有关详细信息，请参阅[在新工作区中组织工作](../collaborate-share/service-new-workspaces.md)。

管理员还可以使用管理门户或 PowerShell CmdLet 来管理和恢复工作区。 

![工作区列表](media/service-admin-portal/workspaces-list.png)

在“工作区”选项卡上，可看到每个工作区的*状态*。 下表提供有关这些状态的含义的更多详细信息。

|州省/自治区/直辖市  |说明  |
|---------|---------|
| 活动 | 普通工作区。 它不指示任何有关使用情况或所含内容的信息，仅指示工作区本身“正常”。 |
| 孤立 | 无管理员用户的工作区。 |
| 已删除 | 已删除的工作区。 如果需要，我们保留了足够的元数据用于还原工作区，最多可保留 90 天。 |
| 正在删除 | 正在删除但尚未消失的工作区。 用户可以删除自己的工作区，将工作区放入“正在删除”并最终放入“已删除”。 |

## <a name="custom-branding"></a>自定义品牌

作为管理员，可以为整个组织自定义 Power BI 的外观。 目前有三个主要选项：

![自定义品牌选项](media/service-admin-portal/power-bi-custom-branding.png)

* **上传徽标**：为获得最佳结果，请上传另存为 .png 的徽标，大小不超过 10 KB，且至少为 200 x 30 像素。

* **上传封面图像**：为获得最佳结果，请上传另存为 .jpg 或 .png 的封面图像，大小不超过 1 MB，且至少为 1920 x 160 像素。

* **选择主题颜色**：可以根据十六进制 #、RGB、值或提供的托盘来选择主题。


有关详细信息，请参阅[为组织自定义品牌](https://aka.ms/orgBranding)。

![工作区列表](media/service-admin-portal/workspaces-list.png)

## <a name="manage-featured-content"></a>管理特别推荐的内容

租户管理员可以在组织的 Power BI 主页上管理已推广到“特别推荐”部分的所有报表、仪表板和应用。

- 在管理门户中，选择“特别推荐的内容”。

可在其中大致了解特别推荐内容的人员、推荐时间及其所有相关元数据。 如果出现可疑问题，或者要清理“特别推荐”部分，可以按需删除已推广的内容。

有关启用特别推荐的内容的信息，请参阅本文中的[特别推荐的内容](#featured-content)。

## <a name="next-steps"></a>后续步骤

[在组织中管理 Power BI](service-admin-administering-power-bi-in-your-organization.md)  
[了解 Power BI 管理员角色](service-admin-role.md)  
[在组织中审核 Power BI](service-admin-auditing.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

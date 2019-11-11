---
title: 从 Power BI 发布到 Web
description: 借助 Power BI 发布到 Web，可在任何设备上通过电子邮件或社交媒体，轻松地将交互式 Power BI 可视化效果在线嵌入博客帖子、网站等处。
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 9f8da4a5f37eb1e652dd2125dd588febf49fb01b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871851"
---
# <a name="publish-to-web-from-power-bi"></a>从 Power BI 发布到 Web

使用 Power BI 的“发布到 Web”选项，可在任何设备上通过电子邮件或社交媒体，轻松地将交互式 Power BI 可视化效果在线嵌入博客帖子、网站等处  。 还可以方便地编辑、更新、刷新或取消共享已发布的视觉对象。

> [!WARNING]
> 使用“发布到 Web”时，Internet 上的所有人都可查看你发布的报表或视觉对象  。 这无需身份验证，并且还可查看报表聚合的详细数据。 发布报表前，请确保可以公开共享数据和可视化效果。 请勿发布机密或专有信息。 如果有任何疑问，请在发布前查看组织策略。

>[!Note]
>要将内容安全地嵌入内部门户或网站，请使用[嵌入](service-embed-secure.md)或[在 SharePoint Online 中嵌入](service-embed-report-spo.md)选项。 这可确保在用户查看内部数据时强制执行所有权限和数据安全性。

## <a name="how-to-use-publish-to-web"></a>如何使用发布到 Web

可在个人工作区或组工作区中编辑的报表提供有“发布到 Web”功能  。  但与你共享的报表，或依赖行级安全性来保护数据的报表不提供该功能。 请参阅以下[限制](#limitations)部分，了解有关不支持“发布到 Web”的情况的完整列表   。 使用“发布到 Web”前请查看本文之前所述的“警告”部分   。

以下短视频演示了此功能的工作方式。 然后，按以下步骤自行尝试。

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

以下步骤介绍如何使用**发布到 Web**。

1. 打开可编辑的工作区中的报表，然后选择“文件”>“发布到 Web”  。

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. 查看对话框内容，然后选择“创建嵌入代码”  。

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. 查看如下所示的警告，并确认数据是否准备好嵌入到公共网站。 如果已准备好，选择“发布”  。

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. 对话框显示一条链接。 可以将此链接发送到电子邮件、将其嵌入 iFrame 等代码，或直接粘贴到网页或博客。

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. 如果之前为报表创建了嵌入代码并选择“发布到 Web”，则不会显示步骤 2-4 中的对话框  。 相反，将显示“嵌入代码”对话框  ：

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   每个报表只能创建一个嵌入代码。


## <a name="tips-and-tricks-for-view-modes"></a>视图模式的提示和技巧

在博客帖子中嵌入内容时，通常需要调整以适合屏幕的特定大小。  可根据需要调整 iFrame 标记中的高度和宽度。 但需要确保报表适合给定的 iFrame 区域，因此编辑报表时还需要设置相应的视图模式。

下表提供有关视图模式及其嵌入时外观的指导。

| 视图模式 | 嵌入时外观 |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |“调整到页面大小”会考虑报表的页面高度和宽度  。 如果将页面设置为“动态”比率，如 16:9 或 4:3，内容将在 iFrame 范围内缩放至合适的大小  。 嵌入 iFrame 中时，使用“调整到页面大小”可能会导致“宽屏”，内容在 iFrame 中调整至合适大小后，iFrame 区域会显示灰色背景   。 为了尽量避免宽屏，请正确设置 iFrame 的高度和宽度。 |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |“实际大小”确保报表保持其在报表页上设置的大小  。 这可能导致 iFrame 中显示滚动条。 设置 iFrame 高度和宽度，以避免出现滚动条。 |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |“适应宽度”确保内容适合 iFrame 的水平区域  。 仍会显示一个边框，但内容进行缩放，以便利用所有可用的水平空间。 |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>iFrame 高度和宽度的提示和技巧

“发布到 Web”嵌入如下所示的代码  ：

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
可以手动编辑宽度和高度，确保它正以所希望的方式适应正将其嵌入到的页面。

若要更加完美地适应，可尝试为 iFrame 的高度添加 56 个像素，以适应底部栏的当前大小。 如果报表页使用动态尺寸，下表提供了一些可用于实现适应页面而不会造成宽屏的尺寸。

| 比率 | 尺寸 | 维度（宽 x 高） |
| --- | --- | --- |
| 16:9 |小 |640 x 416 px |
| 16:9 |中 |800 x 506 px |
| 16:9 |大 |960 x 596 px |
| 4:3 |小 |640 x 536 px |
| 4:3 |中 |800 x 656 px |
| 4:3 |大 |960 x 776 px |

## <a name="manage-embed-codes"></a>管理嵌入代码

创建“发布到 Web”嵌入代码后，可通过 Power BI 中的“设置”菜单管理代码   。 管理嵌入代码包括，能够删除代码的目标视觉对象或报表（使嵌入代码不可用），或获取嵌入代码。

1. 若要管理你的**发布到 Web** 嵌入代码，打开**设置**齿轮，然后选择**管理嵌入代码**。

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. 显示嵌入代码。

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. 可以检索，也可以删除嵌入代码。 删除它会禁用指向该报表或视觉对象的任何链接。

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. 如果选择“删除”，系统会提示进行确认  。

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>报表更新和数据刷新

创建“发布到 Web”嵌入代码并将其共享后，将使用你所做的所有更改对报表进行更新，并立即激活嵌入代码链接  。 打开链接的任何人都可以查看。 但完成此初始操作之后，可能需要大约一个小时用户才能看见对报表或视觉对象的更新。 若要了解详细信息，请参阅本文后面[工作方式](#howitworks)部分  。 

## <a name="data-refresh"></a>数据刷新

数据刷新自动反映在嵌入的报表或视觉对象中。 大约需要一小时才可从嵌入代码中看到刷新的数据。 若要禁用自动刷新，选择报表所用数据集计划上的“不刷新”  。  

## <a name="custom-visuals"></a>自定义视觉对象

自定义视觉对象在**发布到 Web** 中受到支持。 使用“发布到 Web”时，共享你的已发布视觉对象的用户不需要启用自定义视觉对象来查看报表  。

## <a name="limitations"></a>限制

“发布到 Web”支持用于 Power BI 服务中绝大部分数据源和报表，但以下内容目前不受支持或不可用于“发布到 Web”   ：

- 使用行级别安全性的报表。
- 使用任何实时连接数据源的报表，包括在本地托管的 Analysis Services 表格、Analysis Services Multidimensional 以及 Azure Analysis Services。
- 直接或通过组织内容包共享的报表。
- 你不是编辑成员的组中的报表。
- “发布到 Web”报表中当前不支持“R”视觉对象  。
- 从已发布到 Web 的报表中的视觉对象中导出数据。
- ArcGIS Maps for Power BI 视觉对象。
- 包含报表级别 DAX 度量值的报表。
- 单一登录数据查询模型。
- [保护机密或专有信息](#publish-to-web-from-power-bi)。
- 随“嵌入”  选项提供的自动身份验证功能不适用于 Power BI JavaScript API。 对于 Power BI JavaScript API，请使用[用户拥有数据](developer/embed-sample-for-your-organization.md)方法进行嵌入。

## <a name="tenant-setting"></a>租户设置

Power BI 管理员可以启用或禁用“发布到 Web”功能  。 还可以限制对特定组的访问，这可能会对创建嵌入代码产生影响。

|功能 |为整个组织启用 |为整个组织禁用 |特定安全组   |
|---------|---------|---------|---------|
|报表“文件”菜单下的“发布到 Web”  |为所有对象启用|向所有对象隐藏|仅向已授权的用户或组显示。|
|“设置”下的“管理嵌入代码”  |为所有对象启用|为所有对象启用|为所有对象启用。<br><br>仅向已授权的用户或组显示“删除”选项。*  <br>为所有对象启用“获取代码”。*  |
|管理门户中的“嵌入代码” |“状态”将反映以下状态之一：<br>* 活动<br>* 不支持<br>* 已阻止|状态将显示“已禁用” |“状态”将反映以下状态之一：<br>* 活动<br>* 不支持<br>* 已阻止<br><br>如果未根据租户设置为某个用户授权，状态将显示为“侵权”。 |
|现有的已发布报表|全部已启用|全部已禁用|继续向所有对象呈现报表。|

## <a name="understanding-the-embed-code-status-column"></a>了解嵌入代码状态列

“管理嵌入代码”页包括状态列  。 嵌入代码默认处于“激活”状态，但也可能处于以下状态之一  。

| 状态 | 说明 |
| --- | --- |
| **活动** |该报表可供 Internet 用户查看并进行交互。 |
| **被阻止** |报表内容违反了 [Power BI 服务条款](https://powerbi.microsoft.com/terms-of-service)。 Microsoft 已将其阻止。 如果你认为内容被错误阻止，请与支持部门联系。 |
| **不支持** |报表的数据集正在使用行级别安全性或另一个不受支持的配置。 请参阅[限制](#limitations)部分中的完整列表  。 |
| **侵权** |嵌入代码在定义的租户策略外部。 如果在创建嵌入代码后更改“发布到 Web”租户设置以排除拥有该嵌入代码的用户，则通常会发生此情况  。 如果已禁用租户设置，或者不再允许用户创建嵌入代码，则现有嵌入代码显示“侵权”状态  。 |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>如何报告有关发布到 Web 内容的问题

若要报告与嵌入到网页或博客中的“发布到 Web”内容相关的问题，请使用底部栏中的“标志”图标，如下图所示   。 你将需要向 Microsoft 发送一封电子邮件，解释该问题。 Microsoft 将基于 Power BI 服务条款评估该内容，并采取相应的措施。

若要报告问题，请选择所见“发布到 Web”报表的底部栏中的“标志”图标   。

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>授权和定价

你需要成为 Microsoft Power BI 用户才能使用**发布到 Web**。 报告的查看者无需是 Power BI 用户。

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>工作方式（技术详细信息）

使用“发布到 Web”创建嵌入代码时，报表对所有 Internet 用户均可见  。 它是公开提供的，因此你可以期望将来查看者能够轻松地通过社交媒体共享报表。 用户查看报表，或者通过打开直接公共 URL，或者在嵌入到的网页或博客中查看，Power BI 将缓存报表定义和查看报表所需的查询结果。 这确保了成千上万的并发用户能够在不影响性能的情况下查看报表。

缓存持续很长时间，因此如果你更新报表定义（例如更改其视图模式）或刷新报表数据，大约需要一小时才能在用户查看的报表版本中反映更改。 因此建议你提前暂存工作，并仅当你对设置满意时创建**发布到 Web** 嵌入代码。

## <a name="next-steps"></a>后续步骤

- [SharePoint Online 报表 Web 部件](service-embed-report-spo.md) 

- [在安全门户或网站中嵌入报表](service-embed-secure.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

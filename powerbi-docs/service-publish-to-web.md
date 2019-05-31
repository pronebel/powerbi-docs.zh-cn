---
title: 从 Power BI 发布到 Web
description: 借助 Power BI 发布到 Web，可在任何设备上通过电子邮件或社交媒体，轻松地将交互式 Power BI 可视化效果在线嵌入博客帖子、网站等处。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051559"
---
# <a name="publish-to-web-from-power-bi"></a>从 Power BI 发布到 Web

使用 Power BI**发布到 web**选项，可以轻松嵌入交互式 Power BI 可视化效果在线，例如，在发布的博客文章，通过电子邮件或社交媒体网站的任何设备。 还可以方便地编辑、更新、刷新或取消共享已发布的视觉对象。

> [!WARNING]
> 当你使用**发布到 web**，Internet 上的任何人都可以查看已发布的报表或视觉对象。 这不要求身份验证，包括查看详细信息级别数据聚合报表。 之前发布报表，请确保它是可公开共享的数据和可视化效果确定。 请勿发布机密或专有信息。 如果有任何疑问，请在发布前查看组织策略。

>[!Note]
>要将内容安全地嵌入内部门户或网站，请使用[嵌入](service-embed-secure.md)或[在 SharePoint Online 中嵌入](service-embed-report-spo.md)选项。 这可确保在用户查看内部数据时强制执行所有权限和数据安全性。

## <a name="how-to-use-publish-to-web"></a>如何使用发布到 Web

**发布到 web**可用于在您可以编辑个人或组工作区中的报表。  它不是可用于与你，或那些依赖于行级别安全性来保护数据共享的报表。 请参阅[**限制**](#limitations)部分的完整列表的情况下获取其中**发布到 web**不受支持。 审阅**警告**然后才能使用本文前面部分**发布到 web**。

以下*简短视频*演示了此功能的工作原理。 然后，亲自尝试下面的步骤中。

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

以下步骤介绍如何使用**发布到 Web**。

1. 您可以编辑和选择的工作区中打开报表**文件 > 发布到 web**。

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. 查看对话框内容，并选择**创建嵌入代码**。

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. 查看以下警告，如下所示，并确认数据准备好嵌入公共网站。 如果是，则选择**发布**。

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. 包含链接出现一个对话框。 可以将此链接发送一封电子邮件中、 将其嵌入 iFrame，如代码中或直接粘贴到网页或博客。

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. 如果你之前创建的报表的嵌入代码并选择**发布到 web**，不会看到在步骤 2-4 中的对话框。 相反，**嵌入代码**此时将显示对话框：

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   每个报表只能创建一个嵌入代码。


## <a name="tips-and-tricks-for-view-modes"></a>视图模式的提示和技巧

嵌入博客帖子中的内容，通常需要适应特定的屏幕大小。  您可以调整高度和宽度以根据需要的 iFrame 标记。 但是，您需要确保报表适合 iFrame 给定的区域中，因此还需要编辑该报表时设置适当的视图模式。

下表提供有关视图模式及其嵌入时外观的指导。

| 视图模式 | 嵌入时外观 |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**适应页面**将考虑报表的页面高度和宽度。 如果您将您的页面设置为动态比率，如 16:9 或 4:3 将缩放你的内容以适合 iFrame。 当嵌入在 iFrame 中时，使用**调整到页面大小**可能会导致**设置**，其中灰色背景会显示在 iFrame 的区域中的内容后面因为缩放以适合 iFrame。 若要尽量减少宽屏幕，将相应地设置 iFrame 的高度和宽度。 |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**实际大小**可确保报表保持其大小为报表页上的组。 这可能导致在 iFrame 中显示的滚动条。 设置 iFrame 高度和宽度，以避免滚动条。 |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**适应宽度**可确保内容适合 iFrame 的水平区域。 仍将显示边框，但内容可以进行扩展以使用所有可用的水平空间。 |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>iFrame 高度和宽度的提示和技巧

一个**发布到 web**嵌入代码如下所示：

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
您可以编辑的宽度和高度手动以确保它正是您希望其要嵌入的页中容纳不下。

若要实现更多最佳选择，你可以尝试向 iFrame 的高度以适应底部栏的当前大小添加 56 像素。 如果你的报表页使用动态尺寸，下表提供了一些可用于实现适应页面而不会造成宽屏的尺寸。

| 比率 | 尺寸 | 维度（宽 x 高） |
| --- | --- | --- |
| 16:9 |小 |640 x 416 px |
| 16:9 |中 |800 x 506 px |
| 16:9 |大 |960 x 596 px |
| 4:3 |小 |640 x 536 px |
| 4:3 |中 |800 x 656 px |
| 4:3 |大 |960 x 776 px |

## <a name="manage-embed-codes"></a>管理嵌入代码

创建后**发布到 web**嵌入代码，你可以管理你的代码从**设置**Power BI 中的菜单。 管理嵌入代码包括，能够删除目标视觉对象或报表 （呈现嵌入代码不可用） 的代码，或获取嵌入代码。

1. 若要管理你的**发布到 Web** 嵌入代码，打开**设置**齿轮，然后选择**管理嵌入代码**。

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. 显示嵌入代码。

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. 可以检索，也可以删除嵌入代码。 正在删除它会禁用该报表或视觉对象的任何链接。

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. 如果选择**删除**，系统会提示进行确认。

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>报表更新和数据刷新

在创建后你**发布到 web**嵌入代码，并且共享它，报表使用的任何更改更新你使嵌入代码链接立即处于活动状态和任何打开该链接的人都可以查看它。 此初始操作之后，但是，对报表或视觉对象的更新可能需要大约一小时之前变得对用户可见。 如果你需要更新以便立即可用，可以删除嵌入代码并创建一个新的代码。 若要了解详细信息，请参阅[**其工作原理**](#howitworks)本文后面的部分。 

## <a name="data-refresh"></a>数据刷新

数据刷新自动反映在嵌入的报表或视觉对象中。 大约需要 1 小时才可从嵌入代码中看到刷新的数据。 若要禁用自动刷新，可以选择**不刷新**计划上的报表使用的数据集。  

## <a name="custom-visuals"></a>自定义视觉对象

自定义视觉对象在**发布到 Web** 中受到支持。 当你使用**发布到 web**，与你共享已发布视觉对象的用户是否需要启用自定义视觉对象以查看报表。

## <a name="limitations"></a>限制

**发布到 web**绝大部分数据源和报表在 Power BI 服务中，但是，以下是支持**不当前受支持或不可**与**发布到 web**:

- 使用行级别安全性的报表。
- 使用任何实时连接数据源的报表，包括在本地托管的 Analysis Services 表格、Analysis Services Multidimensional 以及 Azure Analysis Services。
- 直接或通过组织内容包共享的报表。
- 你不是编辑成员的组中的报表。
- "R"视觉对象目前不支持在**发布到 web**报表。
- 从报表中的可视化效果导出数据，其中已将发布到 web。
- ArcGIS Maps for Power BI 视觉对象。
- 包含报表级别 DAX 度量值的报表。
- 单一登录数据查询模型。
- [保护机密或专有信息](#publish-to-web-from-power-bi)。
- 随“嵌入”  选项提供的自动身份验证功能不适用于 Power BI JavaScript API。 对于 Power BI JavaScript API，请使用[用户拥有数据](developer/embed-sample-for-your-organization.md)方法进行嵌入。 了解有关[用户拥有数据](developer/embed-sample-for-your-organization.md)的详细信息。

## <a name="tenant-setting"></a>租户设置

Power BI 管理员可以启用或禁用**发布到 web**功能。 它们还可以限制对特定组，可能会影响你创建嵌入代码的能力的访问。

|功能 |为整个组织启用 |为整个组织禁用 |特定安全组   |
|---------|---------|---------|---------|
|**发布到 web**报表的下**文件**菜单|为所有对象启用|向所有对象隐藏|仅向已授权的用户或组显示。|
|“设置”下的“管理嵌入代码”  |为所有对象启用|为所有对象启用|为所有对象启用。<br><br>仅向已授权的用户或组显示“删除”选项。*  <br>为所有对象启用“获取代码”。*  |
|管理门户中的“嵌入代码” |“状态”将反映以下状态之一：<br>* 活动<br>* 不支持<br>* 已阻止|状态将显示“已禁用” |“状态”将反映以下状态之一：<br>* 活动<br>* 不支持<br>* 已阻止<br><br>如果未根据租户设置为某个用户授权，状态将显示为“侵权”。 |
|现有的已发布报表|全部已启用|全部已禁用|继续向所有对象呈现报表。|

## <a name="understanding-the-embed-code-status-column"></a>了解嵌入代码状态列

**管理嵌入代码**页面包括一个状态列。 默认情况下，嵌入代码都**Active**，但也可以是下列状态之一。

| 状态 | 说明 |
| --- | --- |
| **活动** |该报表可供 Internet 用户查看并进行交互。 |
| **被阻止** |报表内容违反[Power BI 服务条款](https://powerbi.microsoft.com/terms-of-service)。 Microsoft 已将其阻止。 如果你认为内容被错误阻止，请与支持部门联系。 |
| **不支持** |报表的数据集正在使用行级别安全性或另一个不受支持的配置。 请参阅[**限制**](#limitations)部分有关的完整列表。 |
| **侵权** |嵌入代码是定义的租户策略外部。 这通常发生在创建嵌入代码时，然后**发布到 web**租户设置已更改，以排除拥有嵌入代码的用户。 如果租户设置处于禁用状态，或不再允许用户创建嵌入代码，则现有嵌入代码 show**侵权**状态。 |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>如何报告有关发布到 Web 内容的问题

报告到相关的问题**发布到 web**内容嵌入网站或博客中，使用**标志**图标在底部栏中，在下图中所示。 你将需要向 Microsoft 发送一封电子邮件说明您关注的问题。 Microsoft 将计算基于 Power BI 服务条款的内容，并采取相应的措施。

若要报告问题，请选择**标志**中的底部栏图标**发布到 web**报告，请参阅。

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>授权和定价

你需要成为 Microsoft Power BI 用户才能使用**发布到 Web**。 在报表查看器不需要是 Power BI 用户。

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>工作方式（技术详细信息）

创建嵌入代码使用时**发布到 web**，报表将出现，并为 Internet 用户。 它是公开提供，因此应该能够轻松地在将来共享通过社交媒体报表的查看者。 用户查看报表，或者通过打开直接公共 URL，或者在嵌入到的网页或博客中查看，Power BI 将缓存报表定义和查看报表所需的查询结果。 这可确保，数以千计的并发用户可以查看报表，而不会影响性能。

缓存是报表的生存期较长，因此如果您更新报表定义 （例如，如果更改其视图模式） 或刷新报表数据，则可能需要大约 1 小时，才能更改会反映在你的用户查看的版本。 因此建议你提前暂存工作，并仅当你对设置满意时创建**发布到 Web** 嵌入代码。

## <a name="next-steps"></a>后续步骤

- [SharePoint Online 报表 Web 部件](service-embed-report-spo.md) 

- [在安全门户或网站中嵌入报表](service-embed-secure.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)

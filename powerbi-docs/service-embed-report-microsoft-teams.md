---
title: 通过 Microsoft Teams 的“Power BI”选项卡嵌入报表
description: 通过 Microsoft Teams 的“Power BI”选项卡，可以在频道和聊天中轻松嵌入交互式报表。
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 03/12/2020
ms.openlocfilehash: fe8b5ed0e3cdf0003986ffe6eab18e97e83f3dec
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381185"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>通过 Microsoft Teams 的“Power BI”选项卡嵌入报表

通过 Microsoft Teams 更新的“Power BI”选项卡，可以在 Microsoft Teams 频道和聊天中轻松嵌入交互式报表。

使用 Microsoft Teams 的“Power BI”选项卡，可帮助你的同事查找团队所使用的数据并在团队频道中进行讨论。

## <a name="requirements"></a>要求

要使 Microsoft Teams 的“Power BI”选项卡工作，需要满足以下要求  ：

- Power BI Pro 许可证，或报告包含在具有 Power BI 许可证的 [Power BI Premium 容量（EM 或 P SKU）](service-premium-what-is.md)中。
- Microsoft Teams 的“Power BI”选项卡。
- 用户必须登录到 Power BI 服务以激活其 Power BI 许可证，才能使用报表。
- 用户必须具有查看报表的权限。

## <a name="embed-your-report"></a>嵌入报表
若要将报表嵌入 Microsoft Teams 频道或聊天，请按如下所述进行添加。

1. 在 Microsoft Teams 中打开所需的频道或聊天，然后选择“+”图标  。

    ![将选项卡添加到频道或聊天](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. 选择“Power BI”选项卡。

    ![显示“Power BI”的 Microsoft Teams 选项卡列表](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. 使用提供的选项从工作区、与我共享或 Power BI 应用中选取报表

    ![Microsoft Teams 的“Power BI”选项卡设置](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. 选项卡名称会自动更新以匹配报表名称，但你可以自行更改。 

5. 按“保存”  。

## <a name="supported-reports"></a>支持的报表

该选项卡允许嵌入以下报表：

- 交互式报表和分页报表
- 我的工作区、新工作区体验和经典工作区中的报表
- Power BI 应用中的报表


## <a name="grant-access-to-reports"></a>授予报表访问权限

在 Microsoft Teams 中嵌入报表不会自动授予用户报表查看权限 - 你需要[在 Power BI 允许用户查看报表](service-share-dashboards.md)。 可以使用 Office 365 组，从而为团队提供更轻松的体验。 

> [!IMPORTANT]
> 请务必在 Power BI 中检查哪些人员可以查看报表，然后向未列出的人员授予访问权限。

要确保团队中的每个人都有权访问嵌入的报表，一种方法是将报表放在 Power BI 的单个工作区中，并为团队的 Office 365 组授予对工作区的访问权限。

## <a name="start-a-conversation"></a>开始对话

将“Power BI 报表”选项卡添加到 Teams 时，Teams 可自动创建报表随附的选项卡对话。 

- 选择右上角的“显示选项卡对话”  。

    ![显示选项卡对话图标](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    第一个注释是指向报表的链接。 该 Teams 频道中的每个人都可以在对话中查看并讨论报表。

    ![选项卡对话](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>已知问题和限制

- Power BI 不支持 Microsoft Teams 支持的本地化语言。 因此，可能无法在嵌入的报表中看到正确的本地化内容。
- 不能在 Microsoft Teams 的“Power BI”选项卡中嵌入 Power BI 仪表板。
- 没有 Power BI 许可证或报表权限的用户将看到“内容不可用”消息。
- 如果使用的是 Internet Explorer 10，可能会遇到问题。 <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Microsoft Teams 的“Power BI”选项卡不支持 [URL 筛选器](service-url-filters.md)。
- 在国家云中，新的“Power BI”选项卡不可用，但可能有较旧的版本可用，该版本不支持 Power BI 应用中的新工作区体验工作区或报表。 
- 保存选项卡后，不能通过选项卡设置更改选项卡名称。 使用重命名选项对其进行更改。

## <a name="next-steps"></a>后续步骤
- [与同事和其他人共享仪表板](service-share-dashboards.md)  
- [在 Power BI 中构建和分发应用](service-create-distribute-apps.md)  
- [什么是 Power BI Premium？](service-premium-what-is.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

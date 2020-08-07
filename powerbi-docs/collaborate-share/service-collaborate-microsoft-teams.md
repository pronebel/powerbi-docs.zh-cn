---
title: 使用 Power BI 在 Microsoft Teams 中开展协作
description: 可以在 Microsoft Teams 频道和聊天中轻松共享和协作处理交互式 Power BI 内容。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/31/2020
ms.openlocfilehash: 01e5b470e0beb189d64da18785a17e771bcaf59b
ms.sourcegitcommit: d9d67ee47954379c2df8db8d0dc8302de4c9f1e5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87478029"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>使用 Power BI 在 Microsoft Teams 中开展协作

随着分布式和远程劳动力成为常态，越来越多的组织依赖于 Microsoft Teams 来使员工保持同步。Power BI 提供多个选项，可用于在 Microsoft Teams 频道和聊天中共享和协作处理交互式 Power BI 内容。 

- 通过 Microsoft Teams 的“Power BI”选项卡，可以[在 Microsoft Teams 频道和聊天中嵌入交互式报表](service-embed-report-microsoft-teams.md)。 “Power BI”选项卡可帮助你的同事查找团队的数据并在团队频道中进行讨论。 
- 将报表、仪表板和应用的链接粘贴到 Microsoft Teams 消息框中时，请创建[链接预览](service-teams-link-preview.md)。 链接预览会显示有关该链接的信息。 
- 在 Power BI 服务中查看报表和仪表板时，请使用[共享到 Teams](service-share-report-teams.md)，以在 Teams 中快速开始对话。
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="嵌入到 Teams 频道的 Power BI 报表的屏幕截图。":::

## <a name="requirements"></a>要求

通常，要使 Power BI 在 Microsoft Teams 中工作，请确保以下元素：

- 用户具有 Power BI Pro 许可证，或报告包含在具有 Power BI 许可证的 [Power BI Premium 容量（EM 或 P SKU）](../admin/service-premium-what-is.md)中。
- 用户已登录到 Power BI 服务以激活其 Power BI 许可证。
- 用户满足使用 Microsoft Teams 中“Power BI”选项卡的要求。

## <a name="grant-access-to-reports"></a>授予报表访问权限

在 Microsoft Teams 中嵌入报表或发送项的链接不会自动授予用户报表查看权限。 你需要[在 Power BI 中允许用户查看报表](service-share-dashboards.md)。 可以使用 Microsoft 365 组，从而为团队提供更轻松的体验。

> [!IMPORTANT]
> 请务必在 Power BI 中检查哪些人员可以查看报表，然后向未列出的人员授予访问权限。

要确保团队中的每个人都有权访问报表，一种方法是将报表放在单个工作区中，并为团队的 Microsoft 365 组授予访问权限。

## <a name="known-issues-and-limitations"></a>已知问题和限制

- Power BI 不支持 Microsoft Teams 支持的本地化语言。 因此，可能无法在嵌入的报表中看到正确的本地化内容。
- 不能在 Microsoft Teams 的“Power BI”选项卡中嵌入 Power BI 仪表板。
- 没有用于访问报表的 Power BI 许可证或权限的用户会看到“内容不可用”消息。
- 如果使用 Internet Explorer 10，则可能会遇到问题。 <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Microsoft Teams 的“Power BI”选项卡不支持 [URL 筛选器](service-url-filters.md)。
- 在国家/地区云中，新的“Power BI”选项卡不可用。 可能有较旧的版本可用，该版本不支持 Power BI 应用中的新工作区体验或报表。
- 保存选项卡之后，无法通过选项卡设置更改选项卡名称。 使用“重命名”选项对其进行更改。
- 链接预览服务不支持单一登录。
- 链接预览在会议聊天或私人频道中不起作用。

## <a name="next-steps"></a>后续步骤

- [在 Microsoft Teams 中嵌入 Power BI 内容](service-embed-report-microsoft-teams.md)
- [在 Microsoft Teams 中获取 Power BI 链接预览](service-teams-link-preview.md)
- [通过 Power BI 服务直接共享到 Teams](service-share-report-teams.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)。

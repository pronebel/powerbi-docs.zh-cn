---
title: 创建指向 Power BI 移动应用中特定位置的链接
description: 了解如何使用统一资源标识符 (URI) 创建指向 Power BI 移动应用中特定仪表板、磁贴或报表的深层链接。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: maggies
ms.openlocfilehash: 1f9503980ba19b290fa5d0fd1f521bb85ef93759
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983568"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>创建指向 Power BI 移动应用中特定位置的链接
可以创建和使用统一资源标识符 (URI) 链接到所有移动平台（iOS、Android 设备和 Windows 10）上 Power BI 移动应用中的特定位置（即 *深层链接* ）。

URI 链接可以直接指向仪表板、磁贴和报表。

深层链接的目标决定了 URI 的格式。 请按以下步骤操作，创建指向不同位置的深层链接。 

## <a name="open-the-power-bi-mobile-app"></a>打开 Power BI 移动应用
在任意设备上使用此 URI 打开 Power BI 移动应用：

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>打开特定仪表板
此 URI 可打开 Power BI 移动应用的特定仪表板：

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

若要查找包含 36 个字符的仪表板对象 ID，请转到 Power BI 服务 (https://powerbi.com)) 中的特定仪表板。 有关示例，请参阅以下 URL 中的突出显示部分：

`https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**`

如果仪表板位于“我的工作区”以外的组中，请在仪表板 ID 前面或后面添加 `&GroupObjectId=<36-character-group-id>`。 例如： 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

请注意两者之间的 & 号。

## <a name="open-to-a-specific-tile-in-focus"></a>打开处于焦点模式的特定磁贴
此 URI 可打开 Power BI 移动应用中处于焦点模式的特定磁贴：

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

若要查找包含 36 个字符的仪表板和磁贴对象 ID，请转到 Power BI 服务 (https://powerbi.com)) 中的特定仪表板，然后打开处于焦点模式的磁贴。 有关示例，请参阅以下 URL 中的突出显示部分：

`https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus`

对于此磁贴，URI 为：

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

请注意两者之间的 & 号。

如果仪表板位于“我的工作区”以外的组中，请添加 `&GroupObjectId=<36-character-group-id>`。

## <a name="open-to-a-specific-report"></a>打开特定报表
此 URI 可打开 Power BI 移动应用中的特定报表：

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

若要查找包含 36 个字符的报表对象 ID，请转到 Power BI 服务 (https://powerbi.com)) 中的特定报表。 有关示例，请参阅以下 URL 中的突出显示部分：

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300`

如果报表位于“我的工作区”以外的组中，请在报表 ID 前面或后面添加 `&GroupObjectId=<36-character-group-id>`。 例如： 

mspbi://app/OpenReport?ReportObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

请注意两者之间的 & 号。

## <a name="open-to-a-specific-report-page"></a>打开特定报表页
此 URI 可打开 Power BI 移动应用中的特定报表页：

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

此报表页名为“ReportSection（后跟一个数字）”。 同样，在 Power BI 服务 (https://powerbi.com)) 中打开报表，再转到特定的报表页。 

有关示例，请参阅以下 URL 中的突出显示部分：

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/ReportSection11`

## <a name="open-in-full-screen-mode"></a>在全屏模式下打开
添加下面用粗体显示的参数，可以在全屏模式下打开特定报表：

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

例如： 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>添加上下文（可选）
还可以在字符串中添加上下文。 如果你需要与我们联系，我们可以使用上下文来筛选我们向你的应用发送的数据。 在链接中添加 `&context=<app-name>`

有关示例，请参阅以下 URL 中的突出显示部分： 

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/&context=SlackDeepLink`

## <a name="next-steps"></a>后续步骤
你的反馈将帮助我们决定未来要做什么，如果你想在 Power BI 移动应用中看到其他功能，别忘了向我们提出你的建议。 

* [适用于移动设备的 Power BI 应用](mobile-apps-for-mobile-devices.md)
* 关注 Twitter 上的 @MSPowerBI
* 加入 [Power BI 社区](http://community.powerbi.com/)的对话
* [什么是 Power BI？](../../power-bi-overview.md)


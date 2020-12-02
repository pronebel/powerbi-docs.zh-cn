---
title: Power BI 计划内维护
description: 面向管理员的有关 Power BI 计划内维护如何影响其组织以及可能需要执行的后续步骤的信息。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/30/2020
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: d62b06e23f7e97141f6d10451e9d75f8fb9e417e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412313"
---
# <a name="power-bi-planned-maintenance"></a>Power BI 计划内维护

Power BI 服务的计划内维护是我们承诺向客户提供可靠产品的必要部分。 当发生计划内维护时，Power BI 服务将在一段时间内不可供组织使用。 用户可能无法访问 Power BI 服务，并且后台操作可能会失败。 在维护时段后，我们预计服务能够正常运行，并成功执行交互式操作和后台操作。  

维护计划在非正常营业时间进行，以帮助最大限度地减少对组织的影响。 对于具有全球用户的组织，我们认识到，“非正常营业时间”可能会对你造成不同的影响。 对用户造成的任何影响，我们深表歉意。 我们正在努力改进 Power BI 并最大限度地减少这些维护时段。

如果你的组织受到影响，我们将提前通知你。 Microsoft 365 管理员将在 Microsoft 365 消息中心中看到提前通知，并将收到电子邮件。 此外，将通过 Microsoft 帐户团队通知具有顶级支持合同的客户。

## <a name="actions-to-take-now"></a>要立即执行的操作

* Microsoft 365 管理员应[检查消息中心](https://admin.microsoft.com/Adminportal/Home#/MessageCenter)是否有 Power BI 计划内维护的相关消息。 与应当了解但可能无权访问消息中心的用户共享消息。
* 如果你不是 Microsoft 365 管理员，请与 IT 部门或内部支持团队联系，询问即将进行的任何维护。

## <a name="actions-to-take-when-maintenance-is-complete"></a>维护完成后要执行的操作

* 用户应刷新任何打开的浏览器窗口。
* Power BI 移动应用用户将需要验证他们使用的版本是否是最新的，然后注销并重新登录应用。 查看你手机的 App Store 或查看我们的 [Power BI 移动版](https://powerbi.microsoft.com/mobile/)页。
* 主动编辑或发布使用组织视觉对象的报表的客户，无论是在本地还是从 OneDrive 和 SharePoint 位置，都需要通过组织视觉对象存储重新导入视觉对象，或在重新发布之前下载更新的 PBIX。 有关组织视觉对象的详细信息，请参阅[组织视觉对象](organizational-visuals.md)。
* 如果使用“在 Excel 中分析”功能的 Excel 工作簿未刷新，则可能需要更新连接字符串或重新下载该数据集的 ODC 连接。 有关详细信息，请参阅[在 Excel 中分析](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data)。
* 维护完成后，可能无法连接嵌入在内容中的 Power BI 链接。 例如，SharePoint 或 Teams 中的嵌入链接可能会导致用户错误。 若要解决此问题，必须重新生成 Power BI 中的嵌入链接，然后更新它们的使用位置。 有关嵌入链接的详细信息，请参阅[在 SharePoint Online 中嵌入报表 Web 部件](../collaborate-share/service-embed-report-spo.md)和[使用 Power BI 在 Microsoft Teams 中开展协作](../collaborate-share/service-collaborate-microsoft-teams.md)。
* 某些在维护前收集的使用情况数据在维护完成后将不可用。 这些使用情况数据包括：

  * [Power BI 活动日志](service-admin-auditing.md#use-the-activity-log)。 在维护之前，用户应下载活动日志。 你还可以使用 [Office 365 审核日志数据](service-admin-auditing.md#access-your-audit-logs)来获取等效的活动详细信息。
  * 在[世系视图](../collaborate-share/service-data-lineage.md#explore-lineage-view)中查看计数
  * [数据保护指标报表](service-security-data-protection-metrics-report.md)
  * [使用指标（预览版）](../collaborate-share/service-modern-usage-metrics.md)

## <a name="next-steps"></a>后续步骤

* [启用服务中断通知](service-interruption-notifications.md)
* [跟踪消息中心即将发生的更改](/microsoft-365/admin/manage/message-center)
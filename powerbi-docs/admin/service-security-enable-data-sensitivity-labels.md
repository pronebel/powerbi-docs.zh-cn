---
title: 在 Power BI 中启用数据敏感度标签
description: 了解如何在 Power BI 中启用数据敏感度标签
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: c6c1c20e88e6da96ed0c7239ee26f63220c28a00
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85227053"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>在 Power BI 中启用数据敏感度标签

为了在 Power BI 中使用 [Microsoft 信息保护数据敏感度标签](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)，必须在租户中启用这些标签。 本文将向 Power BI 租户管理员展示如何执行此操作。 有关 Power BI 中数据敏感度标签的概述，请参阅 [Power BI 中的数据保护](service-security-data-protection-overview.md)。 有关在 Power BI 中应用敏感度标签的信息，请参阅[应用敏感度标签](../collaborate-share/service-security-apply-data-sensitivity-labels.md) 

启用敏感度标签时：

* 组织中的指定用户和安全组可以对其 Power BI 报表、仪表板、数据集和数据流进行分类并[应用敏感度标签](../collaborate-share/service-security-apply-data-sensitivity-labels.md)。
* 组织中的所有成员都可以查看这些标签。

启用数据敏感度标签需要 Azure 信息保护许可证。 有关详细信息，请参阅[授权](service-security-data-protection-overview.md#licensing)。

## <a name="enable-data-sensitivity-labels"></a>启用数据敏感度标签

转到 Power BI 管理门户，打开“租户设置”窗格，并找到“信息保护”部分  。

![查找“信息保护”部分](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

在“信息保护”部分，执行以下步骤：
1. 打开“允许用户对 Power BI 内容应用敏感度标签”。
1. 启用切换。
1. 定义哪些用户可以在 Power BI 资产中应用和更改敏感度标签。 默认情况下，组织中的每个人都能够应用敏感度标签。 但是，可以选择仅为特定用户或安全组启用敏感度标签。 选择整个组织或特定安全组后，可以排除特定的用户或安全组子集。
   
   * 为整个组织启用敏感度标签时，例外情况通常是安全组。
   * 只为特定用户或安全组启用敏感度标签时，例外通常是特定的用户。  
    该方法可以防止某些用户在 Power BI 中应用敏感度标签，即使他们不属于有权执行此操作的组。

1. 点击“应用”。

![启用敏感度标签](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> 只有拥有“创建”和“编辑”资产权限，以及在本部分中设置的相关安全组成员的 Power BI Pro 用户，才能设置和编辑敏感度标签 。 不属于本组的用户无法设置或编辑标签。  

## <a name="troubleshooting"></a>故障排除

Power BI 使用 Microsoft 信息保护敏感度标签。 因此，如果在尝试启用敏感度标签时遇到错误信息，则可能是由下列原因之一造成的：

* 没有 Azure 信息保护[许可证](service-security-data-protection-overview.md#licensing)。
* 敏感度标签尚未迁移到 Power BI 支持的 Microsoft 信息保护版本。 了解关于[迁移敏感度标签](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)的详细信息。
* 组织中未定义 Microsoft 信息保护敏感度标签。 请注意，标签必须是已发布策略的一部分才能使用。 [了解敏感度标签的详细信息](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)，或访问 [Microsoft 安全与合规中心](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels)，了解如何为组织定义标签和发布策略。

## <a name="considerations-and-limitations"></a>注意事项和限制

以下列表提供了 Power BI 中敏感度标签的一些限制：

常规
* 敏感度标签只能应用于仪表板、报表、数据集和数据流。 它们当前不可用于[分页报表](../paginated-reports/report-builder-power-bi.md)和工作簿。
* Power BI 资产上的敏感度标签在工作区列表、世系、收藏夹、最近使用和应用视图中可见。这些标签目前在“与我共享”视图中不可见。 但请注意，应用于 Power BI 资产的标签（即使不可见）将始终保留在导出到 Excel、PowerPoint 和 PDF 文件中的数据上。
* 仅全球（公有）云中的租户支持敏感度标签。 其他云中的租户不支持敏感度标签。
* 模板应用不支持数据敏感度标签。 模板应用创建者设置的敏感度标签在提取和安装应用时被删除，应用使用者添加到已安装模板应用项目的敏感度标签在更新应用时丢失（重置为无）。
* Power BI 不支持[请勿转发](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)、[用户定义](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)和 [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions) 这三种保护类型的敏感度标签。 “请勿转发”和“用户定义”保护类型引用 [Microsoft 365 安全中心](https://security.microsoft.com/)或 [Microsoft 365 合规中心](https://compliance.microsoft.com/)内定义的标签。
* 不建议允许用户在 Power BI 中应用父标签。 如果对内容应用了父标签，则无法将数据从该内容导出到文件（Excel、PowerPoint 和 PDF）。 请参阅[子标签（分组标签）](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels)。

**导出**
* 仅在将数据导出到 Excel、PowerPoint 和 PDF 文件时，才会强制执行标签和保护控件。 在将数据导出到 .csv 或 .pbix 文件、Excel 中的分析或任何其他导出路径时，不会强制执行标签和保护。
* 对导出的文件应用敏感度标签和保护不会向文件添加内容标记。 但是，如果标签配置为应用内容标记，则在 Office 桌面应用中打开文件时，Azure 信息保护统一标签客户端会自动应用这些标记。 在为桌面、移动或 Web 应用使用内置标签时，不会自动应用内容标记。 有关更多详细信息，请参阅 [Office 应用何时应用内容标记和加密](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption)。
* 从 Power BI 导出文件的用户有权根据敏感度标签设置访问和编辑该文件。 导出数据的用户不会获得该文件的所有者权限。
* 如果在将数据导出到文件时无法应用标签，导出将失败。 要检查导出失败的原因是否为无法应用标签，请在标题栏的中心单击报表或仪表板名称，然后在打开的信息下拉菜单中查看是否显示“无法加载敏感度标签”。 如果安全管理员取消发布或删除了应用的标签，或出现了临时系统问题，则可能会发生这种情况。

## <a name="next-steps"></a>后续步骤

本文介绍如何在 Power BI 中启用数据敏感度标签。 以下文章提供了有关 Power BI 中的数据保护的详细信息。 

* [Power BI 中的数据保护概述](service-security-data-protection-overview.md)
* [在 Power BI 中应用数据敏感度标签](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [在 Power BI 中使用 Microsoft Cloud App Security 控件](service-security-using-microsoft-cloud-app-security-controls.md)
* [数据保护指标报表](service-security-data-protection-metrics-report.md)
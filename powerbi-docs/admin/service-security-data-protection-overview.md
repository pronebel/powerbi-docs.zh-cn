---
title: Power BI 中的数据保护
description: 了解 Power BI 中数据保护的工作原理
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315663"
---
# <a name="data-protection-in-power-bi"></a>Power BI 中的数据保护

现代企业对如何处理和保护敏感数据有严格的业务规定和要求。 为了提供对此类数据的控制和可见性，Power BI 与 Microsoft 信息保护和 Microsoft Cloud App Security 进行了集成。 这样，便可以：
* 使用 Microsoft 信息保护[敏感度标签](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide)对 Power BI 服务中的内容（仪表板、报表、数据集和数据流）进行分类和标记，并且遵循与 Office 365 中用于分类和保护文件的相同分类法。
* 在将数据导出到 Excel、PowerPoint 或 PDF 文件时，向数据应用 Microsoft 信息保护敏感度标签和保护。
* 使用 Microsoft Cloud App Security 来监视 Power BI 中的活动；调查安全问题；通过 Microsoft Cloud App Security 条件访问应用控制保护 Power BI 中的内容。

重要事项
* 敏感度标签不会影响对 Power BI 中内容的访问权限 - 对 Power BI 中内容的访问权限由 Power BI 权限单独管理。 如果标签可见，则不会应用任何相关的加密设置（在 [Microsoft 365 安全中心](https://security.microsoft.com/)或 [Microsoft 365 合规中心](https://compliance.microsoft.com/)内配置）。 它们仅应用于导出到 Excel、PowerPoint 和 PDF 文件的数据。
* 除了导出到 Excel、PowerPoint 和 PDF 以外，任何导出路径都不会应用敏感度标签和文件加密。 Power BI 租户管理员可以禁用任何或所有不支持应用敏感度标签及其关联文件加密设置的导出路径。

## <a name="sensitivity-labels-in-power-bi"></a>Power BI 中的敏感度标签

在 [Microsoft 365 安全中心](https://security.microsoft.com/)或 [Microsoft 365 合规中心](https://compliance.microsoft.com/)创建和管理敏感度标签。

要在任一中心访问敏感度标签，请导航到“分类”>“敏感度标签”。 这些敏感度标签可由多个 Microsoft 服务（例如 Azure 信息保护、Office 应用和 Office 365 服务）使用。

> [!Important]
> 如果你的组织使用 Azure 信息保护敏感度标签，则需要将这些标签[迁移](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)到前面列出的服务之一，以便在 Power BI 中使用它们。

> [!NOTE]
> 敏感度标签仅在公有云的租户中受支持，而在云（如主权云）的租户中不受支持。

## <a name="how-sensitivity-labels-work-in-power-bi"></a>敏感度标签在 Power BI 中的工作原理

向 Power BI 仪表板、报表、数据集或数据流应用敏感度标签时，类似于对资源应用标记，这样做具有以下优点：
* 可自定义 - 可以为组织中不同级别的敏感内容创建类别，如个人、公共、一般、机密和高度机密。
* 明文 - 由于标签为明文形式，因此用户可以轻松地根据敏感度标签指南了解如何处理内容。
* **持久** - 向内容应用敏感度标签之后，在将内容导出到 Excel、PowerPoint 和 PDF 文件时，将随内容一起导出标签，并成为应用和强制执行策略的基础。

这意味着，在将内容导出到 Excel、PowerPoint 和 PDF 文件时，敏感度标签会随内容一起导出，并成为应用和强制执行策略的基础。

Power BI 租户管理员可以在 [Power BI 管理门户](service-admin-portal.md)中控制[导出到 Excel](service-admin-portal.md#export-to-excel) 和[导出到 PowerPoint 和 PDF](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents)。

## <a name="sensitivity-label-example"></a>敏感度标签示例

以下是有关 Power BI 中的敏感度标签如何工作的快速示例。
1. 在 Power BI 服务中，“高度机密”敏感度标签应用于报表。

   ![列表视图中的敏感度标签](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. 将数据从此报表导出到 Excel 文件时，敏感度标签和保护将应用于导出的 Excel 文件。

   ![敏感度标签随内容生效](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

在 Microsoft Office 应用程序中，敏感度标签作为标记显示在电子邮件或文档中，类似于上图所示。 你还可以为内容分配一个分类（如标签），它会在通过 Power BI 使用和共享内容时持续存在并随内容漫游。 可以使用此分类生成使用情况报表并查看敏感内容的活动数据。 基于此信息，你始终可以选择以后应用保护设置。

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>在 Power BI 中使用敏感度标签的要求

在 Power BI 中启用和使用敏感度标签前，必须先完成以下先决条件：
* 确保在 [Microsoft 365 安全中心](https://security.microsoft.com/)或 [Microsoft 365 合规中心](https://compliance.microsoft.com/)中定义了敏感度标签。
* 在 Power BI 中[启用敏感度标签](service-security-enable-data-sensitivity-labels.md)。
* 确保用户具有[适当的许可证](#licensing)。
* 如果将 Microsoft Cloud App Security 与 Power BI 结合使用，请确保具有[适当的授权](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing)。

## <a name="protect-content-using-microsoft-cloud-app-security"></a>使用 Microsoft Cloud App Security 保护内容

可以通过使用 Microsoft Cloud App Security 来保护 Power BI 中的内容免遭意外的泄漏或破坏。 设置并配置 Microsoft Cloud App Security 后，安全管理员可以监视用户访问和活动，执行实时风险分析，并设置标签特定的控件。

例如，组织可以使用 Microsoft Cloud App Security 来配置策略，防止用户将敏感数据从 Power BI 下载到非托管设备。 此类配置可让用户保持工作效率并在任何位置都能连接到 Power BI，同时使用 Microsoft Cloud App Security 来防止损害用户操作，所有这些都是实时的。

**要求**

在敏感度标签可使用 Microsoft Cloud App Security 之前，必须先满足以下先决条件：
* 必须为租户[启用 Cloud App Security 和 Azure 信息保护](https://docs.microsoft.com/cloud-app-security/azip-integration)。
* 应用[必须连接到 Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps)。

## <a name="licensing"></a>许可

* 要在 Power BI 中应用和查看 Microsoft 信息保护敏感度标签，需要 Azure 信息保护高级版 P1 或高级版 P2 许可证。 Microsoft Azure 信息保护可以单独进行购买，也可以通过一个 Microsoft 许可套件进行购买。 有关详细信息，请参阅 [Azure 信息保护定价](https://azure.microsoft.com/pricing/details/information-protection/)。
* 要在 Office 应用中查看和应用标签，需满足[许可要求](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels)。
* 要向 Power BI 内容应用标签，除上述任一 Azure 信息保护许可证之外，用户还必须具有 Power BI Pro 许可证。
* 如果要使用 Microsoft Cloud App Security 来保护 Power BI 内容免遭意外泄露或破坏，则必须具有[必要的 Microsoft Cloud App Security 许可证](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing)。

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

本文概述了 Power BI 中的数据保护。 以下文章提供了有关 Power BI 中的数据保护的进一步详细信息。 

* [在 Power BI 中启用数据敏感度标签](service-security-enable-data-sensitivity-labels.md)
* [在 Power BI 中应用数据敏感度标签](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [在 Power BI 中使用 Microsoft Cloud App Security 控件](service-security-using-microsoft-cloud-app-security-controls.md)
* [数据保护指标报表](service-security-data-protection-metrics-report.md)
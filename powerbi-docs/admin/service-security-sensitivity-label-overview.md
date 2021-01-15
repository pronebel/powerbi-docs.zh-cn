---
title: Power BI 中的 Microsoft 信息保护敏感度标签
description: 了解 Power BI 中的 Microsoft 信息保护敏感度标签的工作原理
author: paulinbar
ms.author: painbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: conceptual
ms.custom: contperf-fy21q2
ms.date: 12/20/2020
LocalizationGroup: Data from files
ms.openlocfilehash: d47d9b973eadb06095c2a2aebb8fe93cf6ab4414
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969526"
---
# <a name="sensitivity-labels-in-power-bi"></a>Power BI 中的敏感度标签

本文介绍 Power BI 中 Microsoft 信息保护敏感度标签的功能。

有关在租户上启用敏感度标签的信息（包括许可要求和先决条件），请参阅[在 Power BI 中启用数据敏感度标签](service-security-enable-data-sensitivity-labels.md)。

有关如何将敏感度标签应用于 Power BI 内容和文件的信息，请参阅[如何在 Power BI 中应用敏感度标签](./service-security-apply-data-sensitivity-labels.md)。

>[!NOTE]
>Power BI Desktop 中的敏感度标签目前为预览版。

## <a name="introduction"></a>简介

Microsoft 信息保护敏感度标签为用户提供了一种简单的方法，可在不影响生产力或协作能力的情况下，在 Power BI 中对关键内容进行分类。 它们可以在 Power BI Desktop（预览版）和 Power BI 服务中应用，这样就可以从你开始开发内容到通过实时连接从 Excel 访问敏感数据，都可以保护这些敏感数据。 当你以 .pbix 文件形式在 Desktop 和服务之间来回移动内容时，将保留敏感度标签。

在 Power BI 服务中，敏感度标签可应用于数据集、报表、仪表板和数据流。 如果标记的数据离开 Power BI（通过导出到 Excel、PowerPoint、PDF 或 .pbix 文件或通过其他支持的导出方案，如在 Excel 中分析或实时连接在 Excel 中的数据透视表），则 Power BI 会自动将标签应用于导出的文件，并根据标签的文件加密设置对其进行保护。 这样，即使你的敏感数据离开 Power BI，也能得到保护。

此外，可以在 Power BI Desktop 中将敏感度标签应用于 .pbix 文件，以确保数据和内容在 Power BI 外共享时是安全的（例如，这样只有组织内的用户才能打开已共享或附加在电子邮件中的机密 .pbix），甚至在将其发布到 Power BI 服务之前。 有关更多详细信息，请参阅[使用敏感度标签应用加密来限制对内容的访问](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide)。

应用于报表、仪表板、数据集和数据流的敏感度标签在 Power BI 服务中的许多地方可见。 报表和仪表板上的敏感度标签也在 Power BI iOS 和 Android 移动应用以及嵌入式视觉对象中可见。 在 Desktop 中，可以在状态栏中看到敏感度标签。

借助 Power BI 管理门户中提供的[保护指标报表](service-security-data-protection-metrics-report.md)，Power BI 管理员可完整查看 Power BI 租户中的敏感数据。 此外，Power BI 审核日志包含有关活动（如应用、删除和更改标签，以及查看报表、仪表板等）的敏感度标签信息，使 Power BI 和安全管理员能够查看敏感数据使用情况，以便监视和调查安全警报。

## <a name="important-considerations"></a>重要注意事项

在 Power BI 服务中，敏感度标签不影响对内容的访问。 对服务内容的访问完全由 Power BI 权限管理。 如果标签可见，则不会应用任何相关的加密设置（在 [Microsoft 365 安全中心](https://security.microsoft.com/)或 [Microsoft 365 合规中心](https://compliance.microsoft.com/)内配置）。 它们仅适用于通过支持的导出路径（如导出到 Excel、PowerPoint 或 PDF 文件和下载到 .pbix）离开服务的数据。

在 Power BI Desktop（预览版）中，具有加密设置的敏感度标签会影响对内容的访问。 根据 .pbix 文件上敏感度标签的加密设置，如果用户没有足够的[权限](#power-bi-desktop-preview)，将无法打开该文件。 此外，在 Desktop 中，当你保存工作时，你添加的任何敏感度标签及其关联的加密设置都将应用于保存的 .pbix 文件。

不在不支持的导出路径中应用敏感度标签和文件加密。 Power BI 管理员可以阻止从不支持的导出路径进行导出。

>[!NOTE]
> 有权访问报表的用户具有访问整个基础数据集的权限，除非[行级别安全性 (RLS)](./service-admin-rls.md) 限制其访问权限。 报表作者可使用敏感度标签对报表进行分类和标注。 如果敏感度标签具有保护设置，则当报表数据通过支持的导出路径（如导出到 Excel、PowerPoint 或 PDF，下载到 .pbix 和保存 (Desktop)）离开 Power BI 时，Power BI 将应用这些保护设置。 只有经过授权的用户才能打开受保护的文件。

### <a name="supported-export-paths"></a>支持的导出路径
以下导出路径当前支持将敏感度标签及其关联的保护应用于离开 Power BI 服务的数据：
* 导出到 Excel、PDF 文件（仅限服务）和 PowerPoint。
* Power BI 服务中的“在 Excel 中分析”，会触发通过实时连接到 Power BI 数据集来下载 Excel 文件。
* 通过实时连接到 Power BI 数据集的 Excel 中的数据透视表，适用于具有 M365 E3 及更高版本的用户。
* 下载到 .pbix（服务）

>[!NOTE]
>在 Power BI 服务中使用“下载 .pbix”时，如果下载的报表及其数据集具有不同的标签，则会将更严格的标签应用于 .pbix 文件。 

## <a name="how-sensitivity-labels-work-in-power-bi"></a>敏感度标签在 Power BI 中的工作原理

向 Power BI 内容和文件应用敏感度标签时，类似于对资源应用标记，这样做具有以下优点：
* 可自定义 - 可以为组织中不同级别的敏感内容创建类别，如个人、公共、一般、机密和高度机密。
* 明文 - 由于标签为明文形式，因此用户可以轻松地根据敏感度标签指南了解如何处理内容。
* 持久 - 向内容应用敏感度标签之后，在将内容导出到 Excel、PowerPoint 和 PDF 文件，下载到 .pbix 或保存（在 Desktop 中）时，将随内容一起导出标签，并成为应用和强制执行策略的基础。

以下是有关 Power BI 中的敏感度标签如何工作的快速示例。 下图显示了如何在 Power BI 服务中将敏感度标签应用于报表，然后如何将报表中的数据导出到 Excel 文件，最后如何在导出的文件中保留敏感度标签及其保护。

![显示应用程序和敏感度标签保留性的动态 GIF](media/service-security-sensitivity-label-overview/ApplyLabelandProtection.gif)

应用于内容的敏感度标签与内容一起保留和漫游，如同在整个 Power BI 中使用和共享一样。 可以使用此标签生成使用情况报表并查看敏感内容的活动数据。

## <a name="sensitivity-labels-in-power-bi-desktop-preview"></a>Power BI Desktop（预览版）中的敏感度标签

还可以在 Power BI Desktop 中应用敏感度标签。 这样就可以在首次开始开发内容时保护数据。 在 Desktop 中保存工作时，应用的敏感度标签以及任何关联的加密设置会应用于生成的 .pbix 文件。 如果标签具有加密设置，那么无论文件传输到哪里以及采用何种传输方式，它都会受到保护。 只有具有[必需的 RMS 权限](#power-bi-desktop-preview)的用户才能将其打开。

>[!NOTE]
>* 在此预览版本中，可能会有一些限制。 请参阅[限制](#limitations)。
>* 为了能够使用 Power BI Desktop 中的敏感度标签，你必须先[启用信息保护预览功能](service-security-apply-data-sensitivity-labels.md#apply-sensitivity-labels-in-power-bi-desktop-preview)，然后重启程序。 如果程序在重启后崩溃，则原因可能是你的计算机缺少必需的 Visual C++ 可再发行运行时库版本。 如果遇到此类崩溃，请访问 [Microsoft Visual C++ 2015 Redistributable Update 3 下载页面](https://www.microsoft.com/download/details.aspx?id=53587)，获取有关如何下载和安装更新的说明。 安装更新后，请尝试再次启动 Desktop。

如果在 Desktop 中应用敏感度标签，则在将工作发布到服务时，或者当你将该工作的 .pbix 文件上传到该服务时，标签将与数据一起传送到服务中。 在该服务中，标签将应用于通过文件获取的数据集和报表。 如果数据集和报表已经具有敏感度标签，则这些标签将被来自 Desktop 的标签覆盖。
 
如果上传之前从未发布到服务的 .pbix 文件，并且该文件具有与服务中已存在的报表或数据集相同的名称，则只有当上传者具有更改标签所需的 RMS 权限时，上传才会成功。

反之亦然 - 当你在服务中下载到 .pbix，然后将 .pbix 加载到 Desktop 时，该服务中的标签将应用于已下载的 .pbix 文件，并将其加载到 Desktop。 如果服务中的报表和数据集具有不同的标签，则这两者中更严格的标签将应用于下载的 .pbix 文件。

在 Desktop 中应用标签时，它会显示在状态栏中。

![Desktop 状态栏中敏感度标签的屏幕截图。](media/service-security-sensitivity-label-overview/sensitivity-label-in-desktop-status-bar.png)

[了解如何向 Power BI 内容和文件应用敏感度标签](./service-security-apply-data-sensitivity-labels.md)。


## <a name="sensitivity-label-inheritance-upon-creation-of-new-content"></a>创建新内容时敏感度标签的继承

在 Power BI 服务中创建新报表和仪表板时，它们会自动继承以前应用于父数据集或报表的敏感度标签。 例如，在具有“高度机密”敏感度标签的数据集上创建的新报表也会自动接收“高度机密”标签。

下图显示了数据集的敏感度标签如何自动应用于在该数据集上构建的新报表。

![显示敏感度标签继承的动态 GIF](media/service-security-sensitivity-label-overview/InheritanceUponCreation.gif)

>[!NOTE]
>如果出于某些原因而无法在新报表或仪表板上应用敏感度标签，则 Power BI 将不会阻止创建新项。

## <a name="sensitivity-labels-and-protection-on-exported-data"></a>导出的数据的敏感度标签和保护

将数据从 Power BI 导出到 Excel、PDF 文件（仅限服务）或 PowerPoint 文件时，Power BI 会自动对导出的文件应用敏感度标签，并根据标签的文件加密设置对其进行保护。 这样一来，无论敏感数据位于何处，都将受到保护。

从 Power BI 导出文件的用户有权根据敏感度标签设置访问和编辑该文件；他们不会获得该文件的所有者权限。

>[!NOTE]
>在 Power BI 服务中使用“下载 .pbix”时，如果下载的报表及其数据集具有不同的标签，则会将更严格的标签应用于 .pbix 文件。 

在将数据导出到 .csv 文件或任何其他不支持的导出路径时，不会应用敏感度标签和保护。

对导出的文件应用敏感度标签和保护不会向文件添加内容标记。 但是，如果标签配置为应用内容标记，则在 Office 桌面应用中打开文件时，Azure 信息保护统一标签客户端会自动应用这些标记。 在为桌面、移动或 Web 应用使用内置标签时，不会自动应用内容标记。 有关更多详细信息，请参阅 [Office 应用何时应用内容标记和加密](/microsoft-365/compliance/sensitivity-labels-office-apps#when-office-apps-apply-content-marking-and-encryption)。

如果在将数据导出到文件时无法应用标签，导出将失败。 要检查导出失败的原因是否为无法应用标签，请在标题栏的中心单击报表或仪表板名称，然后在打开的信息下拉菜单中查看是否显示“无法加载敏感度标签”。 如果安全管理员取消发布或删除了应用的标签，或出现了临时系统问题，则可能会发生这种情况。

## <a name="sensitivity-label-inheritance-in-analyze-in-excel"></a>“在 Excel 中分析”的敏感度标签继承

当你通过实时连接到 Power BI 数据集在 Excel 中创建数据透视表（可以从 Power BI 通过[在 Excel 中分析](../collaborate-share/service-analyze-in-excel.md)或从 [Excel](https://support.microsoft.com/office/create-a-pivottable-from-power-bi-datasets-31444a04-9c38-4dd7-9a45-22848c666884?ui=en-US&rs=en-US&ad=US) 执行此操作）时，将继承数据集的敏感度标签，并将其应用于 Excel 文件以及任何关联的保护。 如果数据集上的标签稍后更改为更具限制性的标签，则会在数据刷新时自动更新应用于链接的 Excel 文件的标签。

![Excel 的屏幕截图，显示通过实时连接从数据集继承的敏感度标签。](media/service-security-sensitivity-label-overview/live-connection-inheritance.png)
 
Excel 中手动设置的敏感性标签不会由数据集的敏感度标签自动覆盖。 相反，横幅会通知你数据集具有敏感度标签，并建议你应用该标签。

>[!NOTE]
>如果数据集的敏感度标签比 Excel 文件的敏感度标签限制少，则不会发生标签继承或更新。 Excel 文件永远不会继承限制性较低的敏感度标签。

## <a name="sensitivity-label-persistence-in-embedded-reports-and-dashboards"></a>嵌入式报表和仪表板中的敏感度标签保留性

可在商业应用程序（如 Microsoft Teams 和 SharePoint）或组织的网站中嵌入 Power BI 报表、仪表板和视觉对象。 如果嵌入的视觉对象、报表或仪表板应用了敏感度标签，则该敏感度标签会显示在嵌入视图中，并且在将数据导出到 Excel 时，该标签及其保护将保持不变。

![SharePoint Online 中嵌入的报表的屏幕截图](media/service-security-sensitivity-label-overview/embedded-report-sensitivity-label.png)

支持以下嵌入方案：
* [为组织嵌入内容](../developer/embedded/embed-sample-for-your-organization.md)
* Microsoft 365 应用（例如 [Teams](../collaborate-share/service-embed-report-microsoft-teams.md) 和 [SharePoint](../collaborate-share/service-embed-report-spo.md)）
* [安全 URL 嵌入](../collaborate-share/service-embed-secure.md)（从 Power BI 服务嵌入） 

## <a name="sensitivity-labels-in-the-power-bi-mobile-apps"></a>Power BI 移动应用中的敏感度标签

可在 Power BI 移动应用中的报表和仪表板上查看敏感度标签。 报表或仪表板名称附近的图标指示它具有敏感度标签，并且可在报表或仪表板的信息框中找到标签的类型及其说明。

![移动应用中敏感度标签的屏幕截图](media/service-security-sensitivity-label-overview/mobile-app-sensitivity-label2.png)

## <a name="supported-clouds"></a>受支持的云
敏感度标签仅在全局（公有）云的租户中受支持，而在云（如国家/地区云）的租户中不受支持。

## <a name="licensing-and-requirements"></a>授权和要求

请参阅[授权和要求](service-security-enable-data-sensitivity-labels.md#licensing-and-requirements)。

## <a name="sensitivity-label-creation-and-management"></a>创建和管理敏感度标签

在 [Microsoft 365 安全中心](https://security.microsoft.com/)或 [Microsoft 365 合规中心](https://compliance.microsoft.com/)创建和管理敏感度标签。

要在任一中心访问敏感度标签，请导航到“分类”>“敏感度标签”。 这些敏感度标签可由多个 Microsoft 服务（例如 Azure 信息保护、Office 应用和 Office 365 服务）使用。

>[!Important]
> 如果你的组织使用 Azure 信息保护敏感度标签，则需要将这些标签[迁移](/azure/information-protection/configure-policy-migrate-labels)到前面列出的服务之一，以便在 Power BI 中使用它们。

## <a name="limitations"></a>限制

### <a name="general"></a>常规

* 建议不允许用户在 Power BI 中应用父标签（标签只有在具有子标签时才会被视为父标签）。 如果对内容应用了父标签，则无法将数据从该内容导出到文件（Excel、PowerPoint 和 PDF）。 请参阅[子标签（分组标签）](/microsoft-365/compliance/sensitivity-labels#sublabels-grouping-labels)。

* 模板应用不支持数据敏感度标签。 模板应用创建者设置的敏感度标签在提取和安装应用时被删除，应用使用者添加到已安装模板应用项目的敏感度标签在更新应用时丢失（重置为无）。

* 在 Power BI 服务中，如果数据集的标签已从标签管理中心删除，则无法导出或下载该数据。 在 Excel 中分析中，将发出警告，并将数据导出到没有敏感度标签的 .odc 文件。 在 Desktop 中，如果 .pbix 文件具有此类无效标签，你将无法保存文件。

* Power BI 不支持[请勿转发](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions)、[用户定义](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions)和 [HYOK](/azure/information-protection/configure-adrms-restrictions) 这三种保护类型的敏感度标签。 “请勿转发”和“用户定义”保护类型引用 [Microsoft 365 安全中心](https://security.microsoft.com/)或 [Microsoft 365 合规中心](https://compliance.microsoft.com/)内定义的标签。

### <a name="power-bi-service"></a>Power BI 服务

* 敏感度标签只能应用于仪表板、报表、数据集和数据流。 它们当前不可用于[分页报表](../paginated-reports/report-builder-power-bi.md)和工作簿。

* Power BI 资产上的敏感度标签在工作区列表、世系、收藏夹、最近使用和应用视图中可见。这些标签目前在“与我共享”视图中不可见。 但请注意，应用于 Power BI 资产的标签（即使不可见）将始终保留在导出到 Excel、PowerPoint 和 PDF 文件中的数据上。

### <a name="power-bi-desktop-preview"></a>Power BI Desktop（预览版）

* 受保护的 .pbix 文件只能由作为此文件的 RMS 所有者的用户（最初将标签应用于该文件的用户）打开和/或发布，也可以由具有相关标签的[完全控制和/或导出使用权限](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide)的用户打开和/或发布。 RMS 所有者具有完全控制权限，永远不会被锁定。[查看更多详细信息](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner)

* 如果尚未将应用于 .pbix 文件的标签发布到 Microsoft 365 安全中心或 Microsoft 365 合规中心的用户，则用户将无法在 Desktop 中保存该文件。

* Power BI Desktop 用户可能会在 Internet 连接丢失时（例如在脱机后）保存工作时遇到问题。 在没有 Internet 连接的情况下，与敏感度标签和权限管理相关的一些操作可能无法正确完成。 在这种情况下，建议重新联机，然后再次尝试保存。

* 如果你创建了一个大型模型，并且生成的受保护的 .pbix 文件非常大（超过 2 GB），则在尝试保存或打开该文件时，它可能会崩溃。 若要解决此问题，请考虑从 .pbix 文件中删除保护，并在文件发布到 Power BI 服务后重新应用保护。

    通常，当你使用应用加密的敏感度标签保护文件时，最好也使用其他加密方法，例如页面文件加密、NTFS 加密、bitlockers、反恶意软件等。

* 临时文件不加密。

* 仅当获取数据位于本地时，才能安全上传。 无法上传来自联机服务（例如 SharePoint Online 或 OneDrive for Business）的受保护文件。 对于受保护的文件，你可以将其从本地设备上传，或者先删除 Power BI Desktop 中的文件标签，然后通过其中一个联机服务上传。

* 导出到 PDF 不支持敏感度标签。 如果将具有敏感度标签的文件导出为 PDF，则 PDF 不会收到标签，并且不会应用任何保护。

* Power BI Desktop 中的信息保护不支持 B2B 和多租户方案。

## <a name="next-steps"></a>后续步骤

本文概述了 Power BI 中的数据保护。 以下文章提供了有关 Power BI 中的数据保护的进一步详细信息。 

* [在 Power BI 中启用敏感度标签](service-security-enable-data-sensitivity-labels.md)
* [如何在 Power BI 中应用敏感度标签](service-security-apply-data-sensitivity-labels.md)
* [在 Power BI 中使用 Microsoft Cloud App Security 控件](service-security-using-microsoft-cloud-app-security-controls.md)
* [保护指标报表](service-security-data-protection-metrics-report.md)
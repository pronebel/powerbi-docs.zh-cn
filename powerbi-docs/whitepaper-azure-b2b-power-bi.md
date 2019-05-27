---
title: Power BI 将内容分发给外部来宾用户使用 Azure Active Directory B2B
description: 介绍如何使用 Azure Active Directory B2B 将 Power BI 分发给外部来宾用户的白皮书
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 79b8ae80413cc54b065d12bf36ccb1651a670812
ms.sourcegitcommit: ec5b6a9f87bc098a85c0f4607ca7f6e2287df1f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051601"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Power BI 将内容分发给外部来宾用户使用 Azure Active Directory B2B

**摘要：** 这是一本技术白皮书概述了如何将内容分发到组织外的用户使用的 Azure Active Directory 企业到企业 (Azure AD B2B) 集成。

**编写器：** Lukasz Pawlowski，人： Kasper de Jonge

**技术评审人员：** Adam Wilson、 Sheng Liu、 Qian Liang、 Sergei Gundorov、 Jacob Grimm、 Adam Saxton、 Maya Shenhav、 Nimrod Shalit，Elisabeth Olson

> [!NOTE]
> 可以从浏览器中选择“打印”，然后选择“另存为 PDF”文件，以保存或打印此白皮书。

## <a name="introduction"></a>简介

Power BI 为组织提供了其业务的 360 度视图，并让每个人都在这些组织中使用数据的明智决策。 许多这些组织都有与外部合作伙伴、 客户端和合约商强和受信任的关系。 这些组织需要提供安全访问 Power BI 仪表板和报表复制到这些外部合作伙伴中的用户。

使用 power BI 集成[Azure Active Directory 企业到企业 (Azure AD B2B)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)安全地分发的 Power BI 为来宾用户组织 – 外部内容时仍保持控制和管理访问权限内部数据。

本白皮书的详细介绍了所有需要了解与 Azure Active Directory B2B 的 Power BI 的集成。 我们将介绍其最常见用例、 安装、 许可和行级别安全性。

> [!NOTE]
> 在本白皮书整个我们请参阅为 Azure AD 的 Azure Active Directory 和 Azure Active Directory 作为 Azure AD B2B 企业到企业。

## <a name="scenarios"></a>方案

Contoso 是汽车制造商，适用于许多不同的供应商提供的所有组件、 清单和服务运行其生产操作所需的人员。 Contoso 希望简化其供应链后勤和计划，以使用 Power BI 监视其供应链的关键性能指标。 Contoso 想要使用外部供应链合作伙伴 analytics 共享安全且易于管理的方式。

Contoso 可以启用以下为使用 Power BI 和 Azure AD B2B 的外部用户体验。

### <a name="ad-hoc-per-item-sharing"></a>每个项共享的临时

Contoso 可与供应商生成任何辐射源为 Contoso 的汽车。 通常情况下，它们需要优化任何辐射源使用所有 Contoso 的汽车中的数据的可靠性。 Contoso 处的分析师使用 Power BI 与供应商的一名工程师共享辐射设备可靠性报表。 工程师将收到一封电子邮件包含用于查看报表的链接。

上文所述，这种临时共享企业用户可以按需执行。 通过 Power BI 发送到外部用户的链接是 Azure AD B2B 邀请链接。 外部用户打开该链接，系统会要求其加入 Contoso 的 Azure AD 的组织中的来宾用户。 接受邀请后，链接将打开特定报表或仪表板。 Azure Active Directory 管理员委托邀请到组织外部用户的权限，并选择此文档的管理部分中所述，用户在接受邀请后，这些用户可以执行。 Contoso 分析师可以邀请来宾用户，只是因为 Azure AD 管理员允许该操作和 Power BI 管理员允许用户邀请来宾查看 Power BI 租户设置中的内容。

![邀请来宾到 Power BI 中使用 AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. 在开始使用 Contoso 内部用户与外部用户共享仪表板或报表。 如果外部用户不是已来宾在 Contoso 的 Azure AD 中，受邀。 一封电子邮件发送到其电子邮件地址包含邀请到 Contoso 的 Azure AD
2. 接收方接受邀请到 Contoso 的 Azure AD 和添加为来宾用户在 Contoso 的 Azure AD。
3. 接收方重定向到 Power BI 仪表板、 报表或应用程序，以便用户只能阅读。

由于业务用户在 Contoso 中的执行邀请操作根据需要为他们的业务目的，流程会被视为 ad hoc。 每个项共享都是外部用户可以访问的单个链接来查看内容。

一旦已邀请外部用户访问 Contoso 资源，影子帐户可能在 Contoso Azure AD 中创建它们和他们不需要再次邀请。  第一次尝试访问 Contoso 资源，例如 Power BI 仪表板，它们经过许可过程，兑换邀请。  如果他们未完成同意的情况下，它们不能访问任何 Contoso 的内容。  如果它们具有在兑换其邀请通过提供的原始链接时遇到问题，Azure AD 管理员可以重新发送才能兑换的特定邀请链接。

### <a name="planned-per-item-sharing"></a>每个项共享计划

若要执行的任何辐射源可靠性分析一个分包商的 Contoso 工作。 分包商具有一组 10 人需要访问 Contoso 的 Power BI 环境中的数据。 Contoso Azure AD 管理员是涉及邀请所有用户并处理任何添加/更改为在分包商更改的人员。 为在分包商的所有员工，Azure AD 管理员创建安全组。 使用安全组，Contoso 的员工可以轻松地管理对报表的访问并确保所有必需的分包商人员有权访问所有所需的报告、 仪表板和 Power BI 应用。 Azure AD 管理员还可以避免在涉及在邀请过程中完全通过选择委派邀请到受信任的员工在 Contoso 或分包商权限，以确保及时人员管理。

某些组织需要更好地控制添加外部用户时，要邀请的外部组织中的多个用户或多个外部组织。 在这些情况下，计划内共享可用来管理共享，以强制实施组织的策略，以及甚至委派到受信任的个人可以邀请并管理外部用户的权限的规模。 Azure AD B2B 支持计划性的邀请直接发送[从 IT 管理员在 Azure 门户](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)，或通过[PowerShell 中使用的邀请管理器 API](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api)其中的一组用户也可以在一个接受邀请操作。 使用的计划邀请的方法，组织可以控制谁可以邀请用户，并实现审批过程。 高级 Azure AD 功能，如动态组可以轻松地自动维护安全组成员身份。


![控制哪些宾客所见内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. 与 IT 管理员邀请来宾用户手动或通过 API 提供的 Azure Active Directory 过程星
2. 用户接受邀请到组织。
3. 一旦用户接受邀请，Power BI 中的用户可以与外部用户或安全组中共享报表或仪表板。 就像在 Power BI 中共享的正则外部用户会收到包含项的链接的电子邮件。
4. 当该链接，其在其目录中的身份验证传递给 Contoso 的外部用户访问的 Azure AD，用于获取到 Power BI 内容的访问权限。

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc 或计划共享 Power BI 应用

Contoso 有一组报表和仪表板，它们需要与一个或多个供应商共享。 若要确保所有所需的外部用户有权访问此内容，它被打包为 Power BI 应用。 直接到应用访问列表或通过安全组或者添加外部用户。 Contoso 的人员然后可以将应用程序 URL 发送到所有外部用户，例如在电子邮件中。 当外部用户打开链接时，他们看到在单个的所有内容轻松地导航体验。

使用 Power BI 应用，可以轻松为 Contoso，若要为其供应商构建 BI 门户。 单个访问列表控制对减少浪费的时间检查和设置项目级别权限的所有所需内容的访问。 Azure AD B2B 维护使用供应商的本机标识，因此用户无需其他登录凭据的安全访问权限。 如果使用安全组使用计划的邀请，对应用程序访问管理人员旋转到或移出项目如简化。 手动或使用安全中的成员身份进行分组[动态组](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups)，以便从供应商的所有外部用户自动添加到适当的安全组。


![使用 AAD 内容控件](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. 通过用户邀请到 Contoso 的 Azure AD 组织通过 Azure 门户或 PowerShell 来启动进程
2. 用户可以在 Azure AD 中添加到用户组。 可以使用静态或动态用户组，但动态组有助于减少手动工作。
3. 外部用户被授予访问权限的用户组通过在 Power BI 应用。 应用 URL 应直接发送到外部用户或在站点上放置他们有权访问。 Power BI，你能够最大努力将包含应用链接的电子邮件发送到外部用户，但不能将发送到通过用户组管理的所有外部用户时使用的用户组的成员身份可以更改，Power BI。
4. 当外部用户访问 Power BI 应用的 URL 时，它们通过 Contoso 的 Azure 身份验证 AD 中，为用户安装应用和用户可以看到所有包含的报表和应用程序中的仪表板。

应用还具有一种独特的功能，它允许应用程序作者安装自动为该用户，应用程序，因此当用户登录时，它才可用。 此功能只会自动安装的外部用户已属于 Contoso 的组织在发布或更新应用程序的时间。 因此，它使用计划性的邀请方法时，最好使用并依赖于应用程序正在发布或更新后将用户添加到 Contoso 的 Azure AD。 外部用户始终可以安装使用的应用链接的应用。

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>注释和跨组织订阅内容

Contoso 继续使用其分包商或供应商，如外部工程师需要与 Contoso 的分析人员紧密合作。 Power BI 提供了几个协作功能，可帮助用户就可以使用的内容进行沟通。 仪表板注释 （和即将报告注释），用户可以讨论数据点他们看到并与其报表作者提出的问题。

目前，外部来宾用户可在注释中加入离开注释，并读取回复。 但是，与内部用户，不同的来宾用户不能为@mentioned并不会收到通知它们已接收一条注释。 在撰写本文之际，来宾用户不能使用 Power BI 中的订阅功能。 将在即将发布的版本中，提升这些限制，并且来宾用户将收到一封电子邮件时注释@mentions它们，或当订阅传递到其电子邮件，其中包含指向 Power BI 中的内容。

### <a name="access-content-in-the-power-bi-mobile-apps"></a>在 Power BI 移动应用中访问内容

在即将发布的版本，当 Contoso 的用户使用其外部来宾对应项，共享报表或仪表板时 Power BI 将发送电子邮件通知来宾。 当来宾用户打开报表或其移动设备上的仪表板的链接时，内容将打开其设备上的本机 Power BI 移动应用中，如果它们安装。 然后，来宾用户将能够在外部的租户中，并返回到其自己从其宿主租户中的内容与之共享的内容之间导航。

> [!NOTE]
> 来宾用户不能打开 Power BI 移动应用并立即导航到外部的租户，必须启动时出现外部租户中的项的链接。 中介绍了常见的解决方法[分发到父组织的 Power BI 中的内容的链接](#distributing-links-to-content-in-the-parent-organizations-power-bi)本文档后面的部分。

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>跨组织编辑和管理 Power BI 内容

Contoso 及其供应商和分包商越来越多地紧密配合运行。 通常分包商处的分析师需要其他度量值或数据可视化效果添加到 Contoso 具有与之共享的报表。 数据应驻留在 Contoso 的 Power BI 租户中，但外部用户应该能够对其进行编辑，创建新内容，以及甚至将其分发给适当的人员。

Power BI 提供了一个选项，使**外部来宾用户可以编辑和管理内容**组织中。 默认情况下，外部用户具有只读面向消耗的体验。 但是，此新设置，Power BI 管理员选择的外部用户可以编辑和管理其自己的组织中的内容。 后允许，外部用户可以编辑报表、 面板、 发布或更新应用，在工作区中工作并连接到他们有权使用的数据。

此方案中所述在部分使外部用户可以编辑和管理 Power BI 中本文档后面的内容的详细信息。

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>组织使用 Power BI 和 Azure AD B2B 的关系

Power BI 的所有用户都都对组织内部，时无需使用 Azure AD B2B。 但是后两个或多个组织想要对数据和见解进行协作，, Power BI 支持 Azure AD b2b 使其更轻松且经济高效执行此操作。

下面是通常会遇到非常适合用于 Power BI 中的 Azure AD B2B 样式跨组织协作的组织结构。 Azure AD B2B 适用于大多数情况下，但在某些情况下常见介绍了本文档末尾的替代方法是值得考虑。

### <a name="case-1-direct-collaboration-between-organizations"></a>案例 1:组织之间的直接协作

使用其辐射设备供应商 Contoso 的关系是组织之间的直接协作的一个示例。 由于 contoso 有相对较少的用户和其供应商需有权辐射设备可靠性的信息，使用 Azure AD B2B 基于外部共享是理想之选。 它是简单易用和易于管理。 这也是一种常见模式的咨询服务可能需要生成内容的组织一位顾问。

![组织之间共享](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


通常，这种共享发生最初使用每个项共享的 Ad hoc。 但是，随着团队扩展或同时更深入的关系，每个项共享计划的方法变得的首选的方法，以减少管理开销。 此外，Ad hoc 或计划内共享的 Power BI 应用、 注释和跨组织订阅内容，移动应用中的内容的访问权限可以进入 play，和跨组织编辑和管理 Power BI 内容。 重要的是，如果这两个组织的用户在其各自组织中的 Power BI Pro 许可证，他们可以在彼此的 Power BI 环境中使用这些 Pro 许可证。 这提供了有利许可，因为邀请方组织可能不需要支付的外部用户的 Power BI Pro 许可证。 在本文档后面的许可部分中的更详细地对此进行了讨论。

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>案例 2:父及其分公司或分支机构

某些组织结构是更复杂，其中包括部分或全部控股的子公司、 附属的公司或托管的服务提供商的关系。 这些组织有一个父组织控股公司，如，但基础的组织运行以自主，有时在不同区域的要求。 这会导致每个组织具有其自己的 Azure AD 环境和单独的 Power BI 租户。

![使用分支机构](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


在此结构中的父组织通常需要分发到其子公司标准化的见解。 通常，这种共享发生使用临时或计划的共享 Power BI 应用方法，因为这样标准化权威内容分发到的广泛的受众如下图中所示。 在实践中使用本文档前面所述的所有方案的组合。

![组合方案](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


这遵循以下过程：

1. 从每个分支机构的用户都邀请到 Contoso 的 Azure AD
2. 然后发布的 Power BI 应用，授予这些用户能够访问所需的数据
3. 最后，用户打开通过它们已被赋予才能查看的报表的链接应用

多项重要挑战所面临的此结构中的组织：

- 如何将分发到父组织的 Power BI 中的内容的链接
- 如何允许分公司的用户访问托管的父组织的数据源

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>将分发到父组织的 Power BI 中的内容的链接

这三种方法通常用于将分发内容的链接。 第一个和大多数基本身份验证是将链接发送给该应用到所需的用户或将其放在 SharePoint Online 站点从其可以打开该文件中。 然后，用户可以添加书签所需的数据更快地访问其浏览器中的链接。

第二种方法依赖于跨组织编辑和管理 Power BI 内容功能。 父组织允许用户从分支机构访问其 Power BI，并控制他们可以访问通过权限。 这可让访问 Power BI 主页位置从分支机构用户将看到与他们共享的父组织的租户中的内容的完整列表。 然后向父组织的 Power BI 环境 URL 提供给分支机构的用户。

最后一种方法使用在每个分支机构的 Power BI 租户中创建的 Power BI 应用。 Power BI 应用包括使用仪表板[配置为使用外部链接选项磁贴](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink)。 当用户按该磁贴时，他们所转到相应的报表、 仪表板中或在父组织的 Power BI 中的应用。 此方法具有附加的优势应用可以为分支机构中的所有用户自动安装，而是提供给他们只要登录到其自己的 Power BI 环境。 添加了此方法的优点是它非常适用于本机可以打开该链接在 Power BI 移动应用。 您还可以将这与第二种方法中，若要启用 Power BI 环境之间轻松切换。

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>允许附属用户访问托管的父组织的数据源

通常在分支机构的分析人员需要创建其自己的分析使用提供的父组织的数据。 在这种情况下，通常云的数据源可用于解决难题。

第一种方法利用[Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview)构建为跨父级和其子公司下图所示的分析师需求提供服务的企业级数据仓库。 Contoso 可以承载数据，并使用功能，如行级别安全性，以确保每个分支机构中的用户可以访问他们的数据。 在每个组织的分析师可以访问数据仓库通过 Power BI Desktop，并将生成分析发布到其各自的 Power BI 租户。

![如何使用 Power BI 租户共享发生](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


第二种方法利用[Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)构建的关系数据仓库提供对数据的访问。 此工作方式类似于 Azure Analysis Services 的方法，但一些功能，如行级别安全性可能难以部署和维护跨子公司。

更复杂的方法也可使用，但是上述的到目前为止最常见。

### <a name="case-3-shared-environment-across-partners"></a>案例 3:在合作伙伴之间的共享的环境

Contoso 可以输入与竞争对手共同上进行构建一辆汽车共享程序集行，但将车辆下不同品牌或不同区域中的合作关系。 这在组织中需要广泛协作和 co-ownership 的数据、 智能和分析。 此结构也很常见咨询服务行业中其中的顾问团队可能会执行基于项目的分析操作的客户端。

![在合作伙伴之间的共享的环境](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



在实践中，这些结构很复杂，如下图中所示，需要维护的人员。 为提高效率此结构依赖于跨组织编辑和管理 Power BI 内容功能，因为这样组织能够重复使用其各自的 Power BI 租户的已购买 Power BI Pro 许可证。

![许可证和共享的组织的内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



若要建立共享的 Power BI 租户，Azure Active Directory 需要创建并且至少一个 Power BI Pro 的用户帐户需要为该 active directory 中的用户购买。 此用户邀请到共享的组织所需的用户。 重要的是，在此方案中，Contoso 的用户被视为外部用户时才进行操作。 共享组织的 Power BI 中。

过程如下所示：

1. 共享组织建立为新的 Azure Active Directory 和新的组织中创建至少一个用户帐户。 该用户应具有分配给他们的 Power BI Pro 许可证。
2. 然后，此用户建立 Power BI 租户，并邀请从 Contoso 和合作伙伴组织所需的用户。 用户还建立任何共享的数据资产，例如 Azure Analysis Services。 Contoso 和合作伙伴的用户可以作为来宾用户访问共享的组织的 Power BI。 如果允许编辑和管理 Power BI 中的内容的外部用户可以使用 Power BI 主页、 使用工作区中上, 传或编辑内容和共享报表。 通常情况下，存储和共享组织中访问所有共享的资产。
3. 具体取决于如何双方均同意进行协作，就可以为每个组织来开发自己的专有数据和分析使用共享的数据仓库资产。 它们可以将分发到其各自的内部用户使用其内部的 Power BI 租户。

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>情形 4:分发到数百或数千个外部合作伙伴

虽然 Contoso 创建一个供应商为辐射设备可靠性报表，但现在 Contoso 想要为数百个供应商创建一组标准化的报表。 这样，Contoso，以确保所有供应商具有要进行改进或修复生产缺陷所需的分析。

![分发到许多合作伙伴](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


当组织需要将分发标准化的数据和许多的外部用户/组织的见解时，它们可以使用临时或计划共享 Power BI 应用方案的生成 BI 门户快速且无广泛的开发成本。 案例研究中介绍了构建门户使用 Power BI 应用的过程：构建 BI 门户中使用 Power BI + Azure AD B2B – 分步本文档后面的说明。

当组织尝试与使用者，共享见解，尤其是在想要使用 Power BI Azure B2C 时，这种情况下的一个常见变体。 Power BI 本身不支持 Azure B2C。 如果要评估这种情况下的选项，请考虑替代选项 2 中常见的替代方法在本文档后面部分。

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>案例研究：构建 BI 门户中使用 Power BI + Azure AD B2B – 的分步说明

Power BI 与 Azure AD B2B 集成为 Contoso 提供了无缝、 轻松的方式为来宾用户提供对其 BI 门户的安全访问。 Contoso 可以设置这三个步骤：

![构建一个门户](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. 在 Power BI 中创建 BI 门户

    Contoso 的第一个任务是在 Power BI 中创建其 BI 门户。 Contoso 的 BI 门户将包含的一系列专门构建的仪表板和报表，将可用于向许多内部和来宾用户。 用于 Power BI 中执行此操作的推荐的方法是构建的 Power BI 应用。 详细了解如何[Power BI 中的应用](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/)。

- Contoso 的 BI 团队在 Power BI 中创建应用工作区

    ![应用工作区](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- 其他作者添加到工作区

    ![添加作者](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- 在工作区中创建内容

    ![创建工作区中的内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    现在，内容创建应用工作区中，Contoso 就可以邀请来宾用户在伙伴组织中的使用此类内容。

2. 邀请来宾用户

    有两种方法，contoso 来宾用户邀请到 Power BI 中其 BI 门户：

    * 计划性的邀请
    * 临时邀请

    **计划性的邀请**

    在此方法中，Contoso 邀请到提前其 Azure AD 来宾用户，然后将分发给他们的 Power BI 内容。 Contoso 可以邀请来宾用户从 Azure 门户或使用 PowerShell。 下面是在 Azure 门户中的来宾用户邀请的步骤：

    - Contoso 的 Azure AD 管理员身份导航到**Azure 门户 > Azure Active Directory > 用户和组 > 所有用户 > 新来宾用户**

    ![来宾用户](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - 添加来宾用户邀请消息，然后单击邀请

    ![添加邀请](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > 若要邀请来宾用户从 Azure 门户，你需要 Azure Active directory 租户的管理员。

    如果 Contoso 想要邀请多个来宾用户，他们可以使用 PowerShell 来完成。 Contoso 的 Azure AD 管理员将 CSV 文件中存储所有来宾用户的电子邮件的地址。 以下是[Azure Active Directory B2B 协作代码和 PowerShell 示例](https://docs.microsoft.com/azure/active-directory/b2b/code-samples)和说明。

    后邀请来宾用户接收邀请链接的电子邮件。

    ![邀请链接](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    一旦来宾用户单击链接时，他们可以访问 Contoso Azure AD 租户中的内容。

    > [!NOTE]
    > 可以使用 Azure AD 品牌功能，如所述的邀请电子邮件的布局更改[此处](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email)。


    **临时邀请**

    如果 Contoso 不知道它想要提前邀请的来宾用户？ 或者，如果在 Contoso 中的分析人员 BI 门户中创建想要将内容分发到来宾用户自己？ 我们还支持这种情况下在 Power BI 中使用临时邀请。

    分析师只是可以将外部用户添加到应用程序的访问列表，它们在发布时。 来宾用户获取邀请并接受它们，它们会自动重定向到 Power BI 内容。

    ![添加外部用户](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > 已邀请需要只在首次外部用户邀请到你的组织。


3. 分发内容

    现在，Contoso 的 BI 团队 BI 门户中创建和邀请的来宾用户，他们可以将其门户为最终用户分发由向来宾用户提供访问该应用程序并将其发布。 Power BI 自动完成的之前添加到 Contoso 租户的来宾用户的名称。 此外可以在这里添加即席向用户发送邀请其他来宾。

    > [!NOTE]
    > 如果使用安全组来管理外部用户对应用程序的访问，使用计划的邀请的方法，并直接与每个外部用户都必须访问该共享的应用链接。 否则，外部用户可能无法安装或查看从应用程序中的内容。 _

    来宾用户获得包含到应用的链接的电子邮件。

    ![电子邮件邀请链接](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    单击此链接，要求来宾用户使用其自己组织的标识进行身份验证。

    ![登录页](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    在成功身份验证，系统会将它们重定向到 Contoso 的 BI 应用。

    ![请参阅共享的内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    来宾用户随后可以通过单击电子邮件中的链接或书签链接获取到 Contoso 的应用。 Contoso 还可更加轻松来宾用户通过将此链接添加到来宾用户已在使用任何现有 extranet 门户。

4. 后续步骤

    使用 Power BI 应用和 Azure AD B2B，Contoso 就能够快速创建用于其供应商的 BI 门户中的无代码方法。 这极大地简化将分发给需要它的所有供应商的标准化的分析。

    尽管该示例显示了单一的常见报表如何可能被分散在供应商之间，Power BI 能做到所示。 若要确保每个伙伴会看到仅与自己相关的数据，会将行级别安全性添加轻松到的报表和数据模型。 在本文档后面的外部合作伙伴部分的数据安全介绍此过程的详细信息。

    通常各个报表和仪表板需要嵌入到现有的门户。 这还可重复使用的许多技术示例所示。 但是，在这些情况下可能更轻松地嵌入报表或直接从工作区的仪表板。 邀请并将分配的安全权限的过程需要用户保持不变。

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>实质上：从能够访问 Contoso 的租户中的 Power BI 内容 Supplier1 Lucy 是什么？

既然我们已了解如何 Contoso 是能够无缝 Power BI 将内容分发到伙伴组织中的来宾用户，让我们看看其工作原理。

当 Contoso 受邀[ lucy@supplier1.com ](mailto:lucy@supplier1.com)到其目录中，Azure AD 之间创建链接[ Lucy@supplier1.com ](mailto:Lucy@supplier1.com)和 Contoso Azure AD 租户。 此链接可让 Azure AD 知道，Lucy@supplier1.com可以访问 Contoso 租户中的内容。

当 Lucy 尝试访问 Contoso 的 Power BI 应用时，Azure AD 验证 Lucy 可以访问 Contoso 租户，然后即可提供 Power BI 指示 Lucy 向 Contoso 租户中的内容访问进行身份验证的令牌。 Power BI 使用此令牌以授权，并确保 Lucy 有权访问 Contoso 的 Power BI 应用。

![验证和授权](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Power BI 与 Azure AD B2B 集成适用于所有业务电子邮件地址。 如果用户不具有 Azure AD 标识，它们可能会提示创建一个。 下图显示了详细的流：

![集成流图表](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


非常重要，识别将使用或在外部当事方中创建的 Azure AD 帐户的 Azure AD 中，这将使它可能 Lucy 可以使用自己的用户名和密码，并且自己的凭据将自动停止工作，在其他租户每当她当她的组织还使用 Azure AD 时，离开了公司。

## <a name="licensing"></a>许可

Contoso 可以选择三种方法之一向许可证的来宾用户从供应商和合作伙伴组织有权访问 Power BI 内容。

> [!NOTE]
> _Azure AD B2B 的免费层就足以使用 Power BI 与 Azure AD B2B。一些高级的 Azure AD B2B 功能，如动态组需要额外的许可。请参阅其他信息的 Azure AD B2B 文档：_ [_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>方法 1:Contoso 使用 Power BI Premium

使用此方法时，Contoso 购买 Power BI Premium 容量，并将其 BI 门户网站的内容分配给此容量。 这允许合作伙伴组织中的来宾用户访问 Contoso 的 Power BI 应用，且无需任何 Power BI 许可证。

外部用户也要进行使用 Power BI Premium 中的内容时，向 Power BI 中的"免费"用户提供唯一的体验的消耗。

Contoso 还可以利用其加快的刷新速度、 专用的容量，等大型模型大小的应用程序的其他 Power BI premium 功能。

![其他功能](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>方法 2:Contoso 为来宾用户分配 Power BI Pro 许可证

使用此方法时，Contoso pro 将许可证分配给来宾用户从合作伙伴组织 – 这可以从 Contoso 的 Microsoft 365 管理中心内完成。 这样，合作伙伴组织中的来宾用户访问 Contoso 的 Power BI 应用，而无需购买许可证本身。 这可以是适用于与所在组织尚不采用 Power BI 的外部用户共享。

> [!NOTE]
> _仅当他们访问 Contoso 租户中的内容时，Contoso 的 pro 许可证适用于来宾用户。Pro 许可证启用不是在 Power BI Premium 容量中的内容的访问权限。但是，使用 Pro 许可证的外部用户并默认情况下限制为使用唯一体验。这可以通过使用中所述的方法是更改__使外部用户能够编辑和管理 Power BI 中的内容__本文档后面的部分。_

![许可证信息](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>方法 3:来宾用户携带自己的 Power BI Pro 许可证

使用此方法时，供应商 1 将 Power BI Pro 许可证分配给 Lucy。 然后，她可以访问 Contoso 的 Power BI 应用与此许可证。 由于访问外部的 Power BI 环境时，Lucy 可以从她自己的组织使用她的 Pro 许可证，这种方法有时称为_自带许可_(BYOL)。 如果这两个组织使用的 Power BI，这提供了更有利的许可的整体分析解决方案，并将许可证分配给外部用户的开销降至最低。

> [!NOTE]
> _提供给 Lucy 供应商 1 pro 许可证适用于其中 Lucy 是来宾用户的任何 Power BI 租户。Pro 许可证启用不是在 Power BI Premium 容量中的内容的访问权限。但是，使用 Pro 许可证的外部用户并默认情况下限制为使用唯一体验。这可以通过使用中所述的方法是更改__使外部用户能够编辑和管理 Power BI 中的内容__本文档后面的部分。_

![Pro 许可证要求](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>外部合作伙伴的数据安全性

通常在使用多个外部供应商，Contoso 需要确保每个供应商看到仅涉及其自己产品的数据。 基于用户的安全和动态行级别安全性使这容易完成与 Power BI。

### <a name="user-based-security"></a>基于用户的安全

Power BI 的最强大功能之一是行级别安全性。 此功能允许 Contoso 创建单个报表和数据集，但仍将为每个用户的不同的安全规则的应用。 有关深入的说明，请参阅[行级别安全性 (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/)。

Power BI 与 Azure AD B2B 的集成，Contoso 将行级别安全性规则分配给来宾用户，只要它们受邀加入 Contoso 租户。 正如我们所见之前，Contoso 可以添加来宾用户，通过执行计划内或临时邀请。 如果 Contoso 想要强制实施行级别安全性，强烈建议使用计划性的邀请将提前时间和共享内容之前将其分配给安全角色的来宾用户添加。 如果 Contoso 改为使用临时邀请，可能会有短时间内的来宾用户将无法查看任何数据。

> [!NOTE]
> 访问数据时使用临时邀请受 RLS 这种延迟可能会导致以支持对您的 IT 团队的请求，因为用户将看到空白或中断时他们收到的电子邮件中打开共享链接查找报表/仪表板。 因此，强烈建议在此 scenario.* * 中使用计划性的邀请

让我们演练一下这方面的示例。

如前文所述，Contoso 已在全球范围内，供应商，他们想要确保其供应商组织中的用户从只是其所在区域中的数据获得见解。  但从 Contoso 的用户可以访问所有数据。 而不是创建几个不同的报表，Contoso 创建单个报表和数据的筛选器基于查看它的用户。

![共享的内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

为了确保 Contoso 可以基于连接的人员的数据进行筛选，请在 Power BI desktop 中创建了两个角色。 一个用于筛选 SalesTerritory"Europe"的所有数据，另一个用于"North America"。

![管理角色](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

每当在报表中定义角色，必须将用户分配到特定角色，他们才能访问任何数据。 Power BI 服务内的角色分配发生 (**数据集 > 安全**)

![设置安全性](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

这将打开页面 Contoso 的 BI 团队可以在其中看到这两个角色创建它们。  现在 Contoso 的 BI 团队可以将用户分配到角色。

![行级别安全性](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

Contoso 在示例中添加电子邮件地址的合作伙伴组织中的用户"[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)"到欧洲角色：

![行级安全性设置](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

这由 Azure AD 获取解决，Contoso 可以看到显示在窗口中准备好添加名称：

![显示角色](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

现在当此用户打开已共享给他的应用程序，他只看到带有从欧洲的数据的报表：

![查看内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>动态行级别安全性

另一个有趣的主题是若要查看如何动态行级别安全性 (RLS) 使用 Azure AD B2B 的工作。

简单地说，动态行级别安全性的工作原理是在连接到 Power BI 的人员的用户名所基于的模型中筛选数据。 添加用户组的多个角色，而不是在模型中定义的用户。 我们不会介绍详细的介绍中的模式。 人： Kasper de Jong 中的行级别安全性的各版本上提供详细的写入高达[Power BI Desktop 动态安全备忘单](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)，然后在[本白皮书](https://msdn.microsoft.com/library/jj127437.aspx)。

让我们看看一个小型示例-Contoso 有销售组的简单报表：

![示例内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

现在，需要使用两个来宾用户和内部用户共享此报表-内部的用户可以查看所有内容，但来宾用户只能看到组他们有权访问。 这意味着我们必须仅适用于来宾用户对数据进行筛选。 若要正确筛选数据，Contoso 使用动态 RLS 模式的白皮书和博客文章中所述。 这意味着，Contoso 将添加对数据本身的用户名：

![查看数据本身的 RLS 用户](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

然后，Contoso 创建筛选的正确关系具有适当的数据的适当数据模型：

![显示相应的数据](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

若要根据登录的用户自动对数据进行筛选，Contoso 需要在已连接用户中创建一个角色，将传递。 在这种情况下，Contoso 将创建两个角色 – 第一个参数是筛选器与当前登录到 Power BI （此操作适用即使对于 Azure AD B2B 来宾用户） 的用户的用户名的用户表"securityrole"。

![管理角色](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso 还会为其内部的用户可以查看所有内容创建另一个"AllRole"– 此角色没有任何安全谓词。

Power BI 桌面文件上传到该服务之后, Contoso 可以将来宾用户分配给"SecurityRole"和"AllRole"内部用户

现在，来宾用户打开报表时，他们只能看到一组 a： 从销售

![只能从组 A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

向右矩阵中可以看到两者都返回的来宾用户电子邮件地址 username （） 和 userprincipalname （） 函数的结果。

现在，内部用户获取可以查看所有数据：

![显示所有数据](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

如您所见，动态 RLS 适用于内部或来宾用户。

> [!NOTE]
> 这种情况下也可在 Azure Analysis Services 中使用模型时。 通常在 Azure Analysis Service 连接到相同的 Azure AD 作为 Power BI-在这种情况下，Azure Analysis Services 还知道通过 Azure AD B2B 邀请的来宾用户。

## <a name="connecting-to-on-premises-data-sources"></a>连接到内部部署的数据源

Power BI 提供了 Contoso 在本地数据源，如上利用的功能[SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)或[SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/)感谢到直接[的本地数据网关](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). 它是甚至还可以登录到具有相同的凭据与 Power BI 一起使用这些数据源。

> [!NOTE]
> 在安装网关连接到 Power BI 租户时，必须使用在你的租户中创建的用户。 外部用户不能安装网关，并将其连接到你的租户。 _

对于外部用户，这可能是更复杂，因为外部用户通常不识别到的本地 AD。 Power BI 中提供一种解决方法为此，Contoso 管理员可以将外部用户名映射到内部用户名，如中所述，从而[管理数据源-Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)。 例如， [ lucy@supplier1.com ](mailto:lucy@supplier1.com)可以映射到[lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com)。

![映射用户名称](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

此方法是没问题，如果 Contoso 只有少量的用户或如果 Contoso 可以映射到单个内部帐户的所有外部用户。 对于更复杂的方案，其中每个用户需要其自己的凭据，没有一种更高级的方法，使用[AD 的自定义特性](https://technet.microsoft.com/library/cc961737.aspx)来执行映射中所述[管理数据源-Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). 这样可以允许 Contoso 管理员在 Azure AD （还外部 B2B 用户） 中定义的每个用户的映射。  可以通过使用脚本或代码，因此 Contoso 可以完全自动的映射上邀请或计划的频率的 AD 对象模型设置这些属性。

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>使外部用户能够编辑和管理 Power BI 中的内容

Contoso 可以允许外部用户参与组织内的内容中的跨组织编辑和管理 Power BI 内容部分所述。

> [!NOTE]
> 若要编辑和管理组织的 Power BI 中的内容，用户必须具有工作区以外的我的工作区中的 Power BI Pro 许可证。 用户可以获取 Pro 许可证，如中所述_Licensing__section 本文档。_

Power BI 管理门户提供了**允许外部来宾用户编辑和管理组织中的内容**租户设置中设置。 默认情况下，该设置设置为禁用，这意味着外部用户默认情况下获取受约束的只读的体验。 设置适用于用户在 Azure AD 中设置为来宾的 UserType。 下表描述了用户体验，具体取决于他们的 UserType 和如何配置的设置的行为。

| **Azure AD 中的用户类型** | **允许外部来宾用户编辑和管理内容设置** | **行为** |
| --- | --- | --- |
| 来宾 | 已禁用的用户 （默认值） | 每个项消耗唯一视图。 允许对报表、 仪表板和应用程序时查看通过 URL 发送给来宾用户的只读访问。 Power BI 移动应用向来宾用户提供只读视图。 |
| 来宾 | 为用户启用 | 外部用户获取的访问权限的完整的 Power BI 体验，但某些功能将不可用到它们。 外部用户必须登录到 Power BI 中使用 Power BI 服务 URL，并包含租户信息。 可以浏览主页体验、 我的工作区和根据的权限，用户获取查看和创建内容。 </br></br> Power BI 移动应用向来宾用户提供只读视图。 |

> [!NOTE]
> Azure AD 中的外部用户也将设置为 UserType 成员。 这是当前不支持在 Power BI 中。

在 Power BI 管理门户中，在下图显示设置。

![管理员设置](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

来宾用户获得的只读默认体验，其中可以编辑和管理内容。 默认为禁用，这意味着所有来宾用户都拥有只读的体验。 Power BI 管理员可以启用组织中的所有来宾用户或在 Azure AD 中定义的特定安全组的设置。 在下图中，Contoso Power BI 管理员在 Azure AD 管理的外部用户可以编辑和管理 Contoso 租户中的内容中创建安全组。

为了帮助这些用户能够登录到 Power BI，向他们提供租户 URL。 要查找租户 URL，请执行以下步骤。

1. 在 Power BI 服务中，在顶部菜单中，选择帮助 ( **？** ) 然后**有关 Power BI**。
2. 查找值旁边**租户 URL**。 这是可以与来宾用户共享的租户 URL。

    ![租户 URL](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

当使用允许外部来宾用户编辑和管理组织中的内容，指定的来宾用户有权访问你组织的 Power BI，看到他们有权限访问的任何内容。 它们可以访问主页、 浏览和发布到工作区的内容、 安装的应用，在访问权限的列表，并且它们有我的工作区。 还可以创建或成为使用新工作区体验的工作区管理员。

> [!NOTE]
> 请务必查看本文档的管理部分，因为默认 Azure AD 设置阻止来宾用户使用某些功能，如人员选取器，这可能会导致降低 experience.* * 使用此选项

通过允许外部来宾用户可以编辑和管理组织租户设置中的内容启用的来宾用户，不提供给他们一些体验。 若要更新或发布报表，来宾用户需要使用 Power BI 服务 web UI，包括获取要将 Power BI Desktop 文件上传的数据。 不支持以下体验：

- 从 Power BI Desktop 直接向 Power BI 服务发布
- 来宾用户不能使用 Power BI Desktop 连接 Power BI 服务中的服务数据集
- 绑定到 Office 365 组的经典工作区：来宾用户无法创建或成为这些工作区的管理员。 可以是成员。
- 对于工作区访问列表，不支持发送临时邀请
- 不支持来宾用户使用 Power BI Publisher for Excel
- 来宾用户不能安装 Power BI Gateway，也不能将它连接到组织
- 来宾用户不能安装发布到整个组织的应用
- 来宾用户不能使用、创建、更新或安装组织内容包
- 来宾用户不能使用“在 Excel 中分析”
- 来宾用户不能为@mentioned在注释 （此功能将在即将发布的版本中添加）
- 来宾用户不能使用 （将在即将发布的版本中添加此功能） 的订阅
- 使用此功能的来宾用户应具有工作或学校帐户。 来宾用户使用个人帐户遇到由于登录限制更多的限制。



## <a name="governance"></a>管理

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>其他会影响体验与 Azure AD B2B 相关的 Power BI 中的 Azure AD 设置

在使用 Azure AD B2B 共享时，Azure Active Directory 管理员控制外部用户的体验的方面。 在 Azure Active Directory 设置为你的租户中的外部协作设置页上对它们的控制。

此处提供了设置的详细信息：

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> 默认情况下，来宾用户权限处于限制选项设置为是，因此尤其是 Power BI 中的来宾用户有限体验括起来共享人员选取器 Ui 不适合这些用户。 务必使用你的 Azure AD 管理员要将其设置为否，以确保良好 experience.* * 如下所示

![外部协作设置](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>控制来宾邀请

Power BI 管理员可以控制的外部共享只 Power BI 通过访问 Power BI 管理门户。 但是，租户管理员还可以控制外部共享与各种 Azure AD 策略。  这些策略，管理员可以租户

- 关闭由最终用户的邀请
- 仅管理员和来宾邀请者角色中的用户可以邀请
- 管理员、 来宾邀请者角色和成员可以邀请
- 所有用户，包括来宾，可以都邀请

你可以阅读更多有关在这些策略[委托 Azure Active Directory B2B 协作邀请](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations)。

所有 Power BI 操作由外部用户，都还有[我们审核门户中审核](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)。

### <a name="conditional-access-policies-for-guest-users"></a>来宾用户的条件性访问策略

Contoso 可以强制实施条件性访问策略的来宾用户访问 Contoso 租户中的内容。 有关详细的说明，可以[B2B 协作用户的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions)。

## <a name="common-alternative-approaches"></a>常见的替代方法

虽然 Azure AD B2B 可以轻松在组织之间共享数据和报表，有其他几种方法，通常使用并可能在某些情况下优异。

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>替代选项 1:创建重复的合作伙伴标识用户

使用此选项，Contoso 必须手动创建重复标识为每个合作伙伴用户在 Contoso 租户中，在下图中所示。 然后在 Power BI 中，Contoso 可以共享的已分配的标识相应的报表、 仪表板或应用。

![设置相应的映射和名称](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

选择此替代方法的原因：

- 由于用户的标识由你的组织控制，任何相关的电子邮件、 SharePoint 等服务，等也是你的组织控制范围内。 你的 IT 管理员可以重置密码、 禁用帐户，对访问或审核在这些服务中的操作。
- 因此，对于其业务通常被禁止访问某些服务使用个人帐户的用户可能需要组织帐户。
- 某些服务只能通过组织的用户。 例如，使用 Intune 来管理使用 Azure B2B 外部用户的个人/移动设备上的内容不可能。

无法选择此替代方法的原因：

- 来自合作伙伴组织的用户必须记住两个集的凭据 – 一个用于从 Contoso 对访问内容从其自己的组织和其他访问内容。 这是会为这些来宾用户带来麻烦，多个来宾用户会因这种体验产生混淆。
- Contoso 必须购买并将每个用户许可证分配给这些用户。 如果用户需要接收电子邮件或使用 office 应用程序，也需要相应的许可证，包括 Power BI Pro 即可编辑和共享 Power BI 中的内容。
- Contoso 可能想要强制实施更严格的授权和相比内部用户的外部用户的管理策略。 若要实现此目的，Contoso 需要创建外部用户内部命名法，并且所有 Contoso 用户都需要进行讲解此命名法。
- 当用户离开组织时，它们继续有权访问 Contoso 的资源，直到 Contoso 管理员手动删除其帐户
- Contoso 管理员必须为来宾，包括创建、 密码重置等管理标识。

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>替代选项 2:创建使用自定义身份验证的自定义 Power BI Embedded 应用程序

Contoso 的另一种方法是构建其自己自定义嵌入的 Power BI 应用程序与自定义身份验证 ([应用拥有数据](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers))。 尽管许多组织没有时间或资源来创建自定义应用程序分发 Power BI 内容向其外部合作伙伴，对于某些组织而言这是最好的方法，都应该慎重考虑。

通常情况下，组织都现有合作伙伴门户，集中存储与合作伙伴相关的所有组织资源的访问权限，提供隔离从内部组织资源，并提供简化的体验的合作伙伴可以支持很多合作伙伴和单个用户。

![很多合作伙伴门户](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

在以下示例中，从每个供应商登录到 Contoso 的合作伙伴门户的用户的标识提供程序使用 AAD。 它无法使用 AAD B2B、 Azure B2C、 本机标识，或与任意数量的其他标识提供者联合。 用户将以用户身份登录并访问合作伙伴门户生成使用 Azure Web 应用程序或类似于基础结构。

在 web 应用中，Power BI 报表嵌入从 Power BI Embedded 部署中。 Web 应用会简化对报表和旨在简化供应商与 Contoso 进行交互的整体体验中的任何相关的服务的访问。 此门户的环境也仅限于从 Contoso 内部 AAD 和 Contoso 的内部 Power BI 环境，以确保供应商无法访问这些资源。 通常情况下，数据将存储在单独的合作伙伴数据仓库，以确保数据和隔离。 这种隔离有好处，因为它可以限制直接访问你组织的数据，外部用户限制哪些数据可能有可能可用于外部用户，并限制与外部用户的意外共享数。

使用 Power BI Embedded，在门户可以利用更有利的许可，使用应用令牌或主用户以及高级容量购买的 Azure 模型，这简化了有关将许可证分配给最终用户问题和可以纵向扩展/向下基于应为 on使用情况。 在门户可以提供总体更高的质量和一致的体验，因为合作伙伴访问所有记住的合作伙伴的需求而设计了一个门户。 最后，Power BI Embedded 基于解决方案通常用于为多租户，因为它可以更轻松地确保伙伴组织之间的隔离。

选择此替代方法的原因：

- 更轻松地管理与合作伙伴组织的数量增长。 合作伙伴添加到一个单独的目录与 Contoso 的内部 AAD 目录的隔离，因为它简化了管理职责，并有助于防止意外的内部数据的外部用户共享。
- 典型的合作伙伴门户是高度跨合作伙伴品牌体验一致的体验，并且简化，以满足典型的合作伙伴的需求。 Contoso 可以将所有必需的服务集成到了一个门户，因此向合作伙伴提供更好的整体体验。
- Power BI Embedded 中的编辑内容涵盖 azure 等的高级方案的许可成本购买 Power BI Premium，并且不需要向这些用户的 Power BI Pro 许可证分配。
- 如果为一个多租户解决方案构建在合作伙伴之间提供更好地隔离。
- 在合作伙伴门户通常包括用于 Power BI 项目报表、 仪表板和应用程序的合作伙伴的其他工具。

无法选择此替代方法的原因：

- 需要大量精力来构建、 操作和维护此类一个门户，使之成为一项重大的投资中的资源和时间。
- 到解决方案的时间是更长的时间比使用 B2B 共享自仔细规划后，需要跨多个工作流执行。
- 其中有较小数目的合作伙伴可能是过高，无法调整此替代方法所需的工作。
- 使用临时共享的协作是你的组织所面临的主要方案。
- 报表和仪表板是不同的每个合作伙伴。 此替代方法引入了管理开销超出只需直接与合作伙伴共享。



## <a name="faq"></a>常见问题解答

**可以 Contoso 发送自动兑换的邀请的操作，以便用户只需"准备前往"？或没有用户始终需要单击到达兑换 URL？**

它们可以访问内容之前，最终用户必须始终单击通过同意体验。

如果您将邀请多个来宾用户，我们建议您将此委托从由核心 Azure AD 管理员[将用户添加到资源组织中的来宾邀请者角色](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role)。 此用户可以通过使用登录 UI、 PowerShell 脚本，来邀请合作伙伴组织中的其他用户或 Api。 这将减少你的 Azure AD 管理员邀请或重新邀请发送到伙伴组织的用户的管理负担。

**Contoso 为来宾用户的多重身份验证，如果可以强制其合作伙伴没有多重身份验证？**

是。 有关详细信息，请参阅[B2B 协作用户的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions)。

**B2B 协作如何工作时受邀的合作伙伴使用联合身份验证添加其自己的本地身份验证？**

如果合作伙伴具有联合到本地身份验证基础结构的 Azure AD 租户，在本地上单一登录 (SSO) 是自动实现的。 如果合作伙伴没有 Azure AD 租户，可能会为新用户创建的 Azure AD 帐户。

**可以邀请来宾用户与使用者电子邮件帐户？**

在 Power BI 中支持邀请来宾用户与使用者电子邮件帐户。 这包括如 hotmail.com、 outlook.com 和 gmail.com 域。 但是，这些用户可能会遇到限制超出具有的用户的工作或学校帐户会遇到。

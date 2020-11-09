---
title: 适用于美国政府客户的 Power BI - 概述
description: 美国政府客户可以向其 Microsoft 365 政府版计划添加 Power BI Pro 订阅。 了解如何在此服务说明中注册、连接和查看功能可用性。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/30/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: fe4f9c54b45035cc22f2e582a75ba98d648c549d
ms.sourcegitcommit: 8861dac6724202a5b3be456a6aff8f3584e0cccf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132358"
---
# <a name="power-bi-for-us-government-customers"></a>适用于美国政府客户的 Power BI

本文适用于将 Power BI 作为 Microsoft 365 政府版计划的一部分进行部署的美国政府客户。 政府版计划专为必须满足美国合规性和安全性标准的组织的独特需求而设计。 为美国政府客户设计的 Power BI 服务不同于 Power BI 服务的商业版本。 下面几节说明了这些特性差异和功能。

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>将 Power BI 添加到 Microsoft 365 政府版计划

必须先注册 Microsoft 365 政府版计划，然后才能获取 Power BI 美国政府版订阅并将许可证分配给用户。 如果组织已有 Microsoft 365 政府版计划，请跳到[购买适用于政府客户的 Power BI Pro 订阅](#buy-a-power-bi-pro-subscription-for-government-customers)。

### <a name="enroll-in-a-microsoft-365-government-plan"></a>注册 Microsoft 365 政府版计划

如果你是新客户，则必须先验证组织的资格，然后才能注册 Microsoft 365 政府版计划。  请先完成 [Microsoft 365 政府版资格验证表单](https://www.microsoft.com/microsoft-365/government/eligibility-validation)。 若要确保为组织选择正确的计划，请参阅 [Microsoft 365 美国政府服务说明](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government)。

> [!NOTE]
> 如果已将 Power BI 部署到商业环境中并想要迁移到美国政府云，则需要将新的 Power BI Pro 订阅添加到 Microsoft 365 政府版计划中。 接下来，将商业数据复制到适用于美国政府的 Power BI 服务，从用户帐户中删除商业许可证分配，然后将 Power BI Pro 政府版许可证分配给用户帐户。
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>购买适用于政府客户的 Power BI Pro 订阅

部署 Microsoft 365 后，可以添加 Power BI Pro 订阅。 按照[注册美国政府组织](service-govus-signup.md)中的分步指南来购买 Power BI Pro 政府版服务。 为需要使用 Power BI 的所有用户购买足够的许可证，然后将这些许可证分配给单个用户帐户。

> [!IMPORTANT]
> Power BI 美国政府版不可用作免费许可证。 若要访问政府社区云，必须为每个用户分配 Pro 许可证。 如果为用户帐户分配了免费许可证，则用户只能访问商业云，并会遇到身份验证和访问权限问题。 如果你已购买 Power BI Premium，则你无需分配 Pro 许可证即可启用用户访问权限。  只要将报表发布到 Premium 容量，组织中的用户都可以访问与他们共享的报表。 若要查看许可证类型之间的差异，请参阅[按许可证类型划分 Power BI 服务功能](../fundamentals/service-features-license-type.md)。
>

## <a name="government-cloud-instances"></a>政府云实例

Microsoft 365 为政府机构提供不同的环境，以满足不同的符合性要求。 有关每个环境的详细信息，请参阅：

* [Microsoft 365 政府社区云 (GCC)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) 专为联邦、州/省/直辖市/自治区和地方政府设计。

* [Microsoft 365 政府社区云“高”级别 (GCC High)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) 专为联邦机构、国防行业、航空工业以及持有受控非密信息的其他组织设计。 此环境适用于具有国际武器贸易条例 (ITAR) 数据或国防联邦采购补充规定 (DFARS) 要求的国家安全组织和公司。

* [Microsoft 365 DoD 环境](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod)专为美国国防部设计。


## <a name="sign-in-to-power-bi-for-us-government"></a>登录到适用于美国政府的 Power BI

对于政府用户和商业用户，用于连接到 Power BI 的 URL 有所不同。 若要登录 Power BI，请使用以下 URL：

| 商业版本  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

你的帐户可能已在多个云中设置。 如果通过这种方式设置了帐户，则当登录 Power BI Desktop 时，可以选择要连接的云。

## <a name="allow-connections-to-power-bi"></a>允许连接到 Power BI

若要使用 Power BI 服务，必须允许连接到 Internet 上所需的终结点。 若要在你自己的网络、Power BI 和其他依赖服务之间实现通信，必须可以访问这些目标。

下表列出了要添加到允许列表中的终结点，这些终结点是与 Power BI 服务建立连接以支持常规站点使用所必需的。 它们也是美国政府云所独有的。 Power BI 服务只需针对列出的终结点打开 TCP 端口 443。 用于获取数据、仪表板和报表集成、Power BI 视觉对象以及其他可选服务的终结点并非美国政府云独有。 若要将这些 URL 也添加到允许列表中，请参阅[将 Power BI URL 添加到允许列表](power-bi-whitelist-urls.md)。

Power BI 的身份验证、标识和管理依赖于与 Microsoft 365 服务的连接。 若要查看审核日志，也必须连接到 Microsoft 365。 若要标识这些服务的终结点，请参阅下表中的 Microsoft 365 集成。

### <a name="power-bi-urls-for-general-site-usage"></a>支持常规站点使用的 Power BI URL

|  用途 | 目标 |
| ---- | ----- |
| 后端 API | **GCC** ：api.powerbigov.us |
| | **GCC-High** ：api.high.powerbigov.us |
| | **DoD** ：api.mil.powerbi.gov.us |
| 后端 API | **GCC** ：*analysis.usgovcloudapi.net |
| | **GCC High** ：*.high.analysis.usgovcloudapi.net |
| | **DoD** ：*.mil.analysis.usgovcloudapi.net |
| 后端 API | **全部** ：*.pbidedicated.usgovcloudapi.net |
| 内容分发网络 (CDN) | **GCC** ：gov.content.powerapps.us |
| | **GCC High** ：high.content.powerapps.us |
| | **DoD** ：mil.content.powerapps.us |
| Microsoft 365 集成 | **GCC** ： [全球终结点](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High** ： [美国政府 GCC High 终结点](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD** ： [美国政府 DOD 终结点](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| 门户 |**GCC** ：*.powerbigov.us |
| | **GCC-High** ：*.high.powerbigov.us |
| | **DoD** ：*.mil.powerbigov.us |
| 服务遥测 | **全部** ：dc.services.visualstudio.us |
| 信息性消息（可选） | **全部** ：dynmsg.modpim.com |
| NPS 调查（可选） | **全部** ：nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>连接政府版本和全局 Azure 云服务

Azure 分布在多个云中。 默认情况下，你可以启用防火墙规则以打开与特定于云的实例的连接，但跨云网络不同。  若要在公有云中的服务和政府社区云中的服务之间进行通信，必须配置特定的防火墙规则。 例如，如果要从 Power BI 的政府云部署中访问 SQL 数据库的公有云实例，则需要 SQL 数据库中的防火墙规则。 为 SQL 数据库配置特定的防火墙规则，以便为以下数据中心建立与 Azure 政府云的连接：

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona
* US DoD 东部
* US DoD 中部

若要获取美国政府云 IP 范围，请下载 [Azure IP 范围和服务标记 - 美国政府云](https://www.microsoft.com/download/details.aspx?id=57063)文件。 其中列出了 Power BI 和 Power Query 的 IP 范围。

有关 Microsoft Azure 政府云服务的详细信息，请参阅 [Azure 政府文档](/azure/azure-government/)。

若要为 SQL 数据库设置防火墙，请[创建和管理 IP 防火墙规则](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules)。

## <a name="power-bi-feature-availability"></a>Power BI 功能可用性

为了满足政府云客户的要求，政府版计划与商业版计划之间存在一些差异。 我们的目标是在公开上市后的 30 天内，在政府云中提供所有功能。 在某些情况下，我们因为底层依赖项而无法提供功能。

下表列出了特定政府环境中不可用的功能。 我们纳入了计划发布后的预计可用性：

|功能 |GCC |GCC High |DoD|
|------|------|------|------|
|[政府云和商业云之间的 Azure B2B 协作](service-admin-azure-ad-b2b.md)<sup>1</sup>|![可用](../media/yes.png)|![不可用](../media/no.png)|![不可用](../media/no.png)|
|[使用 Power BI Web 部件在 SharePoint Online 中嵌入](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![可用](../media/yes.png)|![可用](../media/yes.png)|![不可用](../media/no.png)|
|[用于数据驱动警报的 Power Automate 连接](../connect-data/power-bi-data-sources.md)|![可用](../media/yes.png)|![可用](../media/yes.png)|![不可用](../media/no.png)|
|[Teams 中 Power BI 选项卡](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![可用](../media/yes.png)|![不可用](../media/no.png)|![不可用](../media/no.png)|
|[大型模型](service-premium-large-models.md) | 2020 年第 4 季度 |2020 年第 4 季度| ![不可用](../media/no.png) |
|[数据流 - SQL 计算引擎优化](../transform-model/service-dataflows-enhanced-compute-engine.md) | 2020 年第 4 季度 |2020 年第 4 季度| ![不可用](../media/no.png) |
|[数据流 - 直接查询](../transform-model/service-dataflows-directquery.md) | 2020 年第 4 季度 |2020 年第 4 季度|![不可用](../media/no.png)|
|[数据保护（MIP 标签）](service-security-sensitivity-label-overview.md)|2020 年第 4 季度|2020 年第 4 季度 |2020 年第 4 季度|
|[模板应用](../connect-data/service-template-apps-overview.md)<sup>3</sup>|2020 年第 4 季度 |2020 年第 4 季度| 2020 年第 4 季度|
|[自定义视觉对象](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|2020 年第 4 季度 |2020 年第 4 季度| 2020 年第 4 季度|
|[调用质量数据连接器](/microsoftteams/cqd-power-bi-connector)|![不可用](../media/no.png)|![不可用](../media/no.png)|![不可用](../media/no.png)|
|[自带存储 (Azure Data Lake Gen 2)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)|![不可用](../media/no.png)|![不可用](../media/no.png)|![不可用](../media/no.png)|
|[QR 码生成](../create-reports/service-create-qr-code-for-tile.md)|![不可用](../media/no.png)|![不可用](../media/no.png)|![不可用](../media/no.png)|

<sup>1</sup> 尽管可以在 GCC 中进行 B2B 协作，但必须在该环境中向外部用户发出许可证。 商业云许可证在 GCC 中无效。 有关美国政府 B2B 协作已知限制的详细信息，请参阅[比较 Azure 政府和全球 Azure](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2)

<sup>2</sup> 适用于 GCC 的 Teams 中的 Power BI 体验受到限制，仅适用于经典工作区，不包括[在 Microsoft Teams 中嵌入 Power BI 内容](../collaborate-share/service-embed-report-microsoft-teams.md)中所述的增强功能。

<sup>3</sup> 对于政府云，针对版本的模板应用和自定义视觉对象的功能将受到限制。 发布版本时将发布有关特定限制的详细信息。

## <a name="next-steps"></a>后续步骤

* [注册适用于美国政府的 Power BI](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](/power-automate/us-govt)
* [Power BI 美国政府版演示](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)

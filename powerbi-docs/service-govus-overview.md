---
title: 适用于美国政府客户的 Power BI - 概述
description: 美国政府客户可以向其 Office 365 政府版计划添加 Power BI Pro 订阅。 了解如何在此服务说明中注册和查看功能可用性。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: 349b4d51c1649b714c67e61ac42ddcc49b2eeb12
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114879"
---
# <a name="power-bi-for-us-government-customers"></a>适用于美国政府客户的 Power BI
本文适用于将 Power BI 作为 Office 365 政府版计划的一部分进行部署的美国政府客户。 政府版计划专为必须满足美国合规性和安全性标准的组织的独特需求而设计。 为美国政府客户设计的 Power BI 服务不同于 Power BI 服务的商业版本。 下面几节说明了这些特性差异和功能。

## <a name="add-power-bi-to-your-office-365-government-plan"></a>将 Power BI 添加到 Office 365 政府版计划

必须先注册 Office 365 政府版计划，然后才能获取 Power BI 美国政府版订阅并将许可证分配给用户。 如果组织已有 Office 365 政府版计划，请跳到[购买 Power BI Pro 政府版订阅](#purchase-a-power-bi-pro-government-subscription)。

### <a name="enroll-in-office-365-government-plan"></a>注册 Office 365 政府版计划

如果你是新客户，则必须先验证组织的资格，然后才能注册政府版计划。  请先完成 [Office 365 政府版资格验证表单](https://www.microsoft.com/microsoft-365/government/eligibility-validation)。 若要确保为组织选择正确的计划，请参阅 [Office 365 美国政府服务说明](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government)。

> [!NOTE]
> 如果已将 Power BI 部署到商业环境中并想要迁移到美国政府云，则需要将新的 Power BI Pro 订阅添加到 Office 365 政府版计划中。 接下来，将商业数据复制到适用于美国政府的 Power BI 服务，从用户帐户中删除商业许可证分配，然后将 Power BI Pro 政府版许可证分配给用户帐户。
>
>

### <a name="government-cloud-instances"></a>政府云实例
Office 365 为政府机构提供不同的环境，以满足不同的符合性要求。 有关每个环境提供的内容的特定详细信息，请参阅链接服务说明。

* [Office 365 政府社区云 (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) 专为联邦、州/省/直辖市/自治区和地方政府设计。

* [Office 365 政府社区云高 (GCC-High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) 专为联邦机构、国防行业、航空工业以及持有受控非分类信息的其他组织设计。 此环境适用于具有国际武器贸易条例 (ITAR) 数据或国防联邦采购补充规定 (DFARS) 要求的国家安全组织和公司。

* [Office 365 DoD 环境](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod)专为美国国防部设计。 

### <a name="purchase-a-power-bi-pro-government-subscription"></a>购买 Power BI Pro 政府版订阅

部署 Office 365 后，可以添加 Power BI 订阅。 按照[注册美国政府组织](service-govus-signup.md#existing-office-government-cloud-customers)中的分步指南来购买 Power BI Pro 政府版服务。 为需要使用 Power BI 的所有用户购买足够的许可证，然后将这些许可证分配给单个用户帐户。

> [!IMPORTANT]
> Power BI 美国政府版不可用作免费许可证。 必须为每个用户分配 Pro 许可证，才能访问政府社区云。 如果为用户帐户分配了免费许可证，则他们只能访问商业云，并会遇到身份验证和访问权限问题。 如果你已购买 Power BI Premium，则你无需分配 Pro 许可证即可启用用户访问权限。  只要将报表发布到 Premium 容量，组织中的任何用户都可以访问与他们共享的报表。 若要查看许可证类型之间的差异，请参阅[按许可证类型划分 Power BI 服务功能](service-features-license-type.md)。
>
>

## <a name="connect-to-power-bi-for-us-government"></a>连接到适用于美国政府的 Power BI

不同于商业用户，请使用不同的 URL 连接到适用于美国政府的 Power BI。 若要登录 Power BI，请使用以下 URL：

| 商业版本 URL | 美国政府版本 URL | GCC High 的美国政府版 URL |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

帐户可以预配到多个云。 在这种情况下，使用 Power BI Desktop 时，可以在登录时选择要连接的云。

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>政府版本和全局 Azure 云服务之间的连接

Azure 分布在多个云中。 默认情况下，你可以启用防火墙规则以打开与特定于云的实例的连接，但跨云网络不同。  若要在公有云中的服务和政府社区云中的服务之间进行通信，必须配置特定的防火墙规则。 例如，如果要从 Power BI 的政府云部署中访问 SQL 的公有云实例，则需要 SQL 中的防火墙规则。 在 SQL 中配置特定的防火墙规则，以便为以下数据中心建立与 Azure 政府云的连接：

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

在公有云中，这些 IP 范围可用。 若要获取美国政府云 IP 范围，请下载 [Azure IP 范围和服务标记 – 美国政府云](https://www.microsoft.com/download/details.aspx?id=57063)文件。 

若要在 SQL 中设置防火墙，请按照步骤[创建和管理 IP 防火墙规则](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules)。

## <a name="power-bi-feature-availability"></a>Power BI 功能可用性

为了满足政府云客户的要求，政府版计划与商业版计划之间存在一些差异。 请参阅下表，了解每个政府环境中有哪些功能可用。

|功能 |   |GCC |GCC-High |DoD|
|------|------|------|------|------|
|管理|免费许可证|不可用|不可用|不可用|
|  |设置数据存储限制|可用|可用|可用|
|  |使用 Active Directory 组进行共享和访问控制|可用|可用|可用|
|  |通过 Office 365 安全和合规管理中心进行审核|可用|可用|可用|
|  |外部用户共享|可用|可用|可用|
|  |报表和仪表板的使用指标|不可用|不可用|不可用|
|  |GCC 和商业云之间的 Azure B2B|不可用|不可用|不可用|
|报表创建|创建和查看仪表板和报表|可用|可用|可用|
|  |计划的数据刷新|可用|可用|可用|
|  |可刷新的团队仪表板|可用|可用|可用|
|  |分页报表|可用|可用|在路线图上|
|  |模板应用|不可用|不可用|不可用|
|连接到数据|从 Excel 导入数据和报表|可用|可用|可用|
|  |从 CSV 文件导入数据|可用|可用|可用|
|  |从 Power BI Desktop 文件导入数据|可用|可用|可用|
|  |与 CDS 的连接|可用|不可用|不可用|
|  |Azure Data Lake Storage Gen2 连接器|可用|不可用|不可用|
|数据管理|数据管理网关|可用|可用|可用|
|  |Azure SQL 中的数据加密|可用|可用|可用|
|  |Power BI Blob 存储中的数据加密|可用|可用|可用|
|跨产品集成|使用 Power BI Web 部件在 SharePoint Online 中嵌入|不可用|不可用|不可用|
|  |使用嵌入的 Web 部件在 SharePoint Online 中嵌入|可用|可用|可用|
|  |数据流和 AI 函数|不可用|不可用|不可用|
|  |用于数据驱动警报的 Power Automate 连接|不可用|不可用|不可用|
|  |Teams 中 Power BI 选项卡|可用|不可用|不可用|
|  |自动化机器学习|不可用|不可用|不可用|
|  |认知服务|不可用|不可用|不可用|
|  |Azure ML|不可用|不可用|不可用|

## <a name="next-steps"></a>后续步骤

* [注册适用于美国政府的 Power BI](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Power BI 美国政府版演示</a>

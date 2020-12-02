---
title: 连接到 Power BI Desktop 中的 Microsoft Graph Security API
description: 轻松连接到 Power BI Desktop 中的 Microsoft Graph Security API
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 01/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: b3aa9be7be6e2769367cd3337b78030d52bde0c7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411416"
---
# <a name="connect-to-the-microsoft-graph-security-api-in-power-bi-desktop"></a>连接到 Power BI Desktop 中的 Microsoft Graph Security API

使用 Power BI Desktop 的 Microsoft Graph Security 连接器连接到 [Microsoft Graph Security API](/graph/security-concept-overview)。 然后可生成仪表板和报表，从而可深入了解与安全相关的[警报](/graph/api/resources/alert)和[安全功能分数](/graph/api/resources/securescores)。

Microsoft Graph Security API 连接了来自 Microsoft 及其合作伙伴的[多个安全解决方案](/graph/api/resources/security-api-overview#alerts)，可以更轻松地关联警报。 通过这种组合，可以访问丰富的上下文信息并简化自动化。 通过该组合，组织能够在降低成本和复杂性的同时，快速获得见解并跨多个安全产品执行操作。

## <a name="prerequisites-to-use-the-microsoft-graph-security-connector"></a>使用 Microsoft Graph Security 连接器的先决条件

若要使用 Microsoft Graph Security 连接器，必须明确获得 Azure Active Directory (Azure AD) 全局管理员的同意。 请参阅 [Microsoft Graph Security 身份验证要求](/graph/security-authorization)。
获得同意需要连接器的应用程序 ID 和名称，这里引用了该 ID 和名称，可在 [Azure 门户](https://portal.azure.com)中获得：

| 属性 | 值 |
|----------|-------|
| **应用程序名称** | `MicrosoftGraphSecurityPowerBIConnector` |
| **应用程序 ID** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
| **重定向 URI** | `https://oauth.powerbi.com/views/oauthredirect.html` |
|||

若要授予连接器许可，Azure AD 全局管理员可以使用以下任一方法：

* [为 Azure AD 应用程序授予同意](/azure/active-directory/develop/v2-permissions-and-consent)

* 通过[应用程序许可体验](/azure/active-directory/develop/application-consent-experience)响应逻辑应用在首次运行期间提交的请求
   
如果用户不是安全管理员角色的成员，则登录 Microsoft Graph Security 连接器的用户帐户必须是被分配的 Azure AD 安全读取者角色。 请参阅[向用户分配 Azure AD 角色](/graph/security-authorization#assign-azure-ad-roles-to-users)。

## <a name="using-the-microsoft-graph-security-connector"></a>使用 Microsoft Graph Security 连接器

按照以下步骤使用连接器：

1. 在 Power BI Desktop 的“主页”功能区中，选择“获取数据” > “更多”  。
2. 在窗口左侧的类别列表中选择“联机服务”。
3. 选择“Microsoft Graph Security (Beta)”。

    ![“获取数据”对话框](media/desktop-connect-graph-security/GetData.PNG)
    
4. 在“Microsoft Graph Security”窗口中，选择要查询的 Microsoft Graph API 版本：v1.0 或 beta  。

    ![“选择版本”对话框](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. 出现提示时，请登录到 Azure Active Directory 帐户。 此帐户需要具有“安全读取者”或“安全管理员”角色，如上一节所述 。

    ![登录](media/desktop-connect-graph-security/SignIn.PNG) 
    
6. 如果你是管理员，且还未获得 Microsoft Graph Security Power BI 连接器（应用程序）许可，则会出现以下对话框。 选择“代表组织授予同意”。

    ![“管理员同意”对话框](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. 登录后，将看到以下对话框，表示已经过身份验证。 选择“连接”。

    ![“你当前已登录”对话框](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. 连接后，“导航器”窗口将显示步骤 4 中所选版本的 [Microsoft Graph 安全性 API](/graph/security-concept-overview) 中提供的警报、安全分数和其他实体。 选择要在 Power BI Desktop 中导入和使用的一个或多个实体。 然后，选择“加载”以获取在步骤 9 之后显示的结果视图。

    ![导航器对话框](media/desktop-connect-graph-security/NavTable.PNG)
    
9. 如果想使用 Microsoft Graph 安全性 API 进行高级查询，选择“指定自定义 Microsoft Graph 安全性 URL 以筛选结果”。 使用该功能，借助访问 API 所需的权限对 Microsoft Graph 安全性 API 发出 [OData.Feed](./desktop-connect-odata.md) 查询。

   以下示例使用 `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'` serviceUri。 要了解如何生成查询以筛选、排序或检索最新结果，请参阅 [OData 系统查询选项](/graph/query-parameters)。

   ![OdataFeed 示例](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   选择“调用”时，OData.Feed 函数会调用 API，从而打开查询编辑器 。 可以筛选和优化要使用的数据集。 然后，将该数据加载到 Power BI Desktop。

这是我们查询的 Microsoft Graph Security 实体的结果窗口：

   ![结果窗口示例](media/desktop-connect-graph-security/Result.PNG)
    

现在，你已经准备好在 Power BI Desktop 中使用从 Microsoft Graph Security 连接器导入的数据。 可以创建图形或报告。 也可以与从 Excel 工作簿、数据库或其他数据源导入的其他数据进行交互。

## <a name="next-steps"></a>后续步骤
* 在 [Microsoft Graph 安全性 GitHub Power BI 示例](https://aka.ms/graphsecuritypowerbiconnectorsamples)上查看使用此连接器的 Power BI 示例和模板。

* 有关用户方案和其他信息，请参阅 [Microsoft Graph 安全性 Power BI 连接器博客文章](https://aka.ms/graphsecuritypowerbiconnectorblogpost)。

* 可以使用 Power BI Desktop 连接到各种数据。 有关详细信息，请参阅下列资源：

    * [什么是 Power BI Desktop？](../fundamentals/desktop-what-is-desktop.md)
    * [Power BI Desktop 中的数据源](desktop-data-sources.md)
    * [使用 Power BI Desktop 成型和合并数据](desktop-shape-and-combine-data.md)
    * [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)
    * [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)
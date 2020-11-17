---
title: 注册应用以便嵌入 Power BI 内容
description: 了解如何在 Azure Active Directory 中注册应用程序，用于嵌入 Power BI 内容。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 52e835f4ff0d3dc4cad13c2e3ecc77d254f3be9d
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412164"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>注册 Azure AD 应用程序以使用 Power BI

若要使用 Power BI 嵌入式分析，需要在 Azure 中注册 Azure Active Directory (Azure AD) 应用程序。 Azure AD 应用程序为 Power BI REST 资源建立权限，并允许访问 [Power BI REST API](/rest/api/power-bi/)。

## <a name="determine-your-embedding-solution"></a>确定嵌入解决方案

注册应用之前，请确定以下哪种解决方案最适合你：

* 为客户嵌入内容
* 为组织嵌入内容

### <a name="embed-for-your-customers"></a>为客户嵌入内容

如果计划创建专为客户设计的应用程序，请使用[为客户嵌入内容](embed-sample-for-customers.md)解决方案（也称为“应用拥有数据”）。 用户无需登录到 Power BI 或拥有 Power BI 许可证即可使用该应用程序。 该应用程序将使用以下方法之一对 Power BI 进行身份验证：

* “主用户”帐户（用于登录 Power BI 的 Power BI Pro 许可证）

*  [服务主体](embed-service-principal.md)

“为客户嵌入内容”解决方案通常由独立软件供应商 (ISVs) 和为第三方创建应用程序的开发人员使用。

### <a name="embed-for-your-organization"></a>为组织嵌入内容

如果计划创建要求用户使用其凭据对 Power BI 进行身份验证的应用程序，请使用[为组织嵌入内容](embed-sample-for-your-organization.md)解决方案（也称为“用户拥有数据”）。

“为组织嵌入内容”解决方案通常由企业和大型组织使用，适用于内部用户。

## <a name="register-an-azure-ad-app"></a>注册 Azure AD 应用

注册 Azure AD 应用的最简单方法是使用 [Power BI 嵌入安装工具](https://app.powerbi.com/embedsetup)。 该工具使用简单的图形界面为两种嵌入解决方案提供了快速注册过程。

如果要创建“为组织嵌入内容”应用程序，并希望对 Azure AD 应用进行更多的控制，可以在 Azure 门户中手动注册它。

> [!IMPORTANT]
> 注册 Power BI 应用之前，需要一个 [Azure Active Directory 租户和一个组织用户](create-an-azure-active-directory-tenant.md)。

# <a name="embed-for-your-customers"></a>[为客户嵌入内容](#tab/customers)

以下步骤介绍如何针对 Power BI [为客户嵌入内容](embed-sample-for-customers.md)解决方案注册 Azure AD 应用程序。

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. 在“选择嵌入解决方案”部分中，选择“为客户嵌入内容”。

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. 在“步骤 2 - 注册应用程序”中，填写以下字段：

    * **应用程序名称** - 为应用程序指定名称。

    * **API 访问** - 选择应用程序所需的 Power BI API（也称为作用域）。 可以使用“全选”来选择所有 API。 有关 Power BI 访问权限的详细信息，请参阅 [Microsoft 标识平台终结点中的权限和许可](/azure/active-directory/develop/v2-permissions-and-consent)。

5. 选择“注册”。

    Azure AD 应用“应用程序 ID”显示在“摘要”框中。 复制该值以供将来使用。

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. 在“步骤 5 - 授予权限”中，选择“授予权限”，并在弹出窗口中选择“接受” 。 这使你的 Azure AD 应用可以通过已登录的用户访问你选择的 API （也称为作用域）。 此用户也称为“主用户”。

9. （可选）如果使用该工具创建了 Power BI 工作区并将内容上传到了该工作区，则可以选择“下载示例应用程序”。 请确保复制了“摘要”框中的所有信息。

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[为组织嵌入内容](#tab/organization)

以下步骤介绍如何针对 Power BI [为组织嵌入内容](embed-sample-for-your-organization.md)解决方案注册 Azure AD 应用程序。

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. 在“选择嵌入解决方案”部分中，选择“为组织嵌入内容”。

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. 在“步骤 2 - 注册应用程序”中，填写以下字段：

    * **应用程序名称** - 为应用程序指定名称。

    * **主页 URL** - 输入主页的 URL。

    * **重定向 URL** - 登录后，应用程序用户将被重定向到该地址，同时应用程序将从 Azure 接收身份验证代码。 选择以下选项之一：

        * **使用默认 URL** - 此选项会自动创建和下载嵌入式分析应用程序示例。 默认 URL 为 http://localhost:13526/ 。

        * **使用自定义 URL** - 如果已有嵌入式分析应用程序，并知道要用作重定向 URL 的内容，请选择此选项。

    * **API 访问** - 选择应用程序所需的 Power BI API（也称为作用域）。 可以使用“全选”来选择所有 API。 有关 Power BI 访问权限的详细信息，请参阅 [Microsoft 标识平台终结点中的权限和许可](/azure/active-directory/develop/v2-permissions-and-consent)。

5. 选择“注册”。

    Azure AD 应用“应用程序 ID”和“应用程序机密”值显示在“摘要”框中 。 复制这些值以供将来使用。

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. （可选）如果使用该工具创建了 Power BI 工作区并将内容上传到了该工作区，则可以选择“下载示例应用程序”。 请确保复制了“摘要”框中的所有信息。

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[手动注册](#tab/manual)

仅在创建“为组织嵌入内容”解决方案时才使用 Azure AD 手动应用注册。 有关如何在 Azure Active Directory 中注册应用程序的详细信息，请参阅[向 Azure Active Directory 注册应用](/azure/active-directory/develop/quickstart-v2-register-an-app)。

1. 登录到 [Azure 门户](https://portal.azure.com)。

2. 在页面右上角选择你的帐户，从而选择你的 Azure AD 租户。

3. 选择“应用注册” 。 如果无法看到此选项，请进行搜索。
 
4. 在“应用注册”中，选择“新注册”。

5. 填写以下字段：

    * **名称** - 为应用程序指定名称。

    * **支持的帐户类型** - 选择可使用该应用程序的用户。

6. （可选）在“重定向 URI”中，添加一个重定向 URL。

7. 选择“注册”。 注册应用后，你将转到应用的“概述”页，可以在其中获取应用程序 ID。

---

## <a name="change-your-azure-ad-apps-permissions"></a>更改 Azure AD 应用的权限

注册应用程序后，可以更改其权限。 权限更改可以通过编程方式或在 Azure 门户中进行。

# <a name="azure"></a>[Azure](#tab/Azure)

在 Azure 门户中，可以查看应用并对其权限进行更改。

1. 登录到 [Azure 门户](https://portal.azure.com)。

2. 在页面右上角选择你的帐户，从而选择你的 Azure AD 租户。

3. 选择“应用注册” 。 如果无法看到此选项，请进行搜索。

4. 从“拥有的应用程序”选项卡中，选择你的应用。 该应用程序将在“概述”选项卡中打开，你可以在其中查看应用程序ID 。

5. 选择“API 权限”选项卡。

6. 若要添加权限，请执行以下步骤：

    1. 选择“添加权限”，然后选择“Power BI 服务” 。

    2. 选择“委派权限”，然后添加或删除所需的特定权限。

    3. 完成后，选择“添加权限”以保存更改。

7. 若要删除权限，请执行以下步骤：

    1. 选择权限右侧的省略号 (...)。
    
    2. 选择“删除权限”。
    
    3. 在“删除权限”弹出窗口中，选择“是的，删除“。

# <a name="http"></a>[HTTP](#tab/HTTP)

若要以编程方式更改 Azure AD 应用权限，你需要获取租户中的现有服务主体（用户）。 有关如何执行该操作的信息，请参阅 [servicePrincipal](/graph/api/resources/serviceprincipal)。

1. 要在获取租户中的所有服务主体，请调用不带 `{ID}` 的 `Get servicePrincipal` API。

2. 使用作为 `appId` 属性的应用的应用程序 ID 检查服务主体。

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` 是可选项。

3. 通过将以下值之一分配给 `consentType`，为应用授予 Power BI 权限：

    * `AllPrincipals` - 只能被 Power BI 管理员用来代表租户中的所有用户授予权限。

    * `Principal` - 用于代表特定用户授予权限。 如果使用的是此选项，请将 `principalId={User_ObjectId}` 属性添加到请求正文。

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* 如果使用的是“主用户”，则为了避免 Azure AD 提示同意，你需要向主帐户授予权限。
    >* `resourceId` c78a3685-1ce7-52cd-95f7-dc5aea8ec98e 依赖于租户，但不是通用的。 此值是 Azure AD 中 Power BI 服务应用程序的 objectId 。 若要从 Azure 门户获取此值，请导航到[企业应用程序 > 所有应用程序](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps)，并搜索“Power BI 服务”。

4. 通过将值分配给 `consentType`，向 Azure AD 授予应用权限。

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

还可以使用 C# 更改 Azure AD 应用权限。 如果你正在考虑使某些流程自动化，则此方法很有用。

有关 HTTP 请求的详细信息，请参阅 [HTTP 选项卡](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions)。

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

```

---

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[获取 Power BI 应用程序的 Azure AD 访问令牌](get-azuread-access-token.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
---
title: 对用户进行身份验证并获取应用程序的 Azure AD 访问令牌
description: 了解如何在 Azure Active Directory 中注册应用程序，用于嵌入 Power BI 内容。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/04/2019
ms.openlocfilehash: cac59a4689eecd75c53ca1c62d7b097438b2ae53
ms.sourcegitcommit: 7f27b9eb0e001034e672050735ab659b834c54a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74310840"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>获取 Power BI 应用程序的 Azure AD 访问令牌

本文介绍如何在 Power BI 应用程序中对用户进行身份验证，以及如何检索要与 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 配合使用的访问令牌。

需要先获取 Azure Active Directory (Azure AD) **身份验证访问令牌**，然后应用才能调用该 REST API。 应用使用令牌获取对 Power BI 仪表板、磁贴和报表的访问权限。 若要了解详细信息，请参阅[使用 OAuth 2.0 代码授予流授予对 Azure Active Directory Web 应用程序的访问权限](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code)。

访问令牌的检索方式不同，具体视内容的嵌入方式而定。 本文介绍两种不同的方法。

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Power BI 用户（用户拥有数据）的访问令牌

此示例适用于用户使用其组织登录名手动登录 Azure AD 的情况。 此任务用于为具有 Power BI 服务访问权限的用户嵌入内容的情况。

### <a name="get-an-azure-ad-authorization-code"></a>获取 Azure AD 授权代码

获取**访问令牌**的第一步是从 **Azure AD** 获取授权代码。 构造具有以下属性的查询字符串，并重定向到 Azure AD  。

#### <a name="authorization-code-query-string"></a>授权代码查询字符串

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

构造查询字符串后，重定向到 **Azure AD** 以获取**授权代码**。  下面是构造**授权代码**查询字符串的并重定向到 **Azure AD** 的完整 C# 方法。 随后使用**授权代码**获取**访问令牌**。

在 redirect.aspx.cs 中，调用 [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) 生成令牌。

#### <a name="get-authorization-code"></a>获取授权代码

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>通过授权代码获取访问令牌

在 **Azure AD** 使用**授权代码**重定向回 Web 应用后，可使用授权代码来获取访问令牌。 下面的 C# 示例可用于重定向页面和 default.aspx 的 `Page_Load` 事件。

可从 [Active Directory 身份验证库](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet 包检索 **Microsoft.IdentityModel.Clients.ActiveDirectory** 命名空间。

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>非 Power BI 用户（应用拥有数据）的访问令牌

此方法通常用于独立软件供应商 (ISV) 类型的应用程序，即应用拥有数据访问权限。 用户不一定是 Power BI 用户，且应用程序控制用户身份验证和访问。

### <a name="access-token-with-a-master-account"></a>主帐户的访问令牌

若要使用这种方法，请使用一个是 Power BI Pro 用户的主帐户  。 帐户凭据存储在应用程序中。 应用程序使用这些存储的凭据进行 Azure AD 身份验证。 下面显示的示例代码来自[“应用拥有数据”示例](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>服务主体的访问令牌

若要使用这种方法，请使用一个是仅限应用的令牌的[服务主体](embed-service-principal.md)  。 应用程序使用服务主体进行 Azure AD 身份验证。 下面显示的示例代码来自[“应用拥有数据”示例](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>疑难解答

错误消息：“'AuthenticationContext' 不包含 'AcquireToken' 的定义，并且找不到接受 'AuthenticationContext' 类型的第一个参数的可访问 'AcquireToken' (是否缺少 using 指令或程序集引用?)”。

   如果看到此错误，请尝试下载 [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727)。

## <a name="next-steps"></a>后续步骤

至此，已拥有访问令牌，可以调用 Power BI REST API 嵌入内容了。 有关信息，请参阅[如何嵌入 Power BI 内容](embed-sample-for-customers.md#embed-content-within-your-application)。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

---
title: 获取身份验证访问令牌
description: 推送数据演练 - 获取身份验证访问令牌
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: cb50e887b7821ed23a928c6eb28d0c8bb3a28cb1
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86213833"
---
# <a name="step-2-get-an-authentication-access-token"></a>步骤 2：获取身份验证访问令牌

本文是[将数据推送到 Power BI 数据集](walkthrough-push-data.md)系列中的第二步。

在步骤 1 中，你[在 Azure AD 中注册了客户端应用](../embedded/register-app.md)。 在此步骤中，你将获得身份验证访问令牌。 Power BI 应用与 Azure Active Directory 集成，为你的应用提供安全的登录和授权。 你的应用使用令牌向 Azure AD 进行身份验证，并获得对 Power BI 资源的访问权限。

## <a name="get-an-authentication-access-token"></a>获取身份验证访问令牌

在开始之前，请确保已完成[将数据推送到 Power BI 数据集](walkthrough-push-data.md)系列中的[上一步骤](../embedded/register-app.md)。 

此过程要求使用 Visual Studio 2015 或更高版本。

1. 在 Visual Studio 中，创建新的 C# **控制台应用程序**项目。

2. 安装 [Azure AD Authentication Library for .NET NuGet 程序包](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727)。 .Net 应用需要此包才能获取身份验证安全令牌。 

     a. 选择“工具” > “NuGet 包管理器” > “包管理器控制台”。

     b. 输入 **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**

     c. 在 Program.cs 中，添加 `using Microsoft.IdentityModel.Clients.ActiveDirectory;`。

3. 将这些步骤后列出的示例代码添加到 Program.cs。

4. 使用[上一篇系列文章](../embedded/register-app.md)中注册应用时获取的**客户端 ID** 替换“{ClientID}”。

5. 运行控制台应用并登录 Power BI 帐户。 

   令牌字符串应在控制台窗口中显示。

**获取身份验证安全令牌的示例代码**

将此代码添加到 Program {...}。

* 调用操作的令牌变量： 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* 在 static void Main (string[] args) 中：
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* 添加 GetToken() 方法：

```csharp
       #region Get an authentication access token
       private static async Task<string> GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

获得身份验证令牌后，就可以调用任何 Power BI 操作。

本系列的下一篇文章将介绍如何[在 Power BI 中创建数据集](walkthrough-push-data-create-dataset.md)。


## <a name="complete-code-listing"></a>完整代码清单

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static async Task<string> GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>后续步骤

* 本系列的下一篇文章是[在 Power BI 中创建数据集](walkthrough-push-data-create-dataset.md)
* [Power BI REST API 概述](overview-of-power-bi-rest-api.md)  
* [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)  

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
---
title: 获取身份验证访问令牌
description: 推送数据的演练 - 获取身份验证访问令牌
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: maghan
ms.openlocfilehash: 1381706801a1a817927c891fcc205950cef24cbb
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430846"
---
# <a name="step-2-get-an-authentication-access-token"></a>步骤 2：获取身份验证访问令牌
本文是[将数据推送到数据集](walkthrough-push-data.md)的分步演练的一部分。

在将数据推送到数据集的**步骤 1**（[使用 Azure AD 注册应用](walkthrough-push-data-register-app-with-azure-ad.md)）中，你已在 Azure AD 中注册了客户端应用程序。 在此步骤中，你将获得身份验证访问令牌。 Power BI 应用将与 **Azure AD** 集成，以便为你的应用提供安全的登录和授权 你可以使用令牌向 **Azure AD** 进行身份验证，并获得对 Power BI 资源的访问权限。

下面介绍如何获取身份验证访问令牌。

## <a name="get-an-authentication-access-token"></a>获取身份验证访问令牌
> **注意**：在开始之前，先确保已按[将数据推送到数据集](walkthrough-push-data.md)演练中之前的步骤进行了操作。
> 
> 

1. 在 Visual Studio 2015 中，创建**控制台应用程序**项目。
2. 安装 [Azure AD Authentication Library for .NET NuGet 程序包](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)。 若要获取 .NET 应用的身份验证安全令牌，可以使用此程序包。 下面介绍了安装此程序包的方法：
   
     a. 在 Visual Studio 2015 中，选择**工具** > **NuGet 包管理器** > **程序包管理器控制台**。
   
     b. 在**程序包管理器控制台**中，输入 Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612。
3. 将下面的代码添加到 Program {...} 类中。
4. 使用注册应用时获得的**客户端 ID** 替换“{ClientID}”。 请参阅[向 Azure AD 注册应用](walkthrough-push-data-register-app-with-azure-ad.md)。
5. 安装 Microsoft.IdentityModel.Clients.ActiveDirectory 程序包后，将 **using Microsoft.IdentityModel.Clients.ActiveDirectory;** 添加到 Program.cs 中。
6. 运行控制台应用，并登录到你的 Power BI 帐户。 应该可以在控制台窗口中看到令牌字符串。

**获取身份验证安全令牌的示例代码**

将此代码添加到 Program {...}。

* 调用操作的令牌变量：
  
  ```
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* 在 static void Main (string[] args) 中：
  
  ```
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* 添加 GetToken() 方法：

```
       #region Get an authentication access token
       private static string GetToken()
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
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

获得身份验证令牌后，就可以调用任何 Power BI 操作。 下一步演示如何调用 [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) 操作来创建数据集，以便将数据推送到仪表板。

下一步将演示如何[在 Power BI 中创建数据集](walkthrough-push-data-create-dataset.md)。

下面是[完整代码清单](#code)。

<a name="code"/>

## <a name="complete-code-listing"></a>完整代码清单
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
            private static string GetToken()
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
                string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

                Console.WriteLine(token);
                Console.ReadLine();

                return token;
            }

            #endregion

        }
    }


[下一步 >](walkthrough-push-data-create-dataset.md)

## <a name="next-steps"></a>后续步骤
[在 Power BI 中创建数据集](walkthrough-push-data-create-dataset.md)  
[使用 Azure AD 注册应用](walkthrough-push-data-register-app-with-azure-ad.md)  
[Azure AD Authentication Library for .NET NuGet 程序包](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)  
[将数据推送到 Power BI 数据集](walkthrough-push-data.md)  
[Power BI REST API 概述](overview-of-power-bi-rest-api.md)  
[Power BI REST API 引用](https://docs.microsoft.com/rest/api/power-bi/)  
更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


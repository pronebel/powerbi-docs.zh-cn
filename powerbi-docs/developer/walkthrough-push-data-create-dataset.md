---
title: 创建数据集
description: 演练 - 将数据推送到数据集 - 在 Power BI 中创建数据集
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 9b4685752532a849405b8164fb2be0a8dd867411
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55761929"
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>步骤 3：在 Power BI 中创建数据集
本文是[将数据推送到数据集](walkthrough-push-data.md)的分步演练的一部分。

在将数据推送到数据集的**步骤 2**（[获取身份验证访问令牌](walkthrough-push-data-get-token.md)）中，你获得一个对 **Azure AD** 进行身份验证的令牌。 在此步骤中，使用该令牌调用 [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) 操作。

若要调用 REST 资源，需用定位该资源的 URL，并向 Power BI 服务资源发送描述数据集的 JavaScript 对象表示法 (JSON) 字符串。 REST 资源可标识你想使用的 Power BI 服务的部分。 要将数据推送到数据集，目标资源为**数据集**。 标识数据集的 URL 是 https://api.PowerBI.com/v1.0/myorg/datasets。 如果你正在推送组内的数据，该 URL 为 https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets。

若要对 Power BI REST 操作进行身份验证，请将[获取身份验证访问令牌](walkthrough-push-data-get-token.md)中获得的令牌添加到请求头中：

当调用 [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) 操作时，创建新的数据集。 

![](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

下面介绍了如何在 Power BI 中创建数据集。

## <a name="create-a-dataset-in-power-bi"></a>在 Power BI 中创建数据集
> [!NOTE]
> 在开始之前，先确保已按[将数据推送到数据集](walkthrough-push-data.md)演练中之前的步骤进行了操作。
> 
> 

1. 在[步骤 2 - 获取身份验证访问令牌](walkthrough-push-data-get-token.md)中创建的控制台应用程序项目中，将 **using System.Net;** 和 **using System.IO;** 添加到 Program.cs。
2. 在 Program.cs 中，添加以下代码。
3. 运行控制台应用，并登录到你的 Power BI 帐户。 应该可以在控制台窗口中看到**已创建的数据集**。 此外，还可以登录到 Power BI 查看新的数据集。

**将数据推送到数据集示例**

将此代码添加到 Program.cs。

* 在 static void Main (string[] args) 中：
  
    ```
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* Add a CreateDataset() method:
  
    ```
    #region Create a dataset in Power BI
    private static void CreateDataset()
    {
        //TODO: Add using System.Net and using System.IO
  
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "POST";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        //Create dataset JSON for POST request
        string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
            "[{\"name\": \"Product\", \"columns\": " +
            "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
            "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
            "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
            "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
            "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
            "]}]}";
  
        //POST web request
        byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
        request.ContentLength = byteArray.Length;
  
        //Write JSON byte[] into a Stream
        using (Stream writer = request.GetRequestStream())
        {
            writer.Write(byteArray, 0, byteArray.Length);
  
            var response = (HttpWebResponse)request.GetResponse();
  
            Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));
  
            Console.ReadLine();
        }
    }
    #endregion
    ```

下一步将向你演示如何[获取数据集以将行添加到 Power BI 表](walkthrough-push-data-get-datasets.md)

下面是[完整代码清单](#code)。

<a name="code"/>

## <a name="complete-code-listing"></a>完整代码清单
    using System;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System.Net;
    using System.IO;

    namespace walkthrough_push_data
    {
        class Program
        {
            private static string token = string.Empty;

            static void Main(string[] args)
            {

                //Get an authentication access token
                token = GetToken();

                //Create a dataset in Power BI
                CreateDataset();

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


            #region Create a dataset in Power BI
            private static void CreateDataset()
            {
                //TODO: Add using System.Net and using System.IO

                string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                //POST web request to create a dataset.
                //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                request.KeepAlive = true;
                request.Method = "POST";
                request.ContentLength = 0;
                request.ContentType = "application/json";

                //Add token to the request header
                request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                //Create dataset JSON for POST request
                string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                    "[{\"name\": \"Product\", \"columns\": " +
                    "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                    "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                    "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                    "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                    "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                    "]}]}";

                //POST web request
                byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
                request.ContentLength = byteArray.Length;

                //Write JSON byte[] into a Stream
                using (Stream writer = request.GetRequestStream())
                {
                    writer.Write(byteArray, 0, byteArray.Length);

                    var response = (HttpWebResponse)request.GetResponse();

                    Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                    Console.ReadLine();
                }
            }
            #endregion
        }
    }


[下一步 >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>后续步骤
[获取数据集以将行添加到 Power BI 表](walkthrough-push-data-get-datasets.md)  
[获取身份验证访问令牌](walkthrough-push-data-get-token.md)  
[PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)  
[PostDatasetInGroup](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdatasetingroup)  
[将数据推送到 Power BI 仪表板](walkthrough-push-data.md)  
[Power BI REST API 概述](overview-of-power-bi-rest-api.md)  
[Power BI REST API 引用](https://docs.microsoft.com/rest/api/power-bi/)  

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


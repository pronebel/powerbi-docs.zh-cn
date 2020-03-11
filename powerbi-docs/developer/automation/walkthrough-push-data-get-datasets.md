---
title: 获取数据集以添加行
description: 推送数据 - 获取数据集以将行添加到 Power BI 表演练
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 02/05/2019
ms.openlocfilehash: 5b4e6a2506555be6984a03e2a8f0fb8f4050f803
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079292"
---
# <a name="step-4-get-a-dataset-to-add-rows-into-a-power-bi-table"></a>步骤 4：获取数据集以将行添加到 Power BI 表

本文是[将数据推送到数据集](walkthrough-push-data.md)的分步演练的一部分。

在将数据推送到数据集的**步骤 3**（[在 Power BI 中创建数据集](walkthrough-push-data-create-dataset.md)）中，你调用了[创建数据集](https://docs.microsoft.com/rest/api/power-bi/datasets)操作以在 Power BI 中创建数据集。 在此步骤中，你将使用[获取数据集](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)操作和 Newtonsoft.Json 来获取数据集 ID。在步骤 4 中使用数据集 ID 向数据集添加行。 

要将数据推送到 Power BI 数据集，需要引用数据集中的表。 要引用数据集中的表，首先需要获取**数据集 ID**。 使用[获取数据集](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)操作获取数据集 ID  。 “获取数据集”  操作将返回一个 JSON 字符串，它包含 Power BI 中所有数据集的列表。 对 JSON 字符串进行反序列化的推荐的方法是使用 [Newtonsoft.Json](https://www.newtonsoft.com/json)。

下面介绍如何获取数据集。

## <a name="get-a-power-bi-dataset"></a>获取 Power BI 数据集

> **注意：** 在开始之前，先确保已按[将数据推送到数据集](walkthrough-push-data.md)演练中之前的步骤进行了操作。

1. 在步骤 2 中创建的控制台应用程序项目中：推送数据演练，[获取身份验证访问令牌](walkthrough-push-data-get-token.md)，安装 Newtonsoft.Json NuGet 包。 下面介绍了安装此程序包的方法：

     a. 在 Visual Studio 2015 中，选择**工具** > **NuGet 包管理器** > **程序包管理器控制台**。

     b. 在**包管理器控制台**中，输入 Install-Package Newtonsoft.Json。
2. 安装包后，将 **using Newtonsoft.Json;** 添加到 Program.cs。
3. 在 Program.cs 中，添加以下代码以获取**数据集 ID**。
4. 运行控制台应用，并登录到你的 Power BI 帐户。 应可在控制台窗口中看到**数据集ID:** 后跟 ID。

**获取数据集示例**

将此代码添加到 Program.cs。

* 在 static void Main (string[] args) 中：
  
  ```csharp
  static void Main(string[] args)
  {
  
    //Get an authentication access token
    token = GetToken();
  
    //Create a dataset in Power BI
    CreateDataset();
  
    //Get a dataset to add rows into a Power BI table
    string datasetId = GetDataset();
  }
  ```
* 添加 GetDatset() 方法 ︰
  
  ```csharp
    #region Get a dataset to add rows into a Power BI table
    private static string GetDataset()
    {
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "GET";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        string datasetId = string.Empty;
        //Get HttpWebResponse from GET request
        using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
        {
            //Get StreamReader that holds the response stream
            using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
            {
                string responseContent = reader.ReadToEnd();
  
                //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                //and add using Newtonsoft.Json
                var results = JsonConvert.DeserializeObject<dynamic>(responseContent);
  
                //Get the first id
                datasetId = results["value"][0]["id"];
  
                Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                Console.ReadLine();
  
                return datasetId;
            }
        }
    }
    #endregion
  ```

下一步将演示如何[向 Power BI 表中添加行](walkthrough-push-data-add-rows.md)。

下面是[完整代码清单](#code)。

<a name="code"/>

## <a name="complete-code-listing"></a>完整代码清单

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;
using Newtonsoft.Json;

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

            //Get a dataset to add rows into a Power BI table
            string datasetId = GetDataset();

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
            string authorityUri = "https://login.microsoftonline.com/common/";

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

        #region Get a dataset to add rows into a Power BI table
        private static string GetDataset()
        {
            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "GET";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            string datasetId = string.Empty;
            //Get HttpWebResponse from GET request
            using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
            {
                //Get StreamReader that holds the response stream
                using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
                {
                    string responseContent = reader.ReadToEnd();

                    //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                    //and add using Newtonsoft.Json
                    var results = JsonConvert.DeserializeObject<dynamic>(responseContent);

                    //Get the first id
                    datasetId = results["value"][0]["id"];

                    Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                    Console.ReadLine();

                    return datasetId;
                }
            }
        }
        #endregion
    }
}
```

## <a name="next-steps"></a>后续步骤

* [向 Power BI 表中添加行](walkthrough-push-data-add-rows.md)  
* [Newtonsoft.Json](https://www.newtonsoft.com/json)  
* [获取数据集](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)  
* [将数据推送到 Power BI](walkthrough-push-data.md)  
* [Power BI REST API 概述](overview-of-power-bi-rest-api.md)  
* [Power BI REST API 引用](https://docs.microsoft.com/rest/api/power-bi/)  

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
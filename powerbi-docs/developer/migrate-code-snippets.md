---
title: 用于从 Power BI Embedded 迁移内容的代码片段
description: 以下是内容迁移所需的一些基本操作代码片段
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 95c249fe2326d9075d920a415c707811d19e5387
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880517"
---
# <a name="code-snippets-for-migrating-content-from-power-bi-workspace-collection"></a>用于从 Power BI 工作区集合迁移内容的代码片段

以下是内容迁移所需的一些基本操作代码片段。 对于某些报表类型的相关流，请参阅[如何将 Power BI 工作区集合内容迁移到 Power BI Embedded](migrate-from-powerbi-embedded.md#content-migration)。

可使用迁移工具 **** 帮助将内容从 Power BI Embedded (PaaS) 复制到 Power BI 服务 (SaaS)。 尤其是有大量内容时。 有关详细信息，请参阅 [Power BI Embedded 迁移工具](migrate-tool.md)。

下面的代码是使用 C# 和 [Power BI .NET SDK](https://www.nuget.org/profiles/powerbi) 的示例。

请确保使用以下命名空间来执行下面的代码片段。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V1;
using Microsoft.PowerBI.Api.V1.Models;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;
using Microsoft.Rest;
using Microsoft.Rest.Serialization;
using Newtonsoft.Json;
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;
```

## <a name="export-report-from-paas-workspace"></a>从 PaaS 工作区中导出报表

```csharp
    // Create a token credentials with "AppKey" type
    var credentials = new TokenCredentials(<myAppKey==>, "AppKey");

    // Instantiate your Power BI client passing in the required credentials
    var client = new PowerBIClient(credentials);

    client.BaseUri = new Uri("https://api.powerbi.com");

    var response = client.Reports.ExportReportWithHttpMessagesAsync(<myWorkspaceCollectionName>, <myWorkspaceId>, <myReportId>);

    if (response.Result.Response.StatusCode == HttpStatusCode.OK)
    {
        var stream = response.Result.Response.Content.ReadAsStreamAsync();

        using (FileStream fileStream = File.Create(@"C:\Migration\myfile.pbix"))
        {
            stream.Result.CopyTo(fileStream);
            fileStream.Close();
        }
    }
```

## <a name="import-report-to-saas-workspace"></a>将报表导入到 SaaS 工作区

```csharp
    AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.net/common/");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api", <myClientId>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);
    var credentials = new TokenCredentials(PBISaaSAuthResult.AccessToken);
    var client = new PowerBIClient(new Uri($"{"https://api.powerbi.com"}"), credentials);
    using (var file = File.Open(@"C:\Migration\myfile.pbix", FileMode.Open))
    {
        client.Imports.PostImportWithFileInGroup(<mySaaSWorkspaceId>, file, "importedreport", "Abort");
        while (true) ;
    }
```

## <a name="extract-directquery-connection-string-from-paas-report"></a>从 PaaS 报表提取 DirectQuery 连接字符串

该方法用于迁移到 SaaS 后更新 PBIX。

```csharp
    // Extract connection string from PaaS - DirectQuery report
    // Create a token credentials with "AppKey" type
    var credentials = new TokenCredentials(<myAppKey==>, "AppKey");

    // Instantiate your Power BI client passing in the required credentials
    var client = new PowerBIClient(credentials);

    client.BaseUri = new Uri("https://api.powerbi.com");

    var reports = client.Reports.GetReports(<myWorkspaceCollectionName>, <myWorkspaceId>);

    Report report = reports.Value.FirstOrDefault(r => string.Equals(r.Id, <myReportId, StringComparison.OrdinalIgnoreCase));

    var datasource = client.Datasets.GetDatasources(<myWorkspaceCollectionName>, <myWorkspaceId>, report.DatasetId);
```

## <a name="update-directquery-connection-string-is-saas-workspace"></a>更新 DirectQuery 连接字符串是 SaaS 工作区

```csharp
    public class ConnectionString
    {
        [JsonProperty(PropertyName = "connectionString")]
        public string connection { get; set; }
    }

    AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.net/common/");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api",<myclient_id>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);
    var credentials = new TokenCredentials(PBISaaSAuthResult.AccessToken);
    var client = new PowerBIClient(new Uri($"{"https://api.powerbi.com"}"), credentials);

    ConnectionString connection = new ConnectionString() { connection = "data source = <server_name>; initial catalog = <db_name>; persist security info = True; encrypt = True; trustservercertificate = False" };

    client.Datasets.SetAllConnectionsInGroup(<myWorkspaceId>, <dataset_id>, connection);
```

## <a name="set-directquery-credentials-in-saas-workspace"></a>在 SaaS 工作区中设置 DirectQuery 凭据

为简单起见，我们将在此片段中使用未加密的凭据，同时也支持发送加密凭据。

```csharp
    public class ConnectionString
    {
        [JsonProperty(PropertyName = "connectionString")]
        public string connection { get; set; }
    }

    public class BasicCreds
    {
        [JsonProperty(PropertyName = "username")]
        public string user { get; set; }

        [JsonProperty(PropertyName = "password")]
        public string pwd { get; set; }
    }

    var basicCreds = new BasicCreds() { user = <sqldb_username>, pwd = <sqldb_password> };
    var body = new SetCredsRequestBody() { credentialType = "Basic", basicCredentials = basicCreds };

    var url = string.Format("https://api.powerbi.com/v1.0/myorg/gateways/{0}/datasources/{1}", <gateway_id>, <datasource_id>);
    var request = new HttpRequestMessage(new HttpMethod("PATCH"), url);
    // Set authorization header from you acquired Azure AD token
    AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.net/common/");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api", <myclient_id>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", PBISaaSAuthResult.AccessToken);

    request.Content = new StringContent(JsonConvert.SerializeObject(body), Encoding.UTF8, "application/json");

    HttpClient simpleClient = new HttpClient();
    var response = await simpleClient.SendAsync(request);
```

## <a name="push-dataset--report"></a>推送数据集和报表

将需要为创建的数据集重新生成报表。

在此片段中，我们假设可推送的数据集已在 SaaS 环境的工作区中。 有关推送 API 的信息，请参阅[将数据推送到 Power BI 数据集](walkthrough-push-data.md)。

```csharp
    var credentials = new TokenCredentials(<Your WSC access key>, "AppKey");

    // Instantiate your Power BI client passing in the required credentials
    var client = new Microsoft.PowerBI.Api.V1.PowerBIClient(credentials);
    client.BaseUri = new Uri("https://api.powerbi.com");

    // step 1 -> create dummy dataset at PaaS workspace
    var fileStream = File.OpenRead(<Path to your dummy dataset>);
    var import = client.Imports.PostImportWithFileAsync(<Your WSC NAME>, <Your workspace ID>, fileStream, "dummyDataset");
    while (import.Result.ImportState != "Succeeded" && import.Result.ImportState != "Failed")
    {
        import = client.Imports.GetImportByIdAsync(<Your WSC NAME>, <Your workspace ID>, import.Result.Id);
        Thread.Sleep(1000);
    }
    var dummyDatasetID = import.Result.Datasets[0].Id;

    // step 2 -> clone the pushable dataset and rebind to dummy dataset
    var cloneInfo = new Microsoft.PowerBI.Api.V1.Models.CloneReportRequest("pushableReportClone",null, dummyDatasetID);
    var clone = client.Reports.CloneReportAsync(<Your WSC NAME>, <Your workspace ID>, <Your pushable report ID>, cloneInfo);
    var pushableReportCloneID = clone.Result.Id;


    // step 3 -> Download the push API clone report with the dummy dataset
    var response = client.Reports.ExportReportWithHttpMessagesAsync(<Your WSC NAME>, <Your workspace ID>, pushableReportCloneID);
    if (response.Result.Response.StatusCode == HttpStatusCode.OK)
    {
        var stream = response.Result.Response.Content.ReadAsStreamAsync();
        using (fileStream = File.Create(@"C:\Migration\PushAPIReport.pbix"))
        {
            stream.Result.CopyTo(fileStream);
            fileStream.Close();
        }
    }

    // step 4 -> Upload dummy PBIX to SaaS workspace
    AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.net/common/");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api", <Your client ID>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);
    var credentialsSaaS = new TokenCredentials(PBISaaSAuthResult.AccessToken);
    var clientSaaS = new Microsoft.PowerBI.Api.V2.PowerBIClient(new Uri($"{"https://api.powerbi.com"}"), credentialsSaaS);
    using (var file = File.Open(@"C:\Migration\PushAPIReport.pbix", FileMode.Open))
    {

        var importSaaS = clientSaaS.Imports.PostImportWithFileAsyncInGroup(<Your GroupID>, file, "importedreport1", "Abort");
        while (importSaaS.Result.ImportState != "Succeeded" && importSaaS.Result.ImportState != "Failed")
        {
            importSaaS = clientSaaS.Imports.GetImportByIdAsync(importSaaS.Result.Id);
            Thread.Sleep(1000);
        }
        var importedreport1ID = importSaaS.Result.Reports[0].Id;


        // step 5 -> Rebind report to "real" push api dataset
        var rebindInfoSaaS = new Microsoft.PowerBI.Api.V2.Models.RebindReportRequest(<Your pushable dataset  ID at power bi>);
        var rebindSaaS = clientSaaS.Reports.RebindReportInGroupWithHttpMessagesAsync(<Your GroupID>, importedreport1ID, rebindInfoSaaS);

    }
```

## <a name="next-steps"></a>后续步骤

[Power BI Embedded 迁移工具](migrate-tool.md)  
[使用 Power BI 嵌入](embedding.md)  
[如何将 Power BI Embedded 工作区集合内容迁移到 Power BI](migrate-from-powerbi-embedded.md)  
[如何嵌入 Power BI 仪表板、报表和磁贴](embedding-content.md)  
[什么是 Power BI Premium？](../service-premium-what-is.md)  
[JavaScript API Git 存储库](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git 存储库](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript 嵌入示例](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

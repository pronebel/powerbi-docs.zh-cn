---
title: 为政府和主权云客户将 Power BI 内容嵌入到应用程序的嵌入式分析
description: 了解如何通过使用适用于嵌入式分析的 Power BI API，为客户将报表、仪表板或磁贴集成或嵌入到应用程序中。 了解如何使用嵌入式分析软件、嵌入式分析工具或嵌入式商业智能工具将 Power BI 集成到应用程序。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: 790c06dd84d7db3a382ef547c8fcc16237273951
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "55431145"
---
# <a name="tutorial-embed-a-power-bi-dashboard-tile-or-report-into-your-application-for-sovereign-clouds"></a>教程：将 Power BI 仪表板、磁贴或报表嵌入主权云应用程序中

了解如何为主权云将分析内容嵌入到业务流程应用程序中。 可以结合使用 Power BI .NET SDK 与 Power BI JavaScript API 将报表、仪表板或磁贴嵌入到 Web 应用程序中。

Power BI 还支持主权（私有）云。

不同主权云包括：

* 美国政府社区云 (GCC)

* 美 国 军事承包商 (DoDCON)

* 美 国 军事 (DoD)

* Power BI for Germany 云

* Power BI for China 云

![嵌入的仪表板](media/embed-sample-for-customers/powerbi-embed-dashboard.png)

若要开始本演练，需要一个 Power BI 帐户。 如果未设置帐户，则可以根据主权云类型，注册[美国政府 Power BI 帐户](../service-govus-signup.md)、[Power BI for Germany 云帐户](https://powerbi.microsoft.com/power-bi-germany/?ru=https%3A%2F%2Fapp.powerbi.de%2F%3FnoSignUpCheck%3D1)或 [Power BI for China 云帐户](http://www.21vbluecloud.com/powerbi/)。

> [!NOTE]
> 要改为为组织嵌入仪表板？ 请参阅[为组织将仪表板集成到应用中](integrate-dashboard.md)。

若要将仪表板集成到 Web 应用，请使用 **Power BI** API 和 Azure Active Directory (AD) 授权**访问令牌**来获取仪表板。 然后，使用嵌入令牌加载仪表板。 **Power BI** API 向特定 **Power BI** 资源提供编程访问权限。 有关详细信息，请参阅 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)、[Power BI .NET SDK 和 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)。

## <a name="download-the-sample"></a>下载示例

本文展示的是 GitHub 上[“应用拥有数据”示例](https://github.com/Microsoft/PowerBI-Developer-Samples)中使用的代码。 若要按照此演练操作，可以下载这个示例。

![“应用拥有数据”示例](media/embed-sample-for-customers-sovereign-clouds/embed-sample-for-customers-026.png)

* 政府社区云 (GCC)：
1. 使用 GCCCloud.config 内容覆盖 Cloud.config 文件。

2. 在 Web.config 文件中更新 applicationId（本机应用 applicationId）、workspaceId、用户（你的主用户）和密码。

3. 如下所示，在 web.config 文件中添加 GCC 参数。

```xml
<add key="authorityUrl" value="https://login.microsoftonline.net/common/" />
<add key="resourceUrl" value="https://analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.powerbigov.us" />
```

* 军事承包商 (DoDCON)：
1. 使用 TBCloud.config 内容覆盖 Cloud.config 文件。

2. 在 Web.config 文件中更新 applicationId（本机应用 applicationId）、workspaceId、用户（你的主用户）和密码。

3. 如下所示，在 web.config 文件中添加 DoDCON 参数。

```xml
<add key="authorityUrl" value="https://login.microsoftonlineS.net/common/" />
<add key="resourceUrl" value="https://high.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.high.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.high.powerbigov.us" />
```

* 军事 (DoD)：
1. 使用 PFCloud.config 内容覆盖 Cloud.config 文件。

2. 在 Web.config 文件中更新 applicationId（本机应用 applicationId）、workspaceId、用户（你的主用户）和密码。

3. 如下所示，在 web.config 文件中添加 DoDCON 参数。

```xml
<add key="authorityUrl" value="https://login.microsoftonline.net/common/" />
<add key="resourceUrl" value="https://mil.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.mil.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.mil.powerbigov.us" />
```

* Power BI for Germany 云参数
1. 使用 Power BI for Germany 云内容覆盖 Cloud.config 文件。

2. 在 Web.config 文件中更新 applicationId（本机应用 applicationId）、workspaceId、用户（你的主用户）和密码。

3. 在 web.config 文件中添加 Power BI for Germany 云参数，如下所示。

```xml
<add key="authorityUrl" value="https://login.microsoftonline.de/common/" />
<add key="resourceUrl" value="https://analysis.cloudapi.de/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.de/" />
<add key="embedUrlBase" value="https://app.powerbi.de" />
```

* Power BI for China 云参数
1. 使用 [Power BI for China](https://github.com/Microsoft/PowerBI-Developer-Samples/blob/master/App%20Owns%20Data/PowerBIEmbedded_AppOwnsData/CloudConfigs/Power%20BI%20operated%20by%2021Vianet%20in%20China/Cloud.config) 云内容覆盖 Cloud.config 文件。

2. 在 Web.config 文件中更新 applicationId（本机应用 applicationId）、workspaceId、用户（你的主用户）和密码。

3. 在 web.config 文件中添加 Power BI for China 云参数，如下所示。

```xml
<add key="authorityUrl" value="https://login.chinacloudapi.cn/common/" />
<add key="resourceUrl" value="https://analysis.chinacloudapi.cn/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.cn/" />
<add key="embedUrlBase" value="https://app.powerbi.cn" />
```

## <a name="step-1---register-an-app-in-azure-ad"></a>步骤 1 - 在 Azure AD 中注册应用

向 Azure AD 注册应用程序，以执行 REST API 调用。 有关详细信息，请参阅[注册 Azure AD 应用以便嵌入 Power BI 内容](register-app.md)。 由于存在不同的主权云附属关系，因此可以通过不同的 URL 来注册应用程序。

* 政府社区云 (GCC) - https://app.powerbigov.us/apps 

* 军事承包商 (DoDCON) - https://app.high.powerbigov.us/apps 

* 军事 (DoD) - https://app.mil.powerbigov.us/apps

* Power BI for Germany 云 - https://app.powerbi.de/apps

* Power BI for China 云 - https://app.powerbi.cn/apps

如果已下载[“为客户嵌入内容”示例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data)，请使用获取的 applicationId，以便此示例能够进行 Azure AD 身份验证。 若要配置此示例，请在 web.config 文件中更改 applicationId。

## <a name="step-2---get-an-access-token-from-azure-ad"></a>第 2 步 - 从 Azure AD 获取访问令牌

在应用程序中，需要先从 Azure AD 获取**访问令牌**，然后才能调用 Power BI REST API。 有关详细信息，请参阅[对用户进行身份验证并获取 Power BI 应用的 Azure AD 访问令牌](get-azuread-access-token.md)。 由于存在不同的主权云附属关系，因此可以通过不同的 URL 来获取应用程序的访问令牌。

* 政府社区云 (GCC) - https://login.microsoftonline.com

* 军事承包商 (DoDCON) - http://login.microsoftonline.us

* 军事 (DoD) - https://login.microsoftonline.us

* Power BI for Germany 云 - https://login.microsoftonline.de

* Power BI for China 云 - https://login.chinacloudapi.cn

若要查看这些访问令牌的示例，可以参阅 Controllers\HomeController.cs 文件中的每个内容项任务。

## <a name="step-3---get-a-content-item"></a>第 3 步 - 获取内容项

若要嵌入 Power BI 内容，需要执行几项操作，以确保能够正确嵌入内容。 虽然可以直接通过 REST API 完成所有这些步骤，但示例应用程序和本文中的示例都使用 .NET SDK。

### <a name="create-the-power-bi-client-with-your-access-token"></a>使用访问令牌创建 Power BI 客户端

你希望使用访问令牌创建 Power BI 客户端对象，以便能够与 Power BI API 进行交互。 使用 Microsoft.Rest.TokenCredentials 对象包装 AccessToken，以创建你的 Power BI 客户端对象。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. This is used to call the Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>获取要嵌入的内容项

使用 Power BI 客户端对象检索对要嵌入的项的引用。 可以嵌入仪表板、磁贴或报表。 下面的示例展示了如何从给定工作区检索首个仪表板、磁贴或报表。

有关示例，请参阅[“应用拥有数据”示例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data)的 Controllers\HomeController.cs。

#### <a name="reports"></a>报表

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

#### <a name="dashboards"></a>仪表板

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();
```

#### <a name="tiles"></a>磁贴

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// To retrieve the tile, you first need to retrieve the dashboard.

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();

// Get a list of tiles from a specific dashboard
ODataResponseListTile tiles = client.Dashboards.GetTilesInGroup(workspaceId, dashboard.Id);

// Get the first tile in the group.
Tile tile = tiles.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>创建嵌入令牌

使用 JavaScript API，可以生成嵌入令牌。 嵌入令牌特定于要嵌入的项。 只要嵌入 Power BI 内容，就需要为其新建嵌入令牌。 有关详细信息（包括要使用哪个 accessLevel），请参阅 [Embed Token](https://docs.microsoft.com/rest/api/power-bi/embedtoken)（嵌入令牌）。

> [!IMPORTANT]
> 由于嵌入令牌仅用于开发测试，因此 Power BI 主帐户生成的嵌入令牌数量有限。 对于嵌入生产方案，[必须购买容量](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical)。 购买容量后便不会限制嵌入令牌生成。

有关示例，请参阅[“为组织嵌入内容”示例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data)的 Controllers\HomeController.cs。

假设为 EmbedConfig 和 TileEmbedConfig 创建了类。 Models\EmbedConfig.cs 和 Models\TileEmbedConfig.cs 中提供了相关示例。

#### <a name="reports"></a>报表

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

#### <a name="dashboards"></a>仪表板

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Dashboards.GenerateTokenInGroup(workspaceId, dashboard.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = dashboard.EmbedUrl,
    Id = dashboard.Id
};
```

#### <a name="tiles"></a>磁贴

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token for a tile.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Tiles.GenerateTokenInGroup(workspaceId, dashboard.Id, tile.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new TileEmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = tile.EmbedUrl,
    Id = tile.Id,
    dashboardId = dashboard.Id
};
```

## <a name="step-4---load-an-item-using-javascript"></a>第 4 步 - 使用 JavaScript 加载项

可以使用 JavaScript 将仪表板载入网页上的 div 元素。 此示例对仪表板、磁贴或报表使用 EmbedConfig/TileEmbedConfig 模型和视图。 有关使用 JavaScript API 的完整示例，可以参阅 [Microsoft Power BI 嵌入示例](https://microsoft.github.io/PowerBI-JavaScript/demo)。

[“为组织嵌入内容”示例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data)中提供了相关应用示例。

### <a name="viewshomeembeddashboardcshtml"></a>Views\Home\EmbedDashboard.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="dashboardContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'dashboard',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedDashboardId
    };

    // Get a reference to the embedded dashboard HTML element
    var dashboardContainer = $('#dashboardContainer')[0];

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);
</script>
```

### <a name="viewshomeembedtilecshtml"></a>Views\Home\EmbedTile.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="tileContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read tile Id from Model
    var embedTileId = "@Model.Id";

    // Read dashboard Id from Model
    var embedDashboardeId = "@Model.dashboardId";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedTileId,
        dashboardId: embedDashboardeId
    };

    // Get a reference to the embedded tile HTML element
    var tileContainer = $('#tileContainer')[0];

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);
</script>
```

### <a name="viewshomeembedreportcshtml"></a>Views\Home\EmbedReport.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="next-steps"></a>后续步骤

* 可以参考 GitHub 上的示例应用。 上面的示例均以此示例为依据。 有关详细信息，请参阅[“为组织嵌入内容”示例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data)。

* 有关 JavaScript API 的详细信息，请参阅 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)。

* 有关 Power BI for Germany 云的详细信息，请参阅 [Power BI for Germany 云常见问题解答](https://docs.microsoft.com/power-bi/service-govde-faq)

* [如何将 Power BI 工作区集合内容迁移到 Power BI](migrate-from-powerbi-embedded.md)

限制和注意事项

* GCC 帐户现仅支持 P 和 EM 容量

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
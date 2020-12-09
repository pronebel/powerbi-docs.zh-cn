---
title: 为客户实现模板应用安装的自动化配置
description: 了解如何实现模板应用安装的配置自动化。
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 671fcbabf10666c03f39bc4582e00fa0adbdbd5e
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2020
ms.locfileid: "96578351"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>模板应用安装的自动化配置

模板应用有助于客户开始从其数据中获取见解。 模板应用通过与数据连接并提供预生成的报表（可根据需要自定义报表）来快速启动并运行。

客户对有关如何连接到其数据的详细信息不太熟悉，因此，他们可能难以在安装模板应用时提供这些详细信息。

如果你是数据服务提供商，并且创建了一个模板应用来帮助客户在你的服务上开始使用他们的数据，那么可通过自动配置模板应用的参数，让客户更容易安装模板应用。 当客户登录到门户时，他们会单击你准备好的特殊链接。 此操作将会启动自动化来收集所需的信息，预配置模板应用参数，并将客户重定向到他们可在其中安装应用的 Power BI 帐户。 他们只需单击“安装”并对其数据源进行身份验证就可以了！ 

此客户体验如下所示。

![自动安装应用程序的用户体验图示。](media/template-apps-auto-install/high-level-flow.png)

本文介绍自动配置模板应用安装时涉及的基本流程、先决条件、主要步骤以及所需的 API。 但如果你想深入了解并开始使用，可跳到[教程](template-apps-auto-install-tutorial.md)，使用我们准备好的一个使用 Azure Function 的简单示例应用程序，自动配置模板应用安装。

## <a name="basic-flow"></a>基本流程

自动配置模板应用安装时涉及的基本流程如下所示：

1. 用户登录 ISV 的门户并单击提供的链接。 这将启动自动化流程。 ISV 的门户在此阶段准备了用户特定的配置。

2. ISV 根据在 ISV 的租户中注册的[服务主体（仅限应用的令牌）](../embedded/embed-service-principal.md)获取“仅限应用”令牌。

3. 使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)，ISV 将创建“安装票证”，其中包含由 ISV 准备的用户特定参数配置。

4. ISV 使用包含安装票证的 ```POST``` 重定向方法将用户重定向到 Power BI。

5. 通过安装票证将用户重定向到其 Power BI 帐户，并提示他们安装模板应用。 当用户单击“安装”时，将会为其安装模板应用。

>[!Note]
>尽管在创建安装票证时由 ISV 配置参数值，但在安装的最后阶段，只能由用户提供与数据源相关的凭据。 这是为了防止将它们公开给第三方，从而确保用户和模板应用数据源之间的连接安全。

## <a name="prerequisites"></a>先决条件

若要为模板应用提供预配置的安装体验，需要满足以下先决条件：

* Power BI Pro 许可证。 如果没有注册 Power BI Pro，请在开始之前[注册免费试用版](https://powerbi.microsoft.com/pricing/)。

* 自己的 Azure Active Directory 租户设置。 请参阅[创建 Azure Active Directory 租户](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant)，了解如何设置一个租户。

* 在上述租户中注册的服务主体（仅限应用的令牌）。 请参阅[使用服务主体和应用程序机密嵌入 Power BI 内容](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal)，获取更多详细信息。 请务必将应用程序注册为“服务器端 Web 应用程序”应用。 注册服务器端 Web 应用程序以创建应用程序密码。 在此过程中，需要保存“应用程序 ID”（客户端 ID）和“应用程序密码”（客户端密码），以便执行后续步骤 。

* 已准备好安装的参数化模板应用。 必须在将应用程序注册到 Azure Active Directory (Azure AD) 的同一租户中创建模板应用。 有关详细信息，请参阅[模板应用提示](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips)或[在 Power BI 中创建模板应用](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create)。 在模板应用中，需要注意以下信息，以便执行后续步骤：
     * 应用 ID、包密钥和所有者 ID，这些信息显示在创建应用时[定义模板应用的属性](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)过程最后一步的安装 URL 中  。 还可单击模板应用的[发布管理](../../connect-data/service-template-apps-create.md#manage-the-template-app-release)中的“获取链接”，获取相同的链接。

    * 在模板应用的数据集中定义的“参数名称”。 参数名称是区分大小写的字符串，也可在[定义模板应用的属性](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)时从“参数设置”选项卡中进行检索，或从 Power BI 中的数据集设置中进行检索。

    >[!NOTE]
    >如果模板应用已准备好安装，则可在模板应用上测试预配置的安装应用程序，即使该应用尚未在 AppSource 上公开提供。 但是，为了让租户外部的用户能够使用自动化安装应用程序来安装模板应用，模板应用必须在 [Power BI 应用市场](https://app.powerbi.com/getdata/services)中公开提供。 因此，在使用所创建的自动化安装应用程序分发模板应用之前，请务必将其发布到[合作伙伴中心](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer)。

## <a name="main-steps-and-apis"></a>主要步骤和 API

以下各节介绍自动配置模板应用安装时涉及的主要步骤和所需的 API。 尽管大部分步骤都可使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 完成，但下面介绍的代码示例介绍使用 .NET SDK 完成的情况。

## <a name="step-1-create-a-power-bi-client-object"></a>步骤 1：创建 Power BI 客户端对象 

如果使用 Power BI REST API，则需要从 Azure AD 为[服务主体](../embedded/embed-service-principal.md)获取访问令牌 。 必须为 Power BI 应用程序获取 [Azure AD 访问令牌](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data)，然后才能对 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 进行调用。
要使用访问令牌创建 Power BI 客户端，需要创建 Power BI 客户端对象，以便与 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 进行交互。 使用 Microsoft.Rest.TokenCredentials 对象包装“AccessToken”，以创建 Power BI 客户端对象。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>步骤 2：创建安装票证

创建安装票证，将用户重定向到 Power BI 时需要使用该票证。 用于此操作的 API 是 CreateInstallTicket API。
* [模板应用 CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

[示例应用程序](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)中的 [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) 文件提供了为模板应用安装和配置创建安装票证的示例。


下面是使用模板应用 CreateInstallTicket REST API 的代码示例。
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>步骤 3：使用票证将用户重定向到 Power BI

创建安装票证后，可使用它将用户重定向到 Power BI，以便继续执行模板应用安装和配置。 为此，可使用 ```POST``` 方法重定向到模板应用的安装 URL，并将安装票证置于其请求正文中。

使用 ```POST``` 请求发出重定向的方法有多种。 具体选择哪一种方法将取决于方案以及用户与门户或服务的交互方式。

一个简单的示例（主要用于测试目的）利用一个带有隐藏字段的表单，该字段会在加载时自动自行进行提交。

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

下面是[示例应用程序](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)的响应示例，它持有安装票证并自动将用户重定向到 Power BI。 此 Azure Function 的响应实际上与我们在上面的 html 示例中看到的自动自提交表单相同。

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>尽管有各种使用 ```POST``` 浏览器进行重定向的方法，但你应始终使用最安全的方法，具体取决于你的服务需求和限制。 请记住，某些形式的不安全重定向可能导致用户或服务出现安全问题。

## <a name="step-4-move-your-automation-to-production"></a>步骤 4：将自动化移动到生产环境

当你设计的自动化已准备就绪时，请务必将它移动到生产环境。

## <a name="next-steps"></a>后续步骤

* 试用我们的[教程](template-apps-auto-install-tutorial.md)，该教程使用简单的 Azure Function 自动配置模板应用安装。

* 更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

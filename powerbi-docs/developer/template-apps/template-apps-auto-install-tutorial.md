---
title: 使用 Azure Function 自动配置模板应用安装
description: 使用示例应用程序了解如何为客户安装和配置模板应用。
author: paulinbar
ms.author: painbar
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: a44bd7837e7605fd23e49a91e3e9eba106d5a933
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565763"
---
# <a name="tutorial-automate-configuration-of-template-app-installation-using-an-azure-function"></a>教程：使用 Azure Function 自动配置模板应用安装

模板应用有助于客户开始从其数据中获取见解。 模板应用通过将其连接到数据来快速启动并运行。 模板应用为客户提供预先生成的报表，客户可以根据需要对其进行自定义。

客户并不总是熟悉如何连接到其数据的细节。 如果让他们在安装模板应用时提供这些细节对他们来说可能比较困难。

如果你是数据服务提供商，并且创建了一个模板应用来帮助客户在你的服务上开始使用他们的数据，那么可让客户更容易安装模板应用。 你可以自动配置模板应用的参数。

当客户登录到门户时，他们可选择你准备好的特殊链接。 可通过该连接执行以下操作：

- 启动自动化，收集所需的信息。
- 预配置模板应用参数。
- 将客户重定向到可在其中安装应用的 Power BI 帐户。

他们只需选择“安装”并对其数据源进行身份验证就可以了！

此客户体验如下所示。

![自动安装应用程序的用户体验图示。](media/template-apps-auto-install/high-level-flow.png)

本教程将使用我们创建的自动安装 Azure Functions 示例来预配置和安装模板应用。 为了便于演示，故意采用简单的示例。 该示例封装了 Azure Functions 的设置，以利用 Power BI API 来为用户自动安装模板应用并配置它。

有关常规自动化流及其使用的 API 的详细信息，请参阅[自动配置模板应用安装](template-apps-auto-install.md)

我们的简单应用程序使用 Azure Function。 有关 Azure Functions 的详细信息，请参阅 [Azure Functions 文档](/azure/azure-functions/)。

## <a name="basic-flow"></a>基本流程

下面是客户通过选择门户上的链接来启动应用程序时，应用程序执行的基本流程列表。

1. 用户登录 ISV 的门户并选择提供的链接。 此操作将启动流。 ISV 的门户在此阶段准备了用户特定的配置。

1. ISV 根据在 ISV 的租户中注册的[服务主体（仅限应用的令牌）](../embedded/embed-service-principal.md)获取“仅限应用”令牌。

1. 使用 [Power BI REST API](/rest/api/power-bi/)，ISV 将创建“安装票证”，其中包含由 ISV 准备的用户特定参数配置。

1. ISV 使用包含安装票证的 ```POST``` 重定向方法将用户重定向到 Power BI。

1. 通过安装票证将用户重定向到其 Power BI 帐户，并提示他们安装模板应用。 当用户选择“安装”时，将会为其安装模板应用。

>[!Note]
>尽管在创建安装票证的过程中由 ISV 配置参数值，但在安装的最后阶段，只能由用户提供与数据源相关的凭据。 这种安排是为了防止将它们公开给第三方，从而确保用户和模板应用数据源之间的连接安全。

## <a name="prerequisites"></a>先决条件

* 设置你自己的 Azure Active Directory (Azure AD) 租户。 有关如何设置租户的说明，请参阅[创建 Azure Active Directory 租户](../embedded/create-an-azure-active-directory-tenant.md)。
* 在上述租户中注册的[服务主体（仅限应用的令牌）](../embedded/embed-service-principal.md)。
* 已准备好安装的参数化[模板应用](../../connect-data/service-template-apps-overview.md)。 必须在将应用程序注册到 Azure AD 的同一租户中创建模板应用。 有关详细信息，请参阅[模板应用提示](../../connect-data/service-template-apps-tips.md)或[在 Power BI 中创建模板应用](../../connect-data/service-template-apps-create.md)。
* Power BI Pro 许可证。 如果没有注册 Power BI Pro，请在开始之前[注册免费试用版](https://powerbi.microsoft.com/pricing/)。

## <a name="set-up-your-template-apps-automation-development-environment"></a>设置模板应用自动化开发环境

在继续设置应用程序之前，请按照[快速入门：使用 Azure 应用程序配置创建 Azure Functions 应用](/azure/azure-app-configuration/quickstart-azure-functions-csharp)中的说明开发 Azure Function 以及 Azure 应用程序配置。 按照本文中的说明创建应用程序配置。

### <a name="register-an-application-in-azure-ad"></a>在 Azure AD 中注册应用程序

请按照[使用服务主体和应用程序密码嵌入 Power BI 内容](../embedded/embed-service-principal.md)中所述创建服务主体。

请务必将应用程序注册为“服务器端 Web 应用程序”应用。 注册服务器端 Web 应用程序以创建应用程序密码。

保存“应用程序 ID”（客户端 ID）和“应用程序机密”（客户端机密），以便执行后续步骤 。

可通过[嵌入安装程序工具](https://aka.ms/embedsetup/AppOwnsData)快速开始创建应用注册。 如果你使用的是 [Power BI 应用注册工具](https://app.powerbi.com/embedsetup)，请选择“为客户嵌入内容”选项。

## <a name="template-app-preparation"></a>模板应用准备

创建模板应用并准备好进行安装后，请保存以下信息以执行后续步骤：

* 应用 ID、包密钥和所有者 ID，这些信息显示在创建应用时[定义模板应用的属性](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)过程最后一步的安装 URL 中  。

    还可选择模板应用的[“发布管理”窗格](../../connect-data/service-template-apps-create.md#manage-the-template-app-release)中的“获取链接”，获取相同的链接。

* 在模板应用的数据集中定义的“参数名称”。 参数名称是区分大小写的字符串。 也可在[定义模板应用的属性](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)时从“参数设置”选项卡中检索，或从 Power BI 中的数据集设置中检索这些字符串。

>[!NOTE]
>如果模板应用已准备好安装，则可在模板应用上测试预配置的安装应用程序，即使该应用尚未在 AppSource 上公开提供。 为了让租户外部的用户能够使用自动化安装应用程序来安装模板应用，模板应用必须在 [Power BI 应用市场](https://app.powerbi.com/getdata/services)中公开提供。 在使用所创建的自动化安装应用程序分发模板应用之前，请务必将其发布到[合作伙伴中心](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)。


## <a name="install-and-configure-your-template-app"></a>安装和配置模板应用

本节将使用我们创建的自动安装 Azure Functions 示例来预配置和安装模板应用。 为了便于演示，故意采用简单的示例。 它使你可以利用 [Azure Functions](/azure/azure-functions/functions-overview) 和 [Azure 应用程序配置](/azure/azure-app-configuration/overview)来轻松部署和使用适用于你的模板应用的自动安装 API。

### <a name="download-visual-studio-version-2017-or-later"></a>下载 [Visual Studio](https://www.visualstudio.com/)（版本 2017 或更高版本）

下载 [Visual Studio](https://www.visualstudio.com/)（2017 版或更高版本）。 请务必下载最新版 [NuGet 包](https://www.nuget.org/profiles/powerbi)。

### <a name="download-the-automated-installation-azure-functions-sample"></a>下载自动安装 Azure Functions 示例

若要开始，请从 GitHub 下载[自动安装 Azure Functions 示例](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function)。

![显示自动安装 Azure Functions 示例的屏幕截图。](media/template-apps-auto-install/azure-function-sample.png)

### <a name="set-up-your-azure-app-configuration"></a>设置 Azure 应用程序配置

若要运行此示例，需要使用如下所述的值和键设置 Azure 应用程序配置。 键为“应用程序 ID”、“应用程序机密”以及模板应用的“AppId”、“PackageKey”和“OwnerId”值    。 有关如何获取这些值的信息，请参阅以下各节。

这些键还在 Constants.cs 文件中进行了定义。

| 配置密钥 | 含义           |
|---------------    |-------------------|
| TemplateAppInstall:Application:AppId | [安装 URL](#get-the-template-app-properties) 中的 AppId |
| TemplateAppInstall:Application:PackageKey | [安装 URL](#get-the-template-app-properties) 中的 PackageKey |
| TemplateAppInstall:Application:OwnerId | [安装 URL](#get-the-template-app-properties) 中的 OwnerId |
| TemplateAppInstall:ServicePrincipal:ClientId | 服务主体[应用程序 ID](#get-the-application-id) |
| TemplateAppInstall:ServicePrincipal:ClientSecret | 服务主体[应用程序机密](#get-the-application-secret) |
|||


Constants.cs 文件如下所示：

![显示 Constant.cs 文件的屏幕截图。](media/template-apps-auto-install/constants-app-configuration.png)

#### <a name="get-the-template-app-properties"></a>获取模板应用属性

填写创建应用时定义的所有相关模板应用属性。 这些属性是模板应用的“AppId”、“PackageKey”和“OwnerId”值  。

若要获取上述值，请执行以下步骤：

1. 登录 [Power BI](https://app.powerbi.com)。

1. 转到应用程序的原始工作区。

1. 打开“发布管理”窗格。

    ![显示“发布管理”窗格的屏幕截图。](media/template-apps-auto-install/release-management-001.png)

1. 选择应用版本并获取其安装链接。

    ![显示“发布管理”按钮的屏幕截图。](media/template-apps-auto-install/release-management-002.png)

1. 将链接复制到剪贴板。

    ![显示“获取链接”按钮的屏幕截图。](media/template-apps-auto-install/release-management-003.png)

1. 此安装 URL 包含需要其值的 3 个 URL 参数。 使用应用程序的“appId”、“packageKey”“ownerId”值  。 示例 URL 与下面显示的内容相似。

    ```html
    https://app.powerbi.com/Redirect?action=InstallApp&appId=3c386...16bf71c67&packageKey=b2df4b...dLpHIUnum2pr6k&ownerId=72f9...1db47&buildVersion=5
    ```

#### <a name="get-the-application-id"></a>获取应用程序 ID

将 Azure 中的“应用 ID”填入“ApplicationID”字段。 应用使用“applicationId”值对你向其请求获取权限的用户标识自身。

若要获取应用程序 ID，请按以下步骤操作：

1. 登录 [Azure 门户](https://portal.azure.com)。

1. 在左窗格中，选择“所有服务” > “应用注册” 。

    ![显示应用注册搜索的屏幕截图。](media/template-apps-auto-install/embed-sample-for-customers-003.png)

1. 选择需要应用程序 ID 的应用程序。

    ![显示选择应用的屏幕截图。](media/template-apps-auto-install/embed-sample-for-customers-006.png)

1. 存在列为 GUID 的应用程序 ID。 使用此应用程序 ID 作为应用程序的“applicationID”值。

    ![显示 applicationId 值的屏幕截图。](media/template-apps-auto-install/embed-sample-for-customers-007.png)

#### <a name="get-the-application-secret"></a>获取应用程序密码

将 Azure 的“应用注册”部分中的“密钥”部分信息填入“ApplicationSecret”字段  。 使用[服务主体](../embedded/embed-service-principal.md)时，此属性适用。

若要获取应用程序密码，请按以下步骤操作：

 1. 登录 [Azure 门户](https://portal.azure.com)。

 1. 在左窗格中，选择“所有服务” > “应用注册” 。

    ![显示应用注册搜索的屏幕截图。](media/template-apps-auto-install/embed-sample-for-customers-003.png)

1. 选择需要使用应用程序机密的应用。

    ![显示选择应用的屏幕截图。](media/template-apps-auto-install/embed-sample-for-customers-0038.png)

1. 在“管理”下选择“证书和密码” 。

1. 选择“新的客户端密码”。

1. 在“说明”框中输入一个名称并选择持续时间。 然后选择“保存”为应用程序获取值。 如果在保存密钥值后关闭“密钥”窗格，“值”字段会仅显示为隐藏状态 。 此时，你无法检索密钥值。 如果忘记了密钥值，请在 Azure 门户中新建密钥值。

    ![显示密钥值的屏幕截图。](media/template-apps-auto-install/embed-sample-for-customers-042.png)

## <a name="test-your-function-locally"></a>在本地测试函数

按照[在本地运行函数](/azure/azure-functions/functions-create-your-first-function-visual-studio#run-the-function-locally)中所述的步骤运行函数。

配置门户以向函数的 URL 发出 ```POST``` 请求。 示例为 ```POST http://localhost:7071/api/install```。 请求正文应为描述键值对的 JSON 对象。 键是 Power BI Desktop 中定义的参数名称。 值是要为模板应用中的每个参数设置的所需值。

>[!Note]
> 在生产中，将根据门户的预期逻辑推导每个用户的参数值。

所需的流应为：

1. 门户按用户或会话准备请求。
1. 向 Azure Function 发出 ```POST /api/install``` 请求。 请求正文包含键值对。 键是参数名称。 值是要设置的所需值。
1. 如果正确进行了所有配置，浏览器应会自动重定向到客户的 Power BI 帐户并显示自动安装流。
1. 安装后，将按照步骤 1 和 2 中的配置设置参数值。
 
## <a name="next-steps"></a>后续步骤

### <a name="publish-your-project-to-azure"></a>将项目发布到 Azure

若要将项目发布到 Azure，请按照 [Azure Functions 文档](/azure/azure-functions/functions-create-your-first-function-visual-studio#publish-the-project-to-azure)中的说明进行操作。 然后，可以将模板应用自动安装 API 集成到产品中，并开始在生产环境中对其进行测试。
---
title: 为客户将内容嵌入应用程序
description: 了解如何将报表、仪表板或磁贴嵌入 Power BI 嵌入式分析示例。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/02/2020
ms.openlocfilehash: 7bc825992f5c7382e1c0a24783f732957913c588
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96907116"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>教程：使用“为客户嵌入内容”应用程序嵌入 Power BI 内容

通过“嵌入式分析”和“Power BI Embedded”，可以将 Power BI 内容（例如报表、仪表板和磁贴）嵌入到应用程序中 。

本教程介绍以下操作：
>[!div class="checklist"]
>* 设置嵌入式环境。
>* 配置“为客户嵌入内容”（也称为“应用拥有数据”）示例应用程序 。

用户无需登录到 Power BI 或拥有 Power BI 许可证即可使用应用程序。

如果你是独立软件供应商 (ISV) 或开发人员，并希望为第三方创建应用程序，建议你使用“为客户嵌入内容”方法来嵌入 Power BI 内容。

## <a name="code-sample-specifications"></a>代码示例规范

本教程说明了如何采用下列语言之一配置“为客户嵌入内容”示例应用程序：

* .NET framework
* .NET Core
* Java
* Node JS
* Python

代码示例支持下列浏览器：

* Google Chrome

* Microsoft Edge

* Mozilla Firefox

## <a name="prerequisites"></a>先决条件

开始学习本教程之前，请确认你具有下方列出的 Power BI 和代码依赖项：

* **Power BI 依赖项**

    * 你自己的 [Azure Active Directory 租户](create-an-azure-active-directory-tenant.md)。

    * 若要向 Power BI 对应用进行身份验证，需执行以下操作之一：

        * [服务主体](embed-service-principal.md) - 允许 Azure AD 对应用进行身份验证的 Azure Active Directory (Azure AD) [服务主体对象](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)。

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) 许可证 - 这将是你的主用户，你的应用将使用它来向 Power BI 进行身份验证。

        * Power BI [Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) 许可证 - 这将是你的主用户，你的应用将使用它来向 Power BI 进行身份验证。

    >[!NOTE]
    >若要[迁移到生产环境](move-to-production.md)，则需要[容量](embedded-capacity.md)。

* **代码依赖项**

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)
    
    
    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core)（或更高版本）
    
    * 集成开发环境 (IDE)。 建议使用以下项之一：
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK（或 JRE）](https://www.oracle.com/java/technologies/)
    
    * [Eclipse IDE](https://www.eclipse.org/downloads/packages/) - 确认具有 Eclipse for Java EE Developers（企业版）
    
    * [Apache Tomcat Binary Distributions](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * 集成开发环境 (IDE)。 建议使用以下项之一：
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/)（或更高版本）
    
        >[!NOTE]
        >* 如果是首次安装 Python，请选择“将 Python 添加到 PATH”选项，以将安装添加到 `PATH` 变量。
        >* 如果已安装 Python，请确认 `PATH` 变量包括其安装路径。 有关详细信息，请参阅[附录：设置环境变量](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) Python 文档（此链接指的是 Python 3）。
    
    * 集成开发环境 (IDE)。 建议使用以下项之一：
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>方法

若要创建“为客户嵌入内容”示例应用，请执行以下步骤：

1. [选择身份验证方法](#step-1---select-your-authentication-method)。

2. [注册 Azure AD 应用程序](#step-2---register-an-azure-ad-application)。

3. [创建 Power BI 工作区](#step-3---create-a-power-bi-workspace)。

4. [创建并发布 Power BI 报表](#step-4---create-and-publish-a-power-bi-report)。

5. [获取嵌入的参数值](#step-5---get-the-embedding-parameter-values)。

6. [服务主体 API 访问](#step-6---service-principal-api-access)
 
7. [启用工作区访问](#step-7---enable-workspace-access)。

8. [嵌入内容](#step-8---embed-your-content)。

## <a name="step-1---select-your-authentication-method"></a>步骤 1 - 选择身份验证方法

嵌入式解决方案将因所选的身份验证方法而异。 因此，请先了解身份验证方法之间的区别，然后再确定最适合你的解决方案的方法。

下表描述了[服务主体](embed-service-principal.md)与主用户身份验证方法之间的一些主要差异。

|注意事项  |服务主体  |主用户  |
|---------|---------|---------|
|机制     |Azure AD 应用的[服务主体对象](/azure/active-directory/develop/app-objects-and-service-principals.md#service-principal-object)允许 Azure AD 向 Power BI 对嵌入式解决方案应用进行身份验证。        |Azure AD 应用使用 Power BI 用户的凭据（用户名和密码）向 Power BI 进行身份验证。         |
|安全性     |服务主体是 Azure AD 建议的授权方法。 如果使用服务主体，则可使用应用程序机密或证书进行身份验证 。</br></br>本教程仅介绍如何结合使用服务主体和应用程序机密 。 若要使用服务主体和证书嵌入内容，请参阅[服务主体和证书](embed-service-principal-certificate.md)一文 。         |此身份验证方法不如使用服务主体安全。 这是因为必须警惕主用户凭据（用户名和密码）。 例如，不能在嵌入的应用程序中公开它们，而应经常更改密码。         |
|Azure AD 委托的权限 |不需要。 |你的主用户或管理员必须授予你的应用访问 Power BI REST API [权限](/azure/active-directory/develop/v2-permissions-and-consent)（也称为范围）的许可。 例如 Report.ReadWrite.All。 |
|Power BI 服务的访问 |无法使用服务主体访问 Power BI 服务。|可使用主用户凭据访问 Power BI 服务。|
|许可证     |不需要 Pro 许可证。 可使用任何工作区中的内容（如果你是该工作区的成员或管理员）。         |需要 [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) 许可证。         |

## <a name="step-2---register-an-azure-ad-application"></a>步骤 2 - 注册 Azure AD 应用程序

向 Azure AD 注册应用程序可以：
> [!div class="checklist"]
>* 为应用创建标识
>* 让你的应用访问 [Power BI REST API](/rest/api/power-bi/)
>* 如果使用主用户：请指定应用的 [Power BI REST 权限](/azure/active-directory/develop/v2-permissions-and-consent)

若要向 Azure AD 注册应用程序，请按照 [注册应用程序](register-app.md)中的说明进行操作。

>[!NOTE]
>注册应用程序之前，需要确定要使用的身份验证方法、服务主体或主用户 。

## <a name="step-3---create-a-power-bi-workspace"></a>步骤 3 - 创建 Power BI 工作区

Power BI 将报表、仪表板和磁贴存储在工作区中。 若要嵌入这些项，需要创建它们并将其上传到工作区。

>[!TIP]
>如果你已具有工作区，则可跳过此步骤。

若要创建工作区，请执行以下操作：

1. 登录到 Power BI。

2. 选择“工作区”。

3. 选择“创建工作区”。

4. 为工作区命名，然后选择“保存”。

## <a name="step-4---create-and-publish-a-power-bi-report"></a>步骤 4 - 创建并发布 Power BI 报表

下一步是创建报表并将其上传到工作区。 你可使用 Power BI Desktop [创建自己的报表](/powerbi-docs/fundamentals/desktop-getting-started#build-reports)，然后将其[发布](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work)到工作区。 也可将示例报表上传到你的工作区。

>[!Tip]
>如果你的工作区中已有一个报表，则可跳过此步骤。

若要下载示例报表并将其发布到工作区，请执行以下步骤：

1. 打开 GitHub [Power BI Desktop 示例](https://github.com/microsoft/PowerBI-Developer-Samples)文件夹。

2. 选择“代码”，再选择“下载 zip” 。

    :::image type="content" source="media/embed-sample-for-customers/download-sample-report.png" alt-text="在 Power BI桌面示例 GitHub 中显示 ZIP 下载选项的屏幕截图":::

3. 提取已下载的 ZIP 并导航到“Samples Reports”文件夹。

4. 选择要嵌入的报表，并将其[发布](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work)到工作区。

## <a name="step-5---get-the-embedding-parameter-values"></a>步骤 5 - 获取嵌入的参数值

若要嵌入内容，需要获取某些参数值。 下表显示了所需的值并指出了它们是适用于服务主体身份验证方法、主用户身份验证方法还是同时适用于这两种方法 。

嵌入内容之前，请确保你具有下方列出的所有值。 某些值将有所不同，具体取决于所使用的身份验证方法：

|参数   |服务主体   |主用户  |
|-------------------|---|---|
|[客户端 ID](#client-id) |![适用于](../../media/yes.png) |![适用于](../../media/yes.png) |
|[工作区 ID](#workspace-id)     |![适用于](../../media/yes.png) |![适用于](../../media/yes.png) |
|[报表 ID](#report-id)           |![适用于](../../media/yes.png) |![适用于](../../media/yes.png) |
|[客户端机密](#client-secret) |![适用于](../../media/yes.png) |![不适用于：](../../media/no.png) |
|[租户 ID](#tenant-id)                 |![适用于](../../media/yes.png) |![不适用于：](../../media/no.png) |
|[Power BI 用户名](#power-bi-username-and-password)   |![不适用于：](../../media/no.png) |![适用于](../../media/yes.png) |
|[Power BI 密码](#power-bi-username-and-password)   |![不适用于：](../../media/no.png) |![适用于](../../media/yes.png) |

### <a name="client-id"></a>客户端 ID

>[!TIP]
>**适用于：** ![适用于：](../../media/yes.png)服务主体 ![适用于：](../../media/yes.png)主用户

若要获取客户端 ID GUID（也称为“应用程序 ID”），请执行以下步骤：

1. 登录 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜索“应用程序注册”，然后选择“应用程序注册”链接。

3. 选择用于嵌入 Power BI 内容的 Azure AD 应用。

4. 从“概述”部分，复制“应用程序(客户端) ID”GUID 。

### <a name="workspace-id"></a>工作区 ID

>[!TIP]
>**适用于：** ![适用于：](../../media/yes.png)服务主体 ![适用于：](../../media/yes.png)主用户

若要获取工作区 ID GUID，请执行以下步骤：

1. 登录 Power BI 服务。

2. 打开要嵌入的报表。

3. 复制 URL 中的 GUID。 GUID 是 /groups/ 和 /reports/ 之间的数字 。

    :::image type="content" source="media/embed-sample-for-customers/workspace-id.png" alt-text="显示 Power BI 服务 URL 中的工作区 ID GUID 的屏幕截图":::

### <a name="report-id"></a>报表 ID

>[!TIP]
>**适用于：** ![适用于：](../../media/yes.png)服务主体 ![适用于：](../../media/yes.png)主用户

1. 登录 Power BI 服务。

2. 打开要嵌入的报表。

3. 复制 URL 中的 GUID。 GUID 是 /reports/ 和 /ReportSection 之间的数字 。

    :::image type="content" source="media/embed-sample-for-customers/report-id.png" alt-text="显示 Power BI 服务 URL 中的报表 ID GUID 的屏幕截图":::

### <a name="client-secret"></a>客户端机密

>[!TIP]
>**适用于：** ![适用于：](../../media/yes.png)服务主体 ![不适用于：](../../media/no.png)主服务

若要获取客户端机密，请执行下列步骤：

1. 登录 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜索“应用程序注册”，然后选择“应用程序注册”链接。

3. 选择用于嵌入 Power BI 内容的 Azure AD 应用。

4. 在“管理”下，选择“证书和机密”。  

5. 在“客户端机密”下，选择“新建客户端密钥” 。

6. 在“添加客户端机密”弹出窗口中，提供应用程序机密的说明，选择应用程序机密过期时间，然后选择“添加” 。

7. 从“客户端机密”部分，复制新创建的应用程序机密的“值”列中的字符串 。 客户端机密值为你的客户端 ID。

### <a name="tenant-id"></a>租户 ID

>[!TIP]
>**适用于：** ![适用于：](../../media/yes.png)服务主体 ![不适用于：](../../media/no.png)主服务

若要获取租户 ID GUID，请执行以下步骤：

1. 登录 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜索“应用程序注册”，然后选择“应用程序注册”链接。

3. 选择用于嵌入 Power BI 内容的 Azure AD 应用。

4. 从“概述”部分，复制“目录(租户) ID”GUID 。

### <a name="power-bi-username-and-password"></a>Power BI 用户名和密码

>[!TIP]
>**适用于：** ![不适用于：](../../media/no.png)服务主体 ![适用于：](../../media/yes.png)主用户

获取用作主用户的 Power BI 用户的用户名和密码 。 此用户与用于创建工作区并将报表上传到 Power BI 服务的用户相同。

## <a name="step-6---service-principal-api-access"></a>步骤 6 - 服务主体 API 访问

>[!TIP]
>**适用于：** ![适用于：](../../media/yes.png)服务主体 ![不适用于：](../../media/no.png)主服务
>
>仅当使用服务主体身份验证方法时，此步骤才适用。 如果使用主用户，请跳过此步骤，并继续执行步骤 7（[启用工作区访问](#step-7---enable-workspace-access)）。

为了让 Azure AD 应用程序能够访问 Power BI 内容和 API，Power BI 管理员必须在 Power BI 管理门户中启用服务主体访问权限。 如果你不是租户的管理员，请让租户的管理员为你启用“租户设置”。
        
1. 在 Power BI 服务中，选择“设置” > “设置” > “管理员门户”  。
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="显示 Power B I“服务设置”菜单中的“管理员设置”菜单选项的屏幕截图":::
        
2. 选择“租户设置”，然后向下滚动到“开发人员设置”部分 。
        
3. 展开“允许服务主体使用 Power BI API”，然后启用此选项。
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="显示如何启用 Power B I 服务中“租户设置”菜单选项中的“开发人员设置”选项的屏幕截图":::
        
>[!NOTE]
>使用服务主体时，建议使用安全组限制对租户设置的访问 。 若要了解有关此功能的详细信息，请参阅[服务主体](embed-service-principal.md)文章中的以下部分：
> * [创建 Azure AD 安全组](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [启用 Power BI 服务管理设置](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>步骤 7 - 启用工作区访问

要使 Azure AD 应用能够访问 Power BI 服务中的项目（如报表、仪表板和数据集），请以成员或管理员身份将服务主体或主用户添加到工作区   。

1. 登录 Power BI 服务。

2. 滚动到要能够访问的工作区，然后选择“更多”菜单中的“工作区访问”。

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="显示 Power BI 工作区的“更多”菜单中的“工作区访问”按钮的屏幕截图。":::

3. 在“访问”窗格中，根据所使用的身份验证方法，将服务主体或主用户复制到“输入电子邮件地址”文本框中 。

    >[!NOTE]
    >如果使用的是服务主体，则服务主体的名称就是你为 Azure AD 应用指定的名称。

5. 选择 **添加** 。

## <a name="step-8---embed-your-content"></a>步骤 8 - 嵌入内容

使用 Power BI Embedded 示例应用程序，可以创建“为客户嵌入内容”Power BI 应用。

请按照以下步骤来修改“为客户嵌入内容”示例应用程序，以便嵌入 Power BI 报表。  

1. 打开 [Power BI 开发人员示例](https://github.com/microsoft/PowerBI-Developer-Samples)文件夹。

2. 选择“代码”，再选择“下载 zip” 。

    :::image type="content" source="media/embed-sample-for-customers/developer-samples.png" alt-text="在 Power BI 开发人员示例 GitHub 中显示 ZIP 下载选项的屏幕截图":::

3. 提取已下载的 ZIP 并导航到“PowerBI-Developer-Samples-master”文件夹。

4. 根据你希望应用程序使用的语言，打开以下文件夹之一：

* .NET Core
* .NET Framework
* Java
* Node JS
* Python
    >[!NOTE]
    >“为客户嵌入内容”示例应用程序仅支持上面列出的语言。 “React TS”示例应用程序仅支持[为组织嵌入内容](embed-sample-for-your-organization.md)解决方案 。

5. 打开“Embed for your customers”文件夹。

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. 使用以下方法之一打开“为客户嵌入内容”示例应用：

    * 如果使用 [Visual Studio](https://visualstudio.microsoft.com/)，请打开 AppOwnsData.sln 文件。

    * 如果使用 [Visual Studio](https://code.visualstudio.com/)，请打开“App Owns Data”文件夹。

7. 打开 appsettings.json。

8. 根据身份验证方法，填写以下参数值：

    |参数            |服务主体  |主用户  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |服务主体         |MasterUser         |
    |`ClientId`           |Azure 应用[客户端 ID](#client-id)。         |Azure 应用[客户端 ID](#client-id)。         |
    |`TenantId`           |Azure AD [租户 ID](#tenant-id)         |空值         |
    |`PbiUsername`        |空值         |主用户的用户名，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`PbiPassword`        |空值         |主用户的密码，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`ClientSecret`       |Azure AD [客户端机密](#client-secret)         |空值         |
    |`WorkspaceId`        |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)          |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)         |
    |`ReportId`           |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)            |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)         |

9. 通过选择适当的选项来运行项目：

    * 如果使用 Visual Studio，请选择“IIS Express”（播放） 。

    * 如果使用 Visual Studio Code，请选择“运行”>“启动调试” 。

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. 如果使用 [Visual Studio](https://visualstudio.microsoft.com/)，请打开 AppOwnsData.sln 文件。

7. 打开 Web.config。

8. 根据身份验证方法，填写以下参数值：

    |参数            |服务主体  |主用户  |
    |---------------------|---------|---------|
    |`authenticationType` |服务主体         |MasterUser         |
    |`applicationId`           |Azure 应用[客户端 ID](#client-id)。         |Azure 应用[客户端 ID](#client-id)。         |
    |`workspaceId`        |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)          |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)         |
    |`reportId`           |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)            |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)         |
    |`pbiUsername`        |空值         |主用户的用户名，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`pbiPassword`        |空值         |主用户的密码，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`applicationSecret`       |Azure AD [客户端机密](#client-secret)         |空值         |
    |`tenant`           |Azure AD [租户 ID](#tenant-id)         |空值         |

9. 通过选择“IIS Express”（播放）来运行项目。

>[!NOTE]
>如果在运行示例应用时看不到嵌入的报表，请按照以下步骤刷新 Power BI 包：
>1. 右键单击项目名称 (AppOwnesData)，然后选择“管理 NuGet 包”。
>2. 搜索 Power BI JavaScript，然后重新安装包。
>
>有关详细信息，请参阅[如何重新安装和更新包](/nuget/consume-packages/reinstalling-and-updating-packages)。

# <a name="java"></a>[Java](#tab/java)

6. 打开 Eclipse 并按照下方的说明进行操作。

    >[!NOTE]
    >有关“为客户嵌入内容”的 Java 示例应用说明，请参阅 [Eclipse IDE for Java EE Developers](https://www.eclipse.org/downloads/packages/)（企业版）。 如果使用的是其他应用程序，则必须自行设置。

7. 将 Tomcat 服务器添加到 Eclipse：

    a. 选择“窗口” > “显示视图” > “服务器”  。

    b. 在“服务器”选项卡中，选择“无可用服务器。请单击此链接创建新服务。”

    c. 在“定义新服务器”窗口中，展开 Apache，然后选择要在计算机上运行的 Tomcat 服务器 。 例如 Tomcat v9.0 服务器。

    d. 选择“下一步”  。

    e. 在“Tomcat 服务器”窗口中，选择“浏览”并导航到包含 Tomcat 服务器的文件夹 。

    f. 在“Tomcat 服务器”窗口中，选择“安装的 JRE” 。

    g. 在“安装的 JRE”窗口中，选择可用的 JRE，然后选择“应用并关闭”。

    h. 在“Tomcat 服务器”窗口中，选择“完成” 。 可以在“服务器”选项卡中查看 Tomcat 服务器。

8. 在 Eclipse 中打开项目：

    >[!IMPORTANT]
    >如果路径名称太长，Eclipse 可能会遇到问题。 若要避免此问题，请确认示例应用的文件夹在计算机的文件夹结构中未嵌入太深。

    a. 选择“文件”，然后选择“从文件系统打开项目” 。

    b. 在“从文件系统或存档中导入项目”窗口中，选择“目录”并打开 AppOwnsData 文件夹  。

    c. 选择“完成”。

9. 将 Tomcat 服务器添加到项目：

    a. 在“包资源管理器”窗格中，右键单击 AppOwnsData，然后选择“属性”  。

    b. 在“AppOwnesData 的属性”窗口中，选择“目标运行时”，然后选择“Apache Tomcat”  。 此选择将包括你正在使用的 Apache Tomcat 版本，例如 Apache Tomact 9.0 。

    c. 选择“应用并关闭”。

10. 填写必填参数。

    a. 在“包资源管理器”中，展开 AppOwnsData 项目 。

    b. 展开“Java 资源”。

    c. 展开 src。

    d. 展开 com.embedsample.appoensdata.config。

    e. 打开 Config.java。

    f. 根据身份验证方法，填写以下参数值：

    |参数            |服务主体  |主用户  |
    |---------------------|---------|---------|
    |`authenticationType` |服务主体         |MasterUser         |
    |`workspaceId`        |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)          |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)         |
    |`reportId`           |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)            |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)         | 
    |`clientId`           |Azure 应用[客户端 ID](#client-id)。         |Azure 应用[客户端 ID](#client-id)。         |
    |`pbiUsername`        |空值         |主用户的用户名，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`pbiPassword`        |空值         |主用户的密码，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`tenantId`           |Azure AD [租户 ID](#tenant-id)         |空值         |
    |`appSecret`       |Azure AD [客户端机密](#client-secret)         |空值         |

11. 运行项目

    a. 在包资源管理器中，右键单击 AppOwnesData 。

    b. 选择“运行方式”  > “在服务器上运行 ”。

    c. 在“在服务器上运行”窗口中，选择“选择现有服务器”，再选择 Tomcat 服务器 。

    d. 选择“完成”。

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. 使用首选的 IDE 打开“App Owns Data”文件夹。 建议使用以下项之一：

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. 通过执行以下操作打开终端并安装所需的依赖项：`npm install`。

8. 展开 Config 文件夹，然后打开 config.json 。

9. 根据身份验证方法，填写以下参数值：

    |参数            |服务主体  |主用户  |
    |---------------------|---------|---------|
    |`authenticationMode` |服务主体         |MasterUser         |
    |`clientId`           |Azure 应用[客户端 ID](#client-id)。         |Azure 应用[客户端 ID](#client-id)。         |
    |`workspaceId`        |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)          |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)         |
    |`reportId`           |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)            |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)         |
    |`pbiUsername`        |空值         |主用户的用户名，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`pbiPassword`        |空值         |主用户的密码，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`clientSecret`       |Azure AD [客户端机密](#client-secret)         |空值         |
    |`tenantId`           |Azure AD [租户 ID](#tenant-id)         |空值         |

10. 通过执行以下操作运行项目：

    a. 在 IDE 终端中执行 `npm start`。

    b. 在浏览器中打开新选项卡并导航到 [http://localhost:5300](http://localhost:5300)。

# <a name="python"></a>[Python](#tab/python)

6. 打开 PowerShell 或命令提示符 。

7. 确认你处于 Python  > “Embed for your customers”文件夹中，并且该文件夹还包括 requirements.txt 文件，然后运行 `pip3 install -r requirements.txt`  。

8. 使用首选的 IDE 打开“App Owns Data”文件夹。 建议使用以下项之一：

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. 打开 config.py。

10. 根据身份验证方法，填写以下参数值：

    |参数            |服务主体  |主用户  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |服务主体         |MasterUser         |
    |`WORKSPACE_ID`        |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)          |包含嵌入报表的工作区的 ID，请参阅[工作区 ID](#workspace-id)         |
    |`REPORT_ID`           |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)            |要嵌入的报表的 ID，请参阅[报表 ID](#report-id)         |
    |`TENANT_ID`           |Azure AD [租户 ID](#tenant-id)         |空值         |
    |`CLIENT_ID`           |Azure 应用[客户端 ID](#client-id)。         |Azure 应用[客户端 ID](#client-id)。         |
    |`CLIENT_SECRET`       |Azure AD [客户端机密](#client-secret)         |空值         |
    |`POWER_BI_USER`        |空值         |主用户的用户名，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |
    |`POWER_BI_PASS`        |空值         |主用户的密码，请参阅 [Power BI 用户名和密码](#power-bi-username-and-password)         |

11. 保存文件。

12. 通过执行以下操作运行项目：

    a. 在 PowerShell 或命令提示符中，导航到 Python  > “Embed for your customers” > “AppOwnesData”文件夹，并执行 `flask run`    。

    b. 在浏览器中打开新选项卡并导航到 [http://localhost:5300](http://localhost:5300)。

---

## <a name="developing-your-application"></a>开发应用程序

配置并运行“为客户嵌入内容”示例应用程序后，可以开始开发自己的应用程序。

准备就绪后，请查看[迁移到生产环境](move-to-production.md)要求。 还需要[容量](embedded-capacity.md)，并应查看[容量计划](embedded-capacity-planning.md)一文，以创建最能满足你需求的 SKU。


## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
>[转移到生产环境](move-to-production.md)

>[!div class="nextstepaction"]
>[为组织嵌入内容](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[为客户嵌入分页报表](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[为组织嵌入分页报表](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[在 Power BI 社区提问](https://community.powerbi.com/)
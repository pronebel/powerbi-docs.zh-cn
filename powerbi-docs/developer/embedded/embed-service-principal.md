---
title: 使用服务主体和应用程序机密嵌入 Power BI 内容
description: 了解如何使用 Azure Active Directory 应用程序服务主体和应用程序机密对嵌入的分析进行身份验证。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 05/12/2020
ms.openlocfilehash: e9faa50cd7e2c4a1a51dfb4a72dda950cf3a396a
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746783"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>使用服务主体和应用程序机密嵌入 Power BI 内容

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

本文介绍了如何使用应用程序 ID 和应用程序密码进行服务主体身份验证。

>[!NOTE]
>建议使用证书而不是机密密钥来保护后端服务。
>* [详细了解如何使用机密密钥或证书从 Azure AD 获取访问令牌](/azure/architecture/multitenant-identity/client-assertion)。
>* [使用服务主体和证书嵌入 Power BI 内容](embed-service-principal-certificate.md)。

## <a name="method"></a>方法

若要将服务主体和应用程序 ID 与嵌入式分析结合使用，请按照以下步骤操作：

1. 创建 [Azure AD 应用程序](/azure/active-directory/manage-apps/what-is-application-management)。

    1. 创建 Azure AD 应用程序密码。
    
    2. 获取应用程序的应用程序 ID 和应用程序密码。

    >[!NOTE]
    >“第 1 步”中介绍了这些步骤。 若要详细了解如何创建 Azure AD 应用程序，请参阅[创建 Azure AD 应用程序](/azure/active-directory/develop/howto-create-service-principal-portal)一文。

2. 创建 Azure AD 安全组。

3. 启用 Power BI 服务管理设置。

4. 将服务主体添加到工作区中。

5. 嵌入内容。

> [!IMPORTANT]
> 在使服务主体可用于 Power BI 后，应用程序的 AD 权限将不再有效。 然后，将通过 Power BI 管理门户管理应用程序权限。

## <a name="step-1---create-an-azure-ad-app"></a>第 1 步 - 创建 Azure AD 应用程序

使用下面的一种方法来创建 Azure AD 应用程序：
* 在 [Microsoft Azure 门户](https://portal.azure.com/#allservices)中创建应用程序
* 使用 [PowerShell](/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1) 创建应用程序。

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>在 Microsoft Azure 门户中创建 Azure AD 应用程序

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. 单击“证书和密码”选项卡。

     ![屏幕截图展示了 Azure 门户中应用的“证书和机密”窗格。](media/embed-service-principal/certificates-and-secrets.png)


8. 单击“新建客户端密码”

    ![新建客户端密码](media/embed-service-principal/new-client-secret.png)

9. 在“添加客户端密码”窗口中，输入描述，指定所需的客户端密码到期时间，然后单击“添加”。

10. 复制并保存“客户端密码”值。

    ![“客户端密码”值](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >在你离开此窗口后，客户端密码值将会隐藏起来，你将无法再次查看或复制它。

### <a name="creating-an-azure-ad-app-using-powershell"></a>使用 PowerShell 创建 Azure AD 应用程序

此部分中包含使用 [PowerShell](/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0) 新建 Azure AD 应用程序的示例脚本。

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>第 2 步 - 创建 Azure AD 安全组

服务主体无权访问你的任何 Power BI 内容和 API。 若要向服务主体授予访问权限，请在 Azure AD 中创建安全组，并将创建的服务主体添加到此安全组中。

创建 Azure AD 安全组有以下两种方法：
* 手动（在 Azure 中）
* 使用 PowerShell

### <a name="create-a-security-group-manually"></a>手动创建安全组

若要手动创建 Azure 安全组，请按照[使用 Azure Active Directory 创建基本组并添加成员](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)一文中的说明操作。 

### <a name="create-a-security-group-using-powershell"></a>使用 PowerShell 创建安全组

下面的示例脚本用于新建安全组，并向此安全组中添加应用程序。

>[!NOTE]
>若要为整个组织启用服务主体访问权限，请跳过这一步。

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>第 3 步 - 启用 Power BI 服务管理设置

为了让 Azure AD 应用程序能够访问 Power BI 内容和 API，Power BI 管理员必须在 Power BI 管理门户中启用服务主体访问权限。

在“开发人员设置”中，将你在 Azure AD 中创建的安全组添加到特定安全组部分。

>[!IMPORTANT]
>服务主体有权访问为其启用的任何租户设置。 这包括特定安全组或整个组织，具体视管理设置而定。
>
>若要限制服务主体只能访问特定租户设置，请只允许访问特定安全组。 也可以为服务主体创建专用安全组，并将它排除在相应租户设置之外。

![管理门户](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>第 4 步 - 将服务主体添加到工作区

若要让 Azure AD 应用程序能够访问 Power BI 服务中的项目（如报表、仪表板和数据集），请以成员或管理员身份将服务主体实体添加到工作区。

>[!NOTE]
>此部分提供了 UI 说明。 也可以使用[“组 - 添加组用户”API](/rest/api/power-bi/groups/addgroupuser) 将服务主体添加到工作区。

1. 滚动到要能够访问的工作区，然后选择“更多”菜单中的“工作区访问”。

    ![工作区设置](media/embed-service-principal/workspace-access.png)

2. 以管理员或成员身份将服务主体添加到工作区。

    ![工作区管理员](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>第 5 步 - 嵌入内容

可以在示例应用程序或你自己的应用程序中嵌入内容。

* [使用示例应用程序嵌入内容](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [在应用程序中嵌入内容](embed-sample-for-customers.md#embed-content-within-your-application)

嵌入内容后，你便可以[迁移到生产阶段](embed-sample-for-customers.md#move-to-production)。

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[注册应用](register-app.md)

> [!div class="nextstepaction"]
>[适用于客户的 Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Azure Active Directory 中的应用程序和服务主体对象](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[配合使用本地数据网关与服务主体的行级别安全性](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[使用服务主体和证书嵌入 Power BI 内容](embed-service-principal-certificate.md)
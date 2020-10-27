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
ms.date: 10/15/2020
ms.openlocfilehash: 6f6a13f239d1bcfa7731361f4efcd129da7e2031
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197718"
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

* 使用 [PowerShell](/powershell/azure/create-azure-service-principal-azureps) 创建应用程序。

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>在 Microsoft Azure 门户中创建 Azure AD 应用程序

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. 单击“证书和密码”选项卡。

     ![展示 Azure 门户中应用的“证书和密码”窗格的屏幕截图。](media/embed-service-principal/certificates-and-secrets.png)


8. 单击“新建客户端密码”

    ![展示“证书和密码”窗格中的“新建客户端密码”按钮的屏幕截图。](media/embed-service-principal/new-client-secret.png)

9. 在“添加客户端密码”窗口中，输入描述，指定所需的客户端密码到期时间，然后单击“添加”。

10. 复制并保存“客户端密码”值。

    ![展示“证书和密码”窗格中的模糊处理的密码值的屏幕截图。](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >在你离开此窗口后，客户端密码值将会隐藏起来，你将无法再次查看或复制它。

### <a name="creating-an-azure-ad-app-using-powershell"></a>使用 PowerShell 创建 Azure AD 应用程序

此部分中包含使用 [PowerShell](/powershell/azure/create-azure-service-principal-azureps) 新建 Azure AD 应用程序的示例脚本。

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
[!INCLUDE[service create steps two, three and four](../../includes/service-principal-create-steps.md)]

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
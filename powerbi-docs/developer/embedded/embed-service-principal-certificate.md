---
title: 使用服务主体和证书将 Power BI 内容嵌入到 Power BI 嵌入式分析应用程序中，从而改进嵌入式 BI 见解
description: 了解如何使用 Azure Active Directory 应用程序服务主体和证书对 Power BI 嵌入式分析进行身份验证。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 11/23/2020
ms.openlocfilehash: 0e19f2c592f5a5249e80771edf4a16c02eb68708
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565112"
---
# <a name="embed-power-bi-content-with-service-principal-and-a-certificate"></a>使用服务主体和证书嵌入 Power BI 内容

凭借基于证书的身份验证，你可以通过 Azure Active Directory (Azure AD) 使用 Windows、Android 或 iOS 设备上或 [Azure 密钥保管库](/azure/key-vault/basic-concepts)中保存的客户端证书进行身份验证。

借助这种身份验证方法，可使用 CA 从一个中心位置管理证书，以便进行轮换或吊销。

要详细了解 Azure AD 中的证书，请参阅[客户端凭据流](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Client-credential-flows) GitHub 页面。

## <a name="method"></a>方法

1. [使用服务主体嵌入内容](embed-service-principal.md)。

2. [创建证书](embed-service-principal-certificate.md#step-2---create-a-certificate)。

3. [设置证书身份验证](embed-service-principal-certificate.md#step-3---set-up-certificate-authentication)。

4. [从 Azure Key Vault 获取证书](embed-service-principal-certificate.md#step-4---get-the-certificate-from-azure-key-vault)。

5. [使用服务主体和证书进行身份验证](embed-service-principal-certificate.md#step-5---authenticate-using-service-principal-and-a-certificate)。

## <a name="step-1---embed-your-content-with-service-principal"></a>第 1 步 - 使用服务主体嵌入内容

若要使用服务主体嵌入内容，请按照[使用服务主体和应用程序机密嵌入 Power BI 内容](embed-service-principal.md)中的说明进行操作。

>[!NOTE]
>如果你已有使用服务主体嵌入的内容，请跳过此步骤并前往[第 2 步](embed-service-principal-certificate.md#step-2---create-a-certificate)。

## <a name="step-2---create-a-certificate"></a>第 2 步 - 创建证书

可以从受信任的证书颁发机构获取证书，也可以自行生成证书。

本部分介绍如何使用 [Azure 密钥保管库](/azure/key-vault/create-certificate)创建证书，以及下载包含公钥的 .cer 文件。

1. 登录 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜索“密钥保管库”，然后单击“密钥保管库”链接 。

    ![展示 Azure 门户中密钥保管库链接的屏幕截图。](media/embed-service-principal-certificate/key-vault.png)

3. 单击要向其添加证书的密钥保管库。

    ![展示 Azure 门户中经过模糊处理的密钥保管库列表的屏幕截图。](media/embed-service-principal-certificate/select-key-vault.png)

4. 单击“**证书**”。

    ![展示标示了“证书”的“密钥保管库”页的屏幕截图。](media/embed-service-principal-certificate/certificates.png)

5. 单击“生成/导入”。

    ![展示标示了“生成/导入”的“证书”窗格的屏幕截图。](media/embed-service-principal-certificate/generate.png)

6. 按如下所示配置“创建证书”字段：

    * **证书创建方法** - 常规

    * **证书名称** - 输入证书名称

    * **证书颁发机构 (CA) 类型** - 自签名证书

    * **使用者** - [X.500](https://wikipedia.org/wiki/X.500) 可分辨名称

    * **DNS 名称** - 0 DNS 名称

    * **有效期（月）** - 输入证书的有效期

    * **内容类型** - PKCS #12

    * **生存期操作类型** - 在达到给定生存期百分比时自动续订

    * **生存期百分比** - 80

    * **高级策略配置** - 未配置

7. 单击“创建”。 新创建的证书默认处于禁用状态。 可能需要长达五分钟的时间才会启用。

8. 选择你创建的证书。

9. 单击“以 CER 格式下载”。 下载的文件包含公钥。

    ![展示“下载为 cer 格式”按钮的屏幕截图。](media/embed-service-principal-certificate/download-cer.png)

## <a name="step-3---set-up-certificate-authentication"></a>第 3 步 - 设置证书身份验证

1. 在 Azure AD 应用程序中，单击“证书和机密”选项卡。

     ![展示 Azure 门户中应用的“证书和密码”窗格的屏幕截图。](media/embed-service-principal/certificates-and-secrets.png)

2. 单击“上传证书”，上传你在本教程的[第 2 步](#step-2---create-a-certificate)中创建并下载的 .cer 文件。 .cer 文件包含公钥。

## <a name="step-4---get-the-certificate-from-azure-key-vault"></a>第 4 步 - 从 Azure 密钥保管库获取证书

使用托管服务标识 (MSI) 从 Azure 密钥保管库获取证书。 此过程涉及获取同时包含公钥和私钥的 .pfx 证书。

请参阅从 Azure 密钥保管库读取证书的代码示例。 如果要使用 Visual Studio，请参阅[将 Visual Studio 配置为使用 MSI](#configure-visual-studio-to-use-msi)。

```csharp
private X509Certificate2 ReadCertificateFromVault(string certName)
{
    var serviceTokenProvider = new AzureServiceTokenProvider();
    var keyVaultClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(serviceTokenProvider.KeyVaultTokenCallback));
    CertificateBundle certificate = null;
    SecretBundle secret = null;
    try
    {
        certificate = keyVaultClient.GetCertificateAsync($"https://{KeyVaultName}.vault.azure.net/", certName).Result;
        secret = keyVaultClient.GetSecretAsync(certificate.SecretIdentifier.Identifier).Result;
    }
    catch (Exception)
    {
        return null;
    }

    return new X509Certificate2(Convert.FromBase64String(secret.Value));
}
```

## <a name="step-5---authenticate-using-service-principal-and-a-certificate"></a>第 5 步 - 使用服务主体和证书进行身份验证

通过连接到 Azure 密钥保管库，你可以使用服务主体和 Azure 密钥保管库中存储的证书对应用进行身份验证。

要连接并从 Azure 密钥保管库读取证书，请参阅下面的代码。

>[!NOTE]
>如果你已有组织创建的证书，请将 .pfx 文件上传到 Azure 密钥保管库。

```csharp
// Preparing needed variables
var Scope = "https://analysis.windows.net/powerbi/api/.default"
var ApplicationId = "{YourApplicationId}"
var tenantSpecificURL = "https://login.microsoftonline.com/{YourTenantId}/"
X509Certificate2 certificate = ReadCertificateFromVault(CertificateName);

// Authenticating with a SP and a certificate
public async Task<AuthenticationResult> DoAuthentication(){
    IConfidentialClientApplication clientApp = null;
    clientApp = ConfidentialClientApplicationBuilder.Create(ApplicationId)
                                                    .WithCertificate(certificate)
                                                    .WithAuthority(tenantSpecificURL)
                                                    .Build();
    try
    {
        authenticationResult = await clientApp.AcquireTokenForClient(Scope).ExecuteAsync();
    }
    catch (MsalException)
    {
        throw;
    }
    return authenticationResult
}
```

## <a name="configure-visual-studio-to-use-msi"></a>将 Visual Studio 配置为使用 MSI

创建嵌入式解决方案时，将 Visual Studio 配置为使用托管服务标识 (MSI) 可能会很有用。 [MSI](/azure/active-directory/managed-identities-azure-resources/overview) 是用于管理 Azure AD 标识的一项功能。 配置后，它将允许 Visual Studio 针对你的 Azure 密钥保管库进行身份验证。

1. 在 Visual Studio 中打开项目。

2. 单击“工具” > “选项” 。

     ![展示 Visual Studio 中“工具”选项中的“选项”按钮的屏幕截图。](media/embed-service-principal-certificate/visual-studio-options.png)

3. 搜索“帐户选择”并单击“帐户选择” 。

    ![展示 Visual Studio 中“选项”窗口中的“帐户选择”选项的屏幕截图。](media/embed-service-principal-certificate/account-selection.png)

4. 添加有权访问你 Azure 密钥保管库的帐户。

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[注册应用](register-app.md)

> [!div class="nextstepaction"]
>[适用于客户的 Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Azure Active Directory 中的应用程序和服务主体对象](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[配合使用本地数据网关与服务主体的行级别安全性](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)
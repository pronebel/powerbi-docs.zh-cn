---
title: 以编程方式为 Power BI 配置凭据
description: 如何在实现 Power BI 自动化时以编程方式配置凭据
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 02/23/2020
ms.openlocfilehash: 1c8741736f0639cba7f8df3f9891a6fe20397d8e
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079499"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>以编程方式为 Power BI 配置凭据

按照以下步骤以编程方式为 Power BI 配置凭据。

## <a name="update-credentials-flow-for-data-sources"></a>更新数据源的凭据流

1. 调用 [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) 发现数据集的数据源。 在每个数据源的响应正文中，有类型、连接详细信息、网关和数据源 ID。

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. 根据凭据类型相对应的[更新数据源示例](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)生成凭据字符串。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. 调用 [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) 检索网关公钥。

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. 加密凭据。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    使用第 2 步中的网关公钥来加密凭据字符串。 不同的网关版本可能具有不同的公钥大小。 请参阅以下使用 SDK 代码的示例（可以从 [PowerBI-CSharp GitHub 存储库](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions)获取）：
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. 使用加密凭据生成凭据详细信息。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    将 AssymetricKeyEncriptor 类与第 3 步  中检索到的公钥结合使用。

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. 调用 [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) 设置凭据。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>为数据网关配置新的数据源

1. 在计算机上安装[本地数据网关](https://powerbi.microsoft.com/gateway/)。

2. 调用 [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) 检索网关 ID 和公钥。

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. 使用第 2 步  中检索到的网关公钥，按照[更新数据源的凭据流](#update-credentials-flow-for-data-sources)中所述的方法操作，生成凭据详细信息。

4. 生成请求正文。

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. 调用 [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) API。

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>凭据类型

如果使用 [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/) 在“企业本地网关”下调用 [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) 或 [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)，则需要使用网关的公钥加密凭据值  。

>[!NOTE]
>.NET SDK v3 还可以运行下面列出的 .NET SDK v2 示例。

### <a name="windows-and-basic-credentials"></a>Windows 和基本凭据

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>密钥凭据

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2 凭据**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**匿名凭据**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>故障排除

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>调用 Get Datasources 时未找到任何网关和数据源 ID

此问题意味着数据集未绑定到网关。 在新建数据集时，对于每个云连接，不含凭据的数据源在用户的云网关上自动创建。 此网关用于存储云连接的凭据。

创建数据集后，会在数据集与合适的网关之间创建自动绑定，网关包含适用于所有连接的匹配数据源。 如果没有此类网关或多个合适的网关，自动绑定将失败。

如果使用的是本地数据集，请创建缺少的本地数据源，并按照[绑定到网关](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway)中的说明操作，手动将数据集绑定到网关。

若要发现可以绑定到的网关，请按照[发现网关](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways)中的说明操作。
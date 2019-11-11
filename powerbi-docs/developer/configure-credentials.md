---
title: 以编程方式为 Power BI 配置凭据
description: 如何以编程方式为 Power BI 配置凭据以实现自动化
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: 52daf96a4ff6ca7eac4d996f5891740538c88e74
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875862"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>以编程方式为 Power BI 配置凭据

按照以下步骤以编程方式为 Power BI 配置凭据。

## <a name="configure-a-credential-flow-for-data-sources"></a>为数据源配置凭据流

1. 调用 [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) 发现数据集的数据源。 每个数据源的响应正文中都具有类型、连接详细信息、网关和数据源 ID。

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. 根据凭据类型相对应的[更新数据源示例](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)生成凭据字符串。

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. 生成凭据详细信息。

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. 调用 [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) 设置凭据，在步骤 1 中使用网关和数据源 ID，在步骤 4 中使用凭据详细信息。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>过期的本地数据源凭据流

1. [请执行上个方案中的步骤 1 和 2](#configure-a-credential-flow-for-data-sources)。

2. 调用 [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) 检索网关公钥。

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. 通过采用 RSA 加密算法的网关公钥加密凭据字符串。

    使用以下帮助程序类进行加密：

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

4. 使用加密凭据生成凭据详细信息。

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. 调用 [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) 设置凭据。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>为数据网关配置新的数据源

1. 在计算机上安装[本地数据网关](https://powerbi.microsoft.com/gateway/)。

2. 调用 [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) 检索网关 ID 和公钥。

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. 与上个方案类似，使用[过期的本地数据源凭据流](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway)步骤中检索的网关公钥生成凭据详细信息。

4. 生成请求正文

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

## <a name="troubleshooting"></a>故障排除

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>调用 Get Datasources 时未找到任何网关和数据源 ID

此问题意味着数据集未绑定到网关。 在创建新的数据集时，在用户的云网关上将自动为每个云连接创建不含凭据的数据源。 此网关用于存储云连接的凭据。

创建数据集后，数据集会自动绑定到合适的网关，该网关包含适用于所有连接的匹配数据源。 如果没有此类网关或多个合适的网关，自动绑定将失败。

创建缺失的本地数据源（如果有），并使用 [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) 手动将数据集绑定到网关。

要发现可以被绑定的网关，请使用 [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways)。

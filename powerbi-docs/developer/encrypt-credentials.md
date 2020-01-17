---
title: 加密凭据
description: 演练 - 加密本地网关数据源的凭据
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836607"
---
# <a name="encrypt-credentials"></a>加密凭据

如果使用 [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/) 在“企业本地网关”下调用 [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) 或 [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)，则需要使用网关的公钥加密凭据值  。

请参阅下面的代码示例，了解如何在 .NET 中加密凭据。

为下面的 EncodeCredentials 方法提供的凭据应该采用以下格式之一，具体取决于凭据类型：

**Basic/Windows 凭据**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**密钥凭据**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**OAuth2 凭据**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**匿名凭据**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**加密凭据**

使用网关的公钥加密凭据值。 不同的网关版本可能具有不同的公钥大小。

请参阅 SDK 代码中的示例，该示例位于 PowerBI-CSharp GitHub 存储库 [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2)。

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)
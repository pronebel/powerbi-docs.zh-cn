---
title: Power BI 报表服务器中的 Always Encrypted
description: 本文阐述了使用数据源类型 Microsoft SQL Server 和 Microsoft Azure SQL 数据库时 Power BI 报表服务器中的 Always Encrypted 支持。
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "76710197"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Power BI 报表服务器中的 Always Encrypted

本文阐述了使用数据源类型 Microsoft SQL Server 和 Microsoft Azure SQL 数据库时 Power BI 报表服务器中的 Always Encrypted 支持。 有关 SQL Server 中的 Always Encrypted 功能的详细信息，请参阅 [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) 文章。

## <a name="always-encrypted-user-isolation"></a>Always Encrypted 用户隔离

目前，如果用户可以访问报表，Power BI 报表服务器不会限制对报表中 Always Encrypted 列的访问。  因此，如果已通过列主密钥向服务器授予了对列加密密钥的访问权限，则用户可以访问他们可访问的报表的所有列。

## <a name="always-encrypted-column-usage"></a>Always Encrypted 列用法

### <a name="key-storage-strategies"></a>密钥存储策略

|存储  |受支持  |
|---------|---------|
|Windows 证书存储 | 是 |
|Azure Key Vault | 否 |
| 下一代加密技术 (CNG) | 否 |

### <a name="certificate-storage-and-access"></a>证书存储和访问

需要访问证书的帐户为服务帐户。 证书应存储在本地计算机证书存储中。 有关详细信息，请参阅：

- [配置报表服务器服务帐户](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- SQL Server 文章“为 Always Encrypted 创建并存储列主密钥”中的[向应用程序和用户提供证书](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users)部分。

### <a name="column-encryption-strategy"></a>列加密策略

在 Power BI 报表服务器中，列加密策略可以是确定的策略，也可以是随机策略   。 下表阐述了不同之处，具体取决于它所使用的策略。

|用途  |具有确定性  |具有随机性  |
|---------|---------|---------|
|可以在查询结果中按原样读取，如 SELECT 语句。 | 是  | 是  |
|可以用作查询中的分组依据实体。 | 是 | 否 |
|还可用作聚合字段（COUNT 和 DISTINCT 除外）。 | 否，COUNT 和 DISTINCT 除外 | 否 |
|可用作报表参数 | 是 | 否 |

详细了解[确定性与随机性加密](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption)。

### <a name="parameter-usage"></a>参数用法

参数用法仅适用于确定性加密。

**单值参数**。  可以对 Always Encrypted 列使用单值参数。

**多值参数**。 不能对 Always Encrypted 列使用具有多个值的多值参数。

**级联参数**。 如果以下全部都为 true，则可以将级联参数用于 Always Encrypted  ：

- 所有 Always Encrypted 列都必须是具有确定性策略的 Always Encrypted。
- 对 Always Encrypted 列使用的所有参数都是单值参数。
- 所有 SQL 比较均使用等号 (=) 运算符。

## <a name="datatype-support"></a>数据类型支持

| SQL 数据类型 | 支持读取字段 | 支持用作分组依据元素 | 支持的聚合（COUNT、DISTINCT、MAX、MIN、SUM 等） | 支持使用参数通过等式进行筛选 | 备注 |
| --- | --- | --- | --- | --- | --- |
| int | 是 | 是 | COUNT、DISTINCT | 是，作为整数 |   |
| FLOAT | 是 | 是 | COUNT、DISTINCT | 是，作为浮点数 |   |
| nvarchar | 是 | 是 | COUNT、DISTINCT | 是，作为文本 | 确定性加密必须使用具有字符列的 binary2 排序顺序的列排序规则。 有关详细信息，请参阅 SQL Server [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) 一文。  |
| varchar | 是 | 是 | COUNT、DISTINCT | 否 |   |
| Decimal | 是 | 是 | COUNT、DISTINCT | 否 |   |
| numeric | 是 | 是 | COUNT、DISTINCT | 否 |   |
| datetime | 是 | 是 | COUNT、DISTINCT | 否 |   |
| datetime2 | 是 | 是 | COUNT、DISTINCT | 是，作为日期/时间 | 如果列没有毫秒精度（即，没有 datetime2(0)），则支持 |

## <a name="aggregation-alternatives"></a>聚合替代项

目前，唯一支持使用确定性 Always Encrypted 列的聚合是那些直接使用等号 (=) 运算符的聚合。 此 SQL Server 限制是由于 Always Encrypted 列的性质所致。 用户必须在报表中而不是在数据库中聚合。

## <a name="always-encrypted-in-connection-strings"></a>连接字符串中的 Always Encrypted

需要在 SQL Server 数据源的连接字符串中启用 Always Encrypted。 详细了解[在应用程序查询中启用 Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries)。

## <a name="next-steps"></a>后续步骤

SQL Server 和 Azure SQL数据库中的 [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


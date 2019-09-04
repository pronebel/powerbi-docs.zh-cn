---
title: Power BI 中 DirectQuery 支持的数据源
description: 获取数据源可以使用 DirectQuery 的列表。
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 5455a5f3b4bda6cf6d63825222822c4acfa5f03a
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2019
ms.locfileid: "70159948"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Power BI 中 DirectQuery 支持的数据源

Power BI Desktop  和 Power BI 服务  有多个可以连接并访问数据的数据源。 本文介绍了支持称为 DirectQuery  的连接方法的 Power BI 数据源。 有关 DirectQuery 的详细信息，请参阅 [Power BI 中的 DirectQuery](desktop-directquery-about.md)  。

在 Power BI 中，以下数据源支持 DirectQuery：

* Amazon Redshift
* AtScale（Beta 版本）
* Azure 数据资源管理器
* Azure HDInsight Spark
* [Azure SQL 数据库](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL 数据仓库](service-azure-sql-data-warehouse-with-direct-connect.md)
* Google BigQuery
* HDInsight 交互式查询
* IBM DB2 数据库
* IBM Netezza
* Impala（版本 2.x）
* MarkLogic
* Oracle 数据库（版本 12 及更高版本)
* Oracle Essbase
* SAP Business Warehouse 应用程序服务器
* SAP Business Warehouse 消息服务器
* SAP HANA
* Snowflake
* Spark（版本 0.9 及更高版本）
* SQL Server
* Teradata 数据库
* Vertica

名称后带有 (Beta) 或（预览）的数据源会发生更改，不支持在生产环境中使用   。 在将报表发布到 **Power BI 服务**后，这些数据源可能还不受支持，这意味着打开已发布的报表或浏览数据集会导致错误。

(Beta)  与（预览）  数据源之间的唯一区别是（预览）  数据源必须先要作为预览功能启用，然后才可供使用。 要启用（预览）数据连接器，请在 Power BI Desktop 中转到“文件”>“选项和设置”>“选项”，然后选择“预览功能”     。

> [!NOTE]
> 对 SQL Server 进行 DirectQuery 查询，需要使用当前 Windows 身份验证凭据或数据库凭据进行身份验证，以建立访问。 不支持使用其他凭据。
>

## <a name="on-premises-gateway-requirements"></a>本地网关要求
下表指定在将报表发布到 Power BI 服务  后本地数据网关  是否需要连接到指定的数据源。

| 源 | 需要网关？ |
| --- | --- |
| Amazon Redshift |否 |
| Azure HDInsight Spark (Beta) |否 |
| Azure SQL 数据库 |否 |
| Azure SQL 数据仓库 |否 |
| Google BigQuery |否 |
| IBM Netezza |是 |
| Impala（版本 2.x） |是 |
| Oracle 数据库 |是 |
| SAP Business Warehouse 应用程序服务器 |是 |
| SAP Business Warehouse 消息服务器 |在 Power BI 服务  中尚不受支持 |
| SAP HANA |是 |
| Snowflake |是 |
| Spark (Beta)，版本 0.9 及更高版本 |是 |
| SQL Server |是 |
| Teradata 数据库 |是 |

## <a name="single-sign-on-sso-for-directquery-sources"></a>DirectQuery 源的单一登录 (SSO)

启用“SSO”选项后，如果用户访问基于数据源生成的报表，则 Power BI 会在查询中将这些用户的已经过身份验证的 Azure AD 凭据发送到基础数据源。 这样，Power BI 便可以遵守在数据源级别配置的安全设置。

SSO 选项针对使用此数据源的所有数据集生效。 它不影响用于导入方案的身份验证方法。 以下数据源支持通过 DirectQuery 进行连接的 SSO：

- Azure SQL 数据库
- Azure SQL 数据仓库
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> 不支持 Azure 多重身份验证 (MFA)。 想要在 DirectQuery 中使用 SSO 的用户必须免除 MFA。

## <a name="next-steps"></a>后续步骤
有关 DirectQuery 的详细信息，请查看以下资源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [本地数据网关](service-gateway-onprem.md)


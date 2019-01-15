---
title: Power BI 报表服务器中 Power BI 报表数据源
description: Power BI 报表可以连接到多个数据源。 根据数据使用方式，可以提供不同的数据源。
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maghan
ms.openlocfilehash: de16c10a03654802e4c65bfa92e60259e2f9510d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54291736"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI 报表服务器中 Power BI 报表数据源
Power BI 报表可以连接到多个数据源。 根据数据使用方式，可以提供不同的数据源。 可以导入数据，或者可以直接使用 DirectQuery 或与 SQL Server Analysis Services 的实时连接查询数据。

这些数据源特定于 Power BI 报表服务器中使用的 Power BI 报表。 有关分页报表 (.rdl) 支持的数据源的信息，请参阅 [Reporting Services 支持的数据源](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs)。

> [!IMPORTANT]
> Power BI Desktop 报表中的所有数据源必须支持配置计划刷新。
>  

## <a name="list-of-supported-data-sources"></a>受支持数据源的列表

即使不在受支持列表中的其他数据源也可能有效。

| **数据源** | **缓存的数据** | **计划的刷新** | **实时/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server 数据库 |是 |是 |是 |
| SQL Server Analysis Services |是 |是 |是 |
| Azure SQL 数据库 |是 |是 |是 |
| Azure SQL 数据仓库 |是 |是 |是 |
| Excel |是 |是 |否 |
| Access 数据库 |是 |是 |否 |
| Active Directory |是 |是 |否 |
| Amazon Redshift |是 |否 |否 |
| Azure Blob 存储 |是 |是 |否 |
| Azure Data Lake Store |是 |否 |否 |
| Azure HDInsight (HDFS) |是 |否 |否 |
| Azure HDInsight (Spark) |是 |是 |否 |
| Azure 表存储 |是 |是 |否 |
| Dynamics 365 (联机) |是 |否 |否 |
| Facebook |是 |否 |否 |
| 文件夹 |是 |是 |否 |
| Google Analytics |是 |否 |否 |
| Hadoop 文件 (HDFS) |是 |否 |否 |
| IBM DB2 数据库 |是 |是 |否 |
| Impala |是 |否 |否 |
| JSON |是 |是 |否 |
| Microsoft Exchange |是 |否 |否 |
| Microsoft Exchange Online |是 |否 |否 |
| MySQL 数据库 |是 |是 |否 |
| OData 源 |是 |是 |否 |
| ODBC |是 |是 |否 |
| OLE DB |是 |是 |否 |
| Oracle 数据库 |是 |是 |是 |
| PostgreSQL 数据库 |是 |是 |否 |
| Power BI 服务 |否 |否 |否 |
| R 脚本 |是 |否 |否 |
| Salesforce 对象 |是 |否 |否 |
| Salesforce 报表 |是 |否 |否 |
| SAP Business Warehouse 服务器 |是 |是 |是 |
| SAP HANA 数据库 |是 |是 |是 |
| SharePoint 文件夹（本地） |是 |是 |否 |
| SharePoint 列表(本地) |是 |是 |否 |
| SharePoint Online 列表 |是 |否 |否 |
| Snowflake |是 |否 |否 |
| Sybase 数据库 |是 |是 |否 |
| Teradata 数据库 |是 |是 |是 |
| 文本/CSV |是 |是 |否 |
| Web |是 |是 |否 |
| XML |是 |是 |否 |
| appFigures (Beta) |是 |否 |否 |
| Azure Analysis Services 数据库 |是 |否 |是 |
| Azure Cosmos DB (Beta) |是 |否 |否 |
| Azure HDInsight Spark (Beta) |是 |否 |否 |
| Common Data Service (Beta) |是 |否 |否 |
| comScore Digital Analytix (Beta) |是 |否 |否 |
| Dynamics 365 for Customer Insights (Beta) |是 |否 |否 |
| Dynamics 365 for Financials (Beta) |是 |否 |否 |
| GitHub (Beta) |是 |否 |否 |
| Google BigQuery (Beta) |是 |否 |否 |
| IBM Informix 数据库 (Beta) |是 |否 |否 |
| IBM Netezza (Beta) |是 |否 |否 |
| Kusto (Beta) |是 |否 |否 |
| MailChimp (Beta) |是 |否 |否 |
| Microsoft Azure 使用见解 (Beta) |是 |否 |否 |
| Mixpanel (Beta) |是 |否 |否 |
| Planview Enterprise (Beta) |是 |否 |否 |
| Projectplace (Beta) |是 |否 |否 |
| QuickBooks Online (Beta) |是 |否 |否 |
| Smartsheet |是 |否 |否 |
| Spark (Beta 版本) |是 |否 |否 |
| SparkPost (Beta) |是 |否 |否 |
| SQL Sentry (Beta) |是 |否 |否 |
| Stripe (Beta) |是 |否 |否 |
| SweetIQ (Beta) |是 |否 |否 |
| Troux (Beta) |是 |否 |否 |
| Twilio (Beta) |是 |否 |否 |
| tyGraph (Beta) |是 |否 |否 |
| Vertica (Beta 版本) |是 |否 |否 |
| Visual Studio Team Services (Beta) |是 |否 |否 |
| Webtrends (Beta) |是 |否 |否 |
| Zendesk (Beta) |是 |否 |否 |

> [!IMPORTANT]
> 在数据源配置的行级别安全性应适用于某些 DirectQuery（SQL Server、Azure SQL 数据库、Oracle 和 Teradata），以及假设在你的环境中正确配置了 Kerberos 的实时连接。
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>用于模型刷新的受支持的身份验证方法列表

Power BI 报表服务器不支持将基于 OAuth 的身份验证用于模型刷新。 Excel 或 Access 数据库等某些数据源使用单独的步骤（如“文件”或 Web）连接到数据。

| **数据源** | **匿名身份验证** | **密钥身份验证** | **用户名和密码** | **Windows 身份验证** |
| --- | --- | --- | --- | --- |
| SQL Server 数据库 |否 |否 |是 |是 |
| SQL Server Analysis Services |否 |否 |是 |是 |
| Web |是 |否 |是 |是 |
| Azure SQL 数据库 |否 |否 |是 |否 |
| Azure SQL 数据仓库 |否 |否 |是 |否 |
| Active Directory |否 |否 |是 |是 |
| Amazon Redshift |否 |否 |否 |否 |
| Azure Blob 存储 |是 |是 |否 |否 |
| Azure Data Lake Store |否 |否 |否 |否 |
| Azure HDInsight (HDFS) |否 |否 |否 |否 |
| Azure HDInsight (Spark) |是 |是 |否 |否 |
| Azure 表存储 |否 |是 |否 |否 |
| Dynamics 365 (联机) |否 |否 |否 |否 |
| Facebook |否 |否 |否 |否 |
| 文件夹 |否 |否 |否 |是 |
| Google Analytics |否 |否 |否 |否 |
| Hadoop 文件 (HDFS) |否 |否 |否 |否 |
| IBM DB2 数据库 |否 |否 |是 |是 |
| Impala |否 |否 |否 |否 |
| Microsoft Exchange |否 |否 |否 |否 |
| Microsoft Exchange Online |否 |否 |否 |否 |
| MySQL 数据库 |否 |否 |是 |是 |
| OData 源 |是 |是 |是 |是 |
| ODBC |是 |否 |是 |是 |
| OLE DB |是 |否 |是 |是 |
| Oracle 数据库 |否 |否 |是 |是 |
| PostgreSQL 数据库 |否 |否 |是 |否 |
| Power BI 服务 |否 |否 |否 |否 |
| R 脚本 |否 |否 |否 |否 |
| Salesforce 对象 |否 |否 |否 |否 |
| Salesforce 报表 |否 |否 |否 |否 |
| SAP Business Warehouse 服务器 |否 |否 |是 |否 |
| SAP HANA 数据库 |否 |否 |是 |是 |
| SharePoint 文件夹（本地） |是 |否 |否 |是 |
| SharePoint 列表(本地) |是 |否 |否 |是 |
| SharePoint Online 列表 |否 |否 |否 |否 |
| Snowflake |否 |否 |否 |否 |
| Sybase 数据库 |否 |否 |是 |是 |
| Teradata 数据库 |否 |否 |是 |是 |
| appFigures (Beta) |否 |否 |否 |否 |
| Azure Analysis Services 数据库 (Beta) |否 |否 |否 |否 |
| Azure Cosmos DB (Beta) |否 |否 |否 |否 |
| Azure HDInsight Spark (Beta) |否 |否 |否 |否 |
| Common Data Service (Beta) |否 |否 |否 |否 |
| comScore Digital Analytix (Beta) |否 |否 |否 |否 |
| Dynamics 365 for Customer Insights (Beta) |否 |否 |否 |否 |
| Dynamics 365 for Financials (Beta) |否 |否 |否 |否 |
| GitHub (Beta) |否 |否 |否 |否 |
| Google BigQuery (Beta) |否 |否 |否 |否 |
| IBM Informix 数据库 (Beta) |否 |否 |否 |否 |
| IBM Netezza (Beta) |否 |否 |否 |否 |
| Kusto (Beta) |否 |否 |否 |否 |
| MailChimp (Beta) |否 |否 |否 |否 |
| Microsoft Azure 使用见解 (Beta) |否 |否 |否 |否 |
| Mixpanel (Beta) |否 |否 |否 |否 |
| Planview Enterprise (Beta) |否 |否 |否 |否 |
| Projectplace (Beta) |否 |否 |否 |否 |
| QuickBooks Online (Beta) |否 |否 |否 |否 |
| Smartsheet |否 |否 |否 |否 |
| Spark (Beta 版本) |否 |否 |否 |否 |
| SparkPost (Beta) |否 |否 |否 |否 |
| SQL Sentry (Beta) |否 |否 |否 |否 |
| Stripe (Beta) |否 |否 |否 |否 |
| SweetIQ (Beta) |否 |否 |否 |否 |
| Troux (Beta) |否 |否 |否 |否 |
| Twilio (Beta) |否 |否 |否 |否 |
| tyGraph (Beta) |否 |否 |否 |否 |
| Vertica (Beta 版本) |否 |否 |否 |否 |
| Visual Studio Team Services (Beta) |否 |否 |否 |否 |
| Webtrends (Beta) |否 |否 |否 |否 |
| Zendesk (Beta) |否 |否 |否 |否 |

## <a name="list-of-supported-authentication-methods-for-directquery"></a>用于 DirectQuery 的受支持的身份验证方法列表

Power BI 报表服务器不支持将基于 OAuth 的身份验证用于 DirectQuery。

| **数据源** | **匿名身份验证** | **密钥身份验证** | **用户名和密码** | **Windows 身份验证** | **集成 Windows 身份验证** |
| --- | --- | --- | --- | --- | --- |
| SQL Server 数据库 |否 |否 |是 |是 |是 |
| SQL Server Analysis Services |否 |否 |是 |是 |是 |
| Azure SQL 数据库 |否 |否 |是 |否 |否 |
| Azure SQL 数据仓库 |否 |否 |是 |否 |否 |
| Oracle 数据库 |否 |否 |是 |是 |是 |
| SAP Business Warehouse 服务器 |否 |否 |是 |否 |是 |
| SAP HANA 数据库 |否 |否 |是 |是 |否 |
| Teradata 数据库 |否 |否 |是 |是 |是 |


## <a name="next-steps"></a>后续步骤
现在你已连接到数据源，接下来使用该数据源中的数据[创建 Power BI 报表](quickstart-create-powerbi-report.md)。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


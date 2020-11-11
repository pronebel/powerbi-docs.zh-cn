---
title: Power BI 数据源
description: 本文列出了 Power BI 支持的数据源，其中包括有关 DirectQuery 和本地数据网关的信息。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/07/2020
ms.author: davidi
ms.openlocfilehash: 3cce51ad577c700a0f9595a2b92694e5e1b61cc5
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397383"
---
# <a name="power-bi-data-sources"></a>Power BI 数据源

下表展示了 Power BI 支持的数据集的数据源，其中包括有关 DirectQuery 和本地数据网关的信息。 有关数据流的信息，请参阅[连接到 Power BI 数据流的数据源](../transform-model/dataflows/dataflows-configure-consume.md)。

| 数据源 | 从桌面连接 | 从服务连接并刷新 | DirectQuery/实时连接 | 网关（支持） | 网关（必需） | Power BI 数据流 |
|---|---|---|---|---|---|---|---|
| Access 数据库 | 是 | 是 | 否 | 是 <sup>1</sup> | 是 | 是 |
| ActiveDirectory | 是 | 是 | 否 | 是 | 是 | 是 |
| Adobe Analytics | 是 | 是 | 否 | 否 | 否 | 否 |
| Amazon Redshift | 是 | 是 | 是 | 是 | 否 | 是 |
| appFigures | 是 | 是 | 否 | 否 | 否 | 否 |
| AtScale 多维数据集 | 是 | 是 | 是 | 是 | 否 | 否 |
| Azure Analysis Services | 是 | 是 | 是 | 否 | 否 | 否 |
| Azure Blob 存储 | 是 | 是 | 否 | 是 | 否 | 是 |
| Azure Cosmos DB | 是 | 是 | 否 | 否 | 否 | 否 |
| Azure 成本管理 | 是 | 是 | 否 | 否 | 否 | 否 |
| Azure 数据资源管理器 (kusto) | 是 | 是 | 是 | 是 | 否 | 是 |
| Azure Data Lake Storage Gen1 | 是 | 是 | 否 | 否 | 否 | 否 |
| Azure Data Lake Storage Gen2 | 是 | 是 | 否 | 是 | 否 | 是 |
| Azure DevOps | 是 | 是 | 否 | 否 | 否 | 否 |
| Azure DevOps Server | 是 | 是 | 否 | 是 | 是 | 否 |
| Azure HDInsight (HDFS) | 是 | 是 | 否 | 否 | 否 | 否 |
| Azure HDInsight Spark | 是 | 是 | 是 | 否 | 否 | 是 |
| Azure SQL 数据库 | 是 | 是 | 是 | 是 | 否 | 是 |
| Azure SQL 数据仓库 | 是 | 是 | 是 | 是 | 否 | 是 |
| Azure 表存储 | 是 | 是 | 否 | 是 | 否 | 是 |
| BI 连接器 | 是 | 是 | 是 | 是 | 是 | 否 |
| BI360 - Budgeting & Financial Reporting | 是 | 是 | 否 | 否 | 否 | 否 |
| Common Data Service | 是 | 是 | 否 | 否 | 否 | 是 |
| Data.World - Get Dataset | 是 | 是 | 否 | 否 | 否 | 否 |
| Denodo | 是 | 是 | 是 | 是 | 是 | 否 |
| Dremio | 是 | 是 | 是 | 是 | 是 | 否 |
| Dynamics 365 (联机) | 是 | 是 | 否 | 否 | 否 | 否 |
| Dynamics 365 Business Central | 是 | 是 | 否 | 否 | 否 | 否 |
| Dynamics 365 Business Central (本地) | 是 | 是 | 否 | 否 | 否 | 否 |
| Dynamics 365 Customer Insights | 是 | 是 | 否 | 否 | 否 | 否 |
| Dynamics NAV | 是 | 是 | 否 | 否 | 否 | 否 |
| Emigo Data Source | 是 | 是 | 否 | 否 | 否 | 否 |
| Entersoft Business Suite | 是 | 是 | 否 | 否 | 否 | 否 |
| Essbase | 是 | 是 | 是 | 是 | 是 | 否 |
| Exasol | 是 | 是 | 是 | 是 | 是 | 否 |
| Excel | 是 <sup>3</sup> | 是 <sup>3</sup> | 否 | 是 <sup>3</sup> | 否 <sup>4</sup> | 是 |
| Facebook | 是 | 是 | 否 | 否 | 否 | 否 |
| 文件 | 是 | 是 | 否 | 是 | 是 | 是 |
| Folder | 是 | 是 | 否 | 是 | 是 | 是 |
| GitHub | 是 | 是 | 否 | 否 | 否 | 否 |
| Google Analytics | 是 | 是 | 否 | 否 | 否 | 否 |
| Google BigQuery | 是 | 是 | 是 | 否 | 否 | 是 |
| Hadoop 文件 (HDFS) | 是 | 否 | 否 | 否 | 否 | 否 |
| Hive LLAP | 是 | 是 | 是 | 是 | 否 | 否 |
| HDInsight 交互式查询 | 是 | 是 | 是 | 否 | 否 | 否 |
| IBM DB2 | 是 | 是 | 是 | 是 | 否 | 是 |
| IBM Informix 数据库 | 是 | 是 | 否 | 是 | 否 | 否 |
| IBM Netezza | 是 | 是 | 是 | 是 | 是 | 否 |
| Impala | 是 | 是 | 是 | 是 | 是 | 是 |
| Indexima | 是 | 是 | 是 | 是 | 是 | 否 |
| Industrial App Store | 是 | 是 | 否 | 否 | 否 | 否 |
| Information Grid | 是 | 是 | 否 | 否 | 否 | 否 |
| Intersystems IRIS | 是 | 是 | 是 | 是 | 是 | 否 |
| Intune Data Warehouse | 是 | 是 | 否 | 否 | 否 | 否 |
| Jethro ODBC | 是 | 是 | 是 | 是 | 是 | 否 |
| JSON | 是 | 是 | 否 | 是** | 否 <sup>4</sup> | 是 |
| Kyligence Enterprise | 是 | 是 | 是 | 是 | 是 | 否 |
| MailChimp | 是 | 是 | 否 | 否 | 否 | 否 |
| Marketo | 是 | 是 | 否 | 否 | 否 | 否 |
| MarkLogic ODBC | 是 | 是 | 是 | 是 | 是 | 否 |
| Microsoft Azure 使用见解 | 是 | 是 | 否 | 否 | 否 | 否 |
| Microsoft Exchange | 是 | 是 | 否 | 是 | 否 | 否 |
| Microsoft Exchange Online | 是 | 是 | 否 | 否 | 否 | 是 |
| Microsoft Graph Security | 是 | 是 | 否 | 是 | 否 | 否 |
| Mixpanel | 是 | 是 | 否 | 否 | 否 | 否 |
| MySQL | 是 | 是 | 否 | 是 | 是 | 是 |
| OData | 是 | 是 <sup>7</sup> | 否 | 是 | 否 | 是 |
| ODBC | 是 | 是 | 否 | 是 | 是 | 是 |
| OleDb | 是 | 是 | 否 | 是 | 是 | 否 |
| Oracle | 是 | 是 | 是 | 是 | 是 | 是 |
| Paxata <sup>8</sup> | 是 | 是 | 否 | 是 | 否 | 否 |
| PDF | 是 | 是 | 否 | 是 | 否 <sup>4</sup> | 是 |
| Planview Enterprise One - CTM | 是 | 是 | 否 | 否 | 否 | 否 |
| Planview Enterprise One - PRM | 是 | 是 | 否 | 否 | 否 | 否 |
| Planview Projectplace | 是 | 是 | 否 | 否 | 否 | 否 |
| PostgreSQL | 是 | 是 | 是 | 是 | 否 | 是 |
| Power BI 数据流 | 是 | 是 | 否 | 否 | 否 | 是 |
| Power BI 数据集 | 是 | 是 | 是 | 否 | 否 | 否 |
| Power platform 数据流 | 是 | 是 | 否 | 否 | 否 | 是 |
| Python 脚本 | 是 | 是 <sup>5</sup> | 否 | 是 <sup>5</sup> | 是 | 否 |
| QubolePresto | 是 | 是 | 是 | 是 | 是 | 否 |
| Quick Base | 是 | 是 | 否 | 是 | 是 | 否 |
| QuickBooks Online | 是 | 是 | 否 | 否 | 否 | 否 |
| R 脚本 | 是 | 是 <sup>5</sup> | 否 | 是 <sup>5</sup> | 否 | 否 |
| Roamler | 是 | 是 | 否 | 是 | 否 | 否 |
| Salesforce 对象 | 是 | 是 | 否 | 否 | 否 | 是 |
| Salesforce 报表 | 是 | 是 | 否 | 否 | 否 | 是 |
| SAP Business Warehouse 消息服务器 | 是 | 是 | 是 | 是 | 是 | 是 |
| SAP Business Warehouse 服务器 | 是 | 是 | 是 | 是 | 是 | 是 |
| SAP HANA | 是 | 是 | 是 | 是 | 是 | 是 |
| SharePoint 文件夹 | 是 | 是 | 否 | 是 | 否 <sup>4</sup> | 是 |
| SharePoint 列表 | 是 | 是 | 否 | 是 | 否 <sup>4</sup> | 是 |
| SharePoint Online 列表 | 是 | 是 | 否 | 是 | 否 | 是 |
| Smartsheet | 是 | 是 | 否 | 否 | 否 | 是 |
| Snowflake | 是 | 是 | 是 | 是 | 否 | 是 |
| Spark | 是 | 是 | 是 | 是 | 否 | 是 |
| SparkPost | 是 | 是 | 否 | 否 | 否 | 否 |
| SQL Server | 是 | 是 | 是 | 是 | 是 | 是 |
| SQL Server Analysis Services | 是 | 是 | 是 | 是 | 是 | 否 |
| Stripe | 是 | 是 | 否 | 否 | 否 | 否 |
| SurveyMonkey | 是 | 是 | 否 | 是 | 否 | 否 |
| SweetIQ | 是 | 是 | 否 | 否 | 否 | 否 |
| Sybase | 是 | 是 | 否 | 是 | 是 | 是 |
| TeamDesk | 是 | 是 | 否 | 是 | 否 | 否 |
| Tenforce | 是 | 是 | 否 | 否 | 否 | 否 |
| Teradata | 是 | 是 | 是 | 是 | 是 | 是 |
| 文本/CSV | 是 | 是 | 否 | 是 | 否 <sup>4</sup> | 是 |
| Twilio | 是 | 是 | 否 | 否 | 否 | 否 |
| tyGraph | 是 | 是 | 否 | 否 | 否 | 否 |
| Vertica | 是 | 是 | 是 | 是 | 是 | 是 |
| Web | 是 | 是 | 否 | 是 | 是<sup>6</sup> | 是 |
| Webtrends | 是 | 是 | 否 | 否 | 否 | 否 |
| 工作人员维度 | 是 | 是 | 否 | 是 | 否 | 否 |
| XML | 是 | 是 | 否 | 是 | 否 <sup>4</sup> | 是 |
| Zendesk | 是 | 是 | 否 | 否 | 否 | 否 |
| | | | | | | | |

<sup>1</sup> 通过 [ACE OLEDB 提供程序](https://www.microsoft.com/download/details.aspx?id=54920)提供支持，与网关安装在同一台计算机上。

<sup>3</sup> Excel 1997-2003 文件 (.xls) 需要 [ACE OLEDB 提供程序](https://www.microsoft.com/download/details.aspx?id=54920)。

<sup>4</sup> 该技术本地版本的必要条件。

<sup>5</sup> 仅通过[个人网关](service-gateway-personal-mode.md)提供支持。

<sup>6</sup>为 .html、.xls 和 Access 数据库所必需

<sup>7</sup> Power BI 服务不支持需要身份验证的 OData 源。

<sup>8</sup> 针对 Power BI 报表服务器优化的 Power BI Desktop 版本中支持 Paxata。 在发布到 Power BI 报表服务器的 Power BI 报表中不受支持。 有关受支持的数据源的列表，请参阅 [Power BI 报表服务器中的 Power BI 报表数据源](../report-server/data-sources.md)。

## <a name="considerations-and-limitations"></a>注意事项和限制

- Power BI Desktop 中的许多数据连接器都需要 Internet Explorer 10（或更高版本）进行身份验证。 
- 针对 Power BI 报表服务器优化的 Power BI Desktop 支持某些数据源，但在发布到 Power BI 报表服务器时不支持这些数据源。 有关受支持的数据源的列表，请参阅 [Power BI 报表服务器中的 Power BI 报表数据源](../report-server/data-sources.md)。

## <a name="single-sign-on-sso-for-directquery-sources"></a>DirectQuery 源的单一登录 (SSO)

启用“SSO”选项后，如果用户访问基于数据源生成的报表，则 Power BI 会在查询中将这些用户的已经过身份验证的 Azure AD 凭据发送到基础数据源。 这样，Power BI 便可以遵守在数据源级别配置的安全设置。
SSO 选项针对使用此数据源的所有数据集生效。 它不影响用于导入方案的身份验证方法。 以下数据源支持通过 DirectQuery 进行连接的 SSO：

- Azure SQL 数据库
- Azure SQL 数据仓库
- Impala
- SAP HANA
- SAP BW
- SAP BW 消息服务器
- Snowflake
- Spark
- SQL Server
- Teradata

## <a name="next-steps"></a>后续步骤

[连接到 Power BI Desktop 中的数据](desktop-quickstart-connect-to-data.md)  
[在 Power BI 中使用 DirectQuery](desktop-directquery-about.md)  
[Power BI 中的 SQL Server Analysis Services 实时数据](sql-server-analysis-services-tabular-data.md)  
[本地数据网关是什么？](service-gateway-onprem.md)  
[Power BI 报表服务器中 Power BI 报表数据源](../report-server/data-sources.md)
---
title: Power BI 中 DirectQuery 支持的数据源
description: 获取数据源可以使用 DirectQuery 的列表。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 97d9fc6bf7a27b9d681d10ae20ab0780622e5ee8
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223389"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Power BI 中 DirectQuery 支持的数据源
Power BI Desktop 和 Power BI 服务有多个可以连接并访问数据的数据源。 本文介绍了支持称为 DirectQuery 的连接方法的 Power BI 数据源。 有关 DirectQuery 的详细信息，请参阅 [Power BI 中的 DirectQuery](desktop-directquery-about.md)。

在 Power BI 中，以下数据源支持 DirectQuery：

* Amazon Redshift
* Azure HDInsight Spark (Beta)
* Azure SQL 数据库
* Azure SQL 数据仓库
* Google BigQuery (Beta)
* IBM DB2 数据库
* IBM Netezza (Beta)
* Impala（版本 2.x）
* Oracle 数据库（版本 12 及更高版本)
* SAP Business Warehouse 应用程序服务器
* SAP Business Warehouse 消息服务器(Beta)
* SAP HANA
* Snowflake
* Spark (Beta)（版本 0.9 及更高版本)
* SQL Server
* Teradata 数据库
* Vertica (Beta)

名称后带有 (Beta) 或（预览）的数据源会发生更改，不支持在生产环境中使用。 在将报表发布到 **Power BI 服务**后，这些数据源可能还不受支持，这意味着打开已发布的报表或浏览数据集会导致错误。

(Beta) 与（预览）数据源之间的唯一区别是（预览）数据源必须先要作为预览功能启用，然后才可供使用。 要启用（预览）数据连接器，请在 Power BI Desktop 中转到“文件”>“选项和设置”>“选项”，然后选择“预览功能”。

> [!NOTE]
> 对 SQL Server 进行 DirectQuery 查询，需要使用当前 Windows 身份验证凭据或数据库凭据进行身份验证，以建立访问。 不支持使用其他凭据。
>

## <a name="on-premises-gateway-requirements"></a>本地网关要求
下表指定在将报表发布到 Power BI 服务后本地数据网关是否需要连接到指定的数据源。

| 源 | 需要网关？ |
| --- | --- |
| SQL Server |是 |
| Azure SQL 数据库 |否 |
| Azure SQL 数据仓库 |否 |
| SAP HANA |是 |
| Oracle 数据库 |是 |
| Teradata 数据库 |是 |
| Amazon Redshift |否 |
| Impala（版本 2.x） |是 |
| Snowflake |是 |
| Spark (Beta)，版本 0.9 及更高版本 |在 Power BI 服务中尚不受支持 |
| Azure HDInsight Spark (Beta) |否 |
| IBM Netezza |是 |
| SAP Business Warehouse 应用程序服务器 |是 |
| SAP Business Warehouse 消息服务器 |在 Power BI 服务中尚不受支持 |
| Google BigQuery |否 |


## <a name="next-steps"></a>后续步骤
有关 DirectQuery 的详细信息，请查看以下资源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [本地数据网关](service-gateway-onprem.md)


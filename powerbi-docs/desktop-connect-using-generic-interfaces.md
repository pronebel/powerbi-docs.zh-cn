---
title: 使用 Power BI Desktop 中的泛型接口连接到数据
description: 了解如何使用 Power BI Desktop 中的泛型接口连接不同的数据源
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6ac121ee5154a9d343a912904b20d3244ebee59c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513717"
---
# <a name="connect-to-data-using-generic-interfaces-in-power-bi-desktop"></a>使用 Power BI Desktop 中的泛型接口连接到数据
使用从**访问数据库**到 **Zendesk** 资源的内置数据连接器，可以连接到 **Power BI Desktop** 中多种不同的数据源，如“**获取数据**”窗口中所示。 还可使用 Power BI Desktop  中内置的泛型接口（如 ODBC  或 REST API  ）连接到所有其他  类型的数据源，进而进一步增加连接选项。

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_1.png)

## <a name="power-bi-desktop-data-interfaces"></a>Power BI Desktop 数据接口
**Power BI Desktop** 包括一个不断增长的数据连接器的集合，用于连接到特定数据源。 例如，**SharePoint 列表**数据连接器在为 **SharePoint 列表**设计的连接顺序期间提供特定字段和支持信息，这与选择“**获取数据 > 更多...** ”时出现的窗口中的其他数据源的情况相同（如上一张图片中所示）。

此外，通过 Power BI Desktop，可采用以下任一泛型数据接口  连接到“获取数据”  列表中未标识的数据源：

* **ODBC**
* **OLE DB**
* **OData**
* **REST API**
* **R 脚本**

通过提供这些泛型接口所提供的连接窗口中的适当参数，在 **Power BI Desktop** 中可以访问和使用的数据源显著增加。

在以下部分中，可以找到通过这些泛型接口进行访问的数据源的列表。

使用 **Power BI Desktop** 无法找到想要使用的数据源？ 请将你的想法提交到 Power BI 团队的[想法和请求列表](https://ideas.powerbi.com/)。

## <a name="data-sources-accessible-through-odbc"></a>数据源可以通过 ODBC 访问
**Power BI Desktop** 中的 **ODBC** 连接器使你仅通过指定**数据源名称(DSN)** 或*连接字符串*即可从任何第三方 ODBC 驱动程序导入数据。 作为一个选项，还可以指定 SQL 语句，以执行 ODBC 驱动程序。

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_2.png)

以下列表详细介绍了通过使用泛型 **ODBC** 接口，**Power BI Desktop** 可以连接到数据源的几个示例。

| Power BI Desktop 泛型连接器 | 外部数据源 | 有关详细信息的链接 |
| --- | --- | --- |
| ODBC |Cassandra |[Cassandra ODBC 驱动程序](http://www.simba.com/drivers/cassandra-odbc-jdbc/) |
| ODBC |Couchbase DB |[Couchbase 和 Power BI](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |
| ODBC |DynamoDB |[DynamoDB ODBC 驱动程序](http://www.simba.com/drivers/dynamodb-odbc-jdbc/) |
| ODBC |Google BigQuery |[BigQuery ODBC 驱动程序](http://www.simba.com/drivers/bigquery-odbc-jdbc/) |
| ODBC |HBase |[HBase ODBC 驱动程序](http://www.simba.com/drivers/hbase-odbc-jdbc/) |
| ODBC |Hive |[Hive ODBC 驱动程序](http://www.simba.com/drivers/hive-odbc-jdbc/) |
| ODBC |IBM Netezza |[IBM Netezza 信息](https://www.ibm.com/support/knowledgecenter/SSULQD_7.2.1/com.ibm.nz.datacon.doc/c_datacon_plg_overview.html) |
| ODBC |Presto |[Presto ODBC 驱动程序](http://www.simba.com/drivers/presto-odbc-jdbc/) |
| ODBC |Project Online |[Project Online 文章](desktop-project-online-connect-to-data.md) |
| ODBC |Progress OpenEdge |[Progress OpenEdge ODBC 驱动程序博文](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.progress.com%2Fblogs%2Fconnect-microsoft-power-bi-to-openedge-via-odbc-driver&data=02%7C01%7CMatt.Masson%40microsoft.com%7C5e63742e6c454308b58a08d4034b5923%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636137069555329811&sdata=gSu2Rq3vZ0uBVOgjaXxd8Y3uBf%2B8DidX6PG33jwAduY%3D&reserved=0) |

## <a name="data-sources-accessible-through-ole-db"></a>数据源可以通过 OLE DB 访问
**Power BI Desktop** 中的 **OLE DB** 连接器使你仅通过指定*连接字符串*即可从任何第三方 OLE DB 驱动程序导入数据。 作为一个选项，也可以指定 SQL 语句来执行 OLE DB 驱动程序。

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_3.png)

以下列表详细介绍了通过使用泛型 **OLE DB** 接口，**Power BI Desktop** 可以连接到数据源的几个示例。

| Power BI Desktop 泛型连接器 | 外部数据源 | 有关详细信息的链接 |
| --- | --- | --- |
| OLE DB |SAS OLE DB |[SAS Provider for OLE DB](https://support.sas.com/downloads/package.htm?pid=648) |
| OLE DB |Sybase OLE DB |[Sybase Provider for OLE DB](http://infocenter.sybase.com/help/index.jsp?topic=/com.sybase.infocenter.dc35888.1550/doc/html/jon1256941734395.html) |

## <a name="data-sources-accessible-through-odata"></a>数据源可以通过 OData 访问
**Power BI Desktop** 中的 **OData** 连接器可使你仅通过键入或粘贴 **OData URL** 即可从 **OData URL** 导入数据。 可以通过键入或粘贴 **OData 源**窗口中提供的文本框中的这些链接来添加多个 URL 部分。

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_4.png)

以下列表详细介绍了通过使用泛型 **OData** 接口，**Power BI Desktop** 可以连接到数据源的几个示例。

| Power BI Desktop 泛型连接器 | 外部数据源 | 有关详细信息的链接 |
| --- | --- | --- |
| OData |即将推出 |OData 数据源即将推出 |

## <a name="data-sources-accessible-through-rest-apis"></a>数据源可通过 REST API 访问
可使用 **REST API** 连接到数据源，因此，请使用支持 **REST** 的所有类型的数据源的数据。

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_5.png)

以下列表详细介绍了通过使用泛型 **REST API** 接口，**Power BI Desktop** 可以连接到数据源的几个示例。

| Power BI Desktop 泛型连接器 | 外部数据源 | 有关详细信息的链接 |
| --- | --- | --- |
| REST API |Couchbase DB |[Couchbase REST API 信息](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |

## <a name="data-sources-accessible-through-r-script"></a>数据源可以通过 R 脚本访问
可以使用 **R 脚本**访问数据源，并使用 **Power BI Desktop** 中的数据。

![](media/desktop-connect-using-generic-interfaces/r-scripts-2.png)

以下列表详细介绍了通过使用泛型 **R 脚本**接口，**Power BI Desktop** 可以连接到数据源的几个示例。

| Power BI Desktop 泛型连接器 | 外部数据源 | 有关详细信息的链接 |
| --- | --- | --- |
| R 脚本 |SAS 文件 |[CRAN 的 R 脚本指南](https://cran.r-project.org/doc/manuals/R-data.html) |
| R 脚本 |SPSS 文件 |[CRAN 的 R 脚本指南](https://cran.r-project.org/doc/manuals/R-data.html) |
| R 脚本 |R 统计文件 |[CRAN 的 R 脚本指南](https://cran.r-project.org/doc/manuals/R-data.html) |

## <a name="next-steps"></a>后续步骤
可使用 Power BI Desktop 连接到各种数据源  。 有关数据源的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   


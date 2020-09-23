---
title: Power BI 数据源必备条件
description: Power BI 数据源必备条件
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 373249061f39c40ec3a78ba9541575721bd60022
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859626"
---
# <a name="power-bi-data-source-prerequisites"></a>Power BI 数据源必备条件
对于每个数据提供程序，Power BI 支持有关对象的特定提供程序版本。 有关适用于 Power BI 的数据源的详细信息，请参阅[数据源](desktop-data-sources.md)。 下表描述了这些要求。

| 数据源 | 提供程序 | 提供程序的最低版本 | 数据源的最低版本 | 受支持的数据源对象 | 下载链接 |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net（在 .Net Framework 中构建） |.NET Framework 3.5（仅限） |SQL Server 2005+ |表/视图、标量函数、表函数 |包含在 .NET Framework 3.5 或更高版本中 |
| 访问 |Microsoft Access 数据库引擎 (ACE) |ACE 2010 SP1 |无限制 |表/视图 |[下载链接](./desktop-access-database-errors.md) |
| Excel（仅限 .xls 文件）（参见备注 1） |Microsoft Access 数据库引擎 (ACE) |ACE 2010 SP1 |无限制 |表、工作表 |[下载链接](./desktop-access-database-errors.md) |
| Oracle（参见备注 2） |ODP.NET |ODAC 11.2 版本 5 (11.2.0.3.20) |9.x+ |表/视图 |[下载链接](./desktop-connect-oracle-database.md) |
| | System.Data.OracleClient（在 .NET Framework 中构建） |.NET Framework 3.5 |9.x+ |表/视图 |包含在 .NET Framework 3.5 或更高版本中 |
| IBM DB2 |来自 IBM 的 ADO.Net 客户端（IBM 数据服务器驱动程序包的一部分） |10.1 |9.1+ |表/视图 |[下载链接](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |连接器/Net |6.6.5 |5.1 |表/视图、标量函数 |[下载链接](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |NPGSQL ADO.NET 提供程序（Power BI Desktop 随附） |4.0.10 |9.4 |表/视图 |[下载链接](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |适用于 Teradata 的 .NET 数据提供程序 |14+ |12+ |表/视图 |[下载链接](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |面向 .NET 3.5 的 iAnywhere.Data.SQLAnywhere |16+ |16+ |表/视图 |[下载链接](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>扩展名为 .xlsx 的 Excel 文件不需要单独安装提供程序。

>[!NOTE]
>Oracle 提供程序还需要 Oracle 客户端软件（版本 8.1.7+）。
> 
>
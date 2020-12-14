---
title: 安装 Power BI 报表服务器所要满足的硬件和软件要求
description: 本文列出了安装并运行 Power BI 报表服务器所要满足的最低硬件和软件要求。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 12/07/2020
ms.openlocfilehash: 10fb104d1c03ae5d08836b8e865178c347d848ce
ms.sourcegitcommit: 0bf42b6393cab7a37d21a52b934539cf300a08e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96781764"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>安装 Power BI 报表服务器所要满足的硬件和软件要求

本文列出了安装并运行 Power BI 报表服务器所要满足的最低硬件和软件要求。

## <a name="processor-memory-and-operating-system-requirements"></a>处理器、内存和操作系统要求

| 组件 | 要求 |
| --- | --- |
| .NET Framework |4.8<br><br>如果服务器无法访问 Internet，则可从[适用于 Windows 的 Microsoft.NET Framework 4.8（脱机安装程序）](https://support.microsoft.com/en-us/help/4503548/)手动安装 .NET Framework。<br/><br/> 有关 .NET Framework 4.8 的详细信息、建议和指南，请参阅[面向开发者的 .NET Framework 部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。<br/><br/>Windows 8.1 和 Windows Server 2012 R2 中必须有 [KB2919355](https://support.microsoft.com/kb/2919355)，才能安装 .NET Framework 4.8。 |
| 硬盘 |Power BI 报表服务器至少需要 1 GB 的可用硬盘空间。<br><br>托管报表服务器数据库的数据库服务器上必须有额外空间。 |
| 内存 |最小：1 GB<br/><br/> 建议：至少 4 GB |
| 处理器速度 |最低要求：x64 处理器：  1.4 GHz<br/><br/> **推荐：** 2.0 GHz 或更快 |
| 处理器类型 |x64 处理器：AMD Opteron、AMD Athlon 64、支持 Intel EM64T 的 Intel Xeon，以及支持 EM64T 的 Intel Pentium IV |
| 操作系统 |Windows Server 2019 Datacenter<br><br>Windows Server 2019 Standard<br><br>Windows Server 2016 Datacenter<br><br>Windows Server 2016 标准版<br><br>Windows 10 家庭版<br><br>Windows 10 专业版<br><br>Windows 10 企业版<br> |

> [!NOTE]
> 只支持在 x64 处理器上安装 Power BI 报表服务器。


## <a name="database-server-version-requirements"></a>数据库服务器版本要求

SQL Server 用于托管报表服务器数据库。 SQL Server 数据库引擎实例可以是本地或远程实例。 以下是可用于托管报表服务器数据的 SQL Server 数据库引擎受支持的版本：

* Azure SQL 托管实例（Power BI 报表服务器 2020 年 1 月版及更高版本）
* SQL Server 2019
* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

在远程计算机上创建报表服务器数据库时，必须将连接配置为使用域用户帐户或具有网络访问权限的服务帐户。 如果决定使用远程 SQL Server 实例，请仔细考虑报表服务器应使用哪些凭据来连接到 SQL Server 实例。 有关详细信息，请参阅[配置报表服务器数据库连接](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)。

## <a name="considerations"></a>注意事项

Power BI 报表服务器将安装默认值，以配置报表服务器正常运行所需的核心设置。 有以下要求：

* Power BI 报表服务器支持的语言包括：英语、德语、西班牙语、日语、意大利语、法语、俄语、简体中文、繁体中文、巴西葡萄牙语和韩语
* 在安装完成之后且在配置报表服务器数据库之前，必须有 SQL Server 数据库引擎。 数据库引擎实例托管 Reporting Services 配置管理器将创建的报表服务器数据库。 实际的安装体验不需要有数据库引擎。
* [SQL Server 各版本支持的 Reporting Services 功能](/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016)概述了 SQL Server 各版本之间的差异。
* 运行安装程序的用户帐户必须是本地管理员组的成员。
* 运行 Reporting Services 配置管理器的用户帐户必须有权在托管报表服务器数据库的数据库引擎实例上访问并创建数据库。
* 安装程序必须能够使用默认值来保留 URL，从而提供对报表服务器和 Web 门户的访问权限。 这些值为端口 80、强通配符以及格式为 ReportServer 和 Reports 的虚拟目录名称。

## <a name="read-only-domain-controller-rodc"></a>只读域控制器 (RODC)

 可以在具有只读域控制器 (RODC) 的环境中安装报表服务器。 但是，Reporting Services 需要访问读-写域控制器才能正常工作。 如果 Reporting Services 只有权访问 RODC，当你在尝试管理此服务时则可能会遇到错误。

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Power BI 报表和 Analysis Services 实时连接

你可以使用针对表格或多维实例的实时连接。 Analysis Services 服务器必须满足适当的版本要求，才能正常工作。

| **服务器版本** | **所需的 SKU** |
| --- | --- |
| 2012 SP1 CU4 或更高版本 |商业智能和企业版 SKU |
| 2014 |商业智能和企业版 SKU |
| 2016 和更高版本 |标准 SKU 或更高版本 |

## <a name="next-steps"></a>后续步骤

[什么是 Power BI 报表服务器？](get-started.md)  
[管理员概述](admin-handbook-overview.md)  
[安装 Power BI 报表服务器](install-report-server.md)  
[下载报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下载 SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

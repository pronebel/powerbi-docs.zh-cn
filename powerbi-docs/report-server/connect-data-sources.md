---
title: Power BI 报表服务器中的分页报表数据源
description: 了解 Power BI 报表服务器中分页报表 (.rdl) 可以连接的数据源。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260706"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Power BI 报表服务器中的分页报表数据源
Power BI 报表服务器中的 Reporting Services 分页报表支持 SQL Server Reporting Services 中所支持的相同数据源。 请参阅列表 [Reporting Services 支持的数据源](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs)。

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>使用 UseInstalledUICulture 连接到 Oracle 数据源

Power BI 报表服务器使用与 NLS 无关的 Oracle Data Provider for .NET (ODP.NET) 连接到 Oracle 数据源。

默认情况下，报表服务器使用第一个客户端的 UI 区域性来加载 ODP.NET。  因此，除非服务重启，否则所有从报表服务器到 Oracle 的后续连接都会采用这一初始 UI 区域性。  这种方法可能会导致报表呈现出现问题，因为 UI 区域性格式不一致。

为了优化 Power BI 报表服务器使用体验，我们引入了配置设置 UseInstalledUICulture。 如果 UseInstalledUICulture 设置为 true，报表服务器始终采用服务器的 UI 区域性（而不是第一个客户端的区域性）加载 ODP.NET。
自 2 月推出的服务版本起，Power BI 报表服务器开始提供此设置

若要启用此功能，请按如下所示修改 ORACLE 扩展条目 rsreportserver.config 文件。
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>后续步骤
现已连接到数据源，接下来可以[创建分页报表](quickstart-create-paginated-report.md)。  


更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

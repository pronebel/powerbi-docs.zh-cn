---
title: 使用 PowerShell 更改数据源连接字符串 - Power BI 报表服务器（2020 年 10 月前）
description: 使用 PowerShell 中的 API 更改数据源连接字符串 - Power BI 报表服务器（2020 年 10 月前）。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.author: maggies
ms.openlocfilehash: 9b4d31b2acc3ce7ec43bbd3fdb91df8e32c2e953
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049393"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server-pre-october-2020"></a>使用 PowerShell 更改 Power BI 报表中的数据源连接字符串 - Power BI 报表服务器（2020 年 10 月前）


可以使用 PowerShell 来更改 Power BI 报表服务器中托管的 Power BI 报表的数据源连接字符串，以便与所需的 API 交互。 

> [!IMPORTANT]
> 如果使用的是最新版 Power BI 报表服务器（2020 年 10 月版），请参阅[使用 PowerShell 更改 Power BI 报表中的数据源连接字符串 - Power BI 报表服务器](connect-data-source-apis.md)。

> [!NOTE]
> 此功能目前仅适用于 DirectQuery。 即将提供对导入和数据刷新的支持。

1. 安装 Power BI 报表服务器 PowerShell commandlet。 在 [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools) 中查找 commandlet 和安装说明。 

    使用以下命令直接从 [PowerShell 库](https://www.powershellgallery.com/packages/ReportingServicesTools/)安装 `ReportingServicesTools` 模块。

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. 通过 PowerShell commandlet 提取 Power BI 文件的现有数据源信息：

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    查看 Power BI 报表中包含的第一个数据源的信息： 

    ```powershell
    $dataSources[0]
    ```

3. 根据需要更新连接和凭据信息。 如果更新连接字符串和数据源使用了存储的凭据，则需要提供帐户密码。 

    更新数据源连接字符串：

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    更改数据源凭据类型：

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    更改数据源用户名/密码：

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. 将更新后的凭据保存回服务器。

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>后续步骤

[Power BI 报表服务器中的分页报表数据源](connect-data-sources.md) 

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

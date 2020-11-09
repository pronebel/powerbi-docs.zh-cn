---
title: 使用 PowerShell 更改数据源连接字符串
description: 使用 PowerShell 中的 API 更改数据源连接字符串 - Power BI 报表服务器。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.author: maggies
ms.openlocfilehash: 165d38c718377ff7e47442cdf0fe67173b610bd8
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044961"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>使用 PowerShell 更改 Power BI 报表中的数据源连接字符串 - Power BI 报表服务器


从 Power BI 报表服务器 2020 年 10 月版开始，我们启用了对 DirectQuery 的 Power BI 报表的连接更新和刷新功能。

> [!IMPORTANT]
> 这也是关于在之前版本中设置此功能的方式的一项重大更改。 如果使用的是 2020 年 10 月前的 Power BI 报表服务器版本，请参阅[使用 PowerShell 更改 Power BI 报表中的数据源连接字符串 - Power BI 报表服务器（2020 年 10 月前）](connect-data-source-apis-pre-oct-2020.md)

## <a name="prerequisites"></a>先决条件：
- 下载 2020 年 10 月版 [Power BI 报表服务器和针对 Power BI 报表服务器优化的 Power BI Desktop](https://powerbi.microsoft.com/report-server/)。
- 使用针对 Power BI 报表服务器优化的 Power BI Desktop（2020 年 10 月版）保存的报表（启用了增强型数据集元数据）。
- 使用参数化连接的报表。 发布后，只能更新使用参数化连接和数据库的报表。
- 此示例使用 Reporting Services PowerShell 工具。 使用新的 REST API 同样可以实现此目的。

## <a name="create-a-report-with-parameterized-connections"></a>创建使用参数化连接的报表
    
1. 创建与服务器的 SQL Server 连接。 在下面的示例中，我们将连接到名为 ReportServer 的数据库，并从 ExecutionLog 拉取数据。

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="连接到 SQL Server 数据库":::

    此时，M 查询将如下所示：

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. 选择“Power Query 编辑器”功能区中的“管理参数”。

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="选择“管理参数”":::

1.  为 servername 和 databasename 创建参数。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="管理参数，设置 servername 和 databasename。":::


3. 编辑第一个连接的查询，并映射数据库和 servername。

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="映射服务器和数据库名称":::

    现在，查询将如下所示：

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. 将该报表发布到服务器。 在此示例中，报表名为 executionlogparameter。 下图是一个数据源管理页示例。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="数据源管理页面。":::

## <a name="update-parameters-using-the-powershell-tools"></a>使用 PowerShell 工具更新参数

1. 打开 PowerShell 并按照 [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools) 中的说明安装最新的 Reporting Services 工具。
    
2.  若要获取报表的参数，请使用利用以下 PowerShell 调用的新 REST DataModelParameters API：

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. 将此调用的结果保存在变量中：

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. 使用需要更改的值更新此变量。
5. 将此调用的结果保存在变量中：

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. 利用更新后的值，我们可以使用 commandlet `Set-RsRestItemDataModelParameters` 来更新服务器中的值：

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. 更新参数后，服务器将更新已绑定到参数的任何数据源。 返回到“编辑数据源”对话框中，你应能够为更新后的服务器和数据库设置凭据。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="为更新后的服务器和数据库设置凭据。":::

## <a name="next-steps"></a>后续步骤

[Power BI 报表服务器中的分页报表数据源](connect-data-sources.md) 

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

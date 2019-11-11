---
title: 管理数据源
description: 了解如何在 Power BI 中管理数据源。
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 1966a9ea38f8ff9d1517b4df5ed0db1254ddf80d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881781"
---
# <a name="manage-data-sources"></a>管理数据源

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Power BI 支持多个本地数据源，每个都具有自己的要求。 网关可用于一个数据源，也可用于多个数据源。 对于此示例，我们演示如何将 SQL Server 添加为数据源。 类似步骤适用于其他数据源。

大多数数据源管理操作也可以使用 API 执行。 有关详细信息，请参阅 [REST API（网关）](/rest/api/power-bi/gateways)。

## <a name="add-a-data-source"></a>添加数据源

1. 在 Power BI 服务的右上角，选择齿轮图标![“设置”齿轮图标](media/service-gateway-data-sources/icon-gear.png) > “管理网关”  。

    ![管理网关](media/service-gateway-data-sources/manage-gateways.png)

2. 选择网关，然后选择“添加数据源”  。 或者，请转到“网关”   > “添加数据源”  。

    ![添加数据源](media/service-gateway-data-sources/add-data-source.png)

3. 选择“数据源类型”  。

    ![选择 SQL Server](media/service-gateway-data-sources/select-sql-server.png)

4. 输入数据源的信息。 对于此示例，可以是“服务器”、“数据库”和其他信息   。 

    ![数据源设置](media/service-gateway-data-sources/data-source-settings.png)

5. 对于 SQL Server，可以选择“Windows”或“基本”的身份验证方法（SQL 身份验证）    。 如果选择“基本”  ，则输入数据源的凭据。

6. 在“高级设置”下，可以选择配置数据源的[隐私级别](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)（不适用于 [DirectQuery](desktop-directquery-about.md)）  。

    ![高级设置](media/service-gateway-data-sources/advanced-settings.png)

7. 选择**添加**。 如果过程成功，会看到“连接成功”  。

    ![连接成功](media/service-gateway-data-sources/connection-successful.png)

现在可以使用此数据源在 Power BI 仪表板和报表中包含来自 SQL Server 的数据。

## <a name="remove-a-data-source"></a>删除数据源

如果不再使用数据源，则可以将其删除。 删除数据源将中断依赖于该数据源的所有仪表板和报表。

若要删除数据源，请转到该数据源，然后选择“删除”  。

![删除数据源](media/service-gateway-data-sources/remove-data-source.png)

## <a name="use-the-data-source-for-scheduled-refresh-or-directquery"></a>将数据源用于计划刷新或 DirectQuery

创建数据源后，可通过 DirectQuery 连接或通过计划刷新使用该数据源。

> [!NOTE]
>在 Power BI Desktop 和本地数据网关内的数据源之间，服务器名称和数据库名称必须匹配。

数据集和网关内的数据源之间的链接基于服务器名称和数据库名称。 这些名称必须匹配。 例如，如果在 Power BI Desktop 内为服务器名称提供 IP 地址，则需要在网关配置中使用数据源的 IP 地址。 如果在 Power BI Desktop 中使用了 SERVER\INSTANCE，则为网关配置的数据源中也必须使用它  。

如果你被列于网关内配置的数据源的“用户”选项卡中，并且服务器和数据库名称匹配，则你可以看到网关显示为计划刷新的一个选项  。

![网关连接](media/service-gateway-data-sources/gateway-connection.png)

> [!WARNING]
> 如果数据集包含多个数据源，则必须在网关内添加每个数据源。 如果未将一个或多个数据源添加到网关，则不会看到可用于计划刷新的网关。

### <a name="limitations"></a>限制

只有具有本地数据网关的自定义连接器支持 OAuth 身份验证方案。 无法添加需要 OAuth 的其它数据源。 如果数据集具有需要 OAuth 的数据源，而且该数据源不是自定义的连接器，则无法使用网关进行计划刷新。

## <a name="manage-users"></a>管理用户

将数据源添加到网关后，将为用户和启用电子邮件的安全组提供对特定数据源（不是整个网关）的访问权限。 数据源用户列表仅控制有权发布包含来自数据源的数据的报表的用户。 报表所有者可以创建仪表板、内容包和应用，然后与其他用户共享这些项。

还可以为用户和安全组提供对网关的管理访问权限。

### <a name="add-users-to-a-data-source"></a>将用户添加到数据源

1. 在 Power BI 服务的右上角，选择齿轮图标![“设置”齿轮图标](media/service-gateway-data-sources/icon-gear.png) > “管理网关”  。

2. 选择要添加用户的数据源。

3. 选择“用户”  ，然后输入组织中想要授予对所选数据源的访问权限的用户。 例如，在下面的屏幕中，你会添加 Maggie 和 Adam。

    ![“用户”选项卡](media/service-gateway-data-sources/users-tab.png)

4. 选择“添加”  ，此时框中将显示所添加成员的姓名。

    ![添加用户](media/service-gateway-data-sources/add-user.png)

请注意，需要将用户添加到你希望向其授予访问权限的每个数据源。 每个数据源都具有单独的用户列表。 将用户单独添加到每个数据源。

### <a name="remove-users-from-a-data-source"></a>从数据源中删除用户

在数据源的“用户”  选项卡上，可以删除使用此数据源的用户和安全组。

![删除用户](media/service-gateway-data-sources/remove-user.png)

## <a name="store-encrypted-credentials-in-the-cloud"></a>在云中存储加密凭据

将数据源添加到网关时，必须为该数据源提供凭据。 将使用这些凭据运行对数据源的所有查询。 凭据会安全地进行加密。 在云中存储凭据之前，它们会使用对称加密，使其在云中无法被解密。 将凭据发送到运行网关的计算机，以便在访问数据源时对其进行本机解密。

## <a name="list-of-available-data-source-types"></a>可用数据源类型的列表

本地数据网关支持 Power BI 的以下数据源。 除了本地数据源之外，防火墙、VPN 或虚拟网络后面的源可能也需要数据网关。

| **数据源** | **实时/DirectQuery** | **手动或计划刷新（用户配置）** |
| --- | --- | --- |
| Amazon Redshift |是 |是 |
| Analysis Services |是 |是 |
| AtScale 多维数据集 |是 |是 |
| Azure Active Directory |否 |是 |
| Azure Blob 存储 |否 |是 |
| Azure DevOps Server |否 |是 |
| Azure 表存储 |否 |是 |
| BI 连接器 |是 |是 |
| Denodo |是 |是 |
| Dremio |是 |是 |
| EmigoDataSourceConnector |否 |是 |
| Essbase |是 |是 |
| Exasol |是 |是 |
| 文件 |否 |是 |
| 文件夹 |否 |是 |
| Paxata |否 |是 |
| IBM DB2 |是 |是 |
| IBM Informix 数据库 |否 |是 |
| IBM Netezza |是 |是 |
| Impala |是 |是 |
| Jethro ODBC |是 |是 |
| Kyligence Enterprise |是 |是 |
| MarkLogic ODBC |是 |是 |
| Microsoft Graph Security |否 |是 |
| MySQL |否 |是 |
| ODBC |否 |是 |
| OData |否 |是 |
| OLE DB |否 |是 |
| Oracle |是 |是 |
| PostgreSQL |否 |是 |
| QubolePresto |是 |是 |
| Quick Base 连接器 |否 |是 |
| SAP Business Warehouse 消息服务器 |是 |是 |
| SAP Business Warehouse 服务器 |是 |是 |
| SAP HANA |是 |是 |
| SQL Server |是 |是 |
| SharePoint |否 |是 |
| Snowflake |是 |是 |
| Spark |是 |是 |
| SurveyMonkey |否 |是 |
| Sybase |否 |是 |
| TeamDesk.Database |否 |是 |
| Teradata |是 |是 |
| Vertica |是 |是 |
| Web |否 |是 |
| 工作人员维度 |否 |是 |

## <a name="next-steps"></a>后续步骤

* [管理数据源 - Analysis Services](service-gateway-enterprise-manage-ssas.md)
* [管理数据源 - SAP HANA](service-gateway-enterprise-manage-sap.md)
* [管理数据源 - SQL Server](service-gateway-enterprise-manage-sql.md)
* [管理数据源 - Oracle](service-gateway-onprem-manage-oracle.md)
* [管理数据源 - 导入/计划刷新](service-gateway-enterprise-manage-scheduled-refresh.md)
* [部署数据网关指南](service-gateway-deployment-guidance.md)

更多问题？ 尝试参与 [Power BI 社区](https://community.powerbi.com/)。

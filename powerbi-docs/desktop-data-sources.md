---
title: Power BI Desktop 中的数据源
description: Power BI Desktop 中的数据源
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f5fc52df86faa69683fa1e76f8893fb1d1a09ab9
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54281151"
---
# <a name="data-sources-in-power-bi-desktop"></a>Power BI Desktop 中的数据源
使用 Power BI Desktop，你可以连接到来自许多不同的源的数据。 在此页面底部列出了可用数据源的完整清单。

若要连接到数据，请在**主页**功能区中选择 **获取数据**。 选择向下箭头，或按钮上的“获取数据”文本，将会显示最常见的数据类型菜单，如下图所示：

![在 Power BI Desktop 中获取数据](media/desktop-data-sources/data-sources_01.png)

从**最常见**菜单选择 **更多…** 将会显示**获取数据**窗口。 你还可以通过直接选择 **获取数据** **图标按钮** 来打开 **获取数据** 窗口（绕过 **最常见** 菜单）。

![“获取数据”按钮](media/desktop-data-sources/data-sources_02.png)

> [!NOTE]
> Power BI 团队正在不断扩展适用于 Power BI Desktop 和 Power BI 服务的数据源。 因此，你通常会看到工作过程中的数据源版本标记为 *Beta* 或*预览*。 标记为 *Beta* 或*预览*的任何数据源所提供的支持和功能有限，不应在生产环境中使用。

## <a name="data-sources"></a>数据源
数据类型分为以下类别：

* 全部
* 文件
* 数据库
* Power BI
* Azure
* Online Services
* 其他

**全部**类别包括来自所有类别的所有数据连接类型。

**文件**类别提供下列数据连接：

* Excel
* 文本/CSV
* XML
* JSON
* 文件夹
* PDF (Beta)
* SharePoint 文件夹

下图显示**文件**的**获取数据**窗口。

![“获取数据”>“文件”](media/desktop-data-sources/data-sources_03.png)

**数据库**类别提供下列数据连接：

* SQL Server 数据库
* Access 数据库
* SQL Server Analysis Services 数据库
* Oracle 数据库
* IBM DB2 数据库
* IBM Informix 数据库 (Beta)
* IBM Netezza
* MySQL 数据库
* PostgreSQL 数据库
* Sybase 数据库
* Teradata 数据库
* SAP HANA 数据库
* SAP Business Warehouse 应用程序服务器
* SAP Business Warehouse 消息服务器
* Amazon Redshift
* Impala
* Google BigQuery
* Snowflake
* Essbase (Beta)
* BI 连接器
* Exasol
* Dremio (Beta)
* Jethro (Beta)
* Kyligence Enterprise (Beta)

> [!NOTE]
> 某些数据库连接器需要通过选择“文件”>“选项和设置”>“选项”，然后再选择“预览功能”才能启用。 如果你没有看到上面提到的某些连接器，但想使用它们，请检查“预览功能”设置。 另请注意，标记为 *Beta* 或*预览*的任何数据源所提供的支持和功能有限，不应在生产环境中使用。

下图显示**数据库**的**获取数据**窗口。

![“获取数据”>“数据库”](media/desktop-data-sources/data-sources_04.png)

“Power BI”类别提供下列数据连接：

* Power BI 数据集
* Power BI 数据流 (Beta)

下图显示 Power BI 的“获取数据”窗口。

![“获取数据”>“Power BI”](media/desktop-data-sources/data-sources_05.png)

**Azure** 类别提供下列数据连接：

* Azure SQL 数据库
* Azure SQL 数据仓库
* Azure Analysis Services 数据库
* Azure Blob 存储
* Azure 表存储
* Azure Cosmos DB (Beta)
* Azure Data Lake Storage
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight 交互式查询
* Azure 数据资源管理器 (Beta)

下图显示 **Azure** 的**获取数据**窗口。

![“获取数据”>“Azure”](media/desktop-data-sources/data-sources_06.png)

**Online Services** 类别提供下列数据连接：

* SharePoint Online 列表
* Microsoft Exchange Online
* Dynamics 365 (联机)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (本地)
* Common Data Service for Apps (Beta)
* Microsoft Azure 使用见解 (Beta)
* Azure DevOps (Beta)
* Azure DevOps Server (Beta)
* Salesforce 对象
* Salesforce 报表
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* comScore Digital Analytix (Beta)
* Dynamics 365 for Customer Insights (Beta)
* Data.World - 获取数据集 (Beta)
* Facebook
* GitHub (Beta)
* MailChimp (Beta)
* Marketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One - PRM (Beta)
* Planview Projectplace (Beta)
* QuickBooks Online (Beta)
* Smartsheet
* SparkPost (Beta)
* Stripe (Beta)
* SweetIQ (Beta)
* Planview Enterprise One - CMT (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* Zendesk (Beta)
* TeamDesk (Beta)

下图显示 **Online Services** 的**获取数据**窗口。

![“获取数据”>“联机服务”](media/desktop-data-sources/data-sources_07.png)

**其他**类别提供下列数据连接：

* Vertica
* Web
* SharePoint 列表
* OData 数据源
* Active Directory
* Microsoft Exchange
* Hadoop 文件 (HDFS)
* Spark
* R 脚本
* Python 脚本
* ODBC
* OLE DB
* Denado
* Paxata (Beta)
* 空白查询

下图显示**其他**的**获取数据**窗口。

![“获取数据”>“其他”](media/desktop-data-sources/data-sources_08.png)

> [!NOTE]
> 此时，无法连接到使用 Azure Active Directory 保护的自定义数据源。

## <a name="connecting-to-a-data-source"></a>连接到数据源
若要连接到数据源，请从**获取数据**窗口选择数据源，然后选择**连接**。 在下图中，已从**其他**数据连接类别中选择了 **Web**。

![连接到 Web](media/desktop-data-sources/data-sources_08a.png)

将显示特定于数据连接类型的连接窗口。 如果需要提供凭据，将提示你提供凭据。 下图显示输入 URL 以便连接到 Web 数据源。

![输入 Web URL](media/desktop-data-sources/datasources_fromwebbox.png)

输入 URL 或资源连接信息后，选择**确定**。 Power BI Desktop 会建立到数据源的连接，并在**导航器**中显示可用的数据源。

![导航器屏幕](media/desktop-data-sources/datasources_fromnavigatordialog.png)

可以通过选择**导航器窗格**底部的**加载**按钮加载数据，或者选择**编辑**按钮，在加载数据之前编辑查询。

这就是连接到 Power BI Desktop 中的数据源的所有相关信息！ 尝试从我们不断增多的数据源列表连接到数据，并经常回访 - 我们会持续将数据源添加到此列表中。

## <a name="next-steps"></a>后续步骤
Power BI Desktop 可用于执行多种操作。 有关其功能的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 的查询概述](desktop-query-overview.md)
* [Power BI Desktop 中的数据类型](desktop-data-types.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常见查询任务](desktop-common-query-tasks.md)    

---
title: 了解如何连接 Power BI 中的数据流
description: 了解 Power BI 中数据流的工作原理
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5bf9694c42a3a70fbc65085326a03618ae62a8f6
ms.sourcegitcommit: 91ac6185f7026ddbaa925dc54057bb742b4fa411
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/16/2019
ms.locfileid: "56324912"
---
# <a name="connect-to-data-sources-for-power-bi-dataflows-preview"></a>连接到 Power BI 数据流的数据源（预览）

使用 Power BI 数据流，可以连接到多个不同的数据源，以创建新的数据流，或将新实体添加到现有数据流。

本文列出了许多可用于创建或添加数据流的可用数据源，并介绍了如何使用这些数据源来创建这些数据流。

有关如何创建和使用数据流的概述，请参阅[在 Power BI 中创建和使用数据流（预览）](service-dataflows-create-use.md)。

## <a name="create-a-dataflow-from-a-data-source"></a>从数据源创建数据流

要连接到数据，请从“Power BI 服务”中选择“+ 创建”菜单项，然后从显示的菜单项中选择“数据流”。 选中此选项后，Power BI 服务的画布中将显示以下图像。 

![添加新的数据流或实体](media/service-dataflows-data-sources/dataflows-data-sources_01.png)

如果数据流已存在，则可以通过选择“添加实体”（如下所示）或在数据流创作工具中选择“获取数据”，将新实体添加到数据流中。

![将实体添加到现有数据流](media/service-dataflows-data-sources/dataflows-data-sources_02.png)

下图显示数据流创作工具中的“获取数据”按钮。 

![使用“获取数据”添加实体](media/service-dataflows-data-sources/dataflows-data-sources_03.png)


## <a name="data-sources-for-dataflows"></a>数据流的数据源

可以通过从数据流创作工具中选择“获取数据”来查看可用数据源，随后将显示用于选择类别和每个数据源的对话框，如下图所示。


![获取数据流的数据类别](media/service-dataflows-data-sources/dataflows-data-sources_04.png)

数据流的数据源分为以下类别，这些类别显示在“获取数据”对话框的顶部：

* 所有类别
* 文件
* 数据库
* Power BI
* Azure
* Online Services
* 其他

“所有类别”类别包含来自所有类别的全部数据源。 

“文件”类别包括以下用于数据流的可用数据连接：

* 访问
* Excel
* JSON
* 文本/CSV
* XML

“数据库”类别包括以下用于数据流的可用数据连接：

* IBM DB2 数据库
* MySQL 数据库
* Oracle 数据库
* PostgreSQL 数据库
* SQL Server 数据库
* Sybase 数据库
* Teradata 数据库
* Vertica

“Power BI”类别包括以下用于数据流的可用数据连接：

* Power BI 数据流

“Azure”类别包括以下用于数据流的可用数据连接：

* Azure Blob
* Azure 数据资源管理器
* Azure SQL 数据仓库
* Azure SQL 数据库
* Azure 表

“联机服务”类别包括以下用于数据流的可用数据连接：

* Amazon Redshift
* 面向应用程序的 Common Data Service
* Microsoft Exchange Online
* Salesforce 对象
* Salesforce 报表
* SharePoint Online 列表
* Smartsheet

“其他”类别包括以下用于数据流的可用数据连接：

* Active Directory
* OData
* SharePoint 列表
* Web API
* 网页
* 空白表格
* 空白查询


## <a name="connecting-to-a-data-source"></a>连接到数据源

选择数据源以连接到数据源。 我们将使用一个示例来说明该过程的工作原理，但数据流的每个数据连接过程都是类似的。 不同的连接器可能需要特定凭据或其他信息，但流都是类似的。 在本示例中，在下图中可以看到“面向应用程序的 CDS”是从“联机服务”数据连接类别中选择的。

![选择面向应用程序的 CDS](media/service-dataflows-data-sources/dataflows-data-sources_05.png)

所选数据连接的连接窗口随即显示。 如果需要提供凭据，系统会提示你提供凭据。 下图显示了为连接到面向应用程序的 CDS 服务器而输入的服务器 URL。

![用于数据连接的凭据或 URL](media/service-dataflows-data-sources/dataflows-data-sources_06.png)

提供服务器 URL 或资源连接信息后，请选择“登录”以输入用于数据访问的凭据，然后选择“下一步”。

“Power Query Online”发起并建立与数据源的连接，然后在“导航器”窗口中显示该数据源中的可用表，如下图所示。

![导航器窗口显示数据源中的表](media/service-dataflows-data-sources/dataflows-data-sources_07.png)

可以通过选中左窗格中旁边的每个复选框来选择要加载的表和数据。 加载数据，请从“导航器”窗格底部选择“确定”。 “Power Query Online”对话框随即出现，可以在其中编辑查询并执行要对所选数据执行的任何其他转换。

![在 Power Query 编辑器中编辑查询和转换](media/service-dataflows-data-sources/dataflows-data-sources_08.png)

以上是其中包含的全部内容。 其他数据源有类似的流，并使用 Power Query Online 编辑和转换引入数据流的数据。

## <a name="connecting-to-additional-data-sources"></a>连接到其他数据源

还有一些其他的数据连接器没有显示在 Power BI 数据流用户界面中，但通过执行一些附加步骤可以获得。 

可以执行以下步骤来创建连接到没有显示在用户界面中的连接器：

1. 打开“Power BI Desktop”并选择“获取数据”。
2. 在 Power BI Desktop 中打开“Power Query 编辑器”，然后右键单击相关查询并打开“高级编辑器”，如下图所示。 在此处，可以复制显示在高级编辑器中的 M 脚本。

    ![从 Power BI Desktop 的高级编辑器中复制 M 脚本](media/service-dataflows-data-sources/dataflows-data-sources_09.png) 

3. 打开 Power BI 数据流，并为空白查询选择“获取数据”，如下图所示。

    ![创建用于数据流的空白查询](media/service-dataflows-data-sources/dataflows-data-sources_10.png) 

4. 将复制的查询粘贴到数据流的空白查询中。

    ![将 M 脚本复制到编辑器窗口](media/service-dataflows-data-sources/dataflows-data-sources_11.png) 

随后，脚本将连接到指定的数据源。 

以下列表显示了通过复制 M 查询并将其粘贴到空白查询，当前可以使用的连接器：

* SAP Business Warehouse 
* Azure Analysis Services
* Adobe Analytics
* ODBC
* OLE DB
* 文件夹
* SharePoint Online 文件夹
* SharePoint 文件夹
* Hadoop HDFS
* Azure HDInsight (HDFS)
* Hadoop 文件 HDFS
* Informix (beta)

这就是连接到 Power BI 数据流中的数据源的所有相关信息。


## <a name="next-steps"></a>后续步骤

本文介绍了可以连接到数据流的数据源。 以下文章详细介绍了数据流的常见使用方案。 

* [Power BI 中的自助服务数据准备（预览）](service-dataflows-overview.md)
* [在 Power BI 中创建和使用数据流](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用计算实体（预览）](service-dataflows-computed-entities-premium.md)
* [将数据流与本地数据源配合使用（预览）](service-dataflows-on-premises-gateways.md)
* [Power BI 数据流的开发人员资源（预览）](service-dataflows-developer-resources.md)
* [数据流和 Azure Data Lake 集成（预览）](service-dataflows-azure-data-lake-integration.md)

有关 Power Query 和计划刷新的详细信息，可以阅读以下文章：
* [Power BI Desktop 中的查询概述](desktop-query-overview.md)
* [配置计划刷新](refresh-scheduled-refresh.md)

有关通用数据模型的详细信息，可以阅读其概述文章：
* [通用数据模型 - 概述](https://docs.microsoft.com/powerapps/common-data-model/overview)


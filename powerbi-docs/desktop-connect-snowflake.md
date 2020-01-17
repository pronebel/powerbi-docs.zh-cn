---
title: 在 Power BI Desktop 中连接到 Snowflake 计算仓库
description: 轻松地连接到并使用 Power BI Desktop 中的 Snowflake 计算仓库
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a62d1cf6d21df822265c3c41d4e74e74181b7051
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885182"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>在 Power BI Desktop 中连接到 Snowflake 计算仓库
在 Power BI Desktop 中，你可以连接到 **Snowflake** 计算仓库，并可如同使用 Power BI Desktop 中任何其他数据源一样使用基础数据。 

> [!NOTE]
> 此外，在使用 **Snowflake** 连接器的计算机上，你必须  使用匹配 **Power BI Desktop** 32 位或 64 位安装的体系结构安装 **Snowflake ODBC 驱动程序**。 只需按照以下链接操作，并[下载合适的 Snowflake ODBC 驱动程序](https://go.microsoft.com/fwlink/?LinkID=823762)。
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>连接到 Snowflake 计算仓库
要连接到 Snowflake 计算仓库，请从 Power BI Desktop 中的“开始”功能区选择“获取数据”    。 选择左侧类别中的“数据库”  ，然后便会看到“Snowflake”  。

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

在出现的 **Snowflake** 窗口中，将你的 Snowflake 计算仓库名称键入或粘贴到框中，然后选择“**确定**”。 请注意，可以选择将数据直接**导入**到 Power BI 中，或使用 **DirectQuery**。 可以了解有关[使用 DirectQuery](desktop-use-directquery.md) 的详细信息。

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

出现提示时，输入你的用户名和密码。

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> 一旦输入用户名和密码以连接特定 Snowflake  服务器，Power BI Desktop 在后续连接尝试中就会使用这些凭据。 可以通过“文件”>“选项和设置”>“数据源设置”  来修改这些凭据。
> 
> 

要使用 Microsoft 帐户选项，请让你的 Snowflake 管理员联系 Snowflake，了解如何加入此功能的个人预览版。

![Snowflake 连接器中的 Microsoft 帐户身份验证类型。](media/desktop-connect-snowflake/connect-snowflake-6.png)


连接成功后，将会出现“导航器”  窗口，并显示服务器上可用的数据。你可以从这些数据中选择要在 **Power BI Desktop** 中导入和使用的一个或多个元素。

![ODBC 错误 28000，导致连接失败。](media/desktop-connect-snowflake/connect_snowflake_5.png)

你可以**加载**选定的表，该操作将把整个表格加载到 **Power BI Desktop**中，或者你也可以**编辑**查询，这将打开**查询编辑器**，以便筛选和优化要使用的数据集，然后将优化后的数据集加载到 **Power BI Desktop** 中。

## <a name="next-steps"></a>后续步骤
你可以使用 Power BI Desktop 连接到各种数据。 有关数据源的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   


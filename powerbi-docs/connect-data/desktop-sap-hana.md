---
title: 在 Power BI Desktop 中使用 SAP HANA
description: 在 Power BI Desktop 中使用 SAP HANA
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3d78ded05d199676708c0000cab043226a47b166
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222805"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>连接到 Power BI Desktop 中的 SAP HANA 数据库

使用 Power BI Desktop，你现在可以访问 *SAP HANA* 数据库。 若要使用 SAP HANA，必须在本地客户端计算机上安装 SAP HANA ODBC 驱动程序，Power BI Desktop 的 SAP HANA 数据连接才能正常运行。 可以从 [SAP 开发工具](https://tools.hana.ondemand.com/#hanatools)下载 SAP HANA 客户端工具，其中包含所需的 ODBC 驱动程序。 也可以从 [SAP 软件下载中心](https://support.sap.com/en/my-support/software-downloads.html)获取。 在“软件”门户中，搜索 Windows 计算机的 SAP HANA 客户端  。 由于 SAP 软件下载中心的结构经常发生变化，因此没有有关站点导航的更多具体指导。

要连接 SAP HANA 数据库，请依次选择“获取数据”>“数据库” > “SAP HANA 数据库”>“连接”     ：

![SAP HANA 数据库，“获取数据”对话框，Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

连接到 SAP HANA 数据库时，请指定服务器名称。 然后从下拉框和输入框中指定端口。

在此版本中，Power BI Desktop 和 Power BI 服务均支持 [DirectQuery](desktop-directquery-sap-hana.md) 模式下的 SAP HANA。 可以将在 DirectQuery 模式下使用 SAP HANA 的报表发布和上传到 Power BI 服务。 在 DirectQuery 模式下不使用 SAP HANA 时，也可将报表发布和上传到 Power BI Service。

## <a name="supported-features-for-sap-hana"></a>SAP HANA 支持的功能

此版本提供了许多 SAP HANA 功能，如以下列表所示：

* 适用于 SAP HANA 的 Power BI 连接器使用 SAP ODBC 驱动程序来提供最佳的用户体验。

* SAP HANA 支持 DirectQuery 和“导入”选项。

* Power BI 支持 HANA 信息模型（如 Analytic 和计算视图），且具有经过优化的导航。

* 通过 SAP HANA，还可以使用直接 SQL 功能连接到行表和列表。

* Power BI 包括对 HANA 模型的优化导航。

* Power BI 支持 SAP HANA 变量和输入参数。

* Power BI 支持基于 HDI 容器的计算视图。

  * 在 2019 年 8 月发布的 Power BI Desktop 版本中，以公共预览版形式推出对基于 HDI 容器的计算视图的支持。 要在 Power BI 中访问基于 HDI 容器的计算视图，请确保用于 Power BI 的 HANA 数据库用户有权访问其中存储着你要访问的视图的 HDI 运行时容器。 若要授予此访问权限，请创建允许访问 HDI 容器的角色。 然后，将角色分配给将与 Power BI 一起使用的 HANA 数据库用户。 （和往常一样，此用户还必须具有从 \_SYS\_BI 架构中的系统表中读取内容的权限。）要详细了解如何创建和分配数据库角色，请参阅 SAP 官方文档。 不妨先从阅读[此篇 SAP 博客文章](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/)开始。

  * 附加到基于 HDI 的计算视图的 HANA 变量当前存在一些限制。 这些限制是因为 HANA 方面出错。
  
    首先，无法将 HANA 变量应用到基于 HDI 容器的计算视图的共享列中。 若要修复这一限制，请升级到 HANA 2 版本 37.02 及更高版本或 HANA 2 版本 42 及更高版本。 其次，变量和参数的多项默认值当前不在 Power BI UI 中显示。 SAP HANA 中的错误会导致此限制，但是 SAP 尚未发布修复程序。

## <a name="limitations-of-sap-hana"></a>SAP HANA 的限制

SAP HANA 的使用也具有一些限制，如下所示：

* NVARCHAR 字符串截断的最大长度为 4000 个 Unicode 字符。
* 不支持 SMALLDECIMAL。
* 不支持 VARBINARY。
* 有效日期在 1899/12/30 和 9999/12/31 之间。

## <a name="next-steps"></a>后续步骤

有关 DirectQuery 和 SAP HANA 的详细信息，请参阅以下资源：

* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [在 Power BI 中使用 DirectQuery](desktop-directquery-about.md)
* [Power BI 数据源](power-bi-data-sources.md)
* [启用 SAP HANA 加密](desktop-sap-hana-encryption.md)

---
title: 在 Power BI Desktop 中使用 SAP HANA
description: 在 Power BI Desktop 中使用 SAP HANA
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7b3a59ae8926ce5e302cfcdecec617d1f3fd107b
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2019
ms.locfileid: "65513880"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>在 Power BI Desktop 中使用 SAP HANA
使用 Power BI Desktop，你现在可以访问 **SAP HANA** 数据库。 若要使用 **SAP HANA**，必须在本地客户端计算机上按顺序安装 SAP HANA ODBC 驱动程序，以使 Power BI Desktop **SAP HANA** 数据连接能够正常运行。 可以从 [SAP 软件下载中心](https://support.sap.com/swdc)下载 SAP HANA ODBC 驱动程序。 在这里，搜索 Windows 计算机的 SAP HANA 客户端。 由于 **SAP 软件下载中心**的结构经常发生变化，因此没有有关站点导航的更多具体指导。

要连接 SAP HANA 数据库，请依次选择“获取数据”>“数据库”>“SAP HANA 数据库”，如下图所示：

![](media/desktop-sap-hana/sap-hana-1.png)

连接到 SAP HANA 数据库时，指定服务器名称和端口，格式为*服务器:端口* - 下图显示名称为 *ServerXYZ* 的服务器和端口 *30015* 的示例。

![](media/desktop-sap-hana/sap-hana-2.png)

在此版本中，Power BI Desktop 和 Power BI 服务支持 [DirectQuery](desktop-directquery-sap-hana.md) 模式中的 SAP HANA，而且对于使用 DirectQuery 模式中的 SAP HANA 的报表，用户可将其发布和上传到 Power BI 服务。 在 DirectQuery 模式中不使用 **SAP HANA** 时你也可以向 Power BI Service 发布和上传报表。

## <a name="supported-features-for-sap-hana"></a>SAP HANA 支持的功能
此版本有很多适用于 **SAP HANA** 的功能，如以下列表所示：

* 适用于 SAP HANA 的 Power BI 连接器使用 SAP ODBC 驱动程序，以提供最佳使用体验
* **SAP HANA** 支持 DirectQuery 和导入选项
* Power BI 支持 HANA 信息模型（如 Analytic 和 Calc 视图），并具有经过优化的导航
* 通过 SAP HANA，还可以使用直接 SQL 功能连接到单行表和列表
* 包括对 HANA 模型的优化导航
* Power BI 支持 **SAP HANA** 变量和输入参数

## <a name="limitations-of-sap-hana"></a>SAP HANA 的限制
**SAP HANA** 的使用也具有一些限制，如下所示：

* NVARCHAR 字符串截断的最大长度为 4000 个 Unicode 字符
* 不支持 SMALLDECIMAL
* 不支持 VARBINARY
* 有效日期在 1899/12/30 和 9999/12/31 之间


## <a name="next-steps"></a>后续步骤
有关 DirectQuery 的详细信息，请查看以下资源：

* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支持的数据源](desktop-directquery-data-sources.md)


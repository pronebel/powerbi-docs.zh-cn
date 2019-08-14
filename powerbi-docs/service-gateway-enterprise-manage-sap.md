---
title: 管理数据源 - SAP HANA
description: 如何管理本地数据网关和属于该网关的数据源。 本文特定于 SAP HANA。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2458c99192779c0597c38ea9f3a3baf23f4e1dd2
ms.sourcegitcommit: 9665bdabce3bfc31f68dd8256b135bfd56f60589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2019
ms.locfileid: "68832482"
---
# <a name="manage-your-data-source---sap-hana"></a>管理数据源 - SAP HANA

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

[安装本地数据网关](/data-integration/gateway/service-gateway-install)之后，需要[添加可与该网关结合使用的数据源](service-gateway-data-sources.md#add-a-data-source)。 本文介绍如何使用用于计划刷新或 DirectQuery 的网关和 SAP HANA 数据源。

## <a name="add-a-data-source"></a>添加数据源

有关如何添加数据源的详细信息，请参阅[添加数据源](service-gateway-data-sources.md#add-a-data-source)。 在“数据源类型”下，选择 SAP HANA   。

![添加 SAP HANA 数据源](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

选择 SAP HANA 数据源类型后，请填写数据源的“服务器”、“用户名”和“密码”信息    。

> [!NOTE]
> 将使用这些凭据运行对数据源的所有查询。 若要详细了解如何存储凭据，请参阅[在云中存储加密凭据](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud)。

![填充数据源设置](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

填写所有内容之后，选择“添加”  。 现在你可以使用此数据源对本地 SAP HANA 服务器进行计划刷新或 DirectQuery。 如果成功，则会看到“连接成功”  。

![显示连接状态](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>高级设置

为数据源配置隐私级别（可选）。 此设置可控制数据的组合方式。 它仅适用于计划刷新。 隐私级别设置不适用于 DirectQuery。 若要详细了解数据源的隐私级别，请参阅[隐私级别 (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)。

![设置隐私级别](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="use-the-data-source"></a>使用数据源

创建数据源后，可通过 DirectQuery 连接或通过计划刷新使用该数据源。

> [!NOTE]
> 在 Power BI Desktop 和本地数据网关内的数据源之间，服务器名称和数据库名称必须匹配。

数据集和网关内的数据源之间的链接取决于服务器名称和数据库名称。 这些名称必须匹配。 例如，如果在 Power BI Desktop 内为服务器名称提供了某 IP 地址，则网关配置中的数据源也必须使用该 IP 地址。 如果在 Power BI Desktop 中使用了 SERVER\INSTANCE，则为网关配置的数据源中也必须使用它  。

此要求适用于 DirectQuery 和计划刷新这两种情况。

### <a name="use-the-data-source-with-directquery-connections"></a>在 DirectQuery 连接中使用数据源

确保 Power BI Desktop 和为网关配置的数据源之间的服务器名称和数据库名称相互匹配。 还需确保用户列在数据源的“用户”选项卡中，以便发布 DirectQuery 数据集  。 首次导入数据时，需要在 Power BI Desktop 中选择 DirectQuery。 有关如何使用 DirectQuery 的详细信息，请参阅[在 Power BI Desktop 中使用 DirectQuery](desktop-use-directquery.md)。

发布之后，应从 Power BI Desktop 或“获取数据”  启动报表。 在网关中创建数据源之后，可能会花费几分钟时间连接才可用。

### <a name="use-the-data-source-with-scheduled-refresh"></a>通过计划刷新使用数据源

如果你被列于网关内配置的数据源的“用户”选项卡中，并且服务器名称和数据库名称匹配，则你可以看到网关显示为计划刷新的一个选项  。

![显示用户](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>后续步骤

* [本地数据网关疑难解答](/data-integration/gateway/service-gateway-tshoot)
* [对网关进行排除故障 - Power BI](service-gateway-onprem-tshoot.md) 

更多问题？ 请尝试在 [Power BI 社区](http://community.powerbi.com/)中提问


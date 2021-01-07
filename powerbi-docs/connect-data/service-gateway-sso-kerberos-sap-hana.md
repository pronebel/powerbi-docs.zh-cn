---
title: 使用 Kerberos 启用到 SAP HANA 的单一登录 (SSO)
description: 将 SAP HANA 服务器配置为从 Power BI 服务启用 SSO
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 3f50b174e8293d75a0077e1799cb64ff4fdcd696
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675111"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>使用 Kerberos 启用到 SAP HANA 的单一登录 (SSO)

> [!IMPORTANT]
> [SAP 不再支持 OpenSSL](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.05/en-US/de15ffb1bb5710148386ffdfd857482a.html)，因此，Microsoft 也停止了对它的支持。 现有连接将继续有效，但从 2021 年 2 月起，你将无法创建新连接。 今后，请改用 CommonCryptoLib。

本文介绍如何将 SAP HANA 数据源配置为从 Power BI 服务启用 SSO。

> [!NOTE]
> 在尝试刷新使用 Kerberos SSO 的基于 SAP HANA 的报表之前，请完成本文中的步骤以及[配置 Kerberos SSO](service-gateway-sso-kerberos.md) 的步骤。

## <a name="enable-sso-for-sap-hana"></a>为 SAP HANA 启用 SSO

要为 SAP HANA 启用 SSO，请按照以下步骤操作：

1. 确保当前运行的 SAP HANA 服务器具备所需的最低版本（版本取决于 SAP HANA 服务器平台级别）：
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. 在网关计算机上，安装最新的 SAP HANA ODBC 驱动程序。 最低版本为 2017 年 8 月发布的 HANA ODBC 版本 2.00.020.00。

3. 确保为 SAP HANA 服务器配置了基于 Kerberos 的 SSO。 有关使用 Kerberos 为 SAP HANA 设置 SSO 的详细信息，请参阅“SAP HANA 安全指南”中的[使用 Kerberos 进行单一登录](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html)。 另请参阅该页面的链接，特别是 SAP 注释 1837331 - HOWTO HANA DBSSO Kerberos/Active Directory。

还建议执行以下附加步骤，这些步骤可以小幅度提升性能：

1. 在网关安装目录中找到并打开此配置文件：Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config。

2. 找到 `FullDomainResolutionEnabled` 属性，并将其值更改为 `True`。

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

现在，[运行 Power BI 报表](service-gateway-sso-kerberos.md#run-a-power-bi-report)。

## <a name="next-steps"></a>后续步骤

有关本地数据网关和 DirectQuery 的详细信息，请参阅以下资源：

* [本地数据网关是什么？](/data-integration/gateway/service-gateway-onprem)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支持的数据源](power-bi-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)

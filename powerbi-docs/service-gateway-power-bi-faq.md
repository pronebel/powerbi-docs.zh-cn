---
title: 本地数据网关常见问题解答 - Power BI
description: 本文是 Power BI 的本地数据网关常见问题解答。 本文将常见问题收集到一处，供 Power BI 中所用网关使用。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: cd3afd0ed3ba1f5b734aab2106cbd70f65f29006
ms.sourcegitcommit: cc4b18d55b2dca8fdb1bef00f53a0a808c41432a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68867052"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>本地数据网关常见问题解答 - Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**问：** 是否需要升级本地数据网关（个人模式）？

**答：** 不需要，你可以继续使用 Power BI 网关（个人模式）。

**问：** 在 Power BI 服务中安装网关并对其进行管理是否需要任何特殊权限？

**答：** 无需特殊权限。

**问：** 是否可以使用连接到本地数据源的 Power Pivot 数据模型上传 Excel 工作簿？ 此方案是否需要网关？ 

**答：** 是的，可以上传工作簿。 依然不，你不需要网关。 但是，由于数据将驻留在 Excel 数据模型中，基于 Excel 工作簿的 Power BI 中的报表将不是实时的。 为了刷新 Power BI 中的报表，你必须重新上传每次更新的工作簿。 或者，使用带有计划刷新的网关。

**问：** 如果用户共享具有 DirectQuery 连接的仪表板，则其他用户即使可能没有相同的权限，是否也能够看到数据？ 

**答：** 对于已连接到 Azure Analysis Services 的仪表板，用户将只能看到他们有权访问的数据。 如果用户不具有相同的权限，他们将无法查看任何数据。 对于其他数据源，所有用户都将都共享管理员为该数据源输入的凭据。

**问：** 我为什么不能连接到 Oracle 服务器？ 

**答：** 你可能需要使用正确的服务器信息来安装 Oracle 客户端并配置 tnsnames.ora 文件，以便连接至 Oracle 服务器。 这是网关外的单独安装。 有关详细信息，请参阅[安装 Oracle 客户端](service-gateway-onprem-manage-oracle.md#install-the-oracle-client)。

**问：** 网关将使用 Azure ExpressRoute？ 

**答：** 是。 有关 ExpressRoute 和 Power BI 的详细信息，请参阅 [Power BI 和 ExpressRoute](service-admin-power-bi-expressroute.md)。

**问：** 我使用的是 R 脚本。 它受支持吗？

**回答**：个人模式仅支持 R 脚本。

## <a name="analysis-services-in-power-bi"></a>Power BI 中的 Analysis Services

**问：** 我可以使用 msdmpump.dll 为 Analysis Services 创建自定义的有效用户名映射吗？ 

**答：** 否。 此时不支持此用法。

**问：** 我是否可以使用网关连接到多维 (OLAP) 实例？ 

**答：** 是。 本地数据网关支持实时连接 Analysis Services 表格模型和多维模型。

**问：** 如果将网关从使用 Windows 身份验证的本地服务器安装在其他域中的计算机上，会怎么样？ 

**答：** 不能保证成功。 这完全取决于两个域之间的信任关系。 如果两个不同的域在受信任的域模型中，则网关可能会连接到 Analysis Services 服务器，且有效的用户名可以得到解析。 如果没有，你可能会遇到登录失败。

**问：** 如何弄清哪些有效用户名被传递给我的本地 Analysis Services 服务器？ 

**答：** 我们在[故障排除文章](service-gateway-onprem-tshoot.md)中回答了这个问题。

## <a name="next-steps"></a>后续步骤

* [本地数据网关疑难解答](/data-integration/gateway/service-gateway-tshoot)

更多问题？ 尝试参与 [Power BI 社区](http://community.powerbi.com/)。


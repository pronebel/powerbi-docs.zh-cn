---
title: 本地数据网关常见问题
description: 此为本地数据网关常见问题。 它会将常见问题收集到网关的一个位置。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b1c74968365db59d51f7c0a7bdb356552cc75596
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54283773"
---
# <a name="on-premises-data-gateway-faq"></a>本地数据网关常见问题
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**问：** 我可以使用 msdmpump.dll 为 Analysis Services 创建自定义的有效用户名映射吗？  
**答：** 否。 这一次不支持此项。

**问：** 我是否可以使用网关连接到多维 (OLAP) 实例。  
**答：** 可以。 本地数据网关支持实时连接 Analysis Services 表格模型和多维模型。

**问：** 如果将网关从使用 Windows 身份验证的本地服务器安装在其他域中的计算机上，会怎么样？  
**答：** 不能保证成功。 这完全取决于两个域之间的信任关系。 如果两个不同的域在受信任的域模型中，则网关可能会连接到 Analysis Services 服务器，且有效的用户名可以得到解析。 如果没有，你可能会遇到登录失败。

**问：** 如何弄清哪些有效用户名被传递给我的本地 Analysis Services 服务器？  
**答：** 我们在[故障排除文章](service-gateway-onprem-tshoot.md)中回答了这个问题。

**问：** 我在 Analysis Services 中有 25 个数据库，有办法可以让它们全部同时为网关启用吗？  
**答：** 否。 这在规划之中，但我们尚无时间范围。

## <a name="administration"></a>管理
**问：** 一个网关可以有多个管理员吗？  
**答：** 可以。 当你管理网关时，可以转到“管理员”选项卡添加其他管理员。

**问：** 网关管理员是否需要是安装网关的计算机的管理员？  
**答：** 否。 网关管理员是用来管理服务中的网关的。

**问：** 是否可以防止我组织中的用户创建网关？  
**答：** 否。 这在规划之中，但我们尚无时间范围。

**问：** 我是否可以获取我组织中网关的使用情况和统计信息？  
**答：** 否。 这在规划之中，但我们尚无时间范围。

## <a name="power-bi"></a>Power BI
**问：** 是否需要升级个人网关？
**答：** 不需要，你可以继续使用 Power BI 个人网关。

**问：** 通过本地数据网关连接时，Power BI 仪表板中的磁帖多久刷新一次？  
**答：** 大约 10 分钟时间。 DirectQuery 连接就是这样。 这并不意味着每十分钟磁贴就可以向本地服务器发布查询并显示新数据。

**问：** 是否可以使用连接到本地数据源的 Power Pivot 数据模型上传 Excel 工作簿？ 此方案是否需要网关？  
**答：** 是的，可以上传工作簿。 依然不，你不需要网关。 但是，由于数据将驻留在 Excel 数据模型中，基于 Excel 工作簿的 Power BI 中的报表将不是实时的。 为了刷新 Power BI 中的报表，你必须重新上传每次更新的工作簿。 或者，使用带有计划刷新的网关。

**问：** 如果用户共享具有 DirectQuery 连接的仪表板，则其他用户即使可能没有相同的权限，是否也能够看到数据？  
**答：** 对于已连接到 Analysis Services 的仪表板，用户将只能看到他们有权访问的数据。 如果用户不具有相同的权限，他们将无法查看任何数据。 对于其他数据源，所有用户都将都共享管理员为该数据源输入的凭据。

**问：** 我为什么不能连接到 Oracle 服务器？  
**答：** 你可能需要使用正确的服务器信息来安装 Oracle 客户端并配置 tnsnames.ora 文件，以便连接至 Oracle 服务器。 这是网关外的单独安装。 有关详细信息，请参阅 [安装 Oracle 客户端](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client)。

**问：** 网关将使用 ExpressRoute？  
**答：** 是。 有关 ExpressRoute 和 Power BI 的详细信息，请参阅 [Power BI 和 ExpressRoute](service-admin-power-bi-expressroute.md)。

**问：** 我使用的是 R 脚本。 它受支持吗？
**回答**：个人模式仅支持 R 脚本。

## <a name="next-steps"></a>后续步骤
[本地数据网关](service-gateway-onprem.md)  
[深入了解本地数据网关](service-gateway-onprem-indepth.md)  
[本地数据网关故障排除](service-gateway-onprem-tshoot.md)  
更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


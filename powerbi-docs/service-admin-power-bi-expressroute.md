---
title: Power BI 和 ExpressRoute
description: Power BI 和 ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0c4618150094a4eabb0dc9745e9ac93e4f342ff1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187861"
---
# <a name="power-bi-and-expressroute"></a>Power BI 和 ExpressRoute

**ExpressRoute** 是一种 Azure 服务，使你可以在 Azure 数据中心（Power BI 所在的位置）与本地基础结构之间创建专用连接，或是在 Azure 数据中心与主机托管环境之间创建专用连接。

借助 **Power BI** 和 **ExpressRoute**，可以创建从组织到 Power BI 的专用网络连接（或使用 ISP 的主机托管设施），从而绕过 Internet 以更好地保护敏感 Power BI 数据和连接。

有关详细信息，请参阅[ExpressRoute 概述](/azure/expressroute/expressroute-introduction)。 Power BI 符合 ExpressRoute 标准，但是在某些例外情况下 Power BI 会通过公共 Internet 获取或发送数据。 有关 Power BI 使用的 URL 列表，请参阅 [Power BI URL](power-bi-whitelist-urls.md)。

![ExpressRoute 关系图](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)
---
title: Azure SQL 数据库计划刷新中的故障排除
description: Power BI 的 Azure SQL 数据库计划刷新中的故障排除
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6d71a1202ba996b70c7477a33ccab936bebbfc5e
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542798"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Power BI 的 Azure SQL 数据库计划刷新中的故障排除

有关刷新的详细信息，请参阅[刷新 Power BI 中的数据](refresh-data.md)和[配置计划刷新](refresh-scheduled-refresh.md)。

设置 Azure SQL 数据库的计划刷新时，若在编辑凭据时收到含错误代码 400 的错误消息，尝试按照以下步骤设置正确的防火墙规则：

1. 登录 [Azure 门户](https://portal.azure.com)。

1. 请参阅要为其配置刷新的 Azure SQL 数据库。

1. 在“概述”边栏选项卡的顶部，选择“设置服务器防火墙”   。

1. 在“防火墙设置”边栏选项卡上，请确保“允许访问 Azure 服务”设置为“开启”    。

    ![Azure 允许的服务](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)

---
title: Azure SQL 数据库计划刷新中的故障排除
description: Power BI 的 Azure SQL 数据库计划刷新中的故障排除
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 292f80b4fec7da9ff6ce42e3611bf4d6353bae2d
ms.sourcegitcommit: 90bd747b7c460d17b74cd386d3f5714234b1f6c9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74791953"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Power BI 的 Azure SQL 数据库计划刷新中的故障排除

有关刷新的详细信息，请参阅[刷新 Power BI 中的数据](refresh-data.md)和[配置计划刷新](refresh-scheduled-refresh.md)。

设置 Azure SQL 数据库的计划刷新时，若在编辑凭据时收到含错误代码 400 的错误消息，尝试按照以下步骤设置正确的防火墙规则：

1. 登录 [Azure 门户](https://portal.azure.com)。

1. 请参阅要为其配置刷新的 Azure SQL 数据库。

1. 在“概述”边栏选项卡的顶部，选择“设置服务器防火墙”   。

1. 在“防火墙设置”边栏选项卡上，请确保“允许访问 Azure 服务”设置为“开启”    。

    ![Azure 允许的服务](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

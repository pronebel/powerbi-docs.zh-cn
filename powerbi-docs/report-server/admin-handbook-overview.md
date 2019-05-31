---
title: 管理员概述：Power BI 报表服务器
description: 本文是 Power BI 报表服务器管理概述，该服务器是用于存储和管理 Power BI、移动报表和分页报表的本地位置。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: maggies
ms.openlocfilehash: c670c78b03a1cd3fd6ce1ad3aeaa0003ce794eec
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187389"
---
# <a name="admin-overview-power-bi-report-server"></a>管理员概述：Power BI 报表服务器
本文是 Power BI 报表服务器管理概述，该服务器是用于存储和管理 Power BI、移动报表和分页报表的本地位置。 本文介绍规划、部署和管理 Power BI 报表服务器的概念，以及指向详细信息的链接。

![](media/admin-handbook-overview/admin-handbook.png)

## <a name="installing-and-migration"></a>安装和迁移
必须安装 Power BI 报表服务器，才能开始使用它。 我们发布了数篇介绍如何处理此任务的文章。

在开始安装、升级或迁移到 Power BI 报表服务器之前，请先查看报表服务器的[系统要求](system-requirements.md)。

### <a name="installing"></a>安装
若要部署新的 Power BI 报表服务器，请参阅以下对你有所帮助的文档。 

[安装 Power BI 报表服务器](install-report-server.md)

### <a name="migration"></a>迁移
无法就地升级 SQL Server Reporting Services。 如果要让现有 SQL Server Reporting Services 实例成为 Power BI 报表服务器，必须进行迁移。 可能还有其他原因需要执行迁移。 请查看迁移文档，了解更多详细信息。

[迁移报表服务器安装](migrate-report-server.md)

## <a name="configuring-your-report-server"></a>配置报表服务器
报表服务器的配置选项有很多。 要使用 SSL 吗？ 要配置电子邮件服务器吗？ 是否想要与 Power BI 服务集成以固定可视化效果？

可以在报表服务器配置管理器中指定大部分配置。 有关更多详细信息，请查看[配置管理器](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode)文档。

## <a name="security"></a>安全性
安全和保护措施对每个组织都非常重要。 可以查看[安全](https://docs.microsoft.com/sql/reporting-services/security/reporting-services-security-and-protection)文档，了解身份验证、授权、角色和权限。

## <a name="next-steps"></a>后续步骤
[安装 Power BI 报表服务器](install-report-server.md)  
[查找报表服务器产品密钥](find-product-key.md)  
[安装更适合 Power BI 报表服务器的 Power BI Desktop](install-powerbi-desktop.md)  
[下载报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下载 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


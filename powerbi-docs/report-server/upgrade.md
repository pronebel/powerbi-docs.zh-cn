---
title: 升级 Power BI 报表服务器
description: 了解如何升级 Power BI 报表服务器。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.custom: ''
ms.date: 09/05/2017
ms.openlocfilehash: 52863ea4bd666547a9c63b3add1d2d9c0626adc7
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839704"
---
# <a name="upgrade-power-bi-report-server"></a>升级 Power BI 报表服务器

了解如何升级 Power BI 报表服务器。

 下载  ![下载](media/upgrade/download.png "下载")

若要下载 Power BI 报表服务器和针对 Power BI 报表服务器进行了优化的 Power BI Desktop，请转到[使用 Power BI 报表服务器进行本地报告](https://powerbi.microsoft.com/report-server/)。

## <a name="before-you-begin"></a>开始之前

在升级报表服务器之前，建议执行以下步骤来备份报表服务器。

### <a name="backing-up-the-encryption-keys"></a>备份加密密钥

首次配置报表服务器安装时，应备份加密密钥。 还应在每次更改服务帐户标识或重命名计算机时备份密钥。 有关详细信息，请参阅[备份和还原 Reporting Services 加密密钥](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys)。

### <a name="backing-up-the-report-server-databases"></a>备份报表服务器数据库

由于报表服务器是无状态服务器，因此所有应用程序数据都存储在 SQL Server 数据库引擎实例上运行的 reportserver 和 reportservertempdb 数据库中。   可以使用支持的 SQL Server 数据库备份方法之一备份 **reportserver** 和 **reportservertempdb** 数据库。 特定于报表服务器数据库的建议如下所示：

* 使用完整恢复模式备份 **reportserver** 数据库。
* 使用简单恢复模式备份 **reportservertempdb** 数据库。
* 可以对每个数据库使用不同的备份计划。 备份 **reportservertempdb** 的唯一原因是为了避免在出现硬件故障时需要重新创建它。 如果发生硬件故障，无需恢复 reportservertempdb 中的数据，但需要表结构。  如果丢失 reportservertempdb，重新获得它的唯一方法是重新创建报表服务器数据库。  如果重新创建 reportservertempdb，请务必使其名称与主报表服务器数据库名称相同。 

有关 SQL Server 关系数据库的备份和恢复的详细信息，请参阅 [SQL Server 数据库的备份和恢复](https://docs.microsoft.com/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)。

### <a name="backing-up-the-configuration-files"></a>备份配置文件

Power BI 报表服务器使用配置文件来存储应用程序设置。 首次配置服务器以及部署任何自定义扩展后，应备份这些文件。 要备份的文件包括：

* config.json
* RSHostingService.exe.config
* Rsreportserver.config
* Rssvrpolicy.config
* Reportingservicesservice.exe.config
* 用于报表服务器 ASP.NET 应用程序的 Web.config
* 用于 ASP.NET 的 Machine.config

## <a name="upgrade-the-report-server"></a>升级报表服务器

升级 Power BI 报表服务器非常简单。 只需执行几个步骤，即可安装文件。

1. 查找 PowerBIReportServer.exe，然后启动安装程序。

2. 选择“升级 Power BI 报表服务器”  。

    ![升级 Power BI 报表服务器](media/upgrade/reportserver-upgrade1.png "升级 Power BI 报表服务器")

3. 阅读并同意许可条款和条件，然后选择“升级”  。

    ![许可协议](media/upgrade/reportserver-upgrade-eula.png "许可协议")

4. 成功升级后，可选择“配置报表服务器”  以启动 Reporting Services 配置管理器，或选择“关闭”  以退出安装程序。

    ![升级配置](media/upgrade/reportserver-upgrade-configure.png)

## <a name="upgrade-power-bi-desktop"></a>升级 Power BI Desktop

升级报表服务器后，需要确保所有 Power BI 报表作者升级到与此服务器匹配的针对 Power BI 报表服务器进行了优化的 Power BI Desktop 版本。

## <a name="next-steps"></a>后续步骤

* [管理员概述](admin-handbook-overview.md)  
* [安装更适合 Power BI 报表服务器的 Power BI Desktop](install-powerbi-desktop.md)  
* [验证 Reporting Services 安装](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
* [配置报表服务器服务帐户](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
* [配置报表服务器 URL](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
* [配置报表服务器数据库连接](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
* [初始化报表服务器](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
* [在报表服务器上配置 SSL 连接](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
* [配置 Windows 服务帐户和权限](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
* [Power BI 报表服务器的浏览器支持](browser-support.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
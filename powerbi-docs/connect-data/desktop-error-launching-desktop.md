---
title: 解决启动 Power BI Desktop 时出现的问题
description: 解决启动 Power BI Desktop 时出现的问题
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 11/14/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: c41f8f9b23ef57d5dd6fd4b851918b7ffa5904a0
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226930"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>打开 Power BI Desktop 的疑难解答

本文介绍无法打开 Power BI 的多种情况并提供补救措施。 

## <a name="resolve-issues-with-opening-encrypted-pbix-files"></a>解决打开加密 PBIX 文件的问题

无法使用不支持信息保护的 Power BI Desktop 版本打开加密的 PBIX 文件。

如果需要继续使用 Power BI Desktop，建议的解决方法是将其更新为支持信息保护的版本。 可以下载 [Power BI Desktop 的最新版本](https://www.microsoft.com/download/confirmation.aspx?id=58494)（此链接是指向安装可执行文件的直接下载链接）。 最新版本的 Power BI Desktop 支持信息保护，并且可以解密并打开任何加密的 PBIX 文件。

###

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>解决本地数据网关和 Power BI Desktop 存在的问题

在 Power BI Desktop 中，已安装且正在运行旧版 Power BI 本地数据网关的用户可能无法打开 Power BI Desktop，因为 Power BI 本地网关对本地计算机的命名管道施加了管理策略限制。

可通过三种方法，解决与本地数据网关相关的问题，并允许打开 Power BI Desktop：

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>解决方案 1：安装最新版 Power BI 本地数据网关

最新版 Power BI 本地数据网关不会对本地计算机施加命名管道限制，这样 Power BI Desktop 就可以正常打开了。 如需继续使用 Power BI 本地数据网关，建议对其进行更新。 可以下载[最新版 Power BI 本地数据网关](https://go.microsoft.com/fwlink/?LinkId=698863)。 此链接是指向安装可执行文件的直接下载链接。

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>解决方案 2：卸载或停止运行 Power BI 本地数据网关 Microsoft 服务

如果不再需要运行 Power BI 本地数据网关，可以将其卸载。 或者，可以停止运行 Power BI 本地数据网关 Microsoft 服务，这将删除策略限制，这样 Power BI Desktop 就可以打开了。

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>解决方案 3：使用管理员特权运行 Power BI Desktop

可以改为以管理员身份成功启动 Power BI Desktop，这也会使其成功打开。 仍建议安装最新版 Power BI 本地数据网关，如前文中所述。

Power BI Desktop 是作为多进程体系结构设计的，其中一些进程使用 Windows 命名管道进行通信。 可能会有其他进程干扰这些命名管道。 此类干扰最常见原因是安全性，包括防病毒软件或防火墙可能会阻止管道或将流量重定向到特定端口的情况。 使用管理员权限打开 Power BI Desktop 可以解决该问题。 如果无法使用管理员权限打开，请让管理员确定哪些安全规则阻止命名管道正确通信。 然后，将 Power BI Desktop 及其各自的子进程添加到允许列表。

## <a name="resolve-issues-when-connecting-to-sql-server"></a>解决连接到 SQL Server 时发生的问题

尝试连接到 SQL Server 数据库时，可能会收到类似于以下文本的错误消息：

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

如果首先以管理员身份打开 Power BI Desktop，然后再建立 SQL Server 连接，通常可以解决此问题。

以管理员身份打开 Power BI Desktop 并建立连接后，所需的 DLL 会正确注册。 此后，不再需要以管理员身份打开 Power BI Desktop。 如果使用备用 Windows 凭据连接到 SQL Server，则每次连接时都必须以管理员身份打开 Power BI Desktop。

## <a name="get-help-with-other-launch-issues"></a>获取有关其他启动问题的帮助

我们会尽可能地收录 Power BI Desktop 出现的问题。 我们会定期查看可能会对大量客户造成影响的问题，并将其收录到我们的文章中。

如果无法打开 Power BI Desktop 不是由于本地数据网关所致，或先前的解决方案不起作用，可以向 Power BI 支持 (<https://support.powerbi.com>) 提交支持事件，这样有助于我们发现并解决用户遇到的问题。

如果将来在使用 Power BI Desktop 时遇到其他问题，启用跟踪和收集日志文件会很有帮助。 日志文件可能有助于隔离和识别问题。 若要启用跟踪，请选择“文件” > “选项和设置” > “选项”，选择“诊断”，然后选择“启用跟踪”  , 。 必须运行 Power BI Desktop 才能设置此选项，但这有助于在以后解决打开 Power BI Desktop 时遇到的问题。

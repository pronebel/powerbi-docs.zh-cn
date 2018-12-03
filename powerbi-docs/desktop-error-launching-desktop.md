---
title: 解决启动 Power BI Desktop 时的问题
description: 解决启动 Power BI Desktop 时的问题
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 78cfcd51a951095353ce5d0f25c4511cc720c632
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578212"
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>解决 Power BI Desktop 不启动时的问题
在 Power BI Desktop 中，已安装且正在运行旧版 Power BI 本地数据网关的用户可能无法启动 Power BI Desktop，因为 Power BI 本地网关对本地计算机的命名管道施加了管理策略限制。 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>解决本地数据网关和 Power BI Desktop 存在的问题
可通过三种方法，解决与本地数据网关相关的问题，并允许启动 Power BI Desktop：

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>解决方案 1：安装最新版 Power BI 本地数据网关
最新版 Power BI 本地数据网关不会对本地计算机施加命名管道限制，这样 Power BI Desktop 就可以正常启动了。 如需继续使用 Power BI 本地数据网关，建议采用此解决方案。 可以从[此位置](https://go.microsoft.com/fwlink/?LinkId=698863)下载最新版 Power BI 本地数据网关。 请注意，此链接是指向安装可执行文件的直接下载链接。

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>解决方案 2：卸载或停止运行 Power BI 本地数据网关 Windows 服务
如果不再需要使用 Power BI 本地数据网关，可以卸载或停止运行 Power BI 本地数据网关 Windows 服务。这样一来，便会撤消策略限制，并允许启动 Power BI Desktop。

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>解决方案 3：使用管理员特权运行 Run Power BI Desktop
或者，可以管理员身份启动 Power BI Desktop，这也会使其成功启动。 仍建议安装最新版 Power BI 本地数据网关，如本文先前部分中所述。

值得注意的是，Power BI Desktop 是作为多进程体系结构设计的，其中一些进程使用 Windows 命名管道进行通信。 可能会有其他进程干扰这些命名管道。 此类干扰最常见原因是安全性，包括防病毒软件或防火墙可能会阻止管道或将流量重定向到特定端口的情况。 使用管理员权限启动 Power BI Desktop 可以解决该问题。 如果无法使用管理员权限启动，请与管理员联系，确定应用了哪些阻止命名管道正确通信的安全规则，并将 Power BI Desktop 及其各自的子进程列入白名单。

## <a name="resolve-issues-when-connecting-to-sql-server"></a>解决连接到 SQL Server 时发生的问题
如果连接 SQL Server 数据库时遇到类似以下错误消息，通常可以管理员身份启动 Power BI Desktop，然后连接 SQL Server，以解决此问题：

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

以管理员身份启动并建立连接后，可正确注册所需 DLL。 此后，无需以管理员身份启动 Power BI Desktop。

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>帮助解决在启动 Power BI Desktop 时遇到的其他问题
我们会尽可能地收录 Power BI Desktop 出现的问题。 我们会定期查看可能会对大量客户造成影响的问题，并将其收录到我们的文章中。

如果无法启动 Power BI Desktop 不是由于本地数据网关所致，或先前的解决方案不起作用，可以向 [Power BI 支持](https://support.powerbi.com) (https://support.powerbi.com)) 提交支持事件，这样有助于我们发现并解决用户遇到的问题。

如果今后在使用 Power BI Desktop 时遇到其他问题（我们希望不会出现问题或出现的问题很少），启用跟踪和收集日志文件将有助于更好地隔离和发现问题。 若要启用跟踪，请依次选择“文件”、“选项和设置”、“选项”和“诊断”，再选中“诊断选项”下的“启用跟踪”。 我们认识到，必须运行 Power BI Desktop，才能设置此选项，这更有助于解决今后发生的与启动 Power BI Desktop 相关的问题。


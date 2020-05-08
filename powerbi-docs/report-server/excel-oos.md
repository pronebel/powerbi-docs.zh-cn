---
title: 使用 Office Online Server (OOS) 托管 Excel 工作簿 - Power BI 报表服务器
description: 除了在 Web 门户中查看 Power BI 报表之外，Power BI 报表服务器也可以使用 Office Online Server (OOS) 来托管 Excel 工作簿。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 08/21/2018
ms.openlocfilehash: 907e65635424b709ec2c0850e4d0d759f4ba6dd3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874084"
---
# <a name="configure-your-report-server-to-host-excel-workbooks-using-office-online-server-oos"></a>使用 Office Online Server (OOS) 将报表服务器配置为托管 Excel 工作簿

除了在 Web 门户中查看 Power BI 报表之外，Power BI 报表服务器也可以使用 [Office Online Server](https://docs.microsoft.com/officeonlineserver/office-online-server-overview) (OOS) 来托管 Excel 工作簿。 报表服务器将成为用于发布和查看自助服务 Microsoft BI 内容的单个位置。

![从报表服务器 Web 门户查看的 Excel 报表。](media/excel-oos/excel-in-pbirs.png)

## <a name="prepare-server-to-run-office-online-server"></a>准备要运行 Office Online Server 的服务器

在运行 Office Online Server 的服务器上执行下列过程。 此服务器必须是 Windows Server 2012 R2 或 Windows Server 2016。 Windows Server 2016 需要 Office Online Server 的 2017 年 4 月发行的版本或更高版本。

### <a name="install-prerequisite-software-for-office-online-server"></a>为 Office Online Server 安装必备软件

1. 以管理员身份打开 Windows PowerShell 提示符，并运行以下命令以安装所需的角色和服务。

    **Windows Server 2012 R2：**

    ```powershell
    Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation
    ```

    **Windows Server 2016：**

    ```powershell
    Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,NET-Framework-Features,NET-Framework-45-Features,NET-Framework-Core,NET-Framework-45-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation
    ```

    如果出现提示，请重启服务器。
2. 安装以下软件：

   * [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=510096)
   * [Visual C++ Redistributable Packages for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784)
   * [Visual C++ Redistributable for Visual Studio 2015](https://go.microsoft.com/fwlink/p/?LinkId=620071)
   * [Microsoft.IdentityModel.Extention.dll](https://go.microsoft.com/fwlink/p/?LinkId=620072)

### <a name="install-office-online-server"></a>安装 Office Online Server

如果你打算使用任何利用外部数据访问（例如 Power Pivot）的 Excel Online 功能，请注意，Office Online Server 必须与其用户以及你打算使用基于 Windows 的身份验证访问的任何外部数据源位于同一个 Active Directory 林中。

1. 从[批量许可服务中心 (VLSC)](https://go.microsoft.com/fwlink/p/?LinkId=256561) 下载 Office Online Server。 下载位置在 VLSC 门户上的 Office 产品下方。 出于开发目的，可以从 MSDN 订阅者下载页面下载 OOS。
2. 运行 Setup.exe。
3. 在“阅读 Microsoft 软件许可条款”  页上，选择“我接受此协议的条款”  ，然后选择“继续”  。
4. 在“选择文件位置”  页上，选择想要安装 Office Online Server 文件的文件夹（例如，C:\Program Files\Microsoft Office Web Apps\*），然后选择“立即安装”  。 如果你指定的文件夹不存在，安装程序将为你创建一个。

    建议将 Office Online Server 安装在系统驱动器上。

5. 当安装程序完成 Office Online Server 安装时，选择“关闭”  。

### <a name="install-language-packs-for-office-web-apps-server-optional"></a>为 Office Web Apps 服务器安装语言包（可选）

Office Online Server 语言包可让用户以多种语言查看基于 Web 的 Office 文件。

若要安装语言包，请按照下列步骤操作。

1. 从 [Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=798136)下载 Office Online Server 语言包。
2. 运行 wacserverlanguagepack.exe  。
3. 在 Office Online Server 语言包向导中的“阅读 Microsoft 软件许可条款”  页上，选择“我接受此协议的条款”  ，然后选择“继续”  。
4. 当安装程序完成 Office Online Server 安装时，选择“关闭”  。

## <a name="deploy-office-online-server"></a>部署 Office Online Server

### <a name="create-the-office-online-server-farm-https"></a>创建 Office Online Server 场 (HTTPS)

使用 New-OfficeWebAppsFarm 命令创建包含单个服务器的新 Office Online Server 场，如以下示例所示。

```powershell
New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate"
```

**参数**

*  –InternalURL 是运行 Office Online Server 的服务器的完全限定的域名 (FQDN)，如 `https://servername.contoso.com`。
*  –ExternalURL 是在 Internet 上可访问的 FQDN。
*  –CertificateName 是证书的友好名称。

### <a name="create-the-office-online-server-farm-http"></a>创建 Office Online Server 场 (HTTP)

使用 New-OfficeWebAppsFarm 命令创建包含单个服务器的新 Office Online Server 场，如以下示例所示。

```powershell
New-OfficeWebAppsFarm -InternalURL "https://servername" -AllowHttp
```

**参数**

*  –InternalURL 是运行 Office Online Server 的服务器的名称，如 `https://servername`。
*  –AllowHttp 将场配置为使用 HTTP。

### <a name="verify-that-the-office-online-server-farm-was-created-successfully"></a>验证 Office Online Server 场是否已成功创建

创建场后，有关场的详细信息将显示在 Windows PowerShell 提示符下。 要验证 Office Online Server 是否已正确安装和配置，请使用 Web 浏览器访问 Office Online Server 发现 URL，如以下示例所示。 发现 URL 是配置 Office Online Server 场时指定的 InternalUrl  参数，后跟 /hosting/discovery  ，例如：

```
<InternalUrl>/hosting/discovery
```

如果 Office Online Server 按预期方式工作，则应在 Web 浏览器中看到 Web 应用程序开放平台接口协议 (WOPI) 发现 XML 文件。 该文件的前几行应类似于以下示例：

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<wopi-discovery>
<net-zone name="internal-http">
<app name="Excel" favIconUrl="<InternalUrl>/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
<action name="view" ext="ods" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xls" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xlsb" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xlsm" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
```

### <a name="configure-excel-workbook-maximum-size"></a>配置 Excel 工作簿最大大小

Power BI 报表服务器中所有文件的最大文件大小为 100 MB。 若要保持与该大小同步，需要在 OOS 中手动对此进行设置。

```powershell
Set-OfficeWebAppsFarm -ExcelWorkbookSizeMax 100
```

## <a name="using-effectiveusername-with-analysis-services"></a>结合使用 EffectiveUserName 与 Analysis Services

实现实时连接到 Analysis Services 以及利用 EffectiveUserName 的 Excel 工作簿中的连接。 为了使 OOS 能够利用 EffectiveUserName，需要将 OOS 服务器的计算机帐户添加为 Analysis Services 实例的管理员。 为此，需要 Management Studio for SQL Server 2016 或更高版本。

在 Excel 工作簿内当前仅支持嵌入的 Analysis Services 连接。 用户的帐户需要具有连接到 Analysis Services 的权限，因为代理用户的功能不可用。

在 OOS 服务器上运行以下 PowerShell 命令。

```powershell
Set-OfficeWebAppsFarm -ExcelUseEffectiveUserName:$true
Set-OfficeWebAppsFarm -ExcelAllowExternalData:$true
Set-OfficeWebAppsFarm -ExcelWarnOnDataRefresh:$false
```

## <a name="configure-a-power-pivot-instance-for-data-models"></a>配置数据模型的 Power Pivot 实例

安装 Analysis Services Power Pivot 模式实例可让你使用正在使用 Power Pivot 的 Excel 工作簿。 请确保实例名称是 POWERPIVOT  。 将 OOS 服务器的计算机帐户添加为 Analysis Services Power Pivot 模式实例的管理员。 为此，需要 Management Studio for SQL Server 2016 或更高版本。

为了使 OOS 使用 Power Pivot 模式实例，请运行以下命令。

```powershell
New-OfficeWebAppsExcelBIServer -ServerId <server_name>\POWERPIVOT
```

如果你未允许来自上述 Analysis Services 步骤的外部数据，请运行以下命令。

```powershell
Set-OfficeWebAppsFarm -ExcelAllowExternalData:$true
```

### <a name="firewall-considerations"></a>防火墙注意事项

若要避免防火墙问题，可能需要打开端口 2382 和 2383。 还可以为 Power Pivot 实例添加 msmdsrv.exe  作为应用程序防火墙策略。

## <a name="configure-power-bi-report-server-to-use-the-oos-server"></a>将 Power BI 报表服务器配置为使用 OOS 服务器

在“站点设置”的“常规”  页  上，输入 OOS 发现 URL。 OOS 发现 URL 是 InternalUrl  ，在部署 OOS 服务器时使用，后跟 /hosting/discovery  。 例如，`https://servername/hosting/discovery`（用于 HTTP）。 而 `https://server.contoso.com/hosting/discovery`（用于 HTTPS）。

若要转到“站点设置”  ，请选择右上角的齿轮图标，然后选择“站点设置”   。

只有具有“系统管理员”角色的用户才可看到 Office Online Server 发现 URL 设置  。

![Power BI 报表服务器的站点设置。](media/excel-oos/reportserver-site-settings.png)

输入发现 URL 并选择“应用”  ，在 Web 门户中选择 Excel 工作簿时，应在 Web 门户中显示该工作簿。

## <a name="limitations-and-considerations"></a>限制和注意事项

* 但对工作簿仅具有只读权限。

## <a name="next-steps"></a>后续步骤

[管理员概述](admin-handbook-overview.md)  
[安装 Power BI 报表服务器](install-report-server.md)  
[下载报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下载 SQL Server Data Tools (SSDT)](https://go.microsoft.com/fwlink/?LinkID=616714)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

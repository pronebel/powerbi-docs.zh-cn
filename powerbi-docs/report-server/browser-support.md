---
title: Power BI 报表服务器的浏览器支持
description: 了解支持使用哪些版本的浏览器来管理和查看 Power BI 报表服务器和报表查看器控件。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2021
ms.openlocfilehash: 71ee66c6cd531a35a53a3263feaf94115b528114
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687479"
---
# <a name="browser-support-for-power-bi-report-server"></a>Power BI 报表服务器的浏览器支持
了解支持使用哪些版本的浏览器来管理和查看 Power BI 报表服务器和报表查看器控件。

> [!NOTE]
> Microsoft Edge 旧版浏览器支持将于 2021 年 3 月 9 日停止，Microsoft Internet Explorer 11 支持将于 2021 年 8 月 17 日停止。

## <a name="browser-requirements-for-the-web-portal"></a>Web 门户的浏览器要求
以下是 Web 门户当前支持的浏览器列表。

**Microsoft Windows**  
*Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
安装了 iOS 10 的 iPhone 和 iPad

* Apple Safari (+)

**Google Android**  
*Android 4.4 (KitKat) 或更高版本的手机或平板电脑*

* Google Chrome (+)
  
  **(+)** 最新公开发布的版本

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>报表查看器 Web 控件 (2015) 的浏览器要求
下面列出了报表查看器 Web 控件当前支持的浏览器。 报表查看器支持从 Web 门户查看报表。

**Microsoft Windows**  
*Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)** 最新公开发布的版本

### <a name="authentication-requirements"></a>身份验证要求
浏览器支持必须由报表服务器处理的特定身份验证方案，以使客户端请求获得成功。 下表标识 Windows 操作系统上运行的各浏览器支持的默认身份验证类型。

| **浏览器类型** | **支持** | **浏览器默认值** | **服务器默认值** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |协商、Kerberos、NTLM、基本 |Negotiate |是的。 默认身份验证设置使用 Edge。 |
| **Microsoft Internet Explorer** |协商、Kerberos、NTLM、基本 |Negotiate |是的。 默认身份验证设置使用 Internet Explorer。 |
| **Google Chrome**(+) |协商、NTLM、基本 |Negotiate |是的。 默认身份验证设置使用 Chrome。 |
| **Mozilla Firefox**(+) |NTLM、基本 |NTLM |是的。 默认身份验证设置使用 Firefox。 |
| **Apple Safari**(+) |NTLM、基本 |基本 |是的。 默认身份验证设置使用 Safari。 |

 **(+)** 最新公开发布的版本

### <a name="script-requirements-for-viewing-reports"></a>查看报表的脚本要求
若要使用报表查看器，请将浏览器配置为可以运行脚本。

如果未启用脚本功能，则打开报表时将显示如下错误消息：

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 如果选择查看不支持脚本的报表，则报表将会以 HTML 格式呈现，同时不具有报表工具栏和文档结构图等报表查看器功能。

> [!NOTE]
> 报表工具栏是 HTML 查看器组件的一部分。 默认情况下，该工具栏显示在浏览器窗口中呈现的每个报表的返回页首。 报表查看器提供的功能包括能够在报表中搜索信息、滚动到特定的页以及调整页大小以便查看。 有关报表工具栏或 HTML 查看器的详细信息，请参阅 [HTML Viewer and the Report Toolbar](/sql/reporting-services/html-viewer-and-the-report-toolbar)。
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Visual Studio 中的报表查看器 Web 服务器控件的浏览器支持
报表查看器 Web 服务器控件用于在 ASP.NET Web 应用中嵌入报表功能。 若要详细了解如何获取报表查看器控件，请参阅[使用报表查看器控件集成 Reporting Services - 入门](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)。

使用启用了脚本支持的浏览器。 如果浏览器无法运行脚本，则不能查看报表。

**Microsoft Windows**  
*Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)** 最新公开发布的版本

## <a name="next-steps"></a>后续步骤
[管理员概述](admin-handbook-overview.md)  
[安装 Power BI 报表服务器](install-report-server.md)  
[下载报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下载 SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

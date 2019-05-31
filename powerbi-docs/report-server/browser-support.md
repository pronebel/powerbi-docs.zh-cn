---
title: Power BI 报表服务器的浏览器支持
description: 了解支持使用哪些版本的浏览器来管理和查看 Power BI 报表服务器和报表查看器控件。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
ms.openlocfilehash: 5a2ca653a06efbde161899602536b05c8f6ab666
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769772"
---
# <a name="browser-support-for-power-bi-report-server"></a>Power BI 报表服务器的浏览器支持
了解支持使用哪些版本的浏览器来管理和查看 Power BI 报表服务器和报表查看器控件。

## <a name="browser-requirements-for-the-web-portal"></a>Web 门户的浏览器要求
下面列出了 Web 门户当前支持的浏览器。

Microsoft Windows   
Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2 

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

Apple OS X   
OS X 10.9-10.11 

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

Apple iOS   
安装了 iOS 10 的 iPhone 和 iPad 

* Apple Safari (+)

Google Android   
安装了 Android 4.4 (KitKat) 或更高版本的手机和平板电脑 

* Google Chrome (+)
  
  (+)  表示最新公开发布的版本

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>报表查看器 Web 控件 (2015) 的浏览器要求
下面列出了报表查看器 Web 控件当前支持的浏览器。 报表查看器支持从 Web 门户查看报表。

Microsoft Windows   
Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2 

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

Apple OS X   
OS X 10.9-10.11 

* Apple Safari (+)
  
  (+)  表示最新公开发布的版本

### <a name="authentication-requirements"></a>身份验证要求
浏览器支持特定的身份验证方案，这些方案必须由报表服务器进行处理，这样客户端请求才算成功。 下表明确了 Windows 操作系统上运行的各个浏览器支持的默认身份验证类型。

| 浏览器类型  | 支持  | 浏览器默认值  | 服务器默认值  |
| --- | --- | --- | --- |
| Microsoft Edge  (+) |协商、Kerberos、NTLM、基本 |协商 |是的。 默认身份验证设置适用于 Edge。 |
| Microsoft Internet Explorer  |协商、Kerberos、NTLM、基本 |协商 |是的。 默认身份验证设置适用于 Internet Explorer。 |
| Google Chrome  (+) |协商、NTLM、基本 |协商 |是的。 默认身份验证设置适用于 Chrome。 |
| Mozilla Firefox  (+) |NTLM、基本 |NTLM |是的。 默认身份验证设置适用于 Firefox。 |
| Apple Safari  (+) |NTLM、基本 |基本 |是的。 默认身份验证设置适用于 Safari。 |

 (+)  表示最新公开发布的版本

### <a name="script-requirements-for-viewing-reports"></a>有关查看报表的脚本要求
若要使用报表查看器，请将浏览器配置为运行脚本。

如果未启用脚本，将会在打开报表时看到如下错误消息：

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 如果选择在没有脚本支持的情况下查看报表，报表以 HTML 格式呈现，不含报表工具栏和文档结构图等报表查看器功能。

> [!NOTE]
> 报表工具栏属于 HTML 查看器组件。 默认情况下，此工具栏显示在浏览器窗口中呈现的每个报表的顶部。 报表查看器的功能包括在报表中搜索信息、滚动到特定页、调整页面大小以便查看报表。 有关报表工具栏或 HTML 查看器的详细信息，请参阅 [HTML 查看器和报表工具栏](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar)。
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Visual Studio 中的报表查看器 Web 服务器控件的浏览器支持
报表查看器 Web 服务器控件用于在 ASP.NET Web 应用中嵌入报表功能。 若要详细了解如何获取报表查看器控件，请参阅[使用报表查看器控件集成 Reporting Services - 入门](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)。

请使用已启用脚本支持的浏览器。 如果浏览器无法运行脚本，则无法查看报表。

Microsoft Windows   
Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2 

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  (+)  表示最新公开发布的版本

## <a name="next-steps"></a>后续步骤
[管理员概述](admin-handbook-overview.md)  
[安装 Power BI 报表服务器](install-report-server.md)  
[下载报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下载 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


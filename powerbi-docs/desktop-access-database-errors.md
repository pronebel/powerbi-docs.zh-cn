---
title: 解决 Power BI Desktop 中的 Access 和 .XLS 导入问题
description: 解决在 Power BI Desktop 和 Power Query 中导入 Access 数据库和 .XLS 电子表格出现的问题
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1816fb7926ed378cdb70ce2e0ade08893828ce4c
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761947"
---
# <a name="troubleshoot-importing-access-and-excel-xls-files-in-power-bi-desktop"></a>在 Power BI Desktop 中导入 Access 和 Excel .xls 文件的疑难解答

在 Power BI Desktop 中，Access 数据库和旧版 Excel 工作簿（Excel 97-2003 的 .XLS 文件类型）均使用 Access 数据库引擎  。 有三种常见情形可能会导致 Access 数据库引擎无法正常运行。

## <a name="situation-1-no-access-database-engine-is-installed"></a>情况 1：未安装 Access 数据库引擎

当 Power BI Desktop 错误消息指示未安装 Access 数据库引擎时，必须安装与你的 Power BI Desktop 版本匹配的 Access 数据库引擎版本（32 位或 64 位）。 可以从[下载页](https://www.microsoft.com/download/details.aspx?id=13255)安装 Access 数据库引擎。

>[!NOTE]
>如果安装的 Access 数据库引擎位版本不同于 Microsoft Office 安装的位版本，则 Office 应用程序将不能使用 Access 数据库引擎。

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>情况 2：Access 数据库引擎位版本（32 位或 64 位）不同于用户的 Power BI Desktop 位版本

当安装的 Microsoft Office 版本为 32 位，而安装的 Power BI Desktop 版本为 64 位时，通常会发生这种情况。 也可能发生相反的情况，这两种情况都将发生位版本不匹配。 如果使用的是 Office 365 订阅，请参阅[情况 3](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription)，了解不同的问题和解决方法。 以下任何一种解决方案都可以修复此位版本不一致错误：

### <a name="solution-1"></a>解决方法 1

更改 Power BI Desktop 的版本以匹配 Microsoft Office 安装的位版本。 

1. 若要更改 Power BI Desktop 的位版本，请卸载 Power BI Desktop，然后安装与 Office 安装匹配的 Power BI Desktop 版本。 

1. 若要选择 Power BI Desktop 的版本，请在“Power BI Desktop 下载”页上选择“高级下载选项”  。
   
   ![“Power BI Desktop 下载”页面上的“高级下载”选项](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. 在出现的下载页上选择你的语言，然后选择**下载**按钮。 
 
1. 在出现的屏幕上，选择 PBIDesktop.msi 旁边的复选框以选择 32 位版本，或 PBIDesktop_x64.msi 旁边的复选框以选择 64 位版本。 

   在下面的屏幕截图中，选择了 64 位版本。
   
   ![选择 Power BI Desktop 下载类型](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >如果使用 Power BI Desktop 的 32 位版本，创建非常大的数据模型时，可能会遇到内存不足的问题。

### <a name="solution-2"></a>解决方法 2

更改 Microsoft Office 的版本以匹配 Power BI Desktop 安装的位版本：

1. 卸载 Microsoft Office

2. 安装与 Power BI Desktop 安装匹配的 Office 版本。

### <a name="solution-3"></a>解决方法 3

如果试图打开 .XLS 文件（Excel 97-2003 工作簿）时出错，可以通过在 Excel 中打开 .XLS 文件并将其另存为 XLSX 文件，来避免使用 Access 数据库引擎。

### <a name="solution-4"></a>解决方法 4

如果前三种解决方法都不可行，则可安装 Access 数据库引擎的两个版本。 但这不是建议的解决方法。 尽管安装两个版本将解决 Power Query for Excel 和 Power BI Desktop 的这一问题，但对于自动（默认）使用最先安装的 Access 数据库引擎的位版本的任何应用程序，这将引入错误和问题。 

若要安装 Access 数据库引擎的两个位版本，请执行以下步骤：

1. 在[“下载”页](https://www.microsoft.com/download/details.aspx?id=13255)安装Access 数据库引擎的两个位版本。 

1. 使用 /passive 开关运行 Access 数据库引擎的每个版本  。 例如：
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>情况 3：无法结合使用 Office 365 订阅和 Access 或 .XLS 文件

如果使用的是 Office 365 订阅，无论是 Office 2013 还是 Office 2016，Access 数据库引擎提供程序是在仅供 Microsoft Office 进程访问的虚拟注册表位置中进行注册    。 因此，糅合引擎（负责运行非 Office 365 Excel 和 Power BI Desktop，但不是 Office 进程）不能使用 Access 数据库引擎提供程序。

若要纠正这种情形，请[下载并安装 Access 数据库引擎可再发行组件](https://www.microsoft.com/download/details.aspx?id=13255)，该组件与 Power BI Desktop 安装的位版本匹配。 有关位版本的详细信息，请参阅本文前面的部分。

## <a name="other-situations-that-can-cause-import-issues"></a>可能导致导入问题发生的其他情形

我们会尽可能地收录 Access 或 .XLS 文件出现的问题。 如果遇到本文未收录的问题，请将问题提交给 [Power BI 支持团队](https://powerbi.microsoft.com/support/)。 我们会定期查看可能会对大量客户造成影响的问题，并将其收录到我们的文章中。


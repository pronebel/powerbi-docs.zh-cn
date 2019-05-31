---
title: 错误：我们在你的 Excel 工作簿中找不到任何数据
description: 错误：我们在你的 Excel 工作簿中找不到任何数据
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6fb02e6cbaca30859aa00f58ae07c9a3fd7f6fe0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101471"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>错误：我们在你的 Excel 工作簿中找不到任何数据

>[!NOTE]  
>本文适用于 Excel 2007 及更高版本。

将 Excel 工作簿导入 Power BI 时，你可能会看到以下错误：

*错误:我们找不到格式化为表的任何数据。若要从 Excel 导入 Power BI 服务，需要将数据格式化为表。选择您要在表中，按 Ctrl + T 的所有数据。*

![在工作簿中找不到数据](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

## <a name="quick-solution"></a>快速解决方案
1. 在 Excel 中编辑工作簿。
2. 选择包含你的数据的单元格范围。 第一行应包含列标题（列名）。
3. 按 **Ctrl + T** 可创建表。
4. 保存工作簿。
5. 返回到 Power BI 并再次导入工作簿，如果你在 Excel 2016 中工作并且已将工作簿保存到 OneDrive for Business，请在 Excel 中，单击“文件”>“发布”。

## <a name="details"></a>详细信息
### <a name="cause"></a>原因
在 Excel 中，可以通过某一范围的单元格创建**表**，这样可以更方便地对数据进行排序、筛选和设置格式。

导入 Excel 工作簿时，Power BI 会查找这些表，并将它们导入数据集；如果找不到任何表，则你会看到此错误消息。

### <a name="solution"></a>解决方案
1. 在 Excel 中打开工作簿。 
    >[!NOTE]
    >此处的图片属于 Excel 2013。 如果你在不同版本，则显示内容可能稍有不同，但步骤是相同的。
    
    ![打开工作簿](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. 选择包含你的数据的单元格范围。 第一行应包含列标题（列名）：
   
    ![选择单元格范围](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. 在功能区中**插入**选项卡上，单击**表**。 （或者，作为快捷方式，按 **Ctrl + T**。）
   
    ![插入表](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. 你会看到以下对话框。 请确保**表包含标题**已选中，然后选择**确定**：
   
    ![创建表](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. 现在数据格式化为表：
   
    ![格式化为表格的数据](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. 保存工作簿。
7. 返回到 Power BI。 选择左侧导航窗格底部的“获取数据”。
   
    ![获取数据](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. 在**文件**框中，选择**获取**。
   
    ![获取文件](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. 再次导入 Excel 工作簿。 这次导入应找到表并且成功。
   
    如果导入仍失败，请单击帮助菜单中的**“社区”**来告诉我们：
   
    ![社区链接](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)

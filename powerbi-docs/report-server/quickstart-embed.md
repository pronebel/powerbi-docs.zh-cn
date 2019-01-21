---
title: 使用 iFrame 嵌入报表
description: 在 SharePoint Server 的 iFrame 中嵌入 Power BI 报表服务器报表
author: markingmyname
ms.author: maghan
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: a0224188a0205cf134f2b2ee123bf5a3ac7ef0d0
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54288488"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>快速入门：在 SharePoint Server 中使用 iFrame 嵌入“Power BI 报表服务器”报表

在本快速入门中，你将了解如何通过在 SharePoint 页面中使用 iFrame 嵌入 Power BI 报表服务器报表。 如果正在使用 SharePoint Online，则必须可以公开访问 Power BI 报表服务器。 在 SharePoint Online 中，使用 Power BI 服务的 Power BI Web 部件不会使用 Power BI 报表服务器。 

![iFrame 示例](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>先决条件
* 需要安装和配置 [Power BI 报表服务器](https://powerbi.microsoft.com/en-us/report-server/)。
* 需要安装[更适合 Power BI 报表服务器的 Power BI Desktop](install-powerbi-desktop.md)。
* 需要安装和配置 [SharePoint](https://docs.microsoft.com/sharepoint/install/install) 环境。

## <a name="creating-the-power-bi-report-server-report-url"></a>创建 Power BI 报表服务器报表 URL

1. 从 GitHub 下载示例 - [博客演示](https://github.com/Microsoft/powerbi-desktop-samples)。

    ![下载示例 PBIX 文件](media/quickstart-embed/quickstart_embed_14.png)

2. 在“更适合 Power BI 报表服务器的 Power BI Desktop”中从 GitHub 打开示例 PBIX 文件。

    ![PBI RS 桌面工具](media/quickstart-embed/quickstart_embed_02.png)

3. 将报表保存到 Power BI 报表服务器。 

    ![PBI RS 保存](media/quickstart-embed/quickstart_embed_03.png)

4. 在 Web 门户中查看报表。

    ![Web 门户](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>捕获 URL 参数

有了 URL 后，可以在 SharePoint 页面中创建 iFrame 来托管报表。 对于任何 Power BI 报表服务器报表 URL，可以添加 `?rs:embed=true` 的查询字符串参数，从而将报表嵌入到 iFrame 中。 

   例如：
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>在 SharePoint iFrame 中嵌入 Power BI 报表服务器报表

1. 导航到 SharePoint“网站内容”页面。

    ![网站内容页面](media/quickstart-embed/quickstart_embed_05.png)

2. 选择要添加报表的页面。

    ![网站内容页面应用](media/quickstart-embed/quickstart_embed_06.png)

3. 选择右上方的齿轮，然后选择“编辑页面”。

    ![“编辑页面”选项](media/quickstart-embed/quickstart_embed_07.png)

4. 选择“添加 Web 部件”。

    ![添加 Web 部件](media/quickstart-embed/quickstart_embed_08.png)

5. 在“类别”下选择“媒体和内容”，在“部件”下选择“内容编辑器”，然后选择“添加”。

    ![选择内容编辑器 Web 部件](media/quickstart-embed/quickstart_embed_09.png)![选择添加](media/quickstart-embed/quickstart_embed_091.png)

6. 选择“单击此处以添加新内容”。

    ![添加新内容](media/quickstart-embed/quickstart_embed_10.png)

7. 在功能区中选择“格式文本”选项卡，然后选择“编辑源”。

     ![编辑源](media/quickstart-embed/quickstart_embed_11.png)

8. 在“编辑源”窗口中粘贴 iFrame 代码，然后选择“确定”。

    ![iFrame 代码](media/quickstart-embed/quickstart_embed_12.png)

     例如：
     ```
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. 在功能区中选择“页面”选项卡，然后选择“停止编辑”。

    ![停止编辑](media/quickstart-embed/quickstart_embed_13.png)

10. 现在应该可以看到页面上的报表。

    ![iFrame 示例](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>后续步骤

[快速入门：为 Power BI 报表服务器创建 Power BI 报表](quickstart-create-powerbi-report.md)  
[快速入门：为 Power BI 报表服务器创建分页报表](quickstart-create-paginated-report.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/) 
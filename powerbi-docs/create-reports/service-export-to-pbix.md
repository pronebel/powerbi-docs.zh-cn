---
title: 将报表从 Power BI 服务下载到 Power BI Desktop（预览版）
description: 将报表从 Power BI 服务下载到 Power BI Desktop 文件
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/14/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: cd9295e26de50714a15afb672814893317fb8e3b
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861397"
---
# <a name="download-a-report-from-the-power-bi-service-to-power-bi-desktop-preview"></a>将报表从 Power BI 服务下载到 Power BI Desktop（预览版）
      
在 Power BI Desktop 中，可以将报表（.pbix 文件）从本地计算机发布到 Power BI 服务。 Power BI 报表也可以反向流动：可以将报表从 Power BI 服务下载到 Power BI Desktop。 两种情况下，Power BI 报表的扩展均为 .pbix。

有几个需要注意的限制，本文的[注意事项和疑难解答](#considerations-and-troubleshooting)部分中讨论了这些限制。

![文件下拉列表](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix-file"></a>以 .pbix 文件形式下载报表

仅可下载 2016 年 11 月 23 日及之后更新的 [Power BI Desktop 上所创建](/learn/modules/publish-share-power-bi/2-publish-reports)的报表。 如果是之前创建的，则 Power BI 服务中的“下载报表”菜单选项显示为灰色。

若要下载 .pbix 文件，请执行以下步骤：

1. 在 Power BI 服务的[编辑视图](./service-interact-with-a-report-in-editing-view.md)中，打开要下载的报表。

2. 在顶部导航窗格中，依次选择“文件”>“下载报表”。
   
3. 报表正在下载时，状态横幅将显示进度。 在文件就绪后，系统会询问此 .pbix 文件的保存位置。 默认文件名与报表名相匹配。
   
4. 如果还没有[安装 Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)，请安装它，然后在 Power BI Desktop 中打开该 .pbix 文件。
   
    在 Power BI Desktop 中打开报表时，可能会看到警告消息，告知你在 Power BI 服务报表中提供的某些功能在 Power BI Desktop 中不可用。
   
    ![警告对话框](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. Power BI Desktop 中的报表编辑器和 Power BI 服务中的报表编辑器非常相似。  
   
    ![Power BI Desktop 报表编辑器](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

从 Power BI 服务下载 .pbix 文件有几个相关的重要注意事项和限制。

* 若要下载文件，必须具有编辑报表的权限。
* 报表必须使用 Power BI Desktop 创建，且必须在 Power BI 服务中发布。或者，必须已将 .pbix 文件上传到 Power BI 服务中 。
* 报表的发布或更新日期必须晚于 2016 年 11 月 23 日。 不能下载之前发布的报表。
* 此功能对最初在 Power BI 服务中创建的报表及内容包均不适用。
* 打开下载的文件时，始终使用最新版本的 Power BI Desktop。 在 Power BI Desktop 的非当前版本中可能无法打开下载的 .pbix 文件。
* 如果管理员已关闭数据下载功能，则此功能在 Power BI 服务中将不可见。
* 不能将包含递增刷新的数据集下载到 .pbix 文件。
* 无法将为[大模型](../admin/service-premium-large-models.md)启用的数据集下载到 .pbix 文件。
* 无法将使用 [XMLA 终结点](../admin/service-premium-connect-tools.md)修改的数据集下载到 .pbix 文件。
* 如果你创建基于一个工作区中数据集的 Power BI 报表，并将此报表发布到另一个工作区，那么你和你的用户就无法下载此报表。 此场景暂不支持下载功能。

## <a name="next-steps"></a>后续步骤

查看有关此功能的 **Guy in a Cube** 一分钟视频：

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

以下是一些其他文章，可帮助你了解如何使用 Power BI 服务：

* [Power BI 中的报表](../consumer/end-user-reports.md)
* [Power BI 服务中设计器的基本概念](../fundamentals/service-basic-concepts.md)

安装 Power BI Desktop 之后，以下文章可帮助你快速启动和运行：

* [Power BI Desktop 入门](../fundamentals/desktop-getting-started.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)。
---
title: 将报表从 Power BI 服务下载到 Power BI Desktop（预览版）
description: 将报表从 Power BI 服务下载到 Power BI Desktop 文件
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 61fc821e63889951aefd0ef815f885ffa8a880cf
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68994825"
---
# <a name="download-a-report-from-the-power-bi-service-to-power-bi-desktop-preview"></a>将报表从 Power BI 服务下载到 Power BI Desktop（预览版）
在 Power BI Desktop 中，可以将报表（.pbix 文件）从本地计算机发布到 Power BI 服务  。 Power BI 报表也可以反向流动：可以将报表从 Power BI 服务下载到 Power BI Desktop。 两种情况下，Power BI 报表的扩展均为 .pbix。

有几个需要牢记的限制和注意事项，将稍后在本文中讨论。

![文件下拉列表](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix-file"></a>以 .pbix 文件形式下载报表

仅可下载 2016 年 11 月 23 日及之后更新的 [Power BI Desktop 上所创建](guided-learning/publishingandsharing.yml?tutorial-step=2)的报表。 如果是之前创建的，则 Power BI 服务中的“下载报表”菜单选项显示为灰色  。

若要下载 .pbix 文件，请执行以下步骤：

1. 在 Power BI 服务的[编辑视图](https://docs.microsoft.com/power-bi/service-interact-with-a-report-in-editing-view)中，打开要下载的报表。

2. 在顶部导航栏中，依次选择“文件”>“下载报表”  。
   
3. 报表正在下载时，状态横幅将显示进度。 在文件就绪后，系统会询问此 .pbix 文件的保存位置。 默认文件名与报表名相匹配。
   
4. 如果还没有[安装 Power BI Desktop](desktop-get-the-desktop.md)，请安装它，然后在 Power BI Desktop 中打开该 .pbix 文件。
   
    在 Power BI Desktop 中打开报表时，可能会看到警告消息，告知你在 Power BI 服务报表中提供的某些功能在 Power BI Desktop 中不可用。
   
    ![警告对话框](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. Power BI Desktop 中的报表编辑器和 Power BI 服务中的报表编辑器非常相似。  
   
    ![Power BI Desktop 报表编辑器](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
从 Power BI 服务下载 .pbix 文件有几个相关的重要注意事项和限制。

* 若要下载文件，必须具有编辑报表的权限。
* 报表必须使用 Power BI Desktop 创建，且必须在 Power BI 服务中发布。或者，必须已将 .pbix 文件上传到 Power BI 服务中   。
* 报表的发布或更新日期必须晚于 2016 年 11 月 23 日。 不能下载之前发布的报表。
* 此功能对最初在 Power BI 服务中创建的报表及内容包均不适用。
* 打开下载的文件时，始终使用最新版本的 Power BI Desktop。 在 Power BI Desktop 的非当前版本中可能无法打开下载的 .pbix 文件。
* 如果管理员已关闭数据下载功能，则此功能在 Power BI 服务中将不可见。
* 不能将包含递增刷新的数据集下载到 .pbix 文件。

## <a name="next-steps"></a>后续步骤
查看有关此功能的 **Guy in a Cube** 一分钟视频：

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

以下是一些其他文章，可帮助你了解如何使用 Power BI 服务：

* [Power BI 中的报表](consumer/end-user-reports.md)
* [Power BI 服务中设计器的基本概念](service-basic-concepts.md)

安装 Power BI Desktop 之后，以下文章可帮助你快速启动和运行：

* [Power BI Desktop 入门](desktop-getting-started.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)。


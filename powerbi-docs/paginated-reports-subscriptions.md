---
title: 在 Power BI 服务中订阅分页报表
description: 在本文中，将学习在 Power BI 服务中订阅分页报表时应记住的事项。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839548"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>在 Power BI 服务中为自己和他人订阅分页报表 

现在可以在 Power BI 服务中为自己和他人设置分页报表的电子邮件订阅。 一般而言，该过程与[在 Power BI 服务中订阅报表和仪表板](service-report-subscribe.md)的过程相同。 本文介绍其中的差异和注意事项。 

设置订阅时，可以选择接收电子邮件的频率：每天、每周或每小时。 如果选择每天或每周，则可以选择希望订阅运行的时间。 每天总共可以为每个报表设置最多 24 个不同的订阅。 

## <a name="considerations-for-paginated-report-subscriptions"></a>分页报表订阅注意事项 

- 与仪表板或 Power BI 报表的订阅不同，你的订阅包含有关整个报表输出的附件。  支持以下附件类型：PDF、PowerPoint 演示文稿 (PPTX)、Excel 工作簿 (XLSX)、Word 文档 (DOCX)、CSV 文件和 XML。

- 电子邮件正文中没有报表的预览图像。  我们计划在报表的第一页提供该图像并将其作为可选项目。 

- 最大报表附件大小为 25 MB。 

- 可以为其他用户订阅连接到任何当前支持的数据源的分页报表，包括 Azure Analysis Services 或 Power BI 数据集。 请记住，报表附件会根据权限反映数据，就像 SQL Server Reporting Services 目前的状况那样。 

- 报表页订阅与报表的名称相关联。  

- 电子邮件订阅与报表的默认参数值一起发送。 

- 分页报表的频率没有“数据刷新后”选项  。 始终从基础数据源获取最新值。 

## <a name="next-steps"></a>后续步骤

[在 Power BI 服务中为自己和他人订阅报表和仪表板](service-report-subscribe.md)

[Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)

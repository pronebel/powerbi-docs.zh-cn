---
title: 订阅 Power BI 服务中的分页报表
description: 在本文中，你将了解记住有关 Power BI 服务中的分页报表订阅的注意事项。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222197"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>你自己和其他人订阅 Power BI 服务中的分页报表 

现在可以设置 Power BI 服务中的分页报表为你自己和其他人的电子邮件订阅。 一般情况下，该过程是相同[订阅报表和 Power BI 服务中的仪表板](service-report-subscribe.md)。 本文阐述了差异和注意事项。 

设置订阅，选择你想要接收电子邮件的频率： 每日、 每周或每小时。 如果您选择每天或每周，可以选择的时间想要运行的订阅。 在所有，可以设置每个报表每天最多 24 个不同的订阅。 

## <a name="considerations-for-paginated-report-subscriptions"></a>有关分页的报表订阅的注意事项 

- 与不同的仪表板或 Power BI 报表的订阅，你的订阅包含整个报表输出的附件。  支持以下附件类型：PDF、 PowerPoint 演示文稿 (PPTX)、 Excel 工作簿 (XLSX)、 Word 文档 (DOCX)、 CSV 文件和 XML。

- 电子邮件正文中的报表没有预览图像。  我们正计划具有可选的项作为报表的第一页的图像。 

- 附件的最大报表大小是 25 MB。 

- 您可以订阅连接到任何当前支持的数据源，包括 Azure Analysis Services 或 Power BI 数据集的分页报表的其他用户。 请的注意报表附件反映数据基于您的权限，就像 SQL Server Reporting Services 的现状。 

- 报表页订阅已绑定到报表的名称。  

- 使用报表的默认参数值发送的电子邮件订阅。 

- 没有任何**后的数据刷新**与分页报表的频率的选项。 始终从基础数据源获取最新值。 

## <a name="next-steps"></a>后续步骤

[你自己和其他人订阅报表和 Power BI 服务中的仪表板](service-report-subscribe.md)

[Power BI Premium 中的分页报表是什么？（预览）](paginated-reports-report-builder-power-bi.md)

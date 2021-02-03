---
title: 在 Power BI 服务中订阅分页报表
description: 在本文中，将学习在 Power BI 服务中订阅分页报表时应记住的事项。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 01/22/2021
ms.openlocfilehash: 5817bf3752a03361be4e982faf10dffb67bda0b5
ms.sourcegitcommit: 1872a167d1e4d731ad00cf8a6d951c31aa54bcce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2021
ms.locfileid: "98925791"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>在 Power BI 服务中为自己和他人订阅分页报表 

现在可以在 Power BI 服务中为自己和他人设置分页报表的电子邮件订阅。 一般而言，该过程与[在 Power BI 服务中订阅报表和仪表板](end-user-subscribe.md)的过程相同。 本文介绍其中的差异和注意事项。 

设置订阅时，可以选择想要接收电子邮件的频率：每日、每周、每月或每小时。 还可选择想要订阅运行的时间。 每个报表可设置的订阅数没有限制。 

## <a name="considerations-for-paginated-report-subscriptions"></a>分页报表订阅注意事项 

- 无需分页报表编辑权限即可为自己创建订阅，但必须拥有编辑权限才能为他人创建订阅。 如果在分页报表所在的工作区中至少具有“参与者”角色，则可以为其他人创建订阅。 详细了解[工作区中的角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。

- 与仪表板或 Power BI 报表的订阅不同，你的订阅包含有关整个报表输出的附件。  支持以下附件类型：PDF、PowerPoint 演示文稿 (PPTX)、Excel 工作簿 (XLSX)、Word 文档 (DOCX)、CSV 文件和 XML。

- 可以在电子邮件正文中包含报表的预览图像。  这是可选的，且可能与附加的报表文件的第一页略有不同，具体取决于所选的附件格式。 

- 最大报表附件大小为 25 MB。 

- 可以为其他用户订阅连接到任何当前支持的数据源的分页报表，包括 Azure Analysis Services 或 Power BI 数据集。 请记住，报表附件会根据权限反映数据，就像 SQL Server Reporting Services 目前的状况那样。 

- 可以使用报表的当前选定参数或默认参数发送电子邮件订阅。  可以为你为报表创建的每个订阅设置不同的参数值。 

- 如果报表作者已设置基于表达式的参数（例如，默认值始终为今天的日期），则订阅将使用该参数作为默认值。 可以更改其他参数值并选择使用当前值，但除非同时明确更改该值，否则订阅将使用基于表达式的参数。

- 分页报表的频率没有“数据刷新后”选项  。 始终从基础数据源获取最新值。 

## <a name="next-steps"></a>后续步骤

[在 Power BI 服务中为自己和他人订阅报表和仪表板](../collaborate-share/service-report-subscribe.md)

[Power BI 服务中的分页报表](end-user-paginated-report.md)

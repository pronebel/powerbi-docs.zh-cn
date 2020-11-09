---
title: 从数据集下载分页报表的 .rdl
description: 本文介绍如何通过“从 Power BI 服务中的共享数据集中下载”的方式来创建 Power BI 分页报表的 .rdl。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 10/15/2020
ms.openlocfilehash: c5c8f61a7253da46529a83276366044560d4f030
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297624"
---
# <a name="download-the-rdl-for-a-power-bi-paginated-report-from-a-dataset"></a>从数据集下载 Power BI 分页报表的 .rdl

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

本文介绍如何通过“从 Power BI 服务中的共享数据集中下载”的方式来创建 Power BI 分页报表的 .rdl。 分页报表的文件格式为 .rdl。 可以直接从 Power BI 服务的数据集创建 .rdl 文件。

1. 转到任何工作区的列表视图，包括“我的工作区”。 
1. 为数据集选择“更多选项(...)”，然后选择“下载 .rdl”。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-download-rdl.png" alt-text="Power BI 服务中的“下载 .rdl”选项的屏幕截图。":::
1. 你会看到一条消息，要求你更新 Power BI Report Builder。 选择“下载”  。 

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-updates.png" alt-text="安装 Power BI Report Builder 更新的屏幕截图。":::

    如果你拥有 Power BI Report Builder 的最新版本，请选择“我已安装这些更新”。

1. 完成 Power BI Report Builder 安装过程： 

    1. 选择“下载”  。  
    2. 选择“打开文件”并完成 Power BI Report Builder 安装向导中的步骤。

1. Report Builder 安装完成后，返回到 Power BI 服务并选择“下载 .rdl”。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-finished-installing.png" alt-text="下载 .rdl 对话框的屏幕截图。":::

1. 在浏览器窗口中选择“打开文件”。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-open-file.png" alt-text="在浏览器中选择“打开文件”的屏幕截图。":::

1. 打开 Power BI Report Builder 时将自动生成标题，并会打开“数据源”文件夹中的 Power BI 数据集 .pbix 文件。 该数据源具有与 Power BI 数据集相同的名称。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-design-canvas.png" alt-text="设计视图中 Power BI Report Builder 的屏幕截图。":::

    设计图面还提供了一个链接，指向基于[一天玩转 Power BI 分页报表](../learning-catalog/paginated-reports-online-course.md)视频的课程。 如果不熟悉如何创建分页报表，则可以通过该课程来快速了解。  在开始设计报表时，可以将其删除。

    现在可以开始设计分页报表了。
 
## <a name="next-steps"></a>后续步骤 

- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)  
- [教程：创建分页报表并将其上传到 Power BI 服务](paginated-reports-quickstart-aw.md)
- [将分页报表发布到 Power BI 服务](paginated-reports-save-to-power-bi-service.md)


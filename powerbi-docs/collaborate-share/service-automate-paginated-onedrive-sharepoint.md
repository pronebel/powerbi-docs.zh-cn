---
title: 将分页报表保存到 OneDrive for Business 或 SharePoint Online
description: 本文将使用 Power Automate 自动将 Power BI 分页报表保存到 OneDrive for business 或 SharePoint Online 文件夹中。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/17/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 67f49d19e3488b80a980719220fcc4715a6952e7
ms.sourcegitcommit: b2693047fce6a4e0c3ea07013404e99fc9cc1901
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "94904858"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>将分页报表保存到 OneDrive for Business 或 SharePoint Online

借助 [Power Automate](/power-automate/getting-started)，Power BI 分页报表可自动导出并分发到各种受支持的格式和方案。 本文将使用 Power Automate 自动将 Power BI 分页报表保存到 OneDrive for Business 或 SharePoint Online 文件夹中。

:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="将分页报表保存到 OneDrive 或 SharePoint Online 的 Power Automate 流的屏幕截图":::

正在寻找用于 Power BI 分页报表的其他 Power Automate 模板？ 请参阅[使用 Power Automate 导出 Power BI 分页报表](service-automate-paginated-integration.md)。 

## <a name="prerequisites"></a>先决条件  

若要继续操作，请确保：

- Power BI 租户中至少有一个由预留容量提供支持的工作区。 此容量可以是 A4/P1 – A6/P3 SKU 中的任何一个。 详细了解 [Power BI Premium 中的预留容量](../admin/service-premium-what-is.md)。
- 有权访问 Power Automate 中的标准连接器，这些连接器随任何 Office 365 订阅一起提供。

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>将分页报表保存到 OneDrive for Business 或 SharePoint Online 文件夹 

使用上述任一模板，都可以设置分页报表，使其以所需格式定期导出到 OneDrive for Business 或 SharePoint Online 文件夹。 如果这是你第一次使用 Power Automate 流中的“将分页报表导出为文件”操作，请参阅先决条件。 

> [!NOTE]
> 以下步骤和图像将演示如何使用“将 Power BI 分页报表保存到 OneDrive for Business”模板来设置流。 使用“将 Power BI 分页报表保存到 SharePoint Online 文件夹”模板按照相同的步骤创建流。 选择分页报表的导出位置时，请选择 SharePoint Online 文件夹，而不是 OneDrive for Business 文件夹。 

1. 登录 Power Automate [flow.microsoft.com](https://flow.microsoft.com/)。 
1. 选择“模板”，然后搜索“分页报表” **** 。 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="用于 Power BI 分页报表的 Power Automate 模板的屏幕截图。":::

1. 选择“将 Power BI 分页报表保存到 OneDrive for Business”或“将 Power BI 分页报表保存到 SharePoint Online 文件夹” 。 请确保你已登录 Power BI 和 OneDrive for Business 或 SharePoint Online。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="选择 Power BI 和 OneDrive for Business 模板的屏幕截图。":::
1. 选择“继续”。  


1. 若要为流设置“重复周期”，请在“频率”中选择一个选项，并输入所需的“间隔”值  。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="为流选择重复周期。":::

1. （可选）选择“显示高级选项”以设置额外的“重复周期”参数，包括“时区”、“开始时间”、“天数”、“小时数”、“分钟数”      。  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="显示重复周期的高级选项。":::

1. 在“工作区”框中，选择预留容量中的工作区。 在“报表”框中，选择所选工作区中要导出的分页报表。 在“导出格式”框中，选择所需的导出格式。 也可以为分页报表指定参数。 有关参数的详细说明，请参阅 [Power BI Rest API 的连接器参考](/connectors/powerbi/#export-to-file-for-paginated-reports)。  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="选择分页报表、工作区和导出格式。":::

1. 在“文件夹路径”中，选择要将分页报表导出到的 OneDrive for Business 或 SharePoint Online 文件夹。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="选择目标并创建文件。":::

1. Power Automate 会为你自动生成“文件名”和“文件内容” 。 你可以更改文件名，但保留动态生成的“文件内容”值。 

1. 完成后，选择“下一步”或“保存” ****  。 Power Automate 会创建和评估流，并告知你是否找到错误。 

1. 如果有错误，请选择“编辑流”以修复错误 ****  。 如果没有，请选择“后退”箭头以查看流的详细信息并运行新流。 

    运行流时，Power Automate 会采用指定格式将分页报表导出到 OneDrive for Business 或 SharePoint Online。  

## <a name="next-steps"></a>后续步骤

- [使用 Power Automate 导出 Power BI 分页报表](service-automate-paginated-integration.md)
- [Power Automate 入门](/power-automate/getting-started/)
- 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

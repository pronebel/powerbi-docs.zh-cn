---
title: 使用 Power Automate 导出报表并以电子邮件的方式发送
description: 在本文中，你将使用 Power Automate 将 Power BI 报表自动导出并分发到各种受支持的格式和方案。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098570"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>使用 Power Automate 导出 Power BI 报表并以电子邮件的方式发送

借助 [Power Automate](/power-automate/getting-started)，Power BI 报表可自动导出并分发到各种受支持的格式和方案。 在本文中，你将从头开始创建自己的流。 对 Power BI 报表操作使用“导出到文件”，以便通过电子邮件自动分发 Power BI 报表。

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="导出报表并以电子邮件的方式发送的 Power Automate 步骤。":::

## <a name="prerequisites"></a>先决条件  

若要继续操作，请确保：

- Power BI 租户中至少有一个由预留容量提供支持的工作区。 此容量可以是 A1/EM1 - A6/P3 SKU 中的任何一个。 详细了解 [Power BI Premium 中的预留容量](../admin/service-premium-what-is.md)。
- 有权访问 Power Automate 中的标准连接器，这些连接器随任何 Office 365 订阅一起提供。

## <a name="create-a-flow-from-scratch"></a>从头开始创建流 

在此任务中，你将从头开始创建一个简单的流。 该流将 Power BI 报表导出为 PDF 格式，并将其附加到电子邮件，每周发送一次。  

1. 登录 Power Automate (flow.microsoft.com)。
2. 选择“创建” > “计划流”。 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="在 Power Automate 中创建计划流。":::

3. 在“生成计划流”中，为流指定名称。 
4. 在“运行此流”中，选择流的开始日期和时间以及重复频率。
5. 在“在这些天”中，选择想要运行流的日期，然后选择“创建”。

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate，计划流。":::

6. 在“定期”中，选择“显示高级选项”并在“在这些小时”和“在这些分钟”中输入值以设置运行流的特定时间。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="在 Power Automate 中设置定期。":::

7. 选择“新建步骤”。
8. 在“选择操作”中，搜索“Power BI”并选择“将 Power BI 报表导出到文件”。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="在 Power Automate 中选择一个操作。":::

9. 在“将 Power BI 报表导出到文件”中，从下拉列表中选择“工作区”和“报表”。
10. 选择 Power BI 报表所需的导出格式。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="在 Power Automate 中选择导出格式。":::

11. （可选）指示要在“页面 pageName-1”字段中导出的特定页面。 请注意，页面名称参数与显示页面名称不同。 通过导航到 Power BI 服务中的页面并复制 URL 的最后一部分来查找页面名称。
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="选择 URL 中的窗格名称。":::

12. （可选）指示要在“页面书签名称”字段中显示的特定书签。 与页面名称参数一样，你将在报表 URL 中找到书签名称参数。 可以为 Power BI 报表指定其他参数。 有关这些参数的详细说明，请参阅 [Power BI REST API 的连接器参考](/connectors/powerbi/#export-to-file-for-power-bi-reports)。

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="选择 URL 中的书签名称。":::

13. 选择“新建步骤”。
14. 在“选择操作”，搜索“Outlook”并选择“发送电子邮件(V2)”。
15. 在“发送电子邮件(V2)”中，填写电子邮件的“收件人”、“主题”和“正文”字段。
16. 选择“显示高级选项”。 在“附件名称 – 1”中，输入附件的名称。 将文件扩展名添加到与所需的导出格式匹配的文件名（例如，PDF）。
17. 在“附件内容”中，选择“文件内容”以附加导出的 Power BI 报表。  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="选择要以电子邮件形式发送的已导出报表。":::

18. 完成后，选择“下一步”或“保存”。 Power Automate 会创建和评估流，并告知你是否找到错误。
1. 如果有错误，请选择“编辑流”以修复错误 ****  。 如果没有，请选择“后退”箭头来查看流的详细信息，并运行新流。
    运行流时，Power Automate 会以指定的格式导出 Power BI 报表，并按计划将其作为电子邮件附件发送。  

## <a name="next-steps"></a>后续步骤

- [将 Power BI 数据警报与 Power Automate 集成](service-flow-integration.md)
- [Power Automate 入门](/power-automate/getting-started/)
- 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

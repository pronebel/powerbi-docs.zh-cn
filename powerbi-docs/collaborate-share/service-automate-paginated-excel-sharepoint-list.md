---
title: 为 Excel Online 表或 SharePoint 列表中的每一行导出一个分页报表
description: 本文将使用 Power Automate，自动为 Excel Online 表或 SharePoint Online 列表中的每一行导出一个分页报表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: 7a48a9a594364de4261aa66de48c1a4262392364
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097837"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>为 Excel Online 表或 SharePoint 列表中的每一行导出一个分页报表

借助 [Power Automate](/power-automate/getting-started)，Power BI 分页报表可自动导出并分发到各种受支持的格式和方案。 本文将使用 Power Automate 模板自动设置单个或多个分页报表的定期导出。 对于 Excel Online 表或 SharePoint Online 列表中的每一行，可以采用所需格式将它们导出。 你可将导出的分页报表分发到 OneDrive for Business 或 SharePoint Online 站点，或者通过 Office 365 Outlook 向其发送电子邮件。

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="使用 Excel Online 表导出分页报表。":::

Excel Online 表或 SharePoint Online 列表中的每一行都可以表示单个用户，用户可基于订阅接收分页报表。 或者，每一行都可以表示要分发的唯一分页报表。 表或列表需要一列来指定如何分发报表，无论是 OneDrive、SharePoint Online 还是 Outlook。 Power Automate 流在其 Switch 语句中使用此列。

正在寻找用于 Power BI 分页报表的其他 Power Automate 模板？ 请参阅[使用 Power Automate 导出 Power BI 分页报表](service-automate-paginated-integration.md)。

## <a name="prerequisites"></a>先决条件  

若要继续操作，请确保：

- Power BI 租户中至少有一个由预留容量提供支持的工作区。 此容量可以是 A4/P1 – A6/P3 SKU 中的任何一个。 详细了解 [Power BI Premium 中分页报表的预留容量](../admin/service-premium-what-is.md#paginated-reports)。
- 有权访问 Power Automate 中的标准连接器，这些连接器随任何 Office 365 订阅一起提供。
- 如果使用的是 Excel Online 表，则需要将其格式化为 Excel 表。 请参阅[创建表](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)了解操作方法。

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>为表或列表中的每一行导出一个分页报表

> [!NOTE]
> 以下步骤和图像将演示如何使用“为 Excel Online 表中的每一行导出 Power BI 分页报表”模板来设置流。 可使用“为 SharePoint Online 列表中的项导出 Power BI 分页报表”模板按照相同的步骤创建流。 SharePoint Online 列表（而非 Excel Online 表）将包含有关如何导出分页报表的信息。  

1. 登录 Power Automate [flow.microsoft.com](https://flow.microsoft.com/)。 
1. 选择“模板”，然后搜索“分页报表” **** 。 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="用于 Power BI 分页报表的 Power Automate 模板的屏幕截图。":::

1. 选择“为 Excel Online 表中的每一行导出 Power BI 分页报表”或“为 SharePoint Online 列表中的项导出 Power BI 分页报表”模板 。 请确保你已登录 Excel Online、Power BI、OneDrive for Business、SharePoint Online 和 Office 365 Outlook。 选择“继续”。  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="为 Excel Online 表中的每一行导出 Power BI 分页报表。":::

1. 若要为流设置“重复周期”，请在“频率”中选择一个选项，并输入所需的“间隔”值  。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="为流选择重复周期。":::

1. （可选）选择“显示高级选项”以设置额外的“重复周期”参数，包括“时区”、“开始时间”、“天数”、“小时数”、“分钟数”      。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="（可选）选择高级重复周期选项。":::

1. 在“位置”框中，选择保存 Excel Online 表或 SharePoint Online 列表的 OneDrive for Business 或 SharePoint Online 站点。 然后从下拉列表中选择“文档库”。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="选择 Excel Online 表的位置。":::

1. 在“文件”框中选择 Excel Online 文件或 SharePoint Online 列表。 从“表”框的下拉列表中选择表或列表的名称。 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="选择 Excel Online 文件和表的名称。":::

    > [!TIP]
    > 请参阅[创建表](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)，了解如何将数据格式化为 Excel 表。 

1. 初始化要用于文件名的变量。 可保留或修改“名称”和“值”的默认值，但将“类型”保留为“字符串”   。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="填写“名称”和“值”，并将“类型”保留为“字符串”。":::

1. 在“应用到每一项”中，“选择上一步中的输出”框默认设置为“值”  。 此设置将为 Excel Online 表或 SharePoint Online 列表中的每一行循环访问“应用到每一项”中包含的操作。  

1. 在“工作区”框中，选择预留容量中的工作区。 在“报表”框中，选择所选工作区中要导出的分页报表。 如果从下拉列表中设置“输入自定义值”，可将“工作区”和“报表”设置为等于 Excel Online 表或 SharePoint Online 列表中的列  。 这些列应分别包含工作区 ID 和报表 ID。  

1. 从下拉列表中选择“导出格式”，或将其设置为包含所需导出格式的 Excel Online 表中的列。 例如 PDF、DOCX 或 PPTX。 也可以为分页报表指定参数。 有关参数的详细说明，请查看 [Power BI REST API 的连接器参考](/connectors/powerbi/#export-to-file-for-paginated-reports)。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="填写“将分页报表导出为文件”。":::

1. 导出分页报表后，在“值”框中输入名称。 请务必输入文件扩展名。 可静态设置扩展名，如 .pdf、.docx 或 .pptx。 也可通过在 Excel 表中选择与所需导出格式相对应的列，来动态设置扩展名。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="选择报表的名称和文件扩展名。":::

1. 在 Switch 操作中，用 Excel Online 表中与所需传递方法对应的列填充“On”框 ：OneDrive、SharePoint 或电子邮件  。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="在 Switch 中，用 Excel Online 表中的列填充 On 框。":::

1. 在“案例”、“案例 2”和“案例 3”中，输入上一步中选择的 Excel Online 表列中显示的值  。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="为“案例”、“案例 2”和“案例 3”输入值。":::

1. 如果要将分页报表保存到 OneDrive，请选择保存位置的“文件夹路径”。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="保存到 OneDrive 的情况。":::

1. 如果要将分页报表保存到 SharePoint Online，请输入保存位置的“站点地址”和“文件夹路径” 。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="将分页报表保存到 SharePoint Online 的情况。":::

1. 如果要通过 Outlook 以电子邮件的方式发送分页报表，请填充“收件人”、“主题”和“正文”框  。 这些框可以包含静态内容，也可包含来自 Excel Online 表或 SharePoint Online 列表的动态内容。 Power Automate 会将分页报表自动附加到此电子邮件。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="通过 Outlook 以电子邮件的方式发送分页报表的情况。":::

1. 完成后，选择“下一步”或“保存” ****  。 Power Automate 会创建和评估流，并告知你是否找到错误。 

1. 如果有错误，请选择“编辑流”以修复错误 ****  。 如果没有，请选择“后退”箭头来查看流的详细信息，并运行新流。 


## <a name="next-steps"></a>后续步骤

- [使用 Power Automate 导出 Power BI 分页报表](service-automate-paginated-integration.md)
- [Power Automate 入门](/power-automate/getting-started/)
- 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


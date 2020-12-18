---
title: 使用 Power Automate 将分页报表保存到本地文件夹
description: 在本文中，使用模板以所需格式设置将分页报表定期导出到文件系统。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098568"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>使用 Power Automate 将 Power BI 分页报表保存到本地文件夹

借助 [Power Automate](/power-automate/getting-started)，Power BI 分页报表可自动导出并分发到各种受支持的格式和方案。 在本文中，使用模板以所需格式设置将分页报表定期导出到文件系统。 如果这是你第一次使用 Power Automate 流中的“将分页报表导出为文件”操作，请参阅先决条件。

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="设置定期导出分页报表。":::

正在寻找用于 Power BI 分页报表的其他 Power Automate 模板？ 请参阅[使用 Power Automate 导出 Power BI 分页报表](service-automate-paginated-integration.md)。

## <a name="prerequisites"></a>先决条件  

若要继续操作，请确保：

- Power BI 租户中至少有一个由预留容量提供支持的工作区。 此容量可以是 A4/P1 – A6/P3 SKU 中的任何一个。 详细了解 [Power BI Premium 中分页报表的预留容量](../admin/service-premium-what-is.md#paginated-reports)。
- 有权访问 Power Automate 中的标准连接器，这些连接器随任何 Office 365 订阅一起提供。

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>将 Power BI 分页报表保存到本地文件夹

1. 选择“将 Power BI 分页报表保存到本地文件系统”模板。 请确保已登录到 Power BI 并连接到本地文件系统。 选择“继续”。 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="将 Power BI 分页报表保存到本地文件系统。":::

2. 你可能需要选择“添加新连接”以连接到文件系统。 
1. 输入“连接名称”、所需“根文件夹”的路径，并通过输入“用户名”和“密码”来进行身份验证。 如果使用的是本地数据网关，请从下拉列表中选择“网关”。

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="输入连接名称和根文件夹。":::
 
3. 若要为流设置“重复周期”频率，请从“频率”下拉列表中选择一个选项，并输入所需的“间隔”值。  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="设置流的重复周期频率。":::

4. （可选）选择“显示高级选项”。 设置额外的“重复周期”参数，如“时区”、“开始时间”、“天数”、“小时数”、“分钟数”。 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="设置重复周期的高级选项。":::

5. 在“工作区”框中，选择报表所在的预留容量中的工作区。 在“报表”框中，选择要在工作区中导出的分页报表。 在“导出格式”框中，选择所需的导出格式。 也可以为分页报表指定参数。 有关参数的详细说明，请参阅 [Power BI REST API 的连接器参考](/connectors/powerbi/#export-to-file-for-paginated-reports)。  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="选择工作区和报表。":::

6. 在“创建文件”对话框的“文件夹路径”中，选择要将分页报表导出到的文件夹。
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="选择要导出分页报表的文件夹":::

7. Power Automate 会为你自动生成“文件名”和“文件内容”。 可以修改“文件名”，但保留动态生成的“文件内容”值。
8. 完成后，选择“下一步”或“保存”。 此时，Power Automate 会创建并计算流。
9. 如果 Power Automate 发现错误，请选择“编辑流”来修复错误。 如果没有，请选择“后退”箭头来查看流的详细信息，并运行新流。
10. 运行流时，Power Automate 会采用指定格式将分页报表导出到文件系统的所选文件夹中。

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automate 以指定格式导出分页报表。":::

## <a name="next-steps"></a>后续步骤

- [使用 Power Automate 导出 Power BI 分页报表](service-automate-paginated-integration.md)
- [Power Automate 入门](/power-automate/getting-started/)
- 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


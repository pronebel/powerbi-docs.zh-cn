---
title: Power BI 分页报表示例
description: 本文介绍如何下载和使用 Power BI 分页报表示例。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/10/2020
ms.openlocfilehash: cfa4b46e521079802ec87b63d6323e01213625c3
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483814"
---
# <a name="sample-power-bi-paginated-reports"></a>Power BI 分页报表示例


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

本文提供了一些信息和指向多个 Power BI 分页报表示例的链接，可供你下载和探索。 它们演示了分页报表的几种典型用法。

## <a name="prerequisites"></a>先决条件

- 你可以按原样联机共享这些报表，无需编辑。 若要共享这些报表，需要 Power BI Pro 许可证。 注册 [Power BI Pro 许可证免费试用版](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro)。
- 还需要有权访问[高级容量](../admin/service-premium-what-is.md)中的 Power BI 工作区。
- 若要编辑这些报表，需要从 Microsoft 下载中心[安装 Power BI Report Builder](https://aka.ms/pbireportbuilder)。
- 好了，接下来你就可以从 GitHub 下载这些分页报表示例了！ 不需要 GitHub 帐户。 

## <a name="download-the-reports"></a>下载报表

要成功下载报表，需要将存储库下载为 zip 文件，然后将其解压缩。 分页报表是 .rdl 文件。

1. 打开 [Reporting Services GitHub 存储库](https://github.com/microsoft/Reporting-Services)。
1. 选择绿色的“代码”按钮上的箭头 >“下载 ZIP” 。

    :::image type="content" source="media/paginated-reports-samples/paginated-report-download-zip.png" alt-text="包含示例 Power BI 分页报表的 GitHub 存储库的屏幕截图。":::
    
1. 打开文件，选择“全部提取”，然后选择文件的位置。 默认情况下，该文件夹名称为“Reporting Services-master”。
1. 打开”Reporting-Services-master”文件夹，然后打开”PaginatedReportSamples”文件夹 。

    >[!NOTE]
    >可以删除“Reporting-Services-master”文件夹中的所有其他文件夹。 它们包含你不需要的其他示例。

1. 选择其中一个 .rdl 文件，在 Power BI 报表生成器中将其打开。
1. 现在，可以[将分页报表发布到 Power BI 服务](paginated-reports-save-to-power-bi-service.md)。

## <a name="invoice"></a>发票

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Power BI 分页报表发票示例的屏幕截图。":::


此分页报表是一张独立发票。 此报表的应用场景是，你想要一张可以打印的完美像素发票。 它需要显示总销售额，并详细列出明细说明、数量、折扣和成本。

此示例重点介绍了创建真实发票的特征，例如：  

- 一个矩表（基于表和矩阵的数据区域）。 它显示动态生成的用户特定内容和主题。
- 一个矩形数据区域，位于表体中矩表的每一行。
- 报表项（如文本框和行）。
- 一个报表参数，用于动态选择内容。 显示的内容通过表达式占位符应用于特定主题。 

数据源:已包含在 .rdl 文件中

## <a name="labels"></a>标签

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="“分页报表”标签的屏幕截图。":::

这是一个独立的分页报表示例。 它是一个多列报表，大小恰好适合邮件标签模板打印布局。 

标签报表很简单，但创建分页标签有几个特征：

- 一个固定三列的矩表，具有已定义的列间距。
- 一个矩形数据区域，在打印页中跨行和列重复。
- 一个报表参数，用于选择要在每个矩形数据区域中显示的内容。

数据源:已包含在 .rdl 中

## <a name="mailing-letter"></a>邮寄信函

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Power BI 分页报表信函示例的屏幕截图。":::

这个独立分页报表示例专门用于创建真实的邮寄信函。 此报表的应用场景是，你想要一封可以打印的带动态内容的完美像素信函。

此示例有以下特征，例如： 

- 一个矩形数据区域，位于表体的不同部分。 
- 用于对信函进行个性化设置的图像。 
- 一个矩表数据区域（基于表和矩阵的数据区域）。 矩表显示动态生成的用户特定内容。
- 报表项（如文本框和行）。
- 一个报表参数，用于动态选择内容。 显示的内容通过表达式占位符应用于特定主题。 

数据源:已包含在 .rdl 中

## <a name="transcript"></a>字幕

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Power BI 分页报表成绩单示例的屏幕截图。":::

此报表的应用场景是，你想要一份可以打印的完美像素成绩单。 它需要包含列出每个学生的课程描述详细信息和日期的动态内容。

这一独立分页报表示例具有以下特征： 

- 一个矩表数据区域（基于表和矩阵的数据区域）。 矩表使用嵌套行组显示动态生成的用户特定内容。
- 矩形数据区域，位于表体的不同部分。
- 报表项（如文本框和行）。

数据源:已包含在 .rdl 中

## <a name="sales-performance"></a>销售业绩

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="Power BI 分页报表销售业绩示例的屏幕截图。":::

“Country Sales Performance”是一个独立分页报表示例。 此报表的应用场景是，你想要一张可以打印的完美像素发票来查看总销售额和详细信息。 该示例展示了以下特点：

- 使用参数来展开表中的详细信息。
- 页眉和页脚。
- 使用表达式占位符的报表项（如文本框、线条和矩形）。
- 数据栏。
- 趋势线。
- 仪表面板。

数据源:已包含在 .rdl 中
  
## <a name="next-steps"></a>后续步骤

[在 Power BI 服务中查看分页报表](../consumer/paginated-reports-view-power-bi-service.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

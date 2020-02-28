---
title: 分页报表的图像使用指南
description: 在 Power BI 分页报表中使用图像的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 09fd2197cca31e083c0242b187d7e242244235eb
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530363"
---
# <a name="image-use-guidance-for-paginated-reports"></a>分页报表的图像使用指南

本文面向设计 Power BI [分页报表](../paginated-reports-report-builder-power-bi.md)的报表作者。 它在处理图像时提供建议。 通常，报表布局中的图像可以显示公司徽标或图片之类的图形。

图像可以存储在三个不同的位置：

- 报表中（嵌入）
- Web 服务器上
- 数据库中，可通过数据集进行检索

然后，可以在报表布局的各种方案中进行使用：

- 独立的徽标或图片
- 与数据行关联的图片
- 某些报表项的背景：
  - 表体
  - 文本框
  - 矩形
  - Tablix 数据区域（表、矩阵或列表）

## <a name="suggestions"></a>建议

请考虑以下建议，以提供专业的报表布局、轻松的维护和优化的报表性能：

- **尽可能减小图片的大小**：建议准备尺寸小，但看起来仍然清晰明了的图像。 重点是质量和大小之间的平衡。 请考虑使用图形编辑器（如 MS Paint）来减小图像文件的大小。
- **避免嵌入图像**：首先，嵌入图像会使报表文件大小膨胀，这可能会导致报表呈现速度变慢。 其次，如果需要更新多个报表图像（例如公司徽标更改时的情况），则嵌入图像的维护工作可能很快变得繁琐。
- **使用 Web 服务器存储**：将图像存储在 Web 服务器上是一个不错的选择，尤其是可能源自公司网站的公司徽标。 但是，如果报表用户要在你的网络之外访问报表，请注意。 在这种情况下，请确保可通过 Internet 访问图像。

    当图像与你的数据相关（如销售人员的照片），请命名图像文件，使报表表达式可以动态生成图像 URL 路径。 例如，你可以使用每位销售人员的工号来命名销售人员照片。 如果报表数据集可以检索到该工号，你就可以编写表达式来生成完整的图像 URL 路径。
- **使用数据库存储**：当关系数据库存储图像数据时，可以直接从数据库表中获取图像数据，尤其是在图像不太大的情况下。
- **适当的背景图像**：如果决定使用背景图像，请注意不要分散报表用户对报表数据的注意力。 

    此外，请务必使用水印样式的图像。 通常，水印样式的图像具有透明背景（或具有报表所用的背景色）。 它们还使用淡色。 水印样式图像的常见示例包括公司徽标或敏感度标签（如“草稿”或“机密”）。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI Premium 中的分页报表是什么？](../paginated-reports-report-builder-power-bi.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

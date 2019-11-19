---
title: 培训 Power BI 问答的问答工具简介（预览版）
description: Power BI 问答工具简介
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/17/2019
ms.author: mohaali
ms.openlocfilehash: 17d0a68782f34c09286be5ebe020668a15061ee4
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874936"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>培训 Power BI 问答的问答工具简介（预览版）

使用 Power BI 问答工具，可以为用户改进自然语言体验  。 作为设计者或管理员，你可以与自然语言引擎进行交互，并在以下三个方面进行改进： 

- 查看用户提出的问题。
- 教导 Q&A 以了解问题。
- 管理已教导 Q&A 的术语。

除了这些专用工具功能外，Power BI Desktop 中的“建模”  选项卡还提供了更多选项：  

- 同义词
- 行标签
- 在“问答”中隐藏
- 语言架构的配置（高级）

## <a name="get-started-with-qa-tooling"></a>开始使用问答工具

问答工具仅在 Power BI Desktop 中提供，且当前仅支持导入模式。

1. 打开 Power BI Desktop 并使用“问答”来创建视觉对象。 
2. 在视觉对象的角落，选择齿轮图标。 

    ![问答视觉对象齿轮](media/qna-visual-gear.png)

    此时将打开“入门”页。  

    ![问答入门](media/qna-tooling-dialog.png)

### <a name="review-questions"></a>查看问题

选择“查看问题”，查看 Power BI 服务中为租户使用的数据集列表  。 “查看问题”页还会显示数据集所有者、工作区和上次刷新日期  。 在这里，你可以选择一个数据集，并查看用户提出了哪些问题。 数据还会显示无法识别的单词。 此处显示的所有数据都是最近 28 天的数据。

![问答的查看问题](media/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>教导“问答”

在“教导 Q&A”部分，你可以培训问答来识别单词  。 首先，键入一个问题，其中包含一个或多个问答无法识别的单词。 问答提示你输入该术语的定义。 输入与该单词所代表的内容相对应的筛选器或字段名称。 问答随后将重新解释原问题。 如果对结果满意，可保存输入。 要了解详细信息，请参阅[教导 Q&A](q-and-a-tooling-teach-q-and-a.md)

![教导 Q&A 同义词预览版](media/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>管理术语

在教导 Q&A 部分保存的任何内容都显示在此处，因此你可以查看或删除已定义的术语。 目前，你无法编辑现有定义。因此，若要重新定义一个术语，则必须删除并重新创建该术语。

![问答的管理术语](media/qna-manage-terms.png)

## <a name="other-qa-settings"></a>其他问答设置

### <a name="bulk-synonyms"></a>批量同义词

Power BI Desktop“建模”选项卡提供了更多选项来改进问答体验  。 

1. 在 Power BI Desktop 中，选择“建模”视图。

2. 选择一个字段或表，以显示“属性”窗格  。  此窗格显示在画布右侧，并列出了几个问答操作。 其中一个选项是“同义词”  。 在“同义词”框中，可以为所选的表或字段快速定义替换项  。 还可以在“工具”对话框的“教导 Q&A”部分中定义同义词，但在此处为表中的许多字段定义同义词通常更快  。

    ![问答的建模窗格同义词](media/qna-modelling-pane-synonyms.png)

3. 要为单个字段定义多个同义词，请使用逗号来表示下一个同义词。

### <a name="hide-from-qa"></a>在“问答”中隐藏

还可以隐藏字段和表，这样它们不会显示在问答结果中。 

1. 在 Power BI Desktop 中，选择“建模”视图。

2. 选择一个字段或表，以显示“属性”窗格，并将“隐藏”切换为“开启”    。

    问答将遵循此设置并确保不识别该字段。 例如，你可能希望隐藏 ID 字段和外键，以避免不必要的具有相同名称的重复字段。 即使隐藏了字段，你仍可以在问答之外的 Power BI Desktop 视觉对象中使用它。

### <a name="set-a-row-label"></a>设置行标签

使用行标签可以定义哪一列（或字段  ）最能标识表中的单个行。 例如，对于一个名为“客户”的表，行标签通常是“显示名称”。 当用户键入“按客户显示销售额”时，提供此额外的元数据，使问答能绘制出更有帮助的视觉对象。 它可以使用“显示名称”并显示一个显示每个客户销售额的条形图，而不是将“客户”视为一个表。 你只能设置行标签建模视图。 

1. 在 Power BI Desktop 中，选择“建模”视图。

2. 选择一个表，以显示“属性”窗格  。

3. 在“行标签”  框中，选择一个字段。

## <a name="configure-the-linguistic-schema-advanced"></a>配置语言架构（高级）

在 Power BI 中，你可以在问答中完全训练和增强自然语言引擎，包括更改基础自然语言结果的评分和权重。 要了解如何进行操作，请参阅[编辑问答的语言架构并添加短语](q-and-a-tooling-advanced.md)。

## <a name="next-steps"></a>后续步骤

用于改进自然语言引擎的最佳做法还有很多。 有关详细信息，请参阅以下文章：

* [问答最佳做法](q-and-a-best-practices.md)

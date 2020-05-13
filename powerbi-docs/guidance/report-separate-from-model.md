---
title: 与 Power BI Desktop 中的模型分离报表
description: 与 Power BI Desktop 中的模型分离报表的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: 971c699170103d5521763679c93d3641c094cc58
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277424"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>与 Power BI Desktop 中的模型分离报表

创建新 Power BI Desktop 解决方案时，需要执行的第一项任务是“获取数据”。 获取数据可能会导致两种截然不同的结果。 它可以：

- 与已发布的模型建立[实时连接](../connect-data/desktop-report-lifecycle-datasets.md)这些模型可以是 Power BI 数据集或远程托管 Analysis Services 模型。
- 开始开发新模型，可以是 Import 模型、DirectQuery 模型或 Composite 模型。

本文介绍第二个方案。 本文提供有关是否应将报表和模型合并到单个 Power BI Desktop 文件的指导。

## <a name="single-file-solution"></a>单个文件解决方案

“单个文件解决方案”在只有单个基于模型的报表时有效  。 在这种情况下，模型和报表很可能都是同一个人在处理。 尽管报表可以与他人共享，但我们还是将它定义为“个人 BI”解决方案  。 此类解决方案可以表示角色范围内的报表或业务挑战的一次性评估，通常称为临时报表  。

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="单个文件包含由同一个人开发的模型和报表。" border="true":::

## <a name="separate-report-files"></a>分隔报表文件

遇到以下情况时，可以将模型和报表开发分隔到单独的 Power BI Desktop 文件中：

- 数据建模者和报表作者是不同的人。
- 据了解，模型将成为多个报表的源，无论是现在还是将来。

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="有三个 PBIX 文件。第一个文件只包含一个模型。其他两个仅包含报表，它们实时连接到 Power BI 服务中托管的模型。报表由不同的人开发。" border="true":::

数据建模人员仍可以使用 Power BI Desktop 报表创作体验来测试和验证其模型设计。 但是，在将文件发布到 Power BI 服务后，他们应从工作区中删除报表。 另外，他们必须记得在每次重新发布并覆盖数据集时删除报表。

### <a name="preserve-the-model-interface"></a>保留模型接口

有时，模型更改是不可避免的。 因此，数据建模者必须小心，不要破坏模型接口。 如果已破坏，则相关报表视觉对象或仪表板磁贴可能会损坏。 损坏的视觉对象显示为错误，它们可能导致报表作者和使用者感到不满。 更糟糕的是，它们可能会减少对数据的信任。

因此，请仔细管理模型更改。 如果可能，请避免以下更改：

- 重命名表、列、层次结构、层次结构级别或度量值。
- 修改列数据类型。
- 修改度量值表达式，以便返回不同的数据类型。
- 将度量值移动到其他主表。 这是因为移动一个度量值可能会破坏报表范围内的度量值，这些度量值使用主表名称完全限定。 我们不建议使用完全限定度量值名称编写 DAX 表达式。 有关详细信息，请参阅 [DAX：列和度量值引用](dax-column-measure-references.md)。

添加新表、列、层次结构、层次结构级别或度量值是安全的，但有一个例外：新的度量值名称可能与报表范围内的度量值名称冲突。 为了避免冲突，我们建议报表作者在报表中定义度量值时采用命名约定。 他们可以用下划线或其他字符为报表范围内的度量值名称加上前缀。

如果必须对模型进行中断性变更，我们建议：

- 在 Power BI 服务中[查看数据集的相关内容](../consumer/end-user-related.md#view-related-content-for-a-dataset)。
- 浏览 Power BI 服务中的[数据世系](../collaborate-share/service-data-lineage.md)视图。

利用这两种方案都可以快速识别任何相关的报表和仪表板。 数据世系视图可能是更好的选择，因为它很容易看到每个相关项目的联系人。 事实上，它是一个超链接，用于打开发送给联系人的电子邮件。

我们建议联系每个相关项目的所有者，让他们了解任何计划的中断性变更。 这样，他们就可以准备好修复和重新发布报表，帮助最大限度地减少停机时间和降低不满度。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [通过 Power BI Desktop 连接 Power BI 服务中的数据集](../connect-data/desktop-report-lifecycle-datasets.md)
- [查看 Power BI 服务中的相关内容](../consumer/end-user-related.md)
- [数据世系](../collaborate-share/service-data-lineage.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

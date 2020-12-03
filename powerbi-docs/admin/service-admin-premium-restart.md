---
title: 重启 Power BI 高级容量
description: 了解如何重启 Power BI 高级容量，以解决性能问题。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 367195e0e09bbfb7de20acfa71b8da9742664ca2
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413555"
---
# <a name="restart-a-power-bi-premium-capacity"></a>重启 Power BI 高级容量

作为 Power BI 管理员，你可能需要重启高级容量。 本文介绍如何重启容量，并解决有关重启和性能的几个问题。

## <a name="why-does-power-bi-provide-this-option"></a>为什么 Power BI 提供会此选项？

Power BI 使用户能够对大量数据执行复杂的分析。 遗憾的是，用户通过使用作业重载 Power BI 服务、编写过于复杂的查询、创建循环引用等可能会导致性能问题。

Power BI 共享容量通过对文件大小、刷新计划和服务的其他方面施加限制来提供对此类情况的一些保护。 相比之下，在 Power BI 高级容量中，大多数限制都会提高。 因此，具有错误 DAX 表达式或非常复杂模型的单个报表可能会导致显著的性能问题。 在处理问题时，报表可能会占用容量上的所有可用资源。 

Power BI 不断改进其保护高级容量用户免受此类问题的影响。 我们还允许管理员使用工具来分析容量何时负担过重以及原因。 有关详细信息，请参阅[简短培训课程](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be)和[长期培训课程](https://powerbi.tips/2018/07/)。 与此同时，你需要能够在发生重大问题时缓解这些问题。 缓解这些问题的最快方法是重启容量。

> [!NOTE]
> Power BI Premium 最近发布了 Premium 的新版本，名为 Premium Gen2，目前处于预览状态。 Preview Gen2 容量不需要重启，因此该功能在 Premium Gen2 中不可用。

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>重启过程是否安全？ 是否会丢失任何数据？

重启后，所有保存在容量上的数据、定义、报表和仪表板都保持完整。 如果你重启容量，正在进行的计划刷新和临时刷新在大多数情况下都会被刷新引擎暂时停止，然后又因 Power BI 中内置的刷新重试逻辑而重启。 当容量可用时，服务会尝试重试任何受影响的刷新。 在重启过程中，用户界面中的刷新状态可能不会更改。 

在重启过程中，与容量进行交互的用户将丢失未保存的工作。 在重启完成后，用户应刷新其浏览器。

## <a name="how-do-i-restart-a-capacity"></a>如何重启容量？

请按照以下步骤重启容量。

1. 在 Power BI 管理门户中，在“容量设置”选项卡上，导航到你的容量。 

1. 将“CapacityRestart”功能标志添加到容量 URL：`https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`。

1. 在“高级设置” > “容量重启”下，请选择“重启容量”  。

    ![重启容量](media/service-admin-premium-restart/restart-capacity.png)

1. 在“容量重启”对话框中，请选择“是，重启容量”。

    ![确认重启](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>如何防止问题再次发生？

防止出现问题的最佳方法是使用户了解有效的数据建模。 有关详细信息，请参阅[培训课程](https://powerbi.tips/2018/07/)。

另外建议定期[监视容量](service-admin-premium-monitor-capacity.md)，以查找表明潜在问题的趋势。 我们计划定期发布监视应用和其他工具，以便你可以更高效地监视和管理容量。

## <a name="next-steps"></a>后续步骤

[什么是 Power BI Premium？](service-premium-what-is.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

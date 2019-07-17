---
title: 基于来自不同工作区的数据集创建报表（预览） - Power BI
description: 了解如何与整个组织的用户共享数据集。 然后，他们可以在其工作区中基于你的数据集生成报表。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f8229c74a233d8bc44370380bf635527506194f0
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567443"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces-preview"></a>基于来自不同工作区的数据集创建报表（预览）

了解如何根据其他工作区中的数据集在自己的工作区中创建报表。 要基于现有数据集生成报表，可从 Power BI Desktop 或 Power BI 服务的“我的工作区”或[新的体验工作区](service-create-the-new-workspaces.md)中开始。

- 在 Power BI 服务中：“获取数据” > “已发布数据集”   。
- 在 Power BI Desktop 中：“获取数据” > “Power BI 数据集”   。

    ![连接到现有数据集](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
在这两种情况下，数据集发现体验都在此对话框中开始：“选择数据集以创建报表”  。 可以看到你有权访问的所有数据集，无论它们位于何处：

![选择一个数据集](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

你会注意到第一个数据集已标记为“已推广”  。 本文后面部分的[查找已认可数据集](#find-an-endorsed-dataset)中将对此进行介绍。

你在此列表中看到的数据集至少满足以下条件之一：

- 数据集位于其中一个新的体验工作区，你是该工作区的成员。 请参阅[注意事项和限制](service-datasets-across-workspaces.md#considerations-and-limitations)。
- 你对位于新的体验工作区中的数据集具有“生成”权限。
- 该数据集位于“我的工作区”中。

> [!NOTE]
> 如果你是免费用户，则只能看到“我的工作区”中的数据集，或者“高级容量”工作区中你对其具有“生成”权限的数据集。

单击“创建”时，将创建与该数据集的实时连接，并可以使用完整的可用数据集打开报表创建体验  。 尚未创建数据集的副本。 数据集仍位于其原始位置。 可以使用数据集中的所有表和度量值来生成自己的报表。 数据集上应用了行级别安全性 (RLS) 限制，因此你只能根据 RLS 角色查看有权查看的数据。

可以将报表保存到 Power BI 服务中的当前工作区，或者从 Power BI Desktop 将报表发布到工作区。 如果报表基于工作区外的数据集，Power BI 会自动在数据集列表中创建一个条目。 此数据集的图标与工作区中数据集的图标不同： ![共享数据集图标](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

这样，工作区的成员可以区分哪些报表和仪表板使用工作区外的数据集。 该条目显示有关数据集的信息以及一些选择操作。

![数据集操作](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>查找已认可数据集

有两种不同类型的已认可数据集。 数据集所有者可以推广他们向你推荐的数据集  。 此外，Power BI 租户管理员可以指定组织中的专家，他们可以验证  数据集供所有人使用。 查找数据集时可看到已推广和已验证数据集显示的徽章，这些徽章显示在工作区的数据集列表中  。 在数据集发现体验期间，验证数据集的人员的名称显示在工具提示中；将鼠标悬停在“认证”  标签上将看到它。

- 在 Power BI 服务中：“获取数据” > “已发布数据集”   。
- 在 Power BI Desktop 中：“获取数据” > “Power BI 数据集”   。

    在“选择数据集”对话框中，默认情况下，已认可的数据集位于列表顶部  。 

    ![已推广的数据集](media/service-datasets-certify-promote/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>后续步骤

- [跨工作区使用数据集（预览）](service-datasets-across-workspaces.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

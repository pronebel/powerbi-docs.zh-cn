---
title: 从其他工作区复制报表（预览） - Power BI
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
ms.openlocfilehash: 2db4c23b50071e387913ed79b4d01daeafb928a4
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567370"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>从其他工作区复制报表（预览）

在工作区或应用中找到自己喜欢的报表时，你可以复制它，然后将其保存到不同工作区。 然后，你可以修改该报表，添加或删除视觉对象和其他元素。 无需担心如何创建数据模型。 它已为你创建。 修改现有报表比从头开始创建要容易得多。 但是，不能从新工作区的应用中发布报表副本。 请参阅“跨工作区使用数据集”一文中的其他[注意事项和限制](service-datasets-across-workspaces.md#considerations-and-limitations)列表。

## <a name="save-a-copy-of-a-report"></a>保存报表的副本

1. 在应用或工作区中，转到“报表”列表视图。

1. 在“操作”下，选择“保存副本”   。

    ![保存报表的副本](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    只有当报表位于新的体验工作区且你具有[生成权限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)时，你才会看到“保存副本”图标  。 即使你有权访问工作区，也必须具有数据集的“生成”权限。

3. 在“保存此报表的副本”中，为报表提供名称并选择目标工作区  。

    ![“保存副本”对话框](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    可以将报表保存到当前工作区或 Power BI 服务中的其他工作区。 你只看到新的体验工作区，而你是其中的一名成员。
  
4. 选择**保存**。

    保存报表副本时，将创建与该数据集的实时连接，并且可以使用完整的可用数据集打开报表创建体验。 尚未创建数据集的副本。 数据集仍位于其原始位置。 可以在自己的报表中使用数据集中的所有表和度量值。 数据集上应用了行级别安全性 (RLS) 限制，因此你只能根据 RLS 角色查看有权查看的数据。

    如果报表基于工作区外的数据集，Power BI 会自动在数据集列表中创建一个条目。 此数据集的图标与工作区中数据集的图标不同： ![共享数据集图标](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    这样，工作区的成员可以区分哪些报表和仪表板使用工作区外的数据集。 该条目显示有关数据集的信息以及一些选择操作。

    ![数据集操作](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>查看相关数据集

当你在工作区中有报表时，可能需要知道它所基于的数据集。

1. 在“报表”列表视图中，选择“查看相关项”  。

    ![相关视图图标](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. “相关内容”对话框显示所有相关项  。 在此列表中，数据集与任何其他数据集类似。 你无法判断它位于不同的工作区。 这是一个已知问题。
 
    ![“相关内容”对话框](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>删除报表及其共享数据集

你可能决定不再需要工作区中的报表及其关联的共享数据集。

1. 删除报表。 在工作区的报表列表中，选择“删除”  图标。

    ![删除报表图表](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. 在数据集列表中，可以看到共享数据集没有“删除”  图标。 刷新页面，或转到其他页，然后返回。 数据集将消失。 如果没有，请查看“相关视图”  。 它可能与工作区中的另一个表相关。

    ![相关视图图标](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > 删除此工作区中的共享数据集不会删除数据集。 它只是删除对它的引用。


## <a name="next-steps"></a>后续步骤

- [跨工作区使用数据集（预览）](service-datasets-across-workspaces.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

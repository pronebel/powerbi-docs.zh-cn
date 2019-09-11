---
title: 共享数据集（预览）
description: 作为数据集所有者，你可以创建和共享数据集，以便其他人使用。 了解如何使用生成权限来控制有权访问数据的人选。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/14/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c5b880132255fbdf37996273dc6c70029e548df6
ms.sourcegitcommit: 4a3afe761d2f4a5bd897fafb36b53961739e8466
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69654895"
---
# <a name="share-a-dataset-preview"></a>共享数据集（预览）

作为 Power BI Desktop 中数据模型的创建者，你可以在 Power BI 服务中将其作为数据集共享   。 之后报表创建者就可以轻松发现和重用你共享的数据集。 了解如何共享数据集，以及如何使用生成权限来控制有权访问数据的人选。

## <a name="steps-to-sharing-your-dataset"></a>共享数据集的步骤

1. 首先在 Power BI Desktop 的数据模型中创建 .pbix 文件。 如果计划为其他人提供此数据集来生成报表，你甚至可能无需在 .pbix 文件中设计报表。

    最佳做法是将 .pbix 文件保存到 Office 365 组。

1. 将 .pbix 文件发布到 Power BI 服务中的[新的体验工作区](service-create-the-new-workspaces.md)。
    
    完成后，此工作区的其他成员可以在基于此数据集的其他工作区中创建报表。

1. 也可以通过此工作区[发布应用](service-create-distribute-apps.md)。 进行创建时，在“权限”页上指定具有权限的人选及其权限范围  。

    > [!NOTE]
    > 如果选择“整个组织”，则组织中的所有人都将不具生成权限  。 这是一个已知问题。 应转而在“特定个人或组”中指定电子邮件地址  。  如果想要整个组织都具有生成权限，请指定整个组织的电子邮件别名。

    ![设置应用权限](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. 选择“发布应用”，或如果应用已发布则选择“更新应用”   。

## <a name="build-permissions-for-shared-datasets"></a>共享数据集的生成权限

生成权限类型只与数据集相关。 借助它，用户可以在数据集上生成报表、仪表板、问答的固定磁贴和 Insights 发现等新内容。 他们还可基于 Power BI 以外的数据集生成新内容（例如通过“在 Excel 中分析”、XMLA 和“导出”基础数据生成的 Excel 表）。

用户可通过不同方式获得生成权限：

- 如果你是至少具有“参与者”角色的工作区的成员，则自动拥有数据集的“生成”权限以及复制报表的权限。
 
- 数据集所在的工作区中的成员可以在“权限中心”将权限分配给特定用户或安全组。 选择数据集旁边的省略号 (...) >“管理权限”  。

    ![选择省略号](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    此操作将打开该数据集的“权限中心”，你可以在其中设置和更改权限。

    ![权限中心](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- 数据集所在的工作区中的管理员或成员可以在应用发布期间决定，具有应用权限的用户也可以获得底层数据集的生成权限。 若要获取详细信息，请参阅本文中的[共享数据集的步骤](#steps-to-sharing-your-dataset)。

- 假设你在数据集上具有重新共享和生成权限。 共享基于该数据集生成的报表或仪表板时，你可以指定收件人也可以获得底层数据集的生成权限。

    ![生成权限](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

你可以删除个人拥有的数据集“生成”权限。 如果你删除，他们仍然可以查看基于共享数据集的报表，但不能再进行编辑。

## <a name="more-granular-permissions"></a>更细粒度的权限

Power BI 在 2019 年 6 月引入了生成权限，将其作为现有权限（读取和重新共享）的补充。 已在当时通过应用权限、共享或工作区访问获得数据集读取权限的用户也都获得了上述数据集的生成权限。 他们自动获得了生成权限，因为他们可以凭借读取权限来使用“在 Excel 中分析”或“导出”在数据集上生成新内容。

凭借这个更细粒度的生成权限，你可以选择仅可查看现有报表或仪表板中内容的人选，和可创建与底层数据集相连内容的人选。

如果数据集工作区之外的报表在使用你的数据集，则你无法删除该数据集。 而是会看到一条错误消息。

你可以删除生成权限。 如果删除，权限遭到撤消的人员仍可查看报表，但无法再编辑报表和导出基础数据。 具有只读权限的用户仍可导出汇总数据。 

## <a name="track-your-dataset-usage"></a>跟踪数据集使用情况

你在你的工作区中具有共享数据集时，你可能需要知道其他工作区中的基于该共享数据集的报表。

1. 在“数据集”列表视图中，选择“查看相关项”  。

    ![相关视图图标](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. “相关内容”对话框显示所有相关项  。 在此列表中，你可以查看此工作区和“其他工作区”中的相关项  。
 
    ![“相关内容”对话框](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>后续步骤

- [跨工作区使用数据集（预览）](service-datasets-across-workspaces.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

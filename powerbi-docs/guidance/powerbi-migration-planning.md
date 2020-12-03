---
title: 规划与迁移到 Power BI 相关的部署
description: 有关迁移到 Power BI 时规划部署的指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: f161819b6e26c197bacc5534b5abfb426d612624
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419213"
---
# <a name="plan-deployment-to-migrate-to-power-bi"></a>规划与迁移到 Power BI 相关的部署

本文介绍 **阶段 2**，其中涉及规划单个 Power BI 解决方案的迁移。

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="显示了 Power BI 迁移各阶段的图像。本文重点介绍阶段 2。":::

> [!NOTE]
> 有关上图的完整说明，请参阅 [Power BI 迁移概述](powerbi-migration-overview.md)。

阶段 2 的重点是定义如何利用阶段 1 中定义的要求将解决方案迁移到 Power BI。

阶段 2 的输出包含尽可能多的特定决策，用于指导部署过程。

此决策制定过程是一个非线性的迭代过程。 [迁移前的步骤](powerbi-migration-pre-migration-steps.md)中已进行了一些规划。 从概念证明中了解信息（在[阶段 3](powerbi-migration-proof-of-concept.md) 中进行了描述）可能会与部署的规划同时进行。 即使在创建解决方案时（在[阶段 4](powerbi-migration-create-validate-content.md) 中进行了描述），也可能出现影响部署决策的其他信息。

> [!IMPORTANT]
> 阶段 1-5 表示与一个特定解决方案相关的活动。 组织/租户级别有一些决策和活动会影响解决方案级别的进程。 [Power BI 迁移概述](powerbi-migration-overview.md)一文中介绍了其中一些较高级别的计划活动。 适当时，应遵从组织级别的决策以提高效率和一致性。

> [!TIP]
> 本文中讨论的主题也适用于标准 Power BI 实现项目。

## <a name="choose-power-bi-product"></a>选择 Power BI 产品

首先要做出的决策之一是选择 Power BI 产品。 就是在 [Power BI 服务](../fundamentals/power-bi-service-overview.md)和 [Power BI 报表服务器](../report-server/get-started.md)中做选择。 内容发布后，便可以使用许多其他选项，例如嵌入、移动交付和电子邮件订阅。

有关体系结构注意事项的详细信息，请参阅 [规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)的 **第 3 部分**。

> [!CAUTION]
> 如果你想依赖于使用存储在文件系统中的 Power BI Desktop 文件，请注意，这并不是最佳方法。 Power BI 服务（或 Power BI 报表服务器）在安全性、内容分发和协作方面具有明显的优势。 Power BI 服务还提供审核和监视活动的功能。

## <a name="decide-on-workspace-management-approach"></a>确定工作区管理方法

[工作区](../collaborate-share/service-new-workspaces.md)是 Power BI 服务的核心概念，这使得工作区管理成为规划的一个重要方面。 相关问题包括：

- 此新解决方案是否需要新的工作区？
- 是否需要部署单独的工作区来分别满足开发、测试和生产的需要？
- 是将单独的工作区分别用于数据和报表，还是使用一个工作区就足够了？ 分别部署单独的工作区具有很多优点，尤其是在保护数据集方面。 必要时，可以将它们与发布报表的用户分开管理。
- 工作区的安全性要求是什么？ 它会影响[工作区角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)的规划。 如果某个应用将由内容使用者使用，则[该应用的权限](../collaborate-share/service-create-distribute-apps.md#publish-your-app)与工作区分开管理。 为应用查看者提供不同权限为满足报表或仪表板的只读使用者的安全性要求提供了更大的灵活性。
- 是否可使用现有组保护新内容？ Azure Active Directory 和 Microsoft 365 组均受支持。 如果与现有流程保持一致，相比分配给单个用户，使用群组可使权限管理更轻松。
- 是否有与外部来宾用户相关的安全注意事项？ 可能需要与 Azure Active Directory 管理员和 Power BI 管理员协作配置[来宾用户访问](../admin/service-admin-azure-ad-b2b.md)。

> [!TIP]
> 考虑为特定业务活动或项目创建一个工作区。 你可能会想根据组织结构（例如每个部门一个工作区）构建工作区，但这种方法常常会导致工作区范围设置太过宽泛。

## <a name="determine-how-content-will-be-consumed"></a>确定如何使用内容

了解解决方案使用者更喜欢如何查看报表和仪表板是非常有帮助的。 相关问题包括：

- [Power BI 应用](../consumer/end-user-apps.md)（由来自单个工作区的报表和仪表板组成）是否是将内容交付给使用者的最佳方式，还是说直接访问工作区对内容查看者而言已经足够？
- 是否会将某些报表和仪表板嵌入到其他位置，例如 [Teams](../collaborate-share/service-embed-report-microsoft-teams.md)、[SharePoint Online](../collaborate-share/service-embed-report-spo.md) 或[安全门户或网站](../collaborate-share/service-embed-secure.md)？
- 使用者会使用[移动设备](../consumer/mobile/mobile-apps-for-mobile-devices.md)访问内容吗？ 将报表交付到小型设备的要求会影响某些[报表设计决策](../create-reports/desktop-create-phone-report.md)。

## <a name="decide-if-other-content-may-be-created"></a>确定是否可以创建其他内容

关于使用者创建新内容，需要做出几个关键决策，如：

- 是否允许使用者从已发布的数据集创建新报表？ 可以通过向用户分配数据集[生成权限](../connect-data/service-datasets-build-permissions.md)来启用此功能。
- 如果使用者想自定义报表，是否可以[保存副本](../connect-data/service-datasets-copy-reports.md)并对其进行个性化以满足他们的需要？

> [!CAUTION]
> 尽管 _保存副本_ 功能是一项不错的功能，但当报表包含某些图形或页眉/页脚消息时，应谨慎使用。 由于徽标、图标和文本消息通常与品牌要求或法规遵从性有关，应务必谨慎控制其交付和分发的方式。 如果使用了 _保存副本_ 功能，但新作者未更改原始图形或页眉/页脚消息，则可能导致无法确认实际生成报表的人员。 这还可能降低品牌标识的意义。

## <a name="evaluate-needs-for-premium-capacity"></a>评估对高级容量的需求

当工作区存储在[高级容量](../admin/service-premium-what-is.md)上时，有更多可以使用的功能。 以下是为什么高级容量上的工作区具有优势的几个原因：

- 不具有 Power BI 专业许可证的使用者可以访问内容。
- 支持大型数据集。
- 支持更频繁地刷新数据。
- 支持使用完整的数据流功能集。
- 企业功能，包括部署管道和 XMLA 终结点。
- 支持分页报表（当启用了工作负载时）。

## <a name="determine-data-acquisition-method"></a>确定数据采集方法

报表所需的数据可能会影响几个决定。 相关问题包括：

- 是否可以使用现有的 Power BI [共享数据集](../connect-data/service-datasets-share.md)，还是为该解决方案创建新 Power BI 数据集更合适一些？
- 是否需要使用新数据或度量值来扩充现有共享数据集来满足更多需求？
- 哪种[数据存储模式](../transform-model/desktop-storage-mode.md)最合适？ 选项包括导入、DirectQuery、复合或实时连接。
- 是否应使用[聚合](../transform-model/desktop-aggregations.md)来提高查询性能？
- 创建[数据流](../transform-model/dataflows/dataflows-introduction-self-service.md)会有用吗，它可以充当众多数据集的源吗？
- 是否需要注册新的[网关数据源](../connect-data/service-gateway-data-sources.md)？

## <a name="decide-where-original-content-will-be-stored"></a>确定原始内容的存储位置

除了规划目标部署目标之外，规划原始内容或源内容的存储位置也很重要，例如：

- 为原始 Power BI Desktop (.pbix) 文件指定一个经过批准的存储位置。 理想情况下，只有编辑相关内容的人员能够访问此位置。 它应与在 Power BI 服务中设置安全性的方式一致。
- 为包含版本历史记录或源代码管理的原始 Power BI Desktop 文件指定一个位置。 如有必要，内容作者可通过版本控制恢复到以前的文件版本。 可利用 OneDrive for Business 或 SharePoint 很好地实现此目的。
- 为非集中源数据（例如平面文件或 Excel 文件）指定一个经过批准的存储位置。 任何数据集作者都应能够正常访问此路径而不会出错，并应进行定期备份。
- 为从 Power BI 服务导出的内容指定一个经过批准的位置。 目标是确保不会无意中破坏在 Power BI 服务中定义的安全性。

> [!IMPORTANT]
> 当原始 Power BI Desktop 文件包含导入的数据时，为其指定受保护的位置尤为重要。

## <a name="assess-the-level-of-effort"></a>评估投入量

只要可以从需求信息（在[阶段 1](powerbi-migration-requirements.md) 中进行了描述）和解决方案部署规划过程中获取到足够的信息，现在就可以评估投入水平。 然后就可以制定包含任务、时间表和职责信息的项目计划。

> [!TIP]
> 在大多数组织中，劳动力成本（薪金和报酬）通常是最大的支出之一。 尽管可能难以准确估算，但提高生产率可以带来极佳的投资回报 (ROI)。

## <a name="next-steps"></a>后续步骤

在本 [Power BI 迁移系列的下一篇文章](powerbi-migration-proof-of-concept.md)中，了解阶段 3，该阶段与进行概念证明以在迁移到 Power BI 时降低风险并尽早解决未知问题有关。

其他有用的资源包括：

- [Microsoft 的 BI 转换](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [规划 Power BI 企业部署白皮书](https://aka.ms/PBIEnterpriseDeploymentWP)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

有经验的 Power BI 合作伙伴可帮助你的组织成功完成迁移过程。 若要加入 Power BI 合作伙伴，请访问 [Power BI 合作伙伴门户](https://powerbi.microsoft.com/partners/)。
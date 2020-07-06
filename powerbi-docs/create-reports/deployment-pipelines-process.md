---
title: 部署管道过程
description: 了解 Power BI 部署管道过程
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 06/25/2020
ms.openlocfilehash: fc7e6aa751bab6562e097b8ce14ff8416e6231e7
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85782558"
---
# <a name="understand-the-deployment-process-preview"></a>了解部署过程（预览版）

通过部署过程，可以将管道中一个阶段的内容克隆到另一个阶段，这通常是从开发到测试，以及从测试到生产。

在部署过程中，Power BI 将当前阶段的内容复制到目标中。 复制过程中将保留复制的项之间的连接。 Power BI 还将配置的数据集规则应用于目标阶段中更新的内容。 部署内容可能需要一些时间，具体取决于要部署的项数。 在此期间，可以导航到 Power BI 门户中的其他页面，但不能使用目标阶段中的内容。

## <a name="deploying-content-to-an-empty-stage"></a>将内容部署到空阶段

将内容部署到空阶段时，会将要从中部署的工作区中的报表、仪表板和数据集的元数据复制到要部署到的阶段。 部署到的阶段的新工作区是在高级容量上创建的。

有两种方法可以将内容从一个阶段部署到下一个阶段。 可以部署所有内容，也可以[选择要部署的内容项](deployment-pipelines-get-started.md#selective-deployment)。

你还可以将内容从部署管道中的后一阶段反向部署到前一阶段。

部署完成后，刷新数据集，以便可以使用新复制的内容。 数据集刷新是必需的，因为数据不会从一个阶段复制到另一个阶段。 若要了解在部署过程中会复制哪些项属性以及不会复制哪些项属性，请查看[在部署期间复制的项属性](#item-properties-copied-during-deployment)部分。

### <a name="creating-a-premium-capacity-workspace"></a>创建高级容量工作区

在首次部署过程中，部署管道检查是否有高级容量权限。  

如果具有容量权限，则工作区的内容将复制到要部署到的阶段，并在高级容量上创建该阶段的新工作区。

如果没有容量权限，则会创建工作区，但不会复制内容。 你可以要求容量管理员将工作区添加到容量，或者要求提供容量的分配权限。 稍后，在将工作区分配到容量时，可以将内容部署到此工作区。

### <a name="workspace-and-content-ownership"></a>工作区和内容所有权

部署用户自动成为克隆数据集的数据集所有者，以及新工作区的唯一管理员。

## <a name="deploy-content-to-an-existing-workspace"></a>将内容部署到现有工作区

将工作生产管道中的内容部署到具有现有工作区的阶段，包括以下内容：

* 将新内容作为补充部署到已包含内容的阶段。

* 部署了新内容以替换当前工作阶段中的旧内容。

### <a name="deployment-process"></a>部署过程

当前阶段中的内容将复制到目标阶段。 Power BI 标识目标阶段中的现有内容并覆盖它。 若要确定需要覆盖哪个内容项，部署管道将使用父项与其克隆之间的连接。 当创建新内容时，将保留此连接。 覆盖操作仅覆盖项的内容。 项的 ID、URL 和权限保持不变。

在目标阶段中，[未复制的项属性](deployment-pipelines-process.md#item-properties-that-are-not-copied)在部署前后没有变化。 新内容和新项将从当前阶段复制到目标阶段。

### <a name="refreshing-the-dataset"></a>刷新数据集

如果可能，将保留目标数据集中的数据。 如果没有对数据集进行更改，则数据在部署前后没有变化。

进行较小的更改（例如，添加表或度量值）后，Power BI 会保留原始数据，而刷新会经过优化，以便仅刷新所需的内容。 对于重大的架构更改或数据源连接中的更改，需要完全刷新。

### <a name="requirements-for-deploying-to-a-stage-with-an-existing-workspace"></a>部署到具有现有工作区的阶段的要求

只要部署的内容驻留在[高级容量](../admin/service-premium-what-is.md)上，满足以下条件的用户就可以将其部署到具有现有工作区的阶段：

* 属于源和目标部署阶段中的工作区的成员的任何 [Pro 用户](../admin/service-admin-purchasing-power-bi-pro.md)。

* 要部署的目标工作区中所有数据集的所有者。

有关详细信息，请查看[权限](#permissions)部分。

## <a name="deployed-items"></a>部署的项

将内容从一个管道阶段部署到另一个管道阶段时，复制的内容包含以下 Power BI 项：

* 数据集

* 报表

* 仪表板

### <a name="unsupported-items"></a>不支持的项

部署管道不支持以下项：

* 不是源自 .pbix 的数据集

* 基于不支持的数据集的报表

* 工作区不能使用模板应用

* 分页报表

* 数据流

* 推送数据集

* 工作簿

## <a name="item-properties-copied-during-deployment"></a>部署期间复制的项属性

在部署期间，将复制以下项属性，并覆盖目标阶段的项属性：

* 数据源（支持[数据集规则](deployment-pipelines-get-started.md#step-4---create-dataset-rules)）

* 参数（支持[数据集规则](deployment-pipelines-get-started.md#step-4---create-dataset-rules)）

* 报表视觉对象

* 报表页

* 在推入数据时

* 模型元数据

* 项关系

### <a name="item-properties-that-are-not-copied"></a>未复制的项属性

在部署期间，不会复制以下项属性：

* 数据 - 不会复制数据，仅复制元数据

* URL

* ID

* 权限 - 对于工作区或特定项

* 工作区设置 - 每个阶段都有其自己的工作区

* 应用内容和设置 - 若要部署应用，请参阅[部署 Power BI 应用](#deploying-power-bi-apps)

在部署期间，也不会复制以下数据集属性：

* 角色分配
    
* 刷新计划
    
* 数据源凭据
    
* 查询缓存设置（可从容量继承）
    
* 认可设置

## <a name="deploying-power-bi-apps"></a>部署 Power BI 应用

[Power BI 应用](../consumer/end-user-apps.md)是将内容分发到免费 Power BI 使用者的建议方法。 使用部署管道，可以在部署管道中管理 Power BI 应用，以便在到达应用生命周期时获得更多控制和灵活性。

为每个部署管道阶段创建应用，以便可以从最终用户的角度测试每个应用更新。 部署管道可以轻松管理此过程。 使用工作区卡中的“发布”或“查看”按钮，在特定管道阶段中发布或查看应用。

[![发布应用](media/deployment-pipelines-process/publish.png "发布应用")](media/deployment-pipelines-process/publish.png#lightbox)

在生产阶段中，左下角的“主操作”按钮会在 Power BI 中打开“更新应用”页，以便任何内容更新可供应用用户使用。

[![更新应用](media/deployment-pipelines-process/update-app.png "更新应用")](media/deployment-pipelines-process/update-app.png#lightbox)

>[!IMPORTANT]
>部署过程不包括更新应用内容或设置。 若要应用对内容或设置的更改，需要在所需的管道阶段手动更新应用。

## <a name="permissions"></a>权限

管道权限和工作区权限是单独授予和管理的。 例如，具有不包含工作区权限的管道访问权限的用户能够查看管道并将其与其他人共享。 但是，此用户将无法在管道或工作区页中查看工作区的内容，并且无法执行部署。

### <a name="user-with-pipeline-access"></a>具有管道访问权限的用户

具有管道访问权限的用户具有以下权限：

* 查看管道
    
* 与其他人共享管道
    
* 编辑和删除管道

>[!NOTE]
>管道访问权限不会授予查看操作或对工作区内容执行操作的权限。

### <a name="workspace-viewer"></a>工作区查看器

具有管道访问权限的工作区查看者还可以执行以下操作：

* 使用者内容

>[!NOTE]
>工作区查看者无法访问数据集或编辑工作区内容。

### <a name="workspace-contributor"></a>工作区参与者

具有管道访问权限的工作区参与者还可以执行以下操作：

* 使用者内容

* 比较阶段

* 查看数据集

### <a name="workspace-member"></a>工作区成员

具有管道访问权限的工作区成员还可以执行以下操作：

* 查看工作区内容
    
* 比较阶段
    
* 部署报表和仪表板

* 删除工作区

### <a name="workspace-admin"></a>工作区管理员

具有管道访问权限的工作区管理员可以执行工作区成员操作，还可以执行以下操作 ：

* 分配工作区

* 删除工作区

### <a name="dataset-owner"></a>数据集所有者

作为工作区成员或管理员的数据集所有者还可以执行以下操作：

* 更新数据集
    
* 配置规则

>[!NOTE]
>本部分介绍部署管道中的用户权限。 本部分中列出的权限可能在其他 Power BI 功能中具有不同的应用程序。

## <a name="limitations"></a>限制

本部分列出了部署管道中的大部分限制。

* 工作区必须位于 [高级容量](../admin/service-premium-what-is.md)上。

* 无法部署具有 Power BI [敏感度标签](../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi)的 Power BI 项（如报表和仪表板）。

* 单个部署中可部署的 Power BI 项数上限为 300。

* 有关工作区限制的列表，请参阅[工作区分配限制](deployment-pipelines-get-started.md#workspace-assignment-limitations)。

* 有关不支持的项的列表，请参阅[不支持的项](#unsupported-items)。

### <a name="dataset-limitations"></a>数据集限制

* 无法部署使用[增量刷新](../admin/service-premium-incremental-refresh.md)配置的数据集。

* 无法部署使用实时数据连接的数据集。

* 在部署期间，如果目标数据集使用[实时连接](../connect-data/desktop-report-lifecycle-datasets.md)，则源数据集也必须使用此连接模式。

* 部署之后，不支持下载数据集（从其部署到的阶段）。

* 有关数据集规则限制的列表，请参阅[数据集规则限制](deployment-pipelines-get-started.md#dataset-rule-limitations)。

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[部署管道简介](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[部署管道最佳实践](deployment-pipelines-best-practices.md)

>[!div class="nextstepaction"]
>[开始使用部署管道](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[解决部署管道问题](deployment-pipelines-troubleshooting.md)
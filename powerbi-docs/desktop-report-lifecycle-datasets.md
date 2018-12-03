---
title: 通过 Power BI Desktop 连接 Power BI 服务中的数据集
description: 将通用数据集用于多个 Power BI Desktop 报表，并管理报表生命周期
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3679a2f3ab98e1f54ead364e4ef4bf65d382a9d5
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578580"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>通过 Power BI Desktop 连接 Power BI 服务中的数据集
可以与 Power BI 服务中的共享数据集建立实时连接，并根据同一数据集创建多个不同的报表。 也就是说，可以在 Power BI Desktop 中创建理想的数据模型，将其发布到 Power BI 服务中，然后你和其他人可以根据同一通用数据模型创建多个不同的报表（独立的 .pbix 文件）。 此功能称为“Power BI 服务实时连接”。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

此功能具有诸多优势（包括用作最佳做法），本文将对此进行介绍。 也存在一些注意事项和限制。因此，请务必仔细阅读本文结尾部分介绍的注意事项和限制。

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>使用 Power BI 服务实时连接管理报表生命周期
Power BI 的普及带来了一个问题，就是报表、仪表板及其基础数据模型激增。 如此普及的原因在于，可以轻松地在 **Power BI Desktop** 中创建富有吸引力的报表，然后将其共享（[发布](desktop-upload-desktop-files.md)）到 **Power BI 服务**中，并能通过这些数据集创建精彩的仪表板。 由于许多人都这么做（通常使用的是同一个（或几乎相同的）数据集），因此确定报表是以哪个数据集为依据且每个数据集的新近度就变得很困难。 为了应对这一挑战，我们提供了 **Power BI 服务实时连接**功能，以便你可以更轻松、一致地创建、共享和扩展通用数据集报表和仪表板。

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>创建并共享所有人都可以使用的数据集
假设 Anna 是一名业务分析师，同时也是你团队中的一员，她非常擅长创建优质数据模型（通常称为“数据集”）。 借助她自己的专业知识，Anna 可以创建数据集和报表，然后将报表共享到 **Power BI 服务**中。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

每个人都很喜欢她的报表和数据集，而问题也随之而来。团队中的每个人都会尝试根据她的数据集创建自己的版本，然后将他们自己的报表与团队共享。 在 **Power BI 服务**中，你团队的工作区中突然之间就出现了大量报表（以不同的数据集为依据）。 哪一个是最新的？ 这些数据集是完全相同，还只是大致相同？ 区别在哪里？ 借助 **Power BI 服务实时连接**功能，一切都会有所改善。 在下一部分中，我们将了解其他人如何将 Anna 发布的数据集用于自己的报表，以及所有人如何使用同一个已发布且经过审核的可靠数据集来生成自己独一无二的报表。

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>使用实时连接功能连接 Power BI 服务数据集
创建自己的报表（及其依据的数据集）后，Anna 将报表发布到 **Power BI 服务**中，此报表显示在 Power BI 服务中她团队的工作区内。 现在，她的工作区中的每个人都可以查看并使用此报表。

若要了解有关工作区的详细信息，请参阅[应用工作区](service-create-workspaces.md)。

她的工作区中的其他成员现在可以与 Anna 共享的数据模型建立实时连接（使用 **Power BI 服务实时连接**功能），并根据她的原始数据集创建自己独一无二的报表。

下图展示了 Anna 是如何创建一个 **Power BI Desktop** 报表，并将其（包括它的数据模型）发布到 **Power BI 服务**中的。 然后，她的工作区中的其他成员可以使用 **Power BI 服务实时连接**功能连接她的数据模型，并根据她的数据集创建自己独一无二的报表。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> 数据集只在一个工作区中进行共享。 要连接的数据集必须位于你所属的共享工作区中，才能建立 Power BI 服务实时连接。
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>使用 Power BI 服务实时连接的分步流程
至此，我们已经了解 **Power BI 服务实时连接**是多么实用，以及如何将此功能用作管理报表生命周期的最佳做法。接下来，我们逐步了解如何将 Anna 的优质报表（和数据集）变成她的 Power BI 工作区中的同事可以使用的共享数据集。

### <a name="publish-a-power-bi-report-and-dataset"></a>发布 Power BI 报表和数据集
使用 **Power BI 服务实时连接**管理报表生命周期的第一步是，创建并共享同事想要使用的报表（和数据集）。 因此，Anna 必须先从 Power BI Power BI Desktop 发布她的报表。 为此，她在 Power BI Desktop 的“开始”功能区中选择“发布”。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

如果尚未登录 Power BI 服务帐户，系统将会提示她登录。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

随后，她可以选择要将报表和数据集发布到的目标工作区。 请注意，只有有权访问报表发布到的工作区的成员才能使用 **Power BI 服务实时连接**访问报表的数据集。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

此时便会开始发布，**Power BI Desktop** 会显示发布进度。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

完成后，**Power BI Desktop** 会提示发布成功，并显示两个链接，一个链接用于转到 **Power BI 服务**访问报表本身，另一个链接用于获取有关报表的**快速见解**。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

接下来，让我们来看一下有权访问报表（和数据集）发布到的工作区的其他同事如何连接数据集并生成自己的报表。

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>与已发布的数据集建立 Power BI 服务实时连接
若要与已发布的报表建立连接，并根据已发布的数据集创建自己的报表，请在 **Power BI Desktop** 的“开始”功能区中依次选择“获取数据”和“Power BI 服务”。 也可以依次选择“获取数据”>“联机服务”>“Power BI 服务”。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_08.png)

如果尚未登录 Power BI，系统将会提示你登录。 登录后，便会看到一个窗口，其中显示你所属的工作区，你可以选择包含要与其建立 **Power BI 服务实时连接**的数据集的工作区。

工作区旁边括号中的数字表示相应工作组中有多少个共享数据集，选择左侧的三角形可以展开工作区并选择共享数据集。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_09a.png)

对于上面的 **Power BI 服务**实时连接窗口，需要注意下面几点事项：

* 可以搜索共享数据集，但搜索结果范围仅限于展开的工作区，不会搜索未展开的任何工作区。
* 可以展开多个工作区来扩大搜索范围。

选择窗口中的“加载”后，便与所选的数据集建立了实时连接。也就是说，所看到的数据（字段及其值）已实时加载到 **Power BI Desktop** 中。

![](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

现在，你（和其他人）可创建并共享自定义报表，且所有操作均基于同一数据库。 让一个拥有丰富专业知识的人创建格式正确的数据集（就像 Anna 所做），然后允许很多同事使用此共享数据集创建他们自己的报表，不失为一种很好的方法。

> [!NOTE]
> 当基于使用与 Power BI 服务实时连接的数据集创建报表时，只能将该报表发布到包含所使用数据集的同一 Power BI 服务工作区。
> 
> 

## <a name="limitations-and-considerations"></a>限制和注意事项
使用 Power BI 服务实时连接时，需要遵循几项限制和注意事项。

* 工作区的只读成员无法连接到 Power BI Desktop 中的数据集。
* 只有属于同一个 **Power BI 服务**工作区的用户，才能使用 **Power BI 服务实时连接**功能连接已发布的数据集。 用户可以属于多个工作区（通常情况下确实如此）。
* 由于这是实时连接，因此禁用左导航和建模，与连接 **SQL Server Analysis Services** 时的行为相似。
* 由于这是实时连接，因此将强制执行 RLS（行级和角色级安全）、OneDrive for Business 和其他此类连接行为，与连接 **SQL Server Analysis Services** 时的情况相似。
* 选择要连接 **Power BI 服务**中的哪一个数据集时，搜索框的搜索范围仅限于已展开的工作区。
* 如果所有者修改最初共享 .pbix 文件，则将覆盖 Power BI 服务中共享的数据集和报表。
* 工作区的成员无权替换最初共享的报表。 尝试执行此操作会导致出现警告，提示你重命名文件后再进行发布。
* 如果删除 **Power BI 服务**中的共享数据集，那么其他 **Power BI Desktop** (.pbix) 文件将无法再正常运行或显示其视觉对象。
* 对于内容包，必须先创建内容包的副本，然后才能以此为基础将 .pbix 报表和数据集共享到 **Power BI 服务**中。
* 对于来自我的组织的内容包，一旦复制，则无法替换在此服务上创建的报表和/或作为使用实时连接复制内容包的一部分创建的报表。 尝试执行此操作会导致出现警告，提示你重命名文件后再进行发布。 在这种情况下，只能替换已发布的实时连接的报表。
* 基于使用与 **Power BI 服务**实时连接的数据集创建报表时，只能将该报表发布到包含所使用数据集的同一 Power BI 服务工作区。
* 删除 **Power BI 服务**中的共享数据集意味着无法再从 **Power BI Desktop** 访问该数据集。


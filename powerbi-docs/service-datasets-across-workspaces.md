---
title: 跨工作区使用数据集（预览）- Power BI
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
ms.openlocfilehash: 17a8e1c9e0d46a56d6b6ff3e46c0fda6da8ffe12
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567845"
---
# <a name="use-datasets-across-workspaces-preview"></a>跨工作区使用数据集（预览）

商业智能是协作活动。 务必建立可能是一个真实源的标准化数据集。 然后发现和重用这些标准化数据集是关键所在。 组织中的专家数据建模人员创建和共享优化的数据集时，报表创建者可以从这些数据集开始生成精确的报表。 这样，你的组织就具有一致数据，可用于决策和健康的数据文化。

![选择共享数据集](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

在 Power BI 中，数据集创建者可以轻松地验证  或推广  数据集，以便其他人能够发现。 这样一来，报表作者就知道哪些数据集是高质量的官方数据集，并且可以在 Power BI 中创作的任何位置使用这些数据集。 数据集所有者可以使用[生成权限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)来控制有权访问其数据的人选。 租户管理员具有新的租户设置，可以[跨工作区治理数据集的使用](service-datasets-admin-across-workspaces.md)。

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>数据集共享和新的体验工作区

基于不同工作区中的数据集生成报表和将报表复制到不同工作区，这与[新的体验工作区](service-create-the-new-workspaces.md)是紧密耦合的：

- 在该服务中，打开新的工作区体验的数据集目录时，数据集目录将显示“我的工作区”和其他新的工作区体验工作区中的数据集。 
- 你打开经典工作区的数据集目录时，只会看到该工作区中的数据集，而不会看到其他工作区中的数据集。
- 在 Desktop 中，你可以将实时连接报表发布到不同工作区，只要它们的数据集在新的体验工作区中。
- 跨工作区复制报表时，目标工作区需是新的体验工作区。

## <a name="build-permission-for-datasets"></a>数据集的“生成”权限

借助“生成”权限类型，你可以允许组织中的其他人在现有数据集上生成报表、仪表板和问答的固定磁贴等新内容。 他们还可以在除 Power BI 之外的数据集上生成新内容比（例如通过“在 Excel 中分析”、XMLA 和“导出”生成的 Excel 表）。 详细了解[生成权限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)。

## <a name="discover-datasets-preview"></a>发现数据集（预览）

在现有数据集之上生成报表时，第一步是连接到 Power service 或 Power BI Desktop 中的数据集。 了解[发现不同工作区的数据集（预览）](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>复制报表

在工作区或应用中找到自己喜欢的报表时，你可以复制它，然后根据自己的需要进行修改。 无需担心如何创建数据模型。 它已为你创建。 修改现有报表比从头开始创建要容易得多。 详细了解[复制报表](service-datasets-copy-reports.md)。

## <a name="promotion-and-certification"></a>推广和验证

如果创建数据集，则创建其他人可从中受益的数据集，这样其他人可通过[推广数据集](service-datasets-promote.md)更轻松地发现该数据集。 你还可以请求组织中的专家[验证你的数据集](service-datasets-certify.md)。

## <a name="licensing"></a>许可

基于共享数据集功能生成的特定功能和体验是根据其现有场景进行授权的。  例如：

- 一般来说，任何人都可以发现和连接到共享数据集。 但没有 Pro 许可证的用户只能连接到位于其“我的工作区”或“Premium 工作区”中的数据集。
- 推广和验证个人工作区之外的数据集需要 Pro 许可证，因为你需要 Pro 许可证才能成为应用工作区中的成员。
- 复制工作区之间的报表需要 Pro 许可证，也是因为你需要 Pro 许可证才能成为应用工作区中的成员。
- 复制应用的报表需要 Pro 许可证，组织内容包也需要。

## <a name="considerations-and-limitations"></a>注意事项和限制

- 在另一工作区中的数据集上生成报表需要两个部分的新的体验工作区：报表需要位于新的体验工作区中，数据集也需要位于新的体验工作区中。
- 在经典工作区中，数据集发现体验仅显示该工作区中的数据集。
- 你可以在应用工作区中创建报表，该应用工作区基于另一工作区中的数据集。 但不能为包含这些数据集的工作区创建应用。
- Desktop 中的免费用户只能查看“我的工作区”和“基于 Premium 的工作区”中的数据集。
- 如果想将基于共享数据集的报表添加到应用，则你必须是数据集工作区的成员。 这是已知问题。
- “发布到 Web”不适用于基于共享数据集的报表。 这是由设计决定的。
- 如果有两个人是使用共享数据集的工作区的成员，则很可能仅其中一人能够在工作区中查看相关数据集。 只有对数据集至少具有读取权限的人可以查看共享数据集。 

## <a name="next-steps"></a>后续步骤

- [推广数据集](service-datasets-promote.md)
- [验证数据集](service-datasets-certify.md)
- [跨工作区治理数据集的使用](service-datasets-admin-across-workspaces.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

---
title: 跨工作区使用数据集简介（预览）
description: 了解如何与整个组织的用户共享数据集。 然后，他们可以在其工作区中基于你的数据集生成报表。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 258dd735c5ba97122d9e93f888e65cf2030f01eb
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530481"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>跨工作区使用数据集简介（预览）

商业智能是协作活动。 务必建立可能是一个真实源的标准化数据集。 然后发现和重用这些标准化数据集是关键所在。 组织中的专家数据建模人员创建和共享优化的数据集时，报表创建者可以从这些数据集开始生成精确的报表。 这样，你的组织就具有一致数据，可用于决策和健康的数据文化。

![选择共享数据集](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

在 Power BI 中，数据集创建者可以使用[生成权限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)来控制有权访问其数据的人选。 数据集创建者也可以轻松地验证或推广数据集，以便其他人能够发现   。 这样一来，报表作者就知道哪些数据集是高质量的官方数据集，并且可以在 Power BI 中创作的任何位置使用这些数据集。 租户管理员具有新的租户设置，可以[跨工作区治理数据集的使用](service-datasets-admin-across-workspaces.md)。

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>数据集共享和新的体验工作区

基于不同工作区中的数据集生成报表和将报表复制到不同工作区，这与[新的体验工作区](service-create-the-new-workspaces.md)是紧密耦合的：

- 在该服务中，打开新的工作区体验的数据集目录时，数据集目录将显示“我的工作区”和其他新的工作区体验工作区中的数据集。 
- 你打开经典工作区的数据集目录时，只会看到该工作区中的数据集，而不会看到其他工作区中的数据集。
- 在 Power BI Desktop 中，只要报表的数据集位于新的体验工作区中，你就可以将实时连接报表发布到不同工作区。
- 跨工作区复制报表时，目标工作区需是新的体验工作区。

## <a name="discover-datasets-preview"></a>发现数据集（预览）

在现有数据集的基础上生成报表时，第一步是连接到 Power BI 服务或 Power BI Desktop 中的数据集。 了解[发现不同工作区的数据集（预览）](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>复制报表

在工作区或应用中找到自己喜欢的报表时，你可以复制它，然后根据自己的需要进行修改。 无需担心如何创建数据模型。 它已为你创建。 修改现有报表比从头开始创建要容易得多。 详细了解[复制报表](service-datasets-copy-reports.md)。

## <a name="build-permission-for-datasets"></a>数据集的“生成”权限

使用“生成”权限类型，如果你是数据集创建者，则可以确定组织中可以在数据集上生成新内容的人选。 拥有生成权限的人员还可以通过“在 Excel 中分析”、XMLA 和“导出”在除 Power BI 之外（例如，Excel 表）的数据集上生成新内容。 详细了解[生成权限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)。

## <a name="promotion-and-certification"></a>推广和验证

如果你创建数据集，则在创建其他人可从中受益的数据集时，可通过[推广数据集](service-datasets-promote.md)使他人能够更轻松地发现该数据集。 你还可以请求组织中的专家[验证你的数据集](service-datasets-certify.md)。

## <a name="licensing"></a>许可

基于共享数据集功能生成的特定功能和体验是根据其现有场景进行授权的。 例如：

- 一般来说，任何人都可以发现和连接到共享数据集。 但没有 Pro 许可证的用户只能连接到位于其“我的工作区”中的数据集。
- 在 Power BI Desktop 中，没有 Pro 许可证的用户只能看到其“我的工作区”中的数据集。
- 在工作区之间复制报表需要 Pro 许可证。
- 复制应用的报表需要 Pro 许可证，组织内容包也需要。
- 推广和验证数据集也需要 Pro 许可证。

## <a name="considerations-and-limitations"></a>注意事项和限制

- 在另一工作区中的数据集上生成报表需要两个部分的新的体验工作区：报表需要位于新的体验工作区中，数据集也需要位于新的体验工作区中。
- 假设你在工作区 A 中创建一个报表，该表基于工作区 B 中的数据集。当你为工作区 A 创建应用时，如果你也是工作区 B 的成员，则只能在工作区 A 应用中包含该报表。
- 在经典工作区中，数据集发现体验仅显示该工作区中的数据集。
- 如果想将基于共享数据集的报表添加到应用，则你必须是数据集工作区的成员。 这是已知问题。
- “发布到 Web”不适用于基于共享数据集的报表。 这是由设计决定的。
- 如果有两个人是使用共享数据集的工作区的成员，则很可能仅其中一人能够在工作区中查看相关数据集。 只有对数据集至少具有读取权限的人可以查看共享数据集。 

## <a name="next-steps"></a>后续步骤

- [推广数据集](service-datasets-promote.md)
- [验证数据集](service-datasets-certify.md)
- [跨工作区治理数据集的使用](service-datasets-admin-across-workspaces.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](http://community.powerbi.com/)

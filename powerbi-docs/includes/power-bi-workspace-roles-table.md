---
title: Power BI 工作区角色
description: Power BI 工作区角色表
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 07/24/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 6a2fa7aca043c553c9174db81ff575853e526e06
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87260215"
---
|功能   | 管理员  | 成员  | 参与者  | 查看器 |
|---|---|---|---|---|
| 更新和删除工作区。  | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   | 
| 添加/删除人员，包括其他管理员。  |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| 允许参与者为工作区更新应用  |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| 添加成员或具有较低权限的其他人。  |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 发布和更改应用的权限 |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 更新应用。 |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |  如允许 <sup>1</sup>  |   |
| 共享一个项或共享应用。<sup>2</sup> |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 允许其他人重新共享项目。<sup>2</sup> |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 在同事的“主页”上特别推荐应用 |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 在同事的“主页”上特别推荐仪表板和报表 |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| 在工作区中创建、编辑和删除内容。  |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| 将报表发布到工作区，删除内容。  |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| 基于此工作区中的数据集在其他工作区中创建报表。<sup>2</sup> |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| 复制报表。<sup>3</sup> | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| 通过本地网关计划数据刷新。<sup>4</sup> | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| 修改网关连接设置。<sup>4</sup> | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| 查看项并与之交互。<sup>5</sup> |  ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| 读取存储在工作区数据流中的数据 | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) | ![“是”复选标记](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> 如果[工作区管理员将此权限委托给参与者](../collaborate-share/service-create-the-new-workspaces.md#security-settings)，则参与者可以更新应用元数据，但不能发布新应用或更改对应用具有权限的用户。

<sup>2</sup> 如果参与者和查看者具有“重新共享”权限，则他们还可以共享工作区中的项。

<sup>3</sup> 若要复制报表，并基于此工作区中的数据集在另一个工作区中创建报表，则需要[数据集的生成权限](../connect-data/service-datasets-build-permissions.md)。 对于此工作区中的数据集，拥有管理员、成员和参与者角色的相关人员通过其工作区角色自动获得生成权限。

<sup>4</sup> 请记住，你还需要对网关具有相应权限。 这些权限在其他位置进行管理，而不受工作区角色和权限的影响。 有关详细信息，请参阅 [管理本地网关](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage)。

<sup>5</sup> 即使没有 Power BI Pro 许可证，如果项位于高级容量的工作区中，你也可以查看 Power BI 服务中的项并与之交互。

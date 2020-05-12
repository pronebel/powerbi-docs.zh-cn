---
title: Power BI 工作区角色
description: Power BI 工作区角色表
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781332"
---
下面介绍以下四种角色的功能：管理员、成员、参与者和查看者。 上述功能（查看和交互除外）都需要 Power BI Pro 许可证。

|功能   | 管理员  | 成员  | 参与者  | 查看器 |
|---|---|---|---|---|
| 更新和删除工作区。  | X  |   |   |   | 
| 添加/删除人员，包括其他管理员。  | X  |   |   |   |
| 添加成员或具有较低权限的其他人。  |  X | X  |   |   |
| 发布和更新应用。 |  X | X  |   |   |
| 共享一个项或共享应用。<sup>1</sup> |  X | X  |   |   |
| 允许其他人重新共享项目。<sup>1</sup> |  X | X  |   |   |
| 在同事的“主页”上特别推荐应用 |  X | X  |   |   |
| 在同事的“主页”上特别推荐仪表板和报表 |  X | X  | X |   |
| 在工作区中创建、编辑和删除内容。  |  X | X  | X  |   |
| 将报表发布到工作区，删除内容。  |  X | X  | X  |   |
| 基于此工作区中的数据集在其他工作区中创建报表。<sup>1</sup> |  X | X  | X  |   |
| 复制报表。<sup>2</sup> | X | X | X |  |
| 通过本地网关计划数据刷新。<sup>3</sup> | X | X | X |  |
| 修改网关连接设置。<sup>3</sup> | X | X | X |  |
| 查看项并与之交互。<sup>4</sup> |  X | X  | X  | X  |
| 读取存储在工作区数据流中的数据 | X | X | X | X |

1. 如果参与者和查看者具有“重新共享”权限，则他们可以共享工作区中的项。
2. 若要复制报表，并基于此工作区中的数据集在另一个工作区中创建报表，需要数据集的生成权限。 对于此工作区中的数据集，拥有管理员、成员和参与者角色的相关人员通过其工作区角色获得生成权限。
3. 请记住，你还需要对网关具有相应权限。 这些权限在其他位置进行管理，而不受工作区角色和权限的影响。 有关详细信息，请参阅 [管理本地网关](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage)。
4. 即使没有 Power BI Pro 许可证，如果项位于高级容量的工作区中，也可以查看 Power BI 服务中的项并与之交互。


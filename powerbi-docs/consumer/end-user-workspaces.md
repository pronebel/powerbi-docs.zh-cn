---
title: 工作区中的内容组织方式
description: 了解工作区和工作区角色
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 9ec2c608b90bf651df613f0714addd251a885039
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2020
ms.locfileid: "82120133"
---
# <a name="collaborate-in-workspaces"></a>在工作区中协作

 在工作区  中，可以与同事协作处理特定内容。 工作区是由 Power BI 设计人员  创建，用于保留仪表板和报表的集合。 然后设计人员可将该集合捆绑到应用，并可将该应用分发到整个组织或特定人员或组  。 

 使用 Power BI 服务的所有人还具有“我的工作区”  。  “我的工作区”是个人沙盒，可以在其中为自己创建内容。

 可以从 Power BI“主页”  ，或是通过从左侧导航窗格中选择“工作区”  或“我的工作区”  来查看工作区。

 ![显示两种类型的工作区的导航窗格](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>工作区类型
“我的工作区”存储了你拥有和创建的所有内容  。 可以将其作为你的个人沙盒或自己内容的工作区域。 对于很多 Power BI 使用者来说，“我的工作区”保持为空，因为你的作业并不涉及到创建新内容   。 根据定义，使用者会使用其他人创建的数据并使用该数据作出业务决策  。 如果你发现自己要创建内容，不妨改为阅读[面向设计人员的 Power BI 文档](../create-reports/index.yml)。

“应用工作区”  包含特定应用的所有内容。 当设计人员创建一个应用时，他们会将使用该应用所必需的全部内容捆绑在一起  。 内容可能包括仪表板、报表和数据集。 并非每个应用都包含这三项内容。 一个应用可能只包含一个仪表板、每种内容类型中包含三个，或者甚至包含 20 个报表。 这一切都取决于设计人员在应用中随附的内容  。 通常情况下，面向使用者  的应用工作区不包含数据集。

下面的 Fig sales 应用工作区包含三个报表和一个仪表板。 

![显示两种类型的工作区的导航窗格](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>工作区中的角色

角色决定了可以在此工作区中执行什么操作，以便实现团队协作。  授予对新工作区的访问权限时，设计人员  会将个人或组添加到以下工作区角色之一：查看者  、成员  、参与者  或管理员  。 


作为 Power BI 使用者  ，你通常将使用查看者  角色在工作区中进行交互。 但设计人员  还可以将你分配到“成员”  或“参与者”  角色。 使用查看者角色，可以查看其他人创建并与你共享的内容（仪表板、报表、应用），并与之交互。 由于查看者角色无法访问基础数据集，因此这是一种与内容进行交互的安全方式，不必担心会“伤害”基础数据。


有关作为具有查看器角色的使用者  可以执行的操作的详细列表，请参阅[面向使用者的 Power BI 功能](end-user-features.md)。


### <a name="workspace-roles"></a>工作区角色
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
| 复制报表。 | X | X | X |  |
| 查看项并与之交互。<sup>2</sup> |  X | X  | X  | X  |
| 读取存储在工作区数据流中的数据 | X | X | X | X |

1. 如果参与者和成员具有“重新共享”权限，则他们可以共享工作区中的项。

2. 即使没有 Power BI Pro 许可证，如果项位于高级容量的工作区中，也可以查看 Power BI 服务中的项并与之交互。

## <a name="licensing-workspaces-and-capacity"></a>许可、工作区和容量
对于决定在工作区中可以做什么，不可以做什么，许可也起了一定作用。 许多功能要求用户具有 Power BI Pro  许可证。 大多数使用者  使用免费  许可证。 

如果你有免费许可证，并且工作区存储在高级容量  中，则能够查看该工作区中的内容并与之交互。 菱形图标标识存储在高级容量中的工作区和应用。

![所选工作区](media/end-user-workspaces/power-bi-diamond.png) 若要了解详细信息，请参阅[我有哪种许可证？](end-user-license.md)。



## <a name="next-steps"></a>后续步骤
* [Power BI 中的应用](end-user-apps.md)    

* 有疑问？ [尝试在 Power BI 社区中提问](https://community.powerbi.com/)


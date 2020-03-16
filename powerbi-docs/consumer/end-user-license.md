---
title: Power BI 使用者的许可证类型
description: 了解不同类型的许可证以及如何确定你拥有的许可证类型。
author: mihart
ms.reviewer: lukasz
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/09/2020
ms.author: mihart
LocalizationGroup: consumers
ms.openlocfilehash: 09b48ad5bed9472146c81ac1372cdd46baeb0faf
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79040617"
---
# <a name="types-of-power-bi-licenses"></a>Power BI 许可证的类型
作为“使用者”，你可以使用 Power BI 服务来浏览报表和仪表板，以便做出业务决策  。 如果你使用 Power BI 已有一段时间，或与设计师同事聊过天，你可能已经发现只有在拥有某种类型的许可证时才能使用某些功能  。 

本文介绍了各种许可证类型和组合（免费、Pro、Premium 和高级容量）的区别。 你还将了解如何确定自己使用的是哪种许可证组合。  

![许可证关联关系图](media/end-user-license/power-bi-diagram.jpg)

首先来看看两类许可证：每用户许可证和组织许可证。 我们将从默认许可证功能入手。 接下来将介绍 Power BI 管理员和内容所有者如何使用角色和权限来修改默认许可证功能。 

例如，即使你的许可证允许，管理员也可以限制你执行一些操作，如导出数据、使用问答自然语言查询或发布到 Web。 将内容分配到工作区时，报表设计人员  可以向你分配工作区角色。 此类角色决定了你在相应工作区中可以做什么，不可以做什么。 设计人员  可以使用权限设置来进一步调整你的许可证限制。 换句话说...这是很复杂的。 但愿本文能够尽可能（即便不是完全）解惑。

## <a name="per-user-licenses"></a>每用户许可证
第一种类型的许可证是每用户  许可证。 每个 Power BI 服务用户都有免费许可证或 Pro 许可证。 某些功能是为拥有 Pro 许可证的用户预留的。  

- 拥有 Power BI Pro 许可证  的用户可以通过创建和共享内容与其他 Pro 用户协作。 只有具有 Pro 许可证的用户才能发布报表、订阅仪表板和报表、在工作区中与同事协作。 

    ![Pro 用户的图像](media/end-user-license/power-bi-pro.jpg)

    Power BI Pro 是一种单独的用户许可证，使用户能够读取他人已发布到 Power BI 服务的报表和仪表板并与之进行交互。 具有此许可证类型的用户可以与 Power BI Pro 用户共享内容并开展协作。 只有 Power BI Pro 用户才能发布内容或与其他用户共享内容，或使用其他用户创建的内容。 在 [Power BI 高级容量](#understanding-premium-and-premium-capacity)中托管的内容除外。 Pro 许可证通常由报表设计人员  和开发人员使用。 有关详细信息，请参阅下面的 [Power BI 高级容量](#understanding-premium-and-premium-capacity)。


- 尽管独立的 Power BI 免费许可证  功能很强大，但其适用于刚刚开始接触 Power BI 的用户或为自己创建内容的用户。 [以个人身份注册 Power BI 服务](../service-self-service-signup-for-power-bi.md)。 独立的免费许可证与组织许可证没有关联。 

    独立的免费用户许可证非常适合使用 Microsoft 示例了解 Power BI 的用户。 拥有独立的免费许可证的用户不能查看其他用户共享的内容，也不能与其他 Power BI 用户共享自己的内容。 

    ![独立用户的图像](media/end-user-license/power-bi-free-license.jpg)

到目前为止清楚吗？  OK. 让我们再添加一个层，即“高级容量”  。

## <a name="understanding-premium-and-premium-capacity"></a>了解 Premium 和高级容量
Premium 许可证是组织  许可证。 可以将它看作是在组织中的所有 Power BI 每用户  许可证的基础之上添加一层特性和功能。 

在组织购买 Premium 许可证后，管理员通常会将 Pro 许可证分配给将创建和共享内容的员工。 管理员会将免费许可证分配给将使用该内容的每个人。 Pro 用户可创建[工作区](end-user-workspaces.md)，并将内容（仪表板、报表、应用）添加到这些工作区。 为了允许其他人在这些工作区中协作，Pro 用户使用容量  、权限和角色的组合。 

在组织购买 Premium 许可证后，他们会收到 Power BI 服务中专门分配给他们的容量。 该容量不与其他组织共享。 该容量受完全由 Microsoft 管理的专用硬件支持。 组织可以选择广泛应用自己的专用容量，也可以将它分配到特定工作区。 在高级容量中的工作区内，Pro 用户可以与免费用户共享和协作，而不要求免费用户拥有 Pro 帐户。  


在高级容量中，内容设计人员仍必须拥有 Pro 许可证。 设计人员连接到数据源、模型数据，并创建打包为工作区应用的报表和仪表板。 没有 Pro 许可证的用户仍可以访问 Power BI Premium 中的工作区，但前提是内容位于高级容量  中，且工作区所有者向他们提供权限。

在下图中，左侧表示在工作区中创建和共享内容的 Pro 用户。  
- 工作区 A  是在没有 Premium 许可证的组织中创建的。 

- 工作区 B  是在有 Premium 许可证的组织中创建的，尽管此特定工作区没有在高级容量中保存。 此工作区没有菱形图标。

- 工作区 C  是在有 Premium 许可证的组织中创建的，且已在高级容量中保存。 此工作区有菱形图标。  

![Pro 用户的图像](media/end-user-license/power-bi-sharing-premium-under.jpg)

Power BI Pro 设计人员  可以使用这三个工作区中的任何一个与其他 Pro 用户共享和协作。 只要设计人员与整个组织共享工作区，或向 Pro 用户分配工作区角色即可。 

Power BI Pro 设计人员  只能使用工作区 C 与免费用户共享和协作。必须将此工作区分配到高级容量，这样免费用户才能访问此工作区。 在此工作区中，设计人员向协作者分配以下角色：管理员  、成员  、参与者  或查看者  。 角色决定了可以在此工作区中执行什么操作。 Power BI 使用者  通常分配有查看者  角色。 若要了解详细信息，请参阅 [Power BI 使用者的工作区](end-user-workspaces.md)。

## <a name="find-out-which-license-you-have"></a>了解你拥有哪种许可证
可以通过多种方式查阅 Power BI 许可证信息。 

首先，确定你所拥有的用户许可证类型  。

- 某些版本的 Microsoft Office 包含 Power BI Pro 许可证。  要查看你的 Office 版本是否包含 Power BI，请访问 [Office 门户](https://portal.office.com/account)并选择“订阅”  。

    第一位用户 Pradtanna 具有 Office 365 E5，其中包含 Power BI Pro 许可证。

    ![Office 门户“订阅”选项卡](media/end-user-license/power-bi-license-office.png)

    第二个用户 Zalan 具有 Power BI 免费许可证。 

    ![Office 门户“订阅”选项卡](media/end-user-license/power-bi-license-free.png)

接下来，检查你的帐户是否还有 Premium 许可证。 上述任一用户（无论是 Pro 还是免费）都可能属于有 Premium 许可证的组织。  我们来看一下第二个用户 Zalan。  

- 在 Power BI 服务中，选择“我的工作区”，然后选择右上角的齿轮图标  。 选择“管理个人存储”  。

    ![齿轮“设置”菜单显示出来](media/end-user-license/power-bi-license-personal.png)

    每用户  许可证（无论是 Pro 还是免费）都在云中提供 10GB 存储空间，可用于托管 Power BI 报表或 Excel 工作簿。 如果容量超过 10GB，表明你是有 Premium 许可证的组织帐户的成员。

    ![管理显示 100 GB 的存储](media/end-user-license/power-bi-free-capacity.png)

    请记住，在Office 门户页上，Zalan 的用户订阅为 Power BI（免费）。 不过，由于他的组织购买了 Premium 许可证，因此在 Power BI 服务中，Zalan 的存储空间没有 10GB 的限制；他有 100GB 可用空间。 作为有 Premium 许可证的组织中的使用者  ，只要设计人员  将工作区置于高级容量中，Zalan 就能查看共享内容、与同事协作、使用应用等。 他的权限范围由 Power BI 管理员和内容设计人员设定。 请注意，有位 Pro 用户已与 Zalan 共享工作区。 菱形图标指明，此工作区存储在高级容量中。 

   
## <a name="understanding-workspace-roles"></a>了解工作区角色
至此，我们已讨论了每用户许可证、Premium 许可证和高级容量许可证。 现在来看看工作区角色  。

由于这是一篇面向 Power BI 使用者  的文章，因此场景如下：

-  你是有 Power BI Premium 许可证的组织中的免费  用户。 
- Power BI Pro 用户创建了仪表板和报表的集合，并将此集合作为应用  发布给整个组织。  
- 应用位于工作区  中，工作区位于高级容量中。    
- 此应用工作区包含一个仪表板和两个报表。
- Pro 用户向我们分配了查看者  角色。

### <a name="the-viewer-role"></a>查看者角色
借助角色，Power BI 设计人员  可管理谁能在工作区中执行什么操作，以便实现团队协作。 其中一个角色就是查看者  。 

如果工作区位于 Power BI 高级容量中，具有查看者角色的用户可以访问工作区，即使没有 Power BI Pro 许可证，也不例外。 不过，由于查看者角色无法访问或导出基础数据，因此这是一种与仪表板、报表和应用进行交互的安全方式。

> [!TIP]
> 若要了解其他角色（管理员、成员和参与者），请参阅[新建工作区](../service-new-workspaces.md)。


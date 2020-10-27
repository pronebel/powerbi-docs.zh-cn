---
title: Power BI 业务用户的许可证类型
description: 了解不同类型的许可证以及如何确定你拥有的许可证类型。
author: mihart
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: powerbi-consumer
Ms.custom: css_fy20Q4
ms.topic: how-to
ms.date: 10/07/2020
ms.author: mihart
ms.custom: licensing support
LocalizationGroup: consumers
ms.openlocfilehash: 2b0bde7aa193af831a95fc53d461f874a3c1d1d1
ms.sourcegitcommit: d2f633b4bfa271051ba1d2ef0e6e8da7dcf42818
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830382"
---
# <a name="licenses-and-subscriptions-for-business-users"></a>业务用户的许可证和订阅

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

作为[业务用户](end-user-consumer.md)，你可以使用 Power BI 服务来浏览报表和仪表板，以便基于数据做出业务决策。 如果你使用 Power BI 已有一段时间，或与设计者同事聊过天，你可能会发现，有些功能只有在拥有特定类型的许可证、订阅或权限时才能使用。

在 Power BI 服务中能执行的操作取决于三个方面：
-    正在使用的许可证和订阅的类型，
-    内容的存储位置以及
-    分配的角色和权限。


![Pro 用户的图像](media/end-user-license/power-bi-questions-small.png)

在本文中，我们将介绍每种许可证类型的功能以及内容的存储位置如何影响它的使用 。 你还将了解如何查找许可证和订阅，并找出内容的存储位置。 有关角色和权限的详细信息，请参阅[工作区角色](end-user-workspaces.md)。

## <a name="licenses"></a>许可证

Power BI 服务的每个用户都使用免费许可证或 Pro 许可证。 如果你是 Power BI 商务用户，你可能使用的是由 Power BI 管理员管理的免费许可证。

你可以同时拥有多个许可证。  该服务会始终为你提供与你目前拥有的最宽松的许可证等同的体验。

## <a name="power-bi-premium-capacity"></a>Power BI 高级容量

Premium 是一种组织订阅，它提供了另一种存储内容的方式 - 将内存存储在专用容量中。 借助 Premium，组织内外具有权限的任何人都可以查看存储在此高级容量中的内容，而无需购买个人 Power BI Pro 许可证。 

Premium 允许 Pro 用户广泛分发内容，且不要求查看内容的收件人提供 Pro 许可证。 内容设计者需要提供 Pro 许可证。 设计人员连接到数据源、模型数据，并创建打包为工作区应用的报表和仪表板。 如果向用户分配了[ Power BI Premium 容量的工作区中的角色](end-user-workspaces.md)，即使用户没有 Pro 许可证仍可访问该工作区。

在这些工作区中，设计者分配查看者、参与者、成员和管理员等角色。    这些角色决定了同事可与内容交互的程度。 有关详细信息，请参阅[工作区权限和角色。](end-user-workspaces.md) 

有关高级容量的详细信息，请参阅[什么是 Microsoft Power BI Premium？](../admin/service-premium-what-is.md)。

## <a name="find-out-which-licenses-you-have"></a>了解你拥有哪些许可证
选择你的个人资料图片以显示帐户信息。 Zalan 使用的是免费许可证。 

![单击个人资料图片后显示下拉菜单的屏幕截图](media/end-user-license/power-bi-profiles.png)


若要查看帐户的其他详细信息，请选择“查看帐户”。 此时将在新的浏览器选项卡中打开 [Microsoft“我的帐户”页面](https://portal.office.com/account)。查看分配给你的许可证。  选择“订阅”选项卡。

![Microsoft 365 帐户页面的屏幕截图。](media/end-user-license/power-bi-subscriptions.png)




第一位用户 Pradtanna 具有 Office 365 E5，其中包含 Power BI Pro 许可证。

![显示 Office 365 E5 订阅的“Office 门户订阅”选项卡](media/end-user-license/power-bi-license-office.png)

第二个用户 Zalan 具有 Power BI 免费许可证。 

![Office 门户“订阅”选项卡](media/end-user-license/power-bi-license-free.png)

## <a name="find-out-if-you-have-access-to-premium-capacity"></a>了解你是否有权访问高级容量

接下来，检查你是否属于具有高级容量的组织。 上述任一用户（无论是 Pro 还是免费许可证用户）都可能属于具有高级容量的组织。  我们来看一下第二个用户 Zalan。  

通过查阅可用存储量，我们可以确定 Zalan 的组织是否具有高级容量。 

- 在 Power BI 服务中，选择“我的工作区”，然后选择右上角的齿轮图标。 选择“管理个人存储”。

    ![齿轮“设置”菜单显示出来](media/end-user-license/power-bi-license-personal.png)

    如果容量超过 10 GB，表明你是拥有高级订阅的组织中的成员。 下图显示 Zalan 的组织具有高达 100 GB 的存储空间。  

    ![管理显示 100 GB 的存储](media/end-user-license/power-bi-free-capacity.png)

请注意，有位 Pro 用户已与 Zalan 共享工作区。 菱形图标表明，此工作区存储在高级容量中。 

## <a name="identify-content-hosted-in-premium-capacity"></a>识别高级容量中托管的内容

查明你的组织是否具有高级容量的另一种方法是查找具有菱形图标的应用和应用工作区。 菱形表明，此内容存储在高级容量中。 

在下图中，三个应用存储在高级容量中。

![应用屏幕](media/end-user-license/power-bi-premium.png)

如果你是拥有免费许可证的用户，只要设计者将工作区置于 Premium 专用容量中，便可在工作区中查看共享内容、与同事协作、使用应用仪表板和报表，等等。 权限范围由 Power BI 管理员和内容设计者设定。

## <a name="putting-it-all-together"></a>汇总

组织购买高级订阅时，管理员通常会将 Pro 许可证分配给将使用高级容量创建和共享内容的员工。 Pro 用户可创建[工作区](end-user-workspaces.md)，并将内容（仪表板、报表、应用）添加到这些工作区。 为了允许免费用户在这些工作区中协作，管理员或 Pro 用户将这些工作区分配到专用容量中。  

|许可证类型  |共享容量 |专用高级容量  |
|---------|---------|---------|
|**免费**     |  用作个人沙盒，你可以在其中为自己创建内容并与该内容进行交互。 免费许可证是试用 Power BI 服务的好方法。 你不能使用来自其他人的内容，也不能与他人共享你的内容 <sup>1</sup>     |   与分配至专用高级容量的内容进行交互，并与你共享。 免费和 Pro 用户可以进行协作，而无需免费用户拥有 Pro 帐户。      |
|**Pro**     |  通过创建和共享内容与其他 Pro 版用户协作。        |  通过创建和共享内容与免费版和 Pro 版用户协作。       |


<sup>1</sup> 请参阅[注意事项和疑难解答](#considerations-and-troubleshooting)。

在下图中，左侧表示在应用工作区中创建和共享内容的 Pro 用户。

- 工作区 A 是在没有高级容量许可证的组织中创建的。

- 工作区 B 是在具有 Premium 订阅的组织中创建的。 此工作区保存在专用容量中。 此工作区有菱形图标。  

    ![三个工作区的图像](media/end-user-license/power-bi-dedicated.jpg)

Power BI Pro 设计者可以在任何一个工作区中与其他 Pro 用户共享和协作。 但是，Power BI Pro 用户可以与免费版用户共享和协作的唯一方法是使用高级专用容量中的工作区 B。  在此工作区中，设计者向协作者分配以下角色。 角色决定了可以在此工作区中执行什么操作。 Power BI 业务用户通常分配有查看者角色。 若要详细了解角色，请参阅 [Power BI 业务用户的工作区](end-user-workspaces.md)。

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

- 可以有多个 Power BI 许可证。 Power BI 服务将始终提供与你当前拥有的最佳许可证等同的体验。 例如，如果你有 Pro 和免费许可证，Power BI 服务将使用 Pro 许可证。

- 如果想要创建和共享内容（仪表板、报表、应用），或打开其他人与你共享的内容，则需要拥有 Pro 用户许可证。 可以注册可免费使用 60 天的 Power BI Pro 个人试用版。 每次尝试使用 Pro 功能时，选择 Power BI 服务中显示的“升级”对话框。

    ![具有 Pro 试用版链接的对话框](media/end-user-license/power-bi-trial.png)

  60 天试用期到期后，你的许可证将恢复为 Power BI 免费许可证。 许可证恢复后，你无法再使用需要 Power BI Pro 许可证的功能。 如果你想继续使用 Pro 许可证，请联系管理员或 IT 技术支持购买 Power BI Pro 许可证。 如果你没有管理员或 IT 技术支持，请访问 [Power BI 定价页](https://powerbi.microsoft.com/pricing/)。

- 对于通过选择“免费试用”类型按钮自行注册的免费许可证，永远不会过期。 因此，如果你升级到 Pro 试用版或你的组织提供了 Pro 许可证，在试用版结束或组织删除 Pro 许可证后，你仍可重新使用免费许可证 - 除非你取消了该许可证。

- <sup>1</sup> Power BI 服务的免费用户许可证非常适合使用“我的工作区”探索该服务或使用该服务进行个人数据分析和可视化的用户。 免费的独立用户不使用 Power BI 与同事协作。 拥有免费许可证的独立用户不能查看其他用户共享的内容，也不能与其他 Power BI 用户共享自己的内容。



## <a name="next-steps"></a>后续步骤

- [我是 Power BI 业务用户吗？](end-user-consumer.md)    
- [了解工作区](end-user-workspaces.md)    
- [查看按许可证类型列出的 Power BI 业务用户功能](end-user-features.md)

---
title: 什么是 Power BI？
description: 概述了 Power BI 以及如何完美组合使用各种产品（Power BI Desktop、Power BI 服务、Power BI 移动版、报表服务器、Power BI Embedded）。
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: b1efe45d52b5a7a18a86407b41e8af287d3c8260
ms.sourcegitcommit: b717118c44499c8fd8f57534a275f2f78aacc0f1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2019
ms.locfileid: "55971639"
---
# <a name="what-is-power-bi"></a>什么是 Power BI？
**Power BI** 是软件服务、应用和连接器的集合，它们协同工作以将相关数据来源转换为连贯的视觉逼真的交互式见解。 数据可以是 Excel 电子表格，也可以是基于云和本地混合数据仓库的集合。 借助 Power BI 可以轻松连接到数据源，可视化并发现重要内容，并根据需要与他人共享。

![展示 Power BI 输入源的关系图](media/power-bi-overview/power-bi-input-new.png)

**Power BI** 简单且快速，能够从 Excel 电子表格或本地数据库创建快速见解。 同时 **Power BI** 也是可靠的、企业级的，可进行丰富的建模和实时分析，及自定义开发。 因此，它可以成为你的个人报表和可视化工具。 它还可以作为组项目、部门或整个公司的分析和决策引擎。

## <a name="the-parts-of-power-bi"></a>Power BI 的组成部分
Power BI 包含 Windows 桌面应用程序（称为 Power BI Desktop）、联机 SaaS（软件即服务）服务（称为 Power BI 服务），以及适用于 Windows、iOS 和 Android 设备的 Power BI 移动应用。

![Power BI Desktop、Power BI 服务、Power BI 移动版](media/power-bi-overview/power-bi-blocks.png)

Power BI Desktop、服务和移动应用这三个元素旨在使用户通过最有效的方式创建、共享和使用业务见解。

使用第四个元素 Power BI 报表服务器，在 Power BI Desktop 中创建 Power BI 报表后，可以将其发布到本地报表服务器。 详细了解 [Power BI 报表服务器](#on-premises-reporting-with-power-bi-report-server)。

## <a name="how-power-bi-matches-your-role"></a>Power BI 如何与你的角色匹配
使用 Power BI 的方式取决于你在项目中的角色或你所在的团队。 不同角色的用户可能以不同方式使用 Power BI，这很正常。

例如，你可能主要使用 Power BI 服务 。 但处理数字、生成业务报表的同事可能主要使用 Power BI Desktop 来创建报表，并将这些报表发布到 Power BI 服务，你可以在服务中查看这些报表。 而另一个负责销售的同事可能主要使用 Power BI 手机应用，监视销售配额的进度，深入了解新的潜在销售顾客详细信息。

如果你是开发人员，可以使用 Power BI API 将数据推送到数据集或将仪表板和报表嵌入到你自己的自定义应用程序。 有关于新视觉对象的意见或建议？ 自行生成并与他人共享。  

还可能会在不同时间使用 Power BI 的每个元素，具体取决于给定项目尝试实现的目标或你的角色。

也许你会使用 Power BI Desktop 为自己的团队创建有关客户参与统计信息的报表。 也许你还会在服务中的实时仪表板中查看库存和制造进度。 如何使用 Power BI 取决于 Power BI 的哪个功能或服务是适用的最佳工具。 Power BI 的每个部分都可供使用，这正是 Power BI 极具灵活性和吸引力的原因所在。

浏览与你的角色相关的文档：
- 面向[***设计人员***](desktop-what-is-desktop.md)的 Power BI
- 面向[***使用者***](consumer/end-user-consumer.md)的 Power BI
- 面向[***开发人员***](developer/what-can-you-do.md)的 Power BI
- 面向[***管理员***](service-admin-administering-power-bi-in-your-organization.md)的 Power BI

## <a name="the-flow-of-work-in-power-bi"></a>Power BI 中的工作流
通过连接到数据源并在 Power BI Desktop 中生成报表，Power BI 中的常见工作流将开始。 然后，将该报表从 Power BI Desktop 发布到 Power BI 服务并进行共享，以便服务和移动设备中的最终用户可以查看报表并与之交互。
此工作流很常见，展示了三个主要的 Power BI 元素如何相互补充。

以下是 [Power BI Desktop 与 Power BI 服务比较](service-service-vs-desktop.md)的详情。

但是，如果你准备好移动到云，并且希望将报表保留在企业防火墙后，那该怎么做？  请继续阅读。

## <a name="on-premises-reporting-with-power-bi-report-server"></a>使用 Power BI 报表服务器进行本地报告
使用 Power BI 报表服务器提供的各种现成工具和服务在本地创建、部署和管理 Power BI 报表、移动报表和分页报表。

![针对本地的关系图](media/power-bi-overview/power-bi-report-server2.png)

Power BI 报表服务器是在防火墙后部署的一种解决方案，然后以不同方式将报表交付给正确用户，无论是在 Web 浏览器、移动设备还是在电子邮件中查看它们。 Power BI 报表服务器与云中的 Power BI 兼容，因此可以在就绪时转到云。 

详细了解 [Power BI 报表服务器](report-server/get-started.md)。

## <a name="next-steps"></a>后续步骤
[登录、获取数据并以自己的方式了解 Power BI 服务](service-the-new-power-bi-experience.md)   
[教程：Power BI 服务入门](service-get-started.md)
[快速入门：连接到 Power BI Desktop 中的数据](desktop-quickstart-connect-to-data.md)
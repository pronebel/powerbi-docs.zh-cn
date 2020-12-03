---
title: 什么是 Power BI？
description: 概述了 Power BI 以及如何完美组合使用各种产品（Power BI Desktop、Power BI 服务、Power BI 移动版、报表服务器、Power BI Embedded）。
author: mihart
ms.author: mihart
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: overview
ms.date: 09/23/2020
LocalizationGroup: Get started
ms.openlocfilehash: acbd0761b481ec4884ab94d50de219a2d753b574
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416522"
---
# <a name="what-is-power-bi"></a>什么是 Power BI？
**Power BI** 是软件服务、应用和连接器的集合，它们协同工作以将相关数据来源转换为连贯的视觉逼真的交互式见解。 数据可以是 Excel 电子表格，也可以是基于云和本地混合数据仓库的集合。 使用 Power BI，可以轻松连接到数据源，可视化并发现重要内容，并根据需要与任何人共享。

## <a name="the-parts-of-power-bi"></a>Power BI 的组成部分
Power BI 包括多个协同工作的元素，从以下三个基本元素开始： 
- 名为 Power BI Desktop 的 Windows 桌面应用程序
- 名为 Power BI 服务的联机 SaaS（软件即服务）。 
- 适用于 Windows、iOS 和 Android 设备的 Power BI 移动应用

![显示了 Power BI Desktop、服务和移动应用三者集成的示意图的屏幕截图。](media/power-bi-overview/power-bi-overview-blocks.png)

Power BI Desktop、服务和移动应用这三个元素旨在让你能够采用适合你及你的角色且最有效的方式来创建、共享和使用业务见解。

除了这三个元素之外，Power BI 还提供了两个其他元素：

- **Power BI 报表生成器**，用于创建要在 Power BI 服务中共享的分页报表。 请阅读本文后面有关[分页报表](#paginated-reports-in-the-power-bi-service)的更多内容。
- **Power BI 报表服务器**，这是一个本地报表服务器。在 Power BI Desktop 中创建 Power BI 报表后，你可以在该服务器中发布报表。 请阅读本文后面有关 [Power BI 报表服务器](#on-premises-reporting-with-power-bi-report-server)的更多内容。

## <a name="how-power-bi-matches-your-role"></a>Power BI 如何与你的角色匹配
使用 Power BI 的方式取决于你在项目中的角色或你所在的团队。 不同角色的其他用户可能以不同方式使用 Power BI。

例如，你可能主要使用 Power BI 服务来查看报表和仪表板。 负责处理数字和生成业务报表的同事可能主要使用 Power BI Desktop 或 Power BI 报表生成器来创建报表，然后将这些报表发布到 Power BI 服务中，你可以在该服务中查看这些报表 。 另一位负责销售的同事可能主要使用 Power BI 手机应用来监视销售配额的进度和深入了解新的潜在销售顾客的详细信息。

如果你是开发人员，可以使用 Power BI API 将数据推送到数据集或将仪表板和报表嵌入到你自己的自定义应用程序。 有关于新视觉对象的意见或建议？ 自行生成并与他人共享。  

你还可能会在不同时间使用 Power BI 的每个元素，具体视你尝试实现的目标或你在给定项目中的角色而定。

如何使用 Power BI 取决于 Power BI 的哪个功能或服务是适用的最佳工具。 例如，可以使用 Power BI Desktop 来为自己团队创建有关客户参与统计信息的报表，也可以在 Power BI 服务的实时仪表板中查看库存和生产进度。 你可以基于 Power BI 数据集创建可通过邮件发送的发票的分页报表。 Power BI 的每个部分都可供使用，这正是 Power BI 极具灵活性和吸引力的原因所在。

浏览与你的角色相关的文档：
- 面向[业务用户](../consumer/end-user-consumer.md)的 Power BI
- 面向[报表创建者](desktop-what-is-desktop.md)的 Power BI Desktop
- 面向[企业报表创建者](../paginated-reports/paginated-reports-report-builder-power-bi.md)的 Power BI 报表生成器
- 面向 [*管理员*](../admin/service-admin-administering-power-bi-in-your-organization.md)的 Power BI
- 面向开发人员的 Power BI
    * [Power BI 嵌入式分析](../developer/embedded/embedding.md)
    * [Azure 中的 Power BI Embedded 是指什么？](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
    * [Power BI 中的视觉对象](../developer/visuals/power-bi-custom-visuals.md)
    * [开发人员可以使用 Power BI API 做什么？](../developer/automation/overview-of-power-bi-rest-api.md)

## <a name="the-flow-of-work-in-power-bi"></a>Power BI 中的工作流
Power BI 中的一个常见工作流以连接到 Power BI Desktop 中的数据源并生成报表开始。 然后，你将该报表从 Power BI Desktop 发布到 Power BI 服务并进行共享，以便使用 Power BI 服务和移动设备的业务用户可以查看报表并与之交互。

此工作流很常见，展示了三个主要的 Power BI 元素如何相互补充。

以下是 [Power BI Desktop 与 Power BI 服务比较](../fundamentals/service-service-vs-desktop.md)的详情。

## <a name="paginated-reports-in-the-power-bi-service"></a>Power BI 服务中的分页报表

另一个工作流涉及 Power BI 服务中的分页报表。 企业报表创建者设计要打印或共享的分页报表。 他们还可以在 Power BI 服务中共享这些报表。 它们被称为“分页”，因为它们已进行了格式化，以适应页面。 它们通常用于操作性报表，或者用于打印表单，例如发票或脚本。 即使某个表跨多个页，分页报表也能显示表中的所有数据。 Power BI 报表生成器是用于创作分页报表的独立工具。

:::image type="content" source="media/power-bi-overview/paginated-report-invoice-power-bi-service.png" alt-text="Power BI 服务中的分页报表的屏幕截图。":::

请阅读有关 Power BI 服务中的[分页报表](../paginated-reports/paginated-reports-report-builder-power-bi.md)的更多内容。

## <a name="on-premises-reporting-with-power-bi-report-server"></a>使用 Power BI 报表服务器处理本地报表

如果需要将报表保存在本地（比如防火墙后面），该怎么办？  请继续阅读。

你可以使用 Power BI 报表服务器提供的现成工具和服务，在 Power BI Desktop 中创建、部署和管理 Power BI 报表，在报表生成器中创建、部署和管理分页报表。

![显示了 Power BI 报表服务器、服务和移动应用三者集成的示意图的屏幕截图。](media/power-bi-overview/power-bi-report-server2.png)

Power BI 报表服务器是在防火墙后面部署的解决方案，然后以不同方式将报表交付给正确用户，无论是在 Web 浏览器、移动设备还是以电子邮件方式查看它们。 Power BI 报表服务器与云中的 Power BI 兼容，因此可以在就绪时转到云。 

详细了解 [Power BI 报表服务器](../report-server/get-started.md)。

## <a name="next-steps"></a>后续步骤
- [快速入门：了解如何使用 Power BI 服务](../consumer/end-user-experience.md)   
- [教程：Power BI 服务入门](service-get-started.md)
- [快速入门：连接到 Power BI Desktop 中的数据](../connect-data/desktop-quickstart-connect-to-data.md)

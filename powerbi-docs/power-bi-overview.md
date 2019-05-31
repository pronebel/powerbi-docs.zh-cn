---
title: 什么是 Power BI？
description: Power BI Desktop、 Power BI 服务、 Power BI 移动版中，报表服务器和 Power BI 嵌入 Power BI 和不同的部件如何协同工作的概述。
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7236caba1c7a8eb07e93c6f2af7068141b8ac3a7
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413037"
---
# <a name="what-is-power-bi"></a>什么是 Power BI？
**Power BI** 是软件服务、应用和连接器的集合，它们协同工作以将相关数据来源转换为连贯的视觉逼真的交互式见解。 数据可以是 Excel 电子表格，也可以是基于云和本地混合数据仓库的集合。 Power BI，你可以轻松地连接到数据源、 可视化和了解什么是重要的是，和与任何人或所需的每个人都进行分享。

![展示 Power BI 输入源的关系图](media/power-bi-overview/power-bi-input-new.png)

Power BI 可以是简单和快速，能够从 Excel 电子表格或本地数据库创建快速见解。 Power BI 也是可靠，但和企业级，准备好进行丰富的建模和实时分析，以及自定义开发。 它可以是个人报表和可视化工具，并还用作组项目、 部门或整个企业的分析和决策引擎。

## <a name="the-parts-of-power-bi"></a>Power BI 的组成部分
Power BI 组成： 
- Windows 桌面应用程序调用**Power BI Desktop**
- 联机 SaaS (*软件即服务*) 服务名为**Power BI 服务** 
- Power BI**移动应用**面向 Windows、 iOS 和 Android 设备

![Power BI Desktop、Power BI 服务、Power BI 移动版](media/power-bi-overview/power-bi-blocks.png)

这三个元素&mdash;Power BI Desktop、 服务和移动应用&mdash;旨在让用户创建、 共享和使用方式最有效地提供服务，或其角色的业务见解。

使用第四个元素 Power BI 报表服务器  ，在 Power BI Desktop 中创建 Power BI 报表后，可以将其发布到本地报表服务器。 详细了解 [Power BI 报表服务器](#on-premises-reporting-with-power-bi-report-server)。

## <a name="how-power-bi-matches-your-role"></a>Power BI 如何与你的角色匹配
使用 Power BI 的方式取决于你在项目中的角色或你所在的团队。 其他人在其他角色，可以使用 Power BI 以不同的方式。

例如，你可能主要使用 Power BI 服务  。 但处理数字、生成业务报表的同事可能主要使用 Power BI Desktop  来创建报表，并将这些报表发布到 Power BI 服务，你可以在服务中查看这些报表。 另一个同事的销售额，可能主要使用其**Power BI 手机应用**其销售定额上监视进度并深入了解新的潜在销售顾客详细信息。

如果你是开发人员，可以使用 Power BI API 将数据推送到数据集或将仪表板和报表嵌入到你自己的自定义应用程序。 有关于新视觉对象的意见或建议？ 自行生成并与他人共享。  

此外可以使用 Power BI 的每个元素在不同的时间，具体取决于您尝试实现或你的角色对于给定的项目。

如何使用 Power BI 取决于 Power BI 的哪个功能或服务是适用的最佳工具。 例如，可以使用 Power BI Desktop 创建报表为你自己的团队有关客户参与统计信息，并可以查看库存和生产进度 Power BI 服务中的实时仪表板。 Power BI 的每个部分都可供使用，这正是 Power BI 极具灵活性和吸引力的原因所在。

浏览与你的角色相关的文档：
- 面向[***设计人员***](desktop-what-is-desktop.md)的 Power BI
- 面向[***使用者***](consumer/end-user-consumer.md)的 Power BI
- 面向[***开发人员***](developer/what-can-you-do.md)的 Power BI
- 面向[***管理员***](service-admin-administering-power-bi-in-your-organization.md)的 Power BI

## <a name="the-flow-of-work-in-power-bi"></a>Power BI 中的工作流
常见 Power BI 中的工作流首先连接到数据源和 Power BI Desktop 中生成报表。 然后发布到 Power BI 服务中，该报表从 Power BI Desktop，并将其共享，以便在 Power BI 服务和移动设备中的最终用户可以查看和与报表交互。
此工作流很常见，展示了三个主要的 Power BI 元素如何相互补充。

以下是 [Power BI Desktop 与 Power BI 服务比较](service-service-vs-desktop.md)的详情。

但是，如果你准备好移动到云，并且希望将报表保留在企业防火墙后，那该怎么做？  请继续阅读。

## <a name="on-premises-reporting-with-power-bi-report-server"></a>使用 Power BI 报表服务器的报告
创建、 部署和管理在本地的现成的工具和服务的 Power BI 报表服务器提供了一系列的 Power BI 移动和分页报表。

![针对本地的关系图](media/power-bi-overview/power-bi-report-server2.png)

Power BI 报表服务器是在防火墙后部署的一种解决方案，然后以不同方式将报表交付给正确用户，无论是在 Web 浏览器、移动设备还是在电子邮件中查看它们。 Power BI 报表服务器与云中的 Power BI 兼容，因此可以在就绪时转到云。 

详细了解 [Power BI 报表服务器](report-server/get-started.md)。

## <a name="next-steps"></a>后续步骤
- [快速入门：了解 Power BI 服务自己的方式](service-the-new-power-bi-experience.md)   
- [教程：开始使用 Power BI 服务](service-get-started.md)
- [快速入门：连接到 Power BI Desktop 中的数据](desktop-quickstart-connect-to-data.md)

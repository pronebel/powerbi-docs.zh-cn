---
title: Power BI 与 Power Automate 的集成
description: 了解如何创建由 Power BI 数据警报触发的 Power Automate 流。
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: YhmNstC39Mw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: aafba825c5bd4ece3c8b97256d5943f91b456cd7
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609692"
---
# <a name="power-automate-and-power-bi"></a>Power Automate 和 Power BI

[Power Automate](https://docs.microsoft.com/power-automate/getting-started) 是一款跨企业用户依赖的日益增多的应用程序和 SaaS 服务自动执行工作流的 SaaS。 使用 Power Automate，可以通过集成常用应用和服务（包括 Power BI）自动执行任务，从而获得通知、同步文件、收集数据等。 借助工作流自动化，执行重复任务不再是难事。

[立即开始使用 Power Automate。](https://docs.microsoft.com/power-automate/getting-started)

观看 Sirui 如何创建一个 Power Automate 流，在 Power BI 警报触发时向同事发送包含详细信息的电子邮件。 然后可以按照视频下面的分步说明来自己尝试。

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>创建由 Power BI 数据警报触发的流

### <a name="prerequisites"></a>先决条件
本教程介绍了如何创建两个不同的流：一个是通过模板创建，另一个是从头开始创建。 若要继续学习本教程，请[在 Power BI 中创建数据警报](service-set-data-alerts.md)，创建一个免费的 Slack 帐户，然后[注册 Power Automate](https://flow.microsoft.com/#home-signup)（此产品免费！）。

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>通过模板创建使用 Power BI 的流
在此任务中，我们使用模板创建一个由 Power BI 数据警报（通知）触发的简单流。

1. 登录 Power Automate (flow.microsoft.com)。
2. 选择“**我的流**”。
   
   ![Power Automate 菜单栏](media/service-flow-integration/power-bi-my-flows.png)
3. 选择“**使用模板创建**”。
   
    ![“我的流”菜单栏](media/service-flow-integration/power-bi-template.png)
4. 在搜索框中查找 Power BI 模板，然后选择“在触发 Power BI 数据警时，向任何受众发送电子邮件>继续”  。
   
    ![搜索结果](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>生成流
此模板包含一个触发器（通知爱尔兰新获奥运会奖牌的 Power BI 数据警报）和一个操作（发送电子邮件）。 在你选择字段的同时，Power Automate 会显示可以包含的动态内容。  在本示例中，我们在消息正文中添加磁贴值和磁贴 URL。

![流模板](media/service-flow-integration/power-bi-template1.png)

1. 在触发器下拉列表中，选择一个 Power BI 数据警报。 选择“**爱尔兰新获奖牌**”。 若要了解如何创建警报，请参阅 [Power BI 中的数据警报](service-set-data-alerts.md)。
   
   ![警报下拉列表](media/service-flow-integration/power-bi-trigger-flow.png)
2. 输入一个或多个有效电子邮件地址，然后选择“编辑”  （如下所示） 或“添加动态内容”  。 
   
   ![发送电子邮件屏幕](media/service-flow-integration/power-bi-flow-email.png)

3. Power Automate 会为你创建可保留或修改的标题和消息。 在 Power BI 中创建警报时设置的所有值都可供使用 -- 只需将光标置于其中并从灰色突出显示区域选择即可。 

   ![发送电子邮件屏幕](media/service-flow-integration/power-bi-flow-email-default.png)

1.  例如，如果你在 Power BI 中创建了警报标题“我们获得了另一枚奖牌”  ，则可以选择“警报标题”  将该文本添加到电子邮件的“主题”字段。

    ![创建电子邮件文本](media/service-flow-integration/power-bi-flow-message.png)

    而且，你可以接受默认电子邮件正文或自行创建正文。 以上示例包含对消息的一些修改。

1. 完成后，选择“创建流”  或“保存流”  。  此时，系统已创建并计算流。  Power Automate 会在有错误时提示你。
2. 如果有错误，请选择“**编辑流**”修复错误。如果没有错误，请选择“**完成**”运行这一新流。
   
   ![成功消息](media/service-flow-integration/power-bi-flow-running.png)
5. 触发数据警报时，将向你指定的地址发送一封电子邮件。  
   
   ![警报电子邮件](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-power-automate-that-uses-power-bi---from-scratch-blank"></a>从头开始创建使用 Power BI 的 Power Automate
在此任务中，我们从头开始创建一个由 Power BI 数据警报（通知）触发的简单流。

1. 登录 Power Automate。
2. 依次选择“我的流”   > “从头开始创建”  。
   
   ![Power Automate 顶部菜单栏](media/service-flow-integration/power-bi-my-flows.png)
3. 在搜索框中查找 Power BI 触发器，然后选择“Power BI - 当数据驱动警报触发时”  。

### <a name="build-your-flow"></a>生成流
1. 在下拉列表中，选择警报名称。  若要了解如何创建警报，请参阅 [Power BI 中的数据警报](service-set-data-alerts.md)。
   
    ![选择警报名称](media/service-flow-integration/power-bi-totalstores2.png)
2. 选择“新建步骤”   > “添加操作”  。
   
   ![添加新步骤](media/service-flow-integration/power-bi-new-step.png)
3. 搜索 **Outlook**，然后选择“**创建事件**”。
   
   ![生成流](media/service-flow-integration/power-bi-create-event.png)
4. 填写事件字段。 在你选择字段的同时，Power Automate 会显示可以包含的动态内容。
   
   ![继续生成流](media/service-flow-integration/power-bi-flow-event.png)
5. 完成后，选择“创建流”  。  此时，Power Automate 会保存并计算流。 如果没有错误，请选择“**完成**”运行此流。  此时，系统会将这一新流添加到“**我的流**”页中。
   
   ![完成流](media/service-flow-integration/power-bi-flow-running.png)
6. 当 Power BI 数据警报触发流时，你会收到如下 Outlook 事件通知。
   
    ![Power Automate 触发 Outlook 通知](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>后续步骤
* [开始使用 Power Automate](https://docs.microsoft.com/power-automate/getting-started/)
* [在 Power BI 服务中设置数据警报](service-set-data-alerts.md)
* [在 iPhone 上设置数据警报](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* [在适用于 Windows 10 的 Power BI 移动应用中设置数据警报](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


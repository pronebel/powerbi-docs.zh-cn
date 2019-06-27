---
title: Power BI 中的工作共享方式
description: 在 Power BI 中，可以通过不同的方式针对仪表板、报表、磁贴和应用开展协作并进行共享。 每种方法都各有千秋。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/07/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 00574228fbfa8954b8cfb9cb026a9230eb1bd73e
ms.sourcegitcommit: 206806d8ddb6bdfc322c1a46fb34a1b0678acba2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816547"
---
# <a name="ways-to-share-your-work-in-power-bi"></a>Power BI 中的工作共享方式

你已创建仪表板和报表。 可能也会和同事协作处理它们。 现在想让其他人有权限访问它们。 分发的最好方式是什么？ 在本文中，我们将对比 Power BI 中这些用于协作和共享选项：

* 在*工作区*中与同事进行协作，创建有价值的报表和仪表板。
* 将这些仪表板和报表打包为*应用*，并将其分发到更大的组或整个组织。
* 创建*共享数据集*，以便同事可以在其自己的工作区中将共享数据集用作其自己的报表的基础。
* 创建*模板应用*，以便通过 Microsoft AppSource 将其分发给外部 Power BI 用户。
* 通过服务或 Power BI 移动应用与几位用户共享仪表板或报表。
* 打印报表。
* 在安全门户或公共网站中*嵌入*报表。

无论选择哪个选项，都需要 [Power BI Pro 许可证](service-features-license-type.md)才能共享内容，否则内容需要位于[高级容量](service-premium-what-is.md)中。 许可证要求因查看内存的同事而异，具体取决于所选择的选项。 以下各节将进行详细说明。 

![Power BI 服务中的应用](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-apps-home-blog.png)

Power BI 服务中的应用 

## <a name="collaborate-in-a-workspace"></a>在工作区中协作

当团队协同工作时，他们需要访问相同的文档，以便快速协作。 在 Power BI 工作区中，团队能够共享其仪表板、报表、数据集和工作簿的所有权及管理权。 Power BI 用户组有时根据组织结构组织其工作区，而在其他时候为特定项目创建工作区。 仍有一些组织使用多个工作区来存储所用报表或仪表板的不同版本。 

工作区提供的角色可确定同事拥有的权限。 可使用这些角色来确定可以管理整个工作区或编辑其内容及分发其内容的人员。

![工作区](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-apps-workspaces.png)

可能会自然而然地将内容放在“我的工作区”中并从此处进行共享。 但是，工作区比“我的工作区”更适用于协作，因为前者允许共同拥有内容。 用户和整个团队可以轻松进行更新或为其他人授予访问权限。 “我的工作区”最适合个人用于一次性或个人内容。

假设需要与同事共享已完成的仪表板。 为他们提供仪表板访问权限的最佳方法是什么？ 答案取决于多种因素。 

- 如果同事需要使仪表板保持最新，或者需要访问工作区中的所有内容，请考虑将他们添加到工作区。 
- 如果同事只需要查看该仪表板而不是工作区中的所有内容，则可再次拥有备选方案。 如果几位用户只需要这一个仪表板，则共享该仪表板可能为最佳解决方案。
- 但是，如果仪表板是需要分发给许多同事的更大内容集的一部分，则发布*应用*可能为最佳选择。

Power BI 提供新的工作区体验。 阅读[创建新工作区](service-create-the-new-workspaces.md)，了解工作区发生的变化。 

## <a name="distribute-insights-in-an-app"></a>在应用中分发见解

假设想要将仪表板分发给组织中的广泛受众。 你和同事创建了工作区，然后在此工作区中创建并优化了仪表板、报表和数据集  。 现在选择所需的仪表板和报表，并将其作为应用发布 - 发布到组或整个组织。

![“发布应用”图标](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-app-publish-600.png)

可以在 Power BI 服务 ([https://powerbi.com](https://powerbi.com)) 中轻松找到应用并进行安装。 可以向业务用户发送应用的直接链接，或者他们可以在 AppSource 中搜索此应用。 如果 Power BI 管理员已授予你权限，则可以将应用自动安装到同事的 Power BI 帐户中。 阅读有关[发布应用](service-create-distribute-apps.md)的详细信息。

安装应用后，他们可以在浏览器或移动设备中查看应用。

对于查看你的应用的用户，他们同样需要拥有 Power BI Pro 许可证，或者应用需要存储在 Power BI 高级容量中。 请阅读[什么是 Power BI Premium？](service-premium-what-is.md)了解详细信息。

也可以将应用发布给组织外部的人员。 他们可以查看应用内容并与之交互，但无法与他人共享。 现在，可以创建*模板应用*并将它们部署到任何 Power BI 客户。

## <a name="share-a-dataset"></a>共享数据集

让我们面对现实，有些人更擅长在其报表中创建设计精良的高质量数据模型。 也许你就是那个人。 你的整个组织都能够因使用这一设计精良的数据模型而受益。 *共享数据集*可填补这一空缺。 使用每个人都应使用的数据模型创建报表时，可以将该报表保存到 Power BI 服务，并授予合适的人员使用它的权限。 他们随后可以基于你的数据集生成其报表。 这样一来，每个人都基于相同的数据创建其报表，并可看到“同一个版本的事实”。

详细了解[创建和使用共享数据集](service-datasets-across-workspaces.md)。

## <a name="share-dashboards-and-reports"></a>共享仪表板和报表

假设已在自己的“我的工作区”或工作区中完成仪表板和报表，并且希望某些其他人有权访问它。 一种用于访问的方法是  共享它。 

![“共享”图标](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-share-in-situ.png)

需要 Power BI Pro 许可证才能共享内容，你与之共享的人员也需要许可证才能共享，或者该内容需要位于[高级容量](service-premium-what-is.md)中的工作区内。 共享仪表板或报表时，收件人可以查看仪表板并与其交互，但无法对其进行编辑。 除非将行级别安全性 (RLS) 应用到基础数据集，否则他们会看到你在仪表板和报表中看到的相同数据。 如果你允许，与之共享的同事可以与其他同事共享。 

也可以与组织外的用户共享。 他们可以查看仪表板或报表并与之交互，但无法进行共享。 

有关从 Power BI 服务[共享仪表板和报表](service-share-dashboards.md)的详细信息。 此外，还可以向链接添加筛选器并[共享报表的筛选视图](service-share-reports.md)。

## <a name="annotate-and-share-from-the-power-bi-mobile-apps"></a>从 Power BI 移动应用添加批注并共享

在适用于 iOS 和 Android 设备的 Power BI 移动应用中，可以为磁贴、报表或视觉对象添加批注，并通过电子邮件与任何人共享。

![在移动应用中批注并共享](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-iphone-annotate.png)

在共享磁贴、报表或视觉对象快照时，收件人看到的与你发送邮件时的内容完全一致。 邮件还包含仪表板或报表的链接。 如果他们有 Power BI Pro 许可证，或者该内容位于[高级容量](service-premium-what-is.md)中，并且你已与他们共享对象，则他们可以打开此对象。 可以向任何人（不仅仅是同一电子邮件域的同事）发送磁贴的快照。

有关从 iOS 和 Android 移动应用[添加注释并共享磁贴、报表和视觉对象](consumer/mobile/mobile-annotate-and-share-a-tile-from-the-mobile-apps.md)的详细信息。

还可以通过适用于 Windows 10 设备的 Power BI 应用[共享磁贴快照](consumer/mobile/mobile-windows-10-phone-app-get-started.md)。

## <a name="print-or-save-as-pdf-or-other-static-file"></a>打印或另存为 PDF 或其他静态文件

可以在 Power BI 服务中打印整个仪表板、仪表板磁贴、报表页或可视化效果，或将其另存为 PDF（或其他静态文件格式）。 一次只能打印一页报表，而不能一次打印整个报表。 有关[打印或另存为静态文件](consumer/end-user-print.md)的详细信息。

## <a name="embed-reports-in-secure-portals-or-public-web-sites"></a>在安全门户或公共网站中嵌入报表

### <a name="embed-in-secure-portals"></a>在安全门户中嵌入

可以在用户希望看到 Power BI 报表的门户或网站中嵌入这些报表。  
利用 Power BI 服务中的“在 SharePoint Online 中嵌入”和“嵌入”选项，可以为内部用户安全地嵌入报告   。 

- “在 SharePoint Online 中嵌入”适用于 SharePoint Online 的 Power BI Web 部件  。 它提供单一登录体验，并可控制报表的嵌入方式。 
- **嵌入**适用于支持使用 URL 或 iFrame 嵌入内容的任何门户或网站。 

无论选择哪个选项，Power BI 都会强制执行所有权限和数据安全措施，然后才允许用户查看内容。 查看报告的人员需要具有相应许可证。 详细了解 Power BI 中的[在 SharePoint Online 中嵌入](service-embed-report-spo.md)和[嵌入](service-embed-secure.md)选项。

### <a name="publish-to-public-web-sites"></a>发布到公共网站

利用“发布到 Web”，可通过在任意设备上将交互式可视化效果嵌入到博客文章、网站、社交媒体以及其他联机交流媒介，来将 Power BI 报表发布到整个 Internet  。 Internet 上的任何人都可以查看你的报表，并且你无法控制谁可以查看已发布的内容。 他们不需要 Power BI 许可证。 只能将可以编辑的报表发布到 Web。 如果是与你共享的报表或者报表位于应用内部，则无法将其发布到 Web。 有关[发布到 Web](service-publish-to-web.md) 的详细信息。

>[!Warning]
>使用[发布到 Web](service-publish-to-web.md)只用于公开共享内容，而不用于内部共享。

## <a name="create-and-deploy-template-apps"></a>创建和部署模板应用

*模板应用*设计为公开分发，并通常在 Microsoft AppSource 中进行。 你会生成应用，并且在只需很少编码或无需编码的情况下，就可以将其部署到任何 Power BI 客户。 你的客户连接到其自己的数据并实例化其自己的帐户。 详细了解 [Power BI 模板应用](service-template-apps-overview.md)。


## <a name="next-steps"></a>后续步骤

* [与同事和他人共享仪表板](service-share-dashboards.md)
* [在 Power BI 中构建和发布应用](service-create-distribute-apps.md)
* [在安全门户或网站中嵌入报表](service-embed-secure.md)

想提供反馈？ 请转到 [Power BI 社区站点](https://community.powerbi.com/)提出你的建议。

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)

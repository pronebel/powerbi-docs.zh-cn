---
title: 在组织中分发模板应用 - Power BI
description: 了解如何在 Power BI 中安装、自定义和分发组织中的模板应用。
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/14/2019
ms.author: tebercov
ms.openlocfilehash: dcb037fdf064611947719a57316f31d901e3b81d
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2020
ms.locfileid: "73871421"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>在组织中安装和分发模板应用 - Power BI

你是 Power BI 分析师吗？ 如果是，本文将向你介绍如何安装模板应用以连接到多个运行 Salesforce、Microsoft Dynamics 和 Google Analytics 等业务的服务  。 可以修改仪表板和报表来满足组织的需要，然后将其作为应用分发给同事  。 

![已安装 Power BI 应用](media/service-template-apps-install-distribute/power-bi-get-apps.png)

如果你有兴趣创建自己分发的模板应用，请参阅[在 Power BI 中创建模板应用](service-template-apps-create.md)。 Power BI 合作伙伴几乎无需编码，即可构建 Power BI 应用，并将其部署到 Power BI 客户。 

## <a name="prerequisites"></a>先决条件  

以下是安装、自定义和分发模板应用的要求： 

- 一个 [Power BI Pro 许可证](service-self-service-signup-for-power-bi.md)
- 熟悉 [Power BI 的基本概念](service-basic-concepts.md)
- 来自模板应用创建者或 AppSource 的有效安装链接。 
- 安装模板应用的权限。 

## <a name="install-a-template-app"></a>安装模板应用

可能会收到指向模板应用的链接。 此外，可以在 AppSource 中搜索你感兴趣的内容。 无论哪种方式，在安装之后，都可以对其进行修改并将其分发给自己的组织。

### <a name="search-appsource-from-a-browser"></a>从浏览器中搜索 AppSource

在浏览器中，选择此链接以打开筛选为 Power BI 应用的 AppSource：

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>从 Power BI 服务中搜索 AppSource

1. 在 Power BI 服务的导航窗格中，选择“应用” > “获取应用”   。

    ![获取应用](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. 在 AppSource 中，选择“应用”  。

    ![在 AppSource 中搜索](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. 浏览或搜索该应用，然后选择“立即获取”  。

4. 在对话框中，选择“安装”  。

    ![安装应用](media/service-template-apps-install-distribute/power-install-dialog.png) 如果拥有 Power BI Pro 许可证，则会安装该应用及其关联的工作区。 可以在关联的工作区中自定义应用。

    安装成功后，会看到新应用已就绪的通知。
4. 选择“转到应用”  。
5. 在“开始使用新应用”中，请选择以下三个选项之一  ：

    ![开始使用应用](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **浏览应用**：基本示例数据浏览。 从这里开始，了解应用的外观。 
    - **连接数据**：将数据源从示例数据更改为自己的数据源。 可以重新定义数据集参数和数据源凭据。 请参阅模板应用提示文章中的[已知限制](service-template-apps-tips.md#known-limitations)。 
    - “转到工作区”（最高级选项）：可以进行应用生成器允许的任何更改  。

    或者跳过此对话框，直接通过导航窗格中的“工作区”访问关联的工作区  。
    >[!NOTE]
    >安装模板应用，会同时安装组织应用和工作区   。 详细了解如何[在 Power BI 中分发应用](service-create-distribute-apps.md)。
 
6. 在与同事共享之前，需要连接到自己的数据。 可能还希望修改报表或仪表板，使其适用于组织。 还可以在此处添加其他报表或仪表板。

   如果选择未在 AppSource 上列出的应用的安装链接，将获得要求你确认所作选择的验证对话框。

   ![安装应用](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >要安装未在 AppSource 上列出的模板应用，需要从管理员权限进行请求。 有关详细信息，请参阅 Power BI [管理门户的模板应用设置](service-admin-portal.md#template-apps-settings)。

## <a name="customize-and-publish-the-app"></a>自定义并发布应用

在为组织更新应用后，即可将其发布。 这些步骤与发布任何其他应用的步骤相同。

1. 完成自定义后，在工作区列表视图中选择右上角的“更新应用”  。  

    ![开始安装应用](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. 在“详细信息”中，可以修改说明和背景颜色  。

   ![设置应用说明和颜色](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. 在“导航”中，可以为应用使用新导航生成器，或者为登陆页选择仪表板或报表  。 有关详细信息，请参阅[设计导航体验](service-create-distribute-apps.md#design-the-navigation-experience)。

   ![设置应用登陆页面](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. 在“访问”中，可向所选用户或整个组织授予访问权限  。  

   ![设置应用访问](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. 选择“更新应用”  。 

6. 成功发布后，可以复制链接并与被授予访问权限的任何人共享。 如果你与他们共享，他们也会在 AppSource 的“我的组织”标签上看到此内容  。

## <a name="update-a-template-app"></a>更新模板应用

模板应用的创建者可以通过 AppSource 或直接链接发布其模板应用的新版本。 完成后，可以在使用相同或更高版本重新安装模板应用时更新模板应用。

  >[!NOTE]
  >安装新版本会覆盖对报表和仪表板所做的任何更改。 若要保留更新的报表和仪表板，可以在安装前用其他名称或位置保存它们。

- **覆盖现有版本：** 使用模板应用的更新版本覆盖现有工作区。

   ![更新模板应用](media/service-template-apps-install-distribute/power-bi-update-app-overwrite.png)

- **安装到新工作区：** 安装需要重新配置的工作区和应用的新版本

### <a name="overwrite-behavior"></a>覆盖行为

* 覆盖会更新*工作区*（而非应用）中的报表、仪表板和数据集。 覆盖不会更改应用的导航、设置和权限。
* 更新工作区后，需要*更新应用*，以将更改从工作区应用于组织应用。
* 覆盖将保留配置的参数和身份验证。 更新后，数据集会开始自动刷新。 在此期间，组织应用、报表和仪表板将提供*示例数据*体验。
  ![示例数据](media/service-template-apps-install-distribute/power-bi-sample-data.png)
* 覆盖始终显示示例数据，直到刷新完成。 如果模板应用的作者对数据集或参数进行了更改，则工作区和应用的用户将继续看到*示例数据*体验。
* 覆盖绝不会删除添加到工作区的*新*报表或仪表板。 它会使用原始作者的更改覆盖原始报表和仪表板。

>[!IMPORTANT]
>切记在覆盖后[更新应用](#customize-and-publish-the-app)，以将更改应用于组织应用用户的报表和仪表板。

## <a name="next-steps"></a>后续步骤

[与同事一起在 Power BI 中创建工作区](service-create-workspaces.md)

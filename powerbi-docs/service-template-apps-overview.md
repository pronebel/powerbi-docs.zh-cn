---
title: 什么是 Power BI 模板应用？
description: 本文概述了 Power BI 模板应用程序。 了解如何在具有极少编码或无编码的情况下生成 Power BI 应用，并将其部署到任何 Power BI 客户。
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: tebercov
ms.openlocfilehash: c05b53a5fd61d348b6d304b17123d5f2497ab647
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408216"
---
# <a name="what-are-power-bi-template-apps"></a>什么是 Power BI 模板应用？

新的 Power BI 模板应用使 Power BI 合作伙伴能够在极少编码或没有编码的情况下生成 Power BI 应用，并将它们部署到任何 Power BI 客户  。  本文概述了 Power BI 模板应用程序。

模板应用是当前服务内容包的替代品。 作为 Power BI 合作伙伴，你可以为客户创建一组现成可用的内容，并自行发布。  

生成模板应用，允许客户使用其自己的帐户连接并实例化。 对于域专业人员而言，可采用便于业务用户使用的方式来解锁数据。  

将模板应用提交到云合作伙伴门户。 然后，这些应用将在 Power BI 应用库 (app.powerbi.com/getdata/services) 和 Microsoft AppSource (appsource.microsoft.com) 上公开发布。 下文深入介绍了公共模板应用创建体验。  

## <a name="process"></a>过程
开发和提交模板应用的常规过程涉及多个步骤。 某些阶段可能同时包含多个活动。


| 阶段 | Power BI Desktop |  |Power BI 服务  |  |云合作伙伴门户  |
|---|--------|--|---------|---------|---------|
| **一** | 在 .pbix 文件中生成数据模型和报表 |  | 创建工作区。 导入 .pbix 文件。 创建互补仪表板  |  | 注册为合作伙伴 |
| **二** |  |  | 创建测试包并运行内部验证        |  | |
| **三** | |  | 在 Power BI 租户之外将测试包提升到预生产以进行验证，并将其提交给 AppSource  |  | 使用预生产包，创建 Power BI 模板应用产品/服务并启动验证过程 |
| **四** | |  | 将预生产包提升到生产 |  | 投入使用 |

## <a name="before-you-begin"></a>开始之前

若要创建模板应用，需要权限以进行创建。 有关详细信息，请参阅 Power BI 管理门户的模板应用设置。 

若要将模板应用发布到 Power BI 服务和 AppSource，必须满足[成为云市场发布者](https://docs.microsoft.com/azure/marketplace/become-publisher)的要求。
 
## <a name="high-level-steps"></a>高级步骤

高级步骤如下。 

1. [查看要求](#requirements)以确保满足这些要求。 

1. 在 Power BI Desktop 中生成一个报表。 使用参数，以便将其保存为其他人可以使用的文件。 

1. 在 Power BI 服务 (app.powerbi.com) 的租户中，为模板应用创建工作区。 

1. 导入 .pbix 文件并向应用添加仪表板等内容。 

1. 创建测试包以在组织内自己测试模板应用。 

1. 将测试应用提升到预生产，以在 AppSource 中提交应用进行验证，并在自己的租户之外进行测试。 

1. 将内容提交到“云合作伙伴平台”进行发布。 

1. 让产品/服务在 AppSource 中“实时”运行，并将应用移至 Power BI 中的生产。
2. 现在，可以在预生产中开始在同一工作区中开发下一个版本。 

## <a name="requirements"></a>要求

若要创建模板应用，需要权限以进行创建。 有关详细信息，请参阅 Power BI [管理门户的模板应用设置](service-admin-portal.md#template-apps-settings)。 

若要将模板应用发布到 Power BI 服务和 AppSource，必须满足[成为云市场发布者](https://docs.microsoft.com/azure/marketplace/become-publisher)的要求。
 > [!NOTE] 
 > 模板应用提交内容在[云合作伙伴门户](https://cloudpartner.azure.com)中进行管理。 使用同一 Microsoft 开发人员中心注册帐户进行登录。 你的 AppSource 产品/服务应只有一个 Microsoft 帐户。 帐户不得特定于单个服务或产品。

## <a name="tips"></a>提示 

- 确保应用包含示例数据，以便每个人都可单击使用。 
- 通过将应用程序安装在租户和二级租户中，以对该应用程序进行仔细检查。 确保客户只看到你希望他们看到的内容。 
- 使用 AppSource 作为在线商店来托管应用程序。 这样，使用 Power BI 的任何人都可以找到你的应用。 
- 考虑为分开的独特方案提供多个模板应用。 
- 启用数据自定义，例如，安装程序支持自定义连接和参数配置。

要获取更多建议，请参阅[有关在 Power BI 创作模板应用的提示](service-template-apps-tips.md)。

## <a name="support"></a>支持
若要在开发过程中获取支持，请访问 [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support)。 我们积极监视和管理此网站。 客户事件可快速找到通往合适团队的方法。

## <a name="next-steps"></a>后续步骤

[创建模板应用](service-template-apps-create.md)

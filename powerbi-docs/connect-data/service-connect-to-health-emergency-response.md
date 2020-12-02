---
title: 连接到医院紧急响应决策支持仪表板
description: 如何获取和安装用于医疗保健紧急模板应用的 COVID-19 决策支持仪表板，以及如何连接到数据
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/13/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 823c8429c95a0b4d858540b2cf1183ca1c7caac7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403136"
---
# <a name="connect-to-the-hospital-emergency-response-decision-support-dashboard"></a>连接到医院紧急响应决策支持仪表板
医院应急响应决策支持仪表板模板应用是[用于医疗保健应急响应的 Microsoft Power Platform 解决方案](https://powerapps.microsoft.com/blog/emergency-response-solution-a-microsoft-power-platform-solution-for-healthcare-emergency-response/)的报告组件。 仪表板显示整个健康状况系统中紧急管理器的聚合数据，可帮助他们及时做出正确的决策。

![医院紧急响应决策支持仪表板应用报表](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-report.png)

本文介绍如何安装应用以及如何连接到数据源。 若要了解如何使用通过此应用看到的报表，请参阅[医院紧急响应决策支持仪表板文档](/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)。

安装模板应用并连接到数据源后，可以根据需要对报表进行自定义。 然后可以将其作为应用分发给组织中的同事。

## <a name="prerequisites"></a>先决条件

安装此模板应用之前，需要先安装和设置[医院紧急响应 Power Platform 解决方案](/powerapps/sample-apps/emergency-response/deploy-configure)。 安装此解决方案将创建使用数据填充应用时所需的数据源引用。

安装医院紧急响应 Power Platform 解决方案时，请记下 [Common Data Service 环境实例的 URL](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard)。 将模板应用连接到数据时需要使用它。

## <a name="install-the-app"></a>安装应用

1. 单击以下链接可转到该应用：[医院紧急响应决策支持仪表板模板应用](https://aka.ms/AppSource_Hospital_offer)

1. 在应用的 AppSource 页面，选择“[立即获取](https://aka.ms/AppSource_Hospital_offer)”  。

    [![AppSource 中的医院紧急响应决策支持仪表板应用](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-appsource-get-it-now.png)](https://aka.ms/AppSource_Hospital_offer)

1. 阅读“另一件事”中的信息，然后选择“继续”   。

    ![医院紧急响应决策支持仪表板应用, 另一件事](media/service-connect-to-health-emergency-response/service-health-emergency-response-1-more-thing.png)

1. 选择“安装”  。 

    ![安装医院应急响应决策支持仪表板应用](media/service-connect-to-health-emergency-response/service-health-emergency-response-select-install.png)

    安装应用后，你将在应用页面上看到它。

   ![应用页面上的医院紧急响应决策支持仪表板应用](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>连接到数据源

1. 选择应用页面上的图标以打开应用。

1. 在初始屏幕上，选择“浏览”  。

   ![模板应用初始屏幕](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-splash-screen.png)

   应用将打开，显示示例数据。

1. 选择页面顶部横幅上的“连接数据”链接  。

   ![医院紧急响应决策支持仪表板应用连接数据链接](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-connect-data.png)

1. 在对话框中：
   1. 在组织名称字段中，输入组织的名称，例如“Contoso 健康状况系统”。 此字段可选。 此名称显示在仪表板的左上角。
   1. 在 CDS_base_solution 字段中，键入 [Common Data Service 环境实例的 URL](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard)。 例如： https://[myenv].crm.dynamics.com。 完成后单击“下一步”  。

   ![医院紧急响应决策支持仪表板应用报表 URL 对话框](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-url-dialog.png)

1. 在出现的下一个对话框中，将身份验证方法设置为 OAuth2  。 不必对隐私级别设置执行任何操作。

   选择“登录”  。

   ![医院紧急响应决策支持仪表板应用身份验证对话框](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-authentication-dialog.png)

1. 在 Microsoft 登录屏幕，登录到 Power BI。

   ![Microsoft 登录屏幕](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-microsoft-login.png)

   登录后，报表将连接到数据源，并填充了最新的数据。 在此期间，活动监视器将转动。

   ![刷新中的医院紧急响应决策支持仪表板应用](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>计划报表刷新

完成数据刷新后，[设置刷新计划](../connect-data/refresh-scheduled-refresh.md)以保持报表数据为最新状态。

1. 在顶部标题栏中，选择“Power BI”  。

   ![Power BI 痕迹导航](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-powerbi-breadcrumb.png)

1. 在左侧导航窗格中，查找“工作区”下的医院紧急响应决策支持仪表板工作区，然后按照[配置计划刷新](../connect-data/refresh-scheduled-refresh.md)一文中所述的说明进行操作  。

## <a name="customize-and-share"></a>自定义和共享

有关详细信息，请参阅[自定义和共享应用](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)。 在发布或分发应用之前，请务必查看[报告免责声明](../create-reports/sample-covid-19-us.md#disclaimers)。

## <a name="next-steps"></a>后续步骤
* [了解医院紧急响应报表](/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)
* [在 Power Apps 中设置并了解危机通信示例模板](/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
* [什么是 Power BI 模板应用？](../connect-data/service-template-apps-overview.md)
* [在组织中安装和分发模板应用](../connect-data/service-template-apps-install-distribute.md)
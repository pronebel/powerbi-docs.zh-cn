---
title: 连接到 COVID-19 美国跟踪报表
description: 如何获取和安装 COVID-19 美国案例模板应用，以及如何连接到数据。
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/05/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 01dab6cad6142b455a0d61a0011e43cea6da23e1
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349478"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>连接到 COVID-19 美国跟踪报表
本文介绍如何安装 COVID-19 跟踪报告的模板应用，以及如何连接到数据源。

![COVID-19 美国跟踪报告](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

有关报表本身的详细信息（包括免责声明和数据信息），请参阅[美国州和地方政府的 COVID-19 跟踪示例](../create-reports/sample-covid-19-us.md)。

安装模板应用并连接到数据源后，可以根据需要对报表进行自定义。 然后可以将其作为应用分发给组织中的同事。

## <a name="install-the-app"></a>安装应用

1. 单击以下链接可转到该应用：[COVID-19 美国跟踪报表模板应用](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. 在应用的 Appsource 页面上，单击“[立即获取](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)”  。

    [![Appsource 中的 Covid-19 美国跟踪报表](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. 出现提示时，单击“安装”  。 应用安装后，应用页面上会显示。

   ![应用页面上的 COVID-19 美国跟踪报表](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>连接到数据源

1. 单击应用页面上的图标以打开应用。

1. 在出现的初始屏幕上，选择“连接”  。

   ![模板应用初始屏幕](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-splash-screen.png)

1. 随即出现“参数”对话框。 没有必需的参数。 单击“下一步”  。

   ![Covid-19 美国跟踪报表“参数”对话框的屏幕截图。](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-parameters-dialog.png)

1. 随即显示“身份验证方法”对话框。 已预填充建议值。 除非对不同的值有明确的了解，否则请不要更改这些值。

    单击“下一步”  。

   ![Covid-19 美国跟踪报表“身份验证”对话框的屏幕截图。](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-authentication-dialog.png)

1. 单击“登录”  。

   ![Covid-19 美国跟踪报表“登录”对话框的屏幕截图。](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)
 
   报表将连接到数据源，并用最新的数据进行填充。 在此期间，你将看到示例数据，且正在进行刷新。

   ![刷新中的 Covid-19 美国跟踪报表](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>计划报表刷新

数据刷新完成后，你将位于与应用关联的工作区中。 [设置刷新计划](../connect-data/refresh-scheduled-refresh.md)以保持报表数据为最新状态。

## <a name="customize-and-share"></a>自定义和共享

有关详细信息，请参阅[自定义和共享应用](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)。 在发布或分发应用之前，请务必查看[报告免责声明](../create-reports/sample-covid-19-us.md#disclaimers)。

## <a name="next-steps"></a>后续步骤
* [适用于美国各州和地方政府的 COVID-19 跟踪示例](../create-reports/sample-covid-19-us.md)
* 是否有任何问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
* [什么是 Power BI 模板应用？](../connect-data/service-template-apps-overview.md)
* [在组织中安装和分发模板应用](../connect-data/service-template-apps-install-distribute.md)

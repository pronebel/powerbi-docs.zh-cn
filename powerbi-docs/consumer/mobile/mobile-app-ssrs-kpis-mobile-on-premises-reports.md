---
title: 在 Power BI 移动应用中查看本地报表和 KPI
description: 使用 Power BI 移动应用，可以通过触控移动设备实时访问 SQL Server Reporting Services 和 Power BI 报表服务器中的本地业务信息。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/05/2019
ms.author: painbar
ms.openlocfilehash: 2f6d02d6128a2896a19d87f30f46f26f101385f6
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90860983"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>在 Power BI 移动应用中查看本地报表服务器报表和 KPI

使用 Power BI 移动应用，可以通过触控移动设备实时访问 Power BI 报表服务器和 SQL Server 2016 Reporting Services (SSRS) 中的本地业务信息。

适用于：

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android 手机](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android 平板电脑](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone |iPad |Android 手机 |Android 平板电脑 |


![移动应用中的报表服务器主文件夹](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>要做的第一件事
移动应用是用于查看 Power BI 内容（而不是创建内容）的地方。 

* 你和组织中的其他报表创建者可以[使用 Power BI Desktop 创建 Power BI 报表，然后将报表发布到 Power BI 报表服务器 Web 门户中](../../report-server/quickstart-create-powerbi-report.md)。 
* 可以[在 Web 门户中直接创建 KPI](/sql/reporting-services/working-with-kpis-in-reporting-services)，将它们整理到文件夹中，然后标记为收藏项，方便你快速找到。 
* 可以使用 SQL Server 2016 企业版移动报表发布服务器[生成 Reporting Services 移动报表](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher)，然后将其发布到 [Reporting Services Web 门户](/sql/reporting-services/web-portal-ssrs-native-mode)。  

然后，在 Power BI 移动应用中，最多连接五个报表服务器，以查看整理到文件夹中或标记为收藏项的 Power BI 报表和 KPI。 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>不使用服务器连接在移动应用中探索示例
即使无权访问 Reporting Services Web 门户，也仍可以探索 Reporting Services 移动报表和 KPI 的功能。 

1. 点击左上角的个人资料图片，然后在滑出的“帐户”面板上点击“设置”  。

2. 在打开的“设置”页上，点击“Reporting Services 示例”，然后转到相应位置，与示例 KPI 和移动报表进行交互  。
   
   ![Reporting Services 示例](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>连接到本地报表服务器
可以在 Power BI 移动应用中查看本地 Power BI 报表、Reporting Services 移动报表和 KPI。 

1. 在移动设备中，打开 Power BI 应用。
2. 如果你尚未登录到 Power BI，请点击“报表服务器”  。
   
   ![登录报表服务器](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   如果已登录到 Power BI 应用，请点击左上角的个人资料图片，然后在滑出的“帐户”窗格上点击“设置”  。
3. 在打开的“设置”页上，点击“连接到服务器”  。
   
    ![连接到服务器](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

    移动应用需要以某种方式访问服务器。 可通过多种方法实现此目的：
     * 使用相同的网络/VPN 是最简单的方法。
     * 可以使用 Web 应用程序代理从组织外部建立连接。 有关详细信息，请参阅[使用 OAuth 连接到 Reporting Services](mobile-oauth-ssrs.md)。
     * 在防火墙中打开连接（端口）。

4. 填写服务器地址，并为服务器指定一个易记名称（如果需要）。 对服务器地址使用如下格式：
   
     `https://<servername>/reports`
   
     OR
   
     `https://<servername>/reports`
   
   在连接字符串前面加上 **http** 或 **https**。
   
    ![“连接到服务器”对话框](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. 键入服务器地址和可选易记名称后，点击“连接”，然后在出现提示时填写用户名和密码  。
6. 现在，可以在“帐户”窗格中看到该服务器 - 在此示例中，它名为“工作服务器”。
   
   ![导航窗格中的报表服务器](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios-or-android"></a>在 iOS 或 Android 中连接到本地报表服务器

如果你在 iOS 或 Android 移动应用中查看 Power BI，IT 管理员可能定义了应用配置策略。 如果是这样，连接报表服务器的体验就会得到简化，连接报表服务器时不需要提供这么多的信息。 

1. 你将看到一条消息，表示以为移动应用配置报表服务器。 点击“登录”  。

    ![登录报表服务器](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  在“连接到服务器”页上，已填写报表服务器详细信息  。 点击“连接”  。

    ![已填写报表服务器详细信息](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. 键入密码进行身份验证，然后点击“登录”  。 

    ![已填写报表服务器详细信息](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

现在，你可以查看存储在报表服务器上的 KPI 和 Power BI 报表并与之交互。

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>在 Power BI 应用中查看 Power BI 报表和 KPI
Power BI 报表、Reporting Services 移动报表和 KPI 的文件夹与它们在 Reporting Services Web 门户上的文件夹相同。 

* 点击 Power BI 报表 ![Power BI 报表图标](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png)。 它将以横向模式打开，并可在 Power BI 应用中与之交互。

    > [!NOTE]
  > Power BI 报表服务器上的 Power BI 报表中当前未启用向下钻取和向上钻取功能。
  
    ![Power BI 报表](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* 在 Power BI Desktop 中，报表所有者可以为 Power BI 移动应用[优化报表](../../create-reports/desktop-create-phone-report.md)。 在你的移动手机上，已优化的报表都具有一个特殊的图标 ![Optimized Power BI report icon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png)和布局。
  
    ![为移动设备优化的 Power BI 报表](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* 点击 KPI 以在焦点模式中查看它。
  
    ![焦点模式下的 KPI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>查看你收藏的 KPI 和报表
可以在 Web 门户上将 KPI 和报表标记为收藏项，然后在移动设备上的一个方便使用的文件夹中查看它们，以及收藏的 Power BI 仪表板。

* 在导航栏上点击“收藏”  。
  
   ![导航窗格中的收藏夹](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   你在 Web 门户中收藏的 KPI 和报表，以及 Power BI 服务中的 Power BI 仪表板全都在此页上：
  
   ![“收藏夹”页中的 Power BI 报表和仪表板](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>删除与报表服务器的连接
1. 打开“帐户”窗格，点击“设置”  。
2. 点击不想连接到的服务器的名称。
3. 点击“**删除服务器**”。

## <a name="next-steps"></a>后续步骤
* [什么是 Power BI？](../../fundamentals/power-bi-overview.md)  
* 是否有任何问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
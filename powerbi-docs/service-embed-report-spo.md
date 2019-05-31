---
title: 使用报表 Web 部件在 SharePoint Online 中嵌入报表
description: 借助 Power BI 新推出的适用于 SharePoint Online 的报表 Web 部件，可以在 SharePoint Online 页面中轻松嵌入交互式 Power BI 报表。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051264"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>使用报表 Web 部件在 SharePoint Online 中嵌入报表

借助 Power BI 新推出的适用于 SharePoint Online 的报表 Web 部件，可以在 SharePoint Online 页面中轻松嵌入交互式 Power BI 报表。

使用新**在 SharePoint Online 中的嵌入**选项时，嵌入的报表都是完全安全，因此可以轻松创建安全的内部门户。

## <a name="requirements"></a>要求

有关**在 SharePoint Online 中的嵌入**报表才能正常，需要满足以下条件：

* Power BI Pro 许可证或[Power BI Premium 容量 （EM 或 P SKU）](service-premium-what-is.md)与 Power BI 许可证。
* 适用于 SharePoint Online 的 Power BI Web 部件要求使用[新式页面](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)。

## <a name="embed-your-report"></a>嵌入报表
若要将报表嵌入到 SharePoint Online，您需要获取报表 URL 并将其用于 SharePoint Online 的新的 Power BI web 部件。

### <a name="get-a-report-url"></a>获取报表 URL

1. Power BI 中查看报表。

2. 选择**文件**下拉列表菜单，然后选择**在 SharePoint Online 中的嵌入**。

    ![文件菜单](media/service-embed-report-spo/powerbi-file-menu.png)

3. 从对话框复制报表 URL。

    ![嵌入链接](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>将 Power BI 报表复制到 SharePoint Online 页面

1. 在 SharePoint Online 中打开目标页，然后选择**编辑**。

    ![SP 编辑页面](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    或者，在 Sharepoint Online 中，选择 **+ 新建**来创建一个新的新式网站页面。

    ![SP 新建页面](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. 选择 **+** 下拉列表中，然后选择**Power BI**。

    ![SP 新 Web 部件](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. 选择“**添加报表**”。

    ![SP 新报表](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. 粘贴前面复制的报表 URL 传入**Power BI 报表链接**窗格。 报表会自动加载。

    ![SP 新 Web 部件属性](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. 选择“**发布**”，让 SharePoint Online 用户可以看到此更改。

    ![加载的 SP 报表](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>授予报表访问权限

在 SharePoint Online 中嵌入报表不会自动向用户授予权限以查看报表-你需要在 Power BI 中设置的查看权限。

> [!IMPORTANT]
> 请务必在 Power BI 中检查哪些人员可以查看报表，然后向未列出的人员授予访问权限。

有两种方法来提供 Power BI 中的报表访问权限。 第一种方法，如果要使用 Office 365 组生成 SharePoint Online 团队网站，是将用户列为隶属**Power BI 服务中的应用工作区**并**SharePoint 页**。 有关详细信息，请参阅如何[管理应用工作区](service-manage-app-workspace-in-power-bi-and-office-365.md)。

第二种方法是嵌入在应用中的报表并直接与用户共享：  

1. 作者 （需要是 Pro 用户） 在应用工作区中创建报表。 与共享**Power BI 免费用户**，需要将其设置为应用工作区**Premium 工作区**。

2. 作者会将应用发布，并将其安装。 创建者需要确保安装应用程序具有对用于在 SharePoint Online 中嵌入报表 URL 的访问。

3. 此时，所有最终用户也必须要安装应用。 此外可以使用**自动安装应用**功能，则可以在启用[Power BI 管理门户](service-admin-portal.md)来获得预安装为最终用户的应用程序。

   ![自动安装应用](media/service-embed-report-spo/install-app-automatically.png)

4. 作者打开应用并转到报表。

5. 作者将报告安装的应用程序复制嵌入报表 URL。 **不要从应用工作区中使用原始报表 URL。**

6. 在 SharePoint Online 中新建团队网站。

7. 将前面复制的报表 URL 添加到 Power BI web 部件。

8. 添加将使用 SharePoint Online 页面和已创建 Power BI 应用中的数据的所有最终用户和/或组。

    > [!NOTE]
    > 用户或组必须同时有权访问 SharePoint Online 页面和 Power BI 应用中的报表，才能查看 SharePoint 页面上的报表。 

此时，最终用户可以转到 SharePoint Online 中的团队网站，并能查看页面上的报表。

## <a name="multi-factor-authentication"></a>多重身份验证

如果 Power BI 环境要求使用多重身份验证进行登录，系统可能会提示使用安全设备登录，从而验证身份。 如果没有未登录到 SharePoint Online 使用多重身份验证，但 Power BI 环境要求使用安全设备来验证帐户，将发生这种情况。

> [!NOTE]
> Azure Active Directory 2.0 不支持多重身份验证-用户将看到一条错误消息。 如果用户使用安全设备重新登录 SharePoint Online，则可查看报表。

## <a name="web-part-settings"></a>Web 部件设置

下面是可以为 SharePoint Online 的 Power BI web 部件调整的设置。

![SP Web 部件属性](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| 属性 | 说明 |
| --- | --- |
| 页面名称 |设置 web 部件的默认页。 从下拉列表中选择一个值。 如果下拉列表中未显示任何页，要么是因为报表只有一页，要么是因为粘贴的 URL 包含页名称。 从 URL 中删除报表部分即可选择特定页。 |
| 显示 |调整报表如何在 SharePoint Online 页面内适用。 |
| 显示导航窗格 |显示或隐藏报表页导航窗格。 |
| 显示筛选窗格 |显示或隐藏筛选窗格。 |

## <a name="reports-that-do-not-load"></a>报表没有加载

如果您的报表不会加载 Power BI web 部件中，可能会看到以下消息：

![此内容不是可用的消息](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

看见此消息的常见原因有两个。

1. 你没有报表访问权限。
2. 报表已遭删除。

请联系 SharePoint Online 的页所有者，以帮助解决此问题。

## <a name="licensing"></a>许可

在 SharePoint 中查看报表的用户需要具有 Power BI Pro 许可证  ，或该内容需要位于 [Power BI Premium 容量（EM 或 P SKU）](service-admin-premium-purchase.md)  中的工作区中。

## <a name="known-issues-and-limitations"></a>已知问题和限制

* 错误：“出错，请尝试注销并重新登录，然后重新访问此页。 相关 ID: 未定义，http 响应状态: 400，服务器错误代码 10001，消息: 缺少刷新令牌”
  
  如果收到此错误，请尝试以下故障排除步骤之一。
  
  1. 注销并重新登录 SharePoint。 请务必在重新登录前关闭所有浏览器窗口。

  2. 如果您的用户帐户需要多重身份验证 (MFA)，然后登录到 SharePoint 使用 MFA 设备 （手机应用、 智能卡等）。
  
  3. 不支持 Azure B2B 来宾用户帐户。 用户将看到 Power BI 徽标，显示该部件正在加载，但它不会显示报表。

* Power BI 不支持 SharePoint Online 支持的本地化语言。 因此，可能无法在嵌入的报表中看到正确的本地化内容。

* 如果使用的是 Internet Explorer 10，可能会遇到问题。 可以查看 [Power BI 支持的浏览器](consumer/end-user-browsers.md)和 [Office 365 支持的浏览器](https://products.office.com/office-system-requirements#Browsers-section)。

* Power BI Web 部件不适用于[国家云](https://powerbi.microsoft.com/clouds/)。

* 此 Web 部件不支持经典 SharePoint Server。

* SPO Web 部件不支持[URL 筛选器](service-url-filters.md)。

## <a name="next-steps"></a>后续步骤

* [允许或禁止最终用户创建新式网站页面](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [在 Power BI 中构建和分发应用](service-create-distribute-apps.md)  
* [与同事和其他人共享仪表板](service-share-dashboards.md)  
* [什么是 Power BI Premium？](service-premium-what-is.md)
* [在安全门户或网站中嵌入报表](service-embed-secure.md)

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
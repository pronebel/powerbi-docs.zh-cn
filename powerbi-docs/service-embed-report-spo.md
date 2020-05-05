---
title: 在 SharePoint Online 中嵌入报表 Web 部件
description: 借助 Power BI 新推出的适用于 SharePoint Online 的报表 Web 部件，可以在 SharePoint Online 页面中轻松嵌入交互式 Power BI 报表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 04/27/2020
ms.openlocfilehash: 5b726137fae0087701833b2d713cf7b5a329f899
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "82585226"
---
# <a name="embed-a-report-web-part-in-sharepoint-online"></a>在 SharePoint Online 中嵌入报表 Web 部件

借助 Power BI 新推出的适用于 SharePoint Online 的报表 Web 部件，可以在 SharePoint Online 页面中轻松嵌入交互式 Power BI 报表。

使用新增的“在 SharePoint Online 中嵌入”选项时，嵌入的报表绝对安全，因此你可以轻松创建安全的内部门户  。

## <a name="requirements"></a>要求

若要使“在 SharePoint Online 中嵌入”报表生效，以下是必需项  ：

* Power BI Pro 许可证或具有 Power BI 许可证的 [Power BI Premium 容量（EM 或 P SKU）](service-premium-what-is.md)。
* 适用于 SharePoint Online 的 Power BI Web 部件要求使用[新式页面](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)。
* 若要使用嵌入的报表，用户必须登录到 Power BI 服务以激活其 Power BI 许可证。

## <a name="embed-your-report"></a>嵌入报表
若要将报表嵌入到 SharePoint Online，你需要获取报表 URL 并将其用于 SharePoint Online 的 Power BI Web 部件。

### <a name="get-a-report-url"></a>获取报表 URL

1. 在 Power BI 中查看报表。

2. 在“更多选项 (...)”  下拉菜单中，选择“嵌入”   > “SharePoint Online”  。

    ![SharePoint Online 中的“更多选项”菜单](media/service-embed-report-spo/power-bi-more-options-sharepoint-online.png)

3. 复制对话框的报表 URL。

    ![嵌入链接](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>将 Power BI 报表复制到 SharePoint Online 页面

1. 打开 SharePoint Online 中的目标页面，然后选择“编辑”  。

    ![SP 编辑页面](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    或者，在 SharePoint Online 中选择“+ 新建”，新建新式网页  。

    ![SP 新建页面](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. 选择 + 下拉列表，然后选择 Power BI Web 部件   。

    ![SP 新 Web 部件](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. 选择“**添加报表**”。

    ![SP 新报表](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. 将之前复制的报表 URL 粘贴到“Power BI 报表链接”窗格  。 报表会自动加载。

    ![SP 新 Web 部件属性](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. 选择“**发布**”，让 SharePoint Online 用户可以看到此更改。

    ![加载的 SP 报表](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>授予报表访问权限

在 SharePoint Online 中嵌入报表不会自动授予用户报表查看权限 - 你需要在 Power BI 中设置查看权限。

> [!IMPORTANT]
> 请务必在 Power BI 中检查哪些人员可以查看报表，然后向未列出的人员授予访问权限。

在 Power BI 中提供报表访问权限有两种方法。 第一种：若要使用 Office 365 组生成 SharePoint Online 团队站点，请在 Power BI 服务和 SharePoint 页中将用户列为工作区的成员   。 有关详细信息，请参阅如何[管理工作区](service-manage-app-workspace-in-power-bi-and-office-365.md)。

第二种：将报表嵌入应用并直接与用户共享。  

1. 创建者（必须是 Pro 用户）在工作区中创建报表。 若要与 Power BI 免费用户共享，需要将工作区设置为“Premium 工作区”   。

2. 创建者发布并安装应用。 创建者必须安装应用，这样应用才能访问用于在 SharePoint Online 中嵌入的报表 URL。

3. 此时，所有最终用户也必须要安装应用。 也可使用“自动安装应用”功能（可以在 [Power BI 管理门户](service-admin-portal.md)中启用），为最终用户预安装应用  。

   ![自动安装应用](media/service-embed-report-spo/install-app-automatically.png)

4. 作者打开应用并转到报表。

5. 创建者从应用安装的报表中复制嵌入报表 URL。 请勿使用工作区中的原始报表 URL。

6. 在 SharePoint Online 中新建团队网站。

7. 将之前复制的报表 URL 添加到 Power BI Web 部件。

8. 添加将使用 SharePoint Online 页面和已创建 Power BI 应用中的数据的所有最终用户和/或组。

    > [!NOTE]
    > 用户或组必须同时有权访问 SharePoint Online 页面和 Power BI 应用中的报表，才能查看 SharePoint 页面上的报表。 

此时，最终用户可以转到 SharePoint Online 中的团队网站，并能查看页面上的报表。

## <a name="multi-factor-authentication"></a>多重身份验证

如果 Power BI 环境要求使用多重身份验证进行登录，系统可能会提示使用安全设备登录，从而验证身份。 如果未使用多重身份验证登录 SharePoint Online，而 Power BI 环境又需要安全设备来验证帐户，就会发生这种情况。

> [!NOTE]
> Power BI 尚不支持 Azure Active Directory 2.0 中的多重身份验证 - 用户将看到一条错误消息。 如果用户使用安全设备重新登录 SharePoint Online，则可查看报表。

## <a name="web-part-settings"></a>Web 部件设置

以下是可以为 SharePoint Online 的 Power BI Web 部件调整的设置。

![SP Web 部件属性](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| 属性 | 说明 |
| --- | --- |
| 页名称 |设置 Web 部件的默认页。 从下拉列表中选择一个值。 如果下拉列表中未显示任何页，要么是因为报表只有一页，要么是因为粘贴的 URL 包含页名称。 从 URL 中删除报表部分即可选择特定页。 |
| 显示 |调整报表如何能与 SharePoint Online 页面浑然一体。 |
| 显示导航窗格 |显示或隐藏页面导航窗格。 |
| 显示筛选窗格 |显示或隐藏筛选窗格。 |

## <a name="reports-that-do-not-load"></a>报表没有加载

如果 Power BI Web 部件无法加载报表，你可能会看到以下消息：

![“无法查看此内容”消息](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

看见此消息的常见原因有两个。

1. 你不具有报表访问权限。
2. 报表已遭删除。

请与 SharePoint Online 页面的所有者联系，让其帮助解决此问题。

## <a name="licensing"></a>许可

在 SharePoint 中查看报表的用户需要具有 Power BI Pro 许可证  ，或该内容需要位于 [Power BI Premium 容量（EM 或 P SKU）](service-admin-premium-purchase.md)  中的工作区中。

## <a name="known-issues-and-limitations"></a>已知问题和限制

* 错误：“出错，请尝试注销并重新登录，然后重新访问此页。 相关 ID: 未定义，http 响应状态: 400，服务器错误代码 10001，消息: 缺少刷新令牌”
  
  如果收到此错误，请尝试以下故障排除步骤之一。
  
  1. 注销并重新登录 SharePoint。 请务必在重新登录前关闭所有浏览器窗口。

  2. 如果用户帐户要求进行多重身份验证 (MFA)，请使用多重身份验证设备（如手机应用、智能卡等）登录 SharePoint。
  
  3. 不支持 Azure B2B 来宾用户帐户。 用户将看到 Power BI 徽标，显示该部件正在加载，但它不会显示报表。

* Power BI 不支持 SharePoint Online 支持的本地化语言。 因此，可能无法在嵌入的报表中看到正确的本地化内容。

* 如果使用的是 Internet Explorer 10，可能会遇到问题。 <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->

* Power BI Web 部件不适用于[国家云](https://powerbi.microsoft.com/clouds/)。

* 此 Web 部件不支持经典 SharePoint Server。

* SPO Web 部件不支持[URL 筛选器](service-url-filters.md)。

## <a name="next-steps"></a>后续步骤

* [允许或禁止最终用户创建新式网站页面](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [在 Power BI 中构建和分发应用](service-create-distribute-apps.md)  
* [与同事和其他人共享仪表板](service-share-dashboards.md)  
* [什么是 Power BI Premium？](service-premium-what-is.md)
* [在安全门户或网站中嵌入报表](service-embed-secure.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

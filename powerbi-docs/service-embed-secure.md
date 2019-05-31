---
title: 在安全门户或网站中嵌入报表
description: Power BI 嵌入到功能使用户轻松并安全地在内部 web 门户中嵌入报表。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222240"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>在安全门户或网站中嵌入报表

与新**嵌入**选项适用于 Power BI 报告，可以方便且安全地嵌入报表在内部 web 门户中。 这些门户可以是**云端**或**托管在本地**，如 SharePoint 2019。 嵌入的报表是否遵循通过的所有项的权限和数据安全性[行级别安全性 (RLS)](service-admin-rls.md)。 它们提供无需编写代码嵌入到可接受的 URL 或 iFrame 的任何门户。 

**嵌入**选项支持[URL 筛选器](service-url-filters.md)和 URL 设置。 它允许您将与使用低代码方法需要仅基本 HTML 和 JavaScript 知识的门户网站进行集成。

## <a name="how-to-embed-power-bi-reports-into-portals"></a>如何将  Power BI 报表嵌入门户

1. 在 Power BI 服务中报表的“文件”  菜单上提供新的“嵌入”  选项。

    ![“安全嵌入”选项下拉选项](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. 选择**嵌入**选项可打开一个对话框，提供一个链接和可用于安全地嵌入报表的 iFrame。

    ![“嵌入”选项对话框](media/service-embed-secure/secure-embed-code-dialog.png)

3. 无论用户打开报表 URL 直接，还是一个嵌入式 web 门户中，报表访问权限要求身份验证。 如果用户未登录到 Power BI 在其浏览器会话中，会显示以下屏幕。 当他们选择**登录**，可以打开一个新浏览器窗口或选项卡。 让他们检查弹出窗口阻止程序，如果它们不会提示登录。

    ![登录以查看此报表](media/service-embed-secure/secure-embed-sign-in.png)

4. 用户登录后，报表将打开，显示数据并使页面导航和筛选器设置。 仅具有查看权限的用户可以看到在 Power BI 中的报表。 所有[行级别安全性 (RLS)](service-admin-rls.md)也会应用规则。 最后，用户需要获得正确许可，要么需要 Power BI Pro 许可证，要么报表必须位于处于 Power BI Premium 容量范围内的工作区中。 用户需要在每次打开新浏览器窗口登录。 但是，登录后，其他报表将自动加载。

    ![嵌入报表](media/service-embed-secure/secure-embed-report.png)

5. 当使用 iFrame，您可能需要编辑**高度**并**宽度**，使其适合你的门户网页中。

    ![设置高度和宽度](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>授予报表访问权限

**嵌入**选项不会自动允许用户查看报表。 在 Power BI 服务中设置的视图权限。

在 Power BI 服务中，可以与需要访问权限的用户共享嵌入的报表。 如果要使用 Office 365 组，可以将用户列为应用工作区成员。 有关详细信息，请参阅如何[管理 Power BI 和 Office 365 中的应用工作区](service-manage-app-workspace-in-power-bi-and-office-365.md)。

## <a name="licensing"></a>许可

若要查看嵌入的报表，用户需要 Power BI Pro 许可证或内容需要位于在工作区[Power BI Premium 容量 （EM 或 P SKU）](service-admin-premium-purchase.md)。

## <a name="customize-your-embed-experience-using-url-settings"></a>使用 URL 设置自定义嵌入体验

可以自定义使用嵌入 URL 输入的设置的用户体验。 可以在提供的 iFrame 中更新的 URL **src**设置。

| 属性  | 说明  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | 可以使用**pageName**查询字符串参数来设置要打开的报表页面。 您可以找到此值在报表 URL 的结尾在 Power BI 服务中，查看报表时，如下所示。 |  |  |  |
| URL 筛选器  | 可以使用[URL 筛选器](service-url-filters.md)收到从 Power BI UI 来筛选嵌入内容中嵌入 URL。 借助这种方式，可以通过基本 HTML 和 JavaScript 体验生成低代码集成。  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>集的页将打开嵌入报表 

您可以找到**pageName** Power BI 服务中查看报表时报表 URL 的末尾处的值。

1. 从 Power BI 服务中 web 浏览器中，打开报表，然后复制地址栏 URL。

    ![报表区域](media/service-embed-secure/secure-embed-report-section.png)

2. 将 pageName  设置追加到此 URL。

    ![追加 pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>使用 URL 筛选器筛选报表内容 

可以使用[URL 筛选器](service-url-filters.md)来提供不同的报表视图。 例如，下面的 URL 筛选报表以显示能源行业的数据。

将 pageName  和 [URL 筛选器](service-url-filters.md)结合使用的功能非常强大。 可以使用基本 HTML 和 JavaScript 生成体验。

例如，下面是可以添加到 HTML 页的按钮：

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

选中时，按钮将调用一个函数来使用更新的 URL，其中包括能源行业筛选器更新 iFrame。

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![筛选](media/service-embed-secure/secure-embed-filter.png)

可以根据需要添加任意数量的按钮，以创建低代码自定义体验。 

## <a name="considerations-and-limitations"></a>注意事项和限制

* 不支持外部来宾用户访问 Azure 企业到企业 (B2B)。

* 安全嵌入适用于发布到 Power BI 服务的报表。

* 用户需要登录以查看报表，只要他们打开新浏览器窗口。

* 某些浏览器要求你在登录后刷新页面，尤其是在使用 InPrivate 或 Incognito 模式。

* 若要实现单一登录体验，在 SharePoint Online 选项中，使用嵌入或自定义集成使用生成[用户拥有数据](developer/embed-sample-for-your-organization.md)嵌入方法。 

* 随“嵌入”  选项提供的自动身份验证功能不适用于 Power BI JavaScript API。 对于 Power BI JavaScript API，请使用[用户拥有数据](developer/embed-sample-for-your-organization.md)嵌入方法。 

## <a name="next-steps"></a>后续步骤

* [共享 Power BI 中的工作方式](service-how-to-collaborate-distribute-dashboards-reports.md)

* [筛选报表的 URL 中使用查询字符串参数](service-url-filters.md)

* [使用报表 web 部件在 SharePoint Online 中嵌入](service-embed-report-spo.md)

* [从 Power BI 发布到 Web](service-publish-to-web.md)
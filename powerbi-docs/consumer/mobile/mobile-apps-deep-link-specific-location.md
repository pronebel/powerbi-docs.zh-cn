---
title: 创建指向 Power BI 移动应用中特定位置的链接
description: 了解如何使用统一资源标识符 (URI) 创建指向 Power BI 移动应用中特定仪表板、磁贴或报表的深层链接。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 11/16/2020
ms.openlocfilehash: 8c5b3c394d54df390d690d58b56e9084f9829733
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565652"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>创建指向 Power BI 移动应用中特定位置的链接
可以使用链接直接访问特定的 Power BI 内容，例如特定的报表、报表页、仪表板、磁贴等。

使用链接访问 Power BI 移动应用中的内容主要有两种方案： 

* 从移动应用外部打开 Power BI，并登录特定内容。 这通常是一个集成方案，在此方案中，将从其他应用打开 Power BI 移动应用。 
* 在 Power BI 中导航。 要在 Power BI 中创建自定义导航时，通常会执行此操作。

本文涵盖以下案例：
* 使用链接从移动应用外部打开特定的 Power BI 内容。 描述了两种链接格式。 一种使用重定向方法，无论 Power BI 将在哪里打开，都可以使用它。 另一种直接在 Power BI 移动应用中打开，仅在安装了移动应用的移动设备上起作用。
* 使用 Power BI 中的链接导航到特定的 Power BI 内容。

## <a name="use-links-from-outside-the-mobile-app"></a>使用来自移动应用外部的链接
如果要从移动应用外部链接到 Power BI 中的特定项，有两个选项可供选择，具体取决于打开链接的位置：

* 如果希望无论在计算机浏览器中还是在移动设备上单击链接，均可正确打开该链接，则可以创建一个链接，确保无论在何处单击都可以正确打开该链接。 此链接具有特殊的重定向语法，用于启用此明智行为。

* 如果知道链接只会在安装了 Power BI 移动应用的移动设备上打开，则可以避免上述方法的重定向开销，并使用其他链接语法直接在移动设备上的 Power BI 移动应用中打开链接。 不过，请务必注意，虽然此链接避免了第一种方法的重定向开销，但如果在安装了 Power BI 移动应用的移动设备以外的任何其他位置打开链接，则该链接将不起作用。

### <a name="create-a-link-that-works-anywhere"></a>创建在任意位置都有效的链接
本节中描述的链接格式使用重定向来确保在任意位置单击链接均有效。
* 如果在移动设备上单击链接，可确保该设备使用 Power BI 移动应用打开该链接。 如果设备上未安装移动应用，则建议用户前往商店购买。
* 如果在电脑上单击链接，将在 Power BI Web 门户中打开相关项。

链接必须以特殊前缀开头，后跟查询参数：

https<nolink>://app.powerbi.com/Redirect? **[QUERYPARAMETERS]** </code>

> [!IMPORTANT]
> 如果内容托管在特殊数据中心（例如政府，中国等）中，则链接应以相应的 Power BI 地址开头，例如 app.powerbigov.us 或 app.powerbi.cn 。

查询参数是：

|参数  | 值  | 说明 |
|---------|---------|---------|
|action (必需)    | OpenApp<br>OpenReport<br>OpenDashboard<br>OpenTile | |
|**appId**| 包含 36 个字符的 GUID | 如果要打开属于应用的报表或仪表板，则必须指定。<br>示例：appId=baf4b16d-b5bd-4360-8a3a-51d11242c09b |
|**groupObjectId**| 包含 36 个字符的 GUID | 要打开不属于“我的工作区”的报表或仪表板时，请指定工作区。<br>示例：groupObjectId=9a3841c6-74b3-46f1-85fd-bdd78f27b30e |
| **dashboardObjectId** | 包含 36 个字符的 GUID | 仪表板对象 ID（如果操作是 OpenDashboard 或 OpenTile）<br>示例：dashboardObjectId=033bb049-5b68-4392-b3ef-ae9a43738a4a |
| **reportObjectId** | 包含 36 个字符的 GUID | 报表对象 ID （如果操作是 OpenReport）<br>示例：reportObjectId=6114cec7-78e1-4926-88ff-0bc5338452cf |
| **tileObjectId** | 包含 36 个字符的 GUID | 磁贴对象 ID（如果操作是 OpenTile）<br>示例：tileObjectId=a845dcb8-a289-43a8-94ea-67a8c0a068f9 |
| **reportPage** | ReportSection&lt;num&gt; | 页名（如果要打开特定的报表页）。 （如果操作是 OpenReport）<br>示例：reportPage=ReportSection6  |
| **bookmarkGuid** | 包含 36 个字符的 GUID | 书签 ID（如果要打开特定的书签视图）。 （如果操作是 OpenReport）<br>示例：bookmarkGuid=18e8872f-6db8-4cf8-8298-3b2ab254cc7f |
| **ctid** | 包含 36 个字符的 GUID | 项组织 ID（与 B2B 方案相关。 如果项属于用户的组织，则可以省略此项）<br>示例：ctid=5367c770-09d0-4110-bf6a-d760cb5ef681。 |
||||

**示例：**

在以下示例中，参数值的占位符用粗体突出显示。 若要获取实际值，请转到 Power BI 服务，打开要链接到的项，然后从项 URL 中提取所需的值。

* **打开应用**

    https<nolink>://app.powerbi.com/Redirect?action=OpenApp&appId= **&lt;appid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**
   
* **打开属于应用一部分的仪表板**

    https<nolink>://app.powerbi.com/Redirect?action=OpenDashboard&appId= **&lt;appid-guid&gt;** &dashboardObjectId= **&lt;dashboardid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**

* **打开属于“我的工作区”以外的工作区的报表**

    https<nolink>://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId= **&lt;reportid-guid&gt;** &groupObjectId= **&lt;groupobjectid-guid&gt;** &reportPage=**ReportSection&lt;num&gt;**

### <a name="how-to-get-the-correct-link-format"></a>如何获得正确的链接格式

#### <a name="links-to-apps-and-items-in-apps"></a>链接到应用和应用中的项

对于属于应用的应用和报表以及仪表板，获取链接的最简单方法是转到应用工作区并选择“更新应用” 。 这将打开“发布应用”体验。 打开权限选项卡，然后展开链接部分，查看指向应用及其所有内容的链接。 可以从 Power BI 外部使用这些链接直接访问应用及其内容。

![Power BI 发布应用链接 ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-to-items-that-are-not-in-an-app"></a>链接到不在应用中的项 

对于不属于应用的报表和仪表板，需要从项 URL 中提取所需的对象 ID。 为此，请转到 Power BI 服务，导航到要链接的项，然后在浏览器地址栏中显示的 URL 中查找所需的值。

以下示例显示可在要链接到的项 URL 中的何处找到所需 ID。

* 若要查找包含 36 个字符的仪表板对象 ID，请导航到要在 Power BI 服务中链接到的特定仪表板，并在以下指示的位置找到仪表板对象 ID 和任何其他必需的 ID：

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;dashboard-object-id&gt;** ?ctid= **&lt;org-object-id&gt;**

* 若要查找包含 36 个字符的报表对象 ID，请导航到要在 Power BI 服务中链接到的特定报表，并找到必要的 ID，如下所示。 请注意，此示例包含对特定报表页和特定书签的引用。

    https<nolink>://app.powerbi.com/groups/me/reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;num&gt;** ?bookmarkGuid= **&lt;bookmark-id&gt;**

* 若要链接到“我的工作区”以外的工作区中的项，需要提取组对象 ID。 本示例显示来自“我的工作区”以外的工作区的报表。

    https<nolink>://app.powerbi.com/groups/ **&lt;group-object-id&gt;** /reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;report-section-num&gt;** ?ctid= **&lt;org-object-id&gt;**

### <a name="create-a-link-that-opens-only-on-a-device-that-has-the-power-bi-mobile-app-installed"></a>创建仅在安装了 Power BI 移动应用的设备上打开的链接

本部分所述的链接格式链接到所有移动平台（iOS、Android 设备和 Windows 10）上 Power BI 移动应用中的特定位置。 此链接格式直接打开位置，而无需上一部分中介绍的方法涉及的任何重定向。 只能在安装了 Power BI 移动应用的移动设备上打开此格式。

此格式的链接可以直接指向仪表板、磁贴和报表。 深层链接的目标决定了其格式。 请按以下步骤操作，创建指向不同位置的深层链接。 

* **打开 Power BI 移动应用**

    使用此链接可在任何设备上打开 Power BI 移动应用：

    mspbi://app/

* **打开特定仪表板**

    此链接可将 Power BI 移动应用打开到特定的仪表板：

    mspbi://app/OpenDashboard?DashboardObjectId= **<36-character-dashboard-id>**

    若要获取包含 36 个字符的仪表板对象 ID，请导航到 Power BI 服务中的特定仪表板，然后从 URL 中提取它。 例如，在 Power BI 服务的以下 URL 中突出显示了仪表板对象 ID：

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;61b7e871-cb98-48ed-bddc-6572c921e270&gt;**

    如果仪表板不在“我的工作区”中，则还需要在仪表板 ID 的前面或后面添加组对象 ID。 下面显示的深层链接在仪表板对象 ID 后面添加了组对象 ID 参数：

    mspbi://app/OpenDashboard?DashboardObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**</code>

    请注意两个参数之间的 & 号。

* **打开处于焦点模式的特定磁贴**

    此链接可打开 Power BI 移动应用中处于焦点模式的特定磁贴：

    mspbi://app/OpenTile?DashboardObjectId= **<36-character-dashboard-id>** &TileObjectId= **<36-character-tile-id>**

    若要查找包含 36 个字符的仪表板和磁贴对象 ID，请转到 Power BI 服务中的特定仪表板，然后打开处于焦点模式的磁贴。 下面的示例中突出显示了仪表板和磁贴 ID。

    https<nolink>://app.powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

    若要直接打开该磁贴，链接应为：

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

    请注意两个参数之间的 & 号。

    如果仪表板不在“我的工作区”中，请添加 GroupObjectId 参数，例如 &GroupObjectId=<36-character-group-id>

* **打开特定报表**

    此链接可打开 Power BI 移动应用中的特定报表：

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>**

    若要查找包含 36 个字符的报表对象 ID，请导航到 Power BI 服务中的特定报表。 Power BI 服务的以下 URL 说明了需要提取的报表 ID。

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

    如果此报表不在“我的工作区”中，则还需要在报表 ID 的前面或后面添加 &GroupObjectId=<36-character-group-id>。 例如，在这种情况下，深层链接应为：

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**

    请注意两个参数之间的 & 号。

* **打开特定报表页**

    此链接可打开 Power BI 移动应用中的特定报表页：

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>** &reportPage=**ReportSection&lt;number&gt;**

    此报表页名为 ReportSection，后跟一个数字。 同样，若要查找所需的值，请在 Power BI 服务中打开报表，导航到特定的报表页，然后从 URL 中提取所需的值。 例如，此 URL 的突出显示部分表示打开到特定报表页时所需的值：

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**/**ReportSection11**</code>

* **在全屏模式下打开（仅适用于 Windows 设备）**

    对于 Windows 设备，还可以添加 openFullScreen 参数，在全屏模式下打开特定报表。 以下示例在全屏模式下打开报表页：

    mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&**openFullScreen=true**

* **添加上下文**（可选）

    还可以将上下文添加到字符串。 如果需要与我们联系，我们可以使用该上下文来筛选数据，查找与应用相关的内容。 若要添加上下文，请将参数 context=&lt;app-name&gt; 添加到链接：

    例如，以下示例显示包含上下文参数的链接： 

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**&**context=SlackDeepLink**

## <a name="use-links-inside-power-bi"></a>使用 Power BI 中的链接

在 Power BI 移动应用中，Power BI 中链接的运作方式与在 Power BI 服务中一样。

如果要添加指向其他 Power BI 项的报表链接，则只需从浏览器地址栏复制该项的 URL 即可。 详细阅读[如何向报表中的文本框添加超链接](../../create-reports/service-add-hyperlink-to-text-box.md)。

## <a name="next-steps"></a>后续步骤
你的反馈将帮助我们决定未来要做什么，如果你想在 Power BI 移动应用中看到其他功能，别忘了向我们提出你的建议。 

* [适用于移动设备的 Power BI 应用](mobile-apps-for-mobile-devices.md)
* 关注 Twitter 上的 @MSPowerBI
* 加入 [Power BI 社区](http://community.powerbi.com/)的对话
* [什么是 Power BI？](../../fundamentals/power-bi-overview.md)
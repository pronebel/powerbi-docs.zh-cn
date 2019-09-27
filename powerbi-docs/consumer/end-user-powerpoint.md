---
title: 将报表从 Power BI 导出到 PowerPoint
description: 了解如何将 Power BI 报表导出到 PowerPoint。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 9a798afead16174f66fadba87c795d5377747e93
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71141456"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>将报表从 Power BI 导出到 PowerPoint
借助 Power BI，可以将报表发布到 Microsoft PowerPoint，并根据 Power BI 报表轻松地创建幻灯片平台。 **导出到 PowerPoint** 时，会发生以下情况：

* Power BI 报表中的每个页面成为 PowerPoint 中单独的幻灯片
* Power BI 报表中的每个页面导出为 PowerPoint 中的单张高分辨率图像
<!-- * The filters and slicers settings that you added to the report are preserved. -->
* 会在 PowerPoint 中创建链接到 Power BI 报表的链接 

将 Power BI 报表导出到 PowerPoint 非常快速。 只需按照下一部分中所述的步骤操作。

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>如何将 Power BI 报表导出到 PowerPoint
在 Power BI 服务中，选择要在画布上显示的报表。 还可以从左侧导航栏上的“主页”页面、“应用”或任何其他容器中选择报表。

想要导出到 PowerPoint 的报表显示在画布上时，在菜单栏中选择“导出”>“PowerPoint”。

![从菜单栏中选择“导出”](media/end-user-powerpoint/power-bi-export.png)

   
将出现一个弹出窗口，可以选择“当前值”或“默认值”。  “当前值”以当前状态导出报表，其中包括对切片器和筛选器值所做的有效更改。  大多数用户选择此选项。  或者，选择“默认值”以原始状态导出报表（在作者共享此报表时），并不反映对该原始状态所做的任何更改。

![选择要导出的内容](media/end-user-powerpoint/power-bi-current-values.png)
    
此外，还有一个复选框，用于选择是否导出报表的隐藏选项卡。  如果只想在浏览器中导出可浏览的报表选项卡，只需选中此框即可。  如果希望将所有隐藏选项卡作为导出的一部分，则不选中此选项。  如果该复选框显示为灰色，则报表中没有隐藏选项卡。  完成选择后，选择“导出”以继续。

将看到 Power BI 服务浏览器窗口右上角的通知横幅，显示报表正在导入到 PowerPoint。 这可能需要几分钟的时间。在导出报表的同时，可以在 Power BI 中继续进行操作。

![“正在导出到 PowerPoint”通知](media/end-user-powerpoint/power-bi-export-progress.png)

导入完成后，通知横幅会发生变化以通知你 Power BI 服务已完成导出过程。 在浏览器显示下载文件的位置，文件是可用的。 在下图中，它显示为浏览器窗口底部的下载横幅。

![箭头指向屏幕底部的浏览器通知](media/end-user-powerpoint/powerbi_to_powerpoint_4.png)

以上是其中包含的全部内容。 可以下载该文件，使用 PowerPoint 将其打开，然后像对任何其他 PowerPoint 系列幻灯片一样对其进行修改或增强。

## <a name="checking-out-your-exported-powerpoint-file"></a>检查已导出的 PowerPoint 文件
打开 Power BI 导出的 PowerPoint 文件时，会发现几个很酷且很有用的元素。 看一看下图，然后查看下面描述一些很酷功能的编号元素。

![将打开 PowerPoint](media/end-user-powerpoint/powerbi_to_powerpoint_5.png)

1. 幻灯片平台的第一页包括报表名称和链接，以便能**在 Power BI 中查看**幻灯片平台所基于的报表。
2. 还可以获取有关报表的一些有用信息，包括导出的报表所基于的 *上次数据刷新时间* *下载* 时间和日期，这是 Power BI 报表导出为 PowerPoint 文件的时间和日期。
3. 每个报表页面都是单独的幻灯片，如左侧导航窗格所示。 
4. 已发布的报表根据 Power BI 设置或者根据你所用浏览器的区域设置以相应的语言呈现。 若要查看或设置语言首选项，请选择齿轮图标![齿轮图标](media/end-user-powerpoint/power-bi-settings-icon.png) >“设置”>“常规”>“语言”。 有关区域设置信息，请参阅 [Power BI 支持的语言和国家/地区](../supported-languages-countries-regions.md)。
5. PowerPoint 演示文稿包括封面幻灯片，其中包含以正确的时区显示的导出时间。

转到各个幻灯片时，将会发现每个报表页都是独立图像。

>[!NOTE]
> 为每个报表页提供单个视觉对象是新行为。 为每个视觉对象提供独立图像的旧行为将不再实现。 
 

![显示每个视觉对象的图像是单独的图像](media/end-user-powerpoint/powerbi_to_powerpoint_6.png)

如何处理 PowerPoint 系列幻灯片或任何一张高分辨率图像，这取决于你自己！

## <a name="limitations"></a>限制
在使用**导出到 PowerPoint** 功能时，有几个注意事项和限制需要牢记。

* 目前不支持 R 视觉对象。 任何此类视觉对象都将作为空白图像导出到 PowerPoint 中，并显示一条错误消息，指示不支持该视觉对象。
* 支持已取得认证的自定义视觉对象。 有关已取得认证的自定义视觉对象的详细信息（包括如何完成自定义视觉对象认证），请参阅[获取自定义视觉对象认证](../power-bi-custom-visuals-certified.md)。 不支持未取得认证的自定义视觉对象，任何此类视觉对象都会作为空白图像导出到 PowerPoint 中，并显示一条错误消息，指示不支持该视觉对象。
* 暂无法导出报表页超过 30 个的报表。
* 将报表导出到 PowerPoint 的过程可能需要几分钟才能完成，请耐心等待。 影响所需时间的因素包括报表的结构和 Power BI 服务的当前负载。
* 如果 Power BI 服务中没有“导出到 PowerPoint”菜单项，很可能是因为租户管理员已禁用此功能。 有关详细信息，请联系租户管理员。
* 会根据图表的边界区域裁剪背景图像。 强烈建议在导出到 PowerPoint 之前删除背景图像。
* PowerPoint 页始终以标准的 9:16 尺寸创建，无论 Power BI 报表页的原大小或原尺寸如何。
* Power BI 租户域之外的用户拥有的报表（如组织外部人员拥有且与你共享的报表）无法发布到 PowerPoint。
* 如果与组织外部人员（即位于 Power BI 租户之外的用户）共享仪表板，此用户将无法把共享仪表板的关联报表导出到 PowerPoint。 例如，如果你是 aaron@contoso.com，虽然可以与 david@cohowinery.com 共享内容， 但 david@cohowinery.com 无法将关联报表导出到 PowerPoint。
* 导出可能不适用于较早版本的 PowerPoint。
* 如上所述，每个报表页导出为 PowerPoint 文件中的单张图像。
* Power BI 服务将你的 Power BI 语言设置用作 Power BI 导出的语言。 若要查看或设置语言首选项，请选择齿轮图标![齿轮图标](media/end-user-powerpoint/power-bi-settings-icon.png) >“设置”>“常规”>“语言”。
* 导出的 PowerPoint 文件的封面幻灯片上的下载时间被设置为导出时计算机的时区。
* 为导出选择了“当前值”时，当前不遵循 URL 筛选器。

## <a name="next-steps"></a>后续步骤
[打印报表](end-user-print.md)

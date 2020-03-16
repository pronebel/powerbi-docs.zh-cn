---
title: 将报表从 Power BI 导出到 PowerPoint
description: 了解如何将 Power BI 报表导出到 PowerPoint。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/21/2020
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 4194afb71dec7b50d75def0677489d3ff009917e
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "79113754"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>将报表从 Power BI 导出到 PowerPoint

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

借助 Power BI，可以将报表发布到 Microsoft PowerPoint，并根据 Power BI 报表轻松地创建幻灯片组。 导出到 PowerPoint 时，会发生以下情况：

* Power BI 报表中的每个页面成为 PowerPoint 中单独的幻灯片。
* Power BI 报表中的每个页面导出为 PowerPoint 中的单张高分辨率图像。
* 可以保留添加到报表中的筛选器和切片器设置。
* PowerPoint 中会创建链接到 Power BI 报表的链接。

将 Power BI 报表  导出到 PowerPoint  非常快速。 按照下一部分中所述的步骤执行操作。

## <a name="export-your-power-bi-report-to-powerpoint"></a>将 Power BI 报表导出到 PowerPoint
在 Power BI 服务中，选择要在画布上显示的报表  。 你还可以从导航窗格上的“主页”、“应用”或任何其他容器中选择报表   。

想要导出到 PowerPoint 的报表在画布上显示时，在菜单栏中选择“导出” > “PowerPoint”   。

![从菜单栏中选择“导出”](media/end-user-powerpoint/power-bi-export.png)

此时会显示弹出窗口，可在其中选择“当前值”或“默认值”   。 “当前值”以当前状态导出报表，其中包括对切片器和筛选器值所做的有效更改  。 大多数用户选择此选项。 或者，选择“默认值”以原始状态导出报表（在共享此报表时），且不反映对该原始状态所做的任何更改   。

> [!NOTE]
> 当前值不包括视觉对象的滚动状态  。

![选择要导出的内容](media/end-user-powerpoint/power-bi-current-values.png)
 
此外，还有一个复选框，用于选择是否导出报表的隐藏选项卡。 如果只想导出浏览器中对你可见的报表选项卡，请选中此复选框。 如果希望将所有隐藏选项卡作为导出的一部分，则不选中此选复选框。 如果该复选框显示为灰色，则报表中没有隐藏选项卡。 工具提示选项卡是隐藏选项卡的一个示例。[自定义工具提示](../desktop-tooltips.md)由报表设计者创建，且不向客户显示为 Power BI 服务的报表选项卡   。 

完成选择后，选择“导出”以继续  。 将看到 Power BI 服务浏览器窗口右上角的通知横幅，显示报表正在导出到 PowerPoint。 导出可能需要几分钟。 在导出报表的同时，可以在 Power BI 中继续进行操作。

![“正在导出到 PowerPoint”通知](media/end-user-powerpoint/power-bi-export-progress.png)

Power BI 服务完成导出过程后，通知横幅会发生变化以通知你。 在浏览器显示下载文件的位置，文件是可用的。 在下图中，它显示为浏览器窗口底部的下载横幅。

![屏幕底部的浏览器通知](media/end-user-powerpoint/power-bi-browsers.png)

以上是其中包含的全部内容。 可以下载该文件，使用 PowerPoint 将其打开，然后像对任何其他 PowerPoint 幻灯片组一样对其进行修改或增强。

## <a name="check-out-your-exported-powerpoint-file"></a>检查已导出的 PowerPoint 文件
打开 Power BI 导出的 PowerPoint 文件时，会发现几个很酷且很有用的元素。 请看一看下图，查看介绍其中一些很酷的功能的编号元素。

![将打开 PowerPoint](media/end-user-powerpoint/power-bi-powerpoint.png)

1. 幻灯片组的第一页包括报表名称和链接，以便能**在 Power BI 中查看**幻灯片组所基于的报表。
2. 还可以获得有关报表的一些有用信息。 **上次数据刷新**显示导出的报表所基于的日期和时间。 **下载时间**显示 Power BI 报表导出到 PowerPoint 文件中的日期和时间。
3. 每个报表页面都是单独的幻灯片，如导航窗格所示。 
4. 已发布的报表根据 Power BI 设置或者根据你所用浏览器的区域设置以相应的语言呈现。 若要查看或设置语言首选项，请选择齿轮图标 ![齿轮图标](media/end-user-powerpoint/power-bi-settings-icon.png) > “设置” > “常规” > “语言”    。 有关区域设置信息，请参阅 [Power BI 支持的语言和国家/地区](../supported-languages-countries-regions.md)。


转到各个幻灯片时，会发现每个报表页都是独立的图像。

![将每个视觉对象作为单独图像显示的屏幕](media/end-user-powerpoint/power-bi-images.png)

如何处理 PowerPoint 幻灯片组或任何一张高分辨率图像，这取决于你自己。

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
在使用“导出到 PowerPoint”功能时，有几个注意事项和限制需要牢记  。

* 目前不支持 R 视觉对象和 Python 视觉对象。 任何此类视觉对象都将作为空白图像导出到 PowerPoint 中，并显示一条错误消息，指示不支持该视觉对象。
* 支持已认证的自定义视觉对象。 有关已认证的自定义视觉对象的详细信息（包括如何完成自定义视觉对象认证），请参阅[获取自定义视觉对象认证](../developer/power-bi-custom-visuals-certified.md)。 不支持尚未认证的自定义视觉对象。 它们将作为空白图像导出到 PowerPoint 中，并显示一条错误消息，指示不支持该视觉对象。
* ESRI 视觉对象不受支持
* 暂无法导出报表页超过 30 个的报表。
* 具有滚动条的视觉对象以其默认状态导出。 PowerPoint 中的视觉对象将仅显示数据的顶部部分。 PowerPoint 中的滚动功能不可用，因为每张幻灯片都是图像。 
* 将报表导出到 PowerPoint 的过程可能需要几分钟才能完成，请耐心等待。 影响所需时间的因素包括报表的结构和 Power BI 服务的当前负载。
* 如果 Power BI 服务中没有“导出到 PowerPoint”菜单项，则可能是因为租户管理员已禁用该功能  。 有关详细信息，请联系租户管理员。
* 背景图像会根据图表的边界区域进行裁剪。 我们建议在导出到 PowerPoint 之前删除背景图像。
* PowerPoint 页始终以标准的 9:16 尺寸创建，无论 Power BI 报表页的原大小或原尺寸如何。
* Power BI 租户域之外的用户拥有的报表（例如组织外部人员拥有并与你共享的报表）无法发布到 PowerPoint。
* 如果与组织外部人员（即不属于 Power BI 租户的用户）共享仪表板，该用户无法将共享仪表板的关联报表导出到 PowerPoint。 例如，如果你是 aaron@contoso.com，虽然可以与 david@cohowinery.com 共享内容， 但 david@cohowinery.com 无法将关联报表导出到 PowerPoint。
* 导出可能不适用于较旧版本的 PowerPoint。
* 如上所述，每个报表页导出为 PowerPoint 文件中的单张图像。
* Power BI 服务将你的 Power BI 语言设置用作 Power BI 导出的语言。 若要查看或设置语言首选项，请选择齿轮图标 ![齿轮图标](media/end-user-powerpoint/power-bi-settings-icon.png) > “设置” > “常规” > “语言”    。
* 导出的 PowerPoint 文件的封面幻灯片上的下载  时间被设置为导出时计算机的时区。
* 导出为 PPTX 时，使用含自定义字体的主题的报表会将自定义字体替换为默认字体。
* 如果为导出选择“当前值”，当前不遵循 URL 筛选器  。

## <a name="next-steps"></a>后续步骤
[打印报表](end-user-print.md)

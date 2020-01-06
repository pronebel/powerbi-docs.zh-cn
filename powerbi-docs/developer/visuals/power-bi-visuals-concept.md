---
title: Power BI 视觉对象概念
description: 本文介绍了如何集成视觉对象和 Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700837"
---
# <a name="power-bi-visual-concept"></a>Power BI 视觉对象概念

本文介绍用户和视觉对象如何与 Power BI 交互，以及用户如何与 Power BI 视觉对象交互。 在关系图中，可以看到哪些操作直接影响视觉对象或通过 Power BI 影响视觉对象（例如，用户选择书签）。

![Power BI 视觉对象](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>视觉对象从 Power BI 获取更新

视觉对象具有 `update` 方法，此方法通常包含视觉对象的主要逻辑，并负责呈现图表或可视化数据。

调用 `update` 方法可获得更多更新。

### <a name="user-interacts-with-visual-through-power-bi"></a>用户通过 Power BI 与视觉对象交互

* 用户打开视觉对象属性面板。

    Power BI 从视觉对象 `capabilities.json` 中提取支持的对象和属性，并接收 Power BI 调用视觉对象 `enumerateObjectInstances` 方法的属性的实际值。

    视觉对象必须返回属性的实际值。

    有关详细信息，请[阅读视觉对象功能](capabilities.md)。

* 格式面板中的[用户更改视觉对象的属性](../../visuals/power-bi-visualization-customize-title-background-and-legend.md)。

    更改属性值之后，Power BI 调用视觉对象的 `update` 方法，并使用对象的新值将新的 `options` 传递到更新方法。

    有关详细信息，请参阅[视觉对象的对象和属性](objects-properties.md)。

* 用户调整视觉对象的大小。

    当用户更改视觉对象的大小时，Power BI 将使用新 `option` 对象调用 `update` 方法。 选项嵌套了具有新视觉对象宽度和高度的 `viewport` 对象。

* 用户应用报表、页面或视觉对象级筛选器。

    Power BI 根据筛选条件筛选数据，并调用视觉对象的 `update` 方法来向视觉对象分配新数据。

    视觉对象通过一个嵌套对象中的新数据获取 `options` 的新更新。 这取决于视觉对象的数据视图映射配置。

    有关详细信息，请参阅[数据视图映射](dataview-mappings.md)。

* 用户选择报表的另一个视觉对象中的数据点。

    Power BI 筛选器或突出显示所选数据点，并调用视觉对象的 `update` 方法。

    视觉对象通过突出显示的数组获取新的筛选数据或相同数据。

    有关详细信息，请参阅[如何在视觉对象中突出显示数据](highlight.md)。

* 用户选择报表的书签面板上的书签。

    可能会发生两个操作：

    1. Power BI 调用通过方法 `registerOnSelectionCallback` 传递的已注册函数，并回调获取对应书签选择的数组的函数。

    2. Power BI 通过 `options` 内对应的筛选器对象调用 `update` 方法。

    在这两种情况下，视觉对象都必须根据收到的选择或筛选器对象来更改可视化状态。

    有关书签的详细信息，请参阅[如何处理书签](filter-api.md)。

    有关筛选器的详细信息，请参阅 [Power BI 视觉对象如何在其他视觉对象中筛选数据](filter-api.md)。

### <a name="user-interacts-with-visual-directly"></a>用户直接与视觉对象交互

* 用户将鼠标悬停在数据元素上

    视觉对象可通过 Power BI 工具提示 API 来显示关于数据点的其他信息。
    用户将鼠标悬停在视觉对象元素上，视觉对象可以处理事件并在工具提示元素上显示数据。

    视觉对象可显示标准工具提示或报表页工具提示。

    有关详细信息，请参阅[如何添加工具提示](add-tooltips.md)指南。

* 用户更改视觉对象属性（例如，用户展开树，以及视觉对象保存属性状态）

    视觉对象可以通过 Power BI API 保存属性值。 例如，当用户与视觉对象交互时。 视觉对象需要保存或更新属性值。 视觉对象可以为其调用 `presistProperties` 方法。

* 用户单击 URL 链接。

    默认情况下，视觉对象不能打开该 URL。 若要在新选项卡中打开 URL，视觉对象应调用 `launchURL` 方法，并将 URL 作为参数进行传递。

    有关详细信息，请参阅[启动 URL API](launch-url.md)。

* 用户应用筛选器引发视觉对象

    视觉对象调用 `applyJSONFilter` 并将筛选条件传递给筛选器以筛选其他视觉对象中的数据。

    视觉对象可以使用多种类型的筛选器，例如基本筛选器、高级筛选器、元组筛选器。

    有关筛选器的详细信息，请参阅 [Power BI 视觉对象如何在其他视觉对象中筛选数据](filter-api.md)。

* 用户单击/选择视觉对象上的元素。

    有关选择的详细信息，请参阅[视觉对象的交互方式](selection-api.md)。

### <a name="the-visual-interacts-with-power-bi"></a>视觉对象与 Power BI 交互

* 视觉对象请求 Power BI 中的更多数据。

    视觉对象可以按部分处理数据部分。 FetchMoreData API 方法请求下一个数据集片段。

    有关 `fetchMoreData` 的详细信息，请参阅[如何从 Power BI 获取更多数据](fetch-more-data.md)

* 事件服务

    Power BI 可以将报表导出为 PDF 或通过电子邮件发送（仅支持经过认证的视觉对象）。 若要通知 Power BI 已完成呈现，并且已准备好捕获 PDF/电子邮件，视觉对象应调用呈现事件 API。

    有关详细信息，请参阅[从 Power BI 导出报表到 PDF](../../consumer/end-user-pdf.md)

    查找更多[事件服务的信息](event-service.md)

## <a name="next-steps"></a>后续步骤

你是 Web 开发者吗？对创建自己的可视化效果，并将它们添加到 AppSource 感兴趣吗？ 请参阅[开发 Power BI 视觉对象](./custom-visual-develop-tutorial.md)，了解如何[将 Power BI 视觉对象发布到 AppSource](../office-store.md)。

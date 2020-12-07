---
title: Power BI 视觉对象 API 更改日志
description: 本文介绍不同版本的 Power BI 视觉对象 API 中的主要更改
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: c43542bc6c2bb0699403062f68024f9718bbbb60
ms.sourcegitcommit: 54e571a10b0fdde5cd6036017eac9ef228de5116
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501940"
---
# <a name="power-bi-visuals-api-changelog"></a>Power BI 视觉对象 API 更改日志
此页面包含 API 版本的快速摘要。 此处列出的版本被视为稳定版本，不会更改。


## <a name="api-v340"></a>API v3.4.0
  * `fetchMoreData`：新的 `aggregateSegments` 参数（默认为 True），用于支持无聚合 fetchMoreData

## <a name="api-v320"></a>API v3.2.0
  * 支持 [supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)

## <a name="api-v260"></a>API v2.6.0
  * 将 isInFocus 添加到更新选项，并将 switchFocusModeState 方法添加到视觉对象主机
  * 支持“小计”自定义

## <a name="api-v250"></a>API v2.5.0
  * 支持[分析窗格](./analytics-pane.md)
  * 支持 `SelectionIdBuilder` withMatrixNode 和 withTable 方法
  * 不再支持 `DataRepetitionSelector` 接口，已替换为 `data.CustomVisualOpaqueIdentity` 接口

## <a name="api-v230"></a>API v2.3.0
  * [登陆页 API](./landing-page.md)
  * [本地存储 API](./local-storage.md)
  * 元组筛选器 API（多列筛选器） [](./filter-api.md#the-tuple-filter-api-multi-column-filter)
  * 呈现事件 API [](./event-service.md#render-events-in-power-bi-visuals)

## <a name="api-v220"></a>API v2.2.0
  * 支持 **[从数据视图还原 JSON 筛选器](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * ContextMenu API [](./context-menu.md)

## <a name="api-v210"></a>API v2.1.0
  * 性能增强：
    * 加载时间更快
    * 内存占用情况更小
    * 优化的数据和事件事务  

**发行说明**
* 重构的筛选 API 将在 API 2.2 中提供，在 API 2.1 中不受支持。
* 视觉对象将仅接收在其功能中声明的 dataView 类型。 由于此更新，使用了多个 dataView 类型的视觉对象将中断。
* 不再支持 `DataViewScopeIdentity` 接口，已替换为 `data.DataRepetitionSelector` 接口。 如果使用了 `DataViewScopeIdentity` 接口的关键属性，则可使用 `JSON.stringify(identity)` 将其替换
* `undefined` 由 dataView 中的 `null` 替换。 使用 `var item in myArray` 循环访问数组时，它会跳到 `undefined`，但不会跳到 `null`。 此更新可能会破坏使用此模式的视觉对象。 确保检查数组中的 `null`：
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* `proto` 属性不再将隐藏的元数据/数据存储在 dataView 中。 通过 `proto` 访问属性的视觉对象可能会被此更新中断。

## <a name="api-v1130"></a>API v1.13.0
* 支持 **同步切片器 [](./enable-sync-slicers.md)** ，请注意，由于 PBI 当前代码状态，此方法仅适用于单字段切片器， [了解更多信息](../../visuals/power-bi-visualization-slicers.md)。
* 辅助功能：[高对比度支持](./high-contrast-support.md) 
* 辅助功能：允许键盘焦点标志

## <a name="api-v1120"></a>API v1.12.0
* 支持主题
* 支持 **fetchMoreData [](./fetch-more-data.md)** ，请注意，提取“更多的数据 API”克服 30000 数据点的硬限制
* **画布工具提示 API [](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **FilterManager API [](./filter-api.md)**
* 支持 **书签 [](./bookmarks-support.md)** 

## <a name="api-v1100"></a>API v1.10.0
* 添加 `ILocalizationManager`
* 身份验证 API

## <a name="api-v190"></a>API v1.9.0
* **launchUrl API [](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* 支持功能架构中的新型 fillRule（渐变）
* 支持功能架构中对象属性的 rule 属性

## <a name="api-v170"></a>API v1.7.0
* 支持 **RESJSON [](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* 支持 **编辑模式 [](./advanced-edit-mode.md)** ，以使视觉对象进入可视编辑模式
* 支持基于 html 的 **[交互式 (html) R Power BI 视觉对象](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)**

## <a name="api-v150"></a>API v1.5.0
* 支持 **允许交互 [](./visuals-interactions.md)** ，以实现视觉对象交互

## <a name="api-v140"></a>API v1.4.0
* 支持 **[本地化](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* 支持 **工具提示 [](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* 添加 colorPalette，以管理视觉对象上使用的颜色。
* 支持多选 - selectionManager 可以接受 `SelectionId` 的数组。
* 支持使用 R 脚本的 **[R 视觉对象](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)**

## <a name="api-v110"></a>API v1.1.0
* 支持 iFrame 中的调试视觉对象
* 通过更快地初始化 iFrame 来添加轻型沙盒
* 修复 [Capabilities.objects 不支持“text”类型](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)问题
* 支持 `pbiviz update` 以更新视觉对象 API 类型定义和架构
* 支持 `pbiviz new` 中的 `--api-version` 标志，以使用特定 API 版本创建视觉对象
* 支持 API v1.2.0 的 alpha 发布

**视觉对象主机**
* 添加 createSelectionIdBuilder，以创建用于数据选择的唯一标识符
* 添加 createSelectionManager 以管理视觉对象的选择状态，并将更改传达给视觉对象主机
* 添加要在视觉对象中使用的默认颜色数组

## <a name="api-v100"></a>API v1.0.0
* 初始 API 版本

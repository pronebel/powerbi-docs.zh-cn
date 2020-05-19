---
title: 视觉对象 API
description: 本文介绍了如何将 IVisual API 用于 Power BI 视觉对象
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302957"
---
# <a name="visual-api"></a>视觉对象 API
所有视觉对象都以实现 `IVisual` 接口的类开头。 只要有一个实现 `IVisual` 接口的类，你就可以按需命名这个类。

> [!NOTE]
> 视觉对象类的名称必须与 pbiviz.json 文件中的定义相符。

请参阅使用以下应实现的方法的视觉对象类示例：

* `constructor`，一个初始化视觉对象状态的标准构造函数
* `update`，用于更新视觉对象的数据
* `enumerateObjectInstances`，用于返回对象以填充属性窗格（格式设置选项），可根据需要在其中进行修改
* `destroy`，一个用于清理的标准析构函数

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>构造函数

在实例化视觉对象时，将调用视觉对象类的构造函数。 它可用于视觉对象所需的任何设置操作。

```typescript
constructor(options: VisualConstructorOptions)
```

VisualConstructorOptions

* `element: HTMLElement`，对将包含视觉对象的 DOM 元素的引用
* `host: IVisualHost`，可用于与视觉对象主机 (Power BI) 进行交互的属性和服务的集合

   `IVisualHost` 包含以下服务：

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`，生成并存储视觉对象中可选项目的元数据
   * `createSelectionManager`，创建用于在选择状态更改时通知视觉对象主机的通信桥，请参阅[选择 API](./selection-api.md)。
   * `createLocalizationManager`，生成一个管理器来帮助进行[本地化](./localization.md)
   * `allowInteractions: boolean`，一个布尔标志，指示视觉对象是否应该是交互式的
   * `applyJsonFilter`，应用特定的筛选器类型，请参阅[筛选器 API](./filter-api.md)
   * `persistProperties`，允许用户保留属性并将其与视觉对象定义一起保存，使其在下次重载时可用
   * `eventService`，返回一个[事件服务](./event-service.md)来支持 Render 事件
   * `storageService`，返回一个服务，以帮助在视觉对象中使用[本地存储](./local-storage.md)
   * `authenticationService`，生成一个服务以帮助用户进行身份验证
   * `tooltipService`，返回一个[工具提示服务](./add-tooltips.md)，以帮助在视觉对象中使用工具提示
   * `launchUrl`，帮助在下一个选项卡中[启动 URL](./launch-url.md)
   * `locale`，返回一个区域设置字符串，请参阅[本地化](./localization.md)
   * `instanceId`，返回一个字符串来识别当前的视觉对象实例
   * `colorPalette`，返回为数据应用颜色所需的 colorPalette
   * `fetchMoreData`，支持使用超过标准限制（1000 行）的数据
   * `switchFocusModeState`，帮助更改焦点模式状态

## <a name="update"></a>update

所有视觉对象都必须实现一个公共更新方法，每当数据或主机环境发生变化时，就会调用该方法。

```typescript
public update(options: VisualUpdateOptions): void
```

VisualUpdateOptions

* `viewport: IViewport`，应在其中呈现视觉对象的视区的尺寸
* `dataViews: DataView[]`，包含呈现视觉对象所需的所有数据的数据视图对象（视觉对象通常使用 DataView 下的分类属性）
* `type: VisualUpdateType`，用于指示此更新类型 (Data | Resize | ViewMode | Style | ResizeEnd) 的标志
* `viewMode: ViewMode`，用于指示视觉对象的视图模式 (View | Edit | InFocusEdit) 的标志
* `editMode: EditMode`，用于指示视觉对象的编辑模式（“默认” | “高级”）的标志（如果视觉对象支持 AdvancedEditMode，则它应仅在“editMode”设置为“高级”时，呈现其高级 UI 控件，请参阅 [AdvancedEditMode](./advanced-edit-mode.md)）
* `operationKind?: VisualDataChangeOperationKind`，用于指示数据更改类型（“创建” | “追加”）的标志
* `jsonFilters?: IFilter[]`，应用 json 筛选器的集合
* `isInFocus?: boolean`，指示视觉对象是否处于焦点模式的标志
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

功能中列出的每个对象都会调用此方法。 使用选项（目前只是名称），将返回一个 `VisualObjectInstanceEnumeration`，其中包含有关如何显示此属性的信息。

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

EnumerateVisualObjectInstancesOptions

* `objectName: string`，对象的名称

## <a name="destroy-optional"></a>销毁 `optional`

卸载视觉对象时，将调用销毁函数，该函数可用于清理任务，例如，删除事件侦听器。

``` typescript
public destroy(): void
```

> [!Note]
> Power BI 通常不调用 `destroy`，因为删除包含视觉对象的整个 IFrame 更快。

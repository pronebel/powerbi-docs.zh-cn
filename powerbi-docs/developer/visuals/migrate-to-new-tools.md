---
title: 迁移到 powerbi-visuals-tools 版本 3.x
description: 新版本的 powerbi-visuals-tools 入门
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818815"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>迁移到新 powerbi-visuals-tools 版本 3.x

从版本 3 开始，Power BI 视觉对象工具（powerbi-visuals-tools 或 `pbiviz`）使用 Webpack 来生成自定义视觉对象。
新版本为开发者提供了许多有关创建视觉对象方面的改进：

- 默认使用 TypeScript 版本 3.x。 从 TypeScript 1.5 开始，已更改了命名法。 [阅读更多有关 TypeScript 模块的详细信息](https://www.typescriptlang.org/docs/handbook/modules.html)。

- 支持 ECMAScript 6 (ES6) 模块。 现在使用 ES6 导入，而不是 [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries)。

- 支持新版本的数据驱动文档 ([D3v5](https://d3js.org/)) 和其他基于 ES6 模块的库。

- 减小了包的大小。 Webpack 使用 [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) 来删除未使用的代码。 它减少了 JavaScript 代码，使你能够更好地加载视觉对象。

- 提高了 API 性能。

- Globalize.js 库[集成](migrate-to-new-tools.md#remove-the- globalizejs-library)到 FormattingUtils。

- Power BI 视觉对象工具使用 [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) 来显示视觉对象的基本代码。

本文介绍了新版本 Power BI 视觉对象工具的所有迁移步骤。

## <a name="backward-compatibility"></a>向后兼容性

新工具为旧的视觉对象基本代码保留了后向兼容性信息，但可能需要进行一些额外的更改以加载外部库。

支持模块系统的库将作为 Webpack 模块导入。 视觉对象的所有其他库和源代码都将包装到一个模块中。

以前的 Power BI 视觉对象工具中使用的全局变量（如 JQuery 和 Lodash）现已过时。 如果视觉对象旧代码依赖于全局变量，则该视觉对象可能无法使用新工具。

以前版本的 Power BI 视觉对象工具需要在 `powerbi.extensibility.visual` 模块下定义一个视觉对象类。 使用新版本的工具，必须在主 TypeScript (.ts) 文件中定义一个视觉对象类。 通常情况下，该文件是 `src/visual.ts`。

## <a name="install-powerbi-visuals-tools"></a>安装 powerbi-visuals-tools

运行以下命令来安装新工具：

```cmd
npm install -g powerbi-visuals-tools
```

以下代码在视觉对象项目更新为使用新工具之后来自 [sampleBarChart 视觉对象存储库](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15)中的 `package.json` 文件：

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>安装 Power BI 自定义视觉对象 API

新版本的 powerbi-visuals-tools 中不包含所有 API 版本。 相反，必须安装特定版本的 [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api) 包。 选择与 Power BI 自定义视觉对象的 API 版本匹配的包版本。 该包提供了 Power BI 自定义视觉对象 API 的所有类型定义。

通过运行以下命令将 `powerbi-visuals-api` 添加到项目的项目依赖项中：

```cmd
npm install --save-dev powerbi-visuals-api
```

另外，删除指向旧 API 类型定义的任何链接，因为 Webpack 会自动包含 `powerbi-visuals-api` 中的类型。 相应的更改位于 [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) 和 [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14)。

## <a name="update-tsconfigjson"></a>更新 tsconfig.json

若要使用外部模块，请将 `out` 选项更改为 `outDir`。 例如，使用 `"outDir": "./.tmp/build/",` 而不是 `"out": "./.tmp/build/visual.js",`。

此更改是必需的，因为 TypeScript 文件将单独编译到 JavaScript 文件中。 这就是不再需要将 visual.js 文件指定为输出的原因。

如果要使用新式 JavaScript 作为输出，还可以将 `target` 选项改为 `ES6`。 此更改是[可选的](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7)。

## <a name="update-custom-visuals-utilities"></a>更新自定义视觉对象实用工具

如果使用任何 [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) 包，也将它们更新到最新版本。 为此，请运行以下命令：

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

例如，若要获取带有 TypeScript 外部模块的新版本，请运行： 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

有关使用所有 `powerbi-visuals-utils` 包的视觉对象示例，请参阅 [MekkoChart 存储库](https://github.com/Microsoft/powerbi-visuals-mekkochart)。

## <a name="remove-the-globalizejs-library"></a>删除 Globalize.js 库

新版本的 [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) 包含 Globalize.js。 因此，无需将此库手动包含在项目中。 所有必需的本地化将自动添加到最终包中。

## <a name="configure-loading-of-external-libraries"></a>配置外部库的加载

在 `pbiviz.json` 的 `externalJS` 数组中的库之后包含新的 JavaScript 文件。 例如：

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

导入源代码中的库。 例如，对于 `lodash-es`，使用以下语句：

```JS
import * as _ from "lodash-es";
```

在前面的示例中，`_` 是 `lodash` 库的全局变量。

## <a name="make-changes-in-the-sources-of-your-visuals"></a>更改视觉对象的源

必须进行的主要更改是将内部模块转换为外部模块。 不能在内部模块中使用外部模块。

以下是要进行的更改的详细说明。 这些修改在条形图自定义视觉对象代码示例的上下文中进行了描述：

1. 从每个[源代码](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3)文件中删除所有模块定义：

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [导入 Power BI 自定义视觉对象 API 定义](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4)：

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. 从 `powerbi` 内部模块[导入必需的接口或类](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35)。

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [导入 D3.js 库](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2)：

    ```typescript
    import * as d3 from "d3";
    ```

    或仅导入所需的 D3 库模块：

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [将视觉对象项目中定义的实用工具、类和接口导入](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41)到主源文件：

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>导入 CSS 样式

新版工具使你能够将 `CSS` 和 `Less` 样式直接导入到 TypeScript 代码中。 现在，编译器将忽略以前使用过的[样式部分](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21)。

若要使用样式表，请打开主 TypeScript (.ts) 文件并添加此行：  

```typescript
import "./../style/visual.less";
```  

`CSS`、`Less` 样式将自动进行编译。

### <a name="externaljs-section-in-pbivizjson"></a>externalJS section in pbiviz.json

工具[不需要将 `externalJS` 库的列表](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20)加载到视觉对象捆绑包中，因为 Webpack 包含所有导入的库。

> [!NOTE]
> 在 `pbiviz.json` 中，将 `externalJS` 部分留空。

使用典型命令 `npm run package` 创建视觉对象包，或使用 `npm run start` 启动开发服务器。

## <a name="update-the-d3js-library-to-version-5"></a>将 D3.js 库更新到版本 5

使用新视觉对象工具即可开始使用新版本的 D3.js 库。 运行以下命令以更新视觉对象项目中的 D3：

- `npm install --save d3@5` 用于安装新的 D3.js。

- `npm install --save-dev @types/d3@5` 用于安装 D3.js 的新类型定义。

> [!IMPORTANT]
> D3 版本 5 引入了几项重大更改。

修改代码以使用新的 D3.js：

- 接口 `d3.Selection<T>` [已更改](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157)为 `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`。

- 不能通过单一调用 `attr` 方法应用多个属性。 相反，必须在对 `attr` 的[单独调用中传递每个属性](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278)。 并且还[对 `style` 方法进行单独调用](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247)。

- D3.js 版本 4 引入了新的 `merge` 方法。 此方法通常用于在数据联接操作之后合并 `enter` 和 `update` 选择。 若要正确使用 D3，请[调用 `merge` 方法](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272)。

[详细了解](https://github.com/d3/d3/blob/master/CHANGES.md) D3.js 库中的更改。

## <a name="install-babel-and-core-js"></a>安装 Babel 和 core-js

从版本 3.1 开始，视觉对象工具使用 Babel 将新式 JavaScript 代码编译为旧 ECMAScript 5 (ES5)，以支持范围广泛的浏览器。

默认情况下启用 Babel 选项，但必须手动导入 [`core-js`](https://www.npmjs.com/package/core-js) 包。 运行以下命令来安装包：

```cmd
npm install --save core-js
```

然后，在视觉对象代码的起始点导入包。 通常，这是“src/visual.ts”文件。

```JS
import "core-js/stable";
```

有关 Babel 的详细信息，请参阅[文档](https://babeljs.io/docs/en/)。

---
title: 迁移到 powerbi-visuals-tools 3.x
description: 新版本的 powerbi-visuals-tools 入门
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cc554bff1cbd248ccd69a80ee47b60af981cdab1
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061813"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>迁移到新的 powerbi-visuals-tools 3.x.x

从版本 3 开始，Power BI 视觉对象工具使用 Webpack 来生成自定义视觉对象。
新版本为开发人员带来了许多创建视觉对象的新机会：

* 默认情况下，TypeScript v3.x.x。 从 TypeScript 1.5 开始，已更改了命名法。 [阅读更多有关 TypeScript 模块的详细信息](https://www.typescriptlang.org/docs/handbook/modules.html)。

* 支持 ES6 模块。 无需再使用 [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries)，请改用 ES6 导入内容。

* 支持新版本的 [D3v5](https://d3js.org/) 和其他基于 ES6 模块的库。

* 减小了包的大小。 Webpack 使用 [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) 来删除未使用的代码。 它减少了 JS 的代码，因此，你可以在视觉对象加载时获得更好的性能。

* 提高了 API 性能。

* Globalize.js 库[集成](migrate-to-new-tools.md#remove-globalizejs-library)到 formatting-utils。

* 工具使用 [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) 来显示视觉对象的基本代码。

下面介绍了新版本 Power BI 视觉对象工具的所有迁移步骤。

## <a name="backward-compatibility"></a>后向兼容性

新工具为旧的视觉对象基本代码保留了后向兼容性，但可能需要进行一些额外的更改以加载外部库。

支持模块系统的库将作为 Webpack 模块导入。 所有其他库和视觉对象源代码将包装到一个模块中。

以前的 pbiviz 工具中使用的全局变量（如 JQuery 和 Lodash）现已过时。 这意味着，如果旧的视觉对象代码在全局变量上中继，则在这种情况下视觉对象可能损坏。

以前版本的 Power BI 视觉对象工具需要在 `powerbi.extensibility.visual` 模块下定义一个视觉对象类。

## <a name="how-to-install-powerbi-visuals-tools"></a>如何安装 powerbi-visuals-tools

可以通过执行命令来安装新的工具集

```cmd
npm install -g powerbi-visuals-tools
```

SampleBarChart 视觉对象的示例与 `package.json` 中相应的[更改](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) ：

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>如何安装 Power BI 自定义视觉对象 API

新版本的 powerbi-visual-tools 中不包含所有 API 版本。 开发人员应安装特定版本的 [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api) 包。 包的版本与 Power BI 自定义视觉对象的 API 版本相匹配，它为 Power BI 自定义视觉对象 API 提供所有类型定义。

通过执行命令 `npm install --save-dev powerbi-visuals-api` 将 `powerbi-visuals-api` 添加到项目的依赖项。
你应当删除指向旧 API 类型定义的链接。 因为 Webpack 自动包含 `powerbi-visuals-api` 中的类型。 对应的更改在 `package.json` 的[此](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14)行。

## <a name="update-tsconfigjson"></a>更新​​ `tsconfig.json`

若要使用外部模块，应将 `out` 选项切换为 `outDir`。
`"outDir": "./.tmp/build/",` 而不是 `"out": "./.tmp/build/visual.js",`。

需要将它作为 TypeScript 文件单独编译到 JavaScript 文件中。 这就是不再需要将 visual.js 文件指定为输出的原因。

如果要使用新式 JavaScript 作为输出，还可以将 `target` 选项改为 `ES6`。 [它是可选的](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6)。

## <a name="update-custom-visuals-utils"></a>创建自定义视觉对象 utils

如果使用 [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) 之一，则还应将其更新到最新版本。

执行命令 `npm install powerbi-visuals-utils-<UTILNAME> --save`。 （例如 `npm install powerbi-visuals-utils-dataviewutils --save`）以获取带有 TypeScript 外部模块的新版本。

可以在 MekkoChart [存储库](https://github.com/Microsoft/powerbi-visuals-mekkochart)中找到示例。
此视觉对象使用所有 utils。

## <a name="remove-globalizejs-library"></a>删除 Globalize.js 库

新版本的 [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) 包含现成的 globalize.js。
无需将此库手动包含在项目中。
所有必需的本地化将自动添加到最终包中。

## <a name="fix-loading-external-libraries"></a>解决加载外部库

而是在 `pbiviz.json` 的 `externalJS` 数组中的库后包含新的 JS 文件。 示例:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

导入源中的库。 `lodash-es` 的示例：

```JS
import * as _ from "lodash-es";
```

其中 `_` 是 `lodash` 库的全局变量。

## <a name="changes-in-the-visuals-sources"></a>视觉对象源中的更改

主要更改是将内部模块转换为外部模块，因为不能在内部模块中使用外部模块。

这些更改描述了已应用于示例条形图的修改

下面是有关更改的详细说明：

1. 从每个[源代码](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)文件中删除所有模块定义

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [导入 Power BI 自定义视觉对象 API 定义](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2)。

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. 从 `powerbi` 内部模块[导入](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23)必需的接口或类。

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

4. [导入](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) D3.js 库

    ```typescript
    import * as d3 from "d3";
    ```

    或仅导入所需的 d3 库模块

    ```typescript
    import { max, min } from "d3-array";
    ```

5. 将视觉对象项目中定义的 utils、类和接口[导入](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10)到主源文件

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

新版工具使开发人员能够将 CSS、LESS 样式直接导入到 TypeScript 代码中。

因此，编译器将忽略以前使用的[样式部分](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22)。

若要使用样式表，请打开主 ts 文件，并添加以下行：  

```typescript
import "./../style/visual.less";
```  

CSS、LESS 样式将自动进行编译。  

### <a name="externaljs-section-in-pbivizjson"></a>externalJS section in pbiviz.json

这些工具[不需要](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20)将 `externalJS` 列表加载到视觉对象捆绑包。 因为 webpack 包括所有导入库。

pbivi.json 中的 externalJS 部分应为空  。

调用典型命令 `npm run package` 创建视觉对象包或 `npm run start` 以启动 dev 服务器。

## <a name="updating-d3js-library-to-version-5"></a>将 D3.js 库更新到版本 5

使用新工具即可开始使用新版本的 D3.js 库。

调用命令以更新视觉对象项目中的 D3

`npm install --save d3@5` 用于安装新的 D3.js。

`npm install --save-dev @types/d3@5` 用于安装 D3.js 的新类型定义。

由于存在一些重大更改，应修改代码以使用新的 D3.js。

1. 接口 `d3.Selection<T>` [已更改](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157)为 `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. 不能通过单一调用 `attr` 方法应用多个属性。 [应传递](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) `attr` 方法的不同调用中的每个属性。 对于 `style` 方法也采用[类似](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247)操作。

3. 在 D3.js v4 中，引入了新的合并方法。 此方法通常用于在进行数据联接后合并输入和更新选择。 [调用合并方法](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272)以正确使用 d3。

[详细了解](https://github.com/d3/d3/blob/master/CHANGES.md) D3.js 库中的更改。

## <a name="babel"></a>Babel

从版本 3.1 开始，工具使用 Babel 将新式 JS 代码编译为旧 ES5，以支持范围广泛的浏览器。

默认情况下启用此选项，但你需要手动导入 [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill) 包。

执行命令以安装包

`npm install --save @babel/polyfill`

并在视觉对象代码的起始点（通常为“src/visual.ts”文件）导入包：

`import "@babel/polyfill";`

有关 Babel 的详细信息，请参阅[文档](https://babeljs.io/docs/en/)。

最后，运行 [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) 以显示视觉对象的基本代码。  

![视觉对象代码统计信息](./media/webpack-stats.png)

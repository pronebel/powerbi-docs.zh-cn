---
title: 关于在 Power BI 嵌入式分析的 Power BI 视觉对象中使用单元测试以增强嵌入式 BI 见解的介绍
description: 本文介绍如何为 Power BI 视觉对象项目编写单元测试。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: ee7ed48043a902a9b5ebd3c548ebec7505e76ab1
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887905"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>教程：为 Power BI 视觉对象项目添加单元测试

本文介绍了为 Power BI 视觉对象编写单元测试的相关基础知识，包括如何：

* 设置 Karma JavaScript 测试运行程序测试框架 Jasmine。
* 使用 powerbi-visuals-utils-testutils 包。
* 借助 Mocks 和 Fakes 来简化 Power BI 视觉对象的单元测试。

## <a name="prerequisites"></a>先决条件

* 已安装的 Power BI 视觉对象项目
* 经过配置的 Node.JS 环境

## <a name="install-and-configure-the-karma-javascript-test-runner-and-jasmine"></a>安装和配置 Karma JavaScript 测试运行程序和 Jasmine

将所需的库添加到 `devDependencies` 部分中的 package.json 文件中：

```json
"@babel/polyfill": "^7.2.5",
"@types/d3": "5.5.0",
"@types/jasmine": "2.5.37",
"@types/jasmine-jquery": "1.5.28",
"@types/jquery": "2.0.41",
"@types/karma": "3.0.0",
"@types/lodash-es": "4.17.1",
"coveralls": "3.0.2",
"istanbul-instrumenter-loader": "^3.0.1",
"jasmine": "2.5.2",
"jasmine-core": "2.5.2",
"jasmine-jquery": "2.1.1",
"jquery": "3.1.1",
"karma": "3.1.1",
"karma-chrome-launcher": "2.2.0",
"karma-coverage": "1.1.2",
"karma-coverage-istanbul-reporter": "^2.0.4",
"karma-jasmine": "2.0.1",
"karma-junit-reporter": "^1.2.0",
"karma-sourcemap-loader": "^0.3.7",
"karma-typescript": "^3.0.13",
"karma-typescript-preprocessor": "0.4.0",
"karma-webpack": "3.0.5",
"puppeteer": "1.17.0",
"style-loader": "0.23.1",
"ts-loader": "5.3.0",
"ts-node": "7.0.1",
"tslint": "^5.12.0",
"webpack": "4.26.0"
```

若要详细了解 package.json，请参阅 [npm-package.json](https://docs.npmjs.com/files/package.json) 中的说明。

保存 package.json 文件，并在 `package.json` 位置运行以下命令：

```cmd
npm install
```

包管理器安装已添加到 package.json 的所有新包。

要运行单元测试，请配置测试运行程序和 `webpack` 配置。

以下代码是 test.webpack.config.js 文件的示例：

```typescript
const path = require('path');
const webpack = require("webpack");

module.exports = {
    devtool: 'source-map',
    mode: 'development',
    optimization : {
        concatenateModules: false,
        minimize: false
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: /node_modules/
            },
            {
                test: /\.json$/,
                loader: 'json-loader'
            },
            {
                test: /\.tsx?$/i,
                enforce: 'post',
                include: /(src)/,
                exclude: /(node_modules|resources\/js\/vendor)/,
                loader: 'istanbul-instrumenter-loader',
                options: { esModules: true }
            },
            {
                test: /\.less$/,
                use: [
                    {
                        loader: 'style-loader'
                    },
                    {
                        loader: 'css-loader'
                    },
                    {
                        loader: 'less-loader',
                        options: {
                            paths: [path.resolve(__dirname, 'node_modules')]
                        }
                    }
                ]
            }
        ]
    },
    externals: {
        "powerbi-visuals-api": '{}'
    },
    resolve: {
        extensions: ['.tsx', '.ts', '.js', '.css']
    },
    output: {
        path: path.resolve(__dirname, ".tmp/test")
    },
    plugins: [
        new webpack.ProvidePlugin({
            'powerbi-visuals-api': null
        })
    ]
};
```

以下代码是 karma.conf.ts 文件的示例：

```typescript
"use strict";

const webpackConfig = require("./test.webpack.config.js");
const tsconfig = require("./test.tsconfig.json");
const path = require("path");

const testRecursivePath = "test/visualTest.ts";
const srcOriginalRecursivePath = "src/**/*.ts";
const coverageFolder = "coverage";

process.env.CHROME_BIN = require("puppeteer").executablePath();

import { Config, ConfigOptions } from "karma";

module.exports = (config: Config) => {
    config.set(<ConfigOptions>{
        mode: "development",
        browserNoActivityTimeout: 100000,
        browsers: ["ChromeHeadless"], // or Chrome to use locally installed Chrome browser
        colors: true,
        frameworks: ["jasmine"],
        reporters: [
            "progress",
            "junit",
            "coverage-istanbul"
        ],
        junitReporter: {
            outputDir: path.join(__dirname, coverageFolder),
            outputFile: "TESTS-report.xml",
            useBrowserName: false
        },
        singleRun: true,
        plugins: [
            "karma-coverage",
            "karma-typescript",
            "karma-webpack",
            "karma-jasmine",
            "karma-sourcemap-loader",
            "karma-chrome-launcher",
            "karma-junit-reporter",
            "karma-coverage-istanbul-reporter"
        ],
        files: [
            "node_modules/jquery/dist/jquery.min.js",
            "node_modules/jasmine-jquery/lib/jasmine-jquery.js",
            {
                pattern: './capabilities.json',
                watched: false,
                served: true,
                included: false
            },
            testRecursivePath,
            {
                pattern: srcOriginalRecursivePath,
                included: false,
                served: true
            }
        ],
        preprocessors: {
            [testRecursivePath]: ["webpack", "coverage"]
        },
        typescriptPreprocessor: {
            options: tsconfig.compilerOptions
        },
        coverageIstanbulReporter: {
            reports: ["html", "lcovonly", "text-summary", "cobertura"],
            dir: path.join(__dirname, coverageFolder),
            'report-config': {
                html: {
                    subdir: 'html-report'
                }
            },
            combineBrowserReports: true,
            fixWebpackSourcePaths: true,
            verbose: false
        },
        coverageReporter: {
            dir: path.join(__dirname, coverageFolder),
            reporters: [
                // reporters not supporting the `file` property
                { type: 'html', subdir: 'html-report' },
                { type: 'lcov', subdir: 'lcov' },
                // reporters supporting the `file` property, use `subdir` to directly
                // output them in the `dir` directory
                { type: 'cobertura', subdir: '.', file: 'cobertura-coverage.xml' },
                { type: 'lcovonly', subdir: '.', file: 'report-lcovonly.txt' },
                { type: 'text-summary', subdir: '.', file: 'text-summary.txt' },
            ]
        },
        mime: {
            "text/x-typescript": ["ts", "tsx"]
        },
        webpack: webpackConfig,
        webpackMiddleware: {
            stats: "errors-only"
        }
    });
};
```

如有需要，可修改此配置。

Karma 中的代码包含以下变量：

* `recursivePathToTests`：定位测试代码

* `srcRecursivePath`：编译后，定位输出 JavaScript 代码

* `srcCssRecursivePath`：在使用样式编译较少的文件后定位输出 CSS

* `srcOriginalRecursivePath`：定位视觉对象的源代码

* `coverageFolder`：确定要创建覆盖率报表的位置

配置文件包含以下属性：

* `singleRun: true`：测试在持续集成 (CI) 系统上运行，或者可以运行一次。 可将设置更改为 false 以调试测试。 Karma 保持浏览器运行，以便可以使用控制台进行调试。

* `files: [...]`：在本数组中，可以指定要加载到浏览器的文件。 通常有源文件、测试用例、库（jasmine、测试实用工具）。 可以根据需要将其他文件添加到列表中。

* `preprocessors`：在本部分中，你将配置运行单元测试之前运行的操作。 这些操作包括将 typescript 预编译为 JavaScript、准备源映射文件以及生成代码覆盖率报表。 可以在调试测试时禁用 `coverage`。 覆盖率会生成测试覆盖率检查代码的附加代码，这会导致测试调试变得复杂。

如需了解所有 Karma 配置的说明，请转到 [Karma 配置文件](https://karma-runner.github.io/1.0/config/configuration-file.html)页。

为方便起见，可以在 `scripts` 中添加一个测试命令：

```json
{
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "typings":"node node_modules/typings/dist/bin.js i",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "pretest": "pbiviz package --resources --no-minify --no-pbiviz --no-plugin",
        "test": "karma start"
    }
    ...
}
```

现在可以开始编写单元测试了。

## <a name="check-the-dom-element-of-the-visual"></a>检查视觉对象的 DOM 元素

要测试视觉对象，首先须创建一个视觉对象实例。

### <a name="create-a-visual-instance-builder"></a>创建视觉对象实例生成器

使用以下代码将 visualBuilder.ts 文件添加到“测试”文件夹：

```typescript
import {
    VisualBuilderBase
} from "powerbi-visuals-utils-testutils";

import {
    BarChart as VisualClass
} from "../src/visual";

import  powerbi from "powerbi-visuals-api";
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class BarChartBuilder extends VisualBuilderBase<VisualClass> {
    constructor(width: number, height: number) {
        super(width, height);
    }

    protected build(options: VisualConstructorOptions) {
        return new VisualClass(options);
    }

    public get mainElement() {
        return this.element.children("svg.barChart");
    }
}
```

`build` 方法可用于创建视觉对象实例。 `mainElement` 是一个 get 方法，可在视觉对象中返回“root”文档对象模型 (DOM) 元素的实例。 Getter（可选）可使编写单元测试更容易。

现在已经生成了视觉对象实例。 现在来编写测试用例。 测试用例检查显示视觉对象时创建的 SVG 元素。

### <a name="create-a-typescript-file-to-write-test-cases"></a>创建用于编写测试用例的 typescript 文件

使用以下代码为测试用例添加 visualTest.ts 文件：

```typescript
import powerbi from "powerbi-visuals-api";

import { BarChartBuilder } from "./VisualBuilder";

import {
    BarChart as VisualClass
} from "../src/visual";

import VisualBuilder = powerbi.extensibility.visual.test.BarChartBuilder;

describe("BarChart", () => {
    let visualBuilder: VisualBuilder;
    let dataView: DataView;

    beforeEach(() => {
        visualBuilder = new VisualBuilder(500, 500);
    });

    it("root DOM element is created", () => {
        expect(visualBuilder.mainElement).toBeInDOM();
    });
});
```

调用了几种方法：

* [`describe`](https://jasmine.github.io/api/2.6/global.html#describe)：描述测试用例。 在 Jasmine 框架的上下文中，它通常描述一套或一组规范。

* `beforeEach`：在每次调用 `it` 方法之前调用，该方法在 [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach) 方法中定义。

* [`it`](https://jasmine.github.io/api/2.6/global.html#it)：定义单个规范。`it` 方法应包含一个或多个 `expectations`。

* [`expect`](https://jasmine.github.io/api/2.6/global.html#expect)：创建规范预期。如果所有预期均通过而未发生任何失败，规范成功。

* `toBeInDOM`：这是匹配程序的方法之一。 有关匹配程序的详细信息，请参阅 [Jasmine 命名空间：匹配程序](https://jasmine.github.io/api/2.6/matchers.html)。

有关 Jasmine 的详细信息，请参阅[Jasmine 框架文档](https://jasmine.github.io/)页。

### <a name="launch-unit-tests"></a>启动单元测试

此测试检查是否创建了视觉对象的根 SVG 元素。 要运行单元测试，请在命令行工具中输入以下命令：

```cmd
npm run test
```

`karma.js` 在 Chrome 浏览器中运行测试用例。

![在 Chrome 中打开的 Karma JavaScript](media/unit-tests-introduction/karmajs-chrome.png)

> [!NOTE]
> 必须在本地安装 Google Chrome。

在命令行窗口，将得到以下输出：

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open https://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at https://localhost:9876/
23 05 2017 12:24:30.850:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 12:24:31.059:INFO [launcher]: Starting browser Chrome
23 05 2017 12:24:33.160:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#2meR6hjXFmsE_fjiAAAA with id 5875251
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.194 secs / 0.011 secs)

=============================== Coverage summary ===============================
Statements   : 27.43% ( 65/237 )
Branches     : 19.84% ( 25/126 )
Functions    : 43.86% ( 25/57 )
Lines        : 20.85% ( 44/211 )
================================================================================
```

### <a name="how-to-add-static-data-for-unit-tests"></a>如何为单元测试添加静态数据

使用以下代码在“测试”文件夹中创建 visualData.ts 文件：

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;

import {
    testDataViewBuilder,
    getRandomNumbers
} from "powerbi-visuals-utils-testutils";

export class SampleBarChartDataBuilder extends TestDataViewBuilder {
    public static CategoryColumn: string = "category";
    public static MeasureColumn: string = "measure";

    public constructor() {
        super();
        ...
    }

    public getDataView(columnNames?: string[]): DataView {
        let dateView: any = this.createCategoricalDataViewBuilder([
            ...
        ],
        [
            ...
        ], columnNames).build();

        // there's client side computed maxValue
        let maxLocal = 0;
        this.valuesMeasure.forEach((item) => {
                if (item > maxLocal) {
                    maxLocal = item;
                }
        });
        (<any>dataView).categorical.values[0].maxLocal = maxLocal;
    }
}
```

`SampleBarChartDataBuilder` 类扩展 `TestDataViewBuilder` 并实现抽象方法 `getDataView`。

将数据放入数据字段存储桶时，Power BI 会生成基于数据的类别 `dataview` 对象。

![数据字段存储桶](media/unit-tests-introduction/fields-buckets.png)

在单元测试中，你没有可用于重现数据的 Power BI 核心函数。 但你需要将静态数据映射到类别 `dataview`。 `TestDataViewBuilder` 类可协助你进行映射。

有关数据视图映射的详细信息，请参阅 [DataViewMappings](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md)。

在 `getDataView` 方法中，使用数据调用 `createCategoricalDataViewBuilder` 方法。

在 `sampleBarChart` 视觉对象 [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) 文件中，我们有 dataRoles 和 dataViewMapping 对象：

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": "Measure"
    }
],
"dataViewMappings": [
    {
        "conditions": [
            {
                "category": {
                    "max": 1
                },
                "measure": {
                    "max": 1
                }
            }
        ],
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "select": [
                    {
                        "bind": {
                            "to": "measure"
                        }
                    }
                ]
            }
        }
    }
],
```

若要生成相同的映射，必须将以下参数设置为 `createCategoricalDataViewBuilder` 方法：

```typescript
([
    {
        source: {
            displayName: "Category",
            queryName: SampleBarChartData.ColumnCategory,
            type: ValueType.fromDescriptor({ text: true }),
            roles: {
                Category: true
            },
        },
        values: this.valuesCategory
    }
],
[
    {
        source: {
            displayName: "Measure",
            isMeasure: true,
            queryName: SampleBarChartData.MeasureColumn,
            type: ValueType.fromDescriptor({ numeric: true }),
            roles: {
                Measure: true
            },
        },
        values: this.valuesMeasure
    },
], columnNames)
```

其中，`this.valuesCategory` 是类别的数组：

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

`this.valuesMeasure` 是每个类别的度量值数组：

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

现在，可在单元测试中使用 `SampleBarChartDataBuilder` 类。

`ValueType` 类在 powerbi-visuals-utils-testutils 包中定义。 `createCategoricalDataViewBuilder` 方法需要 `lodash` 库。

将这些包添加到依赖项中。

在 `package.json` 中的 `devDependencies` 部分

```json
"lodash-es": "4.17.1",
"powerbi-visuals-utils-testutils": "2.2.0"
```

调用

```cmd
npm install
```

以安装 `lodash-es` 库。

现在，可再次运行单元测试。 必获得以下输出：

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open https://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at https://localhost:9876/
23 05 2017 16:19:58.346:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 16:19:58.394:INFO [launcher]: Starting browser Chrome
23 05 2017 16:19:59.873:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#NcNTAGH9hWfGMCuEAAAA with id 3551106
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (1.266 secs / 1.052 secs)

=============================== Coverage summary ===============================
Statements   : 56.72% ( 135/238 )
Branches     : 32.54% ( 41/126 )
Functions    : 66.67% ( 38/57 )
Lines        : 52.83% ( 112/212 )
================================================================================
```

视觉对象将在 Chrome 浏览器中打开，如下所示：

![UT 在 Chrome 中启动](media/unit-tests-introduction/karmajs-chrome-ut-runned.png)

摘要显示覆盖范围有所增加。 若要详细了解当前代码覆盖率，请打开 `coverage\index.html`。

![UT 覆盖率索引](media/unit-tests-introduction/code-coverage-index.png)

或查看 `src` 文件夹的范围：

![src 文件夹的覆盖率](media/unit-tests-introduction/code-coverage-src-folder.png)

在文件范围内，可查看源代码。 如果在单元测试期间未执行某些代码，`Coverage` 实用程序将以红色突出显示该行。

![visual.ts 文件的代码覆盖率](media/unit-tests-introduction/code-coverage-visual-src.png)

> [!IMPORTANT]
> 代码覆盖并不意味会实现好的视觉对象功能覆盖。 一个简单的单元测试可以在 `src\visual.ts` 中提供超过 96% 的覆盖率。

## <a name="next-steps"></a>后续步骤

当视觉对象就绪时，你可以提交并发布它。 有关详细信息，请参阅[将 Power BI 视觉对象发布到 AppSource](office-store.md)。

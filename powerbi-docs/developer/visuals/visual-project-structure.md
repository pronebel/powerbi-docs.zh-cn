---
title: Power BI 视觉对象项目结构
description: 本文介绍视觉对象项目的结构
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542084"
---
# <a name="power-bi-visual-project-structure"></a>Power BI 视觉对象项目结构

执行 pbiviz new `<visual project name>` 后，该工具将在 `<visual project name>` 文件夹中创建文件和文件夹的基本结构。

## <a name="visual-project-structure"></a>视觉对象项目结构

![视觉对象项目结构](./media/visual-project-structure.png)

* `.vscode` - 包含 VS Code 项目的设置。 要配置工作区，请编辑 `.vscode/settings.json` 文件。 在文档中阅读有关 [VS Code 设置](https://code.visualstudio.com/docs/getstarted/settings)的详细信息

* `assets` 文件夹仅包含 `icon.png` 文件。 该工具使用此文件作为 Power BI 可视化效果窗格中视觉对象的图标。

    ![可视化效果窗格](./media/visualization-pane-analytics-tab.png)

* `node_modules` 文件夹包含 [Node 包管理器安装的所有包](https://docs.npmjs.com/files/folders.html)。

* `src` 文件夹包含视觉对象的源代码。 默认情况下，该工具会创建两个文件：

  * `visual.ts` - 视觉对象的主要源代码。

  * `settings.ts` - 视觉对象设置的代码。 文件中的类简化了[使用视觉对象属性](./objects-properties.md#properties)的过程。

* `style` 文件夹包含视觉对象样式的 `visual.less` 文件。

* `capabilities.json` 文件包含视觉对象的主要属性和设置。 它允许视觉对象声明支持的功能、对象、属性和数据视图映射。

    在文档中阅读有关[功能](./capabilities.md)的详细信息。

* 对于 npm 修改了 `node_modules` 树或 `package.json` 的任何操作，将自动生成 `package-lock.json`。

    在 NPM 官方文档中阅读有关 [`package-lock.json`](https://docs.npmjs.com/files/package-lock.json) 的详细信息。

* `package.json` 描述了项目包。 它通常包含有关项目、其作者、说明和项目依赖项的信息。

    在 NPM 官方文档中阅读有关 [`package.json`](https://docs.npmjs.com/files/package.json.html) 的详细信息。

* `pbiviz.json` 包含视觉对象元数据。 在此文件中指定视觉对象的元数据。

    文件的典型内容：

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    其中

  * `name` - 视觉对象的内部名称。

  * `displayName` -Power BI 的 UI 界面中的视觉对象名称。

  * `guid` - 视觉对象的唯一 ID。

  * `visualClassName` -视觉对象的主类名称。 Power BI 创建此类的实例，以开始在 Power BI 报表中使用视觉对象。

  * `version` - 视觉对象的版本号。

  * `author` - 包含作者姓名和联系人电子邮件。

  * `assets` 中的 `icon` - 视觉对象的图标文件路径。

  * `externalJS` 包含视觉对象中使用的 JS 库的路径。

    > [!IMPORTANT]
    > 最新版本的工具 3.x.x 或更高版本不再使用 `externalJS`。

  * `style` 是样式文件的路径。

  * `capabilities` 是 `capabilities.json` 文件的路径。

  * `dependencies` 是 `dependencies.json` 文件的路径。 `dependencies.json` 包含有关基于 R 的视觉对象中使用的 R 包的信息。

  * `stringResources` 是由包含本地化内容的文件的路径组成的数组。

  在文档中阅读有关[视觉对象本地化](./localization.md)的详细信息

* `tsconfig.json` 是 TypeScript 的配置文件。

    在官方文档中阅读有关 [TypeScript 配置](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)的详细信息

    `files` 部分中的 `tsconfig.json` 必须包含 *.ts 文件的路径，在该文件中，将在 `pbiviz.json` 文件的 `visualClassName` 属性中指定视觉对象主类的位置。

* `tslint.json` 文件包含 TSLint 配置。

    在官方文档中阅读有关 [TSLint 配置](https://palantir.github.io/tslint/usage/configuration/)的详细信息

## <a name="next-steps"></a>后续步骤

* 阅读有关[视觉对象概念](./power-bi-visuals-concept.md)的详细信息，以便更好地理解视觉对象、用户和 Power BI 彼此交互的方式。

* [通过分步指南](./custom-visual-develop-tutorial.md)从头开始开发自己的 Power BI 视觉对象。

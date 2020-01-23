---
title: Power BI 视觉对象项目结构
description: 本文介绍了 Power BI 视觉对象项目的文件夹和文件结构
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 16e7a317102602ffb4faf04da0ed2cae588a2a4d
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925532"
---
# <a name="power-bi-visual-project-structure"></a>Power BI 视觉对象项目结构

开始创建新 Power BI 视觉对象的最佳方式是使用 Power BI 视觉对象 [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) 工具。

若要创建新的视觉对象，请导航至想要存储 Power BI 视觉对象的目录，然后运行以下命令：

`pbiviz new <visual project name>`

运行此命令将创建 Power BI 视觉对象文件夹，其中包含以下文件：

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>文件夹和文件说明

本部分提供 Power BI 视觉对象“pbiciz”  工具所创建目录中的各文件夹和文件信息。  

### <a name="vscode"></a>.vscode

此文件夹包含 VS code 项目设置。

要配置工作区，请编辑 `.vscode/settings.json` 文件。

有关详细信息，请参阅[用户和工作区设置](https://code.visualstudio.com/docs/getstarted/settings)

### <a name="assets"></a>资产

此文件夹包含 `icon.png` 文件。

Power BI 视觉对象工具使用此文件作为 Power BI 可视化效果窗格中的新 Power BI 视觉对象图标。

<!--- ![Visualization pane](./media/visualization-pane-analytics-tab.png) --->

### <a name="src"></a>src

此文件夹包含视觉对象的源代码。

在此文件夹中，Power BI 视觉对象工具会创建以下文件：
* `visual.ts` - 视觉对象的主要源代码。
* `settings.ts` - 视觉对象设置的代码。 文件中的类提供一个接口，用于定义[视觉对象的属性](./objects-properties.md#properties)。

### <a name="style"></a>样式

此文件夹包含保存视觉对象样式的 `visual.less` 文件。

### <a name="capabilitiesjson"></a>capabilities.json

此文件包含视觉对象的主要属性和设置（或[功能](./capabilities.md)）。 它允许视觉对象声明支持的功能、对象、属性和[数据视图映射](./dataview-mappings.md)。

### <a name="package-lockjson"></a>package-lock.json

对于 npm  修改了 `node_modules` 树或 `package.json` 文件的任何操作，将自动生成此文件。

有关此文件的详细信息，请参阅官方 [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) 文档。

### <a name="packagejson"></a>package.json

此文件描述了项目包。 它包含有关作者、说明和项目依赖项等项目信息。

有关此文件的详细信息，请参阅官方的 [npm-package.json](https://docs.npmjs.com/files/package.json.html) 文档。

### <a name="pbivizjson"></a>pbiviz.json

此文件包含视觉对象元数据。

若要查看 `pbiviz.json` 文件（包含说明元数据条目的注释）的示例，请参阅[元数据条目](#metadata-entries)部分。

### <a name="tsconfigjson"></a>tsconfig.json

[TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) 的配置文件。

此文件必须包含 **\*.ts** 文件的路径，在该文件中，将在 `pbiviz.json` 文件的 `visualClassName` 属性中指定视觉对象主类的位置。

### <a name="tslintjson"></a>tslint.json

此文件包含 [TSLint 配置](https://palantir.github.io/tslint/usage/configuration/)。

## <a name="metadata-entries"></a>元数据条目

`pbiviz.json` 文件的以下代码描述中的注释描述了元数据条目。

> [!NOTE]
> * 从“pbiciz”  工具的版本 3.x.x 开始，不再支持 `externalJS`。
> * 为获得本地化支持，[将 Power BI 区域设置添加到你的视觉对象](./localization.md)。

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>后续步骤

* 若要理解视觉对象、用户和 Power BI 之间的交互，请参阅 [Power BI 视觉对象概念](./power-bi-visuals-concept.md)。

* 使用[分步指南](./custom-visual-develop-tutorial.md)从头开始开发自己的 Power BI 视觉对象。
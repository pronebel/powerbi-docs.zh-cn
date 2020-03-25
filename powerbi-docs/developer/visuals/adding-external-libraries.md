---
title: 将外部库添加到 Power BI 视觉对象
description: 本文介绍了如何在 Power BI 视觉对象中使用外部库。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: 9df111e7545c43fe9b75784b1a95df4f37fd01e7
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114120"
---
# <a name="adding-external-libraries"></a>添加外部库

本文介绍了如何在 Power BI 视觉对象中使用外部库。 具体而言，介绍了如何在 Power BI 视觉对象的代码中安装、导入和调用外部库。

## <a name="javascript-libraries"></a>JavaScript 库

1. 使用任意包管理器（如 npm  或 yarn  ）安装外部 JavaScript 库。
2. 将必需模块导入使用外部库的源文件中。

>[!NOTE]
>若要将 typings 添加到 JavaScript 库，并获取 Intellisense 和编译时安全性，请务必安装相应包。

### <a name="installing-the-d3-library"></a>安装 d3 库

此示例展示了如何使用 [npm](https://www.npmjs.com/) 来安装 [d3 库](https://www.npmjs.com/package/d3)和 [@types/d3](https://www.npmjs.com/package/@types/d3) 包。

有关完整示例，请参阅 [Power BI 可视化效果](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29)代码。

1. 安装 d3  包和 d3 types  包。

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. 将 d3  库导入使用它的文件（如 `visual.ts`）中。

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS 框架

1. 使用任意包管理器（如 npm  或 yarn  ）安装外部 CSS 框架。
2. 在视觉对象的 `.less` 文件中，添加 `import` 语句。

### <a name="installing-bootstrap"></a>安装 bootstrap

此示例展示了如何使用 [npm](https://www.npmjs.com/) 来安装 [bootstrap](https://www.npmjs.com/package/bootstrap)。

有关完整示例，请参阅 [Power BI 可视化效果](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32)代码。

1. 安装 bootstrap  包。

    ```powershell
    npm install bootstrap --save
    ```

2. 在 `visual.less` 中添加 `import` 语句。

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```

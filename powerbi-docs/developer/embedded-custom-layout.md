---
title: 包含 Power BI 嵌入式内容的自定义布局
description: 了解在应用程序中嵌入 Power BI 内容时的自定义布局。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/19/2017
ms.openlocfilehash: 28d11a30f7998dc63f86b98fd72d18968480e711
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61344150"
---
# <a name="custom-layouts"></a>自定义布局

使用自定义布局可以嵌入采用不同于原始报表的布局的报表。 定义新布局的过程根据是仅定义页面大小、控制视觉大小还是控制位置和可见性而有所不同。

若要定义自定义布局，请定义一个自定义布局对象，然后将它传入 embed 配置中的 settings 对象。 此外，请将 LayoutType 设置为 Custom。 有关详细信息，请参阅 [Embed 配置详细信息](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details)。

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom
    customLayout: {...}
    }
};
```

## <a name="object-definition"></a>对象定义

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Cortana,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`：使用页面大小控制画布区域大小（即报表白色区域）。
- `displayOptions`：可能的值为：FitToWidth、FitToPage 或 ActualSize。 它控制如何缩放画布，以适合 iframe。
- `pagesLayout`：控制每个视觉对象的布局。 有关更多详细信息，请参阅“PagesLayout”。

## <a name="pages-layout"></a>页面布局

简单而言，定义页面布局就是为每个页面定义布局，并为每个页面的每个视觉对象定义布局。
PageLayout 是可选的。 如果未定义页面布局，将应用默认布局（保存在报表中）。

pagesLayout 是从页面名称到 PageLayout 对象的映射。 定义：

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

PageLayout 包含一个视觉对象布局映射，将每个视觉对象名称映射到视觉对象布局对象：

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>视觉对象布局

若要定义视觉对象布局，请传递新的位置和大小，以及新的可见性状态。

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`：定义视觉对象的新位置。
- `width`、height：定义视觉对象的新大小。
- `displayState`：定义视觉对象的可见性。

## <a name="update-layout"></a>更新布局

加载报表时，随时可以使用 updateSettings 方法更新报表布局。 请参阅[更新设置](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings)。

## <a name="code-example"></a>代码示例

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;

var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom
        customLayout: {
            pageSize: {
                type: models.PageSizeType.Custom,
                width: 1600,
                height: 1200
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};

// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');

// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);
```

## <a name="see-also"></a>另请参阅

[嵌入 Power BI 仪表板、报表和磁贴](embedding-content.md)   
[在 Power BI 社区提问](https://community.powerbi.com/)
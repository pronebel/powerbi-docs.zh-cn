---
title: 根据 R 脚本对 R 视觉对象创建漏斗图
description: 本文介绍如何根据 R 脚本对 R Power BI 视觉对象创建漏斗图。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: 42304e60740c215b1300e66f074807aea10ec6f9
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84317043"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>教程：根据 R 脚本对 R 视觉对象创建漏斗图
本文介绍如何使用 R 脚本对 R 视觉对象逐步创建漏斗图。

本文介绍如何执行以下操作：

> [!div class="checklist"]
>
> * 为 RStudio 创建 R 脚本
> * 在 Power BI 中创建 R 视觉对象
> * 在 Power BI 中创建基于 PNG 的 R 驱动视觉对象
> * 在 Power BI 中创建基于 HTML 的 R 驱动视觉对象

漏斗图提供了一种简单方法，用于使用、解释和显示预期的变化量。 漏斗使用置信度限制而形成，离群值显示为漏斗外的点。

在此示例中，漏斗图用于比较和分析各种数据集。  

> [!NOTE]
> 在每组步骤下均可下载源文件。

## <a name="build-an-r-script-with-dataset"></a>使用数据集生成 R 脚本

1. 下载[最小 R 脚本](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r)及其数据表 [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv)。

1. 接下来，编辑脚本以反映[此脚本](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r)。 这将添加输入错误处理和用户参数以控制绘图的外观。

## <a name="build-a-report"></a>生成报表

接下来，编辑脚本以反映[此脚本](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r)。 这会将 dataset.csv（而不是 read.csv）加载到 Power BI Desktop 工作区，并创建一个“癌症死亡率”表 。 请查看以下 [PBIX 文件](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix)中的结果。

> [!NOTE]
> `dataset` 是任何 R 视觉对象的输入 `data.frame` 的硬编码名称。 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>在 R 代码中创建 R 驱动的视觉对象和包

1. 开始之前，请务必[安装 PBIVIZ 工具](./custom-visual-develop-tutorial.md#installing-packages)。

1. 运行以下命令来创建新的 R 驱动视觉对象：

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   此命令通过初始模板视觉对象（模板的 `-t`）创建文件夹 funnel-visual。 PBIVIZ 位于 dist 文件夹中，R 代码位于 script.r 文件中 。 尝试将其导入 Power BI 并查看会发生什么。

1. 编辑 script.r 文件，并将内容替换为你之前的脚本。

1. 编辑 capabilities.json，并将字符串 `Values` 替换为 `dataset`。 这会将模板中的“角色”名称替换为类似于 R 代码中的名称。

   ![之前与之后](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. （可选）编辑 dependencies.json，并为 R 脚本所需的每个 R 包添加部分 。 这会告诉 Power BI 在首次加载视觉对象时自动导入这些包。

   ![之前与之后](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. 使用 `pbiviz package` 命令重新打包视觉对象，并尝试将其导入 Power BI。

> [!NOTE]
> 请参阅 [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3-RCustomVisual/funnelPlot_RCustomVisual.pbix) 和[源代码](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/)进行下载。

## <a name="make-r-based-visual-improvements"></a>进行基于 R 的视觉对象改进

视觉对象使用起来并不方便，因为用户必须要知道输入表中的列顺序。

1. 将输入字段 `dataset` 分为三个字段（角色）：`Population`、`Number` 和 `Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. 编辑 capabilities.json，并将 `dataset` 角色替换为这三个新角色，或下载 [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json)。

   需要更新 `dataRoles` 和 `dataViewMappings` 两个部分，它们定义每个输入字段的名称、类型、工具提示和最大列数。

   ![](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   有关详细信息，请参阅[功能](./capabilities.md)。

1. 编辑 script.r 以支持将 `Population`、`Number` 和 `Tooltips` 作为输入数据帧而不是 `dataset`，或下载 [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r)。

   ![](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > 要跟踪 R 脚本的更改，请搜索注释块： 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. 使用 `pbiviz package` 命令重新打包视觉对象，并尝试将其导入 Power BI。

> [!NOTE]
> 请参阅 [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) 和[源代码](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02)进行下载。

## <a name="add-user-parameters"></a>添加用户参数

1. 为用户添加功能，以控制视觉对象元素的颜色和大小，包括 UI 中的内部参数。

   ![CV02to03](./media/funnel-plot/diagram-two.PNG)

1. 编辑 capabilities.json 并更新 `objects` 部分。 在这里，我们定义每个参数的名称、工具提示和类型，并决定将参数划分为组（在本例中为三个组）。

   下载 [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json)；有关详细信息，请参阅[对象属性](./objects-properties.md)

   ![](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. 编辑 src/settings.ts 以反映[此 settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts)。 此文件采用 TypeScript 编写。  

   在这里，你将找到针对以下目的添加的两个代码块：
   - 声明新接口以保存属性值
   - 定义成员属性和默认值

   ![](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. 编辑 script.r 以反映[此 script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r)。 这会通过为每个用户参数添加 `if.exists` 调用来添加对 UI 中参数的支持。

   > [!TIP]
   > 要跟踪 R 脚本的更改，请搜索注释：
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   可以决定不向 UI 公开参数，就像我们一样。  

1. 使用 `pbiviz package` 命令重新打包视觉对象，并尝试将其导入 Power BI。

> [!NOTE]
> 请参阅 [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) 和[源代码](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/)进行下载。

> [!TIP]
> 在这里，我们同时添加了几种类型（布尔、数字、字符串和颜色）的参数。 对于简单情况，请参阅[本示例](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md)了解如何添加单个参数。 

## <a name="convert-visual-to-rhtml-based-visual"></a>将视觉对象转换为基于 RHTML 的视觉对象

生成的视觉对象基于 PNG，这种视觉对象无法对鼠标悬停进行响应并且无法执行放大等操作，因此我们需要将其转换为基于 HTML 的视觉对象。 我们将创建一个 R 驱动的基于 HTML 的空视觉对象模板，然后从基于 PNG 的项目中复制一些脚本。

1. 运行以下命令：

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. 打开 capabilities.json 并记下 `"scriptOutputType":"html"` 行。

1. 打开 dependencies.json 并记下列出的 R 包的名称。

1. 打开 script.r 并记下结构。 由于它不使用外部输入，因此可以在 RStudio 中打开并运行它。 

   这将创建并保存 out.html。 此文件是自包含文件（没有外部依赖项），并且定义 HTML 小组件中的图形。 

   > [!IMPORTANT]
   > 对于 `htmlWidgets` 用户，[r_files 文件夹](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files)中提供了 R 实用工具，以帮助将 `plotly` 或 `widget` 对象转换为自容式 HTML。 
   > 
   > 与以前的视觉对象类型不同，此版本的 R 驱动视觉对象还支持 `source` 命令，以提高代码的可读性。   
 
1. 将 capabilities.json 替换为上一步中的 capabilities.json，或下载 [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json) 。

   请务必：

   `"scriptOutputType": "html"`

1. 将最新版 script.r 与模板中的 script.r 进行合并，或下载 [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r) 。

   新脚本使用 `plotly` 包将 ggplot 对象转换为 plotly 对象，然后使用 `htmlWidgets` 包将其保存到 HTML 文件 。 

   大多数实用工具函数会移动到 [r_files/utils.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r)，并且添加了 `generateNiceTooltips` 函数以显示 plotly 对象。

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > 要跟踪 R 脚本的更改，请搜索注释：
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. 将最新版 dependencies.json 与模板中的 dependencies.json 进行合并以包含新的 R 包依赖项，或下载 [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json) 。

1. 按照之前步骤中的相同方式编辑 src/settings.ts。

1. 使用 `pbiviz package` 命令重新打包视觉对象，并尝试将其导入 Power BI。

> [!NOTE]
> 请参阅 [PBIX 和源代码](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01)进行下载。

## <a name="build-additional-examples"></a>生成其他示例

1. 请运行以下命令，创建一个空项目： 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. 采用此[展示](http://www.htmlwidgets.org/showcase_networkD3.html)中的代码，并进行突出显示的更改：

   ![突出显示的更改](./media/funnel-plot/diagram-three.PNG)

1. 替换模板的 script.r 并再次运行 `pbiviz package`。 现在，视觉对象已包含在 Power BI 报表中！

## <a name="tips-and-tricks"></a>提示和技巧

* 建议开发者编辑 pbiviz.json 以存储正确的元数据，例如版本、电子邮件、名称、许可证类型等等   。

   > [!IMPORTANT]
   > guid 字段是视觉对象的唯一标识符。 如果为每个视觉对象创建一个新项目，则 GUID 也将不同。 仅当使用复制到新视觉对象的旧项目（禁止这样做）时，它才会相同。

* 编辑 [assets/icon.png](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) 以便为视觉对象创建唯一图标。 

* 要使用与 Power BI 报表中相同的数据在 RStudio 调试 R 代码，请将以下内容添加到 R 脚本的开头（编辑 `fileRda` 变量）：

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   这会保存 Power BI 报表中的环境，并将其加载到 RStudio 中。 

* 无需使用 [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R) 上提供的代码从头开始开发 R 驱动的视觉对象。 可以选择要用作模板的视觉对象，并将代码复制到新项目中。

   例如，尝试使用[样条自定义视觉对象](https://github.com/Microsoft/PowerBI-visuals-spline)。

* 每个 R 视觉对象都会将 `unique` 运算符应用到其输入表。 要避免删除相同的行，请考虑添加具有唯一 ID 的额外输入字段，并在 R 代码中将其忽略。   

* 如果已有 Power BI 帐户，请使用 Power BI 服务[即时](/PowerBI-visuals/docs/step-by-step-lab/creating-a-custom-visual/#testing-the-custom-visual)开发视觉对象，而不是使用 `pbiviz package` 命令重新打包它们。

### <a name="html-widgets-gallery"></a>HTML 小组件库
浏览 [HTML 小组件库](http://gallery.htmlwidgets.org/)中的视觉对象，以便在下一个视觉对象中使用。 为方便起见，我们创建了一个[视觉对象项目存储库](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML)，其中有 20 多个交互式 HTML 视觉对象可供选择！

> [!TIP]
> 要在 HTML 小组件之间进行切换，请使用“格式” > “设置” > “类型”  。 通过[此 PBIX 文件](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix)进行试用。 

#### <a name="to-use-a-sample-for-your-visual"></a>将示例用于你的视觉对象

1. 下载整个文件夹。
1. 编辑 script.r 和 dependencies.json 以仅保留一个小组件 。
1. 编辑 capabilities.json 和 settings.ts 以删除 `Type` 选择器 。
1. 将 visual.ts 中的 `const updateHTMLHead: boolean = true;` 更改为 `false`。 （以提高性能）
1. 更改 pbiviz.json 中的元数据，最重要的是 `guid` 字段。
1. 重新打包并继续根据需要自定义视觉对象。 

![CV02to03](./media/funnel-plot/diagram-four.PNG)

![CV02to03](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> 服务并不支持此项目中的所有小部件。

## <a name="next-steps"></a>后续步骤

要了解详细信息，请参阅有关 [Power BI 视觉对象](./custom-visual-develop-tutorial.md)和 [R 视觉对象](/power-bi/visuals/service-r-visuals)的其他教程。

了解如何[开发视觉对象并将其提交](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/)到 [Office 应用商店（库）](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI)；有关进一步示例，请参阅 [R 脚本展示](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)

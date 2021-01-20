---
title: 智能叙述教程
description: 教程：在 Power BI 中创建智能叙述摘要可视化效果
author: aphilip94
ms.author: anphil
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 11/06/2020
ms.custom: video-01UrT-z37sw
LocalizationGroup: Visualizations
ms.openlocfilehash: 43b2e9c33bf420c7446aa2eb198048101704a1ba
ms.sourcegitcommit: 396633fc5f7cff1f7d518f558b20043b2e05a513
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98191926"
---
# <a name="create-smart-narrative-summaries-preview"></a>创建智能叙述摘要（预览版）

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

智能叙述可视化效果有助于快速汇总视觉对象和报表。 它提供了可自定义的相关创新性见解。

![在报表右侧显示智能叙述摘要的屏幕截图。](media/power-bi-visualization-smart-narratives/1.png)

在报表中使用智能叙述摘要来处理关键问题、指出趋势，并为特定受众编辑语言和格式。 在 PowerPoint 中，可以添加每次刷新时更新的叙述，而不是粘贴报表要点的屏幕截图。 受众可以使用摘要来了解数据，更快地进入要点，并向其他人解释这些数据。

>[!NOTE]
> 由于智能叙述功能处于预览阶段，因此，如果要使用该功能，必须将其启用。 在 Power BI 中，转至“文件” > “选项和设置” > “选项” > “预览功能”。 然后，选择“智能叙述视觉对象”。
>
>![显示 Power BI 选项的屏幕截图。 已选中“智能叙述视觉对象”选项。](media/power-bi-visualization-smart-narratives/2.png)



## <a name="get-started"></a>入门 
观看 Justyna 演示如何使用智能叙述，然后使用视频下方的教程亲自尝试。  若要按照本教程进行操作，请下载联机销售方案的[示例文件](https://github.com/microsoft/powerbi-desktop-samples/blob/main/Monthly%20Desktop%20Blog%20Samples/2020/2020SU09%20Blog%20Demo%20-%20September.pbix)。

<iframe width="560" height="315" src="https://www.youtube.com/embed/01UrT-z37sw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

选择“可视化效果”窗格中的“智能叙述”图标以自动生成摘要。

![显示“可视化效果”窗格的屏幕截图。 已选中“智能叙述”图标。](media/power-bi-visualization-smart-narratives/3.png)

你将看到基于页面上所有视觉对象的叙述。 例如，在示例文件中，智能叙述可以自动生成报表视觉对象的摘要，其中包括收入、网站访问次数和销售情况。 Power BI 会自动分析趋势，显示收入和访问次数都在增长。 它甚至计算出增长率，在本例中为 72%。
 
![显示如何创建智能叙述摘要的屏幕截图。](media/power-bi-visualization-smart-narratives/4.gif)
 
若要生成可视化效果的智能叙述，请右键单击该可视化效果，然后选择“汇总”。 例如，在示例文件中，尝试汇总显示各种交易的散点图。 Power BI 分析数据，并显示哪个城市或地区的每笔交易收入最高、交易数量最多。 智能叙述还显示这些指标的预期值范围。 可以看到，大多数城市每笔交易的收入都低于 45 美元，且交易量低于 10 笔。
 
  
![显示汇总散点图的智能叙述的屏幕截图。](media/power-bi-visualization-smart-narratives/5.gif)
 
## <a name="edit-the-summary"></a>编辑摘要
 
智能叙述摘要可高度自定义。 可以使用文本框命令进行编辑或添加到现有文本。 例如，可以将文本设置为粗体或更改文本颜色。
 
![显示工具栏上的文本格式命令的屏幕截图。](media/power-bi-visualization-smart-narratives/6.png)
  
要自定义摘要或添加自己的见解，请使用动态值。 可以将文本映射到现有字段和度量值，也可以使用自然语言定义要映射到文本的新度量值。 例如，若要在示例文件中添加有关返回项的数目的信息，请添加一个值。 

键入值名称时，可以从建议列表中进行选择，这与在问答视觉对象中执行的操作相同。 因此，除了在问答视觉对象中询问数据问题之外，现在还可以创建自己的计算，甚至无需使用数据分析表达式 (DAX)。 
  
![显示如何为智能叙述可视化效果创建动态值的屏幕截图。](media/power-bi-visualization-smart-narratives/7.gif)
  
还可以设置动态值的格式。 例如，在示例文件中，可将值显示为货币，指定小数点位置，以及选择千位分隔符。 
   
![显示如何设置动态值格式的屏幕截图。](media/power-bi-visualization-smart-narratives/8.gif)
   
若要设置动态值的格式，请选择摘要中的值，以在“查看”选项卡上查看编辑选项。或在文本框中，选择要编辑的值旁边的“编辑”按钮。 
   
![显示已选中“值”选项卡的文本框的屏幕截图。 在值名称旁，突出显示“编辑”按钮。](media/power-bi-visualization-smart-narratives/9.png)
   
还可以使用“查看”选项卡来查看、删除或重用以前定义的值。 选择加号 (+) 将值插入到摘要中。 还可以打开“查看”选项卡底部的选项，以显示自动生成的值。

有时，隐藏摘要符号会出现在智能叙述中。 它指示当前数据和筛选器不生成值的结果。 如果没有可用的见解，则摘要为空。 例如，在示例文件的折线图中，如果该图中的线为直线，则高值和低值的摘要可能为空。 但摘要可能会在其他情况下出现。 隐藏摘要符号仅在你尝试编辑摘要时可见。


![在某个智能叙述摘要内显示两个隐藏摘要符号的屏幕截图。](media/power-bi-visualization-smart-narratives/10.png)
   
## <a name="visual-interactions"></a>视觉对象交互
摘要是动态的。 当交叉筛选时，会自动更新生成的文本和动态值。 例如，如果在示例文件的环形图中选择电子产品，则报表的其余部分将交叉筛选，并且摘要也将交叉筛选，以便将焦点设置在电子产品上。  

在这种情况下，访问次数和收入具有不同的趋势，因此，摘要文本会进行更新以反映趋势。 添加的返回值的计数将更新为 $4196。 当交叉筛选时，可以更新空摘要。
   
![显示图表中的所选内容如何交叉筛选摘要的屏幕截图。](media/power-bi-visualization-smart-narratives/11.gif)
   
还可以执行更高级的筛选。 例如，在示例文件中，查看多个产品趋势的视觉对象。 如果只对特定季度的趋势感兴趣，请选择相关的数据点来更新该趋势的摘要。
   
![显示如何通过选择趋势线筛选摘要以仅显示该趋势的屏幕截图。](media/power-bi-visualization-smart-narratives/12.gif)
   
## <a name="limitations"></a>限制

智能叙述功能不支持以下功能：
- 固定到仪表板 
- 使用动态值和条件格式（例如，数据绑定标题）
- Azure Analysis Services，本地 AS
- KPI、卡片、多行卡片、映射、表、矩阵、R 视觉对象或 Python 视觉对象、自定义视觉对象 
- 对具有按其他列进行分组的列以及基于“数据组”字段的列的视觉对象进行汇总 
- 从视觉对象交叉筛选
- 重命名动态值或编辑自动生成的动态值
- 对包含动态计算（如 QnA 算法和总计百分比）的视觉对象进行汇总 
- [计算组](/analysis-services/tabular-models/calculation-groups)
   


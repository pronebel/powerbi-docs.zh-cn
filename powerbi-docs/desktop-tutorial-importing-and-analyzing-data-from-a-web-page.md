---
title: 教程：导入和分析网页中的数据
description: 教程：使用 Power BI Desktop 从网页导入和分析数据
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 7d4aaa613ac2d79a08ed6bbc03ba47dd296942de
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2020
ms.locfileid: "75759580"
---
# <a name="tutorial-analyze-webpage-data-by-using-power-bi-desktop"></a>教程：使用 Power BI Desktop 分析网页数据

作为资深球迷，你想要获得多年来欧足联欧洲锦标赛（欧洲杯）获胜队的报导。 使用 Power BI Desktop，可以将此数据从网页导入到报表，并创建显示数据的可视化效果。 在本教程中，将学习如何使用 Power BI Desktop 完成以下操作：

- 连接到 Web 数据源并在其可用表之间导航，
- 调整并转换 Power Query 编辑器  中的数据，
- 命名查询并将其导入 Power BI Desktop 报表，并且 
- 创建和自定义地图和饼图可视化效果。

## <a name="connect-to-a-web-data-source"></a>连接到 Web 数据源

你可以从 https://en.wikipedia.org/wiki/UEFA_European_Football_Championship 处的欧足联欧洲锦标赛维基百科页面上的结果表中获得欧足联获胜队的数据。 

![维基百科结果表](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

请注意：仅使用基本身份验证建立 Web 连接。 需要身份验证的网站可能无法正常使用 Web 连接器。

若要导入数据，请执行下列操作：

1. 在 Power BI Desktop“主页”  功能区选项卡中，下拉“获取数据”旁边的箭头  ，然后选择“Web”  。
   
   ![从功能区获取数据](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 
   
   >[!NOTE]
   >你还可以选择“获取数据”  项本身，或者从 Power BI“开始”对话框中选择“获取数据”   ，再从“获取数据”对话框的“所有”或“其他”部分中选择“Web”     ，然后选择“连接”  。
   
2. 在“从 Web”  对话框中，将 URL `https://en.wikipedia.org/wiki/UEFA_European_Football_Championship` 粘贴到“URL”  文本框，然后选择“确定”  。
   
    ![从对话框获取数据](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)
   
   在连接到维基百科网页后，Power BI“导航器”  对话框会在页面上显示可用表的列表。 可以选择任意表名称以预览其数据。 “结果[编辑]”  表具有所需的数据，尽管它不完全是你希望的外观。 你可以先重新修整并清理数据，然后再将其加载到报表中。 
   
   ![导航器对话框](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)
   
   >[!NOTE]
   >“预览”窗格只显示最近选择的表，但当选择“编辑”或“加载”时，所有被选中的表都会加载到**Power Query 编辑器**中。    
   
3. 字段自动更改为“年份计数”度量值，地图可视化效果现在针对锦标赛获胜次数较多的国家/地区会显示较大数据点。    
   
   表的预览将在“Power Query 编辑器”中打开  ，你可以在其中应用转换以清理数据。 
   
   ![Power Query 编辑器](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)
   
## <a name="shape-data-in-power-query-editor"></a>在 Power Query 编辑器中修整数据

你希望通过仅显示年份和获胜的国家/地区，使数据更易于扫描。 你可以使用“Power Query 编辑器”  执行这些数据修整和清理步骤。

首先，从表中删除除“年份”  和“最终获胜队”  之外的所有列。

1. 在“Power 查询编辑器”  网格中，选择“年份”  和“最终获胜队”  列（按住 Ctrl  键以选择多个项）。
   
2. 右键单击并从下拉列表中选择“删除其他列”  ，或者从“主页”功能区选项卡中的“管理列”组选择“删除列”   > “删除其他列”    ，以从表中删除所有其他列。 
   
   ![删除其他列下拉列表](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png) 或 ![删除其他列功能区](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

接下来，从“年份”列单元格中删除额外的词“详细信息”   。

1. 选择 **Year** 列。
   
2. 右键单击，然后从下拉列表中选择“替换值”  ，或者从功能区的“主页”选项卡中的“转换”组中选择“替换值”    （该选项还位于“转换”选项卡中的“任何列”组中   ）。 
   
   ![替换值下拉列表](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) 或 ![替换值功能区](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)
   
3. 在“替换值”对话框中，在“要查找的值”文本框中键入“详细信息”，“替换为”文本框保持为空，然后选择“确定”从“年份”条目中删除“详细信息”一词。      
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

某些“年份”  单元格仅包含单词“年份”而不是年份值。 你可以筛选“年份”  列以仅显示不包含“年份”一词的行。 

1. 在“年份”列上选择筛选器下拉箭头  。
   
2. 在下拉列表中向下滚动，清除“年份”选项旁的复选框，然后选择“确定”，以删除“年份”列中仅具有“年份”一词的行。    

   ![筛选数据](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

完成清理“年份”列中的数据后，可以开始处理“最终获胜队”列。   因为你现在只查看最终获胜队数据，可以将此列重命名“国家/地区”。  若要重命名列，请执行下列操作：

1. 双击或点击并按住“最终获胜队”  列标题，或者 
   - 右键单击“最终获胜队”  列标题，然后从下拉列表中选择“重命名”  ，或者 
   - 选择“最终获胜队”  列，从功能区的“转换”选项卡中的“任何列”组中选择“重命名”    。 
   
   ![重命名下拉列表](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) 或 ![重命名功能区](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)
   
2. 在标题中键入“国家/地区”  ，然后按 Enter  重命名列。

你还想在“国家/地区”列中过滤掉类似“2020”这样包含 null 值的行。  你可以像处理“年份”  值那样使用筛选器菜单，也可以：

1. 在具有 null 值的“2020”行中右键单击“国家/地区”  单元格   。 
2. 在上下文菜单中选择“文本筛选器”   > “不等于”  以删除任何包含该单元格的值的行。
   
   ![文本筛选器](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)
   
## <a name="import-the-query-into-report-view"></a>将查询导入报表视图

既然已按所需的方式修整数据，你可以准备命名查询“欧洲杯获胜队”并将其导入报表。

1. 在“查询设置”  窗格的“名称”  文字框中，输入“欧洲杯获胜队”  ，然后按“Enter”  。
   
   ![命名查询](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

2. 从功能区的“主页”选项卡选择“关闭并应用”   > “关闭并应用”   。
   
   ![关闭并应用](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)
   
查询将加载到 Power BI Desktop 报表视图  ，你可以在“字段”  窗格中看到该查询。 
   
   ![字段窗格](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)
>[!TIP]
>通过以下方法，你可以随时返回到“Power Query 编辑器”以编辑并优化查询： 
>- 在“字段”窗格中选择“欧洲杯获胜队”旁的“更多选项”  省略号 (...  )   ，并从下拉列表中选择**编辑查询**，或者
>- 在报表视图中“主页”功能区选项卡的“外部数据”组中，选择“编辑查询”   > “编辑查询”    。 

## <a name="create-a-visualization"></a>创建可视化效果

若要基于数据创建可视化效果，请执行下列操作： 

1. 在“字段”窗格中选择“国家/地区”字段   ，或者将其拖到报表画布。 Power BI Desktop 会将数据识别为国家/地区名称，并自动创建“地图”  可视化效果。 
   
   ![地图可视化效果](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)
   
2. 通过拖动角部图柄放大地图，以使所有获胜的国家/地区名称可见。  

   ![放大地图](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)
   
3. 地图针对每个欧洲杯锦标赛获胜国家/地区显示相同的数据点。 若要使每个数据点的大小反映国家/地区的获胜频率，将“年份”字段拖动到“可视化效果”  窗格下半部分“大小”下的“将数据字段拖至此处”    。 字段自动更改为“年份计数”  度量值，地图可视化效果现在针对锦标赛获胜次数较多的国家/地区显示较大数据点。 
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)
   

## <a name="customize-the-visualization"></a>自定义可视化效果

如你所见，基于数据创建可视化效果相当容易。 还可以很方便地自定义可视化效果以更好地按所需方式呈现数据。 

### <a name="format-the-map"></a>设置地图格式
可以更改可视化效果的外观，方法是在“可视化效果”窗格中选中它，然后选择“格式”（绘制滚刷）图标。   例如，可视化效果中的“德国”数据点具有误导性，因为西德获胜两次锦标赛而德国获胜一次，地图重叠显示了这两个点而不是将它们分隔或一起添加。 你可以分别为这两个点添加颜色，以突出显示它们。 你还可以为地图提供一个更具描述性和吸引力的标题。 

1. 选择可视化效果后，选择“格式”  图标，然后选择“数据颜色”  以展开数据颜色选项。 
   
   ![设置数据颜色的格式](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)
   
2. 将“全部显示”  设为“开启”  ，选择“西德”旁的下拉列表  ，然后选择黄色。 
   
   ![更改颜色](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)
   
3. 选择“标题”  以展开标题选项，在“标题文本”  字段中，键入“欧洲杯获胜队”  以替代当前标题。 
4. 将“字体颜色”  更改为红色，将“文本大小”  更改为 12，将“字体系列”  更改为“Segoe (Bold)”   。 
   
   ![设置数据颜色的格式](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)
   

现在你的地图可视化效果类似如下所示：

![已设置格式的地图可视化效果](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)
   
### <a name="change-the-visualization-type"></a>更改可视化效果类型
你可以更改可视化效果类型，方法是选中它，然后选择“可视化效果”窗格顶部的其他图标  。 例如，地图可视化效果缺少苏联和捷克斯洛伐克数据，因为这些国家/地区在世界地图上不再存在。 另一种类似于树状图或饼图的可视化效果可能更加准确，因为它显示了所有值。 

若要将地图更改为饼图，选择地图，然后选择“可视化效果”窗格中的“饼图”  图标  。 
   
![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- 可以使用“数据颜色”  格式设置选项将“德国”和“西德”设为相同的颜色。 
>- 若要在饼图上将获胜次数多的国家/地区分组在一起，请选择可视化效果右上方的省略号 (...  )，然后从下拉列表中选择“按年份计数排序”  。 

Power BI Desktop 提供无缝的端到端体验（从各种数据源获取数据、调整数据以满足你的分析需求，再到以丰富的交互方式可视化这些数据）。 在报表准备就绪后，您可以[将其上载到 Power BI](desktop-upload-desktop-files.md) 并基于它创建仪表板与其他 Power BI 用户共享。

## <a name="see-also"></a>另请参阅
* [阅读其他 Power BI Desktop 教程](https://go.microsoft.com/fwlink/?LinkID=521937)
* [观看 Power BI Desktop 视频](https://go.microsoft.com/fwlink/?LinkID=519322)
* [访问 Power BI 论坛](https://go.microsoft.com/fwlink/?LinkID=519326)
* [阅读 Power BI 博客](https://go.microsoft.com/fwlink/?LinkID=519327)


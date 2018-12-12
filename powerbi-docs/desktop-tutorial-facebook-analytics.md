---
title: 教程︰使用 Power BI Desktop 进行 Facebook 分析
description: 教程︰使用 Power BI Desktop 进行 Facebook 分析
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: ec90e63de1e42350ff205febdc66abf4ba6ee626
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578488"
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>教程：使用 Power BI Desktop 的 Facebook 分析

在本教程中，你将学习如何导入来自 Facebook 的数据并在 Power BI Desktop 中使用该数据。 将从 Power BI Facebook 页面连接和导入数据，将转换应用于导入的数据，并在报表可视化效果中使用数据。

## <a name="connect-to-a-facebook-page"></a>连接到 Facebook 页面

本教程使用 [Microsoft Power BI Facebook 页面](https://www.facebook.com/microsoftbi)(https://www.facebook.com/microsoftbi) 中的数据。 除了个人 Facebook 帐户之外，不需要任何特殊凭据从该页面连接和导入数据。

1. 打开 Power BI Desktop，然后选择“开始使用”对话框中的“获取数据”，或者在“主页”功能区选项卡中，依次选择“获取数据”和“更多...”。
   
2. 在“获取数据”对话框中，从“联机服务”组中选择“Facebook”，然后选择“连接”。
   
   ![获取数据](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   随即出现一个对话框，提醒你如果使用第三方服务，将产生风险。
   
   ![第三方警告](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. 选择“继续”。 “Facebook”对话框随即出现。
   
4. 将页名称“microsoftbi”键入或粘贴到“用户名”文本框，从“连接”下拉列表选择“帖子”，然后选择“确定”。
   
   ![连接](media/desktop-tutorial-facebook-analytics/2.png)
   
5. 在系统提示输入凭据时，请登录到 Facebook 帐户，并允许通过 Power BI 访问该账户。
   
   ![凭据](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   连接到 Power BI Facebook 页面后，将看到页面“帖子”数据的预览。 
   
   ![数据预览](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>调整和转换导入的数据

你想要查看并显示一段时间内哪些帖子的评论数量最多，但注意到在“帖子”数据预览中，“created_time”数据难以读懂和理解，并且根本没有评论数据。 需要对数据进行一些调整和清理操作，以最大限度地利用这些数据。 在将数据导入 Power BI Desktop 之前/之后，可以使用 Power BI Desktop“Power Query 编辑器”编辑数据。 

### <a name="split-the-datetime-column"></a>拆分“日期/时间”列

首先，拆分“created_time”列中的日期和时间值，使其更易于识读。 

1. 在 Facebook 数据预览中，选择“编辑”。 
   
   ![数据预览编辑](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   Power BI Desktop“Power Query 编辑器”会在新窗口中打开，并显示来自 Power BI Facebook 页面的数据预览。 
   
   ![Power Query 编辑器](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. 选择“created_time”列。 注意，从列标题中的“ABC”图标指示可知，它当前为“文本”数据类型。 右键单击标题，然后选择下拉列表中的“拆分列”>“按分隔符”，或者选择功能区“主页”选项卡中“转换”下的“拆分列”>“按分隔符”。  
   
   ![按分隔符拆分列](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. 在“按分隔符拆分列”对话框中，从下拉列表中选择“自定义”，在输入字段中输入“T”（用于启动 created_time 值的时间部分的字符），并选择“确定”。 
   
   ![“按分隔符拆分列”对话框](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   列将拆分为包含“T”分隔符之前和之后的字符串的两个列，名称分别为“created_time.1”和“created_time.2”。 请注意，Power BI 会自动进行检测，并将第一列的数据类型更改为“日期”，将第二列的数据类型更改为“时间”，并设置日期和时间值格式，使其更易于识读。
   
4. 若要重命名列，可以双击每个列标题，或选中每个列，然后选择功能区“转换”选项卡“任何列”组中的“重命名”，并分别键入新的列标题“created_date”和“created_time”。
   
   ![新日期和时间列](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>展开嵌套列

现在日期和时间数据以你期望的形式显示，接下来将通过展开嵌套列来显示评论数据。 

1. 选择“object_link”列，然后选择![展开图标](media/desktop-tutorial-facebook-analytics/14.png)图标以打开“展开/聚合”对话框。 选择“连接”，然后选择“确定”。 
   
   ![展开 object_link](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   列标题将更改为“object_link.connections”。
2. 再次选择“object_link.connections”列顶部的![展开图标](media/desktop-tutorial-facebook-analytics/14.png)图标，选择“评论”，然后选择“确定”。 列标题将更改为“object_link.connections.comments”。
   
3. 选择“object_link.connections.comments”列顶部的![展开图标](media/desktop-tutorial-facebook-analytics/14.png)图标，这次选择对话框中的“聚合”而不是“展开”。 选择“# ID 计数”，然后选择“确定”。 
   
   ![聚合评论](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   列现在显示每个消息的评论数。 
   
4. 将“object_link.connections.comments.id 计数”列重命名为“评论数”。
   
5. 选择“评论数”标题旁的向下箭头，然后选择“降序排序”，按照评论数最多到最少的顺序查看帖子。  
   
   ![每个消息的评论](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>查看查询步骤

在“Power Query 编辑器”中调整和转换数据后，每个步骤都已记录到“Power Query 编辑器”窗口右侧“查询设置”窗格的“应用的步骤”区域。 可以通过“应用的步骤”返回以查看所做的具体更改，并视需要编辑、删除或重新排列它们（尽管这样做可能存在风险，因为更改前面的步骤可能会中断后续步骤）。 

在应用数据转换之后，“应用的步骤”应如下所示：
   
   ![应用的步骤](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >基本的“应用的步骤”是以 Power Query 语言编写的公式，也称为 M 语言。 若要查看和编辑该公式，请选择功能区“主页”选项卡“查询”组中的“高级编辑器”。 

### <a name="import-the-transformed-data"></a>导入转换后的数据

如果对数据感到满意，请选择功能区“主页”选项卡中的“关闭并应用” > “关闭并应用”，将其导入 Power BI Desktop 中。 
   
   ![关闭并应用](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   将看到一个对话框，显示向 Power BI Desktop 数据模型加载数据的进度。 
   
   ![正在加载数据](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   数据加载完成后，它会在“报表”视图中显示为“字段”列表中的新“查询”。
   
   ![新建查询](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>在报表可视化效果中使用数据 

现在，已从 Facebook 页面导入数据，可以使用可视化效果快速轻松地深入了解数据。 创建可视化效果的操作很简单；只需选择一个字段或将其从“字段”列拖动到报表画布。

### <a name="create-a-bar-chart"></a>创建条形图

1. 在“Power BI Desktop 报表”视图中，从“字段”列表中选择“消息”，或将其拖至画布。 显示所有帖子消息的表格将显示在画布上。 
   
   ![新建查询](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. 在选中该表格后，从“字段”列表选择“评论数”，或将其拖动到表格中。 
   
3. 在“可视化效果”窗格中，选择“堆积条形图”图标。 表格将更改为条形图，显示每个帖子的评论数量。 
   
   ![条形图](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. 在“可视化效果”的右上方，选择省略号 (...)，然后选择“按评论数排序”，按降序排列评论数对表格进行排序。 
   
   ![按评论数排序](media/desktop-tutorial-facebook-analytics/barchart2.png)
   
5. 请注意，大多数评论与“空白”消息相关联（这些帖子可能包含应用场景、链接、视频或其他非文本内容）。 若要过滤掉“空白”行，请选择“可视化效果”窗格底部“筛选器”下的“消息(全部)”，选择“全选”，然后选择“空白”以取消此选项的选中状态。 “筛选器”条目将更改为“消息不为(空白)”，且“空白”行会从图表可视化效果中消失。 
   
   ![筛选出空白](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>设置图表格式

可视化效果变得更加有趣，但无法查看图表中的大部分帖子文本。 若要显示更多帖子文本，请执行以下操作：

1. 在图表可视化效果上使用句柄，尽量将图表大小调整为最大。 
   
2. 选中图表后，在“可视化效果”窗格中选择“格式”图标（油漆滚筒）。
   
3. 选择“Y 轴”旁边的向下箭头，然后将“最大大小”旁的滑块拖动到最右边 (50%)。 
4. 另外，将“文本大小”减小到“10”以适应更多文本内容。
   
   ![格式设置更改](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   图表现在可以显示更多帖子内容。 
   
   ![显示更多帖子](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
图表的 X 轴（评论数）不显示确切值，并且看起来在图表底部不存在。 可以改用数据标签显示评论数，操作如下： 

1. 选择“格式”图标，然后选择“X 轴”旁边的滑块将其“关闭”。 
   
2. 选择“数据标签”旁边的滑块以将其“打开”。 现在图表可以显示每个帖子的确切评论数。
   
   ![应用数据标签](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>编辑数据类型

这样效果更好，但所有数据标签都有一个“.0”小数位数，这会分散人的注意力并具有误导性，因为“帖子数”肯定是整数。 需要将“帖子数”列的数据类型更改为“整数”。

1. 要编辑数据类型，右键单击“字段”列表中的“Query1”，或将鼠标悬停在上面，选择“更多选项”省略号 (...)，然后选择“编辑查询”。 另外，还可以从功能区“主页”选项卡的“外部数据”区域选择“编辑查询”，然后从下拉列表选择“编辑查询”。 Power BI Desktop“Power Query 编辑器”在单独窗口中打开。
   
   ![从“字段”列表编辑查询](media/desktop-tutorial-facebook-analytics/editquery1.png)     ![从功能区编辑查询](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)
   
2. 在“Power Query 编辑器”中，选择“评论数”列，并通过以下任一方法将数据类型更改为“整数”： 
   - 选择“评论数”列标题旁边的“1.2”图标，并从下拉列表中选择“整数”，或
   - 右键单击列标题，然后选择“更改类型”>“整数”，或
   - 选择“主页”选项卡“转换”组中的“数据类型: 小数”，或选择”转换”选项卡的”任意列“组，然后选择”整数“。
   
   列标题中的图标更改为“123”，表示“整数”数据类型。
   
   ![更改数据类型](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. 选择“关闭并应用”，或只选择“应用”以应用更改，同时使“Power Query 编辑器”窗口保持打开状态。 加载更改内容后，图表上的数据标签将变为整数。 
   
   ![包含整数的图表](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>创建日期切片器

你想要可视化呈现一段时间内帖子的评论数。 可以创建切片器可视化工具，对图表数据的不同时间范围进行筛选 

1. 单击画布的空白区域，然后选择“可视化效果”窗格中的“切片器”图标。 将显示一个空白的切片器可视化效果。 
   
   ![选择切片器图标](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. 从“字段”列表选择“created_date”字段，或将其拖动到新的切片器。 切片器根据字段的“日期”数据类型，更改为一个日期范围滑块。
   
   ![日期范围滑块切片器](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. 移动滑块图柄以选择不同的日期范围，并注意图表数据是如何相应进行筛选的。 还可以选择切片器中的“日期”字段，并键入特定日期，或者从日历弹出框中选择日期。
    
   ![切分数据](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>设置可视化效果的格式

你决定为图表提供一个更具描述性和吸引力的标题。 

1. 选中图表后，选择“格式”图标，然后选择下拉箭头以展开“标题”。
2. 将“标题文本”更改为“每个帖子的评论”。 
3. 选择“字体颜色”旁边的下拉箭头，然后选择绿色以匹配可视化效果的绿色栏。
4. 将“文本大小”增加到“10”，并将“字体系列”更改为“Segoe (Bold)”。

![设置图表标题格式](media/desktop-tutorial-facebook-analytics/formatting1.png)

尝试使用其他格式设置选项和设置来改变可视化效果的外观。 

![可视化](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>创建更多可视化效果

如你所见，可以方便地在报表中自定义可视化效果以便按所需的方式呈现数据。 例如，尝试使用导入的 Facebook 数据来创建此折线图，显示一段时间内的评论数量。

![折线图](media/desktop-tutorial-facebook-analytics/moreviz.png)

Power BI Desktop 提供无缝的端到端体验（从各种数据源获取数据、调整数据以满足你的分析需求，再到以丰富的交互方式可视化这些数据）。 在报表准备就绪后，可以[将报表上传到 Power BI 服务](desktop-upload-desktop-files.md)，并基于它创建仪表板与其他 Power BI 用户共享。

## <a name="next-steps"></a>后续步骤
* [阅读其他 Power BI Desktop 教程](http://go.microsoft.com/fwlink/?LinkID=521937)
* [观看 Power BI Desktop 视频](http://go.microsoft.com/fwlink/?LinkID=519322)
* [访问 Power BI 论坛](http://go.microsoft.com/fwlink/?LinkID=519326)
* [阅读 Power BI 博客](http://go.microsoft.com/fwlink/?LinkID=519327)


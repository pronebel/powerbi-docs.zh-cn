---
title: 在 Power BI 中创建报表的相关提示和技巧
description: 了解在 Power BI 服务和 Power BI Desktop 中生成报表的最佳做法
author: davidiseminger
ms.reviewer: willthom
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/07/2020
ms.author: davidi
ms.openlocfilehash: ae9a3695c8db084d9c65871314edfef34cde1cb6
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238488"
---
# <a name="tips-and-tricks-for-creating-reports-in-power-bi-desktop"></a>在 Power BI Desktop 创建报表的相关提示和技巧
若要充分利用你的数据，有时你还需要一点帮助。 我们整理了一些提示和技巧，以便你在 Microsoft Power BI Desktop *及*启用了 Power Pivot 加载项且安装和启用了 Power Query 的 Microsoft Excel 2016 或 Excel 2013 Pro-Plus 版本中创建报表时可加以使用。 

## <a name="learning-to-use-the-query-editor"></a>了解如何使用查询编辑器
Power BI Desktop 中的查询编辑器与 Excel 2013 中的 Power Query 加载项功能很相似。 虽然 Power BI 支持中提供了多篇有用的文章，但你可能还想在 support.office.com 上查看可帮助入门的 Power Query 文档。

有关其他信息，请参阅 [Power Query Resource Center](https://support.office.com/article/Microsoft-Power-Query-for-Excel-Help-2b433a85-ddfb-420b-9cda-fe0e60b82a94)（Power Query 资源中心）。

还可查看 [Formula Reference](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f)（公式引用）。

## <a name="data-types-in-query-editor"></a>查询编辑器中的数据类型
在 Power BI Desktop 中使用查询编辑器加载数据时，可以最佳估计的形式监测数据类型。 使用公式时，有时不会保留列上的数据类型设置。 在执行下述操作后，确保列的数据类型正确：将数据初次加载到查询选项卡、第一行用作标题、添加列、按条件分组、合并、追加，以及按住前首次加载数据。

要记住一个关键点是：数据网格中的斜体不表示数据类型设置正确，它仅表示数据不被视为“文本”。

## <a name="reference-queries-in-the-query-editor"></a>引用查询编辑器中的查询
在 Power BI Desktop 的查询编辑器浏览器中，右键单击某个查询时，会显示“引用”选项。 由于下述原因，此选项非常有用：

* 将文件用作查询的数据源时，指向文件的绝对路径存储在查询中。 在分享或移动 Power BI Desktop 文件或 Excel workbook 时，可通过仅更新一次来更新路径，从而节省时间。

默认情况下，所有查询都将加载到数据模型。 某些查询是中间步骤，不用于最终用户。 按上述所提方式引用查询时，通常是这种情况。 可右键单击浏览器中的查询并切换“启用加载”选项，从而控制查询加载行为。 如果“启用加载”旁边没有勾号，则查询仍可用于查询选项卡且可与其他查询一同使用。 在与“合并”、“追加”和“引用”转换配合使用时，此功能尤其有用。 但由于查询结果未加载到数据模型，此查询将不会打乱报表字段列表或数据模型。 

## <a name="scatter-charts-need-a-point-identifier"></a>散点图需要点标识符
举个例子，一个简单的表上记录了天气和进行读取的时间。 如果将其直接绘制在散点图上，Power BI 会将所有值都聚合为一个点。 若要显示单独的数据点，必须在字段框的“详细信息”Bucket 中添加一个字段。 在 Power BI Desktop 中执行此操作的一种简单方法是在“查询”选项卡上，使用“添加列”功能区中的“添加索引列”选项。 

## <a name="reference-lines-in-your-report"></a>报表中的参考线
可使用 Power BI Desktop 中的计算列来定义参考线。 确定你要在其上创建参考线的表格和列。 在功能区中选择“新建列”，然后在公式栏中键入以下公式：

    Target Value = 100

无论在何处使用，此计算列都将返回值 100。 新列将在字段列表中显示。 将“目标值”计算列添加到折线图，以显示任意时序如何与此特定参考线相关联。 

## <a name="sort-by-another-column"></a>按其他列排序
在 Power BI 中将类别（字符串）值用于图表轴或在切片器/筛选器中使用时，默认顺序是按字母顺序。 如果需要替代此顺序（例如针对每周天数或每月天数等项目），则可指示 Power BI Desktop 按其他列进行排序。 若要了解详细信息，请参阅[在 Power BI Desktop 中按列排序](desktop-sort-by-column.md)。

## <a name="building-maps-more-easily-with-hints-to-bing"></a>利用到必应的提示，更轻松地绘制地图
Power BI 与必应相集成，提供默认地图坐标（一个称为地理编码的过程），从而可更轻松地创建地图。 必应使用一些算法和提示来尝试获得正确位置，但这只是最佳估计。 若要增加地理编码正确的可能性，可使用以下提示：

在创建地图时，通常会希望绘制国家/地区、州和城市。 在 Power BI Desktop 中，如果在地理名称后面命名列，它将有助于必应猜测你所希望显示的内容。 例如，如果某个字段具有美国州名（如“加利福利亚”和“华盛顿”），则对于“华盛顿”这个词，必应可能会返回华盛顿特区（而不是华盛顿州）的位置。 将列命名为“州”将提升地理编码的功能。 对于名为“国家/地区”和“城市”的列也是如此。 

在多个国家/地区这一上下文中考虑时，某些名称会引起歧义。 某些情况下，某个国家/地区会将“州”视为“省”、“县”或一些其他名称。 通过构建将多个字段追加在一起的列并将其用于绘制数据位置，可以增加地理编码的准确性。 例如，可传递“英格兰威尔特郡”而不是仅“威尔特”，以获取更准确的地理编码结果。 

在 Power BI 服务或 Power BI Desktop 中，可始终提供具体的维度和经度位置。 执行此操作时，还需要传递一个“位置”字段，否则会默认聚合数据，导致经度和维度位置可能不与所期望的内容相匹配。

## <a name="categorizing-geographic-fields-to-hint-bings-geocoding"></a>对地理字段进行分类以提示必应的地理编码
确保字段进行了正确的地理编码的另一种方法是，通过设置数据字段上的“数据类别”。 在 Power BI Desktop 中，选择所需的表，转至“高级”功能区，然后将“数据类别”设置为“地址”、“市/县”、“洲”、“国家/地区”、“乡镇”、“邮政编码”、“州”或“省/自治区/直辖市”。 这些数据分类有助于必应对数据进行正确编码。 若要了解详细信息，请参阅 [Power BI Desktop 中的数据分类](../transform-model/desktop-data-categorization.md)。

## <a name="better-geocoding-with-more-specific-locations"></a>借助更具体的位置，改善地理编码
有时（甚至于）设置可用于绘制地图的数据类别还不够。 可使用 Power BI Desktop 中的查询编辑器生成街道地址等更具体的位置。 使用“添加列”功能来构建自定义列。 再构建所需位置，如下所示： 

    = [Field1] & " " & [Field2]

然后，在地图可视化效果中使用生成的此字段。 此方法非常有助于从“送货地址”字段中生成常用于数据集的街道地址。 要注意的一点是，串联仅适用于文本字段。 如有必要，请先向街道编号转换为文本数据类型，然后再将其用于生成地址。

## <a name="histograms-in-the-query-stage"></a>查询阶段中的直方图
在 Power BI Desktop 中，直方图有多种构建方法，我们首先讲最简单的，请参见以下内容：

最简单的直方图 - 确定哪个查询具有要在其上构建直方图的字段。 对查询使用“引用”选项来创建新查询，并将其命名为“FieldName 直方图”。 使用“转换”功能区中的“分组依据”选项，然后选择“计行数”集合。 确保数据类型是所得聚合列的编号。 然后就可在报表页上直观显示此数据。 这是快速而简单的构建方法，但是如果你具有多个数据点且不允许跨视觉对象进行笔刷绘制，则这种方法不适用。

定义存储桶以构建直方图 - 确定哪个查询具有要在其上构建直方图的字段。 对查询使用“引用”选项来创建新查询，并将其命名为“FieldName”。 现在，使用规则定义存储桶。 使用“添加列”功能区上的“添加自定义列”选项，然后生成自定义规则。 一个简单的存储桶规则可能如下所示：

    if([FieldName] \< 2) then "\<2 min" else
    if([FieldName] \< 5) then "\<5 min" else
    if([FieldName] \< 10) then "\<10 min" else
    if([FieldName] \< 30) then "\<30 min" else
    "longer")

确保数据类型是所得聚合列的编号。 接下来，可使用“最简单的直方图”中所述的技巧来使用组生成直方图。 此选项可处理更多数据点，但仍不支持“笔刷绘制”功能。

定义支持笔刷绘制的直方图。笔刷绘制用于视觉对象链接在一起的情况，以便在用户选择一个视觉对象中的数据点时，报表页上的其他视觉对象可突出显示或筛选与所选数据点相关的数据点。 因为我们将在查询时操作数据，因此需要创建表格之间的关系，并确保了解与直方图中的存储桶相关的详细信息项，反之亦然。

首先要在查询上使用“引用”选项，其中此查询具有想在其上构建直方图的字段。 将新查询命名为“存储桶”。 对于本例，我们将原始查询称为“详细信息”。 接下来，删除所有列（将用作直方图存储桶的列除外）。 现在，使用查询中的“删除重复项”功能；选择此列后，它将位于右键单击菜单上，从而使剩下的值均为列中的唯一值。 如果有十进制数字，可先使用有关定义存储桶的提示来生成直方图，从而获得一组易于管理的存储桶。 现在，检查查询预览中显示的数据。 如果看到空白值或 Null，则需要在创建关系之前对它们进行修复。 请参阅“在数据具有 Null 值或空白值时创建关系”。 由于排序需要，使用此方法可能会产生问题。 若要获取存储桶以进行正确排序，请参阅“排列顺序：按所需顺序显示分类”。 

>[!NOTE]
>最好在生成视觉对象之前考虑排序顺序。 

本过程中的下一步是在存储桶列上定义“存储桶”和“详细信息”查询之间的关系。 在 Power BI Desktop 中，单击功能区上的**管理关系**。 创建一种关系，其中“存储桶”位于左表，而“详细信息”位于右表，然后选择将用于直方图的字段。 

最后一步是创建直方图。 拖动“存储桶”表中的“存储桶”字段。 从所生成的柱形图中删除默认字段。 现在将直方图字段从“详细信息”表拖到相同的视觉对象中。 在字段框，将默认聚合更改为“计数”。 然后将生成直方图。 如果还通过“详细信息”表创建了类似树状图的视觉对象，请在树状图中选择一个数据点以查看直方图高亮区，并显示与整个数据集趋势相关的所选数据点的直方图。

## <a name="histograms"></a>直方图
在 Power BI Desktop 中，可使用计算字段来定义直方图。 确定要在其上创建直方图的表格和列。 在计算区域，键入以下公式：

> Frequency:=COUNTROWS(\<Column Name\>)
> 
> 

保存更改并返回到报表。 将 \<Column Name\> 和“频率”添加到表格，然后转换为条形图。 确保 \<Column Name\> 位于 x 轴上，“频率”计算字段在 y 轴上。

## <a name="tips-and-tricks-for-creating-relationships-in-power-bi-desktop"></a>在 Power BI Desktop 中创建关系的相关提示和技巧
通常在加载来自多个源的详细信息数据集时，null 值、空白值或重复值等问题将阻止你创建关系。 

我们来看一个示例： 

如果我们加载来自活动客户支持请求的数据集，还加载一个具有以下架构的工作项的数据集：

> CustomerIncidents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

若想要跟踪与特定 CustomerName 相关的所有事件和工作项，则无法在这两个数据集之间简单创建一个关系。 某些 WorkItems 可能与 CustomerName 无关，所以此字段会为空或 NULL。 对于任意给定 CustomerName，WorkItems 和 CustomerIncidents 中可能有多条记录。 

### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-null-or-blank-values"></a>在数据有 NULL 或空白值时在 Power BI Desktop 中创建关系
数据集通常包含具有 null 值或空白值的列。 在尝试使用关系时，这可能会产生问题。 基本上，可有两个选项来处理这些问题。 可删除具有 null 或空白值的行。 为此，可使用查询选项卡中的筛选器功能，或（如果正在合并查询），选择“仅保留匹配行”选项。 此外，可将 null 或空白值替换为适用于关系的值，这通常是“NULL”和“(Blank)”等字符串。 此处无正确方法 - 在查询阶段筛选出行会删除行，并会影响汇总统计和计算。 后一种方法是保留数据行，但这会使不相关的行在模型中显示为相关，导致计算错误。 如果采用后一种解决方案，请确保在视图/图表处使用筛选器（如适用）以保证获取精确结果。 最重要的是，要评估保留/删除哪些行并了解对分析的整体影响。 

### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-duplicate-values"></a>在数据具有重复值时在 Power BI Desktop 中创建关系
通常，在加载来自多个源的详细数据集时，重复数据值将阻止你创建关系。 通过使用两个数据集中的唯一值来创建维度，可克服此问题。 

我们来看一个示例： 

如果我们加载来自活动客户支持请求的数据集，还加载一个具有以下架构的工作项的数据集：

> CustomerInicdents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

若想要跟踪与特定 CustomerName 相关的所有事件和工作项，则无法在这两个数据集之间简单创建一个关系。 某些 WorkItems 可能与 CustomerName 无关，所以此字段会为空或 NULL。 如果 CustomerNames 表中有任意空白值或 null 值，可能仍无法创建关系 - 请参阅“在数据有 null 或空白值时创建关系”。 对于单个 CustomerName，可能存在多个 WorkItems 和 CustomerIncidents。 

若要在此情况下创建关系，需要跨这两个数据集就 CustomerNames 创建一个逻辑数据集。 在查询选项卡中，可使用以下序列来创建逻辑数据集：

1. 复制这两个查询，将第一个命名为 **Temp**，第二个命名为 **CustomerNames**。
2. 在每个查询中，删除所有列（CustomerName 列*除外*）
3. 在每个查询中，使用**删除重复项**。
4. 在 **CustomerNames** 查询中，选择功能区中的**追加**选项，然后选择 **Temp** 查询。
5. 在 **CustomerNames** 查询中，选择**删除重复项**。

现在你拥有一个维度表，可用于关联到 CustomerIncidents 和包含各查询中所有值的 WorkItems。 

## <a name="patterns-to-jump-start-your-use-of-the-query-editor"></a>跳转以开始使用查询编辑器的模式
查询编辑器功能非常强大，它可操作数据以对其进行整理和清理，使数据可用于进行可视化和建模。 下面是需注意的几种模式。

### <a name="temporary-columns-can-be-deleted-after-computing-a-result"></a>计算出结果后，可删除临时列
通常，你需要在 Power BI Desktop 中构建一个计算，将多列中的数据转换到单个新列中。 这可能很复杂。 克服此问题的一种简单的方法是将操作分解为多个步骤。 首先复制初始列。 再生成临时列。 然后，创建最终结果列。 随后可删除临时列，使最终的数据集不杂乱。 这可能是由于查询选项卡按顺序执行步骤造成的。 

### <a name="duplicate-or-reference-queries-followed-by-merge-to-original-query"></a>复制或引用查询，然后合并到原始查询
有时这有助于计算数据集的汇总统计信息。 此操作的简单方法是复制或引用查询选项卡中的查询。然后使用**分组依据**来计算汇总统计信息。 汇总统计信息可帮助你规范化原始数据中的数据，使其更加适合用于比较。 在将单独的值与整体相比较时，此项尤其有用。 此次，请转到原始查询并选择“合并”选项。 然后合并汇总统计信息查询中按合适标识符进行匹配的数据。 现在就可规范化分析所需的数据了。

## <a name="using-dax-for-the-first-time"></a>首次使用 DAX
DAX 是 Power BI Desktop 中的计算公式语言。 它针对 BI 分析进行了优化。 与你仅使用 SQL（如查询语言）时可能熟知的功能相比，它可能略有不同。 可参阅详尽的在线资料和宣传资料来了解 DAX。 

[了解 Power BI Desktop 中的 DAX 基础知识](../transform-model/desktop-quickstart-learn-dax-basics.md)

[数据分析表达式 (DAX) 引用](/dax/)

[DAX 资源中心](https://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx)

## <a name="power-bi-service-and-power-bi-desktop"></a>Power BI 服务和 Power BI Desktop

### <a name="read-or-watch-how-to-design-visually-stunning-reports-and-dashboards"></a>阅读或观看“如何设计视觉效果令人震撼的报表（和仪表板）”
社区成员 Miguel Myers 既是数据科学家又是图形设计师。 

![Power BI 报表](media/desktop-tips-and-tricks-for-creating-reports/power-bi-reports.png)

* [阅读博客](https://powerbi.microsoft.com/blog/how-to-design-visually-stunning-reports/)
* [观看网络研讨会](https://community.powerbi.com/t5/Webinars-and-Video-Gallery/5-3-17-Webinar-How-to-Design-Visually-Stunning-Power-BI-Reports/m-p/168204?Is=Website)

### <a name="consider-your-audience"></a>考虑受众
可帮助他们做决定的关键指标是什么？ 如何使用报表？ 何种习得设定或文化设定可能会影响设计选择？ 你的受众需要哪些信息才能成功？

将在什么位置显示报表？ 如果将在大型监视器上显示，你可在其上放置更多内容。 如果读者将在其平板电脑上查看它，则更少的可视化效果将更具可读性。

### <a name="tell-a-story-and-keep-it-to-one-screen"></a>呈现一个情景，并将其保持在一个屏幕
每个报表页应一目了然地呈现一个情景。 你是否可以在你的页面上避免使用滚动条？ 报表是否太杂乱或太拥挤？  删除可以轻松读取和解释的基本信息以外的所有信息。

### <a name="make-the-most-important-information-biggest"></a>让最重要的信息以最大字体显示
如果报表页上的文本和可视化效果大小相同，你的读者会很难将重点放在最重要的信息上。 例如，卡片可视化效果是突出显示重要数字的好办法：  
![卡片可视化效果](media/service-dashboards-design-tips/pbi_card.png)

### <a name="but-be-sure-to-provide-context"></a>但请务必提供上下文  

使用文本框和工具提示等功能将上下文添加到可视化效果。

### <a name="put-the-most-important-information-in-the-upper-corner"></a>将最重要的信息置于顶部角落
大多数人会从上到下阅读，因此将最高级别的详细信息置于顶部，并在你以受众阅读的方向移动时显示更多详细信息（从左到右、从右到左）。

### <a name="use-the-right-visualization-for-the-data-and-format-it-for-easy-reading"></a>对数据使用适当的可视化效果并设置其格式以方便阅读
避免出于多样性的目的而使可视化效果多样。  可视化效果应对图片润色，且应易于“阅读”和解释。  对于某些数据和可视化效果，简单的图形可视化就足够了。 但其他数据可能会要求更复杂的可视化效果 - 确保使用标题和标签以及其他自定义来帮助读者。  

* 请谨慎使用扭曲实体的图表（如三维图表）和不从零开始的图表。 请记住，对人脑来说，很难解释圆形形状。 饼图、环形图、仪表以及其他圆形的图表类型可能看起来相当美观，但是否可以使用其他视觉对象？    
* 与轴上的图表比例、图表维序，以及用于图表内维度值的颜色保持一致。    
* 务必恰当地对定量数据进行编码。 显示数字时，不要超过三个或四个数字。 对小数点左侧的一个或两个数字显示度量值并显示千或百万的单位，即 3.4 百万，而不是 3,400,000。    
* 尽量避免混合精度级别和时间级别。 确保时间范围易于理解。  不要将上个月的图表置于该年度特定月份的已筛选图表旁。    
* 此外，尽量避免在同一比例上（如在折线图或条形图上）混合大度量值和小度量值。  例如，一个度量值可能以百万计，其他度量值则以千计。  使用这种大比例，很难看出以千计的度量值的差异。  如果需要混合，则选择一个允许使用第二个轴的可视化效果，如组合图。    
* 避免使用不需要的数据标签打乱图表。 条形图中的值（如果足够大）通常易于了解，而不显示实际数。   
* 请注意如何[对图表进行排序](../consumer/end-user-change-sort.md)。 如果你想要将注意点放在最高或最低的数字，则通过度量值进行排序。 如果希望用户能够在许多其他类别中快速找到特定类别，则按轴进行排序。  
* 如果类别少于八个，则饼图最佳。 由于不能并排比较值，所以在饼图中的比较值要比在条形图和柱形图中比较值更难。 饼图有助于查看部分对整体的关系，而不利于将部分进行比较。 仪表盘则非常适合用于在目标上下文中显示当前状态。    

有关更多可视化效果特定指南，请参阅 [Power BI 中的可视化效果类型](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)。  

### <a name="learn-more-about-best-practice-dashboard-design"></a>了解更多关于最佳仪表板设计的信息
一些我们最喜爱的书籍有：

* *Storytelling with Data*，Cole Nussbaumer Knafic 著
* *Data points*，Nathan Yau 著
* *The truthful Art*，Alberto Cairo 著
* *Now You See It* ，Stephen Few 著  
* *Envisioning Information* ，Edward Tufte 著  
* *Advanced Presentations Design*，Andrew Abela 著   

## <a name="next-steps"></a>后续步骤
* [Power BI 服务中设计器的基本概念](../fundamentals/service-basic-concepts.md)
* [Power BI 中的报表](../consumer/end-user-reports.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

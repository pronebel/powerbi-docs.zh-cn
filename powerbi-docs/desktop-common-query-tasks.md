---
title: Power BI Desktop 中的常见查询任务
description: Power BI Desktop 中的常见查询任务
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: dc6aa42691c7caa2593b28e441f96985b1e3bcda
ms.sourcegitcommit: b11e908650379913d00673215e3eaf25d712b122
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65239421"
---
# <a name="common-query-tasks-in-power-bi-desktop"></a>Power BI Desktop 中的常见查询任务
使用 Power BI Desktop 的**查询编辑器**窗口时，可执行很多常用任务。 本文档演示了这些常见的任务，并提供其他信息的链接。 

本文展示了下列常见查询任务：

* 连接到数据
* 调整和合并数据
* 行分组
* 列透视
* 创建自定义列
* 查询公式

我们将使用几个数据连接来完成这些任务。 如果你想要自己逐步完成这些任务，可下载或连接下列数据。

第一个数据连接是 Excel 工作簿，可以从[此链接](http://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx)下载该工作簿。 另一个是 Web 资源（还可用作其他 Power BI Desktop 学习内容），可以从以下链接进行访问：

[*http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx*](http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

执行连接到这两个数据源的必要步骤就是常见查询任务的开始。

## <a name="connect-to-data"></a>连接到数据
若要在 Power BI Desktop 中连接到数据，请从功能区上的“开始”选项卡选择“获取数据”按钮。 Power BI Desktop 将显示一个含有最常见数据源的菜单。 对于 Power BI Desktop 可连接到的数据源的完整列表，请选择菜单底部的“更多... ”按钮。 有关详细信息，请参阅 [Power BI Desktop 中的数据源](https://docs.microsoft.com/power-bi/desktop-data-sources)。

![](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

首先，选择 **Excel** 并导航到该工作簿，然后将其选中。 查询将检查该工作簿，然后在“导航器”窗口中呈现找到的数据。

![](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

在将数据加载到 Power BI Desktop 中之前，可选择**编辑**来调整或组织数据。 在处理想要在加载前进行削减的大型数据集时，先编辑查询再加载数据尤其有用。 我们想要执行此操作，因此选择**编辑**。

连接到其它类型的数据同样简单。 我们还想要连接到 Web 资源。 选择“获取数据 \>更多...”，然后选择**其他\>Web**。

![](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

**从Web**窗口随即出现，可在其中键入网页的 URL。

![](media/desktop-common-query-tasks/datasources_fromwebbox.png)

选择“确定”；和之前一样，Power BI Desktop 将检查工作簿，并在“导航器”窗口中呈现找到的数据。

其他数据连接与此类似。 如果需要身份验证才能建立数据连接，Power BI Desktop 将提示你提供相应凭据。

有关连接到 Power BI Desktop 中数据的分步演示，请参阅[连接到 Power BI Desktop 中的数据](https://docs.microsoft.com/power-bi/desktop-connect-to-data)。

## <a name="shape-and-combine-data"></a>调整和合并数据
可使用查询编辑器轻松地调整和合并数据。 本部分包括几个有关数据调整方式的示例。 有关如何调整和合并数据的更完整演示，请参阅 **[使用 Power BI Desktop 调整和合并数据](https://docs.microsoft.com/power-bi/desktop-shape-and-combine-data)**。

上一节中，我们连接到两组数据 – Excel 工作簿和 Web 资源。 在“查询编辑器”中加载后，我们将看到以下结果，其中选中了网页中的查询（取自“查询编辑器”窗口左侧的“查询”窗格内列出的可用查询）。

![](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

在调整数据时，可将数据源转换为满足你需求的形式和格式。 此情况下不需要名为 *标题* 的第一列，因此将其删除。

在**查询编辑器**中，可在功能区和上下文相关的右键单击菜单中找到许多命令。 例如，在右键单击“标题”列时，显示的菜单将允许删除此列。 还可选中此列，然后选择功能区中的“删除列”按钮。

![](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

还有多种方式可用于调整此查询中的数据；可从顶部或底部删除任意数量的行；可添加列、拆分列、替换值，并执行其他调整任务以指示查询编辑器按所需方式获取数据。

## <a name="group-rows"></a>行分组
在查询编辑器中，可将多个行中的值聚集为单个值。 在汇总所提供的产品数、总销售额或学生计数时，这会很有用。

在此示例中，我们对教育注册数据集中的行进行分组。 数据来自 Excel 工作簿，并已在查询编辑器中进行调整以仅获取所需的列、重命名表格并执行一些其他转换。

我们来了解一下每个州有多少机构（这包括学区和其他教育机构，如区域服务学区等）。 选择 *州缩写* 列，然后选择 **转换** 选项卡中的 **分组依据** 按钮或功能区的 **开始** 选项卡（这两个选项卡中都有 **分组依据** ）。

![](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

**分组依据…** 窗口随即出现。 当查询编辑器对行进行分组时，它会创建一个新列，将**分组依据**结果置于其中。 可按照以下方式调整**分组依据**操作：

1. 分组依据 – 这是要进行分组的列；查询编辑器将选择所选列，但可在此窗口中将其更改为表中的任意列。
2. 新列名 – 查询编辑器会基于它对要进行分组的列所应用的操作为新列建议一个名称；但也可将新列命名为所需的任何名称。
3. 操作 – 在此处指定查询编辑器将应用的操作。
4. 添加分组和添加聚合 – 选择“高级”选项后，将显示这些选项。 可在“分组依据”窗口中一次性完成对多个列执行分组操作（分组依据操作）和执行多个聚合。 查询编辑器将创建一个新列来存储多个列上操作的结果（基于此窗口内的所选内容）。 

选择“添加分组”或“添加聚合”按钮，向“分组依据”操作添加更多分组或聚合操作。 可依次选择“...”图标和“删除”来删除分组或聚合，因此可以不断尝试相关操作，看看它的显示结果。
   
   ![](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

在选择"确定"时，查询将执行"分组依据"操作并返回结果。 嘿，看看这个 – 俄亥俄州、德克萨斯州、伊利诺伊州和加利福尼亚州，每个州现在都有 1,000 多个机构！

![](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

此外，借助查询编辑器，可通过选择刚刚完成的步骤旁边的 **X** 随时删除最近一次调整操作。 因此可以大胆的去尝试，如果结果不合你意，可重做此步骤，直到查询编辑器恰好按所需的方式调整数据。

## <a name="pivot-columns"></a>列透视
通过 Power BI Desktop，可对列进行透视，并创建包含某列中每个唯一值的聚合值的表格。 例如，如果需要知道在每个产品类别中具有多少种不同的产品，可快速创建一个表来精确执行此操作。

我们来看一个示例。 以下**产品**表已调整为仅显示每个唯一产品（按名称）以及每种产品所属的类别。 若要新建一个表格来显示每个类别的产品计数（基于 *CategoryName* 列），请选中该列，然后在功能区上选择**转换**选项卡的**透视列**。

![](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

“透视列”窗口随即出现，显示哪一列的值将被用于创建新列 (1)，并且在展开“高级选项” (2) 时，可选择将应用于聚合值 (3) 的函数。

![](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

当选择**确定**时，查询将根据**透视列**窗口中提供的转换说明显示表。

![](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>创建自定义列
在查询编辑器中，可创建对表中多个列进行操作的自定义公式，然后将此类公式的计算结果放入新的（自定义）列中。 查询编辑器可轻松创建自定义列。

在查询编辑器的功能区上，从“添加列”选项卡中选择“自定义列”。

![](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

将显示以下窗口。 在下例中，我们创建名为 *Percent ELL* 的自定义列，该列计算为英语学习者 (ELL) 的学生总数的百分比。

![](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

如同查询编辑器中应用的任何其他步骤一样，如果新的自定义列没有提供你要查找的数据，则只需通过选择“已添加自定义”步骤旁边的 **X**，从“查询设置”窗格的“所应用步骤”部分删除该步骤即可。

![](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>查询公式
可修改查询编辑器生成的步骤，还可创建自定义公式，从而精确地控制对数据的连接和调整操作。 每当查询编辑器对数据执行操作时，“公式栏”中都会显示与操作关联的公式。 若要查看“公式栏”，请在功能区的“查看”选项卡中选择“公式栏”旁边的复选框。

![](media/desktop-common-query-tasks/queryformulas_formulabar.png)

查询编辑器将每个查询的所有已应用步骤保存为可查看或修改的文本。 可使用**高级编辑器**查看或修改任何查询的文本；在功能区的**查看**选项卡中选择**高级编辑器**时，即会显示该编辑器。

![](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

下面来看看**高级编辑器**，它显示了与 **USA\_StudentEnrollment** 查询关联的查询步骤。 这些步骤是使用 Power Query 公式语言（通常称为 **M**）进行创建的。相关信息，请参阅[了解 Power 查询公式](https://support.office.com/article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f)。 若要查看语言规范本身，请参阅 [Microsoft Power Query for Excel 公式语言规范](http://go.microsoft.com/fwlink/?linkid=320633)。

![](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

Power BI Desktop 提供了一组全面的公式类别。 有关详细信息和所有查询编辑器公式的完整参考，请访问 [Power Query 公式类别](https://support.office.com/article/Power-Query-formula-categories-125024ec-873c-47b9-bdfd-b437f8716819)。

查询编辑器的公式类别如下所示：

* 数字
  * 常量
  * 信息
  * 转换和格式设置
  * 格式
  * 舍入
  * 运算
  * 随机
  * 三角函数
  * 字节数
* 文本
  * 信息
  * 文本比较
  * 提取
  * 修改
  * 成员资格
  * 转换
* 逻辑
* 日期
* 时间
* 日期时间
* 时区
* 持续时间
* 记录
  * 信息
  * 转换
  * 所选内容
  * 序列化
* 列表
  * 信息
  * 所选内容
  * 转换
  * 成员资格
  * Set 运算
  * 排序
  * 平均值
  * 相加
  * 数值
  * 生成器
* 表
  * 构造表
  * 转换
  * 信息
  * 行操作
  * 列操作
  * 成员资格
* 值
* 算术运算
* 参数类型
* 元数据
* 访问数据
* URI
* 二进制格式
  * 读取数字
* 二进制
* 行
* 表达式
* 函数
* 错误
* 比较器
* 拆分器
* 组合器
* 替换器
* 类型

## <a name="next-steps"></a>后续步骤
Power BI Desktop 可用于执行多种操作。 有关其功能的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 的查询概述](desktop-query-overview.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [连接到 Power BI Desktop 中的数据](desktop-connect-to-data.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)


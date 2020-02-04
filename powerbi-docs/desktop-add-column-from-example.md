---
title: 在 Power BI Desktop 中通过示例添加列
description: 将现有列用作示例在 Power BI Desktop 中快速创建新列。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b10bbaa4158e6c5392cb6ed937c54bdbb5d555d2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538452"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Power BI Desktop 中的“从示例中添加列”
通过 Power Query 编辑器中的“从示例中添加列”  ，只需为新列提供一个或多个示例值，便可以将新列添加到数据模型。 可以通过所选内容创建新的列示例，或基于表中的所有现有列提供输入。

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

使用“从示例中添加列”  可快速轻松地创建新列，非常适用于以下情形：

- 你知道自己想要在新列中获得的数据，但不确定通过哪种转换（或一系列转换）可以实现目的。
- 你已知道自己需要执行的转换，但不确定在 UI 中选择什么内容来执行这些转换。
- 你知道在“M”  语言中使用“自定义列”  表达式所需的转换的全部信息，但其中一个或多个表达式在 UI 中不可用。

从示例中添加列十分简单。 接下来的部分演示这是多么简单。

## <a name="add-a-new-column-from-examples"></a>从示例中添加新列

若要从维基百科获取示例数据，请从 Power BI Desktop 功能区的“主页”  选项卡中选择“获取数据”   > “Web”  。 

![从 Web 获取数据](media/desktop-add-column-from-example/add-column-from-example_02.png)

将以下 URL 粘贴到显示的对话框中，然后选择“确定”  ： 

https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States 

在“导航器”  对话框中，选择“美国的州”  表，然后选择“转换数据”  。 该表将在 Power Query 编辑器中打开。

或者，若要从 Power BI Desktop 打开已加载的数据，请从功能区的“主页”  选项卡选择“编辑查询”  。 数据会在 Power Query 编辑器中打开。 

![从 Power BI Desktop 选择“编辑查询”](media/desktop-add-column-from-example/add-column-from-example_05.png)

示例数据在 Power Query 编辑器中打开后，在功能区上选择“添加列”  选项卡，然后选择“示例中的列”  。 选择“示例中的列”  图标本身以从所有现有列创建列，或选择下拉箭头以选择“从所有列”  或“从所选内容”  。 对于本演练，请使用“从所有列”  。

![选择“从示例中添加列”](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>“从示例中添加列”窗格
如果选择“添加列”   > “从示例”  ，则“从示例中添加列”  窗格会在表的顶部打开。 新的“列 1”  会出现在现有列右侧（可能需要滚动才能查看所有这些列）。 在“列 1”  的空白单元格中输入示例值时，Power BI 会创建规则和转换以匹配示例，并使用它们填充列的其余部分。

请注意，“示例中的列”  列还会在“查询设置”  窗格中显示为“应用的步骤”  。 和以往一样，Power Query 编辑器会记录转换步骤，并依序向查询应用这些步骤。

![“从示例中添加列”窗格](media/desktop-add-column-from-example/add-column-from-example_04.png)

在新列中键入示例时，Power BI 会根据创建的转换显示列的其余部分的外观预览。 例如，如果在第一行中键入“Alabama”，则它对应于表中第一列的“Alabama”值   。 按 Enter 后，Power BI 会立即基于第一列的值填充新列的其余部分，并将该列命名为“Name & postal abbreviation[12] - Copy”  。

现在，请跳到新列的“Massachusetts[E]”  行，然后删除字符串的“[E]”  部分。 Power BI 可检测更改，并使用该示例创建转换。 Power BI 在“从示例中添加列”  窗格中描述转换，并将列重命名为“分隔符之前的文本”  。 

![从示例转换的列](media/desktop-add-column-from-example/add-column-from-example_06.png)

如果继续提供示例，Power Query 编辑器会将其添加到转换中。 如果感到满意，请选择“确定”  提交更改。 

可以通过双击列标题或右键单击列标题并选择“重命名”  ，将新列重命名为所需的任何内容。 

观看此视频以了解实际操作的“从示例中添加列”  （使用示例数据源）： 

[Power BI Desktop：从示例中添加列](https://www.youtube.com/watch?v=-ykbVW9wQfw)。 

## <a name="list-of-supported-transformations"></a>支持的转换的列表
使用“从示例中添加列”  时，有很多（但并非所有）转换可用。 下面的列表显示受支持的转换：

 常规

- 条件列

**引用**
  
- 引用特定列，包括修整、清理和大小写转换

**文本转换**

- 合并（支持合并文本字符串和整个列值）
- 替换
- 长度
- 提取   
  - 第一个字符
  - 最后一个字符
  - 范围
  - 分隔符前的文本
  - 分隔符后的文本
  - 分隔符之间的文本
  - 长度
  - 删除字符
  - 保留字符

> [!NOTE]
> 对于所有文本  转换，都要考虑是否需要进行修整、清理或对列值应用大小写转换。

**日期转换**

- 天
- 每周的某一日
- 周几名称
- 每年的某一日
- 月
- 月份名称
- 每年的某一季度
- 每月的某一周
- 每年的某一周
- 年份
- 年限
- 年份开始值
- 年份结束值
- 月份开始值
- 月份结束值
- 季度开始值
- 一个月的某些日
- 季度结束值
- 星期开始值
- 星期结束值
- 每月的某一日
- 一天开始值
- 一天结束值

**时间转换**

- Hour
- Minute
- Second  
- 本地时间

> [!NOTE]
> 对于所有“日期”和“时间”转换，都要考虑是否可能需要将列值转换成“日期”或“时间”或“日期和时间”      。

**数字转换** 

- 绝对值
- 反余弦
- 反正弦
- 反正切
- 转换为数字
- 余弦
- 多维数据集
- 除
- 求幂
- 阶乘
- 整除
- 为偶数
- 为奇数
- 自然对数
- 以 10 为底数的对数
- 取模
- 乘
- 向下舍入
- 向上舍入
- 符号
- 正弦
- 平方根
- 平方
- 减
- 求和
- 正切
- Bucket/范围


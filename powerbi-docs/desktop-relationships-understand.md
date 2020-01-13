---
title: Power BI Desktop 中的模型关系
description: 介绍有关 Power BI Desktop 中模型关系的理论
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 0029d275e5180c29e8653f549d8450014362b59b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2020
ms.locfileid: "75304248"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Power BI Desktop 中的模型关系

本文主要面向使用 Power BI Desktop 的 Import 数据建模者。 它是一个重要的模型设计主题，对于提供直观、准确且最理想的模型至关重要。

若要更深入地探讨包括表角色和关系在内的最佳模型设计，请参阅[了解星型架构及其对 Power BI 的重要性](guidance/star-schema.md)一文。

## <a name="relationship-purpose"></a>关系用途

简而言之，Power BI 关系会将应用于模型表列的筛选器传播到其他模型表。 只要有关系路径可循，筛选器就会进行传播，这可能涉及传播到多个表。

关系路径是确定性的，这意味着筛选器始终以相同的方式传播，而不会随机变化。 但是，可以禁用关系，或通过使用特定 DAX 函数的模型计算来修改筛选器上下文。 有关详细信息，请参阅本文后面的[相关 DAX 函数](#relevant-dax-functions)主题。

> [!IMPORTANT]
> 请务必了解，模型关系不强制实施数据完整性。 有关详细信息，请参阅本文后面的[关系评估](#relationship-evaluation)主题。 此主题介绍当数据存在数据完整性问题时模型关系的行为。

让我们通过一个动画示例，看看关系如何传播筛选器。

![关系筛选器传播的动画示例](media/desktop-relationships-understand/animation-filter-propagation.gif)

在此示例中，模型由四个表组成：**Category**、**Product**、**Year** 和 **Sales**。 **Category** 表关联到 **Product** 表，而 **Product** 表关联到 **Sales** 表。 **Year** 表也关联到 **Sales** 表。 所有关系均为一对多（本文后面将对此进行详细介绍）。

某个查询（可能由 Power BI 卡视觉对象生成）请求单个类别 **Cat-A** 和单个年份 **CY2018** 的销售订单的总销量。 这就是你可以看到 **Category** 和 **Year** 表上应用的筛选器的原因。 **Category** 表上的筛选器传播到 **Product** 表，分离出分配给类别 **Cat-A** 的两个产品。 然后，**Product** 表筛选器传播到 **Sales** 表，针对这些产品分离出两个销售行。 这两个销售行表示分配给类别 **Cat-A** 的产品的销量。 其总量为 14 个单位。 与此同时，传播 **Year** 表筛选器以进一步筛选 **Sales** 表，最终得到一个销售行，该行对应于分配给类别 **Cat-A** 并于 **CY2018** 年订购的产品。 该查询返回的数量值为 11 个单位。 请注意，向某个表应用多个筛选器时（例如本示例中的 **Sales** 表），始终进行 AND 运算，即，要求所有条件都必须成立。

### <a name="disconnected-tables"></a>断开连接的表

一个模型表与另一个模型表不关联的情况不太常见。 可以将有效模型设计中的此类表称为_断开连接的表_。 断开连接的表不用于将筛选器传播到其他模型表， 而用于接受“用户输入”（可能包含切片器视觉对象），从而使模型计算能够以有意义的方式使用输入值。 例如，假设有一个断开连接的表，表中加载了一系列货币汇率值。 如果应用筛选器以按单个费率值进行筛选，则度量值表达式可以使用该值来转换销售值。

Power BI Desktop what-if 参数是一个用于创建断开连接的表的功能。 有关详细信息，请参阅[创建并使用 What if 参数来可视化 Power BI Desktop 中的变量](desktop-what-if.md)一文。

## <a name="relationship-properties"></a>关系属性

模型关系可将一个表中的一列关联到另一个表中的一列。 （在一种特殊情况下，此要求不成立，这种情况仅适用于 DirectQuery 模型中的多列关系。 有关详细信息，请参阅 [COMBINEVALUES](/dax/combinevalues-function-dax) DAX 函数一文。）

> [!NOTE]
> 无法将_同一表中_的一列关联到另一列。 这有时会与能够定义表自引用的关系数据库外键约束相混淆。 此关系数据库概念可用于存储父子关系（例如，每条员工记录均关联到一个“汇报对象”员工）。 无法通过创建模型关系来生成基于父子关系的模型层次结构。 若要生成这样的层次结构，请参阅[父函数和子函数](/dax/parent-and-child-functions-dax)一文。

### <a name="cardinality"></a>基数

必须为每个模型关系定义基数类型。 一共有四个基数类型选项，表示“从”和“到”相关列的数据特征。 “一”侧表示该列包含唯一值；“两”侧表示该列可以包含重复值。

> [!NOTE]
> 如果数据刷新操作尝试将重复值加载到“一”侧列中，则整个数据刷新将失败。

以下项目符号列表描述了这四个选项及其速记符号：

- 一对多 (1:\*)
- 多对一 (\*:1)
- 一对一 (1:1)
- 多对多 (\*:\*)

在 Power BI Desktop 中创建关系时，设计器将自动检测并设置基数类型。 设计器之所以可以执行此操作，是因为它会查询模型以了解哪些列包含唯一值。 对于 Import 模型，它使用内部存储统计信息；对于 DirectQuery 模型，它向数据源发送分析查询。 但是，有时可能会出错。 出错的原因有二：表中尚未加载数据，或者你希望包含重复值的列当前包含唯一值。 在任一情况下，如果任何“一”侧列包含唯一值（或者表中尚未加载数据行），你都可以更新基数类型。

“一对多”和“多对一”基数选项基本相同，并且它们也是最常见的基数类型。

配置一对多或多对一关系时，将选择与列关联顺序匹配的关系。 设想一下，如何使用每个表中的 **ProductID** 列来配置从 **Product** 表到 **Sales** 表的关系。 基数类型将为_一对多_，因为 **Product** 表中的 **ProductID** 列包含唯一值。 如果将表反向关联，即 **Sales** 到 **Product**，则基数为_多对一_。

**一对一**关系意味着两个列都包含唯一值。 这种基数类型并不常见，并且由于冗余数据的存储，它可能代表了不太理想的模型设计。<!-- For guidance on using this cardinality type, see the [One-to-one relationship guidance](guidance/relationships-one-to-one) article.-->

**多对多**关系意味着两个列都可以包含重复值。 这种基数类型很少使用。 在设计复杂的模型需求时，它通常很有用。 有关使用此基数类型的指南，请参阅[多对多关系指南](guidance/relationships-many-to-many.md)。

> [!NOTE]
> 为 Power BI 报表服务器开发的模型目前不支持“多对多”基数类型。

> [!TIP]
> 在 Power BI Desktop 模型视图中，可以通过查看关系线两端的指示符（1 或 \*）来解释关系的基数类型。 若要确定关联了哪些列，你需要选择关系线或将光标悬停在其上方，以突出显示这些列。

### <a name="cross-filter-direction"></a>交叉筛选器方向

必须为每个模型关系定义交叉筛选方向。 你的选择将决定筛选器的传播方向。 可能的交叉筛选选项取决于基数类型。

| 基数类型 | 交叉筛选选项 |
| --- | --- |
| 一对多（或多对一） | 单向<br>两者 |
| 一对一 | 两者 |
| 多对多 | 单（Table1 到 Table2）<br>单（Table2 到 Table1）<br>两者 |

_单_交叉筛选方向表示“单向”，_双_表示“双向”。 在两个方向进行筛选的关系通常称为_双向_。

在一对多关系中，交叉筛选方向始终从“一”侧开始，也可以选择从“多”侧开始（双向）。 在一对一关系中，交叉筛选方向始终同时从两个表开始。 最后，在多对多关系中，交叉筛选方向可以从其中一个表开始，也可以同时从两个表开始。 请注意，当基数类型包括“一”侧时，此类筛选器将始终从该侧传播。

如果将交叉筛选方向设置为“双”，那么在实施行级别安全性 (RLS) 规则时，可以使用一个附加属性来应用双向筛选。 有关 RLS 的详细信息，请参阅 [Power BI Desktop 行级别安全性 (RLS)](desktop-rls.md) 一文。

也可以通过模型计算来修改关系交叉筛选方向（包括禁用筛选器传播）。 这可以通过 [CROSSFILTER](/dax/crossfilter-function) DAX 函数来实现。

双向关系可能会对性能产生负面影响。 此外，尝试配置双向关系可能会导致筛选器传播路径不明确。 在这种情况下，Power BI Desktop 可能无法提交关系更改，并通过错误消息发出警报。 但是，有时 Power BI Desktop 可能允许你在表之间定义不明确的关系路径。 本文后面的[优先规则](#precedence-rules)主题将介绍影响歧义检测和路径解析的优先规则。

建议仅在需要时使用双向筛选。<!-- For guidance on bi-directional filtering, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

> [!TIP]
> 在 Power BI Desktop 模型视图中，可以通过观察关系线的箭头来解释关系的交叉筛选方向。 单箭头表示沿箭头方向的单向筛选器；双箭头表示双向关系。

### <a name="make-this-relationship-active"></a>激活此关系

两个模型表之间只能有一条活动的筛选器传播路径。 你可以引入其他关系路径，但必须将这些关系都配置为_非活动状态_。 只能在模型计算评估期间激活非活动关系。 这可以通过 [USERELATIONSHIP](/dax/userelationship-function-dax) DAX 函数来实现。

<!--For guidance on defining inactive relationships, see the [Active vs inactive relationship guidance](guidance/relationships-active-inactive) article.-->

> [!TIP]
> 在 Power BI Desktop 模型视图中，可以解释关系的活动状态与非活动状态。 活动关系用实线表示；非活动关系用虚线表示。

### <a name="assume-referential-integrity"></a>假设引用完整性

_假设引用完整性_属性仅适用于基于同一数据源的两个 DirectQuery 存储模式表之间的一对多和一对一关系。 启用后，发送到数据源的本机查询会使用内部联接而不是外部联接来联接两个表。 通常，启用此属性可以提高查询性能，但具体取决于数据源的详细情况。

当两个表之间存在数据库外键约束时，应始终启用此属性。 当不存在外键约束时，只要确定存在数据完整性，就仍然可以启用该属性。

> [!IMPORTANT]
> 如果数据完整性受到损害，内部联接将消除表之间不匹配的行。 例如，假设有一个模型 **Sales** 表，其中的 **ProductID** 列值在关联 **Product** 表中不存在。 从 **Product** 表到 **Sales** 表的筛选器传播将消除未知产品的销售行。 这会导致低估销售结果。
>
> 有关详细信息，请参阅 [Power BI Desktop 中的假设引用完整性设置](desktop-assume-referential-integrity.md)一文。

## <a name="relevant-dax-functions"></a>相关 DAX 函数

有几个与模型关系相关的 DAX 函数。 以下项目符号列表简要介绍了每个函数：

- [RELATED](/dax/related-function-dax)：从“一”侧检索值。
- [RELATEDTABLE](/dax/relatedtable-function-dax)：从“多”侧检索表行。
- [USERELATIONSHIP](/dax/userelationship-function-dax)：强制使用特定的非活动模型关系。
- [CROSSFILTER](/dax/crossfilter-function)：修改关系交叉筛选方向（单或双），或者禁用筛选器传播（无）。
- [COMBINEVALUES](/dax/combinevalues-function-dax)：将两个或更多个文本字符串联接成一个文本字符串。 此函数的用途是支持 DirectQuery 模型中的多列关系。
- [TREATAS](/dax/treatas-function)：将表表达式的结果作为筛选器应用于无关表中的列。
- [父函数和子函数](/dax/parent-and-child-functions-dax)：可用于生成计算列以归化父子层次结构的一系列相关函数。 这些列随后可用于创建固定级别的层次结构。

## <a name="relationship-evaluation"></a>关系评估

从评估的角度来看，模型关系分为_强_或_弱_两种。 此关系属性不可配置。 事实上，它是从两个关联表的基数类型和数据源推断出来的。 了解评估类型非常重要，因为如果数据完整性受到损害，可能会产生一些性能影响或后果。 本主题将介绍这些影响和完整性后果。

首先，需要通过一些建模理论来充分了解关系评估。

Import 或 DirectQuery 模型从 Vertipaq 缓存或源数据库中获取其所有数据。 在这两个实例中，Power BI 都能确定某个关系的“一”侧是否存在。

但是，Composite 模型可能由使用不同存储模式（Import、DirectQuery 或 Dual）或多个 DirectQuery 源的表组成。 每个源（包括 Import 数据的 Vertipaq 缓存）都被视为一个_数据岛_。 然后，可以将模型关系分为_岛内_或_跨岛_两种。 岛内关系是指在一个数据岛中关联两个表，而跨岛关系是指关联不同数据岛中的表。 请注意，Import 或 DirectQuery 模型中的关系始终是岛内关系。

让我们看一个 Composite 模型的示例。

![由两个岛组成的 Composite 模型示例](media/desktop-relationships-understand/data-island-example.png)

在此示例中，Composite 模型由两个岛组成：Vertipaq 数据岛和 DirectQuery 源数据岛。 Vertipaq 数据岛包含三个表，而 DirectQuery 源数据岛包含两个表。 该示例中存在一个跨岛关系，即，将 Vertipaq 数据岛中的表关联到 DirectQuery 源数据岛中的表。

### <a name="strong-relationships"></a>强关系

当查询引擎可以确定关系的“一”侧时，模型关系为_强_。 它已确认“一”侧列包含唯一值。 所有一对多的岛内关系都是强关系。

下面的示例中有两个强关系，均标记为“S”。关系包括 Vertipaq 岛中包含的一对多关系和 DirectQuery 源中包含的一对多关系。

![由两个带有强关系标记的岛组成的 Composite 模型示例](media/desktop-relationships-understand/data-island-example-strong.png)

对于 Import 模型，其所有数据都存储在 Vertipaq 缓存中，在数据刷新时会为每​​个强关系创建一个数据结构。 数据结构由所有列到列值的索引映射组成，其用途是在查询时加快表的联接速度。

在查询时，强关系允许进行_表扩展_。 表扩展会包含基表的本机列，然后扩展到关联表中，从而创建虚拟表。 对于 Import 表，此操作在查询引擎中完成；对于 DirectQuery 表，此操作在发送到源数据库的本机查询中完成（前提是未启用“假设引用完整性”属性）。 然后，查询引擎对扩展表进行操作，应用筛选器，并按扩展表列中的值进行分组。

> [!NOTE]
> 非活动关系也会进行扩展，即使计算操作未使用该关系也是如此。 双向关系对表扩展没有影响。

对于一对多关系，使用左外部联接语义从“多”侧到“一”侧进行表扩展。 当从“多”侧到“一”侧的匹配值不存在时，会向“一”侧表添加一个空白虚拟行。

表扩展也适用于一对一的岛内关系，但要使用完全外部联接语义。 它确保必要时在任一侧添加空白虚拟行。

空白虚拟行实际上是_未知成员_。 未知成员表示引用完整性冲突，其中“多”侧值没有对应的“一”侧值。 理想情况下，不应存在这些空白行，可以通过清理或修复源数据来消除它们。

让我们通过一个动画示例来了解表扩展的工作原理。

![表扩展的动画示例](media/desktop-relationships-understand/animation-expanded-table.gif)

在此示例中，模型由三个表组成：**Category**、**Product** 和 **Sales**。 **Category** 表通过一对多的关系关联到 **Product** 表，而 **Product** 表通过一对多的关系关联到 **Sales** 表。 **Category** 表包含两行，**Product** 表包含三行，**Sales** 表包含五行。 所有关系的两侧都有匹配的值，这意味着不存在引用完整性冲突。 系统会显示一个查询时扩展表。 该表由这三个表中的列组成。 实际上，它是三个表中所含数据的非规范化透视图。 将向 **Sales** 表添加一个新行，其中包含一个生产标识符值 (9)，该值在 **Product** 表中没有匹配值。 这是一个引用完整性冲突。 在扩展表中，新行针对 **Category** 和 **Product** 表列具有 (Blank) 值。

### <a name="weak-relationships"></a>弱关系

当没有确定的“一”侧时，模型关系为_弱_。 这种情况可能有两个原因：

- 该关系使用多对多基数类型（即使其中一列或两列都包含唯一值）
- 该关系跨岛（这种情况仅适用于 Composite 模型）

下面的示例中有两个弱关系，均标记为“W”。这两个关系包括一对多跨岛关系和 Vertipaq 岛中包含的多对多关系。

![由两个带有弱关系标记的岛组成的 Composite 模型示例](media/desktop-relationships-understand/data-island-example-weak.png)

对于 Import 模型，永远不会为弱关系创建数据结构。 这意味着必须在查询时解析表联接。

对于弱关系，永远不会发生表扩展。 表联接是使用内部联接语义实现的，因此，不会添加空白虚拟行来补偿引用完整性冲突。

还有一些与弱关系相关的限制：

- 无法使用 RELATED DAX 函数来检索“一”侧列值
- 实施 RLS 时具有拓扑限制

> [!NOTE]
> 在 Power BI Desktop 模型视图中，并非始终能够确定模型关系是强还是弱。 多对多关系永远都是弱关系，就像跨岛关系时的一对多关系一样。 若要确定是否是跨岛关系，需检查表存储模式和数据源以得出正确的确定结果。

### <a name="precedence-rules"></a>优先规则

双向关系可以在模型表之间引入多个（因此不明确）筛选器传播路径。 以下列表列出了 Power BI 用于歧义检测和路径解析的优先规则：

1. 多对一和一对一关系，包括弱关系
2. 多对多关系
3. 反向的双向关系（即，从“多”侧开始）

### <a name="performance-preference"></a>性能首选项

以下列表对筛选器传播性能（从最快到最慢）进行了排序：

1. 一对多岛内关系
2. 多对多基数关系
3. 使用中间表实现的多对多模型关系，并且涉及至少一个双向关系
4. 跨岛关系

<!--For further information and guidance on many-to-many relationships, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

## <a name="next-steps"></a>后续步骤

- [了解星型架构及其对 Power BI 的重要性](guidance/star-schema.md)
- [多对多关系指南](guidance/relationships-many-to-many.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)

---
title: Power BI Desktop 中的 Analysis Services 多维数据
description: Power BI Desktop 中的 SQL Server Analysis Services (SSAS) 多维数据
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eac1134ff12025d05cd59e86b7538cde58e3a2ee
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83287685"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>在 Power BI Desktop 中连接到 SSAS 多维模型

使用 Power BI Desktop，你可以访问 SSAS 多维模型，通常称为 SSAS MD   。

若要连接到 SSAS MD 数据库，请选择“获取数据”，再选择“数据库” > “SQL Server Analysis Services 数据库”，然后选择“连接”     ：

![SQL Server Analysis Services (SSAS) 数据库，“获取数据”对话框，Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Power BI 服务和 Power BI Desktop 都支持实时连接模式下的 SSAS 多维模型。 你可以将实时模式下使用 SSAS 多维模型的报表发布和上传到 Power BI 服务  。

## <a name="capabilities-and-features-of-ssas-md"></a>SSAS MD 的功能和特性

下面的部分将介绍 Power BI 和 SSAS MD 连接的功能和特性。

### <a name="tabular-metadata-of-multidimensional-models"></a>多维模型的表格元数据

下表显示多维对象与返回到 Power BI Desktop 中的表格元数据之间的对应关系。 Power BI 查询表格元数据的模型。 在创建可视化效果（如表、矩阵、图表或切片器）时，基于返回的元数据，Power BI Desktop 对 SSAS 运行适当的 DAX 查询。

| BISM 多维对象 | 表格元数据 |
| --- | --- |
| 多维数据集 |模型 |
| 多维数据集维度 |表 |
| 维度属性（键）、名称 |列 |
| 度量值组 |表 |
| 度量值 |度量值 |
| 没有关联度量值组的度量值 |名为 *度量值* 的表内 |
| 度量值组 -> 多维数据集维度关系 |关系 |
| 透视 |透视 |
| KPI |KPI |
| 用户/父子层次结构 |层次结构 |

### <a name="measures-measure-groups-and-kpis"></a>度量值、度量值组和 KPI

多维数据集中的度量值组显示为“字段”窗格中旁边带有 sigma (∑) 的表  。 没有关联度量值组的计算度量值已归入到表格元数据中名为度量值的特殊表中  。

为了帮助简化多维模型中的复杂模型，你可以在多维数据集中定义一组度量值或 KPI，使其位于显示文件夹内  。 Power BI 可以识别表格元数据中的显示文件夹，并在显示文件夹内显示度量值和 KPI。 多维数据库中的 KPI 支持“值”、“目标”、“状态图形”和“趋势图形”     。

### <a name="dimension-attribute-type"></a>维度属性类型

多维模型还支持具有特定维度属性类型的关联维度属性。 例如，“地理位置”维度中的“城市”、“州-省”、“国家/地区”和“邮政编码”维度属性，都有与之相关联的适当地理位置类型，会在表格元数据中公开      。 Power BI 识别元数据，可使你创建地图可视化效果。 通过 Power BI 中与“字段”窗格中的元素相邻的地图图标，你可以识别这些关联   。

如果提供包含图像 URL（统一资源定位器）的字段，Power BI 还可以呈现图像。 你可以在 SQL Server Data Tools 中（或在 Power BI 中）将这些字段指定为 ImageURL 类型  。 然后通过表格元数据将此类型信息提供给 Power BI。 然后，Power BI 可从 URL 检索这些图像，并将其显示在视觉对象中。

### <a name="parent-child-hierarchies"></a>父子层次结构

多维模型支持父子层次结构，在表格元数据中以层次结构展示  。 父子层次结构的每一级别都将公开为表格元数据中的隐藏列。 父子维度的键属性不在表格元数据内显示。

### <a name="dimension-calculated-members"></a>维度计算成员

多维模型支持创建各种类型的 *计算成员* 。 两种最常见的计算成员类型为：

* 计算成员位于属性层次结构上，而且与“所有”  不同级
* 用户层次结构上的计算成员

多维模型公开“属性层次结构上的计算成员”作为列的值  。 公开此类型的计算成员时，有以下几个其他选项和约束：

* 维度属性可能有一个可选的 UnknownMember  。

* 包含计算成员的属性不能成为该维度的键属性，除非它是该维度仅有的一个属性。

* 包含计算成员的属性不能成为父子属性。

用户层次结构的计算成员不在 Power BI 中公开。 你可以改为连接到包含用户层次结构上的计算成员的多维数据集。 但是，如果计算成员不符合前面的项目符号列表中提到的约束，你将无法看到这些计算成员。

### <a name="security"></a>安全性

通过角色方法，多维模型支持维度和单元格级别的安全性  。 当用户使用 Power BI 连接到多维数据集时，系统将对用户进行身份验证并评估其是否具有适当的权限。 如果用户应用了维度安全性，Power BI 中的用户将无法看到相应的维度成员  。 但如果用户在某些单元格受到限制的情况下定义了单元格安全性权限，则该用户无法使用 Power BI 连接到多维数据集  。

## <a name="considerations-and-limitations"></a>注意事项和限制

使用 SSAS MD 具有某些特定限制：

* 只有 Enterprise 版和 BI 版的 SQL Server 2014 支持实时连接。 对于标准版 SQL Server，实时连接需要 SQL Server 2016 或更高版本。

* 操作和命名集不会向 Power BI 公开   。 若要创建视觉对象和报表，仍然可以连接到包含操作或命名集的多维数据集。

* 当 Power BI 显示 SSAS 模型的元数据时，有时无法从模型中检索数据。 如果你安装的是 32 位版本而非 64 位版本的 MSOLAP 提供程序，则可能会发生这种情况。 安装 64 位版本可以解决此问题。

* 在创作与 SSAS 多维模型实时连接的报表时，无法创建报表级别度量值  。 唯一可用的度量值是 MD 模型中定义的度量值。

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Power BI Desktop 中支持的 SSAS MD 功能

此版本的 SSAS MD 支持使用以下元素。 有关这些功能的详细信息，请参阅[了解多维模型的 Power View](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014)。

* 默认成员
* “维度属性”
* 维度属性类型
* 维度计算成员必须满足以下条件：
  * 必须是单个真实成员（维度具有多个属性时）；
  * 除非维度计算成员是仅有的属性，否则不能成为维度的键属性；
  * 不能是父-子属性。
* 维度安全性
* 显示文件夹
* 层次结构
* ImageUrls
* KPI
* KPI 趋势
* 度量值（有或没有度量值组）
* 作为变体的度量值

## <a name="troubleshooting"></a>故障排除

以下列表介绍了连接到 SQL Server Analysis Services (SSAS) 时出现的所有已知问题。

* **错误：无法加载模型架构** - 当用户连接到 Analysis Services 而无法访问数据库/多维数据集时，通常会出现此错误。

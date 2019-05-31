---
title: Power BI Desktop 中的 Analysis Services 多维数据
description: Power BI Desktop 中的 Analysis Services 多维数据
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7a25a9cc220dcb9f4620b7fb77e6bac264a47256
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514743"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>连接到 Power BI Desktop 中的 SSAS 多维模型
使用 Power BI Desktop，你可以访问 **SSAS 多维模型**，通常称为 **SSAS MD**。

要连接到 SSAS MD 数据库，请选择“获取数据”&gt;“数据库”&gt;“SQL Server Analysis Services 数据库”，如下图所示：  

![](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

实时连接模式下的 **SSAS 多维模型**在 Power BI服务和 Power BI Desktop 中均受支持。 你可以将实时模式下使用**SSAS 多维模型**的报表发布和上传到 Power BI 服务。

## <a name="capabilities-and-features-of-ssas-md"></a>SSAS MD 的功能和特性
下面的部分将介绍 Power BI 和 SSAS MD 连接的功能和特性。

### <a name="tabular-metadata-of-multidimensional-models"></a>多维模型的表格元数据
下表显示多维对象与返回到 Power BI Desktop 中的表格元数据之间的对应关系。 Power BI 查询表格元数据的模式，并在你创建可视化对象（如表、矩阵、图表或切片器）时，基于返回的元数据对 Analysis Services 运行适当的 DAX 查询。

| BISM 多维对象 | 表格元数据 |
| --- | --- |
| 多维数据集 |模型 |
| 多维数据集维度 |表格 |
| 维度属性（密钥）、名称 |列 |
| 度量值组 |表 |
| 度量值 |度量值 |
| 没有关联度量值组的度量值 |名为 *度量值* 的表内 |
| 度量值组 -> 多维数据集维度关系 |关系 |
| 透视 |透视 |
| KPI |KPI |
| 用户/父子层次结构 |层次结构 |

### <a name="measures-measure-groups-and-kpis"></a>度量值、度量值组和 KPI
多维数据集中的度量值组在 Power BI 中公开为表，其在**字段**窗格中旁边带有 ∑ 符号。 没有关联度量值组的计算度量值已归入到表格元数据中名为 *度量值* 的特殊表中。

在多维模型中，你可以在多维数据集中定义一组度量值或 KPI，使其位于 *显示文件夹* 内，这有助于简化复杂的模型。 Power BI 将识别表格元数据中的显示文件夹，并在显示文件夹内显示度量值和 KPI。 多维数据库中的 KPI 支持“值”、“目标”、“状态图形”和“趋势图形”     。

### <a name="dimension-attribute-type"></a>维度属性类型
多维模型还支持具有特定维度属性类型的关联维度属性。 例如，“地理位置”维度中的“城市”、“州-省”、“国家/地区”和“邮政编码”维度属性，都有与之相关联的适当地理位置类型，会在表格元数据中公开      。 Power BI 识别元数据，可使你创建地图可视化效果。 通过 Power BI 中与 **字段** 窗格中的元素相邻的 *地图* 图标，你可以识别这些关联。

当你提供包含图像 URL（统一资源定位符）的字段时，Power BI 还可以呈现图像。 在 SQL Server Data Tools 中（或随后在 Power BI 中），你可以将这些字段指定为 *ImageURL* 类型，其类型信息将在表格元数据中提供给 Power BI。 然后，Power BI 可从 URL 检索这些图像，并将其显示在视觉对象中。

### <a name="parent-child-hierarchies"></a>父子层次结构
多维模型支持父子层次结构，在表格元数据中以 *层次结构* 展示。 父子层次结构的每一级别都将公开为表格元数据中的隐藏列。 父子维度的关键属性不会在表格元数据中公开。

### <a name="dimension-calculated-members"></a>维度计算成员
多维模型支持创建各种类型的 *计算成员* 。 两种最常见的计算成员类型如下所示：

* 计算成员位于属性层次结构上，而且与 *所有* 不同级
* 用户层次结构上的计算成员

多维模型公开“属性层次结构上的计算成员”作为列的值  。 在公开此类型的计算成员时，有以下几个其他选项和约束：

* 维度属性可能有一个可选的 *UnknownMember*
* 包含计算成员的属性不能成为该维度的关键属性，除非它是该维度的唯一属性
* 包含计算成员的属性不能成为父子属性

用户层次结构的计算成员不在 Power BI 中公开。 相反，你将能够连接到用户层次结构上包含计算成员的多维数据集，但是，如果它们不能满足上文中项目符号列表中所述的约束，你将无法查看计算成员。

### <a name="security"></a>安全性
通过 *角色* 方法，多维模型支持维度和单元格级别的安全性。 当使用 Power BI 链接到多维数据集时，将对你进行适当权限的身份验证和评估。 当用户应用了 *维度安全性* 时，Power BI 中的用户将无法看到相应的维度成员。 但是，当用户定义了 *单元格安全性* 权限时，某些单元格将受到限制，并且该用户无法使用 Power BI 连接到多维数据集。

## <a name="considerations-and-limitations"></a>注意事项和限制
使用 **SSAS MD** 具有某些特定限制：

* 服务器必须运行 SQL Server 2012 SP1 CU4 或更高版本的 Analysis Services，才能使 Power BI Desktop SSAS MD 连接器正常工作
* *操作* 和 *命名集* 不会公开到 Power BI，但你仍然可以连接到包含 *操作* 或 *命名集* 的多维数据集，并创建视觉对象和报表。
* 可能会遇到以下问题：Power BI 显示 SSAS 模型元数据，但无法从模型检索数据。 如果系统上安装的 MSOLAP 提供程序是 32 位版本，而不是 64 位版本，则会出现此问题。 安装 64 位版本可以解决此问题。
* 在创作与 SSAS 多维模型实时连接的报表时，无法创建“报表级别”度量值。 唯一可用的度量值是 MD 模型中定义的度量值。

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Power BI Desktop 中支持的 SSAS MD 功能
Power BI Desktop 中支持以下 SSAS MD 功能：

* 在此版本的 **SSAS MD** 支持以下元素消耗（你可以获取有关这些功能的[详细信息](https://msdn.microsoft.com/library/jj969574.aspx)）：
  * 显示文件夹
  * KPI 趋势
  * 默认成员
  * 维度属性
  * 维度计算成员（维度具有多个属性时，必须是单个的真实成员。它不能是维度的关键属性，除非它是唯一的属性，并且它不能是父子属性）
  * 维度属性类型
  * 层次结构
  * 度量值（有或没有度量值组）
  * 度量值作为变量
  * KPI
  * ImageUrls
  * 维度安全性

## <a name="troubleshooting"></a>故障排除 
以下列表介绍了连接到 SQL Server Analysis Services (SSAS) 时出现的所有已知问题。 

* **错误：无法加载模型架构** - 当用户连接到 Analysis Services 而无法访问数据库/多维数据集时，通常会出现此错误。

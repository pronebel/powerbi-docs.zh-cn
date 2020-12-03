---
title: Power BI Desktop 中的查询折叠指南
description: 关于在 Power BI Desktop 中实现 Power Query 查询折叠的指南。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/09/2019
ms.openlocfilehash: 5e2ec32f3eeaff224256f0a84d2a5c23d3e882a5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419305"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的查询折叠指南

本文面向在 Power BI Desktop 中开发模型的数据建模人员。 它提供了关于何时以及如何实现 Power Query 查询折叠的最佳做法指南。

查询折叠是 Power Query 查询的一项功能，可生成单个查询语句以检索和转换源数据  。 有关详细信息，请参阅 [Power Query 查询折叠](/power-query/power-query-folding)。

## <a name="guidance"></a>指南

查询折叠指南因模型模式而异。

对于 DirectQuery 或 Dual 存储模式表，Power Query 查询必须实现查询折叠   。

对于导入表，可能实现查询折叠  。 当查询基于关系源，且可以构造单个 SELECT 语句时，可通过确保发生查询折叠来实现最佳数据刷新性能  。 如果仍需要 Power Query 糅合引擎来处理转换，则应努力减少所需的工作，尤其是对于大型数据集。

下面的项目列表提供了具体指导。

- **尽可能多地委托处理数据源**：如果无法折叠 Power Query 查询的所有步骤，请查找阻止查询折叠的步骤。 尽可能将后续步骤按顺序提前，以便将其纳入查询折叠。 请注意，Power Query 糅合引擎是智能引擎，它也许会在生成源查询时重新排列查询步骤。

    对于关系数据源，如果可以在单个 SELECT 语句中（或在存储过程的过程逻辑中）实现阻止查询折叠的步骤，请考虑使用本机 SQL 查询，如下所述。

- **使用本机 SQL 查询**：虽然 Power Query 查询可从关系源中检索数据，但对某些源而言，可以使用本机 SQL 查询。 该查询实际上可以是任何有效的语句，包括存储过程的执行。 如果该语句产生多个结果集，则仅返回第一个。 可以在语句中声明参数，建议使用 [ Value.NativeQuery](/powerquery-m/value-nativequery) M 函数。 此函数旨在安全且方便地传递参数值。 必须了解的是，Power Query 糅合引擎无法折叠后续的查询步骤，因此应在本机查询语句中包括所有（或尽可能多的）转换逻辑。

    使用本机 SQL 查询时，需要牢记两个重要注意事项：

    - 对于 DirectQuery 模型表，查询必须是 SELECT 语句，并且不能使用公用表表达式 (CTE) 或存储过程。
    - 增量刷新无法使用本机 SQL 查询。 因此，它将强制 Power Query 糅合引擎检索所有源行，然后应用筛选器来确定增量更改。

    > [!IMPORTANT]
    > 本机 SQL 查询可执行的操作远不止检索数据。 任何有效的语句都可以执行（可能多次执行），包括修改或删除数据的语句。 务必应用最小特权原则，以确保用于访问数据库的帐户仅具有对所需数据的读取权限。

- **准备和转换源中的数据**：如果确定某些 Power Query 查询步骤无法折叠，也许可以在数据源中应用转换。 可通过编写逻辑转换源数据的数据库视图来实现转换。 或者，在 Power BI 查询数据之前，通过物理方式准备和具体化数据。 关系数据仓库是准备好的数据的一个极佳例子，通常由预先集成的组织数据源组成。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- Power Query [查询折叠](/power-query/power-query-folding)概念文章
- [Power BI Premium 中的增量刷新](../admin/service-premium-incremental-refresh.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)

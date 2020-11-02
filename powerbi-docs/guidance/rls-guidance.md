---
title: Power BI Desktop 中的行级别安全性 (RLS) 指南
description: 通过 Power BI Desktop 在数据模型中执行行级别安全性 (RLS) 的指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 644e4499a335f18febadf33c371bd15e01499701
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349612"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的行级别安全性 (RLS) 指南

本文面向使用 Power BI Desktop 的数据建模者。 它介绍了在数据模型中执行行级别安全性 (RLS) 的良好设计实践。

务必要了解 RLS 筛选器表行。 它们无法配置为限制对模型对象（包括表、列或度量值）的访问。

> [!NOTE]
> 本文不介绍 RLS 或其设置方式。 有关详细信息，请参阅[使用 Power BI Desktop 行级别安全性 (RLS) 限制数据访问](../create-reports/desktop-rls.md)。
>
> 此外，在通过 Azure Analysis Services 或 SQL Server Analysis Services 与外部托管模型的实时连接中执行 RLS 也与本文无关。 在这些情况下，RLS 由 Analysis Services 执行。 当使用单一登录 (SSO) 连接 Power BI 时，Analysis Services 将执行 RLS（除非该帐户具有管理员权限）。

## <a name="create-roles"></a>创建角色

可以创建多个角色。 当你考虑单个报表用户的权限需要时，请尽量创建单个角色来授予所有这些权限，而不是将报表用户设计为一个具有多个角色的成员。 这是因为报表用户可以通过使用其用户帐户直接映射到多个角色，也可以通过安全组成员身份间接映射到多个角色。 多个角色映射可能会导致意外结果。

将报表用户分配到多个角色时，RLS 筛选器将成为累加筛选器。 这意味着报表用户可以查看代表这些筛选器联合的表行。 此外，在某些情况下，不能保证报表用户看不到表中的行。 因此，与应用于 SQL Server 数据库对象（和其他权限模型）的权限不同，“拒绝后总是拒绝”原则不适用。

请考虑一个具有两个角色的模型：名为“员工”的第一个角色使用以下规则表达式限制对所有“工资单”表行的访问：

```dax
FALSE()
```

> [!NOTE]
> 如果规则的表达式的计算结果为“false”，则该规则将不返回表行。

不过，另一个名为“经理”的角色允许使用以下规则表达式访问所有“工资单”表行：

```dax
TRUE()
```

注意：如果报表用户映射到这两个角色，他们将看到所有“工资”表行。

## <a name="optimize-rls"></a>优化 RLS

RLS 的工作方式是自动将筛选器应用于每个 DAX 查询，这些筛选器可能会对查询性能产生负面影响。 因此，高效的 RLS 归结为良好的模型设计。 必须遵循以下文章中所述的模型设计指南：

- [了解星型架构及其对 Power BI 的重要性](star-schema.md)
- [Power BI 指南文档](./index.yml)中的所有关系指南文章

通常，在维度类型表上而不是在事实类型表上实施 RLS 筛选器通常更有效。 此外，依靠设计良好的关系来确保 RLS 筛选器传播到其他模型表。 因此，当模型关系可以获得相同的结果时，请避免使用 [LOOKUPVALUE](/dax/lookupvalue-function-dax) DAX 函数。

如果对 DirectQuery 表执行 RLS 筛选器，并且与其他 DirectQuery 表存在关系，请务必优化源数据库。 它可能涉及设计适当的索引或使用持久化计算列。 有关详细信息，请参阅 [Power BI Desktop 中的 DirectQuery 模型指南](directquery-model-guidance.md)。

### <a name="measure-rls-impact"></a>衡量 RLS 影响

可以使用[性能分析器](../create-reports/desktop-performance-analyzer.md)来衡量 Power BI Desktop 中的 RLS 筛选器的性能影响。 首先，确定在未执行 RLS 的情况下报表视觉对象查询的持续时间。 然后，使用“建模”功能区选项卡上的“View As”命令来执行 RLS，并确定和比较查询持续时间。

## <a name="configure-role-mappings"></a>配置角色映射

发布到 Power BI 后，必须将成员映射到数据集角色。 只有数据集所有者或工作区管理员才能将成员添加到角色。 有关详细信息，请参阅 [Power BI 行级别安全性 (RLS)（管理模型上的安全性）](../admin/service-admin-rls.md#manage-security-on-your-model)。

成员可以是用户帐户或安全组。 建议尽可能将安全组映射到数据集角色。 它涉及在 Azure Active Directory 中管理安全组成员身份。 它可能会将任务委派给网络管理员。

## <a name="validate-roles"></a>验证角色

测试每个角色以确保它正确筛选模型。 可通过使用“建模”功能区选项卡上的“View As”命令，轻松完成此操作。

如果模型具有使用 [USERNAME](/dax/username-function-dax) DAX 函数的动态规则，请确保测试预期值和意外值。 嵌入 Power BI 内容时（特别是使用[应用拥有数据](../developer/embedded/embedding.md#embedding-for-your-customers)方案），应用逻辑可以将任何值作为有效的标识用户名进行传递。 尽可能确保筛选器中生成的意外值或恶意值不返回任何行。

请考虑使用一个 Power BI Embedded 示例，其中应用将用户的工作角色作为有效用户名传递：它可以是“经理”或“员工”。 经理可以查看所有行，但员工只能查看“Type”列值为“Internal”的行。

定义了以下规则表达式：

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

此规则表达式的问题是：除“Worker”之外的所有值都将返回所有表行。 因此，意外值（如“Wrker”）会无意中返回所有表行。 因此，更安全的做法是编写表达式来测试每个预期值。 在下面改进的规则表达式中，意外值将导致表不返回任何行。

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>设计部分 RLS

有时，计算需要不受 RLS 筛选器约束的值。 例如，报表可能需要显示报表用户销售区域的收入与所有收入的比率。

虽然 DAX 表达式不能替代 RLS（事实上，它甚至无法确定是否执行了 RLS），但你可以使用摘要模型表。 查询摘要模型表以检索“所有区域”的收入，它不受任何 RLS 筛选器的约束。

让我们看看如何实现此设计要求。 首先，请考虑以下模型设计：

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="将显示模型关系图。下面的段落对此进行了介绍。":::

该模型由四个表组成：

- “Salesperson”表为每个销售人员存储一行。 它包含“EmailAddress”列，用于存储每个销售人员的电子邮件地址。 此表处于隐藏状态。
- “Sales”表为每个订单存储一行。 它包括“占所有区域收入的 %”度量值，该度量值旨在返回报表用户所在区域的收入与所有区域收入的比率。
- “Date”表为每个日期存储一行，并允许按年月进行筛选和分组。
- “SalesRevenueSummary”为计算表。 它存储每个订单日期的总收入。 此表处于隐藏状态。

以下表达式定义“SalesRevenueSummary”计算表：

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> [聚合表](../transform-model/desktop-aggregations.md)可以实现相同的设计要求。

以下 RLS 规则适用于“Salesperson”表：

```dax
[EmailAddress] = USERNAME()
```

下表介绍了这三种模型关系：

|关系|说明|
|---------|---------|
|![流程图终止符 1。](media/common/icon-01-red-30x30.png)|“Salesperson”与“Sales”表之间存在多对多关系。 RLS 规则通过使用 [USERNAME](/dax/username-function-dax) DAX 函数，筛选隐藏“Salesperson”表的“EmailAddress”列。 “Region”列值（针对报表用户）传播到“Sales”表。|
|![流程图终止符 2。](media/common/icon-02-red-30x30.png)|“Date”和“Sales”表之间存在一对多关系。|
|![流程图终止符 3。](media/common/icon-03-red-30x30.png)|“Date”和“SalesRevenueSummary”表之间存在一对多关系。|

以下表达式定义“占所有区域收入的 %”度量值：

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> 请注意避免泄露敏感信息。 如果此示例中只有两个区域，则报表用户可以计算其他区域的收入。

## <a name="avoid-using-rls"></a>避免使用 RLS

如果有必要，请避免使用 RLS。 如果你只有少量应用静态筛选器的简单 RLS 规则，请考虑发布多个数据集。 所有数据集都不定义角色，因为每个数据集都包含特定报表用户的数据，这些用户具有相同的数据权限。 然后，为每个受众创建一个工作区，并为工作区或应用分配访问权限。

例如，只有两个销售区域的公司决定将每个销售区域的数据集发布到不同工作区。 这些数据集不执行 RLS。 但它们确实使用[查询参数](/power-query/power-query-query-parameters)来筛选源数据。 这样一来，同一模型将发布到每个工作区（它们只是有不同的数据集参数值）。 只需向销售人员分配一个工作区（或发布的应用）的访问权限。

避免使用 RLS 有以下几点优势：

- 提高查询性能：由于筛选器更少，因此可以提高性能。
- 模型较小：虽然会生成更多的模型，但它们的大小较小。 较小的模型可以改进查询和数据刷新响应能力，尤其是在承载容量在资源方面面临压力时。 此外，将模型大小保持在容量限制的范围内会更容易。 最后，可以更轻松地跨不同容量平衡工作负荷，因为你可以在不同容量上创建工作区，也可以将工作区移动到不同的容量。
- 其他功能：可以使用不能与 RLS 结合使用的 Power BI 功能，如[发布到 Web](../collaborate-share/service-publish-to-web.md)。

但是，避免使用 RLS 也存在一些缺点：

- 多个工作区：每个报表用户受众都需要一个工作区。 如果发布应用，则也意味着每个报表用户受众都有一个应用。
- 内容重复：必须在每个工作区中创建报表和仪表板。 它需要额外的精力和时间来设置和维护。
- 高特权用户：高特权用户（属于多个报表用户受众）无法查看数据的合并视图。 他们需要打开多个报表（来自不同的工作区或应用）。

## <a name="troubleshoot-rls"></a>RLS 排除故障

如果 RLS 产生意外结果，请检查是否存在以下问题：

- 在列映射和筛选器方向方面，模型表之间存在不正确的关系。
- “双向应用安全性筛选器”关系属性未正确设置。 有关详细信息，请参阅[双向关系指南](relationships-bidirectional-filtering.md)。
- 表中不包含数据。
- 将不正确的值加载到表中。
- 用户映射到多个角色。
- 模型包含聚合表，而 RLS 规则未一致筛选聚合和详细信息。 有关详细信息，请参阅[在 Power BI Desktop 中使用聚合（聚合 RLS）](../transform-model/desktop-aggregations.md#rls-for-aggregations)。

当特定用户看不到任何数据时，可能是因为未存储其 UPN 或输入不正确。 这种情况可能会突然发生，因为他们的用户帐户由于名称更改而发生了变更。

> [!TIP]
> 出于测试目的，请添加一个返回 [USERNAME](/dax/username-function-dax) DAX 函数的度量值。 可以将其命名为类似于“我是谁”的名称。 然后，将度量值添加到报表中的卡片视觉对象，并将其发布到 Power BI。

当某个特定用户可以看到所有数据时，他们可以直接在工作区中访问报表，并且他们是数据集所有者。 仅在以下情况下执行 RLS：

- 报表在应用中打开。
- 报表在工作区中打开，且用户映射到[查看者角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI 行级别安全性 (RLS)](../admin/service-admin-rls.md)
- [使用 Power BI Desktop 行级别安全性 (RLS) 限制数据访问](../create-reports/desktop-rls.md)
- [Power BI Desktop 中的模型关系](../transform-model/desktop-relationships-understand.md)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

---
title: 对 Power BI 已嵌入内容使用行级别安全性
description: 了解在应用程序中嵌入 Power BI 内容所需的步骤。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 09/18/2018
ms.openlocfilehash: 60061d781542f8b5a3ef67a75e61d902459d4963
ms.sourcegitcommit: ded8b85276e7eda166d6e67f72d1fe3d5e234745
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/21/2018
ms.locfileid: "46506767"
---
# <a name="use-row-level-security-with-power-bi-embedded-content"></a>对 Power BI 已嵌入内容使用行级别安全性

行级安全性 (RLS) 可用于限制用户对仪表板、磁贴、报表和数据集中数据的访问。 多个不同的用户都可以在查看不同的数据时处理这些相同的项目。 嵌入支持 RLS。

如果要为非 Power BI 用户（应用拥有数据）嵌入（通常是 ISV 方案），那本文很适合你！ 需要配置用于用户和角色的帐户的嵌入令牌。 继续阅读以了解如何执行此操作。

如果要嵌入到组织内的 Power BI 用户（用户拥有数据）中，RLS 的工作方式与它直接在 Power BI 服务中执行的工作方式相同。 无需在应用程序中进行其他操作。 有关详细信息，请参阅 [Power BI 行级别安全性 (RLS)](../service-admin-rls.md)。

![涉及行级别安全性的项。](media/embedded-row-level-security/powerbi-embedded-rls-components.png)

要利用 RLS，务必要了解三个主要概念：用户、角色和规则。 让我们仔细了解每个概念：

用户 – 查看项目（仪表板、磁贴、报表或数据集）的最终用户。 在 Power BI Embedded 中，用户由嵌入令牌中的 username 属性进行标识。

**角色** – 用户属于角色。 角色是规则的容器，并可以命名为“销售经理”或“销售代表”之类的名称。可以在 Power BI Desktop 中创建角色。 有关详细信息，请参阅 [Power BI Desktop 行级别安全性 (RLS)](../desktop-rls.md)。

**规则** – 角色具有规则，并且这些规则要应用于数据的实际筛选器。 这可以是“Country = USA”这样简单的规则，或者是更动态的规则。
在本文的剩余部分中，有编写 RLS 的示例，然后在嵌入应用程序中使用该示例。 我们的示例使用[零售分析示例](http://go.microsoft.com/fwlink/?LinkID=780547) PBIX 文件。

![报表示例](media/embedded-row-level-security/powerbi-embedded-report-example.png)

## <a name="adding-roles-with-power-bi-desktop"></a>使用 Power BI Desktop 添加角色

我们的零售分析示例显示了零售链中所有商店的销售额。 不借助 RLS，无论哪位地区经理登录和查看报表，他们都将看到相同的数据。 高级管理人员已经确定每位地区经理只应该看到他们所管理的商店的销售额，要实现此目的，我们可以使用 RLS。

RLS 在 Power BI Desktop 中进行编写。 当打开数据集和报表时，我们可以切换到关系图视图来查看架构：

![Power BI Desktop 中的关系图视图](media/embedded-row-level-security/powerbi-embedded-schema.png)

下面介绍了此架构的几个注意事项：

* 所有度量值（例如，总销售额）均存储在“销售”事实数据表中。
* 有四个其他的相关维度表：“项目”、“时间”、“商店”和“地区”。
* 关系行上的箭头指示筛选器从一个表流向另一个表的方式。 例如，如果筛选器位于“时间[日期]”上，在当前架构中，它将仅筛选出“销售”表中的值。 由于关系行上的所有箭头均指向“销售”表，不会改变，因此，其他表不会受此筛选器的影响。
* “地区”表指示每个区的经理：
  
    ![“地区”表中的行](media/embedded-row-level-security/powerbi-embedded-district-table.png)

根据此架构，如果我们将筛选器应用于“地区”表中的“地区经理”列，并且，如果该筛选器匹配查看报表的用户，筛选器会筛选出“存储”和“销售”表，从而仅为该地区经理显示数据。

下面介绍如何操作：

1. 在“建模”选项卡中，选择“管理角色”。

    ![Power BI Desktop 中的“建模”选项卡](media/embedded-row-level-security/powerbi-embedded-manage-roles.png)
2. 创建名为“经理”的新角色。

    ![创建新角色](media/embedded-row-level-security/powerbi-embedded-new-role.png)
3. 在“地区”表中，输入以下 DAX 表达式：[District Manager] = USERNAME()。

    ![RLS 规则的 DAX 语句](media/embedded-row-level-security/powerbi-embedded-new-role-dax.png)
4. 为确保这些规则有效，请在“建模”选项卡上，选择“以角色身份查看”，然后选择刚刚创建的“经理”角色，以及“其他用户”。 输入 AndrewMa 作为用户。

    ![“以角色身份查看”对话框](media/embedded-row-level-security/powerbi-embedded-new-role-view.png)

    报表显示数据，就像以 AndrewMa 的身份登录那样。

应用该筛选器（我们此处进行的操作）筛选出“地区”、“商店”和“销售”表中的所有记录。 但是，由于“销售”和“时间”与“销售”和“项目”之间关系的筛选器方向，不会筛选出“项目”和“时间”表。 要了解有关双向交叉筛选的详细信息，请下载 [SQL Server Analysis Services 2016 和 Power BI Desktop 中的双向交叉筛选](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)白皮书。

## <a name="applying-user-and-role-to-an-embed-token"></a>将用户和角色应用于签入令牌

现在，已经配置了 Power BI Desktop 角色，需要在应用程序中进行某些操作才能利用这些角色。

用户由应用程序进行身份验证和授权，而嵌入令牌用于授予用户对特定 Power BI Embedded 报表的访问权限。 Power BI Embedded 不具备有关用户身份的任何特定信息。 要使 RLS 正常工作，需要以标识的形式，将一些其他上下文作为嵌入令牌的一部分进行传递。 这通过 [Embed Token](https://docs.microsoft.com/rest/api/power-bi/embedtoken)（嵌入令牌）API 来实现。

API 接受具有相关数据集指示的标识列表。 要使 RLS 正常工作，需要将以下内容作为标识的一部分进行传递。

* **用户名（必填）** – 这是一个字符串，可用于在应用 RLS 规则时帮助标识用户。 只能列出单个用户。 可以使用 ASCII 字符创建用户名。
* **角色（必填）** – 一个字符串，包含在应用“行级别安全性”规则时要选择的角色。 如果传递多个角色，则这些角色应该作为字符串数组传递。
* **数据集（必需）**– 适用于要嵌入的项目的数据集。

可以通过使用 PowerBIClient.Reports 上的 GenerateTokenInGroup 创建嵌入令牌。

例如，可以更改 [PowerBIEmbedded_AppOwnsData](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data) 示例。 可将 *Home\HomeController.cs 76 和 77 行*从：

```csharp
// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");

var tokenResponse = await client.Reports.GenerateTokenInGroupAsync(GroupId, report.Id, generateTokenRequestParameters);
```

更新为

```csharp
var generateTokenRequestParameters = new GenerateTokenRequest("View", null, identities: new List<EffectiveIdentity> { new EffectiveIdentity(username: "username", roles: new List<string> { "roleA", "roleB" }, datasets: new List<string> { "datasetId" }) });

var tokenResponse = await client.Reports.GenerateTokenInGroupAsync("groupId", "reportId", generateTokenRequestParameters);
```

如果调用的是 REST API，更新的 API 现在接受包含用户名、字符串角色列表和字符串数据集列表的名为 identities 的其他 JSON 数组，例如：

```json
{
    "accessLevel": "View",
    "identities": [
        {
            "username": "EffectiveIdentity",
            "roles": [ "Role1", "Role2" ],
            "datasets": [ "fe0a1aeb-f6a4-4b27-a2d3-b5df3bb28bdc" ]
        }
    ]
}
```

现在，将所有组合在一起后，当有人登录应用程序查看此项目时，他们将只能查看允许他们查看的数据，正如我们的行级别安全性所定义的那样。

## <a name="working-with-analysis-services-live-connections"></a>使用 Analysis Services 实时连接

行级别安全性可用于本地服务器的 Analysis Services 实时连接。 使用这种类型的连接时，应该了解一些具体的概念。

为用户名属性提供的有效标识必须是具有 Analysis Services 服务器操作权限的 Windows 用户。

**本地数据网关配置**

在使用 Analysis Services 实时连接时，将使用[本地数据网关](../service-gateway-onprem.md)。 当生成嵌入令牌时，如果列出标识，则主帐户需要列为网关的管理员。 如果主帐户未列出，则行级别安全性不会正确应用于数据属性。 网关的非管理员可以提供角色，但必须为有效标识指定其自己的用户名。

**使用角色**

可以在嵌入令牌中通过标识提供角色。 如果没有提供角色，则提供的用户名可用于解析相关角色。

**使用 CustomData 功能**

CustomData 功能允许使用 CustomData 连接字符串属性传递自定义文本，供 AS（通过 CUSTOMDATA() 函数）使用。
这种方法可以用作自定义数据消耗的替代方法。
可以在角色 DAX 查询中使用它，并且可以在度量值 DAX 查询中使用，而无需任何角色。
CustomData 功能属于令牌生成功能，适用于以下项目：仪表板、报表和磁贴。 仪表板可以具有多个 CustomData 标识（每个磁贴/模型一个）。

> [!NOTE]
> CustomData 功能仅适用于驻留在 Azure Analysis Services 中的模型，并且仅适用于实时模式。 与用户和角色不同的是，自定义数据功能不能在 .pbix 文件中设置。 使用自定义数据功能生成令牌时，必须拥有用户名。

**CustomData SDK 添加件**

CustomData 字符串属性已添加到令牌生成方案中的有效标识。

        [JsonProperty(PropertyName = "customData")]
        public string CustomData { get; set; }

借助以下调用，可使用自定义数据创建标识：

        public EffectiveIdentity(string username, IList<string> datasets, IList<string> roles = null, string customData = null);

**CustomData SDK 用法**

如果要调用 REST API，则可以在每个标识中添加自定义数据，例如：

```json
{
    "accessLevel": "View",
    "identities": [
        {
            "username": "EffectiveIdentity",
            "roles": [ "Role1", "Role2" ],
            "customData": "MyCustomData",
            "datasets": [ "fe0a1aeb-f6a4-4b27-a2d3-b5df3bb28bdc" ]
        }
    ]
}
```

## <a name="considerations-and-limitations"></a>注意事项和限制

* 使用嵌入令牌时，在 Power BI 服务中向角色分配用户不会影响 RLS。
* 虽然 Power BI 服务不会将 RLS 设置应用于管理员或具有编辑权限的成员，当提供具有嵌入令牌的标识时，它将应用于数据。
* 本地服务器支持 Analysis Services 实时连接。
* Azure Analysis Services 实时连接支持按角色筛选。 可使用 CustomData 执行动态筛选。
* 如果基础数据集不需要 RLS，则 GenerateToken 请求不得包含有效的标识。
* 如果基础数据集是云模型（缓存的模型或 DirectQuery），则有效的标识必须至少包含一个角色，否则不会发生角色分配。
* 使用标识列表可以嵌入仪表板的多个标识标记。 对于其他所有项目，该列表包含单个标识。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

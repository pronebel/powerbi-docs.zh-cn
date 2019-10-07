---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: bbd9b38f30a4ca5cb8072496c9cacb635b03aa88
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71409349"
---
## <a name="faq"></a>常见问题解答
**问：** 如果我以前在 Power BI 服务中为数据集创建了角色和规则会怎么样？ 如果我不执行任何操作，它们是否仍将起作用？  
**答：** 否，视觉对象将不会正确呈现。 你需要重新创建 Power BI Desktop 中的角色和规则，然后发布到 Power BI 服务。

**问：** 我是否可以为 Analysis Services 数据源创建这些角色？  
**答：** 如果你将数据导入 Power BI Desktop 中，那么你就可以创建。 如果你正在使用实时连接，那么你将不能配置 Power BI 服务中的 RLS。 这是在 Analysis Services 模型内部部署中定义的。

**问：** 我能使用 RLS 限制用户可以访问的列或度量值吗？  
**答：** 不能，如果用户有权访问特定数据行，那么他们可以查看该行的所有数据列。

**问：** RLS 是否允许我隐藏详细的数据，但提供对在视觉对象中汇总的数据的访问权限？  
**答：** 不允许，你可以保护单个数据行，但用户始终可以查看详细信息或汇总的数据。

**问：** 我的数据源已经定义了安全角色（例如 SQL Server 角色或 SAP BW 角色）。 这些角色与 RLS 之间有什么关系？  
**答：** 答案取决于要导入数据还是使用 DirectQuery。 如果要将数据导入 Power BI 数据集中，则不会使用数据源中的安全角色。 在这种情况下，应定义 RLS 以对在 Power BI 中进行连接的用户强制实施安全规则。 如果使用 DirectQuery，则使用数据源中的安全角色。 当用户打开报表时，Power BI 将查询发送到基础数据源，该数据源根据用户的凭据将安全规则应用于数据。

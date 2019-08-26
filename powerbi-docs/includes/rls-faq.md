---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560944"
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


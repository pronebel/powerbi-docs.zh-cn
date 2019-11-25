---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: mblythe
ms.openlocfilehash: c658e683e86a899d45728220dee3706a0d617f0f
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284079"
---
## <a name="limitations"></a>限制

以下是云模型上有关行级安全性的当前限制列表。

* 如果你以前在 Power BI 服务中定义了角色和规则，则必须在 Power BI Desktop 中重新创建它们。

* 只能在使用 Power BI Desktop 创建的数据集上定义 RLS。 若想为使用 Excel 创建的数据集启用 RLS，首先必须将你的文件转换为 Power BI Desktop (PBIX) 文件。 [了解详细信息](../desktop-import-excel-workbooks.md)

* 仅支持 ETL 和 DirectQuery 连接。 在本地模型上处理到 Analysis Services 的实时连接。

## <a name="known-issues"></a>已知问题

有一个已知的问题，即当尝试从 Power BI Desktop 发布以前已发布过的报表时，将收到一个错误消息。 该场景如下所示。

1. Anna 有一个已发布到 Power BI 服务且已配置了 RLS 的数据集。

1. Anna 在 Power BI Desktop 中更新报表并重新发布。

1. Anna 收到一个错误。

解决方法  ：重新从 Power BI 服务中发布 Power BI Desktop 文件，直到此问题得到解决。 可以通过选择“获取数据”   > “文件”  来执行此操作。

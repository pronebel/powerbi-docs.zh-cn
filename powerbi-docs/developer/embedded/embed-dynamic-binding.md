---
title: 使用动态绑定将 Power BI 报表连接到数据集
description: 了解如何使用 Power BI 嵌入式分析中的动态绑定嵌入 Power BI 报表。
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 01/17/2021
ms.openlocfilehash: 0bc33ed37e389b42f5c27f8271cc461eb99e229a
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565814"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>使用动态绑定将报表连接到数据集 

在将报表连接到数据集时，可以使用动态绑定。 报表与数据集之间的连接也称为“绑定”。 如果绑定是快要嵌入时确定的，而不是之前预先确定的，则绑定被称为动态绑定。

使用动态绑定嵌入 Power BI 报表时，可以根据用户的凭据将同一报表连接到不同的数据集。

这意味着可使用一个报表显示不同的信息，具体由它连接到的数据集而定。 例如，显示零售销售值的报表可连接到不同的零售商数据集并生成不同的结果，具体由它连接到的零售商的数据集而定。

报表和数据集不需要驻留在同一个工作区中。 必须将两个工作区（包含报表的工作区和包含数据集的工作区）分配到一个[容量](azure-pbie-create-capacity.md)。

在嵌入过程中，请确保生成有足够权限的令牌，并调整配置对象 。

## <a name="generating-a-token-with-sufficient-permissions"></a>生成具有足够权限的令牌

两种嵌入方案（为组织嵌入内容和为客户嵌入内容）都支持动态绑定 。 下表描述了每种方案的注意事项。

|方案  |数据所有权  |令牌  |要求  |
|---------|---------|---------|---------|
|为组织嵌入内容    |用户拥有数据         |Power BI 用户的访问令牌         |使用 Azure AD 令牌的用户必须对所有项目拥有适当的权限。         |
|为客户嵌入内容     |应用拥有数据         |非 Power BI 用户的访问令牌         |必须包括报表和动态绑定数据集的权限。 使用[可为多个项生成嵌入令牌的 API](/rest/api/power-bi/embedtoken/generatetoken)生成支持多个项目的嵌入令牌。         |

## <a name="adjusting-the-config-object"></a>调整配置对象

为了使动态绑定生效，需要向配置对象添加 `datasetBinding`。 若要了解如何执行此操作，请参阅[将数据集动态绑定到报表](/javascript/api/overview/powerbi/bind-report-datasets)。 

## <a name="next-steps"></a>后续步骤

如果不熟悉如何在 Power BI 中嵌入内容，请查看以下教程，了解如何嵌入 Power BI 内容。

>[!div class="nextstepaction"]
>[为客户将 Power BI 内容嵌入应用程序](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[为组织将 Power BI 内容嵌入应用程序](embed-sample-for-your-organization.md)
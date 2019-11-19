---
title: 动态绑定
description: 了解如何使用动态绑定嵌入报表。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776228"
---
# <a name="dynamic-binding"></a>动态绑定

使用动态绑定，可以在嵌入报表时动态选择数据集。 报表和数据集不需要驻留在同一个工作区中。 根据选择的数据集，最终用户将看到不同的结果。

必须将两个工作区（包含报表的工作区以及包含数据集的工作区）分配到一个容量。

使用动态绑定嵌入报表包含两个阶段：
1. 生成令牌
2. 调整配置对象

## <a name="generating-a-token"></a>生成令牌
要生成令牌，请使用[用于生成多个项的嵌入令牌的 API](embed-sample-for-customers.md#multiEmbedToken)。

两种嵌入方案（为组织嵌入内容和为客户嵌入内容）都支持动态绑定   。

| 解决方案                   | 令牌                               | 要求                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 为组织嵌入内容  | Power BI 用户的访问令牌     | 使用 Azure AD 标记的用户必须对所有项目拥有适当的权限。                                                                    |
| 为客户嵌入内容     | 非 Power BI 用户的访问令牌 | 必须包括报表和动态绑定数据集的权限。 使用新 API 生成支持多个项目的嵌入令牌。 |

## <a name="adjusting-the-config-object"></a>调整配置对象
将 `datasetBinding` 添加到配置对象中。 使用页面底部的示例作为参考。

如果不熟悉如何在 Power BI 中嵌入内容，请查看以下教程，了解如何嵌入 Power BI 内容：
* [为客户将 Power BI 内容嵌入应用程序](embed-sample-for-customers.md)
* [教程：为组织将 Power BI 内容嵌入应用程序](embed-sample-for-your-organization.md)

 ### <a name="example"></a>示例
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```
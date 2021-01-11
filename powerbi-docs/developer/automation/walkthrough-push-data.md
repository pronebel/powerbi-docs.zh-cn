---
title: 在 Power BI 嵌入式分析中将数据推送到数据集以增强嵌入式 BI 见解
description: 将数据推送到 Power BI 数据集。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 3c5805f4d498e8e2d8a788c5703a09a8109e024b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887422"
---
# <a name="push-data-into-a-power-bi-dataset"></a>将数据推送到 Power BI 数据集

借助 Power BI API，你可以将数据推送到 Power BI 数据集。 本文将说明如何将包含“产品”表的“销售与市场营销”数据集推送到已有数据集。

开始之前，你需要 Azure Active Directory (Azure AD) 和 [Power BI 帐户](../embedded/create-an-azure-active-directory-tenant.md)。

## <a name="steps-to-push-data-into-a-dataset"></a>将数据推送到数据集的步骤

* 步骤 1：[将应用注册到 Azure AD](../embedded/register-app.md)
* 步骤 2：[获取身份验证访问令牌](walkthrough-push-data-get-token.md)
* 步骤 3：[在 Power BI 中创建数据集](walkthrough-push-data-create-dataset.md)
* 步骤 4：[获取数据集以向 Power BI 表中添加行](walkthrough-push-data-get-datasets.md)
* 步骤 5：[向 Power BI 表中添加行](walkthrough-push-data-add-rows.md)

下一部分是关于推送数据的 Power BI API 操作的一般讨论。

## <a name="power-bi-api-operations-to-push-data"></a>推送数据的 Power BI API 操作

借助 Power BI REST API，你可以将数据源推送到 Power BI。 应用向数据集添加行时，仪表板磁贴自动更新新数据。 若要推送数据，请使用 [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset) 和 [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows) 操作。 若要查找数据集，请使用[获取数据集](/rest/api/power-bi/datasets/getdatasets)操作。 进行以上任意操作时，可以传递组 ID 以将其用于组。 若要获取组 ID 列表，请使用[获取组](/rest/api/power-bi/groups/getgroups)操作。

将数据推送到数据集的操作如下：

* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [获取数据集](/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](/rest/api/power-bi/pushdatasets/datasets_postrows)
* [获取组](/rest/api/power-bi/groups/getgroups)

通过将 JavaScript 对象表示法 (JSON) 字符串传递给 Power BI 服务，在 Power BI 中创建数据集。 若要了解有关 JSON 的详细信息，请参阅 [JSON 简介](https://json.org/)。

数据集的 JSON 字符串具有以下格式：

**Power BI 数据集 JSON 对象**

```json
{"name": "dataset_name", "tables":
    [{"name": "", "columns":
        [{ "name": "column_name1", "dataType": "data_type"},
         { "name": "column_name2", "dataType": "data_type"},
         { ... }
        ]
      }
    ]
}
```

对于我们的“销售与市场营销”数据集示例，将传递如下所示的 JSON 字符串。 在此示例中，“SalesMarketing”是该数据集名称，“Product”是表名称。 定义表后，再定义表架构。 对于 **SalesMarketing** 数据集，表架构具有这些列：ProductID、制造商、类别、市场细分、产品和 IsCompete。

**数据集对象 JSON 示例**

```json
{
    "name": "SalesMarketing",
    "tables": [
        {
            "name": "Product",
            "columns": [
            {
                "name": "ProductID",
                "dataType": "int"
            },
            {
                "name": "Manufacturer",
                "dataType": "string"
            },
            {
                "name": "Category",
                "dataType": "string"
            },
            {
                "name": "Segment",
                "dataType": "string"
            },
            {
                "name": "Product",
                "dataType": "string"
            },
            {
                "name": "IsCompete",
                "dataType": "bool"
            }
            ]
        }
    ]
}
```

对于 Power BI 表架构，可以使用以下数据类型。

## <a name="power-bi-table-data-types"></a>Power BI 表数据类型

| **数据类型** | **限制** |
| --- | --- |
| Int64 |不允许使用 Int64.MaxValue 和 Int64.MinValue。 |
| Double |不允许使用 Double.MaxValue 和 Double.MinValue 值。 不支持 NaN。某些函数（例如 Min、Max）中不支持使用正无穷和负无穷。 |
| 布尔 |无 |
| datetime |在数据加载期间，我们将不足一天的值量化为 1/300 秒（3.33 毫秒）的整数倍。 |
| 字符串 |当前允许最多 12.8 万个字符。 |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>了解有关将数据推送到 Power BI 的详细信息

若要开始将数据推送到数据集，请参阅左侧导航窗格中的[步骤 1：将应用注册到 Azure AD](../embedded/register-app.md)。

## <a name="next-steps"></a>后续步骤

* [注册 Power BI](../embedded/create-an-azure-active-directory-tenant.md)  
* [JSON 简介](https://json.org/)  
* [Power BI REST API 概述](overview-of-power-bi-rest-api.md)  

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
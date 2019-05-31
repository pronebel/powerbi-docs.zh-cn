---
title: 将数据推送到数据集
description: 将数据推送到 Power BI 数据集
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222161"
---
# <a name="push-data-into-a-power-bi-dataset"></a>将数据推送到 Power BI 数据集

Power BI API 可以将数据推送到 Power BI 数据集。 在本文中，我们演示您如何将推送到的现有数据集包含 Product 表的市场部市场营销数据集。

开始之前，你需要 Azure Active Directory (Azure AD) 和一个[Power BI 帐户](create-an-azure-active-directory-tenant.md)。

## <a name="steps-to-push-data-into-a-dataset"></a>将数据推送到数据集的步骤

* 步骤 1：[使用 Azure AD 注册应用](walkthrough-push-data-register-app-with-azure-ad.md)
* 步骤 2：[获取身份验证访问令牌](walkthrough-push-data-get-token.md)
* 步骤 3：[在 Power BI 中创建数据集](walkthrough-push-data-create-dataset.md)
* 步骤 4：[获取数据集以将行添加到 Power BI 表](walkthrough-push-data-get-datasets.md)
* 步骤 5：[向 Power BI 表中添加行](walkthrough-push-data-add-rows.md)

下一部分是关于推送数据的 Power BI API 操作的一般讨论。

## <a name="power-bi-api-operations-to-push-data"></a>推送数据的 Power BI API 操作

借助 Power BI REST API，你可以将数据源推送到 Power BI。 当应用程序将行添加到数据集时，仪表板磁贴，会自动使用新数据更新。 若要将数据推送，使用[PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)并[PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)操作。 若要查找的数据集，请使用[获取数据集](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)操作。 可以传递组 ID，以便使用上述任何操作的组。 若要获取组 ID 列表，请使用[获取组](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)操作。

将数据推送到数据集的操作如下：

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [获取数据集](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [获取组](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

通过将 JavaScript 对象表示法 (JSON) 字符串传递给 Power BI 服务，在 Power BI 中创建数据集。 若要了解有关 JSON 的详细信息，请参阅 [JSON 简介](http://json.org/)。

数据集的 JSON 字符串具有以下格式：

**Power BI 数据集 JSON 对象**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

市场部市场营销数据集示例中，将传递 JSON 字符串，如下所示。 在此示例中，**市场营销**是数据集名称，并**产品**表的名称。 用于定义的表后, 你定义的表架构。 对于 SalesMarketing  数据集，表架构包含以下列：ProductID、制造商、类别、段、产品和 IsCompete。

**数据集对象 JSON 示例**

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

对于 Power BI 表架构，可以使用以下数据类型。

## <a name="power-bi-table-data-types"></a>Power BI 表数据类型

| **数据类型** | **限制** |
| --- | --- |
| Int64 |不允许使用 Int64.MaxValue 和 Int64.MinValue。 |
| 双精度 |不允许使用 Double.MaxValue 和 Double.MinValue 值。 不支持 NaN。 + 正无穷和负无穷大不支持某些函数 （例如，最小，最大）。 |
| 布尔 |无 |
| 日期时间 |数据加载，我们将量化天到 1/300 秒 （3.33 毫秒） 的整数倍的小数部分的值。 |
| 字符串 |当前允许最多 12.8 万个字符。 |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>了解有关将数据推送到 Power BI 的详细信息

若要开始将数据推送到数据集，请参阅左侧导航窗格中的[步骤 1：将应用注册到 Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)。

[下一步 >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>后续步骤

[注册 Power BI](create-an-azure-active-directory-tenant.md)  
[JSON 简介](http://json.org/)  
[Power BI REST API 概述](overview-of-power-bi-rest-api.md)  
更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)
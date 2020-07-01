---
title: 在 Power BI（预览版）中将 DirectQuery 用于数据流
description: 了解如何在 Power BI 中将 DirectQuery 用于数据流
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 669f05c03bd7a42d5b44f6ca2fa1b4d58680f71b
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237751"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>在 Power BI（预览版）中将 DirectQuery 用于数据流

可以使用 DirectQuery 直接连接到数据流，从而能直接连接到自己的数据流，而无需导入其数据。 

将 DirectQuery 用于数据流，可以让 Power BI 和数据流过程得到以下增强：

* 避免单独刷新计划 - DirectQuery 直接连接到数据流，无需创建导入的数据集。 因此，将 DirectQuery 与数据流一起使用意味着不再需要数据流和数据集的单独刷新计划，就能确保数据已同步。

* **筛选数据** - DirectQuery 对于处理数据流中经过筛选的数据视图非常有用。 如果要筛选数据以处理数据流中的一部分数据，可以使用 DirectQuery（和计算引擎）来筛选数据流数据，并处理筛选出的子集。


## <a name="using-directquery-for-dataflows"></a>将 DirectQuery 用于数据流

将 DirectQuery 用于数据流是一项预览功能，从 Power BI Desktop 2020 年 5 月版开始提供。 

若要将 DirectQuery 用于数据流，需要满足以下条件：

* 数据流必须位于已启用 Power BI Premium 的工作区中
* 必须已打开计算引擎。 若要详细了解计算引擎，请参阅[增强的计算引擎](service-dataflows-enhanced-compute-engine.md)。

## <a name="enable-directquery-for-dataflows"></a>为数据流启用 DirectQuery

为了确保数据流可用于 DirectQuery 访问，增强的计算引擎必须处于最优状态。 若要为数据流启用 DirectQuery，请将新的“增强的计算引擎设置”选项设置为“打开”。 下图展示的是正确选择的设置。

![为数据流启用增强的计算引擎](media/service-dataflows-directquery/dataflows-directquery-01.png)

应用该设置后，请刷新数据流以让优化生效。 


## <a name="considerations-and-limitations"></a>注意事项和限制

下面列出的是 DirectQuery 和数据流存在的几个已知限制。

* 用于数据流的 DirectQuery 不适用于已启用增强的元数据预览功能的情况。 我们计划在即将推出的 Power BI Desktop 月度发行版中消除这种冲突。

* 在此功能的预览期间，部分客户在将 DirectQuery 用于数据流时可能会遇到超时或性能问题。 我们会在此预览期间积极地解决此类问题。

* 当前不支持具有导入和 DirectQuery 数据源的复合/混合模型。

* 大型数据流在查看可视化效果时可能会遇到超时问题。 此限制将在功能正式发布时删除。 同时，遇到超时问题的大型数据流应使用导入模式。

* 在“数据源设置”下，如果使用 DirectQuery，数据流连接器将显示无效凭据。 这不会影响行为，并且数据集可以正常工作。 此问题会在临近正式发布时解决。



## <a name="next-steps"></a>后续步骤

以下文章有助于了解关于使用数据流的详细信息和方案：

* [数据流自助服务数据准备](service-dataflows-overview.md)
* [在 Power BI Premium 上使用计算实体](service-dataflows-computed-entities-premium.md)
* [将数据流与本地数据源配合使用](service-dataflows-on-premises-gateways.md)
* [Power BI 数据流的开发人员资源](service-dataflows-developer-resources.md)
* [数据流和 Azure Data Lake 集成（预览）](service-dataflows-azure-data-lake-integration.md)

有关通用数据模型的详细信息，可以阅读其概述文章：
* [通用数据模型 - 概述](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [了解 GitHub 上有关通用数据模型架构和实体的详细信息](https://github.com/Microsoft/CDM)

Power BI Desktop 相关文章：

* [通过 Power BI Desktop 连接 Power BI 服务中的数据集](../connect-data/desktop-report-lifecycle-datasets.md)
* [Power BI Desktop 中的查询概述](desktop-query-overview.md)

Power BI 服务相关文章：
* [配置计划刷新](../connect-data/refresh-scheduled-refresh.md)

---
title: Power BI Premium 支持大型数据集
description: Power BI Premium 现在支持不超过 10 GB 的数据集。
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 941d4bc3d66ce8e636f730d5757b7215c978d582
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794831"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Power BI Premium 支持大型数据集

Power BI Premium 支持上传大小不超过 10 GB 的 Power BI Desktop (.pbix) 文件。 上传后，数据集可被刷新为不超过 12 GB 的大小。 要使用大型数据集，请将其发布到分配给高级容量的工作区。
 
## <a name="best-practices"></a>最佳做法

本节介绍处理大型数据集的最佳做法。

大型模型会占用容量中的大量资源。 对于任何大于 1 GB 的模型，我们建议至少使用 P1 SKU。 虽然将大型模型发布到 A SKU（最高 A3）支持的工作区可能有用，但刷新它们将不起作用。

下表介绍了适合各种 .pbix 大小的建议 SKU 型号：

   |SKU  |.Pbix 大小   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3、P4、P5    | 最多 10 GB   |

Power BI Embedded A4 SKU 等同于 P1 SKU、A5 = P2 和 A6 = P3。 请注意，将大型模型发布到 A 和 EM SKU 可能会返回错误，这些错误并非特定于共享容量中的模型大小限制错误。 A 和 EM SKU 中的大型模型的刷新错误可能指向超时。 我们正在努力改进这些方案的错误消息。

.pbix 文件表示处于高度压缩状态的数据。 数据在加载到内存中时可能会多次扩展，并且在数据刷新期间可能会在内存中再次扩展数次。

对大型数据集进行计划的刷新可能需要很长时间，并且会占用大量资源。 因此，不要安排太多的重叠刷新。 另外，还要注意，对于此容量中的所有数据集，计划的刷新作业的超时时间已经增加了一倍，达到了四个小时。 建议使用[增量刷新](service-premium-incremental-refresh.md)，因为它更快速、更可靠且占用的资源更少。

如果自从上次使用数据集以来已经过一段时间，则大型数据集的初始报表加载可能需要很长时间，因为模型已加载到高级容量的内存中。 需要较长时间加载的报表的加载条可显示加载进度。

如果你从高级容量中删除工作区，则模型和所有关联的报表和仪表板将不起作用。

尽管高级容量中的每个查询内存和时间约束要高得多，但强烈建议使用筛选器和切片器来将视觉对象限制为仅显示必要的内容。

后续步骤

[什么是 Power BI Premium？](service-premium.md)
[Power BI Premium 发行说明](service-premium-release-notes.md)
[Microsoft Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)
[规划 Power BI 企业部署白皮书](https://aka.ms/pbienterprisedeploy)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

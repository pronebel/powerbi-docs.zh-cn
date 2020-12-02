---
title: 在 Power BI 报表服务器中访问作为 OData 源的共享数据集
description: Power BI 报表可以连接不同的数据源。 根据数据使用方式，可以提供不同的数据源。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 01/05/2018
ms.openlocfilehash: 8db19a56d4d1b845f0caf54ba4e9b07c33dfb131
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387358"
---
# <a name="accessing-shared-datasets-as-odata-feeds-in-power-bi-report-server"></a>在 Power BI 报表服务器中访问作为 OData 源的共享数据集
可以使用 OData 源从 Power BI Desktop 访问共享数据集。

1. 通过 OData 源 URL 连接 OData 源。
   
    ![报表服务器 OData 源](media/access-dataset-odata/report-server-odata-feed.png)
2. 在将数据引入 Power BI Desktop 后，可以在查询编辑器中对它进行修改。
   
    ![使用 OData 源的 Power BI Desktop 查询编辑器](media/access-dataset-odata/report-server-odata-results-query-editor.png)
3. 现在你可以在设计报表中使用数据了。
   
    ![使用 OData 源设计 Power BI Desktop 报表](media/access-dataset-odata/report-server-odata-power-bi-desktop-report-design.png)

请务必使用“高级选项”  ，以便在 Power Query 中打开 Open Type 列并相应地设置列格式以满足你的需求。

了解有关[连接到 Power BI Desktop 中的 OData 源](../connect-data/desktop-connect-odata.md)的更多信息。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)



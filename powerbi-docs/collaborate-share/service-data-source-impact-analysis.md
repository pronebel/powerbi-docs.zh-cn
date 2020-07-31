---
title: 数据源影响分析
description: 了解在何处使用数据源。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/20/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: 2c9834310179d8936cda8b769e3b7e3f80d328e6
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87253826"
---
# <a name="data-source-impact-analysis"></a>数据源影响分析

数据源影响分析可帮助你查看整个组织中哪里用到了你的数据源。 当数据源暂时或永久脱机，并且你想了解谁受到影响时，这很有用。 它可以显示使用数据源的工作区、数据流和数据集的数量，并允许轻松导航到受影响的数据流和数据集所在的工作区，以便进一步调查。

数据源影响分析还可以帮助发现租户中的数据重复，例如许多不同用户以同一数据源为基础构建相似模型时出现的数据重复。 通过帮助发现此类冗余数据集和数据流，数据源影响分析支持拥有“单一事实来源”这一目标。

## <a name="perform-data-source-impact-analysis"></a>执行数据源影响分析

执行数据源影响分析的步骤：

1. 转到包含你感兴趣的数据源的工作区，然后打开[世系视图](service-data-lineage.md)。
1. 找到数据源的卡，然后单击影响分析图标。

    ![数据源卡的屏幕截图，其中显示了影响分析按钮。](media/service-data-source-impact-analysis/data-source-impact-analysis-button.png)
 
“影响分析”侧窗格随即打开。

![数据源影响分析侧窗格的屏幕截图。](media/service-data-source-impact-analysis/data-source-impact-analyis-side-pane.png)
 
* **数据源类型**：指示数据源类型
* **数据源的路径**：Power BI Desktop 中定义的数据源路径。 例如，在上图中，SQL Server 数据库数据源的路径是连接字符串“twitterDB-yaronctestingdb1.database.windows.net”，如 Power BI Desktop 中所定义（如下所示）。 它由数据库名称“twitterDB”和服务器名称“yaronctestingdb1.database.windows.net”组成。

    ![Power B I Desktop 中连接字符串定义的屏幕截图。](media/service-data-source-impact-analysis/connection-string-definition-in-desktop.png)
 
* **影响摘要**：显示可能受影响的工作区、数据流和数据集的数量。 此计数包括你无权访问的工作区。
* **使用情况细目**：显示每个工作区受影响的数据流和数据集的名称。 若要进一步研究对特定工作区的影响，请单击工作区名称以打开工作区。 进入受影响的工作区后，使用[数据集影响分析](service-dataset-impact-analysis.md)查看有关已连接报表和仪表板的详细使用情况。

## <a name="privacy"></a>隐私

在影响分析侧窗格中，你只会看到有权访问的工作区、数据集和数据流的真实名称。 你无权访问的项目列于“访问受限”中。 这是因为某些项目名称可能包含个人信息。
影响汇总计数包括所有受影响的数据流和数据集，甚至包括你无权访问的工作区中的数据流和数据集。

## <a name="limitations"></a>限制

分页报表尚不支持数据源影响分析，因此你将看不到数据源是否对租户中的此类报表有任何直接影响。

## <a name="next-steps"></a>后续步骤

* [数据集影响分析](service-dataset-impact-analysis.md)
* [数据世系](service-data-lineage.md)
---
title: 从 Power BI Desktop 进行发布
description: 从 Power BI Desktop 进行发布
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3a67c36b2594696e1c576693cc5808eb0227c1c7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "76709603"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>从 Power BI Desktop 发布数据集和报表
将 Power BI Desktop 文件发布到 Power BI 服务后，将模型中的数据发布到 Power BI 工作区。 这同样适用于在“报表”视图中创建的所有报表  。 你将看一个同名的新数据集以及工作区导航器中的任何报表。

从 Power BI Desktop 发布文件等效于在 Power BI 中使用**获取数据**连接到并上载 Power BI Desktop 文件。

> [!NOTE]
> 在 Power BI 中对报表所做的任何更改都不会保存回原始 Power BI Desktop 文件。 这包括在报表中添加、删除或更改可视化效果。
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>发布 Power BI Desktop 数据集和报表
1. 在 Power BI Desktop 中，选择“文件” **“发布”** “发布到 Power BI”或选择功能区上的“发布”\>  \>   。  

   ![“发布”按钮](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. 登录到 Power BI。
3. 选择目标位置。

   ![选择发布目标位置](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

发布完成后，你会收到报表链接。 选择链接可在 Power BI 站点中打开报表。

![发布成功对话框](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>重新发布或替换从 Power BI Desktop 中发布的数据集
发布 Power BI Desktop 文件后，数据集和你在 Power BI Desktop 中创建的所有报表都会上传到 Power BI 站点。 重新发布 Power BI Desktop 文件后，Power BI 站点中的数据集会替换为 Power BI Desktop 文件中已更新的数据集。

此流程非常简单，但需要注意以下几点：

* Power BI 中有两个或多个与 Power BI Desktop 文件同名的数据集时可能导致发布操作失败。 请确保你在 Power BI 中只具有一个同名的数据集。 也可以重命名文件然后进行发布，这将创建一个与文件同名的新数据集。
* 如果重命名或删除列或度量值，则 Power BI 中任何含有该字段的可视化都可能会被破坏。 
* Power BI 将忽略对现有列某些格式的更改。 例如，如果将列的格式从 0.25% 更改为 25%。
* 假设你有一个为 Power BI 中的现有数据集配置的刷新计划。 当你将新数据源添加到文件中，然后重新发布时，必须在下一次计划的刷新前登录这些数据源。
* 重新发布从 Power BI Desktop 发布的数据集并定义刷新计划时，重新发布后即会开始数据集刷新。 


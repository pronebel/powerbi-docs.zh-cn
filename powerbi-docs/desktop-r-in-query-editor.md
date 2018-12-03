---
title: 在 Power BI 查询编辑器中使用 R
description: 在 Power BI Desktop 查询编辑器中使用 R 进行高级分析
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9183a0fbb163fb4e46e6b310bcce953aaef9d1b8
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670615"
---
# <a name="using-r-in-query-editor"></a>在查询编辑器中使用 R
你可以在 Power BI Desktop **查询编辑器**中使用 **R**，R 是统计学家、数据科学家和数据分析师使用最广泛的一种编程语言。 **查询编辑器**中集成的 R 可使你用 R 来执行数据清理，并在数据集中执行高级数据调整和分析，包括丢失数据补全、预测和聚类分析，此处仅举几例。 **R** 是功能强大的语言，可用于在“查询编辑器”中准备你的数据模型并创建报表。

## <a name="installing-r"></a>安装 R
若要在 Power BI Desktop 的**查询编辑器**中使用 **R**，需要在本地计算机上安装 **R**。 可以从很多位置免费下载并安装 **R**，其中包括 [Revolution Open download page](https://mran.revolutionanalytics.com/download/)（Revolution Open 下载页），以及 [CRAN 存储库](https://cran.r-project.org/bin/windows/base/)。

## <a name="using-r-in-query-editor"></a>在查询编辑器中使用 R
若要演示如何在查询编辑器中使用 R 脚本，请以基于 .CSV 文件的股票市场数据集为例（可[从此处下载](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv)）并按照示例进行操作。 此示例中的步骤如下所示：

1. 首先，将数据加载到 **Power BI Desktop**中。 本例中，请加载 EuStockMarkets_NA.csv 文件，并在 Power BI Desktop 的“主页”功能区中依次选择“获取数据”和“CSV”。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)
2. 选择该文件，并选择“打开”，然后该 CSV 将显示在“CSV 文件”对话框中。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)
3. 加载数据后，你会在 Power BI Desktop 中的 **“字段”** 窗格中看到它。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)
4. 通过从 **Power BI Desktop** 中的“主页”选项卡中选择“查询编辑器”来打开“查询编辑器”。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)
5. 在“转换”选项卡中，选择“运行 R 脚本”，然后“运行 R 脚本”编辑器随即出现（下一步中所示）。 注意，第 15 和 20 行受数据丢失影响。下图中无法看见的其他行也是如此。 以下步骤演示 R（将）如何为你补全这些行。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)
6. 此示例中，请输入以下脚本代码：

       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"

   > [!NOTE]
   > 需要在 R 环境中安装 mice 库才能使之前的脚本代码正常运行。 若要安装 mice，请在 R 安装中运行以下命令：|      > install.packages('mice')
   > 
   > 

   当放入“运行 R 脚本”对话框时，代码如下所示：

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5b.png)
7. 选择“确定”后，“查询编辑器”将显示与数据隐私相关的警告。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. 为使 R 脚本在 Power BI 服务中正常工作，所有的数据源都需要设置为“公用”。 有关隐私设置及其含义的详细信息，请参阅[隐私级别](desktop-privacy-levels.md)。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   请注意“字段”窗格中的名为 completedValues 的新列。 注意，有一些行缺少数据元素，如第 15 和 18 行。 下一节中将介绍 R 如何处理该问题。


只需要五行 R 脚本，**查询编辑器**就能用预测模型填写丢失的值。

## <a name="creating-visuals-from-r-script-data"></a>从 R 脚本数据创建视觉效果
现在，可创建视觉对象，以查看 R 脚本代码如何使用 mice 库补全缺少的值，如下图所示：

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

创建好该视觉对象，以及希望使用 Power BI Desktop 创建的任何其他视觉对象之后，可保存 Power BI Desktop 文件（保存为 .pbix 文件），然后在 Power BI 服务中使用数据模型（及其内附的 R 脚本）。

> [!NOTE]
> 想要查看完成了这些步骤的完整 .pbix 文件吗？ 真幸运 - 你可以在[此处](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix)下载示例中使用的完整 **Power BI Desktop** 文件。

将 .pbix 文件上传到 Power BI 服务后，还需要几个步骤来启用数据刷新（在服务中），以及启用服务中待更新的视觉对象（为了更新视觉对象，数据需要访问 R）。 其它步骤如下所示：

* **启用数据集的计划刷新** - 若要为包含 R 脚本数据集的工作簿启用计划刷新，请参阅[配置计划刷新](refresh-scheduled-refresh.md)，其中也包含有关 **个人网关** 的信息。
* **安装个人网关** - 需要在计算机上与文件和 R 安装位置相同的位置安装**个人网关**；Power BI 服务必须访问该工作簿并重新呈现任何已更新的视觉对象。 你可以获取有关如何[安装和配置个人网关](service-gateway-personal-mode.md)的详细信息。

## <a name="limitations"></a>限制
对包括 R 脚本，在**查询编辑器**中创建的查询有一些限制：

* 所有 R 数据源设置都必须设置为“公用”，并且**查询编辑器**中创建的查询中的所有其它步骤也必须设为“公用”。 若要获取数据源设置，请在 **Power BI Desktop** 中，选择“文件”>“选项和设置”>“数据源设置”。

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  从“数据源设置”对话框中，选择数据源，然后选择“编辑权限...”并确保“隐私级别”设置为“公用”。

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* 若要启用 R 视觉对象或数据集的计划更新，你需要启用“计划更新”，并且拥有安装在存储工作簿和 R 安装的计算机上的**个人网关**。 有关这两方面的详细信息，请参阅本文中的之前章节，其中提供了链接可了解每个方面的详细信息。

通过 R 和自定义查询你能进行各种各样的操作，因此你可以按照你想要显示的方式来探索和分析你的数据。


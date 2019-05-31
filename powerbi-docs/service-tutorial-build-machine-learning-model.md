---
title: 教程：生成 Power BI （预览版） 中的机器学习模型
description: 在本教程中，您将生成在 Power BI 中的机器学习模型。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406164"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>教程：生成 Power BI （预览版） 中的机器学习模型

在本教程的文章中，使用**自动化的机器学习**创建并应用在 Power BI 中的二进制预测模型。 本教程提供有关创建 Power BI 数据流，并在数据流，以进行训练和验证机器学习模型直接在 Power BI 中使用的实体定义。 我们然后使用该模型进行评分来生成预测。

首先，将创建二元预测机器学习模型来预测基于一组其联机会话属性的在线购物者购买意向。 基准测试机器学习数据集用于此练习。 一旦对模型进行训练，Power BI 将自动生成解释模型结果验证报告。 然后，可以查看验证报告，并将模型应用于你的数据进行评分。

本教程包括以下步骤：

> [!div class="checklist"]
> * 使用输入数据创建数据流
> * 创建并定型机器学习模型
> * 查看模型验证报表
> * 将模型应用到数据流的实体
> * 在 Power BI 报表中使用该模型的已评分的输出

## <a name="create-a-dataflow-with-the-input-data"></a>使用输入数据创建数据流

本教程的第一个部分是使用输入数据创建数据流。 该过程需要几个步骤，如中所示以下部分中，从获取数据。

### <a name="get-data"></a>获取数据

创建数据流的第一步是已准备好你的数据源。 在本例中，我们使用的联机会话，其中一些推出而告终中购买的一组中的机器学习数据集。 数据集包含一组有关这些会话，我们将使用用于训练模型的属性。

可以从 UC Irvine 网站来下载数据集。  我们还必须提供此功能，在本教程中，从以下链接： [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv)。

### <a name="create-the-entities"></a>创建实体

若要在数据流中创建实体，登录到 Power BI 服务并导航到启用 AI 预览的专用容量上的工作区。

如果还没有一个工作区，则可以创建一个通过选择**工作区**在 Power BI 服务中，选择左侧的导航菜单中**创建应用工作区**面板底部的将出现。 这将打开一个面板位于右侧，以输入工作区详细信息。 输入工作区名称并选择**高级**。 确认在工作区使用专用容量使用单选按钮，并将它分配给已开启 AI 预览版的专用的容量实例。 然后，选择“保存”  。

![创建工作区](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

创建工作区后，可以选择**跳过**右下角的欢迎屏幕上，在下图中所示。

![如果有一个工作区跳过](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

选择**数据流 （预览版）** 选项卡。选择**创建**正确的工作区中，并选择顶部的按钮**数据流**。

![创建数据流](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

选择“添加新实体”  。 这将启动**Power Query**在浏览器中的编辑器。

![添加新实体](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

选择**Text/CSV 文件**作为数据源下, 图中所示。

![所选的文本/CSF 文件](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

在中**连接到数据源**显示下一步中，粘贴到以下链接*online_shoppers_intention.csv*到**文件路径或 URL**框，并选择**下一步**。

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![文件路径](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Power Query 编辑器显示 CSV 文件中的数据的预览。 选择**转换表**在功能区命令，然后选择**将第一行用作标头**从显示的菜单。 这将添加_升级标头_查询单步执行**应用步骤**部分位于屏幕的右侧。 您可以查询重命名为更友好名称的更改中的值**名称**框在右窗格中找到。 例如，可以更改查询名更改为_Online 的访问者_。

![将更改为友好名称](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

在此数据集中的属性数据类型的一些_数值_或_布尔_中使用，但这些可能被解释为字符串**Power Query**。 选择顶部的每个列标题以更改下面列出的以下类型的列的属性类型图标：

* **十进制数：** Administrative_Duration;Informational_Duration;ProductRelated_Duration;BounceRates;ExitRates;PageValues;SpecialDay
* **True/False:** 周末;收入

![更改数据类型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

**二元预测**我们将训练的模型需要布尔型字段，作为标识从过去的观测值的结果的标签。 在此数据集中_收入_属性指示采购，，此属性现已作为一个布尔值。 因此，我们不需要添加标签的计算的列。 在其他数据集，可能需要将现有标签属性转换为布尔值列。

选择**完成**按钮以关闭 Power Query 编辑器。 这将显示与实体列表_Online 的访问者_我们添加的数据。 选择**保存**在右上角中，为数据流中，提供一个名称，然后选择**保存**在对话框中，在下图中所示。

![保存数据流](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>刷新数据流

保存数据流导致显示一条通知，指出已保存到数据流。 选择**立即刷新**引入数据流的源中的数据。

![立即刷新](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

选择右上角的“关闭”  ，然后等待数据流刷新完成。

此外可以使用刷新到数据流**操作**命令。 刷新完成时，数据流将显示的时间戳。

![刷新的时间戳](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>创建并定型机器学习模型

刷新完成后，请选择数据流。 若要添加的机器学习模型，请选择**应用机器学习模型**按钮**操作**列出包含在定型数据和标签信息的基实体，然后选择**添加机器学习模型**。

![添加机器学习模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

用于创建我们的机器学习模型的第一步是确定历史数据包括你要预测的标签字段。 将通过从这些数据中学习创建模型。

对于我们使用的数据集，这是**收入**字段。 选择**收入**作为历史结果字段值，然后选择**下一步**。

![选择历史数据](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

接下来，我们必须选择机器学习模型来创建的类型。 Power BI 分析你已识别的历史结果字段中的值，并提供建议的机器学习模型可用于创建预测该字段的类型。

在这种情况下，由于我们要预测二进制结果的还是用户将进行购买，或不选择**二元预测**以及该模型类型，然后选择下一步。

![所选的二元预测](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

接下来，Power BI 将执行初步扫描的数据，并建议模型可以使用的输入。 您可以选择自定义用于模型的输入的字段。 在我们组织有序的数据集，若要选择的所有字段，都选择实体名称旁边的复选框。 选择**下一步**接受输入。

![选择下一步复选框](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

在最后一步，我们必须提供我们的模型的名称以及要在自动生成将汇总模型验证的结果的报表中使用的结果友好的标签。 接下来我们需要为模型命名_购买意向预测_，和 true 和 false 标签_采购_并_否购买_。 然后，选择“保存”  。

![保存模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

我们的机器学习模型现已准备好的培训。 选择**立即刷新**开始为模型定型。

![立即刷新](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

定型过程将开始通过采样和对历史数据进行规范化和将你的数据集拆分为两个新实体*购买意向预测定型数据*和*购买意向预测测试数据*。

具体取决于数据集的大小，定型过程可能需要几分钟到几个小时。 此时，请参阅中的模型**机器学习模型，** 与 dataflow 的选项卡。 _准备_状态指示已排队等候培训或低于培训的模型。

![准备好进行培训](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

训练模型时，你将无法查看或编辑数据流。 你可以确认在模型训练和验证通过数据流的状态。 这显示为正在进行中的数据刷新**数据流**工作区的选项卡。

![在过程中](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

模型训练完成后，数据流将显示更新的刷新时间。 你可以确认对模型进行训练，通过导航到**机器学习模型，** 数据流中的选项卡。 你创建的模型应显示状态为**Trained**并**最后一个训练**现在应该更新时间。

![在最后一次培训](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>查看模型验证报表

若要查看模型验证报表，在**机器学习模型，s**选择**查看性能报告和应用模型**按钮**操作**模型列. 此报告描述如何在机器学习模型是可能会执行。

在中**模型性能**的报表中，选择页**关键影响因素**若要查看为您的模型上的预测值。 您可以选择一个预测值，若要查看如何与该预测值关联的结果分布。

![模型性能](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

可以使用**概率阈值**模型性能页上的切片器来检查它的精度和召回率对模型的影响。

![概率阈值](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

报表的其他页面描述模型的性能统计度量值。

该报告还包括培训的详细信息页面，介绍了运行时，如何从输入和使用的最终模型超参数提取功能的不同迭代。

## <a name="apply-the-model-to-a-dataflow-entity"></a>将模型应用到数据流的实体

选择**应用模型**要刷新数据流时调用此模型的报表的顶部的按钮。 在中**应用**对话框中，可以指定包含源数据模型应该应用于目标实体。

![应用模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

出现提示时，您必须**刷新**数据流，以预览您的模型的结果。

应用模型将会创建一个新的实体，带有后缀**丰富 < model_name >** 追加到该模型应用于的实体。 在本例中，将应用到模型**OnlineShoppers**将创建实体**OnlineShoppers 丰富购买意向预测**，其中包括从模型预测的输出。

应用的二元预测模型，将增加与预测的结果、 概率分数和预测的顶部特定于记录的影响因素的三个列，每个指定的列名称作为前缀。

![三个列的结果](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

由于的已知问题，才可从 Power BI Desktop 访问丰富的实体中的已评分的输出列。 若要预览这些服务中，必须使用特殊预览版实体。

数据流刷新完成后，可以选择**OnlineShoppers 丰富购买意向预测预览**实体以查看结果。

![查看结果](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>在 Power BI 报表中使用该模型的已评分的输出

若要使用的机器学习模型评分的输出，也可以使用连接到在数据流从 Power BI desktop 中，数据流连接器。 **OnlineShoppers 丰富购买意向预测**实体现在可用于将合并从 Power BI 报表中模型的预测。

## <a name="next-steps"></a>后续步骤

在本教程中，将创建并应用中 Power BI 中使用这些步骤的二元预测模型：

* 使用输入数据创建数据流
* 创建并定型机器学习模型
* 查看模型验证报表
* 将模型应用到数据流的实体
* 在 Power BI 报表中使用该模型的已评分的输出

有关 Power BI 中的机器学习自动化的详细信息，请参阅[自动在 Power BI （预览版） 中的机器学习](service-machine-learning-automated.md)。

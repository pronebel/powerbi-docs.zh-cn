---
title: 教程：在 Power BI 中生成机器学习模型（预览）
description: 在本教程中，你将在 Power BI 中生成机器学习模型。
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406164"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>教程：在 Power BI 中生成机器学习模型（预览）

在本教程中，你将在 Power BI 中使用自动机器学习创建并应用二进制预测模型。 此教程包括以下操作的指南：创建 Power BI 数据流，以及使用数据流定义的实体直接从 Power BI 训练并验证机器学习模型。 然后使用该模型评分，以生成预测。

首先将创建二进制预测机器学习模型，用于基于在线购物者的联机会话属性集预测他们的购买意向。 在此练习中使用了基准机器学习数据集。 训练模型后，Power BI 将自动生成验证报告，来说明模型结果。 然后则可以查询验证报告，并将模型应用于数据，来进行评分。

此教程包含下列步骤：

> [!div class="checklist"]
> * 使用输入数据创建数据流
> * 创建并训练机器学习模型
> * 查看模型验证报告
> * 将模型应用于数据流实体
> * 在 Power BI 报表中使用模型的评分输出

## <a name="create-a-dataflow-with-the-input-data"></a>使用输入数据创建数据流

此教程的第 1 部分为使用输入数据创建数据流。 此过程需要以下部分所示的几个步骤，首先是获取数据。

### <a name="get-data"></a>获取数据

创建数据流的第 1 个步骤是准备好数据资源。 在示例中，我们使用一组联机会话的机器学习数据集，其中的一些会话以购买结束。 此数据集包含一组与这些会话相关的属性，我们将使用它们训练模型。

可以从 UC Irvine 网站下载此数据集。  我们还在以下链接中提供了此数据集，以便于使用此教程：[online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv)。

### <a name="create-the-entities"></a>创建实体

若要在数据流中创建实体，登录到 Power BI 服务并导航到启用 AI 预览的专用容量上的工作区。

如果还没有工作区，可以通过从 Power BI 服务选择左侧导航菜单的“工作区”来创建一个，然后选择显示的面板底部的“创建应用工作区”。 这将在右侧打开一个面板，用于输入工作区详细信息。 输入一个工作区名称，然后选择“高级”。 使用单选按钮确认工作区使用“专用容量”，并确保将它分配给已启用 AI 预览版的专用容量实例。 然后，选择“保存”。

![创建工作区](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

创建工作区后，可以选择欢迎屏幕右下角的“跳过”，如下图所示。

![若已有工作区，请跳过](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

选择“数据流(预览版)”选项卡。选择工作区右上角的“创建”按钮，再选择“数据流”。

![创建数据流](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

选择“添加新实体”。 这将从浏览器启动 Power Query 编辑器。

![添加新实体](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

选择“文本/CSV 文件”作为数据源，如下图所示。

![已选择“文本/CSF 文件”](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

在接下来出现的“连接到数据源”中，将指向“online_shoppers_intention.csv”的以下链接粘贴到“文件路径或 URL”框，，然后选择“下一步”。

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![文件路径](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Power Query 编辑器显示 CSV 文件中的数据的预览。 从命令功能区中选择“转换表”，然后从显示的菜单中选择“将第一行用作标题”。 此操作将“提升的标题”查询步骤添加到屏幕右侧的“应用步骤”部分中。 更改右侧窗格中“名称”框的值，即可以将查询重命名为一个更加友好的名称。 例如，可以将查询名称更改为“在线访问者”。

![更改为友好名称](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

此数据集中的某些属性数据类型为“数字”或“布尔”，但 Power Query 可以将它们转换为字符串。 在每个列标题的顶部选择属性类型图标，将下面列出的列更改为以下类型：

* **小数：** Administrative_Duration；Informational_Duration；ProductRelated_Duration；BounceRates；ExitRates；PageValues；SpecialDay
* True/False：周末；收入

![更改数据类型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

我们要训练的“二级制预测”模型需要一个布尔字段作为标签，来标识过去观测到的结果。 在此数据集中，“收入”属性表示购买，并且已以布尔值形式提供此属性。 因此，我们无需为此标签添加计算列。 在其他数据集中，可能必须将现有的标签属性转换为布尔列。

选择“完成”按钮以关闭 Power Query 编辑器。 这将显示实体列表，其中包含我们添加的“在线访问者”数据。 选择右上角的“保存”，为数据流提供一个名称，然后从对话框选择“保存”，如下图所示。

![保存数据流](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>刷新数据流

保存数据流后，将显示说明已保存数据流的通知。 选择“立即刷新”以将数据从源引入数据流。

![立即刷新](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

选择右上角的“关闭”，然后等待数据流刷新完成。

也可以使用“操作”命令来刷新数据流。 刷新完成时，数据流将显示时间戳。

![刷新的时间戳](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>创建并训练机器学习模型

完成刷新后，选择数据流。 在包含训练数据和标签信息的基本实体的“操作”列表中，选择“应用 ML 模型”按钮，然后选择“添加机器学习模型，以添加机器学习模型”。

![添加机器学习模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

创建机器学习模型的第 1 个步骤是确认历史数据，包括想要预测的标签字段。 将通过学习此数据创建模型。

对于我们所使用的数据集，即为“收入”字段。 选择“收入”作为“历史结果字段”值，然后选择“下一步”。

![选择历史数据](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

接下来必须选择要创建的机器学习模型的类型。 Power BI 将分析你已确认的历史结果字段中的值，并推荐可以创建以用于预测该字段的机器学习模型类型。

在此示例中，由于预测的是关于用户是否购买的二进制结果，因此为模型类型选择“二进制预测”，然后选择“下一步”。

![已选择二进制预测](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

接下来，Power BI 对数据执行初步扫描，并推荐模型可以使用的输入。 可以选择自定义用于模型的输入字段。 在我们特选的数据集中，选择实体名称旁边的复选框，以选中所有字段。 选择“下一步”，以接受输入。

![选择“下一步”复选框](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

在最后的步骤中，必须为模型提供名称，并为结果提供易记的标签，以便用于自动生成的用于汇总模型验证结果的报表。 接下来必须将模型命名为“购买意向预测”，并将 true 和 false 标签命名为“购买”和“未购买”。 然后，选择“保存”。

![保存模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

现在即可以训练机器学习模型。 选择“立即刷新”，开始训练模型。

![立即刷新](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

训练过程将从采集和规范化历史数据并将数据集拆分为两个新的实体（“购买意向预测训练数据”和“购买意向预测测试数据”）开始。

在任何地方，训练过程均可能需要几分钟到几个小时，具体取决于数据集的大小。 此时，可以从数据流的“机器学习模型”选项卡看到此模型。 “已就绪”状态表示模型已在排队等待训练，或正在进行训练。

![已为训练准备就绪](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

训练模型期间，你无法查看或编辑数据流。 可以通过数据流的状态确认正在训练和验证模型。 在工作区的“数据流”选项卡中，它显示为数据刷新“正在进行中”。

![正在进行中](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

模型训练完成后，数据流显示更新后的刷新时间。 导航到数据流的“机器学习模型”选项卡，即可确认是否已训练模型。 创建的模型显示的状态应为“已训练”，并且“上一次训练”时间现在应更新。

![上次训练时间](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>查看模型验证报告

在“机器学习模型”中，从模型的“操作”列选择“查看性能报表并应用模型”按钮，以查看模型验证报告。 此报告描述机器学习模型的性能趋势。

在报告的“模型性能”页中，选择“关键影响因素”，以查看模型的主要预测指标。 可以选择一个预测指标，查看结果分步与该预测指标的关联。

![模型性能](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

在“模型性能”页上，可以使用“概率阈值”切片器，来查看它对模型的“精度”和“召回率”的影响。

![概率阈值](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

报告的其他页描述模型的统计学性能指标。

此报告还包括“训练详细信息”页，其中说明了运行的各种迭代、如何从输入提取特征，以及使用的最终模型的超参数。

## <a name="apply-the-model-to-a-dataflow-entity"></a>将模型应用于数据流实体

从报告顶部选择“应用模型”按钮，以在刷新数据流时调用此模型。 在“应用”对话框中，可以指定包含模型应应用到的源数据的目标实体。

![应用模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

出现提示时，必须刷新数据流才能预览模型的结果。

应用模型后，将创建新实体，并将后缀“已扩充的 <model_name>”追加到应用模型的实体。 在此示例中，将模型应用到“OnlineShoppers”实体后，将创建“已扩充 OnlineShoppers 的购买意向预测“，其中包括模型的预测输出。

应用二进制预测模型后，将添加三个列，其中包含预测的结果、概率评分以及预测的特定于记录的主要影响因素，每个列的前面均有指定的列名称。

![结果的三个列](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

鉴于已知问题，只可以从 Power BI Desktop 访问已扩充实体中的评分输出列。 必须使用专门的预览实体，才能在服务中预览它们。

数据流刷新完成后，可以选择“已扩充 OnlineShoppers 的购买意向预测预览”实体，以查看结果。

![查看结果](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>在 Power BI 报表中使用模型的评分输出

可以使用数据流，从 Power BI Desktop 连接器连接到数据流，以使用机器学习模型的评分输出。 在 Power BI 报表中，现在可以使用“已扩充 OnlineShoppers 的购买意向预测”实体合并模型的预测。

## <a name="next-steps"></a>后续步骤

在此教程中，你通过以下步骤在 Power BI 中创建并应用了二进制预测模型：

* 使用输入数据创建数据流
* 创建并训练机器学习模型
* 查看模型验证报告
* 将模型应用于数据流实体
* 在 Power BI 报表中使用模型的评分输出

有关 Power BI 中的机器学习自动化的详细信息，请参阅 [Power BI 中的自动机器学习（预览版）](service-machine-learning-automated.md)。

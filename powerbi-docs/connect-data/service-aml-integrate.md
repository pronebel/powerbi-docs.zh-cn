---
title: 教程：在 Power BI 中使用 Azure 机器学习模型
titleSuffix: Azure Machine Learning
description: 了解如何在 Power BI 中使用 Azure 机器学习模型。
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: tutorial
ms.author: samkemp
author: samuel100
ms.reviewer: sdgilley, maggies
ms.date: 12/10/2020
ms.openlocfilehash: 6c68fff575e4da0c9126904df2de5292747c209c
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491773"
---
# <a name="tutorial-consume-azure-machine-learning-models-in-power-bi"></a>教程：在 Power BI 中使用 Azure 机器学习模型

本教程将指导你基于机器学习模型创建 Power BI 报表。 完成本教程后，可执行以下操作：

> [!div class="checklist"]
> * 在 Power BI 中对机器学习模型进行评分（使用 Azure 机器学习部署）。
> * 在 Power Query 编辑器中连接到 Azure 机器学习模型。
> * 基于该模型创建含有可视化效果的报表。
> * 将该报表发布到 Power BI 服务。
> * 为报表设置计划的刷新。

## <a name="prerequisites"></a>先决条件

开始本教程之前，需要：

- 在 Azure 机器学习中训练和部署机器学习模型。 使用以下三个 Azure 机器学习教程之一： 

    - [选项 A：代码](/azure/machine-learning/tutorial-power-bi-custom-model)
    - [选项 B：设计器](/azure/machine-learning/tutorial-power-bi-designer-model)
    - [选项 C：自动化 ML](/azure/machine-learning/tutorial-power-bi-automated-model)

- 注册 [Power BI 免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)。
- 在本地计算机上[安装 Power BI Desktop](https://powerbi.microsoft.com/desktop/)。

## <a name="create-the-data-model"></a>创建数据模型

打开 Power BI Desktop 并选择“获取数据”。 在“获取数据”对话框中，搜索“Web”。 选择“Web”“源”>“连接”。

:::image type="content" source="media/service-aml-integrate/pbi-get-data.png" alt-text="显示 Web 数据的屏幕截图。":::

在“从 Web”对话框中，将以下 URL 复制并粘贴到框中：

```txt 
https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt
```

:::image type="content" source="media/service-aml-integrate/pbi-data.png" alt-text="显示 Web URL 的屏幕截图。":::

选择“确定”  。

选择“转换数据”以打开“Power Query 编辑器”窗口。

在 Power Query 编辑器的“开始”功能区中，选择“Azure 机器学习”按钮。

:::image type="content" source="media/service-aml-integrate/aml-button.png" alt-text="显示 Power Query 编辑器的屏幕截图。":::

使用单一登录登录到 Azure 帐户后，你会看到可用服务的列表。 选择根据“训练和部署机器学习模型”教程创建的 my-sklearn-service。 

Power Query 自动为你填充列。 请记住，在我们的服务架构中，有一个指定了输入的 Python 修饰器。 选择“确定”  。

:::image type="content" source="media/service-aml-integrate/aml-pbi-run.png" alt-text="显示 Azure 机器学习模型的屏幕截图。":::

选择“确定”会调用 Azure 机器学习服务。 它会触发有关数据和终结点的数据隐私的警告。

:::image type="content" source="media/service-aml-integrate/data_privacy_warning.png" alt-text="显示隐私警告的屏幕截图。":::

选择“继续”。 在下一个屏幕中，选择“忽略此文件的隐私级别检查” > “保存”。

对数据进行评分后，Power Query 会创建一个名为“AzureML.my-diabetes-model”的附加列。

:::image type="content" source="media/service-aml-integrate/scored-data.png" alt-text="显示已添加的评分列的屏幕截图。":::

服务返回的数据是列表。 

> [!NOTE]
> 如果已部署设计器模型，你会看到记录。

若要获取预测，请在“转换”功能区中，选择“展开列”按钮 >“展开到新行”。

展开后，你会在 AzureML.my-diabetes-model 列中看到预测。

:::image type="content" source="media/service-aml-integrate/after-expand.png" alt-text="显示扩展的屏幕截图。":::

按照以下后续步骤完成数据模型的清理。

1. 将 AzureML.my-diabetes-model 列重命名为“已预测”。
1. 将 Y 列重命名为“实际”。
1. 更改“实际”列的类型：选择该列，然后在“转换”功能区中，选择“数据类型” > “十进制数”。
1. 更改“已预测”列的类型：选择该列，然后在“转换”功能区中，选择“数据类型” > “十进制数”。
1. 在“开始”功能区中选择“关闭并应用”。

## <a name="create-a-report-with-visualizations"></a>创建含有可视化效果的报表

现在，可以创建一些可视化效果来显示数据。

1. 在“可视化效果”窗格中，选择“折线图”。 
1. 选中“折线图”视觉对象：
1. 将“期限”字段拖到“轴”中。
1. 将“实际”字段拖到“值”中。
1. 将“已预测”字段拖到“值”中。

调整折线图的大小以填充页面。 报表现在具有一个含有两行的折线图，一行用于已预测的值，另一行用于实际值，按期限分布。

:::image type="content" source="media/service-aml-integrate/report-viz.png" alt-text="显示报表可视化效果的屏幕截图。":::

## <a name="publish-the-report"></a>发布报表

如果需要，可以添加更多可视化效果。 为简洁起见，我们将在本教程中发布报表。

1. 保存报表。
1. 选择“文件” > “发布” > “发布到 Power BI”。
1. 登录 Power BI 服务。
1. 选择“我的工作区”。
1. 成功发布报表后，选择“在 Power BI 中打开 <MY_PBIX_FILE.pbix>”链接。 将在浏览器的 Power BI 中打开报表。

     :::image type="content" source="media/service-aml-integrate/publish-success.png" alt-text="显示成功发布的屏幕截图。":::

## <a name="enable-datasets-to-refresh"></a>启用要刷新的数据集

在使用要评分的新数据刷新数据源的方案中，需要更新凭据，以便可以对数据进行评分。 

在 Power BI 服务的“我的工作区”的黑色标题栏中，选择“更多选项(...)” > “设置” > “设置”。

:::image type="content" source="media/service-aml-integrate/settings-pbi.png" alt-text="显示设置的屏幕截图。":::

选择“数据集”，展开“数据源凭据”，然后选择“编辑凭据”。

:::image type="content" source="media/service-aml-integrate/data-refresh.png" alt-text="显示凭据刷新的屏幕截图。":::

按照 azureMLFunctions 和 Web 中的说明进行操作。 请确保选择隐私级别。 现在可以设置数据的“计划的刷新”。 选择“刷新频率”和“时区”。 还可以选择 Power BI 可发送刷新失败通知的电子邮件地址。

:::image type="content" source="media/service-aml-integrate/schedule-refresh.png" alt-text="显示数据集和评分刷新的屏幕截图。":::

选择“应用”。

>[!NOTE]
> 刷新数据时，还会将数据发送到 Azure 机器学习终结点以进行评分。

## <a name="clean-up-resources"></a>清理资源

>[!IMPORTANT]
>可以使用你创建的、用作其他 Azure 机器学习教程和操作指南文章的先决条件的资源。

如果你不打算使用所创建的资源，请将其删除，以免产生任何费用。

1. 在 Azure 门户中，选择最左侧的“资源组”  。
 
1. 从列表中选择你创建的资源组。

1. 选择“删除资源组”。

   ![用于在 Azure 门户中删除资源组的选项的屏幕截图。](./media/service-aml-integrate/delete-resources.png)

1. 输入资源组名称。 然后选择“删除”。
1. 在 Power BI 服务的“我的工作区”中，删除报表和相关数据集。 不需要在计算机上删除 Power BI Desktop 或报表。 Power BI Desktop 是免费的。

## <a name="next-steps"></a>后续步骤

在本系列教程中，你已了解如何在 Power BI 中设置计划，以便 Azure 机器学习中的评分终结点可以对新数据进行评分。

---
title: 教程：开始在 Power BI 服务中创建
description: Power BI 在线服务入门 (app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/08/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: eeda30e5a075166af3718084c2c9f7737f876cbe
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861098"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>教程：开始在 Power BI 服务中创建
本教程介绍了 Power BI 服务的一些功能。 在这里，你可连接到数据、创建报表和仪表板，并就你的问题提问。 你还可在 Power BI 服务中执行更多其他操作；本教程仅作激发兴趣之用。 要了解 Power BI 服务如何与其他 Power BI 产品/服务契合，建议阅读[什么是 Power BI](power-bi-overview.md)。

你是报表读者而不是创建者？ 建议先[了解 Power BI 服务](../consumer/end-user-experience.md)。

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="财务示例仪表板的屏幕截图。":::

在本教程中，将完成以下步骤：

> [!div class="checklist"]
> * 登录 Power BI Online 帐户或进行注册（如果还没有帐户）。
> * 打开 Power BI 服务。
> * 获取一些数据并在报表视图中打开。
> * 使用该数据创建可视化效果并将其另存为报表。
> * 从该报表固定磁贴，创建仪表板。
> * 使用问答自然语言工具将其他可视化效果添加到仪表板。
> * 在仪表板上调整磁贴大小、重新排列磁贴并编辑其详细信息。
> * 删除数据集、报表和仪表板，清理资源。

## <a name="sign-up-for-the-power-bi-service"></a>注册 Power BI 服务
需要 Power BI Pro 许可证方可在 Power BI 中创建内容。 如果没有 Power BI 帐户，请先[注册一个 Power BI Pro 免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)，再进行操作。

## <a name="step-1-get-data"></a>步骤 1：获取数据

通常，需要创建 Power BI 报表时，会先使用 Power BI Desktop。 Power BI Desktop 提供更多功能。 在开始设计报表之前，可对数据进行转换、调整和建模。 而这一次，我们将在 Power BI 服务中从头开始创建一个报表。

在本教程中，我们将从一个简单的 Microsoft Excel 文件获取数据。 想要跟着做吗？ [下载财务示例文件](https://go.microsoft.com/fwlink/?LinkID=521962)。

1. 若要开始，请在浏览器中打开 Power BI 服务 (app.powerbi.com)。 

    还没有帐户？ 别担心，可以[注册一个 Power BI Pro 免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)

1. 在导航窗格中选择“我的工作区”。

1. 在“我的工作区”中，选择“新建” > “上传文件”  。

    随即将打开“获取数据”页面。   

3. 在“新建内容”部分中，确保选中“文件”，然后选择保存 Excel 文件的位置 。
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="“新建内容”>“文件”的屏幕截图。":::

5. 浏览到计算机上的该文件，然后选择“打开”。

5. 在本教程中，我们会选择“导入”，将 Excel 文件添加为数据集，然后就可以使用它来创建报表和仪表板。 如果选择“上传”，则整个 Excel 工作簿都将上传至 Power BI，然后可以在 Excel Online 中打开它并进行编辑。
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="选择“导入”的屏幕截图。":::
6. 数据集准备就绪后，选择财务示例数据集旁边的“更多选项(...)”，然后选择“创建报表” 。
1. 打开报表编辑器。 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="“所有内容”>“创建报表”的的屏幕截图。":::

    报表画布是空白的。 我们看到右侧有“筛选器”、“可视化效果”和“字段”窗格  。

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="空白报表画布的屏幕截图。":::

    > [!TIP]
    > 选择左上角的全局导航按钮来折叠导航窗格。 这样画布就有更多的空间。
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="全局导航按钮。":::
    >

7. 你当前正在编辑视图中。 注意菜单栏中有“阅读视图”选项。 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="“阅读视图”选项的屏幕截图。":::

    在“编辑视图”中可以修改报表，因为你是报表的所有者和创建者 。 当你与同事共享报表时，通常他们只能在“阅读视图”中与报表交互。 他们是“我的工作区”中报表的使用者。 

## <a name="step-2-create-a-chart-in-a-report"></a>步骤 2：在报表中创建图表
连接到数据后，请开始浏览数据。 找到有趣的内容后，可以将其保存到报表画布上。 然后可将其固定到仪表板进行监视，并查看其随时间推移的变化情况。 但首先执行以下操作。
    
1. 在报表编辑器中，首先使用页面右侧的“字段”窗格生成可视化效果。 依次选择“销售总额”字段和“日期”字段 。
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="字段列表的屏幕截图。":::

    Power BI 会分析数据并创建柱形图可视化效果。 

    > [!NOTE]
    > 如果先选择了“日期”字段而非“销售总额”，则会出现一个表 。 别担心！ 我们将在下一步中更改可视化效果。

    某些字段旁有 sigma 符号，因为 Power BI 检测到它们包含数字值。

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="包含 sigma 符号的字段。":::

2. 接下来换一种方式来显示数据。 折线图是用于显示值随时间变化的良好视觉对象。 从“可视化效果”窗格中，选择“折线图” 。
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="选择了折线图的报表编辑器的屏幕截图。":::

3. 看起来不错，让我们将它固定到仪表板。 将鼠标悬停在可视化对象上，并选择固定图标。
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="“固定”图标的屏幕截图。":::

4. 由于此报表是新建的，因此在可视化对象固定到仪表板之前，系统会提示保存。 为报表命名（例如财务示例报表），然后选择“保存”。 

    现在你正在阅读视图中查看报表。 

6. 再次选择“固定”图标。
 
5. 选择“新建仪表板”，并为其命名（例如财务示例仪表板）。 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="为仪表板命名的屏幕截图。":::
  
    会显示一条成功消息（右上角附近），告知你可视化效果已作为磁贴添加到你的仪表板中。
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="“已固定到仪表板”对话框的屏幕截图。":::

    固定此可视化效果后，它存储在仪表板上。 数据始终保持最新状态，因此你可一目了然地跟踪最新值。 但如果在报表中更改此可视化效果类型，仪表板上的可视化效果不会更改。

7. 选择“转至仪表板”来查看新建的仪表板，它包含一个以磁贴形式固定的折线图。 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="固定了可视化效果的仪表板的屏幕截图。":::
   
8. 选择仪表板上的新磁贴。 Power BI 会转回到报表的“阅读视图”。

1. 要切换回“编辑视图”，请在菜单栏中选择“更多选项”(…)，然后选择“编辑” 。

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="选择“编辑”以编辑报表的屏幕截图。":::

    回到“编辑视图”后，可继续探索并固定磁贴。

## <a name="step-3-explore-with-qa"></a>步骤 3：探索问答功能

要快速浏览数据，请尝试问答问题框中提问。 通过问答功能，可以提出有关数据的自然语言查询。 在仪表板中，问答框位于菜单栏下的顶部（用于询问数据相关问题）。 在报表中，它位于顶部菜单栏中（用于提问）。

1. 要返回到仪表板，请在黑色“Power BI”标题栏中选择“我的工作区” 。

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="“返回我的工作区”的屏幕截图。":::

1. 在“我的工作区”中，选择你的仪表板。

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="选择你的仪表板的屏幕截图。":::

1. 选择“询问数据相关问题”。 问答功能会自动提供多项建议。 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="问答画布的屏幕截图。":::

    > [!NOTE]
    > 如果看不到这些建议，请打开“新问答体验”。

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="启用新问答体验的屏幕截图。":::

1. 某些建议会返回一个值。 例如，选择“什么是平均 cog”。

    问答功能会搜索答案，并以卡片可视化形式进行显示。

3. 选择“固定视觉对象”，然后将此可视化对象固定到财务示例仪表板。

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="固定视觉对象的屏幕截图。":::

1. 返回到问答，并选择“显示所有建议”。
1. 选择“按国家/地区列出的总利润”。 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="按国家/地区列出的总利润的屏幕截图。":::

1. 另将该地图固定到财务示例仪表板中。

1. 在仪表板上，选择刚刚固定的地图。 再次看它如何打开问答？ 
1. 将光标放在问答框中“按国家/地区”的后面，然后键入“条形图” 。 Power BI 将使用结果创建条形图。

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="条形图可视化效果的屏幕截图。":::

1. 另请将条形图固定到财务示例仪表板中。

4. 选择“退出问答”以返回到仪表板，可在此处看到所创建的新磁贴。 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="固定了问答视觉对象的仪表板的屏幕截图。":::

   你会看到，即使你已在问答中将地图更改为条形图，磁贴仍为地图，这是因为它在固定时就是地图。 

## <a name="step-4-reposition-tiles"></a>步骤 4：重新放置磁贴

可重新排列磁贴，以便更好地利用仪表板的空间。

1. 将“销售总额”折线图的右下角向上拖动，直到它与“销售”磁贴等高，然后松开鼠标。

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="调整磁贴大小的屏幕截图。":::

    现在，上面两个磁贴高度相同。

1. 选择“COGS 平均值”磁贴的“更多选项(...)”>“编辑详细信息” 。 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="磁贴的“更多选项”菜单的屏幕截图。":::

1. 在“标题”框中，键入“已售货物平均成本” > “应用”。

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="“编辑详细信息”对话框的屏幕截图。":::

1. 重新排列其他视觉对象以组合在一起。

    现在效果更好。

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="重新排列后的仪表板的屏幕截图。":::


## <a name="clean-up-resources"></a>清理资源
完成本教程后，现可删除数据集、报表和仪表板。 

1. 在黑色“Power BI”标题栏中选择“我的工作区” 。
2. 选择财务示例数据集旁边的“更多选项(...)”>“删除” 。

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="删除数据集的屏幕截图。":::

    你会看到一则警告，它提示还将删除该数据集中的所有包含数据的报表和仪表板磁贴。

4. 选择“删除”。

## <a name="next-steps"></a>后续步骤

浏览以下关于 Power BI 的 Microsoft Learn 内容集合：

- [了解 Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
- [成为 Power BI 数据分析师](/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm)
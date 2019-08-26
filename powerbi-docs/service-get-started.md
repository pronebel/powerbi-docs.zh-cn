---
title: Power BI 服务入门
description: Power BI 在线服务入门 (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 007819ead82f558efa8179a49dfba9454558dfbb
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995164"
---
# <a name="tutorial-get-started-with-the-power-bi-service-apppowerbicom"></a>教程：Power BI 服务入门 (app.powerbi.com)
本教程可帮助你开始使用 Power BI 服务  。 若要了解 Power BI 服务如何适应其他 Power BI 产品/服务，建议你先阅读[什么是 Power BI](power-bi-overview.md)。

![Power BI Desktop、服务和移动之间的关系](media/service-get-started/power-bi-components.png)

在本教程中，将完成以下步骤：

> [!div class="checklist"]
> * 查找 Power BI 服务的入门内容。
> * 登录 Power BI Online 帐户或进行注册（如果还没有帐户）。
> * 打开 Power BI 服务。
> * 获取一些数据并在报表视图中打开。
> * 使用该数据创建可视化效果并将其另存为报表。
> * 从该报表固定磁贴，创建仪表板。
> * 使用问答自然语言工具将另一个可视化效果添加到仪表板。
> * 删除数据集、报表和仪表板，清理资源。

## <a name="sign-up-for-the-power-bi-service"></a>注册 Power BI 服务
如果没有 Power BI 帐户，请先[注册一个 Power BI Pro 免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)，再进行操作。

拥有帐户后，在浏览器中输入 app.powerbi.com 以打开 Power BI 服务  。 

如果需要 Power BI Desktop 方面的帮助，请参阅 [Power BI Desktop 入门](desktop-getting-started.md)。 如果正在寻找有关 Power BI 移动端的帮助，请参阅[适用于移动设备的 Power BI 应用](consumer/mobile/mobile-apps-for-mobile-devices.md)。

> [!TIP]
> 更喜欢可以自主掌控进度的免费培训课程？ [在 EdX 上注册学习我们的“数据分析和可视化”课程](http://aka.ms/edxpbi)。

请在 YouTube 上观看我们的[播放列表](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP)。 不妨先从观看“Power BI 服务简介”视频入手  ：
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-the-power-bi-service"></a>什么是 Power BI 服务？
Microsoft Power BI 服务有时也称为 Power BI 在线版或 app.powerbi.com。 Power BI 可帮助你及时掌握对你重要的信息。 借助 Power BI 服务，仪表板可帮助你对企业状况了如指掌  。 仪表板显示磁贴，你可选择这些磁贴打开报表来进一步了解详情   。 连接到多个*数据集*将所有相关数据组合在一起。 是否需要帮助了解构成 Power BI 的构建基块？ 请参阅 [Power BI 服务中设计器的基本概念](service-basic-concepts.md)。

如果你在 Excel 或 CSV 文件中具有重要数据，你可以创建 Power BI 仪表板以便随时随地掌握最新信息，并与他人分享自己的见解。  你是否订阅了 SaaS 应用程序（如 Salesforce）？  从连接到 Salesforce 开始，基于该数据自动创建仪表板，或[查看可以连接到的所有其他 SaaS 应用](service-get-data.md)。 如果你是组织成员，请查看是否已向你发布任何[应用](service-create-distribute-apps.md)。

了解所有其他[获取 Power BI 数据](service-get-data.md)的方式。

## <a name="step-1-get-data"></a>步骤 1：获取数据
下面举例说明如何从 CSV 文件中获取数据。 想要学习此教程吗？ [下载财务示例 CSV 文件](http://go.microsoft.com/fwlink/?LinkID=521962)。

1. [登录 Power BI](http://www.powerbi.com/)。 还没有帐户？ 别担心，可以注册一个免费试用版。
2. Power BI 将在浏览器中打开。 在左侧导航栏底部选择“获取数据”  。

    随即将打开“获取数据”页面  。   

3. 在“创建新内容”部分下，选择“文件”   。 
   
   ![获取文件](media/service-get-started/gs1.png)
4.  选择“本地文件”  。
   
     ![“获取数据”>“文件”屏幕](media/service-get-started/gs2.png)

5. 浏览到计算机上的该文件，然后选择“打开”  。

5. 在本教程中，我们将选择“导入”，以将 Excel 文件添加为数据集，然后就可以使用它来创建报表和仪表板  。 如果选择“上传”，则整个 Excel 工作簿都将上传至 Power BI，然后可以在 Excel Online 中打开它并进行编辑  。
   
   ![选择“导入”](media/service-get-started/power-bi-import.png)
6. 数据集准备就绪后，选择“查看数据集”  在报表编辑器中打开它。 

    ![“你的数据集已就绪”对话框](media/service-get-started/power-bi-gs.png)

    由于我们尚未创建任何可视化效果，报表画布是空白的。

    ![空白报表画布](media/service-get-started/power-bi-report-editor.png)

7. 请注意，顶部导航栏上有“读取视图”选项  。 由于具有此选项，这意味着你当前处于“编辑视图”中。 

    ![“阅读视图”选项](media/service-get-started/power-bi-editing-view.png)

    同时，在“编辑视图”中，可以创建和修改报表，因为你是报表的所有者  。 也是创建者  。 与同事共享报表时，他们只能在“阅读视图”中与报表交互，你的同事是使用者  。 详细了解[阅读视图和编辑视图](consumer/end-user-reading-view.md)。
    
    进行[简要了解](service-the-report-editor-take-a-tour.md)是熟悉报表编辑器的一个不错的方法。
 

## <a name="step-2-start-exploring-your-dataset"></a>步骤 2：着手了解你的数据集
连接到数据后，请开始浏览数据。  发现有趣的内容后，可以创建仪表板来监视内容，并查看内容在不同时间的变化。 我们来看看具体的工作方式。
    
1. 在报表编辑器中，使用页面右侧的“字段”窗格生成可视化对象。  选中“销售总额”和“日期”复选框   。
   
   ![字段列表](media/service-get-started/fields.png)

    Power BI 会分析数据并创建可视化对象。 如果先选择“日期”，会看到一个表格  。 如果先选择“销售总额”，会看到一个图表  。 

2. 切换到不同的数据显示方式。 让我们在折线图中查看此数据。 从“可视化对象”窗格中，选择折线图图标  。
   
   ![选择了折线图的报表编辑器](media/service-get-started/gettingstart5new.png)

3. 看起来不错，让我们将它固定到仪表板  。 将鼠标悬停在可视化对象上，并选择固定图标。 固定此可视化对象时，它将存储在仪表板上并会不断更新，由此你可以大致跟踪最新值。
   
   ![固定图标](media/service-get-started/pinnew.png)

4. 由于此报表是新建的，因此在可视化对象固定到仪表板之前，系统会提示保存。 为报表命名（例如“一段时间内的销售额”），然后选择“保存并继续”   。 
   
   ![“保存报表”对话框](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. 将折线图固定到新仪表板并将其命名为“用于教程的财务示例”  。 
   
   ![为报表命名](media/service-get-started/power-bi-pin.png)
   
6. 选择“固定”  。
   
    会显示一条成功消息（右上角附近），告知你可视化效果已作为磁贴添加到你的仪表板中。
   
    ![“已固定到仪表板”对话框](media/service-get-started/power-bi-pin-success.png)

7. 选择“转至仪表板”，查看以磁贴形式固定到新仪表板的折线图  。 通过添加更多可视化效果磁贴和[重命名、调整大小、链接和重新定位磁贴](service-dashboard-edit-tile.md)来优化仪表板。
   
   ![固定了可视化效果的仪表板](media/service-get-started/power-bi-new-dashboard.png)
   
8. 在仪表板上选择新的磁贴，以便返回到报表。 Power BI 会将你返回到报表编辑器的“阅读视图”。 若要切换回“编辑视图”，请从顶部导航栏中选择“编辑报表”。  位于“编辑视图”后，即可继续探索并固定磁贴。 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>步骤 3：使用“问答”继续探索（自然语言查询）
1. 要快速浏览数据，请在问答框中进行询问。 “问答”问题框位于仪表板顶部（提出有关数据的问题），以及报表的顶部导航栏中（提问）   。 例如，在问答框中键入“哪个市场的收入最高”  。
   
   ![问答画布](media/service-get-started/powerbi-qna.png)

2. “问答”会搜索答案，并以可视化形式显示答案。 选择“固定”图标 ![固定图标](media/service-get-started/pbi_pinicon.png) 可在仪表板上显示此可视化效果。
3. 将可视化效果固定到“用于教程的财务示例”仪表板  。
   
    ![“固定到仪表板”对话框](media/service-get-started/power-bi-pin2.png)

4. 返回到仪表板，会看到新磁贴。

   ![固定了图表的仪表板](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>清理资源
完成本教程后，现可删除数据集、报表和仪表板。 

1. 在左侧导航栏中，选择“我的工作区”  。
2. 选择“数据集”  选项卡并找到本教程导入的数据集。  
3. 选择省略号 (...)，再选择“删除”  。

    ![删除数据集](media/service-get-started/power-bi-delete.jpg)

    删除数据集时，Power BI 也将删除报表和仪表板。 


## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [使用 Power BI 连接到要使用的联机服务](service-connect-to-services.md)


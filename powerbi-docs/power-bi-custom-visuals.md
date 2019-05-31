---
title: 在 Power BI 中自定义视觉对象
description: Power BI 中的自定义可视化效果
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 3fd2f3e47c9b6dd2144ed5a66d45e65a00c5b92e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051241"
---
# <a name="custom-visuals-in-power-bi"></a>在 Power BI 中自定义视觉对象

当创建或编辑 Power BI 报表时，可以使用许多不同类型的视觉对象。 对于这些视觉对象图标显示在**可视化效果**窗格。 下载时，这些视觉对象有预打包[Power BI Desktop](https://powerbi.microsoft.com/desktop/)或打开[Power BI 服务](https://app.powerbi.com)。

![可视化效果](media/power-bi-custom-visuals/power-bi-visualizations.png)

但是，您并不限于这组视觉对象。 如果选择在底部的省略号 （...），另一个源的报表视觉对象变得可用-*自定义视觉对象*。

开发人员创建使用自定义视觉对象 SDK 的自定义视觉对象。 这些视觉对象让业务用户若要查看其数据以最符合其业务的方式。 然后，报表作者可以将自定义 visual 文件导入其报表，并使用它们，就像任何其他 Power BI 视觉对象。 自定义视觉对象是 Power BI 中的第一个类成员，且可筛选、 突出显示、 编辑、 共享和等。

自定义视觉对象都将以三种方式部署：

* 自定义视觉对象文件
* 组织视觉对象
* 市场视觉对象

## <a name="custom-visual-files"></a>自定义视觉对象文件

自定义视觉对象是包含用于呈现给他们提供的数据的代码的包。 任何人都可以创建自定义视觉对象并将其打包为单个`.pbiviz`然后到 Power BI 报表中导入的文件。

> [!WARNING]
> 自定义视觉对象可能包含存在安全或隐私风险的代码。 请确保将其导入报表之前信任作者和自定义视觉对象源。

## <a name="organizational-visuals"></a>组织视觉对象

Power BI 管理员批准和部署到其组织，该报表作者可以轻松地发现、 更新和使用自定义视觉对象。 管理员可以轻松地管理 （例如，更新版本，禁用/启用） 这些视觉对象。

 [详细了解组织的视觉对象](power-bi-custom-visuals-organization.md)。

## <a name="marketplace-visuals"></a>市场视觉对象

社区成员和 Microsoft 已提供公共权益其自定义视觉对象并发布到[AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) marketplace。 您可以下载这些视觉对象将其添加到 Power BI 报表。 Microsoft 已测试并得到批准这些自定义视觉对象的功能和质量。

什么是 [AppSource](developer/office-store.md)？ 它是可以为您的 Microsoft 软件查找应用、 加载项和扩展的位置。 [AppSource](https://appsource.microsoft.com/)连接数以百万计的用户的产品与 Office 365、 Azure、 Dynamics 365、 Cortana 和 Power BI，连接到解决方案，帮助他们完成更有效地、 有见地工作一样、 美观地比之前。

### <a name="certified-visuals"></a>已认证的视觉对象

Power BI 取得认证的视觉对象是商城视觉对象，已通过其他严格质量测试，如支持在其他情况下，[电子邮件订阅](https://docs.microsoft.com/power-bi/service-report-subscribe)，和[导出到 PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
若要查看已认证的自定义视觉对象列表或提交你自己的自定义视觉对象，请参阅[已认证的自定义视觉对象](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified)。

你是 Web 开发者吗？对创建自己的可视化效果，并将它们添加到 AppSource 感兴趣吗？ 请参阅[开发 Power BI 自定义视觉对象](developer/custom-visual-develop-tutorial.md)，并了解如何[将自定义视觉对象发布到 AppSource](https://docs.microsoft.com/power-bi/developer/office-store)。

### <a name="import-a-custom-visual-from-a-file"></a>从文件导入自定义视觉对象

1. 选择底部的省略号**可视化效果**窗格。

    ![visualizations2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. 在下拉列表中，选择“从文件导入”  。

    ![从文件导入](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. 从打开文件菜单中，选择`.pbiviz`想要导入，然后选择文件**打开**。 自定义视觉对象的图标添加到底部你**可视化效果**窗格和现已可供在报表中使用。

    ![已导入的 CV](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>导入组织视觉对象

1. 选择底部的省略号**可视化效果**窗格。

    ![视觉对象组织 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. 在下拉列表中，选择“从市场导入”  。

    ![视觉对象组织 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. 从顶部的选项卡菜单中选择“我的组织”  。

    ![视觉对象组织 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. 滚动浏览列表，找到要导入的视觉对象。

    ![视觉对象组织 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. 选择**添加**导入自定义视觉对象。 它的图标添加到底部你**可视化效果**窗格和现已可供在报表中使用。

    ![视觉对象组织 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>从 Microsoft AppSource 下载或导入自定义视觉对象

有两种方法下载和导入自定义视觉对象： 从 Power BI 中来回[AppSource 网站](https://appsource.microsoft.com/)。

### <a name="import-custom-visuals-from-within-power-bi"></a>在 Power BI 中导入自定义视觉对象

1. 选择底部的省略号**可视化效果**窗格。

    ![可视化效果 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. 在下拉列表中，选择“从市场导入”  。

    ![视觉对象组织 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. 滚动浏览列表，找到要导入的视觉对象。

    ![导入视觉对象](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. 若要详细了解某个视觉对象，请选中它。

    ![选择](media/power-bi-custom-visuals/power-bi-select.png)

5. 在详细信息页中，可以查看屏幕截图、视频、详细说明等内容。

    ![摘要](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. 滚动到底部可以查看评论。

    ![审阅](media/power-bi-custom-visuals/power-bi-reviews.png)

7. 选择**添加**导入自定义视觉对象。 它的图标添加到底部你**可视化效果**窗格和现已可供在报表中使用。

    ![已导入的视觉对象](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>从 Microsoft AppSource 下载和导入自定义视觉对象

1. 首先，访问 [Microsoft AppSource](https://appsource.microsoft.com)，并选择“应用”  选项卡。

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. 转到[应用结果页](https://appsource.microsoft.com/marketplace/apps)。在此页中，可以查看每种类别的热门应用，包括 Power BI 应用  。 我们正在寻找自定义视觉对象，因此，让我们选择**Power BI 视觉对象**从左侧的导航列表来缩小结果。

    ![AppSource 视觉对象](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. AppSource 会显示每个自定义视觉对象的磁贴。  每个磁贴具有自定义可视化快照使用的简短说明和下载链接。 如需了解更多详情，请选择磁贴。

    ![自定义选择视觉对象](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. 在详细信息页中，可以查看屏幕截图、视频、详细说明等内容。 选择**立即获取**下载自定义视觉对象并然后同意使用条款。

    ![AppSource 获取](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. 单击自定义视觉对象下载链接。

    ![下载](media/power-bi-custom-visuals/powerbi-custom-download.png)

    下载页还包括有关如何自定义视觉对象导入 Power BI Desktop 和 Power BI 服务的说明。

    还可以下载包含自定义视觉对象并展示其功能的示例报表。

    ![试用示例](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. 保存`.pbiviz`文件，然后再打开 Power BI。

7. 导入`.pbiviz`文件到您的报表。 （请参阅上面的[从文件导入自定义视觉对象](#import-a-custom-visual-from-a-file)部分。）

## <a name="considerations-and-limitations"></a>注意事项和限制

* 导入完成后，自定义视觉对象就已添加到特定报表中。 若要在其他报表中使用此视觉对象，还需要将它导入到相应报表。 使用“另存为”选项保存包含自定义视觉对象的报表时，自定义视觉对象的副本会与新报表一同保存。 

* 如果没有看到**可视化效果**窗格中，这意味着你没有编辑权限的报表。  只能将自定义视觉对象添加到有权编辑的报表，不能添加到与自己共享的报表。

## <a name="troubleshoot"></a>疑难解答

若要进行故障排除，请参阅[故障排除你的 Power BI 自定义视觉对象](power-bi-custom-visuals-troubleshoot.md)。

## <a name="faq"></a>常见问题解答

有关详细信息和问题的答案，请访问[关于 Power BI 自定义视觉对象的常见问题解答](power-bi-custom-visuals-faq.md#organizational-custom-visuals)。

## <a name="next-steps"></a>后续步骤

* [Power BI 报表中的可视化效果](visuals/power-bi-report-visualizations.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)。

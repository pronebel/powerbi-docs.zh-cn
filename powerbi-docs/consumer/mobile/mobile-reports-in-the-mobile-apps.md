---
title: 在 Power BI 移动应用中浏览报表
description: 了解如何在手机或平板电脑上查看 Power BI 移动应用中的报表，并与之交互。 可以在 Power BI 服务或 Power BI Desktop 中创建报表，然后在移动应用中与报表进行交互。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/21/2019
ms.author: mshenhav
ms.openlocfilehash: bee60dd6f3254b049f2445e6e985c625933caf5b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565448"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>在 Power BI 移动应用中浏览报表
适用于：

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Android 手机](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Android 平板电脑](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Windows 10 设备](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android 手机 |Android 平板电脑 |Windows 10 设备 |

Power BI 报表是交互式数据视图，使用视觉对象来表示不同的数据发现和见解。 在 Power BI 移动应用中查看报表是三步流程中的第三步。

1. [在 Power BI Desktop 中创建报表](../../desktop-report-view.md)。 甚至可以在 Power BI Desktop 中[优化报表，使之更适合在手机中显示](mobile-apps-view-phone-report.md)。 
2. 将这些报表发布到 Power BI 服务 [(https://powerbi.com)](https://powerbi.com) 或 [Power BI 报表服务器](../../report-server/get-started.md)。  
3. 然后，与 Power BI 移动应用中的报表进行交互。

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>在移动应用中打开 Power BI 报表
Power BI 报表存储在移动应用中的不同位置，具体取决于从何处获取。 可以位于“应用”、“与我共享”、“工作区”（包括“我的工作区”）或报表服务器中。 有时，可以通过相关仪表板转到报表；有时，其中也会列出报表。

在列表和菜单中，您会发现报表名称旁边的图标帮助您了解此项是报表。 

![我的工作区中的报表](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png) 

有两个图标的 Power BI 移动应用中的报表：

* ![报表图标](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) 表示报表将以横向方式在应用程序提供程序并在浏览器中看上去外观相同。

* ![手机报表图标](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) 指示具有至少一个电话优化的报表页上，将纵向时呈现的报表。 

注意:在环境中保存您的电话，则始终会横向布局，即使报表页具有手机布局。 

若要从仪表板转到报表，请点击磁贴右上角的省略号 （...） >**打开报表**。
  
  ![打开报表](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  并非所有磁贴都包含报表打开选项。 例如，通过在问答框中提问而创建的磁贴就无法在获得点击后打开报表。 
  
## <a name="interacting-with-reports"></a>与报表交互
在应用中打开报表后，可以开始使用它。 有许多您可以使用您的报表和其数据执行的操作。 在报表表尾中，您会发现在报告中，并通过点击和长点击您还可以切片和切块数据的报表中显示的数据可执行的操作。

### <a name="using-tap-and-long-tap"></a>使用点击和长时间点击
点击等于鼠标单击。 因此，如果你想要交叉突出显示报表基于的数据点上，点击该数据点上。
点击切片器值，使选择的值且该值通过对报表的其余部分进行切片。 点击链接上，按钮或书签将激活它根据由作者定义的操作。

您可能注意到，点击视觉对象后，将出现一个边框。 在右上角的边框的没有省略号 （...）。点击它将显示一个具有可以在该视觉对象执行的操作菜单。

![报表视觉对象和菜单](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>工具提示和钻取操作

在长时间点击 （tap 和 hold） 数据点，工具提示将显示呈现此数据点表示的值。 

![报表工具提示](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

报表作者可以定义层次结构中的数据和报表页之间的关系。 层次结构，允许向下的钻取，向下钻和钻取视觉对象并将值的另一个报表页。 因此，长时间的值，除了工具提示中，点击时相关的钻取选项将显示在页脚中。 

![报表钻取操作](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)

通过钻取，Power BI 会在你点击视觉对象的特定部分时，转到报表中的另一页，筛选出点击的值  。  报表作者可定义一个或多个钻取操作，每个操作分别转到不同页面。 在这种情况下，可选择所需的钻取操作。 后退按钮将返回上一个报表页。

了解如何[在 Power BI Desktop 中添加钻取](../../desktop-drillthrough.md)。
   
   > [!IMPORTANT]
   > 在 Power BI 移动应用中，通过的单元值，而不是由列和行标题启用钻取矩阵和表视觉对象中。
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>在报表表尾中使用的操作
当前报表页上或对整个报表，报表表尾具有可以执行的操作。 页脚具有快速访问最有用的操作，并且所有操作都可以从省略号 （...） 的访问权限。

![报表表尾](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

可以在页脚中执行的操作包括：
1) 重置报表筛选器和交叉突出显示选择恢复到其原始状态。
2) 打开会话窗格可以查看或对此报表中添加注释。
3) 打开筛选器窗格可以查看和修改当前报表上应用的筛选器。
4) 列出此报表中的所有页面。 点击页面名称将加载并显示该页面。
可以通过从屏幕的边缘轻扫，到中心完成报表页间移动。
5) 查看所有报表操作。

#### <a name="all-report-actions"></a>所有报表操作
点击上...选项在报表表尾中，将使你可以对报表执行的所有操作。 

![报告所有操作](./media/mobile-reports-in-the-mobile-apps/report-all-actions.png)

某些操作可能已禁用，因为它们依赖于特定的报表功能。
例如：
1) **筛选器的当前位置由**当在报表中的数据分类包含地理位置数据的作者，才启用。 [了解如何识别在报表中的地理数据](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering)。
2) **扫描，以按条形码筛选报表**在报表中的数据集标记为条形码时，才会启用。 [如何在 Power BI Desktop 中标记条形码](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes)。 
3) **邀请**您有权与他人共享此报表时，才会启用。 仅当您是报表的所有者或已由所有者授予重新共享权限，您将具有权限。
4) **批注并共享**是否存在可能会禁用[Intune 保护策略](https://docs.microsoft.com/intune/app-protection-policies)禁止共享 Power BI 移动应用在组织中。 

## <a name="next-steps"></a>后续步骤
* [查看手机优化版 Power BI 报表并与之交互](mobile-apps-view-phone-report.md)
* [创建手机优化版报表](../../desktop-create-phone-report.md)
* 是否有任何问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)


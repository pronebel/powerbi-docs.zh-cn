---
title: 在 Surface Hub 和 Windows 10 上使用演示模式查看报表 - Power BI
description: 阅读有关在 Surface Hub 中显示 Power BI 报表以及在 Windows 10 设备上以全屏模式显示 Power BI 仪表板、报表和磁贴的内容。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 06/28/2020
ms.author: painbar
ms.openlocfilehash: 436ef20a54312f2e169c428cf1d2914bc47eafb0
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85782681"
---
# <a name="view-reports-and-dashboards-in-presentation-mode-on-surface-hub-and-windows-10-devices"></a>在 Windows 10 Surface Hub 设备上使用演示模式查看报表和仪表板
可以使用演示模式在 Windows 10 设备和 Surface Hub 上全屏显示报表和仪表板。 对于在会议中或在办公室内专用投影仪上显示 Power BI，甚至仅将小屏幕上的空间最大化，演示模式都很有用。

![全屏模式下的报表](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-2.png)

在演示模式下：
* 所有“镶边”（如导航栏和菜单栏）都将消失，让你可以更轻松地专注于报表数据。
* 可使用操作工具栏与数据进行交互和控制演示。
* 可以播放在页面、书签或页面和书签之间自动循环的幻灯片。

>[!NOTE]
>我们将于 2021 年 3 月 16 日终止对使用 Windows 10 移动版的手机提供 Power BI 移动应用支持。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="use-presentation-mode"></a>使用演示模式
在 Power BI 移动应用中，点击“全屏”图标，转到全屏模式。
![全屏图标](././media/mobile-windows-10-app-presentation-mode/power-bi-full-screen-icon.png) 应用镶边将消失，操作工具栏显示在屏幕底部或左右两侧（取决于屏幕大小）。

[![报表在全屏模式下带有侧边工具栏](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar-expanded.png#lightbox)

点击工具栏以执行以下操作：

|||
|-|-|
|![返回图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-back-icon.png)|返回上一页。 长按图标会弹出痕迹导航窗口，可导航到报表或仪表板的包含文件夹。|
|![分页图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-pages-icon.png)|翻页以转到演示文稿中报表的另一页。|
|![书签图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-bookmarks-icon.png)|应用书签以显示书签捕获的数据的特定视图。 可以应用个人书签和报表书签。|
|![墨迹图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-ink-icon.png)|使用 Surface 触控笔在报表页上绘制和批注时，可选择墨迹颜色。|
|![橡皮擦图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-eraser-icon.png)|可擦除使用 Surface 触控笔在报表页上绘制和批注的墨迹。          |
|![重置图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-reset-icon.png)|重置为默认视图并清除任何筛选器、切片器或在演示期间可能进行的任何其他数据视图更改。|
|![“共享”图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-share-icon.png)|与同事共享演示文稿视图的图像。 此图像将包含你在演示过程中使用 Surface 触控笔进行的任何批注。|
|![“刷新”图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-refresh-icon.png)|刷新报表。|
|![播放图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-play-icon.png)|播放幻灯片，隐藏操作栏并开始播放。 可以使用选择器选择在页面、书签或页面和书签之间自动切换。 默认情况下，幻灯片每 30 秒在页面之间自动切换一次。 可以在[“设置”>“选项”](#slideshow-settings)中更改这些设置。 请参阅有关幻灯片的[更多详细信息](#slideshows)|
|![退出全屏模式](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-exit-full-screen-icon.png)|退出演示模式。|
|![搜索图标](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-search-icon.png)|搜索 Power BI 中的其他项目。|

可以分离工具栏并将其拖至屏幕的任何位置。 在使用大屏幕的情况下，有时需要专注于报告中的某个特定区域，并且希望此区域旁边有可用工具，这种时候使用此操作就会很方便。 只需将手指放在工具栏上，并将它滑动到报表画布上即可。

[![演示模式下的报表和分离的工具栏](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2-expanded.png#lightbox)

## <a name="slideshows"></a>幻灯片

可以播放幻灯片来自动遍历演示文稿。 可以将幻灯片设置为在页面、书签或页面和书签之间循环切换。

在操作工具栏上选择“播放”按钮时，幻灯片将开始放映。 此时将显示一个控制器，可以通过该控制器暂停幻灯片或更改正在播放的内容：页面、书签或页面和书签。

![幻灯片放映选择器的屏幕截图](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-selector.png)

 控制器显示当前显示的视图的名称（页面或书签和页面）。 在上面的图像中，我们看到在名为“销售”的报表中，我们正在浏览“销售业绩”页的“亚太”书签。 

### <a name="slideshow-settings"></a>幻灯片放映设置

默认情况下，幻灯片会以每 30 秒一个页面的速度遍历各页面。 可转到“设置”>“选项”来更改这些默认设置，如下所示。

![幻灯片放映设置的屏幕截图](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-settings.png)

## <a name="next-steps"></a>后续步骤
* [在 Power BI 服务中的全屏模式下显示仪表板和报表](../end-user-focus.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)


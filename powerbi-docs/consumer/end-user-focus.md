---
title: 焦点模式和全屏模式 - 如何放大以查看更多详细信息
description: 有关在焦点模式或全屏模式下显示 Power BI 仪表板、仪表板磁贴、报表或报表视觉对象的文档
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: dtdLul6otYE
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/09/2020
LocalizationGroup: Common tasks
ms.openlocfilehash: 6385d263c47bde156a7dae941fefb101b9b30d18
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96400445"
---
# <a name="display-content-in-more-detail-focus-mode-and-full-screen-mode"></a>更详细地显示内容：焦点模式和全屏模式

[!INCLUDE [consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]    

<iframe width="560" height="315" src="https://www.youtube.com/embed/dtdLul6otYE" frameborder="0" allowfullscreen></iframe>

焦点模式和全屏模式是在视觉对象、报表和仪表板中查看更多详细信息的两种不同方式。  这两者之间的主要区别在于，全屏模式会删除内容周围的所有窗格，而焦点模式则允许仍然与视觉对象进行交互。 让我们仔细看看相似之处和不同之处。  

|内容    | 焦点模式  |全屏模式  |
|---------|---------|----------------------|
|仪表板     |   不可用     | 是 |
|报表页   | 不可用  | 是|
|报表视觉对象 | 是    | 是 |
|仪表板磁贴 | 是    | 不可用 |
|Windows 10 移动版 | 不可用 | 是 |

在下面的示例中，我们从报表 (1) 开始，在焦点模式 (2) 下打开一个视觉对象，然后在全屏模式 (3) 下打开相同的视觉对象。 

![由三个报表视图组成的屏幕截图](media/end-user-focus/power-bi-reports.png)

## <a name="when-to-use-full-screen-mode"></a>何时使用全屏模式

![仪表板全屏模式前后对照](media/end-user-focus/power-bi-dashboards-focus.png)

显示 Power BI 服务内容（仪表板、报表页和视觉对象），不受菜单和导航窗格的干扰。  可以随时快速获取内容的纯粹而完整的视图。 有时这也称为电视模式。   

如果使用 Power BI 移动版，[全屏可用于 Windows 10 移动应用](./mobile/mobile-windows-10-app-presentation-mode.md)。 

全屏模式的一些用途包括：

* 在会议上展示你的仪表板、视觉对象或报表
* 在办公室通过专用大屏幕或投影仪显示
* 在小屏幕上查看
* 在锁定模式下查看 -- 你可以触摸屏幕或将鼠标悬停在磁贴上，而不打开基础报表或仪表板

## <a name="when-to-use-focus-mode"></a>何时使用焦点模式？

使用“焦点”*_模式可以展开（弹出）视觉对象或磁贴以查看更多详细信息。  你可能有一个有点拥挤的仪表板或报表，你只想在一个视觉对象上放大。  这时候最适合使用焦点模式。  

![仪表板磁贴焦点模式前后对照](media/end-user-focus/power-bi-compare-dash.png)

在焦点模式下，Power BI 业务用户可以与创建此视觉对象时应用的任何筛选器进行交互。  在 Power BI 服务中，可以在仪表板磁贴或报表视觉对象上使用焦点模式。

## <a name="working-in-full-screen-mode"></a>在全屏幕模式下运行

全屏模式可用于仪表板、报表页和报表视觉对象。 

- 要以全屏模式打开仪表板，请选择全屏图标 ![全屏图标](media/end-user-focus/power-bi-full-screen-icon.png) 从顶部菜单栏中。 

- 要以全屏模式打开仪表板，请选择“视图” > “全屏” 。

    ![从“视图”菜单中选择“全屏”](media/end-user-focus/power-bi-view.png)


- 若要在全屏模式下查看视觉对象，请先在焦点模式下打开视觉对象，然后选择“视图” > “全屏” 。  


你选择的内容将填满整个屏幕。 进入全屏模式后，可以使用顶部和底部的菜单栏（报表）或移动光标时显示的菜单（仪表板和视觉对象）进行导航。 由于全屏可用于各种内容，因此导航选项会有所不同。   


  * 选择“后退”、“返回”或“返回到报表”按钮，导航到浏览器中的前一页  。 如果前一页是 Power BI 页面，它也将以全屏模式显示。  全屏模式将一直保持，直到你退出。

  * ![适应屏幕图标](media/end-user-focus/power-bi-fit-to-screen-icon.png)    
    使用“适应屏幕”按钮来尽可能以最大大小显示仪表板，而无需使用滚动条。  

    ![此屏幕截图显示出主机适应屏幕的情况](media/end-user-focus/power-bi-fit-screen.png)

  * ![适应宽度图标](media/end-user-focus/power-bi-fit-width.png)       
    有时你并不关心滚动条，但希望仪表板能横向填充整个可用空间。 选择“适应宽度”按钮。    

    ![此屏幕截图显示“适应宽度”如何更改画布的外观。 ](media/end-user-focus/power-bi-fit-to-width-new.png)

  * ![报表导航图标](media/end-user-focus/power-bi-report-nav2.png)       
    在全屏显示的报表中，使用这些箭头在报表页之间移动。    
  * ![“退出全屏”图标](media/end-user-focus/exit-fullscreen-new.png)     
  若要退出全屏模式，请选择“退出全屏”图标。

      

## <a name="working-in-focus-mode"></a>在焦点模式下运行

焦点模式可用于仪表板磁贴和报表视觉对象。 

- 若要以焦点模式打开仪表板磁贴，请将鼠标悬停在仪表板磁贴或报表视觉对象上，依次选择“更多选项(…)”和“以焦点模式打开”。

    ![磁贴的省略号菜单](media/end-user-focus/power-bi-focus-dashboard.png).. 

- 若要以焦点模式打开报表视觉对象，请将鼠标悬停在视觉对象上并选择“焦点模式”图标 ![焦点模式图标](media/end-user-focus/pbi_popout.jpg)。  

   ![焦点图标显示在磁贴上](media/end-user-focus/power-bi-hover-focus.png)



视觉对象打开并填充整个画布。 请注意，仍有一个可用于与视觉对象交互的“筛选器”窗格。 “筛选器”窗格可以折叠。

   ![磁贴填充报表画布](media/end-user-focus/power-bi-filter.png)


   ![磁贴填充报表画布，并且两个菜单均折叠](media/end-user-focus/power-bi-filter-collapse.png)  

通过[修改筛选器](end-user-report-filter.md)并在数据中查找感兴趣的发现浏览更多内容。 作为业务用户，无法添加新筛选器、更改视觉对象中使用的字段或创建新的视觉对象。  但是，你可以与现有筛选器进行交互。 

对于仪表板磁贴，无法保存所做的更改。 对于报表视觉对象，退出 Power BI 时会保存对现有筛选器所做的任何修改。 如果不希望 Power BI 记住你的修改，可选择“重置为默认值”。 ![“重置为默认值”按钮](media/end-user-focus/power-bi-resets.png)  

通过选择“退出焦点模式”或“返回到报表”（位于视觉对象左上角），退出焦点模式并返回仪表板或报表 。

![“退出焦点模式”按钮](media/end-user-focus/power-bi-exit.png)    

![“返回到报表”图标](media/end-user-focus/power-bi-back-to-report.png)  

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答

* 在报表中将焦点模式用于视觉对象时，将能够查看以下所有筛选器并与其进行交互：视觉对象级别、页面级别、钻取以及报表级别。    
* 在仪表板上将焦点模式用于视觉对象时，将只能够查看视觉对象级别的筛选器并与其进行交互。

## <a name="next-steps"></a>后续步骤

[报表的视图设置](end-user-report-view.md)
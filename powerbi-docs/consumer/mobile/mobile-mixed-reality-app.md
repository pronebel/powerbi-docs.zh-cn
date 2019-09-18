---
title: Power BI for Mixed Reality 应用（预览版）
description: 无论是沉浸在虚拟世界中，还是处于环境上下文中，均可查看 Power BI for Mixed 应用（预览版）中的仪表板和报表。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/05/2018
ms.author: mshenhav
ms.openlocfilehash: 443615a64bee1f4723450c6c8cc3c49feb81989c
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2019
ms.locfileid: "61373944"
---
# <a name="power-bi-for-mixed-reality-app-preview"></a>Power BI for Mixed Reality 应用（预览版）
沉浸在虚拟世界中或将其置于境上下文中的特定位置时，均可查看 Power BI for Mixed Reality 应用（预览版）中的仪表板和报表。 

从 Windows Store [下载 Power BI for Mixed Reality 应用](https://www.microsoft.com/p/power-bi-mobile/9nblgggzlxn1?activetab=pivot%3aoverviewtab)：在 Windows Store 中，称其为“Power BI 移动版”。 在虚拟世界中与仪表板和报表交互，然后选择要放置的内容。 

## <a name="two-views-windows-classic-and-holographic"></a>两种视图：Windows 经典视图和全息视图

Power BI for Mixed Reality 基于 Power BI Windows 移动应用，结合了混合现实的特有功能。 启动 Power BI for Mixed Reality 时，你会进入 Power BI 的 Windows“经典”视图。 在此视图中，可以在你能访问的仪表板和报表之间进行导航。 找到所需的内容时，可以从 Windows 经典视图切换至全息视图。 


## <a name="windows-classic-view-basics"></a>Windows 经典视图的基础知识

如果你不熟悉混合现实体验，请查看此部分。 与混合现实应用交互和与计算机、平板电脑或手机交互是不同的。 在 Windows 经典视图中，混合现实应用响应一套手势和语音命令，这套命令取代了传统的点击鼠标、敲击键盘或者点击手机操作。 

**隔空敲击**

在所有混合现实应用的交互手势中，隔空敲击是最基础的。 手伸直，大拇指和食指相互敲击，此手势类似于点击鼠标或点击手机。  

![混合现实隔空敲击手势](./media/mobile-mixed-reality-app/power-bi-hololens-airtap.png)

在 Power BI 的 Windows 经典应用中，你可以在任何需要鼠标点击的位置进行隔空敲击。 可以通过隔空敲击打开工作区中的仪表板或报表，也可以隔空敲击某个视觉对象的一部分进行筛选或交叉突出显示其他视觉对象等等。

![在 Power BI 中用手隔空敲击](./media/mobile-mixed-reality-app/power-bi-hololens-airtap-hand.png) 

详细阅读关于新的[混合现实中的 Microsoft 手势](https://developer.microsoft.com/windows/mixed-reality/gestures)的内容。

**固定项目** 

隔空敲击“固定”图标 ![Pin icon](./media/mobile-mixed-reality-app/power-bi-hololens-pin.png) 可将 Windows 经典视图的仪表板或报表固定到全息视图  。 可以将很多项目固定到全息视图。 

**切换到全息视图**

在固定 Windows 经典视图中的项后，隔空敲击“全屏显示”图标 ![Full screen icon](./media/mobile-mixed-reality-app/power-bi-hololens-fullscreen.png) 可切换到全息视图  。 


## <a name="holographic-view-basics"></a>全息视图的基础知识

现在进入了全息视图，之前固定的所有项目都在停靠带中。 你可以将这些固定好的项目放置在现实空间的任何位置，例如放在项目所描述的设备旁边。 在全息视图中，语音命令可与手势互补。 下面是一些常见的语音命令。

**“跟随我”** 

选取一个 Power BI 项目，它将停留在你的主要视野并跟随你的视线移动，直到将它放置到某个位置。

**“停靠”** 

使用“停靠”命令可以将项目放入 Power BI 停靠带，于是该项目虽然不在你的主要视野，但也会跟随你，方便你访问。

**“放在这里”**

使用此命令可以将仪表板或报表放置在墙上或物体上，或者悬停在空中。

![将仪表板悬停在空中](./media/mobile-mixed-reality-app/power-bi-hololens-place-visuals.png)

**“转到主页”**

说“转到主页”可以返回 Power BI 经典 Windows 视图。 

**“删除”**

使用此命令可以从全息视图中删除某个项目。

**“全部删除”** 

使用此命令可以从全息视图中删除所有项目。


## <a name="scan-a-report-qr-code-in-holographic-view"></a>在全息视图中扫描报表 QR 码

在全息视图中可以扫描报表的 QR 码，就像[使用适用于 iPhone 和 Android 的 Power BI 移动应用扫描 QR 码](mobile-apps-qr-code.md)一样。

- 进入全息视图时，注视 QR 码。 Power BI 会打开此 QR 码关联的报表。

## <a name="limitations-and-considerations"></a>限制和注意事项

全息视图有几点限制和注意事项。

- 你不会看到在 Windows 经典视图中设置的交叉筛选或突出显示的内容。
- 这些固定仪表板和报表的视图是私有的。 我们暂时不支持共享体验。
- 随着数据变化，仪表板和报表每 45 秒会刷新一次。


## <a name="next-steps"></a>后续步骤

- [使用 Power BI 移动应用从真实世界获取数据](mobile-apps-data-in-real-world-context.md)

 




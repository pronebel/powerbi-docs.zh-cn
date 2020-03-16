---
title: 在 Apple Watch 上的移动应用中浏览 Power BI 数据
description: Power BI Apple Watch 应用
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: e2014f359d4085ab0dcb85135f7436c9e403eaab
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114518"
---
# <a name="explore-your-data-in-the-power-bi-mobile-app-on-your-apple-watch"></a>在 Apple Watch 上的 Power BI 移动应用中浏览数据
Power BI Apple Watch 应用可以让你在手表上从 Power BI 仪表板查看 KPI 和卡磁贴。 KPI 和卡磁贴最适合在小屏幕上提供心跳测量。 可以从 iPhone 或 Watch 自身刷新仪表板。

## <a name="install-the-apple-watch-app"></a>安装 Apple Watch 应用
因为 Power BI Apple Watch 应用绑定了适用于 iOS 的 Power BI 应用，所以当你从 Apple 应用商店[将 Power BI 应用下载到你的 iPhone](https://go.microsoft.com/fwlink/?LinkId=522062 "下载 iPhone 应用") 时，也会自动下载 Power BI Watch 应用。 Apple 指南说明了如何[安装 Apple Watch 应用程序](https://support.apple.com/HT204784)。

## <a name="use-the-power-bi-app-on-the-apple-watch"></a>在 Apple Watch 上使用 Power BI 应用
从手表的 springboard 或直接从手表表盘单击 Power BI 小组件（如果已配置），以获取 Power BI Apple Watch 应用。

![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_complicatn240arrow.png)

Power BI Apple Watch 应用由两部分组成。

* “索引屏幕”  允许快速浏览已同步的仪表板的所有 KPI 和卡磁贴。
  
  ![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_indexscreen240.png)
* **处于焦点的磁贴**：单击索引屏幕上的磁贴以深入查看某个特定磁贴。
  
  ![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_kpi.png)

## <a name="refresh-a-dashboard-from-your-apple-watch"></a>从 Apple Watch 刷新仪表板
可以直接从 Watch 刷新同步的仪表板。

* 在 Watch 应用上的仪表板视图中，按住屏幕并选择“**刷新**”。

Watch 应用会立即将仪表板与 Power BI 服务中的数据同步。

> [!NOTE]
> Watch 应用通过 iPhone 上的 Power BI 移动应用与 Power BI 通信。 因此，Power BI 应用必须至少在 iPhone 的后台运行，才能使 Watch 应用上的仪表板刷新。
> 
> 

## <a name="refresh-a-dashboard-on-your-apple-watch-from-your-iphone"></a>从 iPhone 刷新 Apple Watch 上的仪表板
还可以从 iPhone 刷新 Apple Watch 上的仪表板。

1. 在 iPhone 上的 Power BI 中，打开你想要同步到 Apple Watch 的仪表板。 
2. 选择“更多选项”(...) >“与 Watch 同步”   。

Power BI 将显示仪表板已同步到手表的指示器。

一次只能同步一个仪表板到手表。

> [!TIP]
> 若要在你的手表上查看来自多个仪表板的磁贴，请在 Power BI 服务中新建仪表板并向其固定所有相关磁贴。
> 
> 

## <a name="set-a-custom-power-bi-widget"></a>设置自定义 Power BI 小组件
还可以直接在 Apple Watch 表盘上显示某个特定的 Power BI 磁贴，所以它随时可见且可访问。

Power BI Apple Watch 小组件更新的时间接近数据更新的时间，请将所需的信息始终保持最新状态。

### <a name="add-a-power-bi-widget-to-your-watch-face"></a>向手表表盘添加 Power BI 小组件
请参阅 Apple 指南中的[自定义你的 Apple Watch 表盘](https://support.apple.com/HT205536)。

### <a name="change-the-text-on-the-widget"></a>更改小组件上的文本
针对 Apple Watch 表盘上的小空间，Power BI Apple Watch 应用可以让你更改小组件的标题以适应小空间。

* 在 iPhone 上，转到 Appe Watch 控制应用，选择 Power BI，导航到小组件名称字段，并键入一个新的名称。
  
  ![Apple Watch](./media/mobile-apple-watch/pbi_aplwatch_oniphone.png)

> [!NOTE]
> 如果未更改名称，则 Power BI 小组件将把名称缩短至可适应手表表盘的小空间的字符数。 
> 
> 

## <a name="next-steps"></a>后续步骤
你的反馈有助于我们决定在未来实现什么，所以不要忘记为你希望在 Power BI 移动应用中实现的其他功能投票。 

* 下载 [Power BI iPhone 移动应用](https://go.microsoft.com/fwlink/?LinkId=522062)
* 关注 [Twitter 上的 @MSPowerBI](https://twitter.com/MSPowerBI)
* 加入 [Power BI 社区](https://community.powerbi.com/)的对话


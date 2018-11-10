---
title: 认证的 Power BI 自定义可视化效果
description: 提交自定义视觉对象以供认证的要求和过程。 已认证的自定义视觉对象的列表。
author: mihart
ms.author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 10/30/2018
ms.openlocfilehash: 72b09083c50a88e2d22e9aa22f54ff014dafa998
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223435"
---
# <a name="getting-a-custom-visual-certified"></a>让自定义视觉对象取得认证

## <a name="what-is-meant-by-certified"></a>取得认证是指什么？

取得认证的自定义视觉对象是指已满足一系列代码要求且已通过严格的安全测试。  自定义视觉对象取得认证后，它可以[导出到 PowerPoint 中](consumer/end-user-powerpoint.md)，并显示在用户[订阅报表页](consumer/end-user-subscribe.md)后收到的电子邮件中。 当然，它还可以用作[标准自定义视觉对象](power-bi-custom-visuals.md)，添加到 Power BI 服务和 Power BI Desktop 报表中，并在 Power BI 移动中查看和嵌入。

你是 Web 开发者吗？对创建自己的可视化效果，并将它们添加到 [Microsoft AppSource](https://appsource.microsoft.com) 感兴趣吗？ 请参阅[开发 Power BI 自定义视觉对象](developer/custom-visual-develop-tutorial.md)，了解如何操作。

## <a name="certification-requirements"></a>认证要求

* Microsoft AppSource 已批准
* 自定义视觉对象是使用经版本控制的 API 1.2 或更高版本进行编写
* 代码存储库可供审核（例如，可通过 GitHub 审核视觉对象代码）
* 仅使用可审核的公共 OSS 组件
* 不访问外部服务或资源

> 提示：建议结合使用 EsLint 与默认安全规则集，以便在提交之前预先验证代码。

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>提交自定义视觉对象以供认证的过程

提交自定义视觉对象以供认证：

1. 向 Power BI 自定义视觉对象支持人员 (pbicvsupport@microsoft.com) 发送电子邮件。 在电子邮件中，添加以下信息：    

   * 标题：视觉对象认证申请
   * 指向托管视觉对象源代码的 GitHub 存储库的链接
   * 符合要求（见上文）
   * 通过代码和安全审核

2. Microsoft 自定义视觉对象团队会通知你自定义视觉对象已取得认证并添加到“取得认证”列表（见下文）中，或自定义视觉对象已遭拒，并随附一份报告，在其中列出需要解决的问题。 开发者负责维护与 Microsoft 建立开放式沟通渠道，并根据需要更新取得认证的视觉对象。

## <a name="removal-of-power-bi-certified-custom-visuals"></a>删除 Power BI 认证的自定义视觉对象

Microsoft 可能会自行从“取得认证”列表中删除视觉对象。  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>取得认证的自定义视觉对象的列表

| AppSource 链接 | 链接到视频 |
| --- | --- |
| [星状体图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft 日历](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) | |
| [MAQ 软件蝴蝶结图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) | [视频](https://youtu.be/So5xKMSpVJI) |
| [框和须线图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) | |
| [MAQ 软件箱线图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) | [视频](https://youtu.be/JoHaFLfhXdo) |
| [MAQ 软件砖形图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | [视频](https://youtu.be/hA3DOsvn2xY) |
| [Akvelon 气泡图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) | |
| [项目符号图表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [视频](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) | [视频](https://youtu.be/mtvUNl9bMjA) |
| [Tallan 的日历](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) | |
| [OKViz K 线图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | [视频](https://youtu.be/nT_18gyRxPo) |
| [Card with States by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Chiclet 切片器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) | |
| [和弦](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) | [视频](https://youtu.be/AQvd2FhRyCI) |
| [MAQ 软件圆形仪表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) | [视频](https://youtu.be/9NHXALkBXuY) |
| [群集映射](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) | |
| [MAQ 软件圆柱仪表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | [视频](https://youtu.be/DgdoWi7Gcxo) |
| [度盘式仪表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) | |
| [点图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) | |
| [OKViz 的点阵图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) | [视频](https://youtu.be/By16pX9KT40) |
| [向下钻取变形地图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) | |
| [向下钻取分级统计图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) | |
| [向下钻取柱形图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) | [视频](https://youtu.be/lBy2gQQ5YsQ) |
| [向下钻取基于时间的数据的柱形图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | [视频](https://youtu.be/T_mRou18vx0) |
| [向下钻取环形图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | [视频](https://youtu.be/AUVFrSHmPeo) |
| [双 KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380983) | [视频](https://youtu.be/Z-tl97BpEr0) |
| [增强散点图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | [视频](https://youtu.be/xCfM0cjM4do) |
| [Enlighten 水族馆](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) | |
| [Enlighten 切片器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) | |
| [Enlighten 洗牌排序法](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Enlighten 方格百分比图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [按 Devscope 列表筛选](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381413) | [视频](https://youtu.be/RetEWGwBu0I) |
| [Force-Directed Graph](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) | [视频](https://youtu.be/YsTa7uyJ4sg) |
| [MAQ 软件带有源的漏斗图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) | [视频](https://youtu.be/R_EcimsLI8U) |
| [甘特图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [视频](https://youtu.be/qJ7s_KrGiUU) |
| [MAQ 软件甘特图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) | [视频](https://youtu.be/vJLV9JRCpI8) |
| [全球数据条](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) | |
| [MAQ 软件网格](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380825) | [视频](https://youtu.be/VOPoDJgZfOY) |
| [Akvelon 层次结构图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) | [视频](https://youtu.be/0ZGzJaq_KT4) |
| [直方图图表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) | |
| [MAQ 软件含点直方图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) | [视频](https://youtu.be/-ILF--wExrw) |
| [MAQ 软件水平漏斗图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) | [视频](https://youtu.be/SudZei68PPo) |
| [CloudScope 映像](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) | |
| [映像网格](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) | |
| [信息图设计器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) | |
| [Akvelon KPI 图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) | |
| [MAQ 软件 KPI 列](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380996) | [视频](https://youtu.be/rU0xoOlIq1U) |
| [MAQ 软件 KPI 网格](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380947) | [视频](https://youtu.be/dM4PvZh71V0) |
| [KPI 指示器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [MAQ 软件 KPI 股票代码](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | [视频](https://youtu.be/cudG4gsZ2V8) |
| [MAQ 软件线性仪表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) | [视频](https://youtu.be/7_jFaM30dkc) |
| [点线图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) | |
| [马赛克图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) | [视频](https://youtu.be/90FLCKpgicA) |
| [多 KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381763) | |
| [CloudScope 概述](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381477) | |
| [播放轴（动态切片器）](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [视频](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI 矩阵](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) | [视频](https://youtu.be/1enze8pcGzY) |
| [脉冲图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) | [视频](https://youtu.be/DQWdcQtjDVw) |
| [MAQ 软件象限图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) | [视频](https://youtu.be/ppBnyhqWNC0) |
| [雷达图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) | |
| [MAQ 软件环形图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) | [视频](https://youtu.be/pDToHDFHnq8) |
| [MAQ 软件旋转图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) | [视频](https://youtu.be/d5xBCMmb3hU) |
| [Sankey 图表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) | [视频](https://youtu.be/WWP9wVUHGaA) |
| [滚动条](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) | [视频](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) | [视频](https://youtu.be/0m3Vnvso9tY) |
| [Stream 关系图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) | |
| [通过 OKViz 实现的摘要面板](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380873) | |
| [热度地图表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) | |
| [转速计](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [视频](https://youtu.be/C3OXdETbS9o) |
| [文本筛选器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) | |
| [MAQ 软件文本包装器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [MAQ 软件温度计](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380847) | [视频](https://youtu.be/SPX9mgrAdBc) |
| [时间刷切片器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380798) | |
| [时间线切片器](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) | [视频](https://youtu.be/ozMtZ4_NZ10) |
| [CloudScope 时间线](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381427) | [视频](https://youtu.be/szNi9YgXFJc) |
| [飓风图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [视频](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [MAQ 软件贸易图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) | [视频](https://youtu.be/xhTR6y6J9Ko) |
| [终极方差](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) | [视频](https://youtu.be/pDYF8iZxERs) |
| [终极瀑布图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | [视频](https://youtu.be/0BZsVCQdEkc) |
| [CloudScope 用户列表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) | |
| [方格百分比图](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) | [视频](https://youtu.be/1vRqYUsm3Vk) |
| [Word Cloud](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [视频](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>后续步骤

* [开发 Power BI 自定义视觉对象](developer/custom-visual-develop-tutorial.md)
* [YouTube 上的 Microsoft 自定义视觉对象播放列表](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI 中的可视化效果](visuals/power-bi-report-visualizations.md)  
* [Power BI 中的自定义可视化效果](power-bi-custom-visuals.md)  
* [将自定义视觉对象发布到 Microsoft AppSource](developer/office-store.md)  

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)
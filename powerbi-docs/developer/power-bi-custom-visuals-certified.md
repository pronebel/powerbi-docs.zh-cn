---
title: 已认证的 Power BI 视觉对象
description: 提交自定义视觉对象以供认证的要求和过程。 以及已认证的 Power BI 视觉对象的列表。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999735"
---
# <a name="get-a-power-bi-visual-certified"></a>获取 Power BI 视觉对象认证

已认证的 Power BI 视觉对象是*市场*中满足由 *Microsoft Power BI 团队*测试和批准的某些*指定代码*要求的视觉对象。 测试旨在检查并确认视觉对象不会访问外部服务或资源。

已认证的 Power BI 视觉对象与[标准 Power BI 视觉对象](power-bi-custom-visuals.md)的使用方法相同。 可将已认证的 Power BI 视觉对象添加到 [Power BI Desktop](../desktop-what-is-desktop.md) 和 [Power BI 服务](../power-bi-service-overview.md)，并通过 [Power BI 移动版](../consumer/mobile/mobile-apps-for-mobile-devices.md)和 [Power BI Embedded](embedding.md) 查看。

认证过程是一个可选的过程。 由开发人员决定是否需要对市场中的 Power BI 视觉对象进行认证。 Power BI 视觉对象一旦通过认证，将提供更多功能。 例如，可[导出到 PowerPoint](../consumer/end-user-powerpoint.md)，或者，如果用户[订阅了报表页](../consumer/end-user-subscribe.md)，则可在收到的电子邮件中的显示视觉对象。

未经认证的 Power BI 视觉对象并不一定是不安全的视觉对象。 某些视觉对象未经认证，是因为它们与一个或多个[认证要求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)不符。 例如，连接到外部服务的地图视觉对象，或使用商业库的视觉对象。

如果 Web 开发人员有兴趣创建自己的 Power BI 视觉对象并将其添加到  [Microsoft AppSource](https://appsource.microsoft.com)，可从 [开发 Power BI 视觉对象](visuals/custom-visual-develop-tutorial.md)教程开始入手。

> [!NOTE]
> Microsoft 不是第三方 Power BI 视觉对象的作者。 若要验证第三方视觉对象的功能，建议客户直接联系视觉对象的作者。

> [!IMPORTANT]
> Microsoft 可自行从[经认证列表](#list-of-power-bi-visuals-that-have-been-certified)中删除 Power BI 视觉对象。

## <a name="certification-requirements"></a>认证要求

若要使 Power BI 视觉对象通过[认证](#get-a-power-bi-visual-certified)，请确保 Power BI 视觉对象符合本节中所列的要求。 

> [!TIP]
> 建议结合使用 EsLint 与默认安全规则集，以便在提交之前预先验证代码。

* Microsoft 卖家面板或合作伙伴中心已批准。 Power BI 视觉对象应位于我们的[市场](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中。
* Power BI 视觉对象是使用 API v2.5 或更高版本编写的。
* Power BI 团队可以查看代码存储库。 例如，可通过 GitHub 使用源代码（JavaScript 或 TypeScript）的可读格式。

    >[!NOTE]
    > 无需在 Github 中公开共享代码。

* 代码存储库要求：
  * 必须包含以下文件：
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * 不得包含 node_modules 文件夹（将 node_modules 添加到 .gitingore* 文件）。
  * npm install 命令不得返回任何错误。
  * npm audit 命令不得返回任何具有高级别或中等级别的警告。
  * pbiviz package 命令不得返回任何错误。
  * 必须包括 [Microsoft 提供的 TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib)，且没有重写的配置。 此命令不得返回任何 Lint 错误。
   * Power BI 视觉对象的编译包必须匹配已提交的包（两个文件的 md5 哈希应相等）。
* 源代码要求：
   * Power BI 视觉对象必须支持[呈现事件 API](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/)。
   * 确保未运行任何任意/动态代码 (bad: eval(), unsafe to use of settimeout(), requestAnimationFrame(), setinterval(some function with user input), running user input/data)。
   * 确保安全地操作 DOM (bad: innerHTML, D3.html(<一些用户/数据输入>)，在将用户输入/数据添加到 DOM 之前，先对其进行清理。
   * 确保浏览器控制台中的任何输入数据均没有 javascript 错误/异常。 用户可能会将 Power BI 视觉对象与不同范围的异常数据一起使用，因此，视觉对象不容失败。 可以将此[示例报表](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)用作测试数据集。

* 如果更改了 capabilities.json 文件中的任何属性，请确保更改不会破坏现有的用户报表。

* 确保 Power BI 视觉对象符合 [Power BI 视觉对象指南](./guidelines-powerbi-visuals.md)。
    
* 你的代码只能使用可供审核的公用 OSS 组件，例如公用 Javascript 或 TypeScript 库。 源代码必须可供审核，且无已知漏洞。 我们无法验证使用商业组件的自定义视觉对象。

* Power BI 视觉对象不得访问外部服务或资源。 例如，任何 HTTP/S 或 WebSocket 请求都不能从 Power BI 外部发送到任何服务。 

## <a name="submitting-a-power-bi-visual-for-certification"></a>提交 Power BI 视觉对象用于认证

可以通过合作伙伴中心请求 Power BI 团队认证 Power BI 视觉对象。

>[!TIP]
>Power BI 认证过程可能需要一段时间。 如果要创建新的 Power BI 视觉对象，建议在请求 Power BI 认证之前，通过合作伙伴中心发布 Power BI 视觉对象。 这样可以确保不会延迟视觉对象的发布。

请求 Power BI 认证的步骤：

1. 登录到合作伙伴中心。
2. 在“概述”页上，选择你的 Power BI 视觉对象，然后转到“产品”设置页。
3. 选中“请求 Power BI 认证”复选框。
4. 在“审阅并发布”页的“认证说明”文本框中，提供指向源代码的链接以及访问它所需的凭据。

>[!NOTE]
> 如果在 Power BI 的视觉对象提交过程中需要使用[卖家面板](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store)（旧的管理工具），请查看[卖家面板认证提交流程](seller-dashboard.md#seller-dashboard-certification-submission-process)说明。

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>已认证的 Power BI 视觉对象的列表

| 链接 | 视频 |
| --- | --- |
| [3AG 系统 - 具有相对方差的条形图](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) | |
| [3AG 系统 - 具有相对方差的柱形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [高级环形图视觉对象](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [高级网络可视化效果](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [高级 TimeSeries 视觉对象](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [高级组合图视觉对象](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [星状体图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft 日历](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [MAQ 软件蝴蝶结图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [视频](https://youtu.be/So5xKMSpVJI) |
| [框和须线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [MAQ 软件箱线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [视频](https://youtu.be/JoHaFLfhXdo) |
| [MAQ 软件砖形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [视频](https://youtu.be/hA3DOsvn2xY) |
| [Akvelon 气泡图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [项目符号图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [视频](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [视频](https://youtu.be/mtvUNl9bMjA) |
| [Tallan 的日历](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [OKViz K 线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [视频](https://youtu.be/nT_18gyRxPo) |
| [Card with States by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet 切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [和弦](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [视频](https://youtu.be/AQvd2FhRyCI) |
| [MAQ 软件圆形仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [视频](https://youtu.be/9NHXALkBXuY) |
| [群集映射](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [MAQ 软件圆柱仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [视频](https://youtu.be/DgdoWi7Gcxo) |
| [度盘式仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [点图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [OKViz 的点阵图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [视频](https://youtu.be/By16pX9KT40) |
| [向下钻取变形地图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [向下钻取分级统计图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [向下钻取柱形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [视频](https://youtu.be/lBy2gQQ5YsQ) |
| [向下钻取基于时间的数据的柱形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [视频](https://youtu.be/T_mRou18vx0) |
| [向下钻取环形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [视频](https://youtu.be/AUVFrSHmPeo) |
| [双 KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [视频](https://youtu.be/Z-tl97BpEr0) |
| [增强散点图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [视频](https://youtu.be/xCfM0cjM4do) |
| [Enlighten 水族馆](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten 切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten 洗牌排序法](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten 方格百分比图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [按 Devscope 列表筛选](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [视频](https://youtu.be/RetEWGwBu0I) |
| [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [视频](https://youtu.be/YsTa7uyJ4sg) |
| [MAQ 软件带有源的漏斗图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [视频](https://youtu.be/R_EcimsLI8U) |
| [甘特图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [视频](https://youtu.be/qJ7s_KrGiUU) |
| [MAQ 软件甘特图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [视频](https://youtu.be/vJLV9JRCpI8) |
| [全球数据条](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [MAQ 软件网格](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [视频](https://youtu.be/VOPoDJgZfOY) |
| [Akvelon 层次结构图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [视频](https://youtu.be/0ZGzJaq_KT4) |
| [直方图图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [MAQ 软件含点直方图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [视频](https://youtu.be/-ILF--wExrw) |
| [MAQ 软件水平漏斗图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [视频](https://youtu.be/SudZei68PPo) |
| [CloudScope 映像](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [映像网格](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [信息图设计器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [Akvelon KPI 图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [MAQ 软件 KPI 列](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [视频](https://youtu.be/rU0xoOlIq1U) |
| [MAQ 软件 KPI 网格](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [视频](https://youtu.be/dM4PvZh71V0) |
| [KPI 指示器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [MAQ 软件 KPI 股票代码](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [视频](https://youtu.be/cudG4gsZ2V8) |
| [MAQ 软件线性仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [视频](https://youtu.be/7_jFaM30dkc) |
| [点线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [马赛克图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [视频](https://youtu.be/90FLCKpgicA) |
| [多 KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [CloudScope 概述](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [播放轴（动态切片器）](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [视频](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI 矩阵](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [视频](https://youtu.be/1enze8pcGzY) |
| [脉冲图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [视频](https://youtu.be/DQWdcQtjDVw) |
| [MAQ 软件象限图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [视频](https://youtu.be/ppBnyhqWNC0) |
| [雷达图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [MAQ 软件环形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [视频](https://youtu.be/pDToHDFHnq8) |
| [MAQ 软件旋转图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [视频](https://youtu.be/d5xBCMmb3hU) |
| [Sankey 图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [视频](https://youtu.be/WWP9wVUHGaA) |
| [Akvelon 散点图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [滚动条](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [视频](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [视频](https://youtu.be/0m3Vnvso9tY) |
| [Stream 关系图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [通过 OKViz 实现的摘要面板](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [热度地图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [转速计](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [视频](https://youtu.be/C3OXdETbS9o) |
| [文本筛选器](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [MAQ 软件文本包装器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [MAQ 软件温度计](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [视频](https://youtu.be/SPX9mgrAdBc) |
| [时间刷切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [时间线切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [视频](https://youtu.be/ozMtZ4_NZ10) |
| [CloudScope 时间线](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [视频](https://youtu.be/szNi9YgXFJc) |
| [飓风图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [视频](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [MAQ 软件贸易图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [视频](https://youtu.be/xhTR6y6J9Ko) |
| [终极方差](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [视频](https://youtu.be/pDYF8iZxERs) |
| [终极瀑布图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [视频](https://youtu.be/0BZsVCQdEkc) |
| [CloudScope 用户列表](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [方格百分比图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [视频](https://youtu.be/1vRqYUsm3Vk) |
| [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [视频](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>常见问题解答

有关视觉对象的详细信息，请参阅[关于认证视觉对象的常见问题解答](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)。

## <a name="next-steps"></a>后续步骤

* [开发 Power BI 自定义视觉对象](../developer/custom-visual-develop-tutorial.md)
* [YouTube 上的 Microsoft 自定义视觉对象播放列表](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI 中的可视化效果](../visuals/power-bi-report-visualizations.md)  
* [Power BI 中的自定义可视化效果](power-bi-custom-visuals.md)  
* [将 Power BI 视觉对象发布到 Microsoft AppSource](../developer/office-store.md)  

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

---
title: 已认证的 Power BI 视觉对象
description: 提交自定义视觉对象以供认证的要求和过程，以及已认证 Power BI 视觉对象的列表。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2019
ms.openlocfilehash: 04954397a16fecddabca63067c903dee742873ef
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925573"
---
# <a name="get-a-power-bi-visual-certified"></a>获取 Power BI 视觉对象认证

已认证的 Power BI 视觉对象是 [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) 中满足 Microsoft Power BI 团队[代码要求](#certification-requirements)的视觉对象。 将对这些视觉对象进行测试，以验证它们是否无法访问外部服务或资源，以及是否遵循安全编码模式和指导原则。

Power BI 视觉对象一旦通过认证，将提供更多功能。 例如，可[导出到 PowerPoint](../consumer/end-user-powerpoint.md)，或者，如果用户[订阅了报表页](../consumer/end-user-subscribe.md)，则可在收到的电子邮件中的显示视觉对象。

认证过程是可选的。 未经认证的 Power BI 视觉对象不一定是不安全的 Power BI 视觉对象。 某些 Power BI 视觉对象未经认证，是因为它们与一个或多个[认证要求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)不符。 例如，连接到外部服务的 Power BI 地图视觉对象，或使用商业库的 Power BI 视觉对象。

> [!NOTE]
> Microsoft 不是第三方 Power BI 视觉对象的作者。 若要验证第三方视觉对象的功能，请直接联系视觉对象的作者。

## <a name="certification-requirements"></a>认证要求

若要使 Power BI 视觉对象通过[认证](#get-a-power-bi-visual-certified)，Power BI 视觉对象必须符合本节中所列的要求。 

### <a name="general-requirements"></a>一般要求

Power BI 视觉对象必须由卖方仪表板或合作伙伴中心批准。 建议 Power BI 视觉对象已在 [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) 中。 若要了解如何将 Power BI 视觉对象发布到 AppSource，请参阅[将 Power BI 视觉对象发布到合作伙伴中心](office-store.md)。

提交 Power BI 视觉对象之前，请验证它是否符合 [Power BI 视觉对象的准则](./guidelines-powerbi-visuals.md)。

提交 Power BI 视觉对象时，请确保已编译的包与提交的包完全匹配。

### <a name="code-repository-requirements"></a>代码存储库要求

尽管你无需在 GitHub 中公开共享代码，但该代码存储库必须可供 Power BI 团队查看。 实现此目的的最佳方式是在 GitHub 中提供源代码（JavaScript 或 TypeScript）。

存储库必须只包含一个 Power BI 视觉对象的代码。 它不能包含多个 Power BI 视觉对象的代码或不相关的代码。

存储库必须包含名为“认证”  的分支。 此分支中的源代码必须与提交的包匹配。 如果正在重新提交 Power BI 视觉对象，则只能在下一次提交过程中更新此代码。

如果 Power BI 视觉对象使用私有 npm 包或 git 子模块，则必须提供对包含此代码的其他存储库的访问权限。

### <a name="file-requirements"></a>文件要求

使用最新版本的 API 编写 Power BI 视觉对象。

存储库必须包含以下文件：
* **.gitignore** - 将 `node_modules` 添加到此文件。 该代码不能包含 node_modules  文件夹。
* **capabilities.json** - 如果你提交的是Power BI 视觉对象的较新版本，并对该文件中的属性进行了更改，请验证它们不会中断现有用户的报表。
* **pbiviz.json**
* **package.json**
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>命令要求

请确保以下命令不会返回任何错误。

* `npm install`
* `pbiviz package`
* `npm audit` - 不得返回任何具有高级别或中等级别的警告。
* [Microsoft 提供的 TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib)，没有重写的配置。 此命令不得返回任何 Lint 错误。

### <a name="compiling-requirements"></a>编译要求

使用最新版本的 [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) 编写 Power BI 视觉对象。

必须用 `pbiviz package` 编译 Power BI 视觉对象。 如果你使用自己的生成脚本，请提供 `npm run package` 自定义生成命令。



### <a name="source-code-requirements"></a>源代码要求

验证是否遵循 [Power BI 视觉对象的其他认证](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification)策略列表。 如果提交未遵循这些指导原则，则合作伙伴中心的拒绝电子邮件将包含此链接中列出的策略编号。

请遵循下面列出的代码要求，确保代码符合 Power BI 认证策略。  

**必需**
* 只能使用可供审核的公用 OSS 组件，例如公用 JavaScript 或 TypeScript 库。
* 代码必须支持[呈现事件 API](./visuals/event-service.md)。
* 确保已安全操作 DOM。 在将用户输入或用户数据添加到 DOM 之前，对其使用清理。
* 将此[示例报表](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)用作测试数据集。

**不允许**
* 访问外部服务或资源。 例如，任何 HTTP/S 或 WebSocket 请求都不能从 Power BI 外部发送到任何服务。
* 使用 `innerHTML` 或 `D3.html(user data or user input)`。
* 浏览器控制台中的任何输入数据均没有 JavaScript 错误/异常。
* 任意或动态代码（如 `eval()`）、不安全使用 `settimeout()`、`requestAnimationFrame()`、`setinterval(user input function)` 及用户输入或用户数据。
* 缩小的 JavaScript 文件或项目。

## <a name="submitting-a-power-bi-visual-for-certification"></a>提交 Power BI 视觉对象用于认证

可以通过合作伙伴中心请求 Power BI 团队认证 Power BI 视觉对象。

>[!TIP]
>Power BI 认证过程可能需要一段时间。 如果要创建新的 Power BI 视觉对象，建议在请求 Power BI 认证之前，通过合作伙伴中心发布 Power BI 视觉对象。 这样可以确保不会延迟视觉对象的发布。

请求 Power BI 认证的步骤：

1. 登录到合作伙伴中心。
2. 在“概述”页  上，选择你的 Power BI 视觉对象，然后转到“产品”  设置页。
3. 选中“请求 Power BI 认证”  复选框。
4. 在“审阅并发布”  页的“认证说明”  文本框中，提供指向源代码的链接以及访问它所需的凭据。

>[!NOTE]
> 如果在 Power BI 的视觉对象提交过程中需要使用[卖家面板](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store)（旧的管理工具），请查看[卖家面板认证提交流程](seller-dashboard.md#seller-dashboard-certification-submission-process)说明。

## <a name="certified-power-bi-visuals"></a>已认证的 Power BI 视觉对象

已认证的 Power BI 视觉对象如下所示。 单击此链接可在 AppSource 中打开 Power BI 视觉对象。 如果有视频，可以单击视频链接观看视频。

* [3AG 系统 - 具有绝对方差的条形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG 系统 - 具有相对方差的条形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [3AG 系统 - 具有相对方差的柱形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG 系统 - 具有方差的柱形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [高级环形图视觉对象（完整版）](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [高级环形图视觉对象（精简版）](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [高级图形视觉对象](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [高级网络可视化效果](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [高级时序视觉对象（完整版）](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [星状体图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft 日历](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [MAQ 软件蝴蝶结图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [框和须线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [MAQ 软件箱线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [MAQ 软件砖形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Akvelon 气泡图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [项目符号图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)，[视频链接](https://youtu.be/AOlsFYkfkcw) 
* [项目符号图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [OKViz 项目符号图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953)，[视频链接](https://youtu.be/mtvUNl9bMjA) 
* [MAQ 软件日历](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Tallan 的日历](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [OKViz K 线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952)，[视频链接](https://youtu.be/nT_18gyRxPo) 
*  [Card with States by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet 切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [和弦](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761)，[视频链接](https://youtu.be/AQvd2FhRyCI) 
*  [MAQ 软件圆形仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [群集映射](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Akvelon 自定义日历](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [MAQ 软件圆柱仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [度盘式仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[点图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [OKViz 点图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949)，[视频链接](https://youtu.be/By16pX9KT40) 
*  [向下钻取变形地图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [向下钻取分级统计图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [向下钻取柱形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857)，[视频链接](https://youtu.be/lBy2gQQ5YsQ) 
*  [基于时间的数据的向下钻取柱形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881)，[视频链接](https://youtu.be/T_mRou18vx0) 
*  [向下钻取环形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)，[视频链接](https://youtu.be/AUVFrSHmPeo) 
*  [双 KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [增强散点图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762)，[视频链接](https://youtu.be/xCfM0cjM4do) 
*  [Enlighten 水族馆](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten 切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten 洗牌排序法](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten 方格百分比图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [按 Devscope 列表筛选](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413)，[视频链接](https://youtu.be/RetEWGwBu0I) 
*  [力导向图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764)，[视频链接](https://youtu.be/YsTa7uyJ4sg) 
*  [MAQ 软件带有源的漏斗图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [甘特图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765)，[视频链接](https://youtu.be/qJ7s_KrGiUU) 
* [MAQ 软件甘特图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [全球数据条](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [MAQ 软件网格](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Akvelon 层次结构图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333)，[视频链接](https://youtu.be/0ZGzJaq_KT4) 
*  [直方图图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [MAQ 软件含点直方图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [水平条形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [MAQ 软件水平漏斗图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [CloudScope 映像](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [映像网格](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [信息图设计器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [Akvelon KPI 图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [MAQ 软件 KPI 列](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [MAQ 软件 KPI 网格](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI 指示器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [MAQ 软件 KPI 股票代码](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [MAQ 软件线性仪表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [点线图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [马赛克图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785)，[视频链接](https://youtu.be/90FLCKpgicA) 
*  [多 KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [CloudScope 概述](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [播放轴（动态切片器）](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083)，[视频链接](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI 矩阵](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299)，[视频链接](https://youtu.be/1enze8pcGzY) 
*  [脉冲图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006)，[视频链接](https://youtu.be/DQWdcQtjDVw) 
*  [MAQ 软件象限图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [雷达图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [MAQ 软件环形图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [MAQ 软件旋转图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey 图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777)，[视频链接](https://youtu.be/WWP9wVUHGaA) 
*  [Akvelon 散点图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [滚动条](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [OKViz 智能筛选器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859)，[视频链接](https://youtu.be/gcJsDDRQq28) 
*  [OKViz 迷你图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910)，[视频链接](https://youtu.be/0m3Vnvso9tY) 
*  [Stream 关系图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [通过 OKViz 实现的摘要面板](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [热度地图表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [转速计](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937)，[视频链接](https://youtu.be/C3OXdETbS9o) 
*  [文本筛选器](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [MAQ 软件文本包装器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [MAQ 软件温度计](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [时间刷切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [时间线切片器](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786)，[视频链接](https://youtu.be/ozMtZ4_NZ10) 
*  [CloudScope 时间线](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427)，[视频链接](https://youtu.be/szNi9YgXFJc)
*  [飓风图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768)，[视频链接](https://www.youtube.com/watch?v=AQvd2FhRyCI) 
*  [MAQ 软件贸易图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [终极 KPI 卡](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [终极方差](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140)，[视频链接](https://youtu.be/pDYF8iZxERs) 
*  [终极瀑布图](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956)，[视频链接](https://youtu.be/0BZsVCQdEkc) 
*  [CloudScope 用户列表](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [MAQ 软件文氏图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [小提琴图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio 视觉对象](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [方格百分比图](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049)，[视频链接](https://youtu.be/1vRqYUsm3Vk) 
*  [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752)，[视频链接](https://youtu.be/AblTenl9fqo) 

## <a name="faq"></a>常见问题解答

有关视觉对象的详细信息，请参阅[关于认证视觉对象的常见问题解答](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)。

## <a name="next-steps"></a>后续步骤

* [开发 Power BI 自定义视觉对象](../developer/custom-visual-develop-tutorial.md)
* [YouTube 上的 Microsoft 自定义视觉对象播放列表](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI 中的可视化效果](../visuals/power-bi-report-visualizations.md)  
* [Power BI 中的自定义可视化效果](power-bi-custom-visuals.md)  
* [将 Power BI 视觉对象发布到 Microsoft AppSource](../developer/office-store.md) 
* 如果 Web 开发人员有兴趣创建自己的 Power BI 视觉对象并将其添加到  [Microsoft AppSource](https://appsource.microsoft.com)，可从 [开发 Power BI 视觉对象](visuals/custom-visual-develop-tutorial.md)教程开始入手。 

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

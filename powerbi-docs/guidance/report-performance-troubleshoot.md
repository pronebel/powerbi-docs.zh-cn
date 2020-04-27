---
title: Power BI 中的报表性能疑难解答
description: 用于诊断 Power BI 中报表性能缓慢的故障排除指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: a5230a39706ce5d6941c00386160fe10114442e1
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81527982"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Power BI 中的报表性能疑难解答

本文提供的指南可帮助开发人员和管理员解决报表性能缓慢的故障。 它适用于 Power BI 报表，也适用于 Power BI 分页报表。

如果报表用户在与切片器或其他功能交互时遇到加载速度缓慢的报表，或更新速度缓慢的报表，则可能会发现慢速报表。 报表托管在高级容量上时，还可以通过监视 [Power BI Premium 指标应用](../service-admin-premium-monitor-capacity.md)来识别慢速报表。 此应用程序可帮助你监视 Power BI Premium 订阅的运行状况和容量。

## <a name="follow-flowchart-steps"></a>遵循流程图步骤

使用以下流程图帮助了解性能缓慢的原因，并确定要执行的操作。

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="图像显示本文完整介绍的流程图。" border="true":::

有六个流程图终止符，每个终止符描述要执行的操作：

|终止符|操作|
|---------|---------|
|![流程图终止符 1。](media/common/icon-01-red-30x30.png)|管理容量<br />扩展容量 |
|![流程图终止符 2。](media/common/icon-02-red-30x30.png)|调查使用典型报表期间的容量活动|
|![流程图终止符 3。](media/common/icon-03-red-30x30.png)|体系结构更改<br />考虑 Azure Analysis Services<br />检查本地网关|
|![流程图终止符 4。](media/common/icon-04-red-30x30.png)|考虑 Azure Analysis Services<br />考虑 Power BI Premium|
|![流程图终止符 5。](media/common/icon-05-red-30x30.png)|使用 Power BI Desktop 性能分析器<br />优化报表、模型或 DAX|
|![流程图终止符 6。](media/common/icon-06-red-30x30.png)|提交支持工单|

## <a name="take-action"></a>执行操作

第一个注意事项是了解慢速报表是否托管在高级容量上。

### <a name="premium-capacity"></a>高级容量

报表托管在高级容量上时，请使用 Power BI Premium Metrics 应用来确定报表托管容量是否经常超过容量资源  。 CPU 频繁超过 80% 时就属于这种情况。 对于内存，当[活动内存指标](../service-premium-metrics-app.md#the-active-memory-metric)超过 50 时就属于这种情况。 资源面临压力时，可能需要[管理或扩展容量](../service-admin-premium-manage.md)（流程图终止符 1）。 当资源充足时，在使用典型报表期间调查容量活动（流程图终止符 2）。

### <a name="shared-capacity"></a>共享容量

报表托管在共享容量上时，无法监视容量运行状况。 这是需要采取其他调查方法。

首先，确定性能缓慢是否发生在一天或一个月的特定时间。 如果是，并且许多用户刚好在这些时间打开报表，请考虑以下两种方案：

- 通过将数据集迁移到 [Azure Analysis Services ](/azure/analysis-services/analysis-services-overview)或高级容量以提高查询吞吐量（流程图终止符 4）。
- 使用 Power BI Desktop [性能分析器](../desktop-performance-analyzer.md)了解视觉对象和 DAX 公式等报表元素的性能。 它特别适用于确定是查询还是视觉对象呈现引发的性能问题（流程图终止符 5）。

如果确定没有时间模式，接下来请考虑性能缓慢是否仅限于特定地理位置或区域。 如果是，则数据源可能距离遥远，并且网络通信速度很慢。 在这种情况下，请考虑：

- 使用 [Azure Analysis Services ](/azure/analysis-services/analysis-services-overview)更改体系结构（流程图终止符 3）。
- 优化[本地数据网关性能](/data-integration/gateway/service-gateway-performance)（流程图终止符 3）。

最后，如果确定没有时间模式，并且所有区域的性能都很慢，请调查在特定设备、客户端或 Web 浏览器上是否出现性能缓慢  。 如果没有，请使用 Power BI Desktop [性能分析器](../desktop-performance-analyzer.md)（如前面所述）来优化报表或模型（流程图终止符 5）。

确定特定设备、客户端或 Web 浏览器导致性能缓慢时，我们建议通过 [Power BI 支持页](https://powerbi.microsoft.com/support/)创建支持工单（流程图终止符 6）。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [Power BI 指南](index.yml)
- [监视报表性能](monitor-report-performance.md)
- [性能分析器](../desktop-performance-analyzer.md)
- 白皮书：[规划 Power BI Enterprise 部署](https://go.microsoft.com/fwlink/?linkid=2057861)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com/)

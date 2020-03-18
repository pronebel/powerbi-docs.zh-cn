---
title: Power BI 嵌入式分析中的容量和 SKU
description: 了解 Power BI 嵌入式分析中的容量和 SKU。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 27d6ddd9b24e09805bd22150a22347e5cd93c8e0
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2020
ms.locfileid: "79492827"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Power BI 嵌入式分析中的容量和 SKU

当移动到生产环境时，Power BI 嵌入式分析需要专用的容量（A、EM 或 P SKU）来发布嵌入式 Power BI 内容    。

容量是为独占式使用而保留的一组专用资源。 通过容量，你可向用户发布仪表板、报表和数据集，而无需购买按用户分配的许可证。 它还为内容提供稳定可靠的性能。

>[!NOTE]
>需要拥有一个 Power BI Pro 帐户才能发布。

## <a name="what-is-embedded-analytics"></a>什么是嵌入式分析？

Power BI 嵌入式分析包括两个解决方案：
* *Power BI Embedded* - Azure 产品/服务
* 在 Power BI Premium 中嵌入 Power BI - Office 产品/服务 

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded 适用于想要将视觉对象嵌入到其应用程序中的 ISV 和开发人员。

使用 Power BI Embedded 的应用程序允许用户使用 Power BI Embedded 容量中存储的内容。

### <a name="power-bi-premium"></a>Power BI Premium

对于需要完整 BI 解决方案的企业而言，[Power BI Premium](../../service-premium-what-is.md) 可以提供组织、合作伙伴、客户和供应商的单一视图。

Power BI Premium 是一款 SaaS 产品，能够让用户通过移动应用、内部开发的应用或 Power BI 门户（Power BI 服务）使用内容。 这使 Power BI Premium 能够为面向内部和外部客户的应用程序提供解决方案。

## <a name="capacity-and-skus"></a>容量和 SKU

每个容量提供一系列的 SKU，每个 SKU 为内存和计算能力提供不同的资源层。 所需的 SKU 类型取决于要部署的解决方案类型。

要了解每个层支持的工作负载，请参阅[在 Premium 容量中配置工作负载](../../service-admin-premium-workloads.md)一文

若要计划并测试容量，请使用以下链接：
* [容量规划](embedded-capacity-planning.md)
* [测试方法](../../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Power BI Embedded SKU

Power BI Embedded 随附了 [a SKU  ](../../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)。

### <a name="power-bi-premium-skus"></a>Power BI Premium SKU

Power BI premium 提供两个 SKU，P 和 EM   。
* [了解 P 和 EM SKU 的区别](../../service-premium-what-is.md#subscriptions-and-licensing)  
* [购买 Premium SKU](../../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>我应该使用哪个 SKU？

本表概述了功能、所需的容量以及每项功能所需的特定 SKU。 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>功能</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>已使用了什么？</em><p></td>
<td><p><em>正在使用什么？</em><p></td>
<td style="text-align: center"><p><em>A SKU</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>EM SKU</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>P SKU</br>(Office)</em></p></td>
</tr>
<tr>
<td>从 Power BI 工作区嵌入项目</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Power BI 报表</td>
<td>适用于你的组织的嵌入应用程序</br>（用户拥有数据）</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>适用于你的客户的嵌入应用程序</br>（应用拥有数据）</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Power BI 内容<br>（使用免费 Power BI 许可证）</td>
<td>Power BI 服务</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI 移动版</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>MS Office 应用</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>容量注意事项

下表列出了每个容量的支付和使用注意事项。

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>产品</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center;">每小时</td>
<td style="text-align: center;">每月</td>
<td style="text-align: center;">每月</td>
</tr>
<tr>
<td><p><strong>承诺</strong></td>
<td style="text-align: center;">无</td>
<td style="text-align: center;">每年</td>
<td style="text-align: center;">每月或每年</td>
</tr>
<tr>
<td valign="top"><p><strong>使用情况</strong></td>
<td style="text-align: center;">Azure 资源可以是：</br>- <a href="azure-pbie-scale-capacity.md">横向或纵向扩展</a></br>- <a href="azure-pbie-pause-start.md">暂停并恢复</a>
</td>
<td style="text-align: center;">嵌入到应用和</br> Microsoft 应用程序</td>
<td style="text-align: center;">嵌入到应用和</br> Power BI 服务</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU 内存和计算能力

下表介绍每个 SKU 的资源和限制。

| 容量节点 | 总虚拟核心 | 后端 V 核心 | RAM (GB) | 前端 V 核心 | DirectQuery/Live Connection（每秒） | 模型刷新并行度 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
>[为客户嵌入内容](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[为组织嵌入内容](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [从应用嵌入内容](embed-from-apps.md)
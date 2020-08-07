---
title: DAX 示例模型
description: 用于支持参考文章的 DAX 示例模型。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/25/2020
ms.author: v-pemyer
ms.openlocfilehash: 6e2fe331fa274305447266321893204dddcc3148
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537449"
---
# <a name="dax-sample-model"></a>DAX 示例模型

Adventure Works DW 2020 Power BI Desktop 示例模型设计用于支持 DAX 学习。 该模型基于 AdventureWorksDW2017 的 [Adventure Works 数据仓库示例](/sql/samples/adventureworks-install-configure#data-warehouse-downloads)，但数据已经过修改以匹配示例模型的目标。

## <a name="scenario"></a>方案

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="显示 Adventure Works 公司徽标的图像。":::

Adventure Works 公司代表一家自行车制造商，将自行车及其配件销售到全球市场。 该公司的数据仓库数据存储在 Azure SQL 数据库中。

## <a name="model-structure"></a>模型结构

模型包含七个表：

|表|说明|
|-----|-------|
|**Customer**|描述客户及其地理位置。 客户在线购买产品（Internet 销售）。|
|**Date**|Date 与 Sales 表之间存在三种关系，分别表示订单日期、发货日期和截止日期。 订单日期关系处于活动状态。 公司以每年 7 月 1 日为会计年度的起始日进行销售报告。 使用 Date 列将表标记为日期表。|
|**Product**|仅存储已完成的产品。|
|**Reseller**|描述经销商及其地理位置。 经销商向自己的客户销售产品。|
|**Sales**|在每个销售订单行存储一行。 所有财务价值均以美元 (USD) 为单位。 最早订单日期为 2017 年 7 月 1 日，最晚订单日期为 2020 年 6 月 15 日。|
|**Sales Order**|描述销售订单和订单行号，以及销售渠道（经销商还是 **Internet**）。 此表与 Sales 表之间存在一对一的关系。|
|**Sales Territory**|销售区域按组（北美、欧洲和太平洋）、国家和地区显示。 只有美国在区域级别销售产品。|

该模型不包含任何 DAX 计算。

## <a name="download-sample"></a>下载示例

可以在[此处](https://aka.ms/dax-docs-sample-file)下载 Power BI Desktop 示例模型文件。

## <a name="next-steps"></a>后续步骤

有关本文的详细信息，请参阅以下资源：

- [数据分析表达式 (DAX) 引用](/dax/)
- 学习路径：[在 Power BI Desktop 中使用 DAX](https://docs.microsoft.com/learn/paths/dax-power-bi/)
- 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)
- 建议？ [提出改进 Power BI 的想法](https://ideas.powerbi.com)

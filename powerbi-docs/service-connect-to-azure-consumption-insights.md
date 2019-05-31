---
title: 使用 Power BI 连接到 Microsoft Azure Consumption Insights
description: 适用于 Power BI 的 Microsoft Azure Consumption Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222128"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>使用 Power BI 连接到 Microsoft Azure Consumption Insights
可使用 Power BI 内容包在 Power BI 中浏览和监视 Microsoft Azure 的消耗数据。 一天一次自动刷新的数据。

连接到适用于 Power BI 的 [Microsoft Azure Consumption Insights 内容包](https://app.powerbi.com/getdata/services/azureconsumption)。

## <a name="how-to-connect"></a>如何连接
1. 选择左侧导航窗格底部的**获取数据**。
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. 在**服务**框中，选择**获取**。
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. 选择**Microsoft Azure Consumption Insights** \> **立即获取**。 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. 提供要导入的数据的月数以及你的 Azure Enterprise 注册号。 有关详细信息，请参阅下面的[查找这些参数](#FindingParams)。
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. 提供访问密钥进行连接。 可以在 Azure EA 门户中找到你的注册密钥。 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. 导入过程会自动开始。 完成后，新的仪表板、 报表和模型将显示在导航窗格中。 选择仪表板查看已导入的数据。
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](service-dashboard-edit-tile.md)。
* [选择磁贴](consumer/end-user-tiles.md)以打开基础报表。
* 虽然你的数据集计划每日刷新，可以更改刷新计划或尝试刷新根据需要使用**立即刷新**

## <a name="whats-included"></a>包含的内容
Microsoft Azure Consumption Insights 内容包包括每月报表提供连接时的月份范围的数据。 范围是范围不断变化，因此包含的日期会随着数据集刷新更新。

## <a name="system-requirements"></a>系统要求
内容包需要访问 Azure 门户中的企业功能。 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>查找参数
Power BI 报表仅适用于 EA 直接、 合作伙伴和间接客户可以查看计费信息。 在下面阅读有关查找连接流程所需要的值的每个详细信息。

**月数**

* 从今天你想要导入数据的月份 (1-36) 数。

**注册号**

* 在 Azure Enterprise 注册号，您可以在找到[Azure Enterprise Portal](https://ea.azure.com/)下的主屏幕**合约详细信息**。
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**访问密钥**

* 可以在 Azure Enterprise 门户中，找到你的访问密钥**下载使用情况** > **API 访问密钥**。
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**其他帮助**

* 有关更多帮助设置 Azure Enterprise Power BI 包，在登录到 Azure 企业门户并查看 API 帮助文件下**帮助**。 此外可以找到下的其他说明**报表** -> **下载使用情况** -> **API 访问密钥**。

## <a name="next-steps"></a>后续步骤
[Power BI 入门](service-get-started.md)

[在 Power BI 中获取数据](service-get-data.md)


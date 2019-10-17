---
title: 使用 Power BI 连接到 Microsoft Azure Consumption Insights
description: 适用于 Power BI 的 Microsoft Azure Consumption Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020438"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>使用 Power BI 连接到 Microsoft Azure Consumption Insights
可使用 Power BI 内容包在 Power BI 服务中浏览和监视 Microsoft Azure 的消耗数据。 此数据每天自动刷新一次。

连接到适用于 Power BI 服务的 [Microsoft Azure 使用见解内容包](https://app.powerbi.com/getdata/services/azureconsumption)。

> [!NOTE]
> 对于自定义更强的设置，请尝试使用 Power BI Desktop 中的 [Azure 使用见解连接器](desktop-connect-azure-consumption-insights.md)。

## <a name="how-to-connect"></a>如何连接
1. 在 Power BI 服务中，选择左侧导航窗格底部的“获取数据”  。
   
    ![获取数据](media/service-connect-to-azure-consumption-insights/getdata.png)
2. 在**服务**框中，选择**获取**。
   
   ![获取服务](media/service-connect-to-azure-consumption-insights/services.png)
3. 选择“Microsoft Azure 使用见解”  \>“立即获取”  。 
   
   ![立即获取](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. 提供要导入的数据的月数以及你的 Azure Enterprise 注册号。 请参阅下面有关[查找这些参数](#FindingParams)的详细信息。
   
    ![连接到 Microsoft Azure 使用见解](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. 提供访问密钥进行连接。 可以在 Azure EA 门户中找到注册密钥。 
   
    ![Microsoft Azure 使用见解：密钥](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. 导入过程会自动开始。 导入完成后，在导航窗格中将会出现新的仪表板、报表和模型。 选择仪表板查看已导入的数据。
   
   ![Microsoft Azure 使用见解仪表板](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](service-dashboard-edit-tile.md)。
* [选择磁贴](consumer/end-user-tiles.md)以打开基础报表。
* 虽然数据集按计划每日刷新，但可更改刷新计划或根据需要使用“立即刷新”来尝试刷新 

## <a name="whats-included"></a>包含的内容
Microsoft Azure 使用见解内容包中包含你在连接时提供的月份范围的每月报表数据。 该范围是不断变化的时间窗口，因此包含的日期会随着数据集刷新而更新。

## <a name="system-requirements"></a>系统要求
该内容包需要可以在 Azure 门户中访问企业功能。 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>查找参数
Power BI 报表可用于能够查看计帐信息的 EA 直接客户、合作伙伴和间接客户。 有关查找连接流程所需的每个值的详细信息，请阅读以下内容。

**月数**

* 当前要导入的数据的月数 (1-36)。

**注册号**

* 你的 Azure Enterprise 注册号，可以在 [Azure Enterprise 门户](https://ea.azure.com/)主屏幕上的“注册详细信息”  下找到。
  
    ![合约编号](media/service-connect-to-azure-consumption-insights/params2.png)

**访问密钥**

* 可以在 Azure Enterprise 门户中的“下载使用情况” > “API 访问密钥”下找到访问密钥   。
  
    ![访问密钥](media/service-connect-to-azure-consumption-insights/creds2.png)

**其他帮助**

* 有关设置 Azure Enterprise Power BI 包的其他帮助，请登录到 Azure Enterprise 门户，然后查看“帮助”下的 API 帮助文件  。 也可以在“报表”   -> “下载使用情况”   -> “API 访问密钥”  下找到其他说明。
* 对于自定义更强的设置，请尝试使用 Power BI Desktop 中的 [Azure 使用见解连接器](desktop-connect-azure-consumption-insights.md)。

## <a name="next-steps"></a>后续步骤

Power BI Desktop 中的 [Azure 使用见解连接器](desktop-connect-azure-consumption-insights.md)

[在 Power BI 中获取数据](service-get-data.md)


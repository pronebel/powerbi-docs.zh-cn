---
title: Power BI 中的 SQL Server Analysis Services 实时数据
description: Power BI 中的 SQL Server Analysis Services 实时数据。 这是通过为企业网关配置的数据源来实现。
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: Minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 08/10/2017
LocalizationGroup: Data from databases
ms.openlocfilehash: 51efec6c78dbb29b9c3dc760284c7bb3c8711bdc
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769930"
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>Power BI 中的 SQL Server Analysis Services 实时数据

在 Power BI 中，有两种方法可以连接到实时的 SQL Server Analysis Services 服务器。 获取数据  时，可以连接到 SQL Server Analysis Services 服务器，或者可以连接到已连接到 Analysis Services 服务器的 [Power BI Desktop 文件](service-desktop-files.md)或 [Excel 工作簿](service-excel-workbook-files.md)。 根据最佳做法，Microsoft 强烈建议使用 Power BI Desktop，因为它提供丰富的工具集，并且能够在本地维护 Power BI Desktop 文件的备份副本。

>[!IMPORTANT]
> * 若要连接到实时的 Analysis Services 服务器，管理员必须安装并配置本地数据网关。 有关详细信息，请参阅[本地数据网关](service-gateway-onprem.md)。
> * 当使用网关时，你的数据将保留在本地。  你基于数据创建的报表保存在 Power BI 服务中。 
> * [问答自然语言查询](service-q-and-a-direct-query.md)对 Analysis Services 实时连接以预览提供。

## <a name="to-connect-to-a-model-from-get-data"></a>要在获取数据时连接到一个模型

1. 在“我的工作区”  中，选择“获取数据”  。 你还可以切换到组工作区中，如果有的话。

   ![连接到获取数据按钮](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)

2. 选择**数据库和其他**。

   ![连接以获取数据 1](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)

3. 选择 **SQL Server Analysis Services** > **连接**。

   ![连接以获取数据 2](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)

4. 选择一个服务器。 如果你未看见此处列出任何服务器，则表示未配置网关和数据源，或者在网关中的数据源的**用户**选项卡中未列出你的帐户。 请与管理员确认。

5. 选择想要连接到的模型。 该模型可以是表格或多维模型。

连接到模型后，该模型将在 Power BI 站点的**我的工作区/数据集**中显示。 如果切换到组工作区，那么数据集将在组中显示。

![连接到数据集](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>在推入数据时

如果将视觉对象从报表固定到仪表板，那么将每 10 分钟自动刷新固定的磁贴。 如果更新了本地 Analysis Services 服务器中的数据，那么 10 分钟后会自动更新磁贴。

## <a name="common-issues"></a>常见问题

* 无法加载模型架构错误 - 连接到 SSAS 的用户无权访问 SSAS 数据库、多维数据集和模型时，会发生此错误。

## <a name="next-steps"></a>后续步骤

* [On-premises data gateway (本地数据网关)](service-gateway-onprem.md)  
* [管理 Analysis Services 数据源](service-gateway-enterprise-manage-ssas.md)  
* [本地数据网关故障排除](service-gateway-onprem-tshoot.md)  

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)
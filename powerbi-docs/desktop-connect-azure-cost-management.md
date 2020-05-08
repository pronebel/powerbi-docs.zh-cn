---
title: 在 Power BI Desktop 中连接到 Azure 成本管理数据
description: 使用 Power BI Desktop 轻松连接到 Azure，并获取有关 Azure 成本的见解
author: davidiseminger
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ed6832bd92ca2bea0d64bbaeb41569b6a8fb6ddc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "77026683"
---
# <a name="create-visuals-and-reports-with-the-azure-cost-management-connector-in-power-bi-desktop"></a>使用 Power BI Desktop 中的 Azure 成本管理连接器创建视觉对象和报表

可以使用适用于 Power BI Desktop 的 Azure 成本管理连接器来创建功能强大的自定义可视化效果和报表，帮助你更好地了解 Azure 支出。 Azure 成本管理连接器目前支持签订了 [Microsoft 客户协议](https://azure.microsoft.com/pricing/purchase-options/microsoft-customer-agreement/)或[企业协议 (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/) 的客户。  

Azure 成本管理连接器使用 OAuth 2.0 向 Azure 进行身份验证，并识别要使用连接器的用户。 在此过程中生成的令牌在特定时间段内有效。 Power BI 保留用于下一次登录的令牌。 OAuth 2.0 是在后台执行的进程的标准，可确保安全地处理这些权限。 若要进行连接，必须使用[企业管理员](https://docs.microsoft.com/azure/billing/billing-understand-ea-roles)帐户（对于企业协议）或[计费帐户所有者](https://docs.microsoft.com/azure/billing/billing-understand-mca-roles)（对于 Microsoft 客户协议）。 

> [!NOTE]
> 此连接器取代了先前可用的 [Azure 使用见解和 Azure 成本管理 (Beta)](desktop-connect-azure-consumption-insights.md) 连接器。 使用之前的连接器创建的任何报表都必须使用此连接器重新创建。

## <a name="connect-using-azure-cost-management"></a>使用 Azure 成本管理连接

若要在 Power BI Desktop 中使用 Azure 成本管理连接器  ，请执行以下步骤：

1.  在“主页”功能区中，选择“获取数据”   。
2.  从数据类别列表中选择“Azure”  。
3.  选择“Azure 成本管理”  。

    ![获取数据](media/desktop-connect-azure-cost-management/azure-cost-management-00b.png)

4. 在出现的对话框中，输入“计费对象信息 ID”  （对于“Microsoft 客户协议”  ），或“合约编号”  （对于“企业协议 (EA)”）  。 


## <a name="connect-to-a-microsoft-customer-agreement-account"></a>连接到 Microsoft 客户协议帐户 

若要连接到 Microsoft 客户协议  帐户，可以从 Azure 门户获取“计费对象信息 ID”  ：

1.  在 [Azure 门户](https://portal.azure.com/)中，导航至“成本管理和计费”  。
2.  选择计费对象信息。 
3.  在菜单中的“设置”  下，在边栏中选择“属性”  。
4.  在“计费对象信息”  下，复制“ID”  。 
5.  对于“选择范围”  ，选择“计费对象信息 ID”  并粘贴上一步中的计费对象信息 ID。 
6.  输入月数并选择“确定”  。

    ![获取计费 ID](media/desktop-connect-azure-cost-management/azure-cost-management-01a.png)

7.  出现提示时，请使用你的 Azure 用户帐户和密码登录。 


## <a name="connect-to-an-enterprise-agreement-account"></a>连接到企业协议帐户

若要连接到企业协议 (EA) 帐户，可以从 Azure 门户获取合约 ID：

1.  在 [Azure 门户](https://portal.azure.com/)中，导航至“成本管理和计费”  。
2.  选择计费帐户。
3.  在“概述”  菜单上，复制“计费帐户 ID”  。
4.  对于“选择范围”  ，选择“合约编号”  并粘贴上一步中的计费帐户 ID。 
5.  输入月数，然后选择“确定”  。

    ![获取计费 ID](media/desktop-connect-azure-cost-management/azure-cost-management-01b.png)

6.  出现提示时，请使用你的 Azure 用户帐户和密码登录。 

## <a name="data-available-through-the-connector"></a>通过连接器提供的数据

成功经过身份验证后，将显示“导航器”  窗口，其中包含以下可用数据表：



| **表格** | **说明** |
| --- | --- |
| **余额汇总** | 企业协议(EA) 余额的摘要。 |
| **计费事件** | 提供新发票、信用点数购买等信息的事件日志。仅适用于 Microsoft 客户协议。 |
| **预算** | 提供预算详细信息，以查看针对现有预算目标的实际成本或使用情况。 |
| **费用** | 提供 Azure 使用情况、市场费用和单独计费的月级别小结。 仅适用于 Microsoft 客户协议。 |
| **额度批次** | 为提供的计费对象信息提供 Azure 额度批次购买详情。 仅适用于 Microsoft 客户协议。 |
| **价目表** | 提供的计费对象信息或 EA 合约的适用计量费率。 |
| **RI 费用** | 过去 24 个月与预留实例相关联的费用。 |
| **RI 建议（共享）** | 根据过去 7 天、30 天或 60 天所有订阅的使用趋势得出的预留实例购买建议。 |
| **RI 建议（单个）** | 根据过去 7 天、30 天或 60 天单个订阅的使用趋势得出的预留实例购买建议。 |
| **RI 使用情况详细信息** | 上个月现有预留实例的使用情况详细信息。 |
| **RI 使用情况摘要** | 每日 Azure 预留使用百分比。 |
| **使用率详细信息** | 提供 EA 合约给定计费对象信息的已使用量的明细和估计费用。 |
| **使用情况详细信息摊销** | 提供 EA 合约给定计费对象信息的已使用量的明细和估计摊销费用。 |

可以选择某个表以查看预览对话框。 可以通过选中表名称旁边的框来选择一个或多个表，然后选择“加载”  。

![获取计费 ID](media/desktop-connect-azure-cost-management/azure-cost-management-01c.png)

选择“加载”后，数据将加载到 Power BI Desktop  。 

加载所选数据后，将在“字段”  窗格中显示数据表和字段。


## <a name="next-steps"></a>后续步骤

可使用 Power BI Desktop 连接到多个不同数据源。 有关详细信息，请参阅以下文章：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   

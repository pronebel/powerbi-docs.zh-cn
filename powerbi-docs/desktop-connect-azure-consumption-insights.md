---
title: 连接到 Power BI Desktop 中的 Azure 成本和使用情况
description: 使用 Power BI Desktop 轻松连接到 Azure，并获取有关使用情况的见解
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 383d28a9e24165b12cda73ee254541a32db4391c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61324134"
---
# <a name="analyze-azure-cost-and-usage-data-in-power-bi-desktop"></a>分析 Power BI Desktop 中的 Azure 成本和使用情况数据

Power BI Desktop 可以连接到 Azure，并获取有关组织的 Azure 服务使用情况的深度数据。 可以使用这些数据创建自定义报表和度量值，更好地了解和分析 Azure 支出。

Power BI 目前支持连接到企业协议和客户协议的计费帐户。

* **企业协议**用户应使用连接**Azure 使用情况见解连接器**。

* **客户协议**用户应使用连接**Azure 成本管理连接器**。

## <a name="connect-with-azure-consumption-insights"></a>使用 Azure 使用见解连接

通过 Azure 使用见解可连接到 Azure 企业协议计费帐户。

在本部分中，你将了解如何连接以获取所需的数据，如何使用 Azure 企业连接器进行迁移，且还会找到 ACI（Azure 使用见解）API 中提供的“使用情况详细信息列”的映射   。

要使用 Azure 使用情况见解  连接器成功连接，需要能够访问 Azure 门户中的“企业”功能。

要使用 Azure 使用情况见解连接器进行连接，请从“Power BI Desktop”的“主页”功能区中选择“获取数据”     。 从左侧类别中选择“联机服务”  ，会看到“Microsoft Azure 使用情况见解 (Beta)”  。 选择“连接”  。

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

在出现的对话框中，提供你的“合约编号”  。

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

* 可以从 [Azure Enterprise Portal](https://ea.azure.com) 获取合约编号，获取位置如下图所示：
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)
  
  此版本的连接器仅支持来自 https://ea.azure.com 的企业合约。 目前尚不支持中国合约。

接下来，提供“访问密钥”  进行连接。

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

* 合约的访问密钥可在 [Azure Enterprise Portal](https://ea.azure.com) 上找到。
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

提供“访问密钥”  并选择“连接”  后，将出现“导航”  窗口并显示九个可用的表： 
* **预算**：提供预算详细信息，以查看针对现有预算目标的实际成本或使用情况。 
* **市场**：提供基于使用情况的 Azure市场费用。
* **价目表**：为注册提供适用的费率（由指示器计费）。
* **RICharges**：提供过去 24 个月与保留实例相关联的费用。
* **RIRecommendations_Single**：提供基于过去 7 天、30 天或 60 天单个订阅上的使用趋势的保留实例购买建议。
* **RIRecommendations_Shared**：提供基于过去 7 天、30 天或 60 天所有订阅上的使用趋势的保留实例购买建议。
* **RIUsage**：提供上个月现有保留实例的使用情况详细信息。
* **摘要**：提供余额、新购买、Azure 市场服务费用、调整和超额费用的月度摘要。
* **UsageDetails**：提供已使用量的明细和注册的估计费用。

可以选中任意表旁边的复选框来查看预览。 可以通过勾选表名称旁边的框来选择一个或多个表，然后选择“加载”  。

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04b.png)

> [!NOTE]
> “摘要”和“价目表”这两个表仅适用于注册级 API 密钥   。 此外，这些表中的数据默认包含“使用情况”  和“价目表”  的当前月份数据。 未将“摘要”  和“市场”  这两个表限制到当前月份。
> 
> 

选择“加载”  时，数据将加载到 Power BI Desktop  。

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

加载所选数据后，可以在“字段”  窗格中看到选择的表和字段。

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>使用 Azure 使用情况见解
要使用 Azure 使用情况见解  连接器，需要能够访问 Azure 门户中的“企业”功能。

使用 Azure 使用情况见解  连接器成功加载数据后，可以使用“查询编辑器”  创建自己的自定义度量值和列，并且可以创建可在 Power BI 服务  中共享的视觉对象、报表和仪表板。

Azure 还包括一些可以使用空查询检索的示例自定义查询的集合。 为此，在 Power BI Desktop  的“主页”  功能区中，选择“获取数据”  中的下拉箭头，然后选择“空查询”  。 此外，还可以在“查询编辑器”  中执行此操作，方法是右键单击左侧的“查询”  窗格，然后从显示的菜单中选择“新建查询”>”空查询”  。

在“编辑栏”中，键入以下内容  ：

    = MicrosoftAzureConsumptionInsights.Contents

随即出现示例集合，如下图所示：

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

处理报表和创建查询时，请使用以下命令：

* 要定义从当前日期开始的月数，请使用 numberOfMonth 
  * 使用介于 1 到 36 之间的值表示自当前日期开始要导入的月数。 建议获取的数据不要超过 12 个月，以避免超过导入限制和 Power BI 中查询允许数据量限制。
* 要在历史时间窗口中定义一段时间内的月份，请使用 startBillingDataWindow  和 endBillingDataWindow 
* 请勿将 numberOfMonth 与 startBillingDataWindow 或 endBillingDataWindow 一起使用    

## <a name="migrating-from-the-azure-enterprise-connector"></a>从 Azure 企业连接器迁移
一些客户使用 Azure 企业连接器 (Beta)  创建视觉对象，这些对象最终将被停用，并被替换为 Azure 使用情况见解  连接器。 Azure 使用情况见解  连接器具有以下功能和增强功能：

* “余额汇总”  和“市场购买”  可用的其他数据来源
* 新增参数和高级参数，如 startBillingDataWindow  和 endBillingDataWindow 
* 更好的性能和响应能力

为了帮助客户过渡到较新的 Azure 使用情况见解  连接器，并保留他们在创建自定义仪表板或报表方面所做的工作，以下步骤显示如何移至新的连接器。

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>步骤 1：使用新的连接器连接到 Azure
第一步是使用 Azure 使用情况见解  连接器进行连接，这在本文前面的部分中进行了详细介绍。 在此步骤中，在 Power BI Desktop  的“主页”  功能区中选择“获取数据”>“空查询”  。

### <a name="step-2-use-the-advanced-editor-to-create-a-query"></a>步骤 2：使用高级编辑器创建查询
在“查询编辑器”  中，从“主页”  功能区的“查询”  部分选择“高级编辑器”  。 在出现的“高级编辑器”窗口中，输入以下查询  ：

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

当然，需要将 enrollmentNumber  的值替换为你自己的合约编号，该编号可从 [Azure Enterprise Portal](https://ea.azure.com) 获取。 numberOfMonth  参数表示要从当前数据中返回几个月的数据。 当前月份用零 (0) 表示。

在“高级编辑器”窗口中选择“完成”后，预览将会刷新，你将看到表中指定月份范围的数据   。 选择“关闭并应用”  ，然后返回。

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>步骤 3：将度量值和自定义列移动到新报表
接下来，需要将创建的全部自定义列或度量值移动到新的详细信息表中。 步骤如下。

1. 打开记事本（或其他文本编辑器）。
2. 选择要移动的度量值，从“公式”字段中复制文本并粘贴到记事本中  。
   
   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. 将 Query1  重命名为原始详细信息表名称。
4. 右键单击表格并选择“新建度量值”，然后剪切并粘贴已存储的度量值和列，完成在表中创建新的度量值和自定义列操作  。

### <a name="step-4-re-link-tables-that-had-relationships"></a>步骤 4：重新关联具有关系的表
许多仪表板包含用于查找或筛选的其他表，例如日期表或用于自定义项目的表。 重新建立这些关系可解决大部分遗留问题。 下面介绍如何执行该操作。

- 在 Power BI Desktop  的“建模”  选项卡中，选择“管理关系”  会弹出允许你管理模型中关系的窗口。 根据需要重新关联表。
   
    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>步骤 5：验证视觉对象，并根据需要调整字段格式
执行这一步时，大部分原始视觉对象、表和向下钻取应该按预期方式工作。 但是，格式设置可能需要进行一些微小调整，使内容按预期显示。 花点时间查看每个仪表板和视觉对象，确保它们按预期显示。

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>使用 Azure 使用情况和见解 (ACI) API 获取使用情况数据
Azure 还提供了 [Azure 使用情况和见解 (ACI) API  ](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/)。 用户可以使用 ACI API 创建自己的自定义解决方案来收集、报告和直观显示 Azure 使用情况信息。

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>映射门户、连接器和 API 之间的名称和使用情况详细信息
Azure 门户中的列和名称详细信息与 API 和连接器中的相关信息类似，但并不总是完全一致。 为清晰起见，下表提供了可在 Azure 门户中看到的 API、连接器、和列之间的映射。 还指示了列是否已过时。 有关这些术语的详细信息和定义，请查看 [Azure 帐单数据字典](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail)。

| ACI 连接器/ContentPack ColumnName | ACI API 列名称 | EA 列名称 | 已过时/用于向后兼容 |
| --- | --- | --- | --- |
| AccountName |accountName |Account Name |否 |
| AccountId |accountId | |是 |
| AcccountOwnerId |accountOwnerEmail |AccountOwnerId |否 |
| AdditionalInfo |additionalInfo |AdditionalInfo |否 |
| AdditionalInfold | | |是 |
| Consumed Quantity |consumedQuantity |Consumed Quantity |否 |
| Consumed Service |consumedService |Consumed Service |否 |
| ConsumedServiceId |consumedServiceId | |是 |
| 开销 |cost |ExtendedCost |否 |
| Cost Center |costCenter |Cost Center |否 |
| 日期 |日期 |日期 |否 |
| 日 | |日 |否 |
| DepartmentName |departmentName |Department Name |否 |
| DepartmentID |departmentId | |是 |
| Instance ID | | |是 |
| InstanceId |instanceId |Instance ID |否 |
| 位置 | | |是 |
| Meter Category |meterCategory |Meter Category |否 |
| Meter ID | | |是 |
| Meter Name |meterName |Meter Name |否 |
| Meter Region |meterRegion |Meter Region |否 |
| Meter Sub-Category |meterSubCategory |Meter Sub-Category |否 |
| MeterId |meterId |Meter ID |否 |
| 月 | |月 |否 |
| 产品 |产品 |产品 |否 |
| ProductId |productId | |是 |
| Resource Group |resourceGroup |Resource Group |否 |
| Resource Location |resourceLocation |Resource Location |否 |
| ResourceGroupId | | |是 |
| ResourceLocationId |resourceLocationId | |是 |
| ResourceRate |resourceRate |ResourceRate |否 |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |否 |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |否 |
| ServiceInfo1Id | | |是 |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |否 |
| ServiceInfo2Id | | |是 |
| Store Service Identifier |storeServiceIdentifier |Store Service Identifier |否 |
| StoreServiceIdentifierId | | |是 |
| 订阅名称 |subscriptionName |订阅名称 |否 |
| 标记 |标记 |标记 |否 |
| TagsId | | |是 |
| Unit Of Measure |unitOfMeasure |Unit Of Measure |否 |
| 年份 | |年份 |否 |
| SubscriptionId |subscriptionId |SubscriptionId |是 |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |否 |

## <a name="connect-with-azure-cost-management"></a>使用 Azure 成本管理连接

本部分介绍如何连接到客户协议计费帐户。

> [!NOTE]
> Azure 成本管理连接器当前支持的客户上**客户协议**。  **企业协议**客户应使用 Microsoft Azure Consumption Insights 连接器。
> 
> 

要使用“Azure 成本管理”连接器进行连接，请从“Power BI Desktop”的“主页”功能区中选择“获取数据”     。  从左侧的类别中选择“Azure”，可看到 Azure 成本管理（Beta 版）   。 选择“连接”  。

![](media/desktop-connect-azure-consumption-insights/azure-cost-management-00.png)

在显示的对话框中，输入“计费对象信息 ID”  。

![](media/desktop-connect-azure-consumption-insights/azure-cost-management-01.png)

可以从 [Azure 门户](https://portal.azure.com)获取计费对象信息 ID。  导航至“成本管理和计费”，选择计费帐户，然后在边栏中选择“计费对象信息”   。  选择自己的计费对象信息，然后在边栏中选择“属性”  。  复制计费对象信息 ID。

![](media/desktop-connect-azure-consumption-insights/azure-cost-management-02.png)

系统将提示你使用 Azure 电子邮件和密码登录。  进行身份验证后，将看到一个“导航器”窗口，其中包含 12 个表  ：

* **计费事件**：提供新发票、信用卡购买等的事件日志。
* **预算**：提供预算详细信息，以查看针对现有预算目标的实际成本或使用情况。 
* **费用**：提供 Azure 使用情况、市场费用和单独计费的月级别小结。
* **额度批次**：为提供的计费对象信息提供 Azure 额度批次购买详情。
* **额度摘要**：为提供的计费对象信息提供额度摘要。
* **市场**：提供基于使用情况的 Azure市场费用。
* **价目表**：为计费对象信息提供按流量计费的适用费率。
* **RI 费用**：提供过去 24 个月与保留实例相关联的费用。
* **RI 建议（单个）** ：提供基于过去 7 天、30 天或 60 天单个订阅上的使用趋势的保留实例购买建议。
* **RI 建议（共享）** ：提供基于过去 7 天、30 天或 60 天所有订阅上的使用趋势的保留实例购买建议。
* **RI 使用情况**：提供上个月现有保留实例的使用情况详细信息。
* **使用情况详细信息**：提供给定计费对象信息 ID 的已使用量的明细和估计费用。

可以选中任意表旁边的复选框来查看预览。  可以通过勾选表名称旁边的框来选择一个或多个表，并选择“加载”  。

![](media/desktop-connect-azure-consumption-insights/azure-cost-management-03.png)

选择“加载”  时，数据将加载到 Power BI Desktop  。

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

加载所选数据后，可以在“字段”  窗格中看到选择的表和字段。

![](media/desktop-connect-azure-consumption-insights/azure-cost-management-05.png)

## <a name="writing-custom-queries"></a>编写自定义查询

如果要自定义月数，更改 API 版本或对返回的数据执行更多高级逻辑，就可以创建自定义 M 查询。

转到“Power BI Desktop”的“主页”功能区，选择“获取数据”中的下拉列表，然后选择“空查询”     。  此外，还可以在“查询编辑器”中执行此操作，方法是右键单击左侧的“查询”窗格，然后从显示的菜单中选择“新建查询”>”空白菜单”    。

在“公式栏”中，键入以下内容，将 `billingProfileId` 替换为实际 ID，并将“费用”替换为任何有效的表名（上文已列出）  。

```
let
    Source = AzureCostManagement.Tables(billingProfileId, [ numberOfMonths = 3 ]),
    charges = Source{[Key="charges"]}[Data]
in
    charges
```

除了将 `numberOfMonths` 修改为 1 到 36 之间的任何值之外，还可以提供：

* `apiVersion` 自定义查询将调用的 API 版本。
* `lookbackWindow`，用于 RI 建议（单个或共享），以修改要从中生成建议的窗口（有效选择：7、30 或 60 天）


## <a name="next-steps"></a>后续步骤
你可以使用 Power BI Desktop 连接到各种数据。 有关数据源的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   


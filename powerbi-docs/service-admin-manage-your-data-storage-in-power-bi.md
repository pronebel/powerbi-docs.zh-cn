---
title: 管理工作区中的数据存储
description: 了解如何管理个人或工作区中的数据存储，确保可以继续发布报表和数据集。
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/23/2020
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: bc8b8c16675e6d413c22d4ae88018222b02b17d6
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709879"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>管理 Power BI 工作区中的数据存储

了解如何管理个人或工作区中的数据存储，以便可以继续发布报表和数据集。

## <a name="capacity-limits"></a>容量限制

无论是我的工作区还是应用工作区，工作区存储限制都取决于工作区是[共享容量还是高级容量](service-basic-concepts.md#capacities)。

### <a name="shared-capacity-limits"></a>共享容量限制
对于共享容量中的工作区： 

- 每个工作区的存储限制为 10 GB。
- 对于应用工作区，总使用量不能超过 10 GB 乘以租户中的 Pro 许可证数量。

### <a name="premium-capacity-limits"></a>高级容量限制
对于高级容量中的工作区：
- 每个高级容量的限制为 100 TB。
- 每个用户都没有存储限制。

了解有关 [Power BI 定价模型](https://powerbi.microsoft.com/pricing)的其他功能。

## <a name="whats-included-in-storage"></a>存储中包含的内容

数据存储中包含你自己的数据集和 Excel 报表，以及某人与你共享的这些项。 数据集是任何已上传或连接到的数据源。 这些数据源包括正在使用的 Power BI Desktop 文件和 Excel 工作簿。 以下内容也包含在数据容量中。

* 固定到仪表板的 Excel 范围。
* 固定到 Power BI 仪表板的 Reporting Services 本地可视化效果。
* 已上载的图像。

共享仪表板的大小因其上的固定内容而有所不同。 例如，如果固定分属两个数据集的两个报表中的项，则其大小包括这两个数据集。

<a name="manage"/>

## <a name="manage-items-you-own"></a>管理拥有的项

确定你 Power BI 帐户中的数据存储使用情况，并管理帐户。

1. 若要管理你自己的存储，请转到导航窗格中的“我的工作区”  。
   
    ![我的工作区](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)

2. 依次选择右上角的齿轮图标![齿轮图标](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)\>“管理个人存储”  。
   
    顶部栏会显示你已使用的存储限制量。
   
    ![管理存储空间上限](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    数据集和报表会分为两个选项卡：
   
    **由我所有：** 你已将这些报表和数据集上传到 Power BI 帐户，包括服务数据集（如 Salesforce 和 Dynamics CRM）。  

    **由他人所有：** 其他人与你共享了这些报表和数据集。
1. 若要删除数据集或报表，请选择垃圾桶图标 ![垃圾桶图标](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png)。

请记住，你或其他人可能会具有基于某个数据集的报表和仪表板。 如果删除该数据集，则这些报表和仪表板将无法再正常工作。

## <a name="manage-your-workspace"></a>管理工作区
1. 依次选择“工作区”旁边的箭头 \> 工作区的名称  。
   
    ![选择“工作区”](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. 依次选择右上角的齿轮图标![齿轮图标](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)\>“管理组存储”  。
   
    顶部栏会显示已使用的组存储限制量。
   
    ![管理工作区存储](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    数据集和报表会分为两个选项卡：
   
    **由我们所有：** 你或其他人已将这些表和数据集上传到组的 Power BI 帐户，包括服务数据集（如 Salesforce 和 Dynamics CRM）。

    **由他人所有：** 其他人与你共享了组内的这些报表和数据集。

3. 若要删除数据集或报表，请选择垃圾桶图标 ![垃圾桶图标](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png)。
   
   > [!NOTE]
   > 请记住，你或组中的其他人可能会具有基于某个数据集的报表和仪表板。 如果删除该数据集，则这些报表和仪表板将无法再正常工作。
   
   工作区中具有管理员、成员或参与者角色的任何成员都有权从工作区中删除数据集和报表。

## <a name="dataset-limits"></a>数据集限制
导入到 Power BI 中的每个数据集都有 1 GB 的限制。 如果选择保留 Excel 体验，而不是导入数据，则数据集的限制为 250 MB。

## <a name="what-happens-when-you-reach-a-limit"></a>达到限制时，会发生什么情况
达到可以执行的操作的数据容量限制时，你会在服务中看到提示。 

如果选择齿轮图标 ![齿轮图标](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)，你会看到一个红色条，指示你已超过数据容量限制。

![已达到存储限制](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

此限制也会显示在“管理个人存储空间”中  。

 ![管理个人存储，超过存储空间上限](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 尝试执行的操作达到某个限制时，你会看到一条超出限制的消息。 可以[管理](#manage)存储，以减少存储量，从而符合限制要求。

 ![超出存储空间上限](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 ## <a name="next-steps"></a>后续步骤

 更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


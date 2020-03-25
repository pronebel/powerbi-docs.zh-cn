---
title: 在 Azure 门户中创建 Power BI Embedded 容量 | Microsoft Docs
description: 本文介绍如何在 Microsoft Azure 中创建 Power BI Embedded 容量。
author: KesemSharabi
ms.author: kesharab
ms.service: power-bi-embedded
ms.subservice: ''
ms.devlang: csharp, javascript
ms.topic: conceptual
ms.reviewer: zakharb
ms.date: 02/05/2019
ms.openlocfilehash: 57204602900e76e7bd5034e96f6385e5e944c04e
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114787"
---
# <a name="create-power-bi-embedded-capacity-in-the-azure-portal"></a>在 Azure 门户中创建 Power BI Embedded 容量

本文介绍如何在 Microsoft Azure 中创建 [Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) 容量。 Power BI Embedded 通过帮助用户快速将令人惊叹的视觉对象、报表和仪表板添加到应用中，简化 Power BI 功能。

如果没有 Azure 订阅，请在开始之前先创建一个[免费帐户](https://azure.microsoft.com/free/)。

> [!VIDEO https://www.youtube.com/embed/aXrvFfg_iSk]

## <a name="before-you-begin"></a>开始之前

若要完成本快速入门教程，需要以下内容：

* **Azure 订阅：** 访问 [Azure 免费试用版](https://azure.microsoft.com/free/)，创建一个帐户。
* **Azure Active Directory：** 订阅必须与 Azure Active Directory (AAD) 租户关联。 此外，***需要使用该租户中的帐户登录 Azure***。 不支持 Microsoft 帐户。 若要了解详细信息，请参阅[身份验证和用户权限](https://docs.microsoft.com/azure/analysis-services/analysis-services-manage-users)。
* **Power BI 租户：** AAD 租户中至少必须有一个帐户已注册 Power BI。
* **资源组：** 使用已有的资源组或[创建新的资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)。

## <a name="create-a-capacity"></a>创建容量

1. 登录到 [Azure 门户](https://portal.azure.com/)。

2. 在搜索框中，搜索  *Power BI Embedded*。

3. 在 Power BI Embedded 中，选择“创建”  。

4. 填写所需的信息，然后选择“创建”  。

    ![创建新容量需要填写的字段](media/azure-pbie-create-capacity/azure-portal-create-power-bi-embedded.png)

    |设置 |说明 |
    |---------|---------|
    |**资源名称**|用于标识容量的名称。 除 Azure 门户外，资源名称还会在 Power BI 管理门户中显示。|
    |**订阅**|想要为其创建容量的订阅。|
    |**资源组**|包含此新容量的资源组。 从现有资源组中选取，或创建其他资源组。 有关详细信息，请参阅 [Azure 资源管理器概述](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)。|
    |**Power BI 容量管理员**|Power BI 容量管理员可在 Power BI 管理门户中查看容量，并为其他用户提供分配权限。 默认情况下，容量管理员为你的帐户。 容量管理员必须位于 Power BI 租户内。|
    |**位置**|为租户托管 Power BI 的位置。 你的默认位置位于主区域内，但可以使用 [Multi-Geo 选项](embedded-multi-geo.md)更改该位置。
    |**定价层**|选择满足需求的 SKU（v 核心数和内存大小）。  有关详细信息，请参阅 [Power BI Embedded 定价](https://azure.microsoft.com/pricing/details/power-bi-embedded/)|

可导航到“所有服务” > “Power BI Embedded”，查看容量是否已准备就绪   。 或者，可以在通知部分或边栏选项卡中选择“固定到仪表板”，导航到仪表板以查看新容量  。

![提供 Power BI Embedded 容量的 Azure 门户仪表板](media/azure-pbie-create-capacity/azure-portal-dashboard.png)

## <a name="next-steps"></a>后续步骤

若要使用新的 Power BI Embedded 容量，请浏览到 Power BI 管理门户来分配工作区。 有关详细信息，请参阅[管理 Power BI Premium 和 Power BI Embedded 中的容量](https://powerbi.microsoft.com/documentation/powerbi-admin-premium-manage/)。

如果不需要使用此容量，则可将其暂停以停止计费。 有关详细信息，请参阅[在 Azure门户中暂停和启动 Power BI Embedded 容量](azure-pbie-pause-start.md)。

若要开始在应用程序中嵌入 Power BI 内容，请参阅[如何嵌入 Power BI 仪表板、报表和磁贴](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/)。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
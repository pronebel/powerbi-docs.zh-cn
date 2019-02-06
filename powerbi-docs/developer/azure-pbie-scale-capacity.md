---
title: 缩放 Power BI Embedded 容量 | Microsoft Docs
description: 本文介绍如何在 Microsoft Azure 中缩放 Power BI Embedded 容量。
services: power-bi-embedded
author: markingmyname
ms.author: maghan
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 01/31/2019
ms.openlocfilehash: 862e2dceb261e9f89480f50320bd0e1ce6a27931
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762274"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>在 Azure 门户中缩放 Power BI Embedded 容量

本文介绍如何在 Microsoft Azure 中缩放 Power BI Embedded 容量。 缩放操作可增加或减少容量的大小。

这里假设你已创建 Power BI Embedded 容量。 如果还没有，请参阅[在 Azure 门户中创建 Power BI Embedded 容量](azure-pbie-create-capacity.md)开始创建。

> [!NOTE]
> 缩放操作可能需要大约一分钟。 在此期间，容量不可用。 可能无法加载嵌入的内容。

## <a name="scale-a-capacity"></a>缩放容量

1. 登录到 [Azure 门户](https://portal.azure.com/)。

2. 选择“所有服务” > “Power BI Embedded”以查看容量。

    ![Azure 门户中的所有服务](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. 选择要缩放的容量。

    ![Azure 门户中的 Power BI Embedded 容量列表](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. 在容量内选择“缩放”下的“定价层”。

    ![缩放下的定价层选项](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    你当前的定价层以蓝色框出。

    ![当前的定价层以蓝色框出](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. 若要纵向扩展或减少容量，请选择要移动到的新层。 选择新层时会将所选层用蓝色虚线边框框起来。 选择“选择”以缩放到新层。

    ![选择新层](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    缩放容量可能需要一两分钟才能完成。

6. 通过查看概述选项卡确认你的定价层。系统会列出当前的定价层。

    ![确认当前层](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>后续步骤

若要暂停或启动容量，请参阅[在 Azure 门户中暂停和启动 Power BI Embedded 容量](azure-pbie-pause-start.md)。

若要开始在应用程序中嵌入 Power BI 内容，请参阅[如何嵌入 Power BI 仪表板、报表和磁贴](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/)。

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)

---
title: 在 Microsoft 365 中跟踪 Power BI 服务运行状况
description: 了解如何在 Microsoft 365 管理中心中查看当前和历史服务运行状况。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 3b3faab2a01a00e09560d39e850f40d0672a5863
ms.sourcegitcommit: c18130ea61e67ba111be870ddb971c6413a4b632
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86161160"
---
# <a name="track-power-bi-service-health-in-microsoft-365"></a>在 Microsoft 365 中跟踪 Power BI 服务运行状况

Microsoft 365 管理中心为 Power BI 管理员提供重要工具。 这些工具包括有关服务运行状况的当前和历史信息。 若要访问服务运行状况信息，必须是以下角色之一：

* Power BI 服务管理员

* 全局管理员角色

有关角色的详细信息，请参阅[与 Power BI 相关的管理员角色](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)。

1. 登录 [MIcrosoft 365 管理中心](https://portal.office.com/adminportal)。

1. 从导航窗格中，选择“全部显示” > “运行状况” > “服务运行状况”  。 将显示“服务运行状况”页面：

    ![Microsoft 365 管理中心（启用了“运行状况”和“服务运行状况”选项）的屏幕截图。](media/service-admin-health/service-health-tile.png)

1. 从“所有服务”列表中，选择“公告”或“事件” ，并查看结果。 在下面的屏幕快照中，可以查看三个活动公告之一。

    ![“服务运行状况”页（其中包含针对 Power BI 的三个公告并启用了“显示详细信息”选项）的屏幕截图。](media/service-admin-health/active-advisories.png)

1. 若要查看详细信息，请选择项的“显示详细信息”。 在下面的屏幕快照中，可以查看其他详细信息，包括最近状态更新。

    ![“公告”详细信息的屏幕截图，其中显示了其他信息。](media/service-admin-health/advisory-details.png)

    向下滚动以查看更多信息，完成时关闭窗格。

1. 若要查看所有服务的历史信息，请在“服务运行状况”页面右上角选择“查看历史记录” 。 然后，选择“过去 7 天”或“过去 30 天”。 

1. 若要返回到当前服务运行状况，请选择“查看当前状态”。
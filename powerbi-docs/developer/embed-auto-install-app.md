---
title: 为组织嵌入内容时，自动安装 Power BI 应用
description: 了解如何为组织嵌入内容时自动安装 Power BI 应用。
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: bb9ba5531c2a23f15ccbf98261e246ab7080aecb
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61376188"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>为组织嵌入内容时自动安装 Power BI 应用

若要嵌入应用程序中的内容，嵌入的用户必须具有[应用的访问权限](../service-create-distribute-apps.md)。 如果为用户安装应用，然后嵌入可以顺利地工作。 有关详细信息，请参阅[嵌入的报表或仪表板应用](embed-from-apps.md)。 可以在所有应用可以都在 PowerBI.com 中定义[自动安装](https://powerbi.microsoft.com/blog/automatically-install-apps/)。 但是，此操作在租户级别完成，并应用到所有应用。

## <a name="auto-install-app-on-embedding"></a>嵌入的自动安装应用

如果用户有权访问应用，但未安装该应用程序，然后嵌入失败。 因此可以避免这些故障，应用程序中嵌入内容时，可以允许自动安装时嵌入应用。 此操作的含义，如果未安装应用程序用户尝试进行嵌入，它会自动安装为您。 因此你想要的内容获取嵌入立即，导致用户获得流畅的体验。

## <a name="embed-for-power-bi-users-user-owns-data"></a>为 Power BI 用户 （用户拥有数据） 嵌入

若要允许用户自动安装的应用，需要为你的应用程序提供内容创建权限时[注册应用程序](register-app.md#register-with-the-power-bi-application-registration-tool)，或将其添加，如果你尚未注册应用。

![注册应用程序创建的内容](media/embed-auto-install-app/register-app-create-content.png)

接下来，需要提供嵌入 URL 中的应用 ID。 若要提供的应用程序 ID，应用创建者首先需要安装该应用程序，然后使用某个受支持[Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/)调用-[获取报表](https://docs.microsoft.com/rest/api/power-bi/reports/getreports)或[获取仪表板](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards)。 然后应用创建者需要执行的 REST API 响应中的嵌入 Url。 如果内容是从应用程序，应用程序 ID 将显示在 URL 中。  嵌入 URL 后，可用于定期嵌入。

## <a name="secure-embed"></a>保护嵌入

若要使用自动安装的应用，应用创建者首先需要安装该应用程序，然后转到 PowerBI.com 上的应用程序，导航到报表，并以常用方式获取的链接。 所有其他用户有权访问的应用程序可以使用以下链接可以嵌入报表。

## <a name="considerations-and-limitations"></a>注意事项和限制

* 只可以嵌入报表和仪表板以这种情况。

* 此功能当前不支持的应用拥有数据和 SharePoint 嵌入方案。
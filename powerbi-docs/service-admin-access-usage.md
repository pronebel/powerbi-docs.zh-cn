---
title: 查找已登录的 Power BI 用户
description: 如果你是租户管理员，并且想要查看谁具有登录到 Power BI，可以使用 Azure Active Directory 访问和使用情况报告来监控。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906760"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>查找已登录的 Power BI 用户

如果你是租户管理员，并且想要查看到 Power BI 中使用签名者[Azure Active Directory 访问和使用情况报告](/azure/active-directory/reports-monitoring/concept-sign-ins)获得可见性。

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> **登录名**报表提供了有用的信息，但它不会识别每个用户具有的许可证的类型。 请使用 Microsoft 365 管理中心查看许可证。

## <a name="requirements"></a>要求

任何用户（包括非管理员）都可以查看自己的登录活动报告，但必须符合以下要求，才能查看所有用户的报告。

* 租户必须具有与之关联的 Azure Active Directory Premium 许可证。

* 必须属于以下角色之一：全局管理员、安全管理员或安全读取者。

## <a name="use-the-azure-portal-to-view-sign-ins"></a>使用 Azure 门户查看登录活动

若要查看登录活动，请按以下步骤操作。

1. 在“Azure 门户”  中，选择“Azure Active Directory”  。

1. 在“监视”  下，选择“登录活动”  。
   
    ![使用 Azure Active Directory 和登录名选项突出显示 Azure UI 的屏幕截图。](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. 按“Microsoft Power BI”  或“Power BI Gateway”  筛选应用，再选择“应用”  。

    **Microsoft Power BI**登录活动筛选器与服务相关的而**Power BI Gateway**登录特定于活动的本地数据网关的筛选器。
   
    ![与应用程序字段突出显示的登录名筛选器的屏幕截图。](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>导出数据

你可以[下载的登录报告](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report)两种格式之一： CSV 文件或 JSON 文件。

![下载按钮的屏幕截图。](media/service-admin-access-usage/download-sign-in-data-csv.png)

在顶部**登录名**报表中，选择**下载**，然后选择下列选项之一：

* **CSV**以下载当前已筛选数据的 CSV 文件。

* **JSON**以下载当前已筛选数据的 JSON 文件。

## <a name="data-retention"></a>数据保留期

与登录活动相关的数据最长可保留 30 天。 有关详细信息，请参阅[Azure Active Directory 报告保留策略](/azure/active-directory/reports-monitoring/reference-reports-data-retention)。

## <a name="next-steps"></a>后续步骤

[在组织内使用审核](service-admin-auditing.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
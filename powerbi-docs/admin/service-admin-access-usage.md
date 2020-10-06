---
title: 查找已登录的 Power BI 用户
description: 如果你是管理员，想查看谁已登录到 Power BI，则可以使用 Azure Active Directory 访问和使用情况报表/
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: e278918fdcf19a8de5cd5af1995bbc050dd765ec
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/26/2020
ms.locfileid: "91374700"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>查找已登录的 Power BI 用户

如果你是组织的管理员，想查看谁已登录到 Power BI，请使用 [Azure Active Directory 访问和使用情况报表](/azure/active-directory/reports-monitoring/concept-sign-ins)。

> [!NOTE]
> “登录”报表提供了有用的信息，但它并未标识每个用户的许可证类型。 请使用 Microsoft 365 管理中心查看许可证。

## <a name="requirements"></a>要求

任何用户都可以查看他们自己的登录的报表。若要查看所有用户的报表，你必须是以下角色之一：全局管理员、安全管理员、安全读取者、全局读取者或报表读取者。

## <a name="use-the-azure-active-directory-admin-center-to-view-sign-ins"></a>使用 Azure Active Directory 管理中心查看登录

若要查看登录活动，请按以下步骤操作。

1. 登录到[“Azure Active Directory 管理中心”](https://aad.portal.azure.com)，然后从门户菜单中选择“Azure Active Directory”。

1. 从资源菜单中选择“监视” > “登录”。
   
    ![Azure Active Directory 管理中心的屏幕截图，其中突出显示了“登录”选项。](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. 默认情况下，将显示最近 24 小时内所有用户和所有应用程序的所有登录。 若要选择其他时间段，请在工作窗格中选择“日期”，然后从可用时间间隔中进行选择。 只有过去 7 天的信息可用。 若仅查看 Power BI 的登录，请添加筛选器。 选择“添加筛选器”，选取“应用程序”作为筛选依据字段，然后选择“应用”。 从工作窗格顶部选择“应用程序开头是”，然后输入应用名称。 选择“应用”。

    **Microsoft Power BI** 筛选出与服务相关的登录活动。 **Power BI Gateway** 筛选出特定于本地数据网关的登录活动。
   
    ![登录筛选器的屏幕截图，突出显示“应用程序”字段。](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>导出数据

你可以以两种格式之一[下载登录报表](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report)：CSV 文件或 JSON 文件。

1. 从“登录”报表的命令栏中选择“下载”，然后选择以下选项之一 ：

   * **XSV**：下载当前已筛选数据的 CSV 文件。

   * **JSON**：下载当前已筛选数据的 JSON 文件。

2. 键入文件名，然后选择“下载”。

![数据导出的屏幕截图，其中突出显示了“下载”选项。](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>数据保留

与登录相关的数据最多可保留 7 天，除非你的组织有 Azure AD 高级许可证。 如果你使用的是 Azure AD Premium P1 或 Azure AD Premium P2，则可以看到过去 30 天的数据。 有关详细信息，请参阅 [Azure Active Directory 报表保留策略](/azure/active-directory/reports-monitoring/reference-reports-data-retention)。

## <a name="next-steps"></a>后续步骤

[审核用户活动](service-admin-auditing.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
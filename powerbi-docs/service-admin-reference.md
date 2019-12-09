---
title: 管理员适用的 PowerShell cmdlet、REST API 和 .NET SDK
description: 了解可以通过脚本和编程 API 管理 Power BI 的方式。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: b4f4227a53a87cd831962bc5c944a569531b8232
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699857"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>使用 PowerShell cmdlet、REST API 和 .NET SDK 进行 Power BI 管理
通过 Power BI，管理员可以使用 PowerShell cmdlet 编写常见任务的脚本。 还可以利用其中的 REST API 和 .NET SDK 开发管理解决方案。 本主题列出了一系列 cmdlet 和相应的 SDK 方法以及 REST API 终结点。 有关详细信息，请参阅：

- PowerShell [下载](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/)和[文档](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- REST API [文档](https://docs.microsoft.com/rest/api/power-bi/admin)
- .NET SDK [下载](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> 应使用 `-Scope Organization` 调用下面的 cmdlet，以对租户执行管理操作。

| **Cmdlet 名称** | **别名** | **SDK 方法** | **REST API 终结点** | **说明** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | 不适用 | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | 获取给定数据集的数据源。 |
| `Get-PowerBIDataset` | 不适用 | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | 获取 Power BI 租户中的完整数据集列表。 |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | 获取 Power BI 租户中的完整工作区列表。 |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | 将用户作为成员添加到给定的工作区。 |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | 从给定工作区的成员身份列表中删除用户。 |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | 还原已删除的工作区。 |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | 更新给定工作区的属性。 |
| `Get-PowerBIDataset -WorkspaceId` | 不适用 | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | 获取给定工作区中的数据集。 |
| `Get-PowerBIReport` | 不适用 | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | 获取 Power BI 租户中的完整报表列表。 |
| `Get-PowerBIDashboard` | 不适用 | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | 获取 Power BI 租户中的完整仪表板列表。 |
| `Get-PowerBIDashboard -WorkspaceId` | 不适用 | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | 获取给定工作区中的仪表板。 |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | 获取给定仪表板的磁贴。 |
| `Get-PowerBIReport` | 不适用 | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | 获取给定工作区中的报表。 |
| `Get-PowerBIImport` | 不适用 | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | 获取 Power BI 租户中的完整导出列表。 |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | 不适用 | 不适用 | 登录 Power BI 并启动一个会话。 |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | 不适用 | 不适用 | 注销 Power BI 并关闭现有会话。 |
| `Invoke-PowerBIRestMethod`| 不适用 | 不适用 | 不适用 | 将任意 REST API 调用发送到 Power BI。 |
| `Get-PowerBIAccessToken`| 不适用 | 不适用 | 不适用 | 在会话中获取 Power BI 访问令牌。 |
| `Resolve-PowerBIError`| 不适用 | 不适用 | 不适用 | 获取失败 cmdlet 调用的详细错误信息。 |

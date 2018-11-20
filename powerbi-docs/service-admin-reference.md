---
title: 管理员适用的 PowerShell cmdlet、REST API 和 .NET SDK
description: 了解可以通过脚本和编程 API 管理 Power BI 的方式。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: f4455fef5a2ed0e7ee23ff8ca3a0b626cd695838
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507982"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>使用 PowerShell cmdlet、REST API 和 .NET SDK 进行 Power BI 管理
通过 Power BI，管理员可以使用 PowerShell cmdlet 编写常见任务的脚本。 还可以利用其中的 REST API 和 .NET SDK 开发管理解决方案。 本主题列出了一系列 cmdlet 和相应的 SDK 方法以及 REST API 终结点。 有关详细信息，请参阅：

  - PowerShell [下载](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/)和[文档](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
  - REST API [文档](https://docs.microsoft.com/rest/api/power-bi/admin)
  - .NET SDK [下载](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) 


| **Cmdlet 名称** | **SDK 方法** | **REST API 终结点** | **说明** |
| --- | --- | --- | --- |
| **Get-PowerBIDatasource** | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | 获取给定数据集的数据源。 |
| **Get-PowerBIDataset** | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | 获取 Power BI 租户中的完整数据集列表。 |
| **Get-PowerBIWorkspace** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | 获取 Power BI 租户中的完整工作区列表。 |
| **Add-PowerBIWorkspaceUser** | Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | 将用户作为成员添加到给定的工作区。 |
| **Remove-PowerBIWorkspaceUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | 从给定工作区的成员身份列表中删除用户。 |
| **Restore-PowerBIWorkspace** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | 还原已删除的工作区。 |
| **Set-PowerBIWorkspace** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | 更新给定工作区的属性。 |
| **Get-PowerBIDataset -WorkspaceId** | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | 获取给定工作区中的数据集。 |
| **Export-PowerBIReport** | Reports\_ExportReportAsAdmin | 不适用 | 将给定报表导出到本地文件。 |
| **Get-PowerBIReport** | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | 获取 Power BI 租户中的完整报表列表。 |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | 获取 Power BI 租户中的完整仪表板列表。 |
| **Get-PowerBIDashboard -WorkspaceId** | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | 获取给定工作区中的仪表板。 |
| **Get-PowerBITile -DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | 获取给定仪表板的磁贴。 |
| **Get-PowerBIReport -WorkspaceId** | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | 获取给定工作区中的报表。 |
| **Get-PowerBIImport** | Imports\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | 获取 Power BI 租户中的完整导出列表。 |
| **Connect-PowerBIServiceAccount** | 不适用 | 不适用 | 登录 Power BI 并启动一个会话。 |
| **Disconnect-PowerBIServiceAccount** | 不适用 | 不适用 | 注销 Power BI 并关闭现有会话。 |
| **Invoke-PowerBIRestMethod** | 不适用 | 不适用 | 将任意 REST API 调用发送到 Power BI。 |
| **Get-PowerBIAccessToken** | 不适用 | 不适用 | 在会话中获取 Power BI 访问令牌。 |
| **Resolve-PowerBIError** | 不适用 | 不适用 | 获取失败 cmdlet 调用的详细错误信息。 |
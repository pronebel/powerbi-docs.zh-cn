---
title: 使用 Power BI 连接到 Office365Mon
description: 适用于 Power BI 的 Office365Mon
author: paulinbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 11/26/2019
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 8e9563d10d80290a48e20cd2d6a889831d34924b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "74548596"
---
# <a name="connect-to-office365mon-with-power-bi"></a>使用 Power BI 连接到 Office365Mon
使用 Power BI 和 Office365Mon 模板应用可轻松分析 Office 365 故障和运行状况性能数据。 Power BI 将检索你的数据（包括故障和运行状况探测），然后基于该数据构建可立即使用的仪表板和报表。

连接到 Power BI 的 [Office365Mon 模板应用](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3)。

>[!NOTE]
>需要使用 Office365Mon 管理员帐户连接和加载 Power BI 模板应用。

## <a name="how-to-connect"></a>如何连接
1. 在导航窗格底部，选择“获取数据”  。
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. 在**服务**框中，选择**获取**。
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. 选择“Office365Mon”\>“获取”   。
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. 对于身份验证方法，请选择“oAuth2”\>“登录”   。
   
   出现提示时，输入Office365Mon 管理凭据，然后按照身份验证过程进行操作。
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Power BI 导入数据后，你将在导航窗格中看到新的仪表板、报表和数据集。 新的项目会以黄色星号 \* 标记，请选择 Office365Mon 条目。
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](service-dashboard-edit-tile.md)。
* [选择磁贴](consumer/end-user-tiles.md)以打开基础报表。
* 虽然数据集将按计划每日刷新，但你可以更改刷新计划或根据需要使用“立即刷新”  来尝试刷新

## <a name="troubleshooting"></a>故障排除
使用 Office365Mon 订阅凭据进行登陆后，若显示**登录失败**，则表明所用帐户无权检索你的帐户中的 Office365Mon 数据。 验证其是否为管理员帐户，然后重试。

## <a name="next-steps"></a>后续步骤
[什么是 Power BI？](fundamentals/power-bi-overview.md)

[获取 Power BI 的数据](service-get-data.md)


---
title: 如何刷新 Xero 内容包证书
description: 如果使用 Xero Power BI 内容包，由于最近的 Power BI 服务事件，你可能遇到了内容包的每日刷新问题。
author: SarinaJoan
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 0a7268c041976a3cab3316c91470c1378a3685f5
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83327728"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>刷新失败时，如何刷新 Xero 内容包证书
如果使用 Xero Power BI 内容包，由于最近的 Power BI 服务事件，你可能遇到了一些内容包的每日刷新问题。

可以通过检查 Xero 数据集的最后刷新状态看到内容包是否已成功刷新，如下面的屏幕截图中所示。

![](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

如果看到如上所示的刷新失败，请按照以下步骤续订内容包凭据。

1. 单击 Xero 数据集旁边的“更多选项”(…)，然后单击“计划刷新”   。 这将打开 Xero 内容包的设置页。
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. 在“**Xero 设置**”页，选择“**数据源凭据**” > “**编辑凭据**”。
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. 输入你的组织名称 > **下一步**。
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. 使用 Xero 帐户登录。
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. 现在凭据已更新，我们必须确保刷新计划设置为每天运行一次。 单击 Xero 数据集旁边的“更多选项”(…)，然后再次单击“计划刷新”以进行检查   。
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. 还可以选择立即刷新数据集。 单击 Xero 数据集旁边的“更多选项”(…)，然后单击“立即刷新”   。
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

如果仍有刷新方面的问题，请随时与我们联系 [https://support.powerbi.com](https://support.powerbi.com) 

若要了解更多有关 Power BI Xero 内容包的详细信息，请访问 [Xero 内容包帮助页](service-connect-to-xero.md)。

### <a name="next-steps"></a>后续步骤
* 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


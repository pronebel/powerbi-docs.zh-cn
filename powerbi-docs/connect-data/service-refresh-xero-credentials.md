---
title: 如何刷新 Xero 内容包证书
description: 如果使用 Xero Power BI 内容包，由于最近的 Power BI 服务事件，你可能遇到了内容包的每日刷新问题。
author: paulinbar
ms.author: painbar
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/10/2017
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 972340d4c9cca4507308aaac4c07f410ff8fc6fe
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392096"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>刷新失败时，如何刷新 Xero 内容包证书
如果使用 Xero Power BI 内容包，由于最近的 Power BI 服务事件，你可能遇到了一些内容包的每日刷新问题。

可以通过检查 Xero 数据集的最后刷新状态看到内容包是否已成功刷新，如下面的屏幕截图中所示。

![Xero 对话框的屏幕截图，其中显示了 Xero 数据集的刷新状态。](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

如果看到如上所示的刷新失败，请按照以下步骤续订内容包凭据。

1. 单击 Xero 数据集旁边的“更多选项”(…)，然后单击“计划刷新” 。 这将打开 Xero 内容包的设置页。
   
    ![Xero 对话框的屏幕截图，其中显示了“计划刷新”选项。](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. 在“**Xero 设置**”页，选择“**数据源凭据**” > “**编辑凭据**”。
   
    ![“Xero 设置”对话框的屏幕截图，其中显示了已选择“编辑凭据”的 Xero 设置。](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. 输入你的组织名称 > **下一步**。
   
    ![“配置 Xero”对话框的屏幕截图，其中显示了组织的名称。](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. 使用 Xero 帐户登录。
   
    ![Xero 登录对话框的屏幕截图，其中显示了如何登录到 Xero 帐户。](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. 现在凭据已更新，我们必须确保刷新计划设置为每天运行一次。 单击 Xero 数据集旁边的“更多选项”(…)，然后再次单击“计划刷新”以进行检查 。
   
    ![“计划刷新”对话框的屏幕截图，其中显示了刷新频率和时区。](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. 还可以选择立即刷新数据集。 单击 Xero 数据集旁边的“更多选项”(…)，然后单击“立即刷新” 。
   
    ![Xero 对话框的屏幕截图，其中已选择“立即刷新”。](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

如果仍有刷新方面的问题，请随时与我们联系 [https://support.powerbi.com](https://support.powerbi.com) 

若要了解更多有关 Power BI Xero 内容包的详细信息，请访问 [Xero 内容包帮助页](service-connect-to-xero.md)。

### <a name="next-steps"></a>后续步骤
* 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


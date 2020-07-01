---
title: 使用 Power BI 连接到 QuickBooks Online
description: 适用于 Power BI 的 QuickBooks Online
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 7153d663d54924aa9d13a1e60fd303d667c65b8c
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85229737"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>使用 Power BI 连接到 QuickBooks Online
从 Power BI 连接到 QuickBooks Online 数据时，你将立即获得一个 Power BI 仪表板和 Power BI报表，报表提供了关于业务现金流、盈利率和客户等的信息。 按原样使用仪表板和报表，或者对其进行自定义以突出显示你最关注的信息。 此数据每天自动刷新一次。

连接到适用于 Power BI 的 [QuickBooks Online 模板应用](https://dxt.powerbi.com/getdata/services/quickbooks-online)。

>[!NOTE]
>若要将你的 QuickBooks Online 数据导入 Power BI，你需要是 QuickBooks Online 帐户管理员，并使用管理员帐户凭据进行登录。 无法在 QuickBooks Desktop 软件中使用此连接器。 

## <a name="how-to-connect"></a>如何连接

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. 选择 **QuickBooks Online**，然后选择**获取**。
   
   ![获取 QuickBooks](media/service-connect-to-quickbooks-online/qbo.png)

4. 在“安装此 Power BI 应用?”中，选择“安装” 。

    ![安装 QuickBooks](media/service-connect-to-quickbooks-online/power-bi-install-quickbooks.png)

4. 在“应用”窗格中，选择“QuickBooks”磁贴 。

   ![选择 QuickBooks 磁贴](media/service-connect-to-quickbooks-online/power-bi-quickbooks-tile.png)

6. 在“开始使用新应用”中，选择“连接” 。

    ![开始使用新应用](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. 对于身份验证方法，选择 **oAuth2**，然后选择**登录**。 
5. 出现提示时，输入 QuickBooks Online 凭据，然后按照 QuickBooks Online 身份验证过程操作。 （如果你已经在浏览器中登录到 QuickBooks Online，则可能不会看到凭据提示。）
   >[!NOTE]
   >你的 QuickBooks Online 帐户需要管理凭据。
6. 在下一屏幕中选择你想要连接到 Power BI 的公司。
   
   ![在 QuickBooks 中基本准备就绪](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)

7. 在下一屏幕中选择**授权**以开始导入过程。 该过程可能需要几分钟时间，具体耗时取决于公司数据的大小。 
   
   ![授权 QuickBooks](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
8. Power BI 导入数据后，你会看到 QuickBooks 应用的内容列表：新的仪表板、报表和数据集。
9. 选择 QuickBooks 仪表板以开始浏览过程。 Power BI 自动创建了此仪表板，以显示你导入的数据。

    ![QuickBooks 仪表板](media/service-connect-to-quickbooks-online/power-bi-connect-quickbooks-sample.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](../consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](../create-reports/service-dashboard-edit-tile.md)。
* [选择磁贴](../consumer/end-user-tiles.md)以打开基础报表。
* 虽然数据集将按计划每日刷新，但你可以更改刷新计划或根据需要使用“立即刷新”来尝试刷新

## <a name="troubleshooting"></a>故障排除
**“抱歉!出现错误。”**

如果在选择**授权**后出现此消息：

“糟糕！ 出现错误。” 请关闭此窗口，然后重试。

此公司的另一用户已订阅该应用程序。 若要对此订阅进行更改，请联系 [管理员电子邮件]。”

![抱歉! 出现错误](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

...此错误意味着你公司的另一个管理员已使用 Power BI 连接到公司数据。 联系该管理员以共享仪表板。 目前，只能有一个管理员用户可以将特定的 QuickBooks Online 公司数据集连接到 Power BI。 Power BI 创建仪表板后，管理员可以与多个同事在同一 Power BI 租户上共享此仪表盘。

**“此应用未设置允许来自你所在国家/地区的连接”**

当前 Power BI 仅支持 QuickBooks Online 的美国版本。 

![此应用未设置为允许来自你所在国家/地区的连接](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>后续步骤
[什么是 Power BI？](../fundamentals/power-bi-overview.md)

[Power BI 服务中设计器的基本概念](../fundamentals/service-basic-concepts.md)

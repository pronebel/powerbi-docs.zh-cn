---
title: 使用 Power BI 连接到 Projectplace
description: 适用于 Power BI 的 Projectplace
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: cd478abbac94c6b8aaf5aaa087dbfa4840e05fd7
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184549"
---
# <a name="connect-to-projectplace-by-planview-with-power-bi"></a>使用 Power BI 连接到 Projectplace by Planview
通过 Projectplace by Planview 内容包，你能够以全新的方式直接在 Power BI 中可视化你的协作项目数据。 使用你的 Projectplace 登录凭据交互式查看关键项目统计信息，找出最活跃和最富生产力的团队成员，并识别出 Projectplace 帐户各项目中存在风险的卡片和活动。 你还可以扩展现成的仪表板和报表，以获取对你最重要的信息。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[连接到 Power BI 中的 Projectplace 内容包](https://app.powerbi.com/getdata/services/projectplace)

>[!NOTE]
>要将 Projectplace 数据导入 Power BI，则你必须是 Projectplace 用户。 其他要求见下文。

## <a name="how-to-connect"></a>如何连接
1. 选择左侧导航窗格底部的**获取数据**。
   
    ![](media/service-connect-to-projectplace/get.png)
2. 在**服务**框中，选择**获取**。
   
    ![](media/service-connect-to-projectplace/services.png)
3. 在 Power BI 页上，选择 **Projectplace by Planview**，然后选择**获取**：  
   
    ![](media/service-connect-to-projectplace/projectplace.png)
4. 在 OData 数据源 URL 文本框中，输入想要使用的 Projectplace OData 数据源的 URL，如下图所示：
   
    ![](media/service-connect-to-projectplace/params.png)
5. 在身份验证方法列表中，若 **OAuth**未被选择，则选择该项。 点击**登录**，然后按照登录流程操作。  
   
   ![](media/service-connect-to-projectplace/creds.png)
6. 在左侧窗格中，从仪表板列表中选择 **Projectplace**。 Power BI 将 Projectplace 数据导入仪表板。 请注意，加载数据可能需要一些时间。  
   
    仪表板包含显示来自你 Projectplace 数据库的数据的磁贴。 下图为 Power BI 中默认 Projectplace 仪表板的示例。
   
    ![](media/service-connect-to-projectplace/dashboard.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](service-dashboard-edit-tile.md)。
* [选择磁贴](consumer/end-user-tiles.md)以打开基础报表。
* 虽然数据集将按计划每日刷新，但你可以更改刷新计划或根据需要使用“立即刷新”  来尝试刷新

## <a name="system-requirements"></a>系统要求
要将 Projectplace 数据导入 Power BI，则你必须是 Projectplace 用户。 此过程假设你已使用 Power BI 帐户登录到 Microsoft Power BI 主页。 如果没有 Power BI 帐户，请转到 [powerbi.com](https://powerbi.microsoft.com/get-started/)，在“Power BI - 云协作和共享”下，选择“免费试用”   。 然后单击“获取数据”  。

## <a name="next-steps"></a>后续步骤
[什么是 Power BI？](power-bi-overview.md)

[Power BI 服务中设计器的基本概念](service-basic-concepts.md)


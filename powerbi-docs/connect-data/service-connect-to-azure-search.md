---
title: 使用 Power BI 连接到 Azure 搜索
description: 适用于 Power BI 的 Azure 搜索
author: davidiseminger
ms.author: davidi
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: 5c2c5d3b6382fdb85125a71829d62624dab31e83
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403366"
---
# <a name="connect-to-azure-search-with-power-bi"></a>使用 Power BI 连接到 Azure 搜索
Azure 搜索流量分析允许你监视并了解 Azure 搜索服务的流量。 适用于 Power BI 的 Azure 搜索内容包提供了搜索数据的详细深入解析，包括过去 30 天内的搜索、索引、服务统计和延迟。 有关详细信息，请参阅 [Azure 博客文章](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/)。

[!INCLUDE [include-short-name](../includes/service-deprecate-content-packs.md)]

连接到适用于 Power BI 的 [Azure 搜索内容包](https://app.powerbi.com/getdata/services/azure-search)。

## <a name="how-to-connect"></a>如何连接
1. 在导航窗格底部，选择“获取数据”。
   
   ![Power BI Desktop 中“获取数据”的屏幕截图，其中显示了导航窗格中的按钮。](media/service-connect-to-azure-search/pbi_getdata.png) 
2. 在 **服务** 框中，选择 **获取**。
   
   ![“服务”对话框的屏幕截图，其中显示了“获取”按钮。](media/service-connect-to-azure-search/pbi_getservices.png) 
3. 选择“Azure 搜索”\>“获取” 。
   
   ![“Azure 服务”对话框的屏幕截图，其中显示了“获取”链接。](media/service-connect-to-azure-search/azuresearch.png)
4. 提供存储了 Azure 搜索分析的表存储帐户的名称。
   
   ![“连接 Azure 搜索”对话框的屏幕截图，其中显示了“Azure 存储帐户名称”字段。](media/service-connect-to-azure-search/params.png)
5. 选择“密钥”作为验证机制，并提供你的存储帐户密钥。 单击“登录”开始加载程序。
   
   ![“连接 Azure 搜索”对话框的屏幕截图，其中“身份验证方法”字段中已输入“密钥”。](media/service-connect-to-azure-search/creds.png)
6. 加载完成后，导航窗格中会出现新的仪表板、报表和模型。 选择仪表板查看已导入的数据。
   
    ![导航窗格的屏幕截图，其中显示了仪表板、报表和模型。](media/service-connect-to-azure-search/dashboard2.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](../consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](../create-reports/service-dashboard-edit-tile.md)。
* [选择磁贴](../consumer/end-user-tiles.md)以打开基础报表。
* 虽然数据集将按计划每日刷新，但你可以更改刷新计划或根据需要使用“立即刷新”来尝试刷新

## <a name="system-requirements"></a>系统要求
Azure 搜索内容包需要对帐户启用 Azure 搜索流量分析。

## <a name="troubleshooting"></a>故障排除
确保已提供正确的存储帐户名称以及完整的访问密钥。 存储帐户名称应对应使用 Azure 搜索流量分析配置的帐户。

## <a name="next-steps"></a>后续步骤
[什么是 Power BI？](../fundamentals/power-bi-overview.md)

[Power BI 服务中设计器的基本概念](../fundamentals/service-basic-concepts.md)

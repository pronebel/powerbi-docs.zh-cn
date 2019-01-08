---
title: 使用 Power BI 连接到 SendGrid
description: 适用于 Power BI 的 SendGrid
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 2e9da4bc46a741af42a214d4e70fd46bfaa4a541
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54007769"
---
# <a name="connect-to-sendgrid-with-power-bi"></a>使用 Power BI 连接到 SendGrid
Power BI 的 SendGrid 内容包允许你从你的 SendGrid 帐户提取见解和统计信息。 使用 SendGrid 内容包可以在仪表板中可视化你的 SendGrid 统计信息。

连接到 Power BI 的 [SendGrid 内容包](https://app.powerbi.com/getdata/services/sendgrid)。

## <a name="how-to-connect"></a>如何连接
1. 选择左侧导航窗格底部的**获取数据**。
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. 在**服务**框中，选择**获取**。
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. 选择 **SendGrid** 内容包，并单击**获取**。
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. 出现提示时，提供你的 SendGrid 用户名和密码。 选择**登录**。
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. Power BI 导入数据后，你将看到新的仪表板、报表以及左侧导航窗格中的数据集，其中填充了过去 90 天的电子邮件统计信息。 新的项目会以黄色星号 \* 标记。
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](service-dashboard-edit-tile.md)。
* [选择磁贴](consumer/end-user-tiles.md)以打开基础报表。
* 虽然数据集将按计划每日刷新，但你可以更改刷新计划或根据需要使用“立即刷新”来尝试刷新

## <a name="whats-included"></a>包含的内容
SendGrid 仪表板中提供以下指标：

* 总体电子邮件统计信息 - 请求、已发送的邮件、已退回的邮件、拦截的垃圾邮件、垃圾邮件报表等。
* 按类别列出的电子邮件统计信息
* 按地理位置列出的电子邮件统计信息
* 按 ISP 列出的电子邮件统计信息
* 按设备、客户端、浏览器列出的电子邮件统计信息

## <a name="next-steps"></a>后续步骤
[什么是 Power BI？](power-bi-overview.md)

[获取数据](service-get-data.md)


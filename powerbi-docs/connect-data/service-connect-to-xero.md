---
title: 使用 Power BI 连接到 Xero
description: 适用于 Power BI 的 Xero
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 03/06/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: c942e399eb32fd7118d515f0d072972e3a820578
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410473"
---
# <a name="connect-to-xero-with-power-bi"></a>使用 Power BI 连接到 Xero
Xero 是易于使用的专为小型企业设计的在线会计软件。 基于带有此 Power BI 模板应用的 Xero 财务状况创建引人注目的可视化效果。 你的默认仪表板包括许多小型企业指标，如现金头寸、收入和支出、盈亏趋势、应收帐款天数和投资回报。

连接到 Power BI 的 [Xero 模板应用](https://app.powerbi.com/getdata/services/xero)或了解有关 [Xero 与 Power BI](https://help.xero.com/Power-BI) 集成的详细信息。

## <a name="how-to-connect"></a>如何连接

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. 选择“Xero”\>“立即获取”。
4. 在“安装此 Power BI 应用?”中，选择“安装” 。

    ![安装 Xero](media/service-connect-to-xero/power-bi-install-xero.png)

4. 在“应用”窗格中，选择“Xero”磁贴 。

   ![选择“Xero”磁贴](media/service-connect-to-xero/power-bi-start-xero.png)

6. 在“开始使用新应用”中，选择“连接” 。

    ![开始使用新应用](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. 为与你的 Xero 帐户相关联的组织输入一个昵称。 任何名称均可，这主要是为帮助拥有多个 Xero 组织的用户整理组织。 有关详细信息，请参阅本文后面的 [查找参数](#FindingParams)。

    ![组织昵称](media/service-connect-to-xero/params.png)

5. 对于“身份验证方法”，选择“OAuth”。 当出现提示时，请登录你的 Xero 帐户并选择要连接的组织。 登录完成后，请选择“登录”以启动加载过程。
   
    ![身份验证方法](media/service-connect-to-xero/creds.png)
   
    ![欢迎使用 Xero](media/service-connect-to-xero/creds2.png)
6. 审批后，导入过程将自动开始。 导入完成后，导航窗格中将出现新的仪表板、报表和模型。 选择仪表板查看已导入的数据。
   
     ![Xero 仪表板](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**下一步？**

* 尝试在仪表板顶部的[在“问答”框中提问](../consumer/end-user-q-and-a.md)
* 在仪表板中[更改磁贴](../create-reports/service-dashboard-edit-tile.md)。
* [选择磁贴](../consumer/end-user-tiles.md)以打开基础报表。
* 虽然数据集将按计划每日刷新，但你可以更改刷新计划或根据需要使用“立即刷新”来尝试刷新

## <a name="whats-included"></a>包含的内容
模板应用仪表板包括涵盖各个区域的磁贴和指标，有关详细信息，请参阅对应报表：  

| 分区图 | 仪表板磁贴 | 报表 |
| --- | --- | --- |
| 现金 |每日现金流 <br>兑现 <br>结算 <br>按帐户结算余额 <br>结算今日余额 |银行帐户 |
| 客户 |已开票销售额 <br>已开票销售额（按客户） <br>已开票销售额增长趋势 <br>发票到期 <br>未收的应收帐款 <br>逾期应收帐款 |客户 <br>库存 |
| 供应商 |已开帐单购买 <br>已开帐单购买（按供应商） <br>已开帐单购买的增长趋势 <br> 帐单到期 <br>未收的应付帐款 <br>逾期应付帐款 |供应商 <br>库存 |
| 库存 |每月销售额（按产品） |库存 |
| 损益 |每月损益 <br>本财政年净利润 <br>本月净利润 <br>最高支出帐户 |损益 |
| 资产负债表 |总资产 <br>总负债 <br>权益 |资产负债表 |
| 健康产业 |流动比率 <br>毛利润百分比 <br> 总资产回报率 <br>总负债/权益比率 |健康产业 <br>术语和技术说明 |

数据集还包括以下各表，用于自定义你的报表和仪表板：  

* 地址  
* 警报  
* 银行对帐单每日余额  
* 银行对帐单  
* 联系人  
* 费用报销单  
* 发票行项目  
* 发票  
* 项  
* 月末  
* 组织  
* Trial Balance  
* Xero 帐户

## <a name="system-requirements"></a>系统要求
访问 Xero 模板应用需要以下角色：“Standard + Reports”或“Advisor”。

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>查找参数
为你的组织提供名称以便在 Power BI 中进行跟踪。 指定名称将允许你连接到多个不同的组织。 不能多次连接到同一个组织，因为它会影响计划刷新。   

## <a name="troubleshooting"></a>故障排除
* Xero 用户必须具有以下角色才能访问 Power BI 的 Xero 模板应用：“Standard + Reports”或“Advisor”。 模板应用需要使用基于用户的权限才能通过 Power BI 访问报表数据。
* 加载过程中，仪表板上的磁贴处于泛加载状态。 它们会一直保持这种状态，直到完成整个加载。 如果收到加载完成的通知，但磁贴仍处于加载状态，请尝试使用仪表板右上角的 ... 刷新仪表板磁贴。
* 如果模板应用刷新失败，请检查是否在 Power BI 中多次连接到同一组织。 Xero 只允许对组织的单一活动连接，如果多次连接到同一组织，则可能会看到错误消息，提示你的凭据无效。  
* 对于连接 Power BI 的 Xero 模板应用遇到的问题（如错误消息或加载缓慢），请先清除缓存或 cookie 并重启浏览器，然后重新连接到 Power BI。  

如果仍存在其他问题，请前往 https://support.powerbi.com 提交票证。

## <a name="next-steps"></a>后续步骤
[Power BI 入门](../fundamentals/service-get-started.md)

[在 Power BI 中获取数据](service-get-data.md)

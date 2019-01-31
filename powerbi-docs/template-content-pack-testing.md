---
title: 测试 Power BI 的模板内容包
description: 模板内容包测试
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: 8a5382a5e435f916599b05310f89d9b1f0327023
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430662"
---
# <a name="testing-template-content-packs-for-power-bi"></a>测试 Power BI 的模板内容包
提交内容包进行发布之前，有多种方法测试你的内容包。  

> [!NOTE]
> 如果你的内容包使用你开发的自定义[数据连接器](https://aka.ms/DataConnectors)，则不能测试数据刷新或模板内容包，如下所述。 如果是这样的话，请继续[提交](#submission)你的内容包，Power BI 团队将与你一起测试你的内容包。
> 
> 

## <a name="testing-scheduled-data-refresh"></a>测试计划的数据刷新
连接时，模板内容包可利用 PowerBI.com 中的刷新实例化具有客户数据的内容包。 公开发布内容包之前，可以使用已创建的 Desktop 文件测试此流程。

上传文件后，选择数据集旁边的“...”，然后选择“计划刷新”。 为源配置凭据。 请确保你的数据集刷新成功，同时尝试“立即刷新”和“计划刷新”。 如果刷新遇到任何故障，请查阅错误消息并验证你的查询和终端系统。

### <a name="additional-refresh-tips"></a>其他刷新提示
* 当你尝试计划刷新时，应只检测到一个数据源。  
* 测试连接应指示你的用户将能够加载该内容包。 如果不是这种情况，请确保你的查询可以处理更多错误情况。  
* 刷新应在合理的时间内完成，建议大约 5 分钟时间。  

![设置](media/template-content-pack-testing/scheduledrefresh.png)

<a name="templates"></a>

## <a name="testing-templates"></a>测试模板
模板内容包类似于现有的解决方案，只不过它的数据集中不包括实际数据。 相反，当用户使用或实例化模板时，将提示他们提供参数和凭据才能连接。 连接后，他们将在仪表板、报表和数据集中看到自己的数据。 

用户将有权访问的内容包实例化到数据集设置（包括计划刷新）后，数据集上的任何 RLS 设置都**不**会随内容包一同发布。  

> [!NOTE]
> 模板内容包中只包括 1 个仪表板、1 个报表和 1 个数据集。 请在[创作](template-content-pack-authoring.md#restrictions)页面查看限制列表。 
> 
> 

若要为租户启用模板创建，请与 Power BI 管理员联系以启用以下功能开关。 

![功能开关](media/template-content-pack-testing/featureswitch.png)

启用后，你会看到[“创建内容包”](https://app.powerbi.com/groups/me/publish-content/)底部的复选框，允许你将模板内容包发布到组织。 

![复选框](media/template-content-pack-testing/checkbox.png)

### <a name="naming"></a>命名
建议在整个内容包中统一命名仪表板、报表和数据集，确保一致性。 这些名称都采用硬编码形式，并且对于所有用户都相同，因此使用产品/方案名称更易于客户查找。

### <a name="additional-template-tips"></a>其他模板提示
* 确保在查询中指定的参数对最终用户有意义
* 请考虑最终用户需要等待多长时间完成计划刷新

![创建](media/template-content-pack-testing/createtemplate.png)

<a name="submission"></a>

## <a name="submission"></a>提交
通过 [Microsoft AppSource](https://appsource.microsoft.com/partners/list-an-app) 进行的提交过程将允许你在 PowerBI.com 的服务内容包库中发布你的模板内容包，并在 [Microsoft AppSource](http://appsource.microsoft.com) 中列出内容包。

### <a name="before-submission"></a>提交之前
* 查看内容包中每个项目的创作提示
* 测试并连接各种帐户和数据条件。 （如果你开发自己的自定义[数据连接器](https://aka.ms/DataConnectors)，则跳过此步骤）
* 查看所有视觉对象，请仔细查看拼写错误项
* 为确保内容包对问答响应良好，建议对整个数据模型进行至少 30 个不同问题的测试。 （如果你开发自己的自定义[数据连接器](https://aka.ms/DataConnectors)，则跳过此步骤）

### <a name="submission"></a>提交
准备好进行提交后，请访问 AppSource 上的[应用提交页](https://appsource.microsoft.com/partners/list-an-app)，并提交你的信息。 请务必从可用的产品列表中选择 Power BI

Power BI 团队会审查你的提交内容，并与你联系以确保所有项目都符合提交要求。 除确保完整以外，我们还将验证提供的仪表板和报表的质量以确保它们满足应用程序中所述的业务方案。

### <a name="updates"></a>更新
遵循与原始提交相同的流程更新你的内容包。 


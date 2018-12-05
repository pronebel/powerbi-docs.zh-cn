---
title: 在 Power BI 中使用组织自定义视觉对象
description: 在 Power BI 中使用、管理和创建组织的自定义视觉对象
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/05/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: e34491ebc1cc7554e8c8c000da7528754b5a673b
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223090"
---
# <a name="use-organizational-custom-visuals-in-power-bi"></a>在 Power BI 中使用组织级的自定义视觉对象

你可以在 Power BI 中使用自定义视觉对象量身定做特殊的视觉对象类型来传达你的数据见解。 自定义视觉对象通常由开发人员进行创建，当 Power BI 中包含的众多视觉对象不能十分满足他们的需求时，常常会创建自定义视觉对象。 

在某些组织中，自定义视觉对象对其尤为重要，可能必须使用它们才能向组织传递特定数据或唯一见解，它们可能具有特殊数据要求，或者可以高亮显示私有业务方法。 此类组织需要开发自定义视觉对象，在其整个组织中共享这些视觉对象，并确保对其进行正常维护。 Power BI 自定义视觉对象可让组织实现上述目标。

下图显示了 Power BI 中的组织级自定义视觉对象从管理员开始通过开发和维护最终转到数据分析人员手中的过程。

![自定义视觉对象图片](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Power BI 管理员从管理门户界面部署和管理组织视觉对象。 视觉对象一旦部署到组织的存储库后，组织中的用户便可以轻松发现它们，并直接从 Power BI Desktop 将组织级自定义视觉对象导入到报表中。

若要详细了解如何在创建的报表中使用组织级自定义视觉对象，请参阅以下文章：[详细了解如何将组织的视觉对象导入报表](power-bi-custom-visuals.md)。

## <a name="administer-organizational-custom-visuals"></a>管理组织级自定义视觉对象

若要详细了解如何执行、部署和管理组织中的自定义视觉对象，请参阅以下文章：[详细了解如何部署和管理组织级自定义视觉对象](https://go.microsoft.com/fwlink/?linkid=866790)。

> [!WARNING]
> 自定义视觉对象可能包含存在安全或隐私风险的代码。 在将其部署到组织存储库之前，请务必确保你可以信任自定义视觉对象的作者和来源。

## <a name="considerations-and-limitations"></a>注意事项和限制

有几个事项和限制需要注意。

管理员：

* 不支持旧的自定义视觉对象（例如不是基于新版本 API 生成的自定义视觉对象无法支持）

* 如果从存储库中删除自定义视觉对象，那么任何使用过此自定义视觉对象的报表都将不再呈现该内容。 存储库中的删除操作是不可逆的。 若要暂时禁用自定义视觉对象，请使用“禁用”功能。

最终用户：

* 组织的自定义视觉对象是从组织存储库中导入的专用视觉对象。 像任何专用视觉对象一样，它们不能被[导出到 PowerPoint上](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint)，或在用户通过[订阅报表页面](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe)接收的电子邮件中进行显示。 只有从市场中直接导入的[已认证的自定义视觉对象](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified)才支持这些功能。

* 如果来自 AppSource 市场的 Visio 视觉对象、PowerApps 视觉对象、Map box 视觉对象和 GlobeMap 视觉对象通过组织存储库进行部署，它们将不会予以呈现。

## <a name="troubleshoot"></a>疑难解答

有关疑难解答的信息，请访问 [Power BI 自定义视觉对象疑难解答](power-bi-custom-visuals-troubleshoot.md)。

## <a name="faq"></a>常见问题解答

有关详细信息和问题的答案，请访问[关于 Power BI 自定义视觉对象的常见问题解答](power-bi-custom-visuals-faq.md#organizational-custom-visuals)。

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)。

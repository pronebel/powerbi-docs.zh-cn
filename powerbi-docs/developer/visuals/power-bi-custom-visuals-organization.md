---
title: Power BI 中的组织视觉对象
description: 在 Power BI 中使用、管理和创建组织的视觉对象
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/11/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: b969fa3dd04f25c8921db563a89b11125216c752
ms.sourcegitcommit: ffc46032d0771227395cc38be9ec9ff1500eac70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89401947"
---
# <a name="organizational-visuals-in-power-bi"></a>Power BI 中的组织视觉对象

可以在 Power BI 中使用 Power BI 视觉对象创建为自己量身定做的独特视觉对象类型。 Power BI 视觉对象由开发人员创建，当 Power BI 中包含的众多视觉对象不能充分满足他们的需求时，常常会创建 Power BI 视觉对象。

在某些组织中，Power BI 视觉对象甚至更为重要，可能必须使用它们才能传递组织特有的具体数据或见解，它们可能具有特殊的数据要求，或者可以突出显示专用业务方法。 此类组织需要开发 Power BI 视觉对象，在其整个组织中共享这些视觉对象，并确保对其进行正确维护。 Power BI 视觉对象可让组织实现上述目的。

下图显示了 Power BI 中的组织 Power BI 视觉对象从管理员开始通过开发和维护最终转到数据分析人员手中的过程。

![自定义视觉对象图片](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Power BI 管理员从“管理”门户部署和管理组织视觉对象。 视觉对象部署到组织存储库后，组织中的用户便可以轻松发现它们，并直接从 Power BI Desktop 将组织 Power BI 视觉对象导入到其报表中。

若要详细了解如何在创建的报表中使用组织 Power BI 视觉对象，请参阅以下文章：[详细了解如何将组织视觉对象导入报表](power-bi-custom-visuals.md)。

## <a name="administer-organizational-power-bi-visuals"></a>管理组织 Power BI 视觉对象

若要详细了解如何执行、部署和管理组织中的组织 Power BI 视觉对象，请参阅以下文章：[详细了解如何部署和管理组织 Power BI 视觉对象](../../admin/organizational-visuals.md)。

> [!WARNING]
> 通过文件安装的 Power BI 视觉对象可能包含存在安全或隐私风险的代码。 在将 Power BI 视觉对象文件部署到组织存储库之前，请确保你信任它的作者和源。

## <a name="considerations-and-limitations"></a>注意事项和限制

需留意几个注意事项和限制。

管理员：

* 如果从存储库中删除 ApSource 或文件中的 Power BI 视觉对象，任何使用删除的视觉对象的现有报表都会停止呈现。 从存储库中删除是不可逆的。 若要暂时禁用 ApSource 或文件中的 Power BI 视觉对象，请使用“禁用”功能。

* Power BI 报表服务器不支持组织 Power BI 视觉对象。

最终用户：

* 组织 Power BI 视觉对象是从组织存储库中导入的专用视觉对象。 与任何专用视觉对象一样，不能将它们[导出到 PowerPoint](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint)，也不能在用户[订阅报表页面](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe)时接收的电子邮件中显示它们。 只有从市场中直接导入的[已认证 Power BI 视觉对象](power-bi-custom-visuals-certified.md)才支持这些功能。

* 如果来自 AppSource 市场的 Visio 视觉对象、PowerApps 视觉对象、Map box 视觉对象和 GlobeMap 视觉对象通过组织存储库部署，它们将不会呈现。

## <a name="troubleshoot"></a>疑难解答

有关疑难解答的信息，请访问 [Power BI 视觉对象疑难解答](power-bi-custom-visuals-troubleshoot.md)。

## <a name="faq"></a>常见问题解答

有关详细信息和问题的答案，请访问[关于 Power BI 视觉对象的常见问题解答](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)。

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)。

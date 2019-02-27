---
title: 可能需要额外付费 - Power BI 视觉对象指南
description: 了解如何将自定义视觉对象发布到 AppSource 让其他人了解并付费使用。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: 92d4320026164e523297cbe48ee87ce33d9ab2f7
ms.sourcegitcommit: 796bf513bf8669676e2a44627b56221b1629a6a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2019
ms.locfileid: "56826574"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>额外购买的 Power BI 视觉对象指南

一直到最近，市场 (AppSource) 仅接受免费的 Power BI 视觉对象。 此策略已更改，还可以向 AppSource 提交带有“可能需要额外付费”价格标签的视觉对象。 

“可能需要额外付费”的视觉对象类似于 Office 应用商店中的应用内购买 (IAP) 加载项。 在得到 AppSource 团队的批准，并确保视觉对象符合认证要求后，开发人员还可提交这些视觉对象进行认证。 有关要求的详细信息，请参阅[认证的自定义视觉对象](../power-bi-custom-visuals-certified.md)。

> [!NOTE]
> * 要认证的视对象觉不得访问外部服务或资源。
> * 所有免费视觉对象应保留以前提供的相同免费功能。 可以在现有免费功能基础上添加可选的高级付费功能。 我们建议将具有高级功能的 IAP 视觉对象作为新视觉对象提交，而不是更新现有免费视觉对象。


## <a name="what-changed-in-the-submission-process"></a>提交过程有什么变化？

开发人员通过卖家仪表板将其 IAP 视觉对象上传到 AppSource，与上传免费视觉对象时一样。 为表明提交的视觉对象具有 IAP 功能，开发人员应在卖家仪表板上注明：“应用内购买视觉对象。” 此外，开发人员需提供许可证密钥或令牌，以便验证团队可验证 IAP 功能。 在视觉对象通过验证和批准后，列出 IAP 视觉对象的 AppSource 会在定价选项下声明“可能需要额外付费”。

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>什么是具有 IAP 功能的 Power BI 视觉对象？

IAP 视觉对象是一个免费的视觉对象，可提供免费功能。 它还有一些高级功能，可能需要支付额外费用才能使用这些功能。 在视觉对象的描述中，开发人员必须告知用户哪些功能需要额外付费。 目前，Microsoft 不提供支持购买应用和加载项的本机 API。

开发人员可使用各种第三方支付系统进行购买。 有关详细信息，请参阅[我们的应用商店策略](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads)。

> [!NOTE]
> 不允许在免费功能上设置水印。 如果在没有有效许可证的情况下使用高级付费功能，开发人员可能会显示一个弹出窗口或水印。  

## <a name="logo-guidelines"></a>徽标指南

本部分介绍了在视觉对象中添加徽标和标识的规范。

> [!NOTE]
> 仅允许在编辑模式下使用徽标。 无法在查看模式下显示徽标。

![定义](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![需要注意的事项](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![需要避免的事项](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![大小和格式](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![边距和大小调整](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![编辑模式](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>最佳做法

### <a name="visual-landing-page"></a>视觉对象登陆页面

使用登陆页面向用户说明视觉对象的使用方法，以及在何处购买许可证。 请勿包含自动播放的视频。 仅添加有助于改善用户体验的材料，例如有关许可证购买详情的信息或链接，以及如何使用 IAP 功能。

### <a name="license-key-and-token"></a>许可证密钥和令牌

为方便用户，请在格式窗格的顶部添加许可证密钥或令牌相关字段。

## <a name="faq"></a>常见问题解答

有关视觉对象的详细信息，请参阅[关于额外付费的视觉对象的常见问题解答](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases)。

## <a name="next-steps"></a>后续步骤

了解如何将自定义视觉对象发布到 [AppSource](office-store.md) 让其他人了解和使用。

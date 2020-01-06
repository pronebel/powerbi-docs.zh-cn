---
title: Power BI 视觉对象指南
description: 了解如何将自定义视觉对象发布到 Microsoft AppSource 让其他人了解并付费使用。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 07/16/2019
ms.openlocfilehash: 6bf7610a010a72248a3d2fdd96718eea513a68da
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000080"
---
# <a name="guidelines-for-power-bi-visuals"></a>Power BI 视觉对象指南
在将 Power BI 视觉对象[发布](https://docs.microsoft.com/power-bi/developer/office-store)到 Microsoft AppSource 供其他人了解和使用之前，请遵循相关指南，为用户创造好的体验。

## <a name="power-bi-visuals-with-additional-purchases"></a>需额外付费的 Power BI 视觉对象

可以向市场 (Microsoft AppSource) 提交免费的 Power BI 视觉对象。 还可以向 Microsoft AppSource 提交带有“可能需要额外付费”价格标签的 Power BI 视觉对象。 “可能需要额外付费”的 Power BI 视觉对象类似于 Office 应用商店中的应用内购买 (IAP) 加载项。 

IAP Power BI 视觉对象与免费 Power BI 视觉对象类似，也可以认证。 提交 IAP Power BI 视觉对象进行认证之前，请确保它符合[认证要求](../power-bi-custom-visuals-certified.md)。 

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>什么是具有 IAP 功能的 Power BI 视觉对象？

IAP Power BI 视觉对象是一种免费的视觉对象，可提供免费功能   。 它还有一些高级功能，可能需要支付额外费用。 在 Power BI 视觉对象的描述中，开发人员必须告知用户哪些功能需要额外付费。 目前，Microsoft 不提供支持购买应用和加载项的本机 API。

开发人员可使用各种第三方支付系统进行购买。 有关详细信息，请参阅[我们的应用商店策略](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads)。


>[!IMPORTANT]  
> 如果将 Power BI 视觉对象从免费更新为“可能需要额外付费”，用户必须获得与更新前相同级别的免费功能。 可以在现有免费功能基础上添加可选的高级付费功能。

### <a name="watermarks"></a>水印

你可使用水印，以便客户可以继续使用 IAP 高级功能，而无需付费。 

在购买之前，水印可用于展示 Power BI 视觉对象的全部功能。 

* 只能为使用时无有效许可的付费功能使用水印。
* 带有“免费”价格标签的 Power BI 视觉对象中不允许使用水印  。
* 当用户使用免费功能时，IAP 视觉对象中不允许使用水印。 

### <a name="pop-up-window"></a>弹出窗口

如果在 Power BI IAP 视觉对象中使用了无效（或过期）许可证，则可以使用弹出窗口来说明如何购买许可证。

### <a name="submission-process"></a>提交过程

按照[提交过程](office-store.md#submitting-to-appsource)，然后导航到“产品设置”选项卡，并选中“我的产品要求购买服务”复选框   。

在 Power BI 视觉对象通过验证和批准后，列出 IAP Power BI 视觉对象的 Microsoft AppSource 会在定价选项下声明“可能需要额外付费”。

>[!NOTE]
>如果已使用[卖家面板](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store)提交了 Power BI 视觉对象，并且需要添加 IAP 功能，则必须在卖家面板注释中写明“可在应用内购买的视觉对象”。 此外，还需提供许可证密钥或令牌，以便验证团队可验证 IAP 功能。

## <a name="context-menu"></a>上下文菜单
上下文菜单是在用户将鼠标悬停在视觉对象上时显示的右键单击菜单。
所有 Power BI 视觉对象都应启用上下文菜单，以带来统一的体验。 请查看[本文](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md)了解如何添加上下文菜单。

## <a name="commercial-logo"></a>商业徽标
本部分介绍了在 Power BI 视觉对象中添加商业徽标的规范。 商业徽标并非强制需要。 如果已添加徽标，则其必须遵循这些准则。

> [!NOTE]
> * 本文中的“商业徽标”一词指下面图片中所描述的任何商业性质的公司图标。
> * 本文仅以 Microsoft 商业徽标为例。 将自己的商业徽标与 Power BI 视觉对象配合使用。

> [!IMPORTANT]
> 仅允许在编辑模式下使用商业徽标  。 无法在查看模式下显示商业徽标  。

### <a name="commercial-logo-type"></a>商业徽标类型

有三种类型的商业徽标：
* **徽标** - 徽标包括两个锁定在一起的元素，图标和名称。

    ![Microsoft 徽标](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **符号** - 没有任何文本的图形。

    ![Microsoft 符号](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **标识** - 不带图标的徽标，只包括文本。

    ![Microsoft 符号](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>商业徽标颜色

使用商业徽标时，徽标的颜色必须为灰色（十六进制颜色 #C8C8C8）。 请勿向商业徽标添加效果（如渐变）。

* **徽标**

    ![Microsoft 符号](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **符号** - 没有任何文本的图形。

    ![Microsoft 符号](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **标识** - 不带图标的徽标，只包括文本。

    ![Microsoft 符号](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * 如果 Power BI 视觉对象包含图形，请考虑为徽标添加白色背景（10 px 边距）。
> * 请考虑为徽标添加阴影（不透明度为 30% 的黑色）。

### <a name="commercial-logo-size"></a>商业徽标大小

Power BI 视觉对象需要两个商业徽标，一个用于大型磁贴，一个用于小型磁贴。 将徽标放置在位于右上角或右下角的边界框中（4 px 边距）。

下表描述了 Power BI 视觉对象的大小注意事项。

|  |小型 Power BI 视觉对象  |大型 Power BI 视觉对象  |
|---------|---------|---------|
|徽标宽度     |最多 240 px         |大于 240 px         |
|徽标高度      |最多 160 px         |大于 160 px         |
|边界框大小      |40 x 15 px         |101 x 30 px         |
|商业徽标示例      |![Microsoft 符号](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Microsoft 徽标](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|边界框示例     |![小型徽标示例](media/guidelines-powerbi-visuals/small-logo-box.png)         |![大型徽标示例](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>商业徽标行为

仅允许在编辑模式下使用商业徽标。 单击商业徽标后只能包含以下功能：

* 单击商业徽标将重定向到你的网站。

* 单击商业徽标将打开一个弹出窗口，其中包含附加信息。 弹出窗口应分为两部分：
    * 营销区域，其中可包含商业徽标、视觉对象和市场评级。
    * 信息区域，其中可包含信息和链接。    


### <a name="things-to-avoid"></a>需要避免的事项

* 无法在查看模式下显示商业徽标。

* 动画商业徽标可显示长达五秒的动画。

* 如果 Power BI 视觉对象在阅读模式下包含信息性图标 (i)，则它们应符合上述商业徽标的颜色、大小和位置。

* 避免使用彩色或黑色商业徽标。 商业徽标必须为灰色（十六进制颜色 #C8C8C8）。

    ![未经授权的彩色徽标](media/guidelines-powerbi-visuals/no-color-logo.png) ![未经授权的黑色徽标](media/guidelines-powerbi-visuals/black-logo.png)

* 带有效果的商业徽标，如渐变或强阴影。

    ![未经授权的徽标样式](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>最佳做法

发布 Power BI 视觉对象时，请考虑以下建议，以便提供良好的用户体验。

### <a name="visual-landing-page"></a>视觉对象登陆页面

使用登陆页面向用户说明 Power BI 视觉对象的使用方法，以及在何处购买许可证。 请勿包含自动播放的视频。 仅添加有助于改善用户体验的材料，例如有关许可证购买详情的信息或链接，以及如何使用 IAP 功能。

### <a name="license-key-and-token"></a>许可证密钥和令牌

为方便用户，请在格式窗格的顶部添加许可证密钥或令牌相关字段。

## <a name="faq"></a>常见问题解答

有关 Power BI 视觉对象的详细信息，请参阅[关于额外付费的 Power BI 视觉对象的常见问题解答](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases)。

## <a name="next-steps"></a>后续步骤

了解如何将 Power BI 视觉对象发布到 [Microsoft AppSource](office-store.md) 让其他人了解并使用。
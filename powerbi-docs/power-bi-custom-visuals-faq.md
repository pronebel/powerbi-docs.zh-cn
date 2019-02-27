---
title: 有关 Power BI 自定义视觉对象的常见问题
description: 浏览有关 Power BI 自定义对象的常见问题和解答列表
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 9b4ff995b1cfaede1608e976bf2715feece0ade6
ms.sourcegitcommit: a2f274cfb392fe3b1b466a39ec7eaf58a7c5ce00
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "56408129"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>有关 Power BI 自定义视觉对象的常见问题

## <a name="organizational-custom-visuals"></a>组织的自定义视觉对象

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>管理员如何管理组织的自定义视觉对象？

在管理门户中，在“组织的自定义视觉对象”选项卡下，管理员可以查看和[管理企业中的所有组织的自定义视觉对象](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals)：添加、禁用、启用和删除。
无需再通过电子邮件或共享文件夹共享这些视觉对象！ 一旦将视觉对象部署到组织的存储库，组织中的用户便可以轻松发现它们，并直接从 Power BI Desktop 或 Power BI 服务将组织的自定义视觉对象导入其报表。 可以从“我的组织”选项卡下的内置存储（在桌面和服务中）中找到组织的自定义视觉对象。一旦管理员上传新的组织的自定义视觉对像的版本，组织中的每个人都将获得同一更新的版本。 报表作者无需删除其报表中的视觉对象以获取这些视觉对象的新版本，因为使用这些视觉对象的所有报表都将被自动更新！ 更新机制类似于市场视觉对象。

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>如果管理员将自定义视觉对象从公共市场上传到组织存储，当供应商在公共市场更新视觉对象后，它是否会被自动更新？

不，不会有来自公共市场的任何自动更新。
更新组织的自定义视觉对象的版本是管理员的职责。

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>是否有方法禁用组织的存储？

不，用户始终能够从 Power BI 桌面和服务中看到“我的组织”选项卡。 管理员可以从管理门户禁用或删除所有组织的自定义视觉对象，且组织存储为空。
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>如果管理员禁用管理门户中的自定义视觉对象（“租户”设置），用户是否仍具有组织的自定义视觉对象的访问权限？

是，如果管理员禁用管理门户上的自定义视觉对象，它不会影响组织存储。 某些组织禁用自定义视觉对象，且仅启用由 Power BI 管理员导入和上传到组织存储的手动选择的视觉对象。 在 Power BI Desktop 中不会强制禁用来自管理门户中的自定义视觉对象。 桌面用户仍然可以在其报表中添加和使用来自公共市场的自定义视觉对象。 但是，一旦这些公共自定义视觉对象被发布到 Power BI 服务，它们将停止呈现，并发出相应的错误。 在使用 Power BI 服务时，你将无法从公共市场中导入自定义视觉对象。 仅能导入来自组织存储中的视觉对象，因为将在 Power BI 服务中强制实施管理门户中的自定义视觉对象设置。

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>为什么组织存储和组织的自定义视觉对象可提供杰出的企业解决方案？

* 每个人都会获得相同的视觉对象版本，该版本由 Power BI 管理员控制。 一旦管理员更新管理员门户中的视觉对象的版本，组织中的所有用户都将自动获得更新的版本。

* 无需再通过电子邮件或共享文件夹共享视觉对象文件！ 在一个位置对登录的所有成员都可见。

* 与市场视觉对象类似，新版本的组织的自定义视觉对象将在所有报表中自动更新，具有安全性和可支持性。

* 组织中使用组织的自定义视觉对象的用户需要登录才能查看和使用组织的自定义视觉对象，这是组织的一个安全元素。

* 管理员可以控制在组织中可以使用哪些自定义视觉对象。

* 管理员可以从管理门户中启用/禁用用于测试的视觉对象。 提供更好的安全执行，因为将仅允许这些视觉对象供组织成员使用。

## <a name="certified-custom-visuals"></a>认证的自定义视觉对象

### <a name="what-are-certified-custom-visuals"></a>什么是认证的自定义视觉对象？

认证的自定义视觉对象是[市场](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中满足由 Power BI 团队[指定](power-bi-custom-visuals-certified.md)的代码要求和测试的视觉对象。  执行的测试旨在检查视觉对象是否会访问外部服务或资源。 但 Microsoft 不是第三方自定义视觉对象的作者。 我们建议客户直接与作者联系，验证此类视觉对象的功能。

## <a name="visuals-with-additional-purchases"></a>额外付费的视觉对象

### <a name="what-is-a-visual-with-additional-purchases"></a>什么是额外付费的视觉对象？

额外付费的视觉对象类似于市场中的应用内购买 (IAP) 加载项，这些加载项具有一个价格标记：  **可能需要额外付费** 。

IAP 自定义视觉对象是可免费下载的自定义视觉对象 - 用户无需付费即可从市场中下载这些自定义视觉对象。 IAP 视觉对象提供可选的应用内购买选项，可用于购买高级功能。  

### <a name="whats-the-benefit-to-developers"></a>对开发人员有什么益处？

许多日常访客均能够发现 AppSource 中的 IAP 自定义视觉对象，从而可带来有价值的流量，你的 IAP 自定义视觉对象和你作为一名开发人员的市场认知度由此得到提升。

如果此前你一直通过网站来管理这些视觉对象，那么现在可以将它们提交到 AppSource。 这有助于提高 IAP 视觉对象在 Power BI 社区内的可发现性和可见性。

AppSource 中的视觉对象可通过商店中的评论和评分系统，从使用 IAP 自定义视觉对象的客户那里直接获取反馈。  

你的 IAP 视觉对象获得 AppSource 验证团队的批准后，你还可以提交这些视觉对象进行认证。 这是一个可选流程。  

IAP 自定义视觉对象取得认证后，视觉对象可以导出到 PowerPoint 中，并显示在用户订阅报表页后收到的电子邮件中。 所以，现在如果将 IAP 自定义视觉对象提交到市场，还可对 IAP 视觉对象进行认证并获取额外的功能集支持。  

### <a name="do-iap-visuals-need-to-be-certified"></a>IAP 视觉对象是否需要取得认证？

认证过程是可选的。 由开发人员自行决定是否认证他们的 IAP 自定义视觉对象或使其不同于免费视觉对象。

### <a name="what-is-changing-in-the-submission-process"></a>提交过程有什么不同？

将 IAP 自定义视觉对象提交到市场的过程与提交免费视觉对象的过程相同。 都是通过卖家仪表板操作的。  提交过程的唯一差别是开发人员需要在卖家仪表板的开发人员注释中说明： “存在应用内付费的视觉对象”。 如果必须验证付费/高级功能，还需要提供许可证密钥/令牌。  

卖家仪表板中没有新增选项：免费但存在应用内付费，需将 IAP 视觉对象提交为免费视觉对象。

此外，需在你的商店里提供详细的描述，让用户知道哪些功能是免费的，哪些功能需要额外付费才能使用。  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>提交 IAP 自定义视觉对象之前应该做什么？

如果正在开发 IAP 自定义视觉对象或已经有一个，请确保其符合规范准则。  

如果自定义视觉对象中有徽标，请确保它符合徽标规范（颜色、位置、大小和操作触发）。

规范中还提供了最佳做法说明。  
> [!Note]
> 所有免费视觉效果应保留以前提供的相同免费功能。 可以在旧版免费功能基础上添加可选的高级付费功能。 我们建议将具有高级功能的 IAP 视觉效果作为新视觉效果提交，而不是更新旧版免费视觉效果。


### <a name="can-i-get-my-iap-custom-visual-certified"></a>我的 IAP 自定义视觉对象可获取认证吗？

可以，与免费视觉对象一样。  IAP 自定义视觉对象取得 AppSource 团队批准后，即可提交视觉对象进入认证流程。

若要认证视觉对象，应符合认证要求，例如视觉对象不可访问外部许可证验证服务。

认证是一个可选流程，由你决定是否要认证 IAP 视觉对象。

## <a name="additional-questions"></a>其他问题

### <a name="how-to-get-support"></a>如何获取支持？

请随时联系自定义视觉对象支持团队：  *pbicvsupport@microsoft.com*  可咨询任何相关问题或提供反馈意见。  

## <a name="next-steps"></a>后续步骤

有关详细信息，请访问 [Power BI 自定义视觉对象疑难解答](power-bi-custom-visuals-troubleshoot.md)。

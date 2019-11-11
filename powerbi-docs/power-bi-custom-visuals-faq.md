---
title: 有关 Power BI 视觉对象的常见问题
description: 浏览有关 Power BI 视觉对象的常见问题和解答列表
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: ff20ece0b96c5037e0ca98be953d77b921e37585
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874548"
---
# <a name="frequently-asked-questions-about-power-bi-visuals"></a>有关 Power BI 视觉对象的常见问题

## <a name="organizational-visuals"></a>组织视觉对象

借助管理门户，用户可以管理组织中的 Power BI 视觉对象。

### <a name="how-can-the-admin-manage-the-organizational-power-bi-visuals"></a>管理员如何管理组织 Power BI 视觉对象？

在管理门户中的“组织视觉对象”选项卡下，管理员可以查看和[管理企业中的所有组织 Power BI 视觉对象](service-admin-portal.md#organizational-visuals)：添加、禁用、启用和删除。
无需再通过电子邮件或共享文件夹共享这些视觉对象！ 视觉对象部署到组织存储库后，组织中的用户便可以轻松发现它们，并直接从 Power BI Desktop 或 Power BI 服务将组织视觉对象导入到其报表中。 可以从“我的组织”选项卡下的内置存储（在桌面和服务中）中找到组织视觉对象  。一旦管理员上传新的组织的自定义视觉对像的版本，组织中的每个人都将获得同一更新的版本。 报表作者无需删除其报表中的视觉对象以获取这些视觉对象的新版本，因为使用这些视觉对象的所有报表都将被自动更新！ 更新机制类似于市场视觉对象。

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>如果管理员将自定义视觉对象从公共市场上传到组织存储，当供应商在公共市场更新视觉对象后，它是否会被自动更新？

不，不会有来自公共市场的任何自动更新。
更新组织视觉对象的版本是管理员的职责。

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>是否有方法禁用组织的存储？

不，用户始终能够从 Power BI 桌面和服务中看到“我的组织”选项卡。 管理员可以从管理门户禁用或删除所有组织视觉对象，且组织存储为空。
  
### <a name="if-the-administrator-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-visuals"></a>如果管理员通过管理门户禁用 Power BI 视觉对象（“租户”设置），用户是否仍具有组织视觉对象的访问权限？

是，如果管理员通过管理门户禁用 Power BI 视觉对象，它不会影响组织存储。 某些组织禁用 Power BI 视觉对象，且仅启用由 Power BI 管理员导入和上传到组织存储的手动选择的视觉对象。 在 Power BI Desktop 中不会强制通过管理门户禁用 Power BI 视觉对象。 桌面用户仍然可以在其报表中添加和使用来自公共市场的 Power BI 视觉对象。 但是，一旦这些公共 Power BI 视觉对象被发布到 Power BI 服务，它们将停止呈现，并发出相应的错误。 使用 Power BI 服务时，无法从公共市场中导入 Power BI 视觉对象。 仅能导入来自组织存储的视觉对象，因为在 Power BI 服务中强制实施管理门户中的 Power BI 视觉对象设置。

### <a name="why-does-the-organizational-store-and-organizational-visuals-make-a-great-enterprise-solution"></a>为什么组织存储和组织视觉对象可提供杰出的企业解决方案？

* 每个人都会获得相同的视觉对象版本，该版本由 Power BI 管理员控制。 一旦管理员更新管理员门户中的视觉对象的版本，组织中的所有用户都将自动获得更新的版本。

* 无需再通过电子邮件或共享文件夹共享视觉对象文件！ 在一个位置对登录的所有成员都可见。

* 与市场视觉对象类似，新版本的组织视觉对象将在所有报表中自动更新，具有安全性和可支持性。

* 组织中使用组织视觉对象的用户需要登录才能查看和使用组织视觉对象，这是组织的一个安全元素。

* 管理员可控制在组织中可以使用的 Power BI 视觉对象。

* 管理员可以从管理门户中启用/禁用用于测试的视觉对象。 提供更好的安全执行，因为将仅允许这些视觉对象供组织成员使用。

## <a name="certified-power-bi-visuals"></a>已认证的 Power BI 视觉对象

### <a name="what-are-certified-power-bi-visuals"></a>什么是已认证的 Power BI 视觉对象？

已认证的 Power BI 视觉对象是[市场](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中满足 Power BI 团队的某些[指定](power-bi-custom-visuals-certified.md)代码要求并通过其测试的视觉对象。  执行的测试旨在检查视觉对象是否会访问外部服务或资源。 但 Microsoft 不是第三方 Power BI 视觉对象的作者，建议客户直接与作者联系，验证此类视觉对象的功能。

### <a name="what-tests-are-done-during-the-certification-process"></a>在认证过程中完成哪些测试？

认证过程测试包括但不限于：代码评审、静态代码分析、数据泄露测试、数据模糊测试、渗透测试、访问 XSS 测试、恶意数据注入测试、输入验证和功能测试。
 
### <a name="do-you-certify-visuals-every-submission"></a>是否每次提交时都认证视觉对象？

是。 每次向市场提交新版本的认证视觉对象时，视觉对象的版本更新将进行相同的认证检查。

开发人员请注意：如果是提交认证视觉对象的版本更新，则不需要发送单独的电子邮件作为[首次认证请求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification) 版本更新的认证会自动进行，如果出现任何导致拒绝的违规，系统都会发送一封电子邮件，说明需要修复的事项。 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>经过认证的视觉对象有没有可能因新的更新而停止认证？

不，这不可能。 经过认证的视觉对象不会因新的更新而被取消认证。 该更新将被拒绝。
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>如果我要提交到认证过程，是否需要在公共存储库中共享我的代码？

不，你不需要公开共享你的代码。 但你需要向我们提供检查视觉对象代码的读取权限。 例如 GitHub 中的专用存储库。
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>我们是否必须在[市场](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中[发布](https://docs.microsoft.com/power-bi/developer/office-store)视觉对象以进行认证？

是。 接受认证的强制要求是首先将视觉对象发布到市场。
要认证自定义视觉对象，应将它放在我们的服务器中。 我们无法认证私有视觉对象。
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>认证视觉对象需要多长时间？

若是更新版本，可能需要最多 3 周。 若是新的提交（首次验证），可能需要最多 4 周。 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>认证过程是否会确保没有数据泄漏发生？

执行的测试旨在检查视觉对象是否会访问外部服务或资源。 但 Microsoft 不是第三方 Power BI 视觉对象的作者，建议客户直接与作者联系，验证此类视觉对象的功能。
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>未经认证的 Power BI 视觉对象使用起来安全吗？

未经认证的 Power BI 视觉对象并不一定是不安全的视觉对象。
某些视觉对象未经认证，是因为它们与一个或多个[认证要求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)不符。 例如，连接到外部服务的地图视觉对象，或使用商业库的视觉对象。
 
## <a name="visuals-with-additional-purchases"></a>额外付费的视觉对象

### <a name="what-is-a-visual-with-additional-purchases"></a>什么是额外付费的视觉对象？

额外付费的视觉对象类似于市场中的应用内购买 (IAP) 加载项，这些加载项具有一个价格标记：“可能需要额外付费”  。

IAP Power BI 视觉对象是可免费下载的 Power BI 视觉对象 - 用户无需付费即可从市场中下载这些 Power BI 视觉对象。 IAP 视觉对象提供可选的应用内购买选项，可用于购买高级功能。  

### <a name="whats-the-benefit-to-developers"></a>对开发人员有什么益处？

许多日常访客能够发现 AppSource 中的 IAP Power BI 视觉对象，从而带来有价值的流量，你的 IAP Power BI 视觉对象和你作为一名开发人员的市场认知度由此得到提升。

如果此前你一直通过网站来管理这些视觉对象，那么现在可以将它们提交到 AppSource。 这有助于提高 IAP 视觉对象在 Power BI 社区内的可发现性和可见性。

AppSource 中的视觉对象可通过商店中的评论和评分系统，从使用 IAP 自定义视觉对象的客户那里直接获取反馈。  

你的 IAP 视觉对象获得 AppSource 验证团队的批准后，你还可以提交这些视觉对象进行认证。 这是一个可选流程。  

IAP Power BI 视觉对象取得认证后，视觉对象可以导出到 PowerPoint 中，并在用户订阅报表页后收到的电子邮件中显示。 因此，现在如果将 IAP 视觉对象提交到市场，还可对 IAP Power BI 视觉对象进行认证并获取额外的功能集支持。  

### <a name="do-iap-visuals-need-to-be-certified"></a>IAP 视觉对象是否需要取得认证？

认证过程是可选的。 由开发人员自行决定是否认证他们的 IAP Power BI 视觉对象或使其不同于免费视觉对象。

### <a name="what-is-changing-in-the-submission-process"></a>提交过程有什么不同？

将 IAP Power BI 视觉对象提交到市场的过程与提交免费视觉对象的过程相同。 都是通过卖家仪表板操作的。  提交过程的唯一差别是开发人员需要在卖家仪表板的开发人员注释中说明： “存在应用内付费的视觉对象”。 如果必须验证付费/高级功能，还需要提供许可证密钥/令牌。  

卖家仪表板中没有新增选项：免费但存在应用内付费，需将 IAP 视觉对象提交为免费视觉对象   。

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

请随时联系 Power BI 视觉对象支持团队 ( *pbicvsupport@microsoft.com*  )，可咨询任何相关问题或提供反馈意见。  

## <a name="next-steps"></a>后续步骤

有关详细信息，请访问 [Power BI Power BI 视觉对象疑难解答](power-bi-custom-visuals-troubleshoot.md)。

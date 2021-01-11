---
title: Power BI 嵌入式分析中用于增强嵌入式 BI 见解的 Power BI 视觉对象的常见问题解答
description: 浏览有关 Power BI 视觉对象的常见问题和解答列表。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 09/30/2020
ms.openlocfilehash: b2bfac5cbd3ce9b850e42ebf25c63b6e22fbeb68
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97884915"
---
# <a name="power-bi-visuals-faq"></a>Power BI 视觉对象常见问题解答

## <a name="organizational-power-bi-visuals"></a>组织 Power BI 视觉对象

借助管理门户，用户可以管理组织中的 Power BI 视觉对象。

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>管理员如何管理组织 Power BI 视觉对象？

在管理门户中的“组织视觉对象”选项卡下，管理员可以查看和[管理企业中的所有组织 Power BI 视觉对象](../../admin/organizational-visuals.md#organizational-visuals)  。 具体操作包括添加、禁用、启用和删除 Power BI 视觉对象。

组织中的用户可以轻松地查找 Power BI 视觉对象，并直接从 Power BI Desktop 或服务将视觉对象导入到自己的报表中。

一旦管理员上传组织 Power BI 视觉对象的新版本，组织中的每个人都将获得相同的更新版本。 使用更新的 Power BI 视觉对象的所有报表都将自动更新。

用户可以在内置 Power BI Desktop 和 Power BI 服务组织存储中的“我的组织”  选项卡下找到组织 Power BI 视觉对象。 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-using-add-visual--from-appsource-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>如果管理员使用“添加视觉对象”>“来自 AppSource”将 Power BI 视觉对象从公共市场上传到组织存储，它是否会在供应商更新公共市场中的视觉对象后自动更新？

会，视觉对象会从公共市场自动更新。 如果视觉对象已获得认证，则会保留认证，包括导出到 PDF 或 PowerPoint 等其他功能。

### <a name="is-there-a-way-to-disable-the-organization-store"></a>是否有方法禁用组织存储？

没有，用户始终能够从 Power BI 桌面和服务中看到“我的组织”选项卡  。 如果管理员从管理门户中禁用或删除所有组织 Power BI 视觉对象，组织存储将为空。
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>如果管理员通过管理门户禁用 Power BI 视觉对象（“租户”设置），用户是否仍具有组织 Power BI 视觉对象的访问权限？

是，如果管理员通过管理门户禁用 Power BI 视觉对象，它不会影响组织存储。

某些组织禁用 Power BI 视觉对象，且仅启用由 Power BI 管理员导入和上传到组织存储的手动选择的视觉对象。

在 Power BI Desktop 中不会强制通过管理门户禁用 Power BI 视觉对象。 桌面用户仍然可以在其报表中添加和使用来自公共市场的 Power BI 视觉对象。 但是，一旦这些公共 Power BI 视觉对象被发布到 Power BI 服务，它们将停止呈现，并发出相应的错误。 

强制执行管理门户中的 Power BI 视觉对象设置后，Power BI 服务中的用户无法从公共市场导入 Power BI 视觉对象。 只能导入来自组织存储的视觉对象。

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>组织存储中的 Power BI 视觉对象有什么优点？

* 每个人都会获得相同的视觉对象版本，该版本由 Power BI 管理员控制。一旦管理员更新管理员门户中的视觉对象的版本，组织中的所有用户都将自动获得更新的版本。

* 无需通过电子邮件或共享文件夹共享视觉对象文件。 组织存储产品/服务对所有已登录的成员可见。

* 新版本的组织 Power BI 视觉对象将在所有报表中自动更新，具有安全性和可支持性。

* 管理员可控制在组织中可以使用的 Power BI 视觉对象。

* 管理员可以从管理门户中启用/禁用用于测试的视觉对象。

## <a name="certified-power-bi-visuals"></a>已认证的 Power BI 视觉对象

### <a name="what-are-certified-power-bi-visuals"></a>什么是已认证的 Power BI 视觉对象？

经过认证的 Power BI 视觉对象是满足特定[要求](power-bi-custom-visuals-certified.md)并由 Microsoft 进行认证的 Power BI 视觉对象。

在[市场](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中，经过认证的 Power BI 视觉对象有一个黄色徽章，指示它们已经过认证。

Microsoft 不是第三方 Power BI 视觉对象的作者。 我们建议客户直接与作者联系，验证第三方视觉对象的功能。

### <a name="what-tests-are-done-during-the-certification-process"></a>在认证过程中完成哪些测试？

认证过程测试包括但不限于： 
* 代码评审
* 静态代码分析
* 数据泄露
* 数据模糊测试
* 渗透测试
* 访问 XSS 测试
* 恶意数据注入
* 输入验证
* 功能测试
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Power BI 视觉对象经过认证后，每次新提交（升级）时是否会再次进行检查？

是。 每次向市场提交新版本的经过认证的视觉对象时，视觉对象的版本更新将进行相同的认证检查。

版本更新证书是自动生成的。 如果存在导致拒绝更新的冲突，系统会向开发人员发送一封电子邮件，说明需要解决的问题。

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>在新的更新后，经过认证的 Power BI 视觉对象的认证可能会停用/丢失吗？

不，这不可能。 经过认证的视觉对象不会因新的更新而丢失认证。 该更新将被拒绝。
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>如果要认证 Power BI 视觉对象，是否需要在公共存储库中共享我的代码？

不，你不需要公开共享你的代码。

可以提供读取权限以检查 Power BI 视觉对象代码。 例如，通过使用 GitHub 中的专用存储库来操作。
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>经过认证的 Power BI 视觉对象是否必须位于市场中？

是。 专用视觉对象不进行认证。
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>认证视觉对象需要多长时间？

认证新 Power BI 视觉对象（首次认证）最多可能需要四周。 

认证 Power BI 视觉对象的更新版本最多可能需要三周时间。 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>认证过程是否能确保没有数据泄露？

执行的测试旨在检查视觉对象是否会访问外部服务或资源。 

Microsoft 不是第三方 Power BI 视觉对象的作者。 我们建议客户直接与作者联系，验证第三方 Power BI 视觉对象的功能。
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>未经认证的 Power BI 视觉对象使用起来安全吗？

未经认证的 Power BI 视觉对象并不一定是不安全的视觉对象。

某些视觉对象未经认证，因为它们与一个或多个[认证要求](power-bi-custom-visuals-certified.md#certification-requirements)不符。 例如，连接到外部服务的地图视觉对象，或使用商业库的视觉对象。
 
## <a name="visuals-with-additional-purchases"></a>额外付费的视觉对象

### <a name="what-is-a-visual-with-additional-purchases"></a>什么是额外付费的视觉对象？

具有额外购买的视觉对象类似于应用内购买  (IAP) 加载项。 这些加载项包括“可能需要额外购买”  价格标记。

IAP Power BI 视觉对象是免费的可下载 Power BI 视觉对象。 用户无需付费即可从市场下载这些 Power BI 视觉对象。

IAP 视觉对象提供可选的应用内购买选项，可用于购买高级功能。  

### <a name="what-is-changing-in-the-submission-process"></a>提交过程有什么不同？

将 IAP Power BI 视觉对象提交到市场的过程与提交免费 Power BI 视觉对象的过程相同。 可以使用[合作伙伴中心](/partner-center/)提交 Power BI 的视觉对象以供认证。


注册 Power BI 视觉对象后，导航到“产品设置”  选项卡，并选中“我的产品要求购买服务”复选框  。

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>提交 IAP Power BI 视觉对象之前应该做什么？

如果使用的是 IAP Power BI 视觉对象，请确保它符合[准则](guidelines-powerbi-visuals.md)。  

> [!NOTE]
> 具有增加的 IAP 功能的免费 Power BI 视觉对象必须保留以前提供的相同免费功能。 可以在旧版免费功能基础上添加可选的高级付费功能。 建议提交具有高级功能的 IAP Power BI 视觉对象作为新的 Power BI 视觉对象，而不是更新旧的免费 BI 视觉对象。

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>IAP Power BI 视觉对象是否需要取得认证？

[认证](power-bi-custom-visuals-certified.md)过程是可选的。 由开发人员自行决定是否认证他们的 IAP Power BI 视觉对象。

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>我的 IAP Power BI 视觉对象可获取认证吗？

可以，IAP Power BI 视觉对象获得 AppSource 团队批准后，你就可以提交 Power BI 视觉对象以供[认证](power-bi-custom-visuals-certified.md)了。

认证是一个可选流程，由你决定是否要认证 IAP 视觉对象。

## <a name="additional-questions"></a>其他问题

### <a name="how-to-get-support"></a>如何获取支持？

请随时联系 Power BI 视觉对象支持团队 (pbicvsupport@microsoft.com)，可咨询任何相关问题或提供反馈意见。  

## <a name="next-steps"></a>后续步骤

有关详细信息，请访问 [Power BI 视觉对象疑难解答](power-bi-custom-visuals-troubleshoot.md)。
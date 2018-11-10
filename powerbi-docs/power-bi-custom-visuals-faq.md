---
title: 有关 Power BI 自定义视觉对象的常见问题
description: 浏览有关 Power BI 自定义对象的常见问题和解答列表
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223067"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>有关 Power BI 自定义视觉对象的常见问题

## <a name="organizational-custom-visuals"></a>组织的自定义视觉对象

管理员如何管理组织的自定义视觉对象？

在管理门户中，在“组织的自定义视觉对象”选项卡下，管理员可以查看和[管理企业中的所有组织的自定义视觉对象](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals)：添加、禁用、启用和删除。
无需再通过电子邮件或共享文件夹共享这些视觉对象！ 一旦将视觉对象部署到组织的存储库，组织中的用户便可以轻松发现它们，并直接从 Power BI Desktop 或 Power BI 服务将组织的自定义视觉对象导入其报表。 可以从“我的组织”选项卡下的内置存储（在桌面和服务中）中找到组织的自定义视觉对象。一旦管理员上传新的组织的自定义视觉对像的版本，组织中的每个人都将获得同一更新的版本。 报表作者无需删除其报表中的视觉对象以获取这些视觉对象的新版本，因为使用这些视觉对象的所有报表都将被自动更新！ 更新机制类似于市场视觉对象。

如果管理员将自定义视觉对象从公共市场上传到组织存储，当供应商在公共市场更新视觉对象后，它是否会被自动更新？

不，不会有来自公共市场的任何自动更新。
更新组织的自定义视觉对象的版本是管理员的职责（若需要）。

是否有方法禁用组织的存储？

不，用户始终能够从 Power BI 桌面和服务中看到“我的组织”选项卡。 管理员可以从管理门户禁用或删除所有组织的自定义视觉对象，且组织存储为空。
  
如果管理员禁用管理门户中的自定义视觉对象（“租户”设置），用户是否仍具有组织的自定义视觉对象的访问权限？

是，如果管理员禁用管理门户上的自定义视觉对象，它不会影响组织存储。 某些组织禁用自定义视觉对象，且仅启用由 Power BI 管理员导入和上传到组织存储的手动选择的视觉对象。 在 Power BI Desktop 中不会强制禁用来自管理门户中的自定义视觉对象。 桌面用户仍然可以在其报表中添加和使用来自公共市场的自定义视觉对象。 但是，一旦这些公共自定义视觉对象被发布到 Power BI 服务，它们将停止呈现，并发出相应的错误。 在使用 Power BI 服务时，你将无法从公共市场中导入自定义视觉对象。 仅能导入来自组织存储中的视觉对象，因为将在 Power BI 服务中强制实施管理门户中的自定义视觉对象设置。

为什么组织存储和组织的自定义视觉对象可提供杰出的企业解决方案？

* 每个人都会获得相同的视觉对象版本，该版本由 Power BI 管理员控制。 一旦管理员更新管理员门户中的视觉对象的版本，组织中的所有用户都将自动获得更新的版本。

* 无需再通过电子邮件或共享文件夹共享视觉对象文件！ 在一个位置对登录的所有成员都可见。

* 与市场视觉对象类似，新版本的组织的自定义视觉对象将在所有报表中自动更新，具有安全性和可支持性。

* 组织中使用组织的自定义视觉对象的用户需要登录才能查看和使用组织的自定义视觉对象，这是组织的一个安全元素。

* 管理员可以控制在组织中可以使用哪些自定义视觉对象。

* 管理员可以从管理门户中启用/禁用用于测试的视觉对象。 提供更好的安全执行，因为将仅允许这些视觉对象供组织成员使用。

## <a name="certified-custom-visuals"></a>认证的自定义视觉对象

什么是认证的自定义视觉对象？

认证的自定义视觉对象是[市场](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中满足由 Power BI 团队[指定](power-bi-custom-visuals-certified.md)的代码要求和测试的视觉对象。  执行的测试旨在检查视觉对象未访问外部服务或资源，但是，Microsoft 不是第三方自定义视觉对象的作者，因此，我们建议客户直接联系作者，以验证此视觉对象的功能。

## <a name="next-steps"></a>后续步骤

有关疑难解答的信息，请访问 [Power BI 自定义视觉对象疑难解答](power-bi-custom-visuals-troubleshoot.md)。

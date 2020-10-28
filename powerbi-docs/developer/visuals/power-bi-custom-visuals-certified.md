---
title: 已认证的 Power BI 视觉对象
description: 提交自定义视觉对象以供认证的要求和过程，以及已认证 Power BI 视觉对象的列表。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 03/08/2020
ms.openlocfilehash: 8dd6a33ab19e692d9dc04138d53b04e8e49da2bf
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049168"
---
# <a name="get-a-power-bi-visual-certified"></a>获取 Power BI 视觉对象认证

已认证的 Power BI 视觉对象是 [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) 中满足 Microsoft Power BI 团队[代码要求](#certification-requirements)的视觉对象。 将对这些视觉对象进行测试，以验证它们是否无法访问外部服务或资源，以及是否遵循安全编码模式和指导原则。

Power BI 视觉对象一旦通过认证，将提供更多功能。 例如，可[导出到 PowerPoint](../../consumer/end-user-powerpoint.md)，或者，如果用户[订阅了报表页](../../consumer/end-user-subscribe.md)，则可在收到的电子邮件中的显示视觉对象。

认证过程是可选的。 未经认证的 Power BI 视觉对象不一定是不安全的 Power BI 视觉对象。 某些 Power BI 视觉对象未通过认证，因为它们不符合一项或多项[认证要求](power-bi-custom-visuals-certified.md#certification-requirements)。 例如，连接到外部服务的 Power BI 地图视觉对象，或使用商业库的 Power BI 视觉对象。

> [!NOTE]
> Microsoft 不是第三方 Power BI 视觉对象的作者。 若要验证第三方视觉对象的功能，请直接联系视觉对象的作者。

## <a name="certification-requirements"></a>认证要求

若要使 Power BI 视觉对象通过[认证](#get-a-power-bi-visual-certified)，Power BI 视觉对象必须符合本节中所列的要求。 

### <a name="general-requirements"></a>一般要求

Power BI 视觉对象必须由合作伙伴中心批准。 建议 Power BI 视觉对象已在 [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) 中。 若要了解如何将 Power BI 视觉对象发布到 AppSource，请参阅[将 Power BI 视觉对象发布到合作伙伴中心](office-store.md)。

提交 Power BI 视觉对象之前，请验证它是否符合 [Power BI 视觉对象的准则](guidelines-powerbi-visuals.md)。

提交 Power BI 视觉对象时，请确保已编译的包与提交的包完全匹配。

### <a name="code-repository-requirements"></a>代码存储库要求

尽管你无需在 GitHub 中公开共享代码，但代码存储库必须可供 Power BI 团队审阅。 实现此目的的最佳方式是在 GitHub 中提供源代码（JavaScript 或 TypeScript）。

存储库必须包含以下内容：
* 仅适用于一个 Power BI 视觉对象的代码。 它不能包含多个 Power BI 视觉对象的代码或不相关的代码。
* 名为 certification（需小写）的分支  。 此分支中的源代码必须与提交的包匹配。 如果正在重新提交 Power BI 视觉对象，则只能在下一次提交过程中更新此代码。

如果 Power BI 视觉对象使用私有 npm 包或 git 子模块，则必须提供对包含此代码的其他存储库的访问权限。

若要了解 Power BI 视觉对象存储库的外观，请查看 GitHub 存储库中的 [Power BI 视觉对象示例条形图](https://github.com/microsoft/PowerBI-visuals-sampleBarChart)。

### <a name="file-requirements"></a>文件要求

使用最新版本的 API 编写 Power BI 视觉对象。

存储库必须包含以下文件：
* **.gitignore** - 将 `node_modules`、`.tmp` 和 `dist` 添加到此文件。 代码不得包含 node_modules  、.tmp  或 dist  文件夹。
* **capabilities.json** - 如果你提交的是Power BI 视觉对象的较新版本，并对该文件中的属性进行了更改，请验证它们不会中断现有用户的报表。
* **pbiviz.json** 
* **package.json** ： 视觉对象必须已安装以下包：
   * ["tslint"](https://www.npmjs.com/package/tslint) - 版本 5.18.0 或更高版本
   * ["typescript"](https://www.npmjs.com/package/typescript) - 版本 3.0.0 或更高版本
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib) - 版本 6.2.0 或更高版本
   * 文件必须包含用于运行 Linter 的命令 - `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>命令要求

请确保以下命令不会返回任何错误。

* `npm install`
* `pbiviz package`
* `npm audit` - 不得返回任何具有高级别或中等级别的警告。
* [Microsoft 提供的 TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib)，包含[所需的配置](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json)。 此命令不得返回任何 Lint 错误。

### <a name="compiling-requirements"></a>编译要求

使用最新版本的 [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) 编写 Power BI 视觉对象。

必须用 `pbiviz package` 编译 Power BI 视觉对象。 如果你使用自己的生成脚本，请提供 `npm run package` 自定义生成命令。

### <a name="source-code-requirements"></a>源代码要求

验证是否遵循 [Power BI 视觉对象的其他认证](/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification)策略列表。 如果提交未遵循这些指导原则，则合作伙伴中心的拒绝电子邮件将包含此链接中列出的策略编号。

请遵循下面列出的代码要求，确保代码符合 Power BI 认证策略。  

**必需**
* 只能使用可供审核的公用 OSS 组件，例如公用 JavaScript 或 TypeScript 库。
* 代码必须支持[呈现事件 API](event-service.md)。
* 确保已安全操作 DOM。 在将用户输入或用户数据添加到 DOM 之前，对其使用清理。
* 将此[示例报表](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)用作测试数据集。

**不允许**
* 访问外部服务或资源。 例如，任何 HTTP/S 或 WebSocket 请求都不能从 Power BI 外部发送到任何服务。
* 使用 `innerHTML` 或 `D3.html(user data or user input)`。
* 浏览器控制台中的任何输入数据均没有 JavaScript 错误/异常。
* 任意或动态代码（如 `eval()`）、不安全使用 `settimeout()`、`requestAnimationFrame()`、`setinterval(user input function)` 及用户输入或用户数据。
* 缩小的 JavaScript 文件或项目。

## <a name="submitting-a-power-bi-visual-for-certification"></a>提交 Power BI 视觉对象用于认证

可以通过合作伙伴中心请求 Power BI 团队认证 Power BI 视觉对象。

>[!TIP]
>Power BI 认证过程可能需要一段时间。 如果要创建新的 Power BI 视觉对象，建议在请求 Power BI 认证之前，通过合作伙伴中心发布 Power BI 视觉对象。 这样可以确保不会延迟视觉对象的发布。

请求 Power BI 认证的步骤：

1. 登录到合作伙伴中心。
2. 在“概述”页  上，选择你的 Power BI 视觉对象，然后转到“产品”  设置页。
3. 选中“请求 Power BI 认证”  复选框。
4. 在“审阅并发布”  页的“认证说明”  文本框中，提供指向源代码的链接以及访问它所需的凭据。

### <a name="private-repository-submission-process"></a>专用存储库提交过程

如果使用的是诸如 GitHub 之类的专用存储库来提交 Power BI 视觉对象进行认证，请按照本节中的说明进行操作。
1. 为验证团队创建一个新帐户。
2. 为帐户配置[双因素身份验证](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa)。
3. [生成一组新的恢复代码](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes)。
4. 提交 Power BI 视觉对象时，请提供以下内容：
    * 存储库链接
    * 登录凭据（包括密码）
    * 恢复代码
    * 帐户的只读权限 ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visual-badges"></a>认证 Power BI 视觉对象徽章

通过认证后，Power BI 视觉对象会获得指定徽章，指明视觉对象已通过认证。

### <a name="certified-power-bi-visuals-in-appsource"></a>AppSource 中的认证 Power BI 视觉对象

* 在 [AppSource中联机搜索 Power BI 视觉对象](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)时，你会看到视觉对象的卡上有黄色小徽章，这指明它是认证 Power BI 视觉对象。

    ![AppSource 中的认证 Power BI 视觉对象](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* 单击 AppSource 中的 Power BI 视觉对象卡后，你会看到标题为“PBI 认证”  的黄色徽章，指明此 Power BI 视觉对象已通过认证。

    ![应用页中的认证 Power BI 视觉对象](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Power BI 接口中的认证 Power BI 视觉对象

* 从 Power BI（Desktop 或服务）中导入 Power BI 视觉对象时，你会看到蓝色徽章，指明此 Power BI 视觉对象已通过认证。

    ![Power BI 接口中的认证 Power BI 视觉对象](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* 可以通过选择“Power BI 认证”  筛选器选项，只显示认证 Power BI 视觉对象。

## <a name="publication-timeline"></a>发布时间线

部署到 AppSource 的过程可能需要一段时间。 完成此过程后，即可从 AppSource 下载 Power BI 视觉对象。

### <a name="when-will-users-be-able-to-download-my-visual"></a>用户何时才能下载我的视觉对象？

* 如果你是第一次提交 Power BI 视觉对象，则用户将能够在你收到来自 AppSource 的电子邮件后的几个小时内下载视觉对象。

* 如果你提交了现有 Power BI 视觉对象的更新，则用户将能够在你提交的这个月内下载该更新。

    >[!NOTE]
    > AppSource 中的“版本”字段将更新为 AppSource 批准 Power BI 的当天日期（大约在你提交视觉对象后的一周进行更新）  。 用户将能够下载更新后的视觉对象，但更新后的功能将不会生效。 视觉对象的新功能将在大约一个月后才会在用户报表中生效。 

### <a name="when-will-my-power-bi-visual-display-a-certification-badge"></a>我的 Power BI 视觉对象何时显示证书徽章？

* 如果你是第一次提交 Power BI 视觉对象，则证书徽章将在你收到来自 AppSource 的批准电子邮件的一天内显示。

* 如果你正在请求现有 Power BI 视觉对象的认证，则证书徽章将在你提交的月份内显示。

## <a name="next-steps"></a>后续步骤

* 如果 Web 开发人员有兴趣创建自己的 Power BI 视觉对象并将其添加到  [Microsoft AppSource](https://appsource.microsoft.com)，可从 [开发 Power BI 圆形卡片视觉对象](develop-circle-card.md)教程开始入手。

* 有关视觉对象的详细信息，请参阅[关于认证视觉对象的常见问题解答](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)。

* [YouTube 上的 Microsoft Power BI 视觉对象播放列表](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Power BI 中的视觉对象](power-bi-custom-visuals.md)

* [将 Power BI 视觉对象发布到 Microsoft AppSource](office-store.md)

* 更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
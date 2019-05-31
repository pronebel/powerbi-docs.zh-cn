---
title: 受信任的 Power BI 中的第三方连接器
description: 如何在 Power BI 中的已签名的第三方连接器信任
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607794"
---
# <a name="trusting-third-party-connectors"></a>信任第三方连接器

## <a name="why-do-you-need-trusted-third-party-connectors"></a>为什么需要受信任的第三方连接器？

在 Power BI 中，我们通常建议保持在较高级别，这会阻止不由 Microsoft 认证的代码加载在数据扩展插件安全级别。 但是，可能有很多情况下想要加载特定的连接器-你已编写，为一或顾问或 Microsoft 认证路径外部供应商向你提供的。

给定连接器的开发人员可以使用证书进行签名，并为您提供您需要安全地加载它，而不降低您的安全设置的信息。

如果你想要了解有关安全设置的详细信息，您可以阅读有关这些[此处](https://docs.microsoft.com/power-bi/desktop-connector-extensibility)。

## <a name="using-the-registry-to-trust-third-party-connectors"></a>使用注册表来信任第三方连接器

信任在 Power BI 中的第三方连接器是通过列出你想要信任指定的注册表值中的证书的指纹。 如果此指纹匹配的连接器上想要加载的证书指纹，您将能够将它加载到 Power BI 的推荐安全级别。 

注册表路径是 HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop。 请确保该路径存在，或创建它。 我们选择了由于其主要受控的 IT 策略，以及需要的本地计算机管理访问权限才能编辑此位置。 

![没有受信任的第三方键的 power BI Desktop 注册表设置](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

添加上面指定的路径下的新值。 类型应为"多字符串值"(REG_MULTI_SZ)，它应调用"TrustedCertificateThumbprints" 

![Power BI Desktop 注册表的受信任的第三方连接器，但没有键的条目](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

添加你想要信任的证书指纹。 您可以添加多个证书通过使用"\0"作为分隔符，或在注册表编辑器中，右键单击修改并将每个指纹置于新行上。 从自签名证书获取的示例指纹。 

 ![Power BI Desktop 注册表使用受信任的第三方密钥集](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

如果您已正确，按照说明进行操作，并已授予适当的指纹的开发人员，现在应能够安全地使用关联的证书签名的信任连接器。

## <a name="how-to-sign-connectors"></a>如何注册连接器

如果您还是需要登录开发人员有了连接器，你可以通过阅读文章了解一下 Power Query 文档[此处](https://docs.microsoft.com/power-query/handlingconnectorsigning)。

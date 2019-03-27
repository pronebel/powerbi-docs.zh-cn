---
title: 深入了解本地数据网关
description: 本文深入探讨了本地网关。 它探讨了该服务与 Analysis Services 配合使用时在 Azure Active Directory 和本地 Active Directory 中的运行方式
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: fa7d10403ca6bd8dc94729b7b4fd631475a3671e
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383407"
---
# <a name="on-premises-data-gateway-in-depth"></a>深入了解本地数据网关
组织中的用户可以访问本地数据（他们已经具有该数据的访问授权），但在这些用户可以连接到本地数据源之前，需要安装和配置本地数据网关。 该网关便于云中的用户与你的本地数据源相互进行快速安全的后台通信，然后返回到云。

安装和配置网关通常由管理员完成。 它可能要求具备本地服务器的专门知识，在某些情况下可能需要服务器管理员权限。

本文不提供有关如何安装和配置网关的分步指导。 为此，请务必参阅[本地数据网关](service-gateway-onprem.md)。 本文旨在让你深入了解网关的工作原理。 我们还将深入了解有关 Azure Active Directory 和 Analysis Services 中的用户名和安全性的详细信息，以及该云服务如何使用用户登录时所用的电子邮件地址、网关和 Active Directory 来安全地连接到你的本地数据并进行查询。

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>登录帐户
用户将使用工作或学校帐户登录。 这是你的组织帐户。 如果你注册了 Office 365 产品/服务，但没有提供实际的工作电子邮件，则可能类似于 nancy@contoso.onmicrosoft.com。 你在云服务中的帐户存储于 Azure Active Directory (AAD) 中的租户内。 在大多数情况下，你的 AAD 帐户的 UPN 将与电子邮件地址匹配。

## <a name="authentication-to-on-premises-data-sources"></a>向本地数据源进行身份验证
存储的凭据将用于从网关连接到本地数据源（Analysis Services 除外）。 无论是哪个用户，该网关都使用存储的凭据进行连接。

## <a name="authentication-to-a-live-analysis-services-data-source"></a>向实时 Analysis Services 数据源进行身份验证
每次用户与 Analysis Services 交互时，有效用户名将传递到网关，然后传递到你的本地 Analysis Services 服务器。 我们会将你用于登录云的用户主体名称 (UPN)（通常为电子邮件地址）作为有效用户传递到 Analysis Services。 UPN 将在连接属性 EffectiveUserName 中传递。 此电子邮件地址应与本地 Active Directory 域内定义的 UPN 匹配。 UPN 是 Active Directory 帐户的属性。 该 Windows 帐户还需位于 Analysis Services 角色中，以便能够访问服务器。 如果在 Active Directory 中找不到匹配项，则登录不会成功。

Analysis Services 还可以基于此帐户提供筛选。 筛选可能伴随基于角色的安全性或行级别安全性出现。

## <a name="role-based-security"></a>基于角色的安全性
模型提供了基于用户角色的安全性。 在 SQL Server Data Tools – Business Intelligence (SSDT-BI) 中创作期间，或在部署模型之后，通过使用 SQL Server Management Studio (SSMS) 为特定模型项目定义角色。 角色包含按 Windows 用户名或按 Windows 组的成员。 角色定义了用户进行查询或对模型执行操作所具有的权限。 大多数用户将属于具有读取权限的角色。 其他角色用于具有处理项目、管理数据库功能和管理其他角色的权限的管理员。

## <a name="row-level-security"></a>行级别安全性
行级别安全性特指 Analysis Services 行级别安全性。 模型可以提供动态的行级别安全性。 不像在用户所属的角色中至少具有一个角色，任何表格模型都不需要动态安全性。 在较高级别，动态安全定义了用户对数据以至特定表中的特定行的读取访问权限。 类似于角色，动态行级别安全性依赖于用户的 Windows 用户名。

用户是否能够查询和查看模型数据首先取决于 Windows 用户帐户所属的角色，其次取决于动态行级别安全性（如已配置）。

在模型中实现角色和动态行级别安全性已超出本文的讨论范围。  你可以在 MSDN 上的[角色（SSAS 表格）](https://msdn.microsoft.com/library/hh213165.aspx)和[安全角色（Analysis Services - 多维数据）](https://msdn.microsoft.com/library/ms174840.aspx)了解详细信息。 若要特别深入地了解表格模型的安全性，请下载并阅读[保护表格 BI 语义模型](https://msdn.microsoft.com/library/jj127437.aspx)白皮书。

## <a name="what-about-azure-active-directory"></a>Azure Active Directory 如何？
Microsoft 云服务使用 [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) 来处理对用户的身份验证。 Azure Active Directory 是包含用户名和安全组的租户。 通常情况下，用户登录时使用的电子邮件地址与帐户的 UPN 相同。

本地 Active Directory 的角色是什么？

为了使 Analysis Services 能够确定连接到它的用户是否属于具有数据读取权限的角色，服务器需要转换从 AAD 传递到网关，然后传递到 Analysis Services 服务器的有效用户名。 Analysis Services 服务器向 Windows Active Directory 域控制器 (DC) 传递有效用户名。 接着，Active Directory DC 在本地帐户上确认有效用户名是有效 UPN，并将该用户的 Windows 用户名返回到 Analysis Services 服务器。

不能在未加入域的 Analysis Services 服务器上使用 EffectiveUserName。 为避免发生登录错误，Analysis Services 服务器必须加入域。

## <a name="how-do-i-tell-what-my-upn-is"></a>如何辨别我的 UPN？
你可能不知道你的 UPN 是什么，而且你有可能不是域管理员。 你可以从工作站使用以下命令找出你的帐户的 UPN。

    whoami /upn

结果将类似于电子邮件地址，但是这是位于本地域帐户上的 UPN。 如果你将 Analysis Services 数据源用于实时连接，它必须与从网关传递到 EffectiveUserName 的用户名匹配。

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>映射 Analysis Services 数据源的用户名
Power BI 允许映射 Analysis Services 数据源的用户名。 你可以配置规则，以便将登录 Power BI 时使用的用户名映射到为 Analysis Services 连接上的 EffectiveUserName 传递的名称。 当 AAD 中的用户名与本地 Active Directory 中的 UPN 不匹配时，映射用户名功能是解决此问题的一种好方法。 例如，如果你的电子邮件地址是 nancy@contoso.onmicrsoft.com，你可以将其映射到 nancy@contoso.com，并且该值将被传递到网关。 你可以了解有关如何[映射用户名](service-gateway-enterprise-manage-ssas.md#map-user-names)的详细信息。

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>将本地 Active Directory 与 Azure Active Directory 同步
如果打算使用 Analysis Services 实时连接，本地 Active Directory 帐户就要与 Azure Active Directory 匹配。 因为帐户之间的 UPN 必须匹配。

云服务只知道 Azure Active Directory 中的帐户。 不管你是在本地 Active Directory 中添加了一个帐户，还是该帐户在 AAD 中不存在或者无法使用，都没有关系。 你可以通过多种不同的方式将本地 Active Directory 帐户与 Azure Active Directory 匹配。

1. 可以将帐户手动添加到 Azure Active Directory 中。
   
   可以在 Azure 门户或 Microsoft 365 管理中心中创建一个帐户，帐户名称与本地 Active Directory 帐户的 UPN 匹配。
2. 你可以使用 [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) 工具将本地帐户同步到 Azure Active Directory 租户。
   
   Azure AD Connect 工具提供有关目录同步和设置身份验证的选项，包括密码哈希同步、传递身份验证和联合身份验证。 如果你不是租户管理员或本地域管理员，则需要联系 IT 管理员对其进行配置。

使用 Azure AD Connect 可确保 AAD 与本地 Active Directory 之间的 UPN 匹配。

> [!NOTE]
> 使用 Azure AD Connect 工具同步帐户时，将在你的 AAD 租户内创建新帐户。
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>现在，这就网关起作用的地方
网关充当云和本地服务器之间的桥梁。 [Azure 服务总线](/azure/service-bus-messaging/service-bus-messaging-overview)可保护云和网关之间的数据传输。 服务总线通过网关上的出站连接在云和本地服务器之间创建一条安全通道。  你不需要在本地防火墙上打开任何入站连接。 Power BI 为你管理服务总线，因此无需额外成本或配置步骤。

如果有 Analysis Services 数据源，你需要在加入到与 Analysis Services 服务器位于同一个林/域的计算机上安装网关。

网关离服务器越近，连接速度就越快。 如果可以在数据源所在的同一服务器上获取网关，最好避免网关和服务器之间的网络延迟。

## <a name="what-to-do-next"></a>接下来该怎么做？
安装网关后，需要为该网关创建数据源。 可以在“**管理网关**”屏幕中添加数据源。 有关详细信息，请参阅与管理数据源相关的文章。

[管理数据源 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[管理数据源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[管理数据源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
[管理数据源 - Oracle](service-gateway-onprem-manage-oracle.md)  
[管理数据源 - 导入/计划刷新](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>这时事情可能会出错
有时，安装网关会失败。 或者，也许网关似乎已正常安装，但该服务仍无法使用它。 在许多情况下，是很简单的原因，如网关用于登录到数据源的凭据的密码。

在其他情况下，用户登录所使用的电子邮件地址的类型可能有问题或者 Analysis Services 不能解析有效用户名。 如果你的多个域彼此之间存在信任关系，并且网关在一个域，而 Analysis Services 在另一个域，这有时就会导致一些问题。

我们没有在这里详细讨论如何解决网关问题，而是将一系列疑难解答步骤放到另一篇文章中，即[本地数据网关疑难解答](service-gateway-onprem-tshoot.md)。 但愿不会有任何问题。 但如果出现问题，了解所有这些的工作原理和学习故障排除文章都应有所帮助。

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>后续步骤

[本地数据网关故障排除](service-gateway-onprem-tshoot.md)  
[Azure 服务总线](/azure/service-bus-messaging/service-bus-messaging-overview/)  
[Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis/)  

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


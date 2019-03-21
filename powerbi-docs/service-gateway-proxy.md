---
title: 为本地数据网关配置代理设置
description: 有关本地数据网关代理设置配置的信息。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2122ce9bd6eb850a51a06188ca1c10faf78f4bb1
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964654"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>为本地数据网关配置代理设置
你的工作环境可能要求你通过代理访问 Internet。 这会阻止本地数据网关连接到该服务。

## <a name="does-your-network-use-a-proxy"></a>你的网络是否使用代理？
superuser.com 上的以下文章讨论了尝试确定网络上有无代理的可行方法。

[如何确定我正在使用的代理服务器？(SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>配置文件位置和默认配置
在 .NET 配置文件中配置代理信息。 位置和文件名将因所用网关而异。

### <a name="on-premises-data-gateway"></a>本地数据网关
本地数据网关涉及两个主要配置文件。

**配置**

第一个用于实际配置网关的配置屏幕。 如果你在配置网关时遇到问题，可查看此文件。

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Windows 服务**

第二个用于与 Power BI 服务进行交互并处理请求的实际 Windows 服务。

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>配置代理设置
默认代理配置如下。

```
<system.net>
    <defaultProxy useDefaultCredentials="true" />
</system.net>
```


默认配置适用于 Windows 身份验证。 如果你的代理服务器使用另一种形式的身份验证，则你将需要更改设置。 如果你不确定，则应与你的网络管理员联系。 不建议执行基本代理身份验证，如果尝试执行，可能会导致代理身份验证错误出现，进而导致错误配置网关。 若要解决此问题，请使用更强大的代理身份验证机制。

除使用默认凭据外，还可以添加 <proxy> 元素以更详细地定义代理服务器设置。 例如，可以通过将 bypassonlocal 参数设为 false，指定本地数据网关应始终使用代理，即使对于本地资源也是如此。 如果想在代理日志文件中跟踪来自本地数据网关的所有 https 请求，这样做有助于进行故障排除。 下面的示例配置指定所有请求都必须通过 IP 地址为 192.168.1.10 的特定代理。

```
<system.net>
    <defaultProxy useDefaultCredentials="true">
        <proxy  
            autoDetect="false"  
            proxyaddress="http://192.168.1.10:3128"  
            bypassonlocal="false"  
            usesystemdefault="true"
        />  
    </defaultProxy>
</system.net>
```

此外，对于通过代理连接到云数据源的网关，请更新以下文件：C:\Program Files\On-premises data gateway\Microsoft.Mashup.Container.NetFX45.exe。 在文件中，展开“`<configurations>`”部分以包含以下内容，并使用自己的代理信息更新 `proxyaddress` 属性。 以下示例将通过 IP 地址为 192.168.1.10 的特定代理路由所有云请求。

```
<configuration>
<system.net>
    <defaultProxy useDefaultCredentials="true" enabled="true">
    <proxy proxyaddress=""http://192.168.1.10:3128" bypassonlocal="true" />
    </defaultProxy>
</system.net>
</configuration>
```

若要了解有关 .NET 配置文件代理元素配置的详细信息，请参阅 [defaultProxy 元素（网络设置）](https://msdn.microsoft.com/library/kd3cf2ex.aspx)。

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>将网关服务帐户更改为域用户
当配置代理设置以使用默认凭据时，如上文所述，你可能会遇到关于代理的身份验证问题。 这是因为默认服务帐户是服务 SID，而不是经过身份验证的域用户。 你可以更改网关的服务帐户，以允许对代理进行正确的身份验证。

> [!NOTE]
> 建议使用托管的服务帐户以避免重置密码。 了解如何通过 Active Directory 创建[托管服务帐户](https://technet.microsoft.com/library/dd548356.aspx)。
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>更改本地数据网关服务帐户
1. 更改“本地数据网关服务”的 Windows 服务帐户。

    此服务的默认帐户是 NT SERVICE\PBIEgwService。 你会想要在 Active Directory 域内将其更改为域用户帐户。 或者，你会想要使用托管服务帐户以避免更改密码。

    你会想要在 Windows 服务属性中的“登录”选项卡上更改帐户。
2. 重启“本地数据网关服务”。

    从管理员命令提示符中，发出以下命令。

        net stop PBIEgwService

        net start PBIEgwService
3. 启动“本地数据网关配置器”。 可选择 Windows“开始”按钮，然后搜索“本地数据网关”。
4. 登录到 Power BI。
5. 使用恢复密钥还原网关。

    这将使新的服务帐户能够解密存储的数据源凭据。

> [!NOTE]
> 如果直接使用服务控制面板更改服务帐户，它不会自动更新 ACL。 必须确保新服务帐户有权访问安装文件和文件夹。 “网关安装”文件夹位于 C:\Program Files\On-premises data gateway 下。 
> 

## <a name="next-steps"></a>后续步骤
[本地数据网关（个人模型）](service-gateway-personal-mode.md)
[防火墙信息](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)


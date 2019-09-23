---
title: 配置 Kerberos 以使用 Power BI 报表
description: 了解如何将报表服务器配置为对在分布式环境的 Power BI 报表中使用的数据源进行 Kerberos 身份验证。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.author: maggies
ms.openlocfilehash: 63bf5653ddf17097a44113324011951734f6d13c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770707"
---
# <a name="configure-kerberos-to-use-power-bi-reports"></a>配置 Kerberos 以使用 Power BI 报表
<iframe width="640" height="360" src="https://www.youtube.com/embed/vCH8Fa3OpQ0?showinfo=0" frameborder="0" allowfullscreen></iframe>

了解如何将报表服务器配置为对在分布式环境的 Power BI 报表中使用的数据源进行 Kerberos 身份验证。

Power BI 报表服务器提供 Power BI 报表托管功能。 报表服务器可支持许多数据源。 尽管本文着重介绍 SQL Server Analysis Services，但你可以使用这些概念并将其应用于 SQL Server 等其他数据源。

可以在一台计算机上安装 Power BI 报表服务器、SQL Server 和 Analysis Services，一切都应正常运转，而无需执行其他任何配置。 这非常适合测试环境。 如果在称为“分布式环境”的独立计算机上安装这些服务，可能会看到错误消息。 在此环境中，必须使用 Kerberos 身份验证。 必须通过执行其他配置来实现此解决方案。 

具体来说，需要配置约束委派。 可能已在环境中配置了 Kerberos，但并未配置 Kerberos 约束委派。

## <a name="error-running-report"></a>生成报表时出错
如果未正确配置报表服务器，可能会看到以下错误消息。

    Something went wrong.

    We couldn’t run the report because we couldn’t connect to its data source. The report or data source might not be configured correctly. 

“技术详细信息”中显示以下消息。

    We couldn’t connect to the Analysis Services server. The server forcibly closed the connection. To connect as the user viewing the report, your organization must have configured Kerberos constrained delegation.

![](media/configure-kerberos-powerbi-reports/powerbi-report-config-error.png)

## <a name="configuring-kerberos-constrained-delegation"></a>配置 Kerberos 约束委派
必须先配置多个项，然后 Kerberos 约束委派才能生效。 这包括服务帐户上的服务主体名称 (SPN) 和委派设置。

> [!NOTE]
> 必须是域管理员，才能配置 SPN 和委派设置。
> 
> 

我们需要配置或验证以下设置。

1. 报表服务器配置中的身份验证类型。
2. 报表服务器服务帐户的 SPN。
3. Analysis Services 服务的 SPN。
4. Analysis Services 计算机上 SQL Browser 服务的 SPN。 这仅适用于命名实例。
5. 报表服务器服务帐户上的委派设置。

## <a name="authentication-type-within-report-server-configuration"></a>报表服务器配置中的身份验证类型
我们需要将报表服务器的身份验证类型配置为允许 Kerberos 约束委派。 此操作在 rsreportserver.config  文件中完成。 此文件的默认位置是 `C:\Program Files\Microsoft Power BI Report Server\PBIRS\ReportServer`。

在 rsreportserver.config 文件中，需要微调“Authentication/AuthenticationTypes”  部分。

我们需要确保 RSWindowsNegotiate 被列为身份验证类型列表中的第一个类型。 它应类似于下面这样。

```xml
<AuthenticationTypes>
    <RSWindowsNegotiate/>
    <RSWindowsNTLM/>
</AuthenticationTypes>
```

如果不得不更改配置文件，需要停止并启动报表服务器，以确保更改生效。

有关详细信息，请参阅[在报表服务器上配置 Windows 身份验证](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server)。

## <a name="spns-for-the-report-server-service-account"></a>报表服务器服务帐户的 SPN
接下来，我们需要确保报表服务器包含有效的 SPN。 具体操作视所配置的报表服务器服务帐户而定。

### <a name="virtual-service-account-or-network-service"></a>虚拟服务帐户或网络服务帐户
如果将报表服务器配置为使用虚拟服务帐户或网络服务帐户，不应执行任何操作。 这是在计算机帐户的上下文中。 默认情况下，计算机帐户具有 HOST SPN。 这些会覆盖 HTTP 服务，并由报表服务器使用。

如果使用的是与计算机帐户不同的虚拟服务器名称，那么 HOST 条目将不会进行覆盖，你需要手动添加虚拟服务器主机名的 SPN。

### <a name="domain-user-account"></a>域用户帐户
如果将报表服务器配置为使用域用户帐户，则需要在相应帐户上手动创建 HTTP SPN。 为此，可以使用 Windows 随附的 setspn 工具完成。

> [!NOTE]
> 必须拥有域管理员权限，才能创建 SPN。
> 
> 

建议创建两个 SPN。 一个采用 NetBIOS 名称，另一个采用完全限定的域名 (FQDN)。 SPN 格式如下所示。

    <Service>/<Host>:<port>

Power BI 报表服务器将使用 HTTP 服务。 对于 HTTP SPN，不会列出端口。 此时，我们关注的服务是 HTTP。 SPN 的主机将是你在 URL 中使用的名称。 这通常是计算机名称。 如果支持负载均衡器，这可能是虚拟名称。

> [!NOTE]
> 可以通过查看在浏览器地址栏中输入的内容来验证 URL，也可以查看 Web 门户 URL 选项卡上的“报表服务器配置管理器”。
> 
> 

如果计算机名为 ContosoRS，SPN 将如下所示。

| SPN 类型 | SPN |
| --- | --- |
| 完全限定的域名 (FQDN) |HTTP/ContosoRS.contoso.com |
| NetBIOS |HTTP/ContosoRS |

### <a name="location-of-spn"></a>SPN 位置
那么，要将 SPN 置于何处呢？ 将 SPN 置于要对服务帐户使用的任意位置上。 如果使用的是虚拟服务帐户或网络服务帐户，此位置为计算机帐户。 尽管我们之前提到过，但还是要提一下，只需为虚拟 URL 执行此操作。 如果将报表服务器配置为使用域用户服务帐户，请将 SPN 置于相应的域用户帐户上。

例如，如果使用的是网络服务帐户，且计算机名为 ContosoRS，那么我们会将 SPN 置于 ContosoRS 上。

如果使用的是 RSService 的域用户帐户，那么我们会将 SPN 置于 RSService 上。

### <a name="using-setspn-to-add-the-spn"></a>使用 SetSPN 添加 SPN
我们可以使用 SetSPN 工具来添加 SPN。 继续以上面使用计算机帐户和域用户帐户的示例为例。

如果使用 contosoreports 的虚拟 URL，那么将 SPN（包括 FQDN 和 NetBIOS SPN）置于计算机帐户上的命令如下所示。

      Setspn -a HTTP/contosoreports.contoso.com ContosoRS
      Setspn -a HTTP/contosoreports ContosoRS

如果对 SPN 主机使用计算机名称，那么将 SPN（包括 FQDN 和 NetBIOS SPN）置于域用户帐户上的命令如下所示。

      Setspn -a HTTP/ContosoRS.contoso.com RSService
      Setspn -a HTTP/ContosoRS RSService

## <a name="spns-for-the-analysis-services-service"></a>Analysis Services 服务的 SPN
配置 Analysis Services 服务的 SPN 类似于配置 Power BI 报表服务器的 SPN。 如果有命名实例，那么 SPN 的格式就会略有不同。

对于 Analysis Services，我们使用 MSOLAPSvc.3 服务。 我们将为 SPN 上的端口位置指定实例名称。 SPN 的主机部分为计算机名称或群集虚拟名称。

Analysis Services SPN 示例如下所示。

| 类型 | 格式 |
| --- | --- |
| 默认实例 |MSOLAPSvc.3/ContosoAS.contoso.com<br>MSOLAPSvc.3/ContosoAS |
| 命名实例 |MSOLAPSvc.3/ContosoAS.contoso.com:INSTANCENAME<br>MSOLAPSvc.3/ContosoAS:INSTANCENAME |

SPN 的放置也类似于 Power BI 报表服务器 SPN 的放置。 具体操作视服务帐户而定。  如果使用的是本地系统或网络服务，那么这是在计算机帐户的上下文中。 如果对 Analysis Services 实例使用域用户帐户，请将 SPN 置于域用户帐户上。

### <a name="using-setspn-to-add-the-spn"></a>使用 SetSPN 添加 SPN
我们可以使用 SetSPN 工具来添加 SPN。 在此示例中，计算机名为 ContosoAS。

将 SPN（包括 FQDN 和 NetBIOS SPN）置于计算机帐户上的命令如下所示。

    Setspn -a MSOLAPSvc.3/ContosoAS.contoso.com ContosoAS
    Setspn -a MSOLAPSvc.3/ContosoAS ContosoAS

将 SPN（包括 FQDN 和 NetBIOS SPN）置于域用户帐户上的命令如下所示。

    Setspn -a MSOLAPSvc.3/ContosoAS.contoso.com OLAPService
    Setspn -a MSOLAPSvc.3/ContosoAS OLAPService

## <a name="spns-for-the-sql-browser-service"></a>SQL Browser 服务的 SPN
如果有 Analysis Services 命名实例，还需要确保有浏览器服务的 SPN。 这是 Analysis Services 的专属要求。

配置 SQL Browser 的 SPN 类似于配置 Power BI 报表服务器的 SPN。

对于 SQL Browser，我们使用 MSOLAPDisco.3 服务。 我们将为 SPN 上的端口位置指定实例名称。 SPN 的主机部分为计算机名称或群集虚拟名称。
不必为实例名称或端口指定任何内容。

Analysis Services SPN 示例如下所示。

    MSOLAPDisco.3/ContosoAS.contoso.com
    MSOLAPDisco.3/ContosoAS

SPN 的放置也类似于 Power BI 报表服务器 SPN 的放置。 不同之处在于，SQL Browser 始终在本地系统帐户下运行。 也就是说，SPN 始终都会在计算机帐户上运行。 

### <a name="using-setspn-to-add-the-spn"></a>使用 SetSPN 添加 SPN
我们可以使用 SetSPN 工具来添加 SPN。 在此示例中，计算机名为 ContosoAS。

将 SPN（包括 FQDN 和 NetBIOS SPN）置于计算机帐户上的命令如下所示。

    Setspn -a MSOLAPDisco.3/ContosoAS.contoso.com ContosoAS
    Setspn -a MSOLAPDisco.3/ContosoAS ContosoAS

有关详细信息，请参阅[必须有 SQL Server Browser 服务的 SPN](https://support.microsoft.com/kb/950599)。

## <a name="delegation-settings-on-the-report-server-service-account"></a>报表服务器服务帐户上的委派设置
我们需要配置的最后一个部分是报表服务器服务帐户上的委派设置。 可以使用不同的工具来执行这些步骤。 在本文档中，我们将继续使用 Active Directory 用户和计算机。

首先，需要转到 Active Directory 用户和计算机中的报表服务器服务帐户属性页面。 如果使用的是虚拟服务帐户或网络服务帐户，可以是计算机帐户；否则，可以是域用户帐户。

我们将要通过协议传输来配置约束委派。 使用约束委派时，需要明确要委派哪些服务。 我们将把 Analysis Services 服务 SPN 和 SQL Browser SPN 添加到 Power BI 报表服务器可以委派的列表中。

1. 右键单击报表服务器服务帐户，然后选择“属性”  。
2. 选择“**委派**”选项卡。
3. 选中“仅信任此计算机来委派指定的服务”  。
4. 选中“使用任意身份验证协议”  。
5. 在“可以由此帐户提供委派凭据的服务:”  下，选择“添加”  。
6. 在新对话框中，选择“用户或计算机”  。
7. 输入 Analysis Services 服务的服务帐户，然后选择“确定”  。
8. 选择已创建的 SPN。 它以 `MSOLAPSvc.3` 开头。 如果 FQDN 和 NetBIOS SPN 都添加了，两个都会被选中。 你可能只会看到其中一个。
9. 选择**确定**。  现在，列表中应该会显示 SPN。
10. 也可以选中“已扩展”  ，在列表中同时显示 FQDN 和 NetBIOS SPN。
11. 再次选择“添加”  。 现在，我们将添加 SQL Browser SPN。
12. 在新对话框中，选择“用户或计算机”  。
13. 输入 SQL Browser 服务所在计算机的名称，然后选择“确定”  。
14. 选择已创建的 SPN。 它以 `MSOLAPDisco.3` 开头。 如果 FQDN 和 NetBIOS SPN 都添加了，两个都会被选中。 你可能只会看到其中一个。
15. 选择“确定”  。 如果选中“已扩展”  ，对话框应如下所示。
    
    ![](media/configure-kerberos-powerbi-reports/powerbi-report-config-delegation.png)
16. 选择“确定”  。
17. 重启 Power BI 报表服务器。

## <a name="running-a-power-bi-report"></a>生成 Power BI 报表
指定完上述所有配置后，应该就可以正确显示报表了。 

![](media/configure-kerberos-powerbi-reports/powerbi-report.png)

虽然此配置在大多数情况下都适用于 Kerberos，但也可以指定不同的配置，具体视环境而定。 如果报表仍未加载，请与你的域管理员联系以展开进一步调查，或与支持人员联系。

## <a name="next-steps"></a>后续步骤
[管理员概述](admin-handbook-overview.md)  
[安装 Power BI 报表服务器](install-report-server.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


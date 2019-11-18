---
title: 对网关进行排除故障 - Power BI
description: 本文指导在遇到本地数据网关和 Power BI 问题时如何进行故障排查。 它提供了针对已知问题的可能方法，也提供了能够帮助你的工具。
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: troubleshooting
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: b420c827df3c18796d0d46514f81170f202eafbd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881574"
---
# <a name="troubleshoot-gateways---power-bi"></a>对网关进行排除故障 - Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

本文介绍将本地数据网关用于 Power BI 时的一些常见问题。 如果遇到此处未列出的问题，则可以使用 Power BI [社区](https://community.powerbi.com)站点。 也可以创建[支持票证](https://powerbi.microsoft.com/support)。

## <a name="configuration"></a>配置

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>错误：Power BI 服务报告本地网关无法访问。 请重启网关，然后重试。

配置结束时，将再次调用 Power BI 服务以验证网关。 Power BI 服务没有将网关报告为动态。 重启 Windows 服务可能会使通信成功。 若要获取携程信息，可以收集并查看日志，如[收集本地数据网关应用的日志](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)中所述。

## <a name="data-sources"></a>数据源

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>错误：无法连接。 详细信息:“连接凭据无效”

在“显示详细信息”中，显示从数据源收到的错误消息  。 对于 SQL Server，可看到如下所示的内容：

    Login failed for user 'username'.

验证你具有正确的用户名和密码。 另外，验证这些凭据是否可以成功地连接到数据源。 请确保所使用的帐户与身份验证方法匹配。

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>错误：无法连接。 详细信息:“无法连接到数据库”

可以连接到服务器，但不能连接所提供的数据库。 验证该数据库的名称以及该用户凭据有适当的权限来访问该数据库。

在“显示详细信息”中，显示从数据源收到的错误消息  。 对于 SQL Server，可看到如下所示的内容：

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>错误：无法连接。 详细信息:“数据网关中发生未知错误”

此错误可能会由于不同的原因发生。 请务必验证你可以从承载网关的计算机连接到数据源。 此情况可能是不可访问的服务器的结果。

在“显示详细信息”中，可以看到错误代码 DM_GWPipeline_UnknownError   。

还可以查看“事件日志”   > “应用程序和服务日志”   > “本地数据网关服务”  ，了解详细信息。

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>错误：我们在尝试连接到\<服务器\>时遇到错误。 详细信息:“我们已连接到数据网关，但网关无法访问本地数据源。”

无法连接到指定数据源。 请务必验证为该数据源所提供的信息。

在“显示详细信息”中，可以看到错误代码 DM_GWPipeline_Gateway_DataSourceAccessError   。

如果基础错误消息类似于以下内容，这意味着你正在对数据源使用的帐户不是该 Analysis Services 实例的服务器管理员。 有关详细信息，请参阅[授予对 Analysis Services 实例的服务器管理员权限](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance)。

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

如果基础错误消息类似以下消息，则可能意味着 Analysis Services 的服务帐户可能缺少 [token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx) (TGGAU) 目录属性。

    The username or password is incorrect.

具有 Windows 2000 以前版本兼容访问权限的域启用了 TGGAU 属性。 最新创建的域不会默认启用此属性。 有关详细信息，请参阅[某些应用程序和 API 需要访问帐户对象的授权信息](https://support.microsoft.com/kb/331951)。

若要确认是否已启用该属性，请执行以下步骤。

1. 连接 SQL Server Management Studio 中的 Analysis Services 计算机。 在高级连接属性中，输入问题用户的 EffectiveUserName，并检查此添加是否会产生错误。
2. 可以使用 dsacls Active Directory 工具来验证是否列出了属性。 此工具可在域控制器上找到。 你需要知道帐户的可分辨域名是什么，并将该名称传递给该工具。

        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"

    你应该在结果中看到与以下类似的内容：

            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

若要更正此问题，必须启用用于 Analysis Services Windows 服务的帐户上的 TGGAU。

#### <a name="another-possibility-for-the-username-or-password-is-incorrect"></a>“用户名或密码错误”的另一种可能。

如果 Analysis Services 服务器与用户位于不同的域，并且没有建立双向信任，则也可能导致此错误。

可与域管理员合作来验证域间的信任关系。

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>在 Power BI 服务中使用 Analysis Services 的“获取数据”功能时，无法查看数据网关数据源

确保你的帐户列于网关配置中数据源的**用户**选项卡。 如果你没有权限访问网关，请与网关管理员核对，并请他们进行验证。 仅用户列表中的帐户可查看列于 Analysis Services 列表中的数据源  。

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>错误：没有为此数据集中的数据源安装或配置任何网关。

请确保已按[添加数据源](service-gateway-data-sources.md#add-a-data-source)中所述，向网关添加一个或多个数据源。 如果“管理网关”下的管理门户中未显示网关，请清除浏览器缓存或注销服务，然后重新登录  。

## <a name="datasets"></a>数据集

### <a name="error-there-is-not-enough-space-for-this-row"></a>错误：对于此行没有足够的空间。

如果单行大于 4 MB，则会出现此错误。 从数据源确定该行，并尝试将其筛除或减少该行的大小。

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>错误：提供的服务器名称与 SQL Server SSL 证书上的服务器名称不一致。

如果证书公用名称针对的是服务器完全限定的域名 (FQDN)，而你只提供了服务器 NetBIOS 名称，则会出现此错误。 此情况会导致证书不匹配。 若要解决此问题，请将网关数据源和 PBIX 文件内的服务器名称设置为使用服务器的 FQDN。

### <a name="error-you-dont-see-the-on-premises-data-gateway-present-when-you-configure-scheduled-refresh"></a>错误：在配置计划刷新时看不到本地数据网关。

有几种不同的情况可能会导致此错误：

- 在 Power BI Desktop 中输入的服务器和数据库名称与为网关配置的数据源中的名称不一致。 这些名称必须相同。 它们不区分大小写。
- 网关配置中数据源的“用户”  选项卡上未列出你的帐户。 需要由网关的管理员将你添加到该列表。
- Power BI Desktop 文件中有多个数据源，并不是所有这些数据源都配置为网关数据源。 需要定义每个网关数据源，这样相应网关才能在计划刷新内显示。

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>错误：网关客户端上收到的未压缩数据已超出限制。

每个表的未压缩数据量的确切限制为 10GB。 如果遇到此问题，可以使用实用选项来优化和避免它发生。 具体而言，减少使用高度恒定的长字符串值，而是改用规范化键。 或者，如果未使用列，则删除它会有所帮助。

## <a name="reports"></a>报表

### <a name="error-report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>错误：报表无法访问数据源，因为你无权通过本地数据网关访问我们的数据源。

此错误通常是由于以下原因之一导致的：

- 数据源信息与基础数据集中的内容不匹配。 为本地数据网关定义的数据源和为 Power BI Desktop 提供的内容之间的服务器和数据库名称需要匹配。 如果在 Power BI Desktop 中使用 IP 地址，则用于本地数据网关的数据源也需要使用 IP 地址。
- 贵组织内的任何网关上均没有可用的数据源。 可以在新的或现有的本地数据网关上配置数据源。

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>错误：数据源访问错误。 请联系网关管理员。

如果此报表使用实时 Analysis Services 连接，你可能遇到的问题是值被传入无效或无权访问 Analysis Services 计算机的 EffectiveUserName 中。 通常来说，出现身份验证问题是由于传给 EffectiveUserName 的值与本地用户主体名称 (UPN) 不匹配。

若要确认有效用户名，请按照以下步骤操作。

1. 在[网关日志](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)中查找有效的用户名。
2. 传递值之后，验证其是否正确。 如果它是你的用户，可以从命令提示符下使用以下命令查看 UPN。 UPN 外观类似电子邮件地址。

        whoami /upn

或者，你可以查看 Power BI 从 Azure Active Directory 获取的内容。

1. 浏览到 [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer)。
2. 在右上角选择“登录”  。
3. 运行以下查询。 你将看到相当大的 JSON 响应。

        https://graph.windows.net/me?api-version=1.5
4. 查找 **userPrincipalName**。

如果你的 Azure Active Directory UPN 与本地 Active Directory UPN 不匹配，则可以使用[映射用户名](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources)功能将其替换为有效的值。 或者，可以通过租户管理员或本地 Active Directory 管理员更改 UPN。

## <a name="kerberos"></a>Kerberos

如果没有针对 [Kerberos 约束委派](service-gateway-sso-kerberos.md)基础数据库服务器和本地数据网关，请在网关上启用[详细日志记录](/data-integration/gateway/service-gateway-performance#slow-performing-queries)。 然后，将网关日志文件中的错误或跟踪作为故障排除起点，基于此信息进行调查。 若要收集网关日志以供查看，请参阅[收集本地数据网关应用的日志](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)。

### <a name="impersonationlevel"></a>ImpersonationLevel

ImpersonationLevel 与 SPN 设置或本地策略设置相关。

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**解决方案**

请按照下列步骤操作，解决该问题。

1. 为本地网关设置 SPN。
2. 在 Active Directory 中设置约束委派。

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException:未能为用户 userid 创建 Windows 标识

如果无法代表其他用户进行模拟，将出现 FailedToImpersonateUserException。 如果尝试模拟的帐户来自另一个域，而不是网关服务域所在的域，也可能会发生此错误。 这是一个限制。

**解决方案**

* 按照上面“ImpersonationLevel”部分中的步骤操作，验证配置是否正确。
* 请确保它尝试模拟的用户 ID 是一个有效的 Active Directory 帐户。

### <a name="general-error-1033-error-while-you-parse-the-protocol"></a>常规错误：分析协议时出现 1033 错误

如果使用 UPN (alias@domain.com) 模拟用户，那么在 SAP HANA 中配置的外部 ID 与登录名不匹配时，就会收到 1033 错误。 在日志中，可看到“原始 UPN 'alias@domain.com 在错误日志顶部替换为新 UPN 'alias@domain.com'”，如下所示：

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**解决方案**

* SAP HANA 要求模拟的用户在 Active Directory 中使用 sAMAccountName 属性（用户别名）。 如果此属性不正确，将看到 1033 错误。

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount.png)

* 可在日志中看到 sAMAccountName（别名）而不是 UPN，它是后跟域的别名 (alias@doimain.com)。

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] 通讯链接失败:-10709 连接失败 (RTE:[-1] Kerberos 错误。 主要:“其他故障 [851968]。” 次要：“安全包中没有可用的凭据。”

如果未在 Active Directory 中正确配置委派，将收到“-10709 连接失败”错误消息。

**解决方案**

* 确保在网关服务帐户 Active Directory 中的委派选项卡上拥有 SAP Hana 服务器。

   ![“委派”选项卡](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="refresh-history"></a>刷新历史记录

将网关用于计划刷新时，“刷新历史记录”  可以帮助查看发生的错误。 如果需要创建支持请求，则它也可以提供有用数据。 可以查看计划刷新和按需刷新。 以下步骤介绍如何访问刷新历史记录。

1. 在 Power BI 导航窗格的“数据集”中，选择一个数据集  。 打开菜单，然后选择“计划刷新”  。

    ![如何选择“计划刷新”](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. 在**设置...** &gt;“计划刷新”  中，选择“刷新历史记录”  。

    ![选择刷新历史记录](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![刷新历史记录显示](media/service-gateway-onprem-tshoot/refresh-history.png)

有关对刷新方案进行故障排除的详细信息，请参阅[刷新方案故障排除](refresh-troubleshooting-refresh-scenarios.md)。

## <a name="fiddler-trace"></a>Fiddler 跟踪

[Fiddler](https://www.telerik.com/fiddler) 是 Telerik 提供的一款用于监视 HTTP 流量的免费工具。 可以从客户端计算机通过 Power BI 服务来回查看。 此流量列表可能会显示错误和其他相关信息。

![使用 Fiddler 跟踪](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>后续步骤

* [本地数据网关故障排除](/data-integration/gateway/service-gateway-tshoot)
* [为本地数据网关配置代理设置](/data-integration/gateway/service-gateway-proxy)  
* [管理数据源 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [管理数据源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [管理数据源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [管理数据源 - 导入/计划刷新](service-gateway-enterprise-manage-scheduled-refresh.md)  

更多问题？ 尝试参与 [Power BI 社区](https://community.powerbi.com/)。

---
title: 使用 Web 应用程序代理和 Active Directory 联合身份验证服务 - Power BI 报表服务器
description: 了解如何使用 Web 应用程序代理 (WAP) 和 Active Directory 联合身份验证服务 (AD FS) 连接到 Power BI 报表服务器和 SQL Server Reporting Services (SSRS) 2016 及更高版本。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 2caa96aceef90ad1d25a521cbf4a3f699a2a64e0
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2020
ms.locfileid: "76042431"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>使用 Web 应用程序代理和 Active Directory 联合身份验证服务 - Power BI 报表服务器

本文介绍如何使用 Web 应用程序代理 (WAP) 和 Active Directory 联合身份验证服务 (AD FS) 连接到 Power BI 报表服务器和 SQL Server Reporting Services (SSRS) 2016 及更高版本。 通过这种集成，远离企业网络的用户可以从其客户端浏览器访问 Power BI 报表服务器和 Reporting Services 报表，并通过 AD FS 预身份验证进行保护。 对于 Power BI 移动应用，还需要[配置 OAuth 以连接到 Power BI 报表服务器和 SSRS](../consumer/mobile/mobile-oauth-ssrs.md)。

## <a name="prerequisites"></a>先决条件

### <a name="domain-name-services-dns-configuration"></a>域名服务 (DNS) 配置

- 确定用户将连接到的公共 URL。 它可能类似于下面的示例：`https://reports.contosolab.com`。
- 为主机名配置 DNS（如 `reports.contosolab.com`），以指向 Web 应用程序代理 (WAP) 服务器的公共 IP 地址。
- 为 AD FS 服务器配置公用 DNS 记录。 例如，可能为 AD FS 服务器配置了以下 URL：`https://adfs.contosolab.com`。
- 配置 DNS 记录以指向 Web 应用程序代理 (WAP) 服务器的公共 IP 地址，例如 `adfs.contosolab.com`。 它作为 WAP 应用程序的一部分发布。

### <a name="certificates"></a>证书

需要为 WAP 应用程序和 AD FS 服务器配置证书。 这些证书都必须是计算机可以识别的有效证书颁发机构的一部分。

## <a name="1-configure-the-report-server"></a>1.配置报表服务器

我们需要确保具有有效的服务主体名称 (SPN)。 有效 SPN 支持正确的 Kerberos 身份验证，并支持报告服务器进行协商身份验证。

### <a name="service-principal-name-spn"></a>服务主体名称 (SPN)

SPN 是使用 Kerberos 身份验证的服务的唯一标识符。 确保报表服务器存在正确的 HTTP SPN。

有关如何为报表服务器配置正确的服务主体名称 (SPN) 的信息，请参阅[为报表服务器注册服务主体名称 (SPN)](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server)。

### <a name="enabling-negotiate-authentication"></a>启用协商身份验证

若要使报表服务器可以使用 Kerberos 身份验证，需要将报表服务器的身份验证类型配置为 RSWindowsNegotiate。 可在 rsreportserver.config 文件中进行配置。

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

有关详细信息，请参阅[修改 Reporting Services 配置文件](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config)和[在报表服务器上配置 Windows 身份验证](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server)。

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2.配置 Active Directory 联合身份验证服务 (AD FS)

需要在环境中的 Windows 2016 服务器上配置 AD FS。 可通过服务器管理器并在“管理”下选择“添加角色和功能”完成配置。 有关详细信息，请参阅 [Active Directory 联合身份验证服务](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services)。

在 AD FS 服务器上，使用 AD FS 管理应用程序，完成以下步骤。

1. 右键单击“信赖方信任”   > “添加信赖方信任”  。

    ![添加信赖方信任](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. 按照“添加信赖方信任”  向导中的步骤操作。

    选择“非声明感知”  选项以使用 Windows 集成安全性作为身份验证机制。

    ![欢迎使用“添加信赖方信任”向导](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    在“指定显示名称”  中输入你喜欢的名称，然后选择“下一步”  。
    添加信赖方信任标识符：`<ADFS\_URL>/adfs/services/trust`

    例如：`https://adfs.contosolab.com/adfs/services/trust`

    ![报表服务器](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    选择符合组织需求的“访问控制策略”  ，并选择“下一步”  。

    ![选择访问控制](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    选择“下一步”  ，然后选择“完成”  以完成“添加信赖方信任”  向导。

    完成后，信赖方信任的属性应如下所示。

    ![信赖方信任](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3.配置 Web 应用程序代理 (WAP)

需要在环境中的服务器上启用 Web 应用程序代理（角色）Windows 角色。 必须在 Windows 2016 服务器上执行此过程。 有关详细信息，请参阅 [Windows Server 2016 中的 Web 应用程序代理](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server)及[发布使用 AD FS 预身份验证的应用程序](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication)。

### <a name="configure-constrained-delegation"></a>配置约束委派

若要从 Forms 身份验证转换到 Windows 身份验证，需要结合使用约束委派和协议转换。 此步骤是 Kerberos 配置的一部分。 我们已在报表服务器配置中定义报表服务器 SPN。

我们需要在 Active Directory 内的 WAP 服务器计算机帐户上配置约束委派。 如果不具备访问 Active Directory 的权限，则需要与域管理员合作。

若要配置约束委派，请执行以下步骤。

1. 在已安装 Active Directory 工具的计算机上，启动“**Active Directory 用户和计算机**”。
2. 找到 WAP 服务器的计算机帐户。 默认情况下，它会位于“计算机”  容器中。
3. 右键单击 WAP 服务器并转到“属性”  。
4. 在“委派”  选项卡上，选择“仅信任此计算机来委派指定的服务”  ，然后选择“使用任意身份验证协议”  。

    ![信任此计算机](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. 该选项设置了此 WAP 服务器计算机帐户的约束委派。 然后我们需要指定允许该计算机委派到的服务。
2. 在”服务”框下选择“添加”  。

    ![AD FS 添加信任](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. 选择“用户或计算机”  。
2. 输入用于报表服务器的服务帐户。 此帐户与你在前面[报表服务器配置](#1-configure-the-report-server)部分中用于添加 HTTP SPN 的帐户相同。 

3. 为报表服务器选择 HTTP SPN，然后选择“确定”  。

    > [!NOTE]
    > 你可能只能看到 NetBIOS SPN。 如果同时存在 NetBIOS 和 FQDN SPN，实际上会同时选中这两个。

1. 选中“已展开”  复选框时，结果应类似于下面的示例。

    ![WAP 属性](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>添加 WAP 应用程序

1. 在 Web 应用程序代理服务器上，打开“远程访问管理”  控制台，然后在“导航”窗格中选择“Web 应用程序代理”  。 

2. 在“任务”  窗格中，选择“发布”  。

2. 在“欢迎”页上，选择“下一步”  。

    ![欢迎使用发布](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. 在“预身份验证”  页上，选择“Active Directory 联合身份验证服务(AD FS)”  ，然后选择”下一步”  。

    ![预身份验证](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. 选择“Web 和 MSOFBA”  预身份验证，因为我们将仅为报表服务器设置浏览器访问，而不设置移动应用访问。

    ![支持的客户端](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. 添加在 AD FS 服务器中创建的“信赖方”  （如下所示），然后选择“下一步”  。

    ![信赖方发布](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. 在“外部 URL”  部分，放入在 WAP 服务器上配置的可公开访问的 URL。 添加使用报表服务器配置的 URL（报表服务器配置管理器），如下面的“后端服务器 URL”  部分所示。 在“后端服务器 SPN”  部分中添加报表服务器的 SPN。

    ![发布设置](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. 选择“下一步”  和“发布”  。
8. 运行以下 PowerShell 命令来验证 WAP 配置。

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![PowerShell 命令](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>通过浏览器连接到报表服务器

然后可以从浏览器访问公共 WAP URL，例如 Web 服务的 `https://reports.contosolab.com/ReportServer` 和 Web 门户的 `https://reports.contosolab.com/Reports`。 成功通过身份验证后，即可查看报表。

![AD FS 登录](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>后续步骤

* [配置 OAuth 以连接到 Power BI 报表服务器和 SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[什么是 Power BI 报表服务器？](get-started.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


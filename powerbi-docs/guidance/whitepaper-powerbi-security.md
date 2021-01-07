---
title: Power BI 安全性白皮书
description: 白皮书讨论并描述了 Power BI 的安全性体系结构和实现
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 05/14/2020
LocalizationGroup: Conceptual
ms.openlocfilehash: 806869b10b52ff7c161484f3e8d38fbc61b85f60
ms.sourcegitcommit: c700e78dfedc34f5a74b23bbefdaef77e2a87f8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2021
ms.locfileid: "97961261"
---
# <a name="power-bi-security-whitepaper"></a>Power BI 安全性白皮书

**摘要：** Power BI 是 Microsoft 提供的一项在线软件服务 (*SaaS* 或软件即服务) 提供的服务，可让你轻松快速地创建自助服务商业智能仪表板、报表、数据集和可视化效果。 使用 Power BI，可以连接到多个不同的数据源，合并并调整来自这些连接的数据，然后创建可与其他人共享的报表和仪表板。

**编写器：** David Iseminger

**技术审阅者：** Pedram Rezaei、Cristian Petculescu、Siva Harinath、Tod Manning、Haydn Richardson、Adam Wilson、Ben Childs、Robert Bruckner、Sergei Gundorov、Kasper de Jonge

**适用于：** Power BI SaaS、Power BI Desktop、Power BI Embedded Power BI Premium

> [!NOTE]
> 可以通过在浏览器中选择 " **打印** "，然后选择 " **另存为 PDF**" 来保存或打印此白皮书。

## <a name="introduction"></a>简介

Power BI 是 Microsoft 提供的在线软件服务（SaaS 或软件即服务），你可以通过它轻松快速地创建自助式商业智能仪表板、报表、数据集和可视化。 使用 Power BI，可以连接到多个不同的数据源，合并并调整来自这些连接的数据，然后创建可与其他人共享的报表和仪表板。

Power BI 服务受 [Microsoft Online Services 条款](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31)和 [Microsoft Enterprise Privacy 声明](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx)约束。 有关数据处理的位置，参阅 Microsoft Online Services 条款中的数据处理条款位置。 有关符合性信息，[Microsoft 信任中心](https://www.microsoft.com/trust-center/product-overview)提供了适用于 Power BI 的大量资源。 Power BI 团队正在努力为客户提供最新创新和提高生产效率。 Power BI 当前在 Microsoft 365 相容性框架的第 D 层中。 在 [Microsoft 信任中心](https://docs.microsoft.com/compliance/regulatory/offering-home)了解有关符合性的详细信息。

本文通过以下方式介绍了 Power BI 的安全性：首先说明 Power BI 的体系结构，然后说明用户如何对 Power BI 进行身份验证以及如何建立数据连接，最后描述 Power BI 如何通过服务存储和移动数据。 最后一部分专门讨论与安全相关的问题，并附上了每个问题的答案。

## <a name="power-bi-architecture"></a>Power BI 体系结构

Power BI 服务基于 Azure 构建，后者是 Microsoft 的[云计算平台](https://azure.microsoft.com/overview/what-is-azure/)。 Power BI 目前部署在世界各地的多个数据中心 – 在这些数据中心提供服务的区域，向客户提供了许多主动部署，以及相同数量的被动部署，被动部署用作每个主动部署的备份。

每个 Power BI 部署均包含两个群集 - Web 前端 (WFE) 群集和后端群集 。 这两个群集如下图所示，为本文其余部分提供了背景知识。 

![WFE 和后端](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

Power BI 使用 Azure Active Directory (AAD) 进行帐户身份验证和管理。 Power BI 还使用 **Azure 流量管理器 (ATM)** 将用户流量定向到最近的数据中心，由尝试连接的客户端的 DNS 记录确定，用于身份验证过程和下载静态内容和文件。 Power BI 使用地理位置最接近的 WFE 来有效地将所需的静态内容和文件分发给用户，但使用 **Azure 内容交付网络 (CDN)** 传递的 Power BI 视觉对象除外。

### <a name="the-wfe-cluster"></a>WFE 群集

**WFE** 群集为 Power BI 管理初始连接和身份验证进程，使用 AAD 对客户端进行身份验证并为后续客户端连接到 Power BI 服务提供令牌。

![WEF 群集](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

用户尝试连接到 Power BI 服务时，客户端的 DNS 服务可以与 Azure 流量管理器通信，以查找具有 Power BI 部署的最近的数据中心。 有关此过程的详细信息，请参阅 [Azure 流量管理器的性能流量路由方法](/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method)。

离用户最近的 WFE 群集管理登录和身份验证序列（本文稍后将介绍），并在身份验证成功后为用户提供 AAD 令牌。 WFE 群集中的 ASP.NET 组件分析请求以确定用户所属的组织，然后咨询 Power BI 全局服务。 全局服务是在所有全球 WFE 和后端群集中共享的一个 Azure 表，它将用户和客户组织映射到容纳其 Power BI 租户的数据中心。 WFE 向浏览器指定容纳组织租户的后端群集。 用户进行身份验证后，将直接与后端群集进行后续客户端交互，而不会将 WFE 作为这些请求的中介。

### <a name="the-power-bi-back-end-cluster"></a>Power BI 后端群集

**后端** 群集是指经身份验证的客户端如何与 Power BI 服务进行交互。 **后端** 群集管理可视化、用户仪表板、数据集、报表、数据存储、数据连接、数据刷新以及与 Power BI 服务进行交互的其他方面。

![后端群集](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

**网关角色** 充当用户请求与 Power BI 服务之间的网关。 用户并不直接与网关角色以外的任何角色进行交互。

**重要提示：** 需要注意的是， _只能_ 通过公共 Internet 访问 Azure API 管理 (**APIM**) 和网关 (**GW**) 角色。 它们提供身份验证、授权、DDoS 保护、限制、负载平衡、路由和其他功能。

上方后端群集映像中的虚线阐明了仅用户可访问的两个角色（左边的虚线）与仅系统可访问的角色之间的边界。 经身份验证的用户连接到 Power BI 服务时，该连接和客户端的任何请求均由网关角色和 Azure API 管理接受和管理，它会以用户的名义与 Power BI 服务的其余部分进行交互。 例如，当客户端尝试查看仪表板时，**网关角色** 接受该请求，然后分别发送请求到 **演示文稿角色** 来检索浏览器呈现仪表板时所需的数据。

![网关角色](media/whitepaper-powerbi-security/powerbi-security-whitepaper_04.png)

### <a name="power-bi-premium"></a>Power BI Premium

Power BI Premium 为需要专用资源进行 Power BI 活动的订阅者提供专用、预配和分区的服务工作区。 客户注册 Power BI Premium 订阅时，将通过 Azure 资源管理器创建高级容量。 在推出该订阅的同时将在托管 Power BI 租户的数据中心分配一组与订阅级别相称的虚拟机（multi-geo 环境例外，本文档稍后将进行介绍），它们将随 Azure Service Fabric 部署启动。

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

创建后，与 Premium 群集的所有通信都将通过 Power BI 后端群集进行路由，在该群集中建立了与客户端的专用 Power BI Premium 订阅虚拟机的连接。

### <a name="data-storage-architecture"></a>数据存储体系结构

Power BI 使用两个主要的存储库进行数据存储和管理：用户上传的数据通常发送到 Azure Blob 存储，并且系统本身的所有元数据以及项目均存储在 Azure SQL 数据库中的防火墙后面。

![数据存储](media/whitepaper-powerbi-security/powerbi-security-whitepaper_06.png)

例如，用户将 Excel 工作簿导入 Power BI 服务时，系统将创建内存中的 Analysis Services 表格数据库，并将数据存储在内存中长达一个小时（或直到系统出现内存压力）。 该数据也会发送到 Azure Blob 存储。

Azure SQL 数据库中存储和更新了用户的 Power BI 订阅相关的元数据，例如仪表板、报表、最新数据源、工作区、组织信息、租户信息以及有关系统的其他元数据。 存储在 Azure SQL 数据库中的所有信息都使用 [Azure SQL 透明数据加密](/azure/sql-database/transparent-data-encryption-azure-sql) (TDE) 方法进行了完全加密。 存储在 Azure Blob 存储中的所有数据也都已加密。 有关数据的加载、存储和移动过程的详细信息，请参阅“数据存储和移动”部分。

## <a name="tenant-creation"></a>创建租户

租户是组织在注册 Azure、Microsoft Intune、Power BI 或 Microsoft 365 等 Microsoft 云服务时接收并拥有的 Azure AD 服务的专用实例。 每个 Azure AD 租户都是独特的，独立于其他 Azure AD 租户。

租户包含公司中的用户以及有关这些用户的信息 - 他们的密码、用户配置文件数据、权限，等等。 它还包含与某家组织及其安全性相关的组、应用程序和其他信息。 有关详细信息，请参阅 [什么是 Azure AD 租户](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings)。

在最接近国家/地区 (或区域) 的数据中心创建 Power BI 租户，Azure Active Directory 在 Microsoft 365 或 Power BI 服务最初预配时提供的和状态信息。 当前，Power BI 租户不会从该数据中心位置移动。

### <a name="multiple-geographies-multi-geo"></a>多地理位置 (Multi-geo)

某些组织因业务需求需要在多个地理位置或区域具有 Power BI。 例如，业务可能在美国中有 Power BI 租户，但也可以在其他地理区域（如澳大利亚）中执行业务，并需要某些 Power BI 数据在该远程区域保持静止，以符合当地的法规。 从2018的下半年开始，在一个地理位置具有其主租户的组织也可以预配和访问位于另一个地理位置 Power BI 资源。 为了在本文档中方便阅读和参考，将此功能称为“multi-geo”。

多地区信息的最新文章和最新文章是为 [Power BI Premium 文章配置多异地支持](../admin/service-admin-premium-multi-geo.md) 。 

在不同地区运营时，应在本地法律和法规的上下文中对多个技术详细信息进行评估。 这些详细信息包括：

- 远程查询执行层承载于远程容量区域，以确保数据模型、缓存和大多数数据处理都保留在远程容量区域中。 有一些例外情况，详细信息请 Power BI Premium 一文中的 [多地域](../admin/service-admin-premium-multi-geo.md) 。
- 缓存的查询文本和存储在远程区域中的相应结果将停留在该区域，但是传输中的其他数据可能会在多个地理区域之间来回切换。
-  (上传) 到 Power BI 服务的多地理容量的已发布的 .PBIX 或 .XLSX 文件可能会导致副本临时存储在 Power BI 租户区域中的 Azure Blob 存储中。 在这种情况下，将使用 Azure 存储服务加密 (SSE) 对数据进行加密，并且在文件内容处理和传输到远程区域完成后，会立即将副本计划为进行垃圾回收。 
- 跨多个地域环境中的区域移动数据时，将在7-30 天内删除源区域中的数据实例。 

### <a name="datacenters-and-locales"></a>数据中心和区域设置

Power BI 根据 Power BI 群集在区域数据中心的部署位置在某些区域提供。 Microsoft 计划将其 Power BI 基础结构扩展到其他数据中心。

以下链接提供了有关 Azure 数据中心的其他信息。

- [Azure 区域](https://azure.microsoft.com/regions/) - 有关 Azure 全球存在状况和位置的信息
- [Azure 服务（按区域）](https://azure.microsoft.com/regions/#services) - Microsoft 在每个区域提供的 Azure 服务（基础结构服务和平台服务）的完整列表。

目前，Power BI 服务在特定区域提供，由数据中心提供服务，如 [Microsoft 信任中心](https://www.microsoft.com/trust-center/product-overview)中所述。 下面的链接显示的是 Power BI 数据中心图，将光标悬停在某个区域上方即可查看位于该区域的数据中心：

* [Power BI 数据中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)

Microsoft 还为国家/地区主权提供数据中心。 有关国家云的 Power BI 服务可用性的详细信息，请参阅 [Power BI 国家云](https://powerbi.microsoft.com/clouds/)。

有关数据存储位置和使用方式的详细信息，请参阅 [Microsoft 信任中心](https://www.microsoft.com/trust-center/product-overview)。 在 [Microsoft Online Services 条款](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31)的“数据处理条款”中指定了有关静态客户数据位置的承诺使用量。

## <a name="user-authentication"></a>用户身份验证

Power BI 服务的用户身份验证包括用户的浏览器与 Power BI 服务或 Power BI 使用的 Azure 服务之间的一系列请求、响应和重定向。 该序列介绍了 Power BI 中用户身份验证的过程。 有关组织的用户身份验证模型选项的详细信息 (登录模型) ，请参阅 Microsoft 365 的 " [选择登录模型](https://blogs.office.com/2014/05/13/choosing-a-sign-in-model-for-office-365/)"。

### <a name="authentication-sequence"></a>身份验证序列

Power BI 服务的用户身份验证序列如下图中的步骤所示。

1. 用户通过在地址栏中键入 Power BI 地址来启动与 Power BI 服务的连接，方法是：在地址栏中键入地址 (如 `https://app.powerbi.com`) 或从 Power BI 登陆页中选择 " _登录_ " (https://powerbi.microsoft.com) 。 使用 TLS 1.2 和 HTTPS 建立连接，浏览器和 Power BI 服务之间的所有后续通信都使用 HTTPS。 请求将发送到 Azure 流量管理器。

2. Azure 流量管理器检查用户的 DNS 记录，以确定部署 Power BI 的最近数据中心，并使用应将用户发送到其中的 WFE 群集的 IP 地址响应 DNS。

3. 然后，WFE 将用户重定向到 Microsoft Online Services 登录页面。

    ![身份验证序列](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

1. 用户进行身份验证后，登录页会将用户重定向到先前确定的最近的 Power BI 服务 WFE 群集。

2. 浏览器将从成功登录后获得的 cookie 提交到 Microsoft Online Services，WFE 群集内的 ASP.NET 服务会检查该 cookie。

3. WFE 集群使用 Azure Active Directory (AAD) 服务进行检查，以验证用户的 Power BI 服务订阅，并获取 AAD 安全令牌。 AAD 返回成功的用户身份验证并返回 AAD 安全令牌时，WFE 群集将咨询“Power BI**** 全局服务”，该服务维护租户及其 Power BI 后端群集位置的列表，并确定包含用户的租户的 Power BI 服务群集。 然后，WFE 群集将用户定向到其租户所在的 Power BI 群集，并向用户的浏览器返回一系列项：

      - **AAD 安全令牌**
      - **会话信息**
      - 用户可以与之通信和交互的后端群集的 Web 地址

1. 然后，用户的浏览器联系指定的 Azure CDN 或 WFE 的一些文件，以下载启用浏览器与 Power BI 服务交互所必需的指定公共文件的集合。 在 Power BI 服务浏览器会话期间，浏览器页面包含 AAD 令牌、会话信息、关联后端群集的位置以及从 Azure CDN 和 WFE 群集下载的文件集合。

![Azure CDN 交互](media/whitepaper-powerbi-security/powerbi-security-whitepaper_09.png)

完成这些项后，浏览器将开始联系指定的后端群集，用户与 Power BI 服务的交互开始启动。 从那时起，对 Power BI 服务的所有调用都使用指定的后端群集，并且所有调用都包含用户的 AAD 令牌。 AAD 令牌的超时时间为一小时；如果用户的会话保持打开状态，WFE 会定期刷新令牌，以保持访问权限。

## <a name="data-storage-and-movement"></a>数据存储和移动

在 Power BI 服务中，数据要么处于静态（可用于 Power BI 用户的当前未执行此操作的数据），要么在处理中（例如：正在运行的查询、正在执行操作的数据连接和模型、要上传到 Power BI 服务的数据和/或模型，以及用户或 Power BI 服务可能对正在活跃地访问或更新的数据采取的其他操作）。 在处理中的数据也称为“进程内数据”。 Power BI 中的静态数据是加密的。 传输中的数据（即 Power BI 服务发送或接收的数据）也是加密的。

Power BI 服务还根据是使用 DirectQuery 访问数据，还是导入数据，以不同的方式管理数据。 因此，Power BI 有两类用户数据：DirectQuery 访问的数据和 DirectQuery 不访问的数据。

DirectQuery 是一种查询，针对这种查询，Power BI 用户的查询已经从 Microsoft Data Analysis Expressions (DAX) 语言（这是 Power BI 和其他 Microsoft 产品用于创建查询的语言）转换为数据源的本机数据语言（例如，T-SQL 或其他本机数据库语言）。 与 DirectQuery 关联的数据仅通过引用存储，即 DirectQuery 未处于活跃状态时，源数据不会存储在 Power BI 中（用于显示仪表板和报告的可视化数据除外，如下面的“进程内数据（数据移动）”部分所述）。 相反，存储对 DirectQuery 数据的引用，从而允许在运行 DirectQuery 时访问该数据。 DirectQuery 包含执行查询所需的所有信息，包括用于访问数据源的连接字符串和凭据，这些信息允许 DirectQuery 连接到包含的数据源以进行自动刷新。 使用 DirectQuery，可以将基础数据模型信息合并到 DirectQuery 中。

导入数据集的查询由一组 DAX 查询组成，这些查询未直接转换为任何基础数据源的本机语言。 导入查询不包含基础数据的凭据，并且基础数据会加载到 Power BI 服务中，除非它是通过 [Power BI Gateway](../connect-data/service-gateway-onprem.md) 访问的本地数据。在这种情况下，查询仅存储对本地数据的引用。

下表说明基于正在使用的查询类型的 Power BI 数据。 **X** 指示使用关联的查询类型时有 Power BI 数据。

|                         | 导入   | DirectQuery | 实时连接  |
|-------------------------|----------|-------------|---------------|
|**架构**               | X        | X           |               |
|**行数据**             | X        |             |               |
|**视觉对象数据缓存** | X        | X           | X             |

DirectQuery 和其他查询之间的区别决定了 Power BI 服务如何处理静态数据，以及查询本身是否加密。 以下部分介绍静态数据和移动中的数据，并说明用于处理数据的加密、位置和过程。

### <a name="data-at-rest"></a>静态数据

数据处于静态时，Power BI 服务将按照以下小节中描述的方式存储数据集、报表和仪表板磁贴。 如前所述，Power BI 中的静态数据是加密的。 ETL 代表以下部分中的 Extract、Transform 和 Load。

#### <a name="encryption-keys"></a>加密密钥

- 在 Azure Key Vault 中存储、加密 Azure Blob 密钥的加密密钥。
- Azure SQL 数据库 TDE 技术的加密密钥由 Azure SQL 本身管理。
- 数据移动服务和本地数据网关的加密密钥存储在以下位置：
  - 在客户的基础结构上的本地数据网关中 - 用于本地数据源
  - 在数据移动角色中 - 用于基于云的数据源

用于加密 Microsoft Azure Blob 存储 (CEK) 的内容加密密钥是一个随机生成的256位密钥。 CEK 用于加密内容的算法是 AES \_CBC\_256。

用于加密 CEK 的密钥加密密钥 (KEK) 则是预定义的 256 位密钥。 KEK 加密 CEK 采用的算法是 A256KW。

基于恢复密钥的网关加密密钥永远不会离开本地基础结构。 Power BI 无法访问加密的本地凭据值，也无法拦截这些凭据；Web 客户端使用与其通信的特定网关关联的公钥来加密凭据。

对于基于云的数据源，数据移动角色使用 [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine) 方法对加密密钥进行加密。 可以详细了解 [Always Encrypted 数据库功能](/sql/relational-databases/security/encryption/always-encrypted-database-engine)。

#### <a name="datasets"></a>数据集

1. 元数据（表、列、度量值、计算、连接字符串等。）

    a. 对于本地 Analysis Services，除了对 Azure SQL 中加密存储的数据库的引用外，服务中不会存储任何内容。

    b. ETL、DirectQuery 和推送数据的所有其他元数据都已加密并存储在 Azure Blob 存储中。

1. 原始数据源的凭据
  
      a. 本地 Analysis Services – 不需要凭据，因此不存储凭据。

      b. DirectQuery - 取决于模型是否在服务中直接创建，如果直接创建，则存储在连接字符串中并在 Azure Blob 中加密；或者取决于是否从 Power BI Desktop 导入模型，如果导入，则凭据加密存储在数据移动的 Azure SQL 数据库。 加密密钥存储在客户基础结构上运行网关的计算机上。

      c. 推送的数据 - 不适用

      d. ETL

      - 对于“Salesforce”或“OneDrive” - 在 Power BI 服务的 Azure SQL 数据库中加密存储刷新令牌。
      - 否则：
        - 如果数据集设置为刷新，则凭据将加密存储在数据移动的 Azure SQL 数据库中。 加密密钥存储在客户基础结构上运行网关的计算机上。
        - 如果数据集未设置为刷新，则不存储数据源的凭据

1. 数据

    a. 本地 Analysis Services 和 DirectQuery - Power BI 服务中不存储任何内容。

    b. ETL - 在 Azure Blob 存储中加密，但当前在 Power BI 服务的 Azure Blob 存储中的所有数据都使用 [Azure 存储服务加密 (SSE)](/azure/storage/common/storage-service-encryption)（也称为服务器端加密）。 Multi-geo 也使用 SSE。

    c. 推送数据 v1 - 在 Azure Blob 存储中加密存储，但当前在 Power BI 服务的 Azure Blob 存储中的所有数据都使用 [Azure 存储服务加密 (SSE)](/azure/storage/common/storage-service-encryption)（也称为服务器端加密）。 Multi-geo 也使用 SSE。 推送数据 v1 从2016开始已停止使用。 

    d. 推送数据 v2 - 在 Azure SQL 中加密存储。

Power BI 使用客户端加密方法，利用具有高级加密标准 (AES) 的密码块链接 (CBC) 模式来加密其 Azure Blob 存储。 你可以[详细了解客户端加密](/azure/storage/common/storage-client-side-encryption)。

Power BI 通过以下方式提供数据完整性监视：

* 对于 Azure SQL 中的静态数据，Power BI 在 SQL 的本机产品/服务中使用 dbcc、TDE 和常数页面校验和。

* 对于 Azure Blob 存储中的静态数据，Power BI 使用客户端加密和 HTTPS 将数据传输到存储，其中包括在检索数据期间的完整性检查。 你可以[详细了解 Azure Blob 存储安全性](/azure/storage/blobs/security-recommendations)。

#### <a name="reports"></a>报表

1. 元数据（报表定义）

   a. 报表可以是 Excel Microsoft 365 报表，也可以 Power BI 报表。 以下内容适用于基于报表类型的元数据：
        
    &ensp;&ensp;一个。 Excel 报表元数据存储在 SQL Azure 中进行加密。 元数据也存储在 Microsoft 365 中。

    &ensp;&ensp;b。 Power BI 报表存储在 Azure SQL 数据库中。

2. 静态数据

   静态数据包括背景图像和 Power BI 视觉对象等项目。

    &ensp;&ensp;一个。 对于用 Excel Microsoft 365 创建的报表，不会存储任何内容。

    &ensp;&ensp;b。 对于 Power BI 报表，在 Azure Blob 存储中存储和加密静态数据。

3. 缓存

    &ensp;&ensp;一个。 对于用 Excel Microsoft 365 创建的报表，不会缓存任何内容。

    &ensp;&ensp;b。 对于 Power BI 报表，显示的报表视觉对象的数据将缓存并存储在以下部分所述的可视化数据缓存中。
 

4. 发布到 Power BI 的原始 Power BI Desktop (.pbix) 或 Excel (.xlsx) 文件

    有时，在 Power BI 的 Azure Blob 存储中存储 .xlsx 或 .pbix 文件的副本或影子副本。当发生这种情况时，会对数据进行加密。 存储在 Azure Blob 存储的 Power BI 服务中的所有此类报表都使用 [ Azure 存储服务加密 (SSE)](/azure/storage/common/storage-service-encryption)（也称为服务器端加密）。 Multi-geo 也使用 SSE。

#### <a name="dashboards-and-dashboard-tiles"></a>仪表板和仪表板磁贴

1. 缓存-仪表板上视觉对象所需的数据通常缓存并存储在以下部分所述的可视化数据缓存中。 其他磁贴（例如，Excel 或 SQL Server Reporting Services (SSRS) 中的固定视觉对象）作为图像存储在 Azure Blob 中，并且也进行了加密。

2. 静态数据-包括在 Azure Blob 存储中存储、加密的背景图像和 Power BI 视觉对象等项目。

无论使用哪种加密方法，Microsoft 都代表客户管理密钥加密。

#### <a name="visual-data-cache"></a>可视化数据缓存

视觉对象数据缓存在不同位置，具体取决于是否在 Power BI Premium 容量上承载数据集。 对于未托管在容量中的数据集，将缓存视觉数据并将其存储在 Azure SQL 数据库中进行加密。 对于在容量上承载的数据集，可在以下任何位置缓存可视数据：

* Azure Blob 存储
* Azure 高级文件
* "Power BI Premium 容量" 节点


### <a name="data-transiently-stored-on-non-volatile-devices"></a>数据暂时存储在非易失性设备上

非易失性设备是指有内存保持不间断电源的设备。 以下内容描述了暂时存储在非易失性设备上的数据。 

#### <a name="datasets"></a>数据集

1. 元数据（表、列、度量值、计算、连接字符串等。）

2. 一些与架构相关的项目可以在有限的时间内存储在计算节点的磁盘上。 某些项目也可以在未加密的 Azure REDIS Cache 中存储一段有限的时间。

3. 原始数据源的凭据

    a. 本地 Analysis Services - 不存储任何内容

    b. DirectQuery - 取决于模型是否在服务中直接创建，如果直接创建，则以加密格式存储在连接字符串中，加密密钥以明文形式存储在同一位置（与加密信息一起）；或者取决于是否从 Power BI Desktop 导入模型，如果导入，则凭据不会存储在非易失性设备上。

    > [!NOTE]
    > 从2017开始，服务端模型创建功能已停止使用。

    c. 推送的数据 - 无（不适用）

    d. ETL - 无（没有任何内容存储在计算节点上，也不同于上述“静态数据”部分中所述）
4. 数据

    一些数据项目可以在有限的时间内存储在计算节点的磁盘上。

### <a name="data-in-process"></a>进程内数据

用户主动使用或访问数据时，数据正在处理中。 例如，在用户访问数据集、修订或修改仪表板或报表时，或者在发生刷新或可能发生的其他数据访问活动时，数据就正在处理中。 发生任何这些事件并将数据放入进程时，Power BI 服务中的数据角色将创建内存中 Analysis Services (AS) 数据库，并将数据集加载到内存中 Analysis Services 数据库。 无论数据集是否基于 DirectQuery，AS 数据库中加载的数据都是未加密的，以允许数据角色访问，并保存在内存中以供进一步访问，直到 Power BI 服务不再需要数据集。 对于具有 Power BI Premium 订阅的客户，Power BI 会在客户单独预配的 Power BI 虚拟机集合中创建内存中 Analysis Services (AS) 数据库。

不论数据集是否基于 DirectQuery，对数据进行操作（包括第一次将数据加载到 Power BI）后，Power BI 服务就可以将可视化数据缓存在加密的 Azure SQL 数据库中。

要监视进程内数据的数据完整性，Power BI 使用 HTTPS、TCP/IP 和 TLS 来确保数据已加密并在传输过程中保持完整性。

## <a name="user-authentication-to-data-sources"></a>对数据源的用户身份验证

对于每个数据源，用户基于其登录名建立连接，并使用这些凭据访问数据。 然后，用户可以根据基础数据创建查询、仪表板和报表。

用户共享查询、仪表板、报表或任何可视化时，访问该数据和这些可视化取决于基础数据源是否支持 Role Level Security (RLS)。

如果基础数据源能够实现 Power BI 的 **** 角色级别安全性 (RLS)，Power BI 服务将应用该角色级别安全性，并且没有足够的凭据来访问基础数据（可以是在仪表板、报表或其他数据项目中使用的查询）的用户将不会看到用户没有足够权限访问的数据。 如果用户对基础数据的访问权限与创建仪表板或报表的用户不同，则可视化和其他项目将仅根据用户对数据的访问级别来显示数据。

如果数据源未应用 RLS，则 Power BI 登录凭据将应用于基础数据源，或者如果在连接期间提供了其他凭据，则应用所提供的凭据。 用户将数据从非 RLS 数据源加载到 Power BI 服务时，数据将存储在 Power BI 中，如本文档中的“数据存储和移动”部分所述。 对于非 RLS 数据源，数据与其他用户（例如，通过仪表板或报表）共享时或刷新数据时，原始凭据用于访问或显示数据。

![角色级别安全性 (RLS)](media/whitepaper-powerbi-security/powerbi-security-whitepaper_10.png)

对比 RLS 和非 RLS 数据源的一个简要示例是，假设 Sam 创建报表和仪表板，然后将其与 Abby 和 Ralph 共享。 如果报表和仪表板中使用的数据源来自不支持 RLS 的数据源，则 Abby 和 Ralph 都将能够看到 Sam 包含在仪表板中的数据（该数据已上传到 Power BI 服务），并且 Abby 和 Ralph 都可以与数据进行交互。 相反，如果 Sam 从支持 RLS 的数据源创建报表和仪表板，然后将其与 Abby 和 Ralph 共享，当 Abby 尝试查看仪表板时，会发生以下情况：

1. 由于仪表板来自 RLS 数据源，因此仪表板可视化将简要显示&quot;正在加载&quot;消息，同时 Power BI 服务查询数据源以检索与仪表板的基础查询关联的连接字符串中指定的当前数据集。

2. 数据的访问和检索基于 Abby 的凭据和角色，并且仅 Abby 拥有足够授权的数据才会加载到仪表板和报表中。

3. 仪表板和报告中的可视化根据 Abby 的角色级别显示。

如果 Ralph 要访问共享仪表板或报表，则会根据其角色级别产生相同的序列。

## <a name="power-bi-mobile"></a>Power BI 移动版

Power BI 移动版是为三个主要移动平台设计的应用的集合： Android、iOS 和 Windows Mobile。 Power BI 移动版应用的安全注意事项分为两类：

* 设备通信
* 设备上的应用程序和数据

对于设备通信，所有 Power BI 移动版应用程序都与 Power BI 服务进行通信，并使用浏览器使用的相同连接和身份验证序列，本白皮书前面部分对此进行了详细介绍。 iOS 和 Android Power BI 移动版应用程序在应用程序内启动浏览器会话，而 Windows 移动版应用启动中转站以与 Power BI 建立通信通道。

下表按移动设备平台列出了 Power BI 移动版基于证书的身份验证 (CBA) 的支持情况：

| **CBA 支持** | **iOS** | **Android** | **Windows** |
| --- | --- | --- | --- |
| **Power BI**（登录服务） | 受支持 | 受支持 | 不支持 |
| **SSRS ADFS**（连接到 SSRS 服务器） | 不支持 | 支持 | 不支持 |

Power BI 移动版应用主动与 Power BI 服务进行通信。 遥测用于收集移动应用使用情况统计数据和类似数据，这些数据传输到用于监视使用情况和活动的服务；遥测数据中未发送个人数据。

设备上的 Power BI 应用程序在设备上存储有助于使用应用的数据：

* Azure Active Directory 和刷新令牌存储在设备上，采用的安全机制使用了行业标准安全措施。

* 数据缓存在设备的存储中，而不是由应用程序本身直接加密

* 设置也存储在未加密的设备上，但不存储实际的用户数据。

Power BI 移动版的数据缓存在设备上保留两周，或直到：应用程序已删除；用户注销 Power BI 移动版；或者用户无法登录（例如，令牌过期事件或密码更改）。 数据缓存包括以前从 Power BI 移动版应用访问的仪表板和报表。

Power BI 移动版应用程序不查看设备上的文件夹。 

Power BI 移动版可用的所有三个平台都支持 Microsoft Intune，这是一种提供移动设备和应用程序管理的软件服务。 启用并配置 Intune 后，将加密移动设备上的数据，并且 Power BI 应用程序本身无法安装在 SD 卡上。 你可以[详细了解 Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune)。

## <a name="power-bi-security-questions-and-answers"></a>Power BI 安全问题与解答

以下问题是 Power BI 的常见安全问题和解答。 这些内容按其添加到本白皮书的时间进行组织，以便在本文更新时快速找到新问题和答案。 最新的问题将添加到此列表的末尾。

**在使用 Power BI 时，用户如何连接并访问数据源？**

* **Power BI 凭据和域凭据：** 用户使用电子邮件地址登录到 Power BI;当用户尝试连接到数据资源时，Power BI 会将 Power BI 登录电子邮件地址作为凭据传递。 对于连接了域的资源（无论是本地还是基于云），目录服务将登录电子邮件与用户主体名称 ([UPN](/windows/win32/secauthn/user-name-formats)) 匹配，以确定是否存在允许访问的足够凭据。 如果组织使用基于工作的电子邮件地址登录到 Power BI (他们用于登录工作资源的同一电子邮件，如 _david@contoso.com_) ，则可以无缝地进行映射; 对于不使用基于工作的电子邮件地址 (如) 的组织， _david@contoso.onmicrosoft.com_ 必须建立目录映射，才能允许使用 Power BI 登录凭据访问本地资源。

* **SQL Server Analysis Services 和 Power BI：** 对于使用本地 SQL Server Analysis Services 的组织，Power BI 提供 Power BI 的本地数据网关 (，这是一个 **网关**，如前面部分) 所引用。  Power BI 本地数据网关可以对数据源 (RLS) 强制执行角色级安全性。 有关 RLS 的详细信息，请参阅本文档前面的“对数据源的用户身份验证”。 有关网关的详细信息，请参阅 [本地数据网关](../connect-data/service-gateway-onprem.md)。

  此外，组织可以使用 Kerberos 进行单一登录 (SSO)，并从 Power BI 无缝连接到 SQL Server、SAP HANA 和 Teradata 等本地数据源。 有关更多信息和特定配置要求，请参阅[将 Kerberos 用于从 Power BI 到本地数据源的 SSO](../connect-data/service-gateway-sso-overview.md)。

* **非域连接**：对于未加入域且不具备角色级别安全性 (RLS) 的数据连接，用户必须在连接顺序中提供凭据，然后 Power BI 传递到数据源以建立连接。 如果有足够的权限，则会将数据从数据源加载到 Power BI 服务。

**如何将数据传输到 Power BI？**

* Power BI 请求和传输的所有数据在传输过程中都使用 HTTPS 进行加密，以便从数据源连接到 Power BI 服务。 与数据提供程序建立安全连接，并且只有在建立了该连接后，数据才能遍历网络。

**Power BI 如何缓存报表、仪表板或模型数据，以及缓存是否安全？**

* 访问数据源时，Power BI 服务将遵循本文档前面的“数据存储和移动”部分中概述的过程操作。

**客户端是否在本地缓存网页数据？**

* 浏览器客户端访问 Power BI 时，Power BI Web 服务器会将“Cache-control”指令设置为“no-store”。 “no-store”指令指示浏览器不缓存用户正在查看的网页，并且不会将网页存储在客户端的缓存文件夹中。

**基于角色的安全性、共享报表或仪表板以及数据连接是什么？如何处理数据访问、仪表板查看、报表访问或刷新？**

* 对于启用了“非角色级别安全性 (RLS)”的数据源，如果通过 Power BI 与其他用户共享仪表板、报表或数据模型，则获得该数据共享的用户可以查看和交互该数据。 Power BI 不会针对原始数据源重新验证用户身份；将数据上传到 Power BI 后，对源数据进行身份验证的用户负责管理可以查看数据的其他用户和组。

  与支持 RLS 的数据源（例如，Analysis Services 数据源）建立数据连接时，仅在 Power BI 中缓存仪表板数据。 每次在 Power BI 中查看或访问使用支持 RLS 的数据源中的数据的报表或数据集时，Power BI 服务都会访问数据源以根据用户的凭据获取数据。如果存在足够的权限，则将数据加载到该用户的报表或数据模型中。 如果身份验证失败，用户将看到错误。

  有关详细信息，请参阅本文档前面的“对数据源的用户身份验证”部分。

**我们的用户始终都连接到相同的数据源，其中一些用户需要不同于其域凭据的凭据。如何避免在每次进行数据连接时都输入这些凭据？**

* Power BI 提供了 [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846)，该功能允许用户为多个不同的数据源创建凭据，随后在访问这些数据源时可自动使用这些凭据。 有关详细信息，请参阅 [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846)。

**Power BI 组是如何工作的？**

* Power BI 组允许用户快速轻松地在已建立的团队中协作创建仪表板、报表和数据模型。 例如，如果你有 Power BI 组，其中包含所在团队中的所有人，则从 Power BI 中选择组便可轻松地与团队中的每个人进行协作。 Power BI 组等同于 Office 365 通用组（可以[了解有关](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)、[创建](https://support.office.com/Article/View-create-and-delete-Groups-in-the-Office-365-admin-center-a6360120-2fc4-46af-b105-6a04dc5461c7)和[管理](https://support.office.com/Article/Manage-Group-membership-in-the-Office-365-admin-center-e186d224-a324-4afa-8300-0e4fc0c3000a)的信息），并使用 Azure Active Directory 中使用的相同身份验证机制来保护数据。 可以[在 Power BI 中创建组](https://support.powerbi.com/knowledgebase/articles/654250)，或在 Microsoft 365 管理中心中创建通用组；或者在 Power BI 中创建组的结果与此相同。

  请注意，与 Power BI 组共享的数据具有与 Power BI 中的任何共享数据相同的安全注意事项。 对于非 RLS 数据源，Power BI 不会针对原始数据源重新验证用户身份。将数据上传到 Power BI 后，对源数据进行身份验证的用户负责管理可以查看数据的其他用户和组。 有关详细信息，请参阅本文档前面的“对数据源的用户身份验证”部分。

  可以获取有关 [Power BI 中的组](https://support.powerbi.com/knowledgebase/articles/654247)的详细信息。

**本地数据网关和个人网关使用哪些端口？是否有任何域名是否需要用于连接？**

* 有关此问题的详细解答，请访问以下链接： [网关端口](/data-integration/gateway/service-gateway-communication#ports)

**使用本地数据网关时，如何使用恢复密钥，它们存储在何处？安全凭据管理是什么？**

* 在网关安装和配置期间，管理员键入网关“恢复密钥”。 该 **恢复密钥** 用于生成强 **AES** 对称密钥。 同时还会创建一个 **RSA** 非对称密钥。

    这些生成的密钥（RSA 和 AES）存储在本地计算机上的文件中。 该文件也是加密的。 该文件的内容只能由该特定 Windows 计算机解密，并且只能由该特定网关服务帐户解密。

    用户在 Power BI 服务 UI 中输入数据源凭据时，将使用浏览器中的公钥对凭据进行加密。 网关使用 RSA 私钥对凭据进行解密，并使用 AES 对称密钥对其进行重新加密，然后将数据存储在 Power BI 服务中。 通过此过程，Power BI 服务永远无法访问未加密的数据。

**本地数据网关使用哪些通信协议，以及如何保护这些协议？**

* 网关支持以下两种通信协议：

  - **AMQP 1.0 – TCP + TLS**：此协议需要为传出通信打开端口443、5671-5672 和9350-9354。 此协议是首选方法，因为它具有较低的通信开销。

  - **Https – ip-https OVER https**：此协议只使用端口443。 WebSocket 由单个 HTTP CONNECT 消息发起。 建立通道后，通信实质上是 TCP+TLS。 可以通过修改 [本地网关一文](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus)中所述的设置，强制网关使用此协议。

**Azure CDN 在 Power BI 中的角色是什么？**

* 如前所述，Power BI 使用 Azure 内容分发网络 (CDN) 来有效地根据地理区域设置将所需的静态内容和文件分发到用户。 为了进一步详细说明，Power BI 服务使用多个 CDN 通过公共 Internet 有效地将所需的静态内容和文件分发到用户。 这些静态文件包括产品下载（如 Power BI Desktop、本地数据网关或来自各个独立服务提供商的 Power BI 应用）、用于发起和建立与 Power BI 服务的任何后续连接的浏览器配置文件以及初始安全 Power BI 登录页。

  根据初始连接到 Power BI 服务期间提供的信息，用户的浏览器会联系指定的 Azure CDN（或者对于某些文件，则联系 WFE），以下载启用浏览器与 Power BI 服务交互所需的指定公共文件集合。 在 Power BI 服务浏览器会话期间，浏览器页面包含 AAD 令牌、会话信息、关联后端群集的位置以及从 Azure CDN 和 WFE 群集下载的文件集合。

**对于 Power BI 视觉对象，Microsoft 是否在将项目发布到库之前对自定义视觉对象执行任何安全或隐私评估？**

* 不是。 客户有责任评审并确定是否应依赖自定义视觉对象代码。 所有自定义视觉对象代码都在沙盒环境中运行，因此自定义视觉对象中的任何错误代码都不会对 Power BI 服务的其余部分产生负面影响。

**是否有在客户网络外发送信息的其他 Power BI 视觉对象？**

* 是。 必应地图和 ESRI 视觉对象为使用这些服务的视觉对象在 Power BI 服务外部传输数据。

**对于模板应用，Microsoft 是否在将项目发布到库之前对模板应用执行任何安全或隐私评估？**
* 不是。 应用发布者负责查看内容，同时客户需要查看并确定是否信任模板应用发行者。 

**是否存在可以在客户网络之外发送信息的模板应用？**
* 是。 客户负责查看发布者的隐私策略，并确定是否在租户上安装模板应用。 此外，发布者还负责通知应用程序的行为和功能。

**数据主权？能否在位于特定地理区域的数据中心内预配租户，以确保数据不会留下国家/地区界限？**

* 某些地理位置的某些客户可以选择在国家云中创建租户，其中数据存储和处理与所有其他数据中心分开。 由于单独的数据受托人代表 Microsoft 对国家云 Power BI 服务进行操作，因此国家云的安全性略有不同。

  或者，客户也可以在特定区域中设置租户，但此类租户不具有来自 Microsoft 的单独数据受托人。 国家云的定价不同于已公开发布的商业版 Power BI 服务。 有关国家云的 Power BI 服务可用性的详细信息，请参阅 [Power BI 国家云](https://powerbi.microsoft.com/clouds/)。

**Microsoft 如何为具有 Power BI Premium 订阅的客户处理连接？那些连接是否不同于为非高级 Power BI 服务建立的连接？**

* 为具有 Power BI Premium 订阅的客户建立的连接实施 [Azure 企业对企业 (B2B)](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)授权过程，使用 Azure Active Directory (AD) 启用访问控制和授权。 Power BI 处理从 Power BI 订阅者到 Power BI 资源的连接，就像处理任何其他 Azure AD 用户一样。

## <a name="conclusion"></a>结束语

Power BI 服务体系结构基于两个群集 - Web 前端 (WFE) 群集和后端群集。 WFE 群集负责执行初始连接并对 Power BI 服务进行身份验证，经过身份验证后后，后端会处理所有后续的用户交互。 Power BI 使用 Azure Active Directory (AAD) 来存储和管理用户身份，并分别使用 Azure Blob 和 Azure SQL Database 管理数据和元数据存储。

Power BI 中的数据存储和数据处理根据是否使用 DirectQuery 访问数据而有所不同，并且还取决于数据源是在云中还是在本地。 Power BI 还能够强制执行角色级别安全性 (RLS) ，并且与提供对本地数据的访问的网关进行交互。

## <a name="feedback-and-suggestions"></a>反馈和建议

我们非常感谢反馈。 我们有兴趣听取你对本白皮书的改进、补充或说明以及与 Power BI 相关的其他内容的任何建议。 向发送建议 [pbidocfeedback@microsoft.com](mailto:pbidocfeedback@microsoft.com) 。

## <a name="additional-resources"></a>其他资源

有关 Power BI 的更多信息，请参阅以下资源。

- [Power BI 中的组](https://support.powerbi.com/knowledgebase/articles/654247)
- [Power BI Desktop 入门](https://support.powerbi.com/knowledgebase/articles/471664)
- [Power BI REST API - 概述](/rest/api/power-bi/)
- [Power BI API 引用](/rest/api/power-bi/)
- [On-premises data gateway (本地数据网关)](../connect-data/service-gateway-onprem.md)
- [Power BI 国家云](https://powerbi.microsoft.com/clouds/)
- [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
- [将 Kerberos 用于从 Power BI 到本地数据源的 SSO](../connect-data/service-gateway-sso-overview.md)
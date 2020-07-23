---
title: 排查 Power BI Premium（预览版）中 XMLA 终结点的连接问题
description: 介绍如何通过 Power BI Premium 中的 XMLA 终结点来排查连接问题。
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 07/16/2020
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 5d6e3af615a73f8e4a3db42406bf94e33f16a2a3
ms.sourcegitcommit: cfcde5ff2421be35dc1efc9e71ce2013f55ec78f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86459660"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>排查 XMLA 终结点连接问题

Power BI Premium 中的 XMLA 终结点依赖于本机 Analysis Services 通信协议来访问 Power BI 数据集。 因此，XMLA 终结点故障排除与排查典型 Analysis Services 连接问题大致相同。 但 Power BI 特定依赖项的某些差异也适用。

## <a name="before-you-begin"></a>开始之前

在对 XMLA 终结点方案进行故障排除之前，请务必查看[使用 XMLA 终结点的数据集连接](service-premium-connect-tools.md)中所述的基本知识。 其中介绍了最常见的 XMLA 终结点用例。 其他 Power BI 故障排除指南（如[对网关进行排除故障 - Power BI](../connect-data/service-gateway-onprem-tshoot.md) 和[“在 Excel 中分析”故障排除](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)）也会有所帮助。

## <a name="enabling-the-xmla-endpoint"></a>启用 XMLA 终结点

可以在 Power BI Premium 和 Power BI Embedded 容量上启用 XMLA 终结点。 对于较小的容量（例如仅 2.5 GB 内存的 A1 容量），尝试将 XMLA 终结点设置为“读/写”，然后选择“应用”时，可能会在“容量”设置中遇到错误。 错误指示“工作负荷设置出现问题。 请稍后重试。”。

下面是几个要尝试的操作：

- 将容量中其他服务的内存消耗限制为 40% 或更少，或者完全禁用不必要的服务。  
- 将容量升级到更大的 SKU。 例如，从 A1 升级到 A3 容量可解决此配置问题，而无需禁用数据流。

请记住，还必须在 Power BI 管理门户中启用租户级[导出数据设置](service-premium-connect-tools.md#security)。 “在 Excel 中分析”功能也需要此设置。

## <a name="establishing-a-client-connection"></a>建立客户端连接

启用 XMLA 终结点后，最好测试与容量上工作区的连接性。 要了解详细信息，请参阅[连接到 Premium 工作区](service-premium-connect-tools.md#connecting-to-a-premium-workspace)。 另外，请务必阅读[连接要求](service-premium-connect-tools.md#connection-requirements)部分，了解有关当前 XMLA 连接限制的有用提示和信息。

### <a name="connecting-with-a-service-principal"></a>使用服务主体进行连接

如果已启用租户设置以允许服务主体使用 Power BI API，如[启用服务主体](service-premium-service-principal.md#enable-service-principals)中所述，则可以使用服务主体连接到 XMLA 终结点。 请记住，服务主体要求工作区或数据集级别的与普通用户相同的访问权限级别。

若要使用服务主体，请确保在连接字符串中将应用程序标识信息指定为：

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

例如：

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

如果收到以下错误：

“无法连接到数据集，因为帐户信息不完整。 对于服务主体，请确保使用 app:\<appId>@\<tenantId> 格式指定租户 ID 和应用 ID，然后重试。”

请确保使用正确的格式指定租户 ID 和应用 ID。

也可以指定应用 ID 而不指定租户 ID。 但是，在这种情况下，必须将数据源 URL 中的 `myorg` 别名替换为实际租户 ID。 然后 Power BI 可以在正确的租户中查找服务主体。 但作为最佳做法，请使用 `myorg` 别名，并在用户 ID 参数中指定租户 ID 和应用 ID。

### <a name="connecting-with-azure-active-directory-b2b"></a>使用 Azure Active Directory B2B 进行连接

通过对 Power BI 中 Azure Active Directory (Azure AD) 企业到企业 (B2B) 的支持，你可以为外部来宾用户提供对 XMLA 终结点上的数据集的访问。 请务必先在 Power BI 管理门户中启用[与外部用户共享内容](service-admin-portal.md#export-and-sharing-settings)设置。 若要了解详细信息，请参阅[使用 Azure AD B2B 将 Power BI 内容分发给外部来宾用户](service-admin-azure-ad-b2b.md)。

## <a name="deploying-a-dataset"></a>部署数据集

可以将 Visual Studio (SSDT) 中的表格模型项目部署到 Power BI Premium 工作区，与部署到 Azure Analysis Services 大致相同。 但是，在部署到 Power BI Premium 工作区时，还有一些其他注意事项。 请务必查看“使用 XMLA 终结点的数据集连接”一文中的[部署 Visual Studio 中的模型项目 (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) 部分。

### <a name="deploying-a-new-model"></a>部署新模型

在默认配置中，Visual Studio尝试将模型作为部署操作的一部分处理，以便从数据源将数据加载到数据集。 如[部署 Visual Studio 中的模型项目 (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) 中所述，此操作可能会失败，因为不能在部署操作过程中指定数据源凭据。 相反，如果尚未为任何现有数据集定义数据源的凭据，则必须使用 Power BI 用户界面在数据集设置中指定数据源凭据（“数据集” > “设置” > “数据源凭据” > “编辑凭据”）。 定义数据源凭据后，Power BI 可以在元数据部署成功和创建了数据集之后，自动将凭据应用到此数据源。

如果 Power BI 无法将新的数据集绑定到数据源凭据，则会收到一条错误，指示“无法处理数据库。 原因:无法将修改保存到服务器。” 并显示错误代码“DMTS_DatasourceHasNoCredentialError”，如下所示：

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="模型部署错误":::

若要避免处理失败，请将“部署选项” > “处理选项”设置为“不处理”，如下图所示。 Visual Studio 就会只部署元数据。 然后，你可以配置数据源凭据，并在 Power BI 用户界面中为数据集单击“立即刷新”。 有关排查处理问题的信息，请参阅本文后面的[刷新数据集](#refreshing-a-dataset)部分。

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="“不处理”选项":::

### <a name="new-project-from-an-existing-dataset"></a>从现有数据集新建项目

不支持通过导入 Power BI Premium 工作区上现有数据集中的元数据来在 Visual Studio 中创建新的表格项目。 不过，你可以使用 SQL Server Management Studio 连接到数据集，使用脚本编写元数据，并在其他表格项目中重复使用。

## <a name="migrating-a-dataset-to-power-bi"></a>将数据集迁移到 Power BI

建议为表格模型指定 1500（或更高）的兼容性级别。 此兼容性级别支持大多数功能和数据源类型。 更高的兼容性级别与早期级别向后兼容。

### <a name="supported-data-providers"></a>支持的数据提供程序

在 1500 兼容性级别，Power BI 支持以下数据源类型：

- 提供程序数据源（包含模型元数据中连接字符串的旧式数据源）。
- 结构化数据源（在 1400 兼容性级别引入）。
- 数据源的内联 M 声明（就像 Power BI Desktop 声明的那样）。

建议使用结构化数据源，这是 Visual Studio 在执行导入数据流时默认创建的。 但是，如果你计划将现有模型迁移到使用提供程序数据源的 Power BI，请确保提供程序数据源依赖于支持的数据提供程序。 具体而言，即 Microsoft OLE DB Driver for SQL Server 和任何第三方 ODBC 驱动程序。 对于 OLE DB Driver for SQL Server，必须将数据源定义切换到用于 SQL Server 的 .NET Framework 数据提供程序。 对于在 Power BI 服务中可能不可用的第三方 ODBC 驱动程序，必须改为切换到结构化数据源定义。

此外，建议将 SQL Server 数据源定义中过时的 Microsoft OLE DB Driver for SQL Server (SQLNCLI11) 替换为适用于 SQL Server 的 .NET Framework 数据提供程序。

下表提供了适用于 SQL Server 的 .NET Framework 数据提供程序连接字符串示例，该连接字符串替换 OLE DB Driver for SQL Server 相应的连接字符串。

|适用于 SQL Server 的 OLE DB 驱动程序  |用于 SQL Server 的 .NET Framework 数据访问接口   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>交叉引用分区源

正如有多个数据源类型一样，表格模型还可以包含多个分区源类型，以便将数据导入表中。 具体而言，分区可以使用查询分区源或 M 分区源。 这些分区源类型又可以引用提供程序数据源或结构化数据源。 虽然 Azure Analysis Services 中的表格模型支持交叉引用这些不同的数据源和分区类型，但 Power BI 强制实现更严格的关系。 查询分区源必须引用提供程序数据源，而 M 分区源必须引用结构化数据源。 Power BI 中不支持其他组合。 如果要迁移交叉引用数据集，下表说明了支持的配置：  

|数据源   |分区源   |注释   |在使用 XMLA 终结点的 Power BI Premium 中受支持   |
|---------|---------|---------|---------|
|提供程序数据源      |   查询分区源      |   AS 引擎使用基于插件的连接堆栈来访问数据源。       |     是     |
|提供程序数据源      |   M 分区源       |   AS 引擎将提供程序数据源转换为泛型结构化数据源，然后使用糅合引擎导入数据。       |    否     |
|结构化数据源      |     查询分区源     |    AS 引擎将分区源上的本机查询包装到一个 M 表达式中，然后使用糅合引擎导入数据。      |    否     |
|结构化数据源      |    M 分区源      |     AS 引擎使用糅合引擎来导入数据。     |   是      |

## <a name="refreshing-a-dataset"></a>刷新数据集

使用 XMLA 终结点可以对表格模型以及在 Power BI Desktop 中创建的数据集执行刷新操作。 若要支持后者，请确保指定增强型存储格式设置。 如果要使用 XMLA 终结点执行处理或其他读/写操作，则需要此设置。 可以在 Power BI Desktop 的“预览功能”下找到此设置。 设置完成后，再次将 PBIX 解决方案发布到 Power BI Premium 工作区。  

如果在没有增强元数据的情况下通过 XMLA 终结点对模型执行刷新，Power BI 将返回以下错误：“仅在 Power BI Premium 中将属性 'DefaultPowerBIDataSourceVersion' 设置为 'PowerBI_V3' 的模型上支持此操作。”

### <a name="data-sources-and-impersonation"></a>数据源和模拟

可为提供程序数据源定义的模拟设置与 Power BI 无关。 Power BI 使用基于数据集设置的不同机制来管理数据源凭据。 为此，如果要创建提供程序数据源，请确保选择“服务帐户”。

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="模拟服务帐户":::

### <a name="fine-grained-processing"></a>细化处理

在 Power BI 中触发计划刷新或按需刷新时，Power BI 通常会刷新整个数据集。 在许多情况下，选择性地执行刷新更有效。 你可以在 SQL Server Management Studio (SSMS) 中执行细化处理任务（如下所示），或使用第三方工具或脚本。

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="在 SSMS 中处理表":::

## <a name="see-also"></a>另请参阅

[使用 XMLA 终结点的数据集连接](service-premium-connect-tools.md)   
[使用服务主体自动完成 Premium 工作区和数据集任务](service-premium-service-principal.md)   
[“在 Excel 中分析”故障排除](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)   
[表格模型解决方案部署](https://docs.microsoft.com/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current)

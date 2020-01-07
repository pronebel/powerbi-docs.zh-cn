---
title: Power BI 中的数据刷新
description: 本文从概念层面介绍了 Power BI 的数据刷新功能及其依赖项。
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: maggies
LocalizationGroup: Data refresh
ms.openlocfilehash: bdb5b797146dae0bd8c6a70163a245f44430da8c
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2020
ms.locfileid: "74791687"
---
# <a name="data-refresh-in-power-bi"></a>Power BI 中的数据刷新

借助 Power BI，你可以快速完成从数据到洞察再到操作的过程，但必须确保 Power BI 报表和仪表板中的数据是最新的。 了解如何刷新数据通常对于提供准确的结果至关重要。

本文从概念层面介绍了 Power BI 的数据刷新功能及其依赖项。 它还提供了避免常见刷新问题的最佳做法和技巧。 该内容为帮助你了解数据刷新的工作原理奠定了基础。 有关配置数据刷新的有针对性的分步说明，请参阅本文末尾的“后续步骤”部分中列出的教程和操作指南。

## <a name="understanding-data-refresh"></a>了解数据刷新

每当你刷新数据时，Power BI 都必须查询基础数据源，可能要将源数据加载到数据集中，然后更新报表或仪表板中依赖于该更新数据集的所有可视化效果。 整个过程由多个阶段组成，具体取决于数据集的存储模式，如以下各节所述。

若要了解 Power BI 如何刷新数据集、报表和仪表板，必须了解以下概念：

- **存储模式和数据集类型**：Power BI 支持的存储模式和数据集类型具有不同的刷新要求。 你可以选择将数据重新导入 Power BI 来查看发生的所有更改，也可以选择直接在源中查询数据。
- **Power BI 刷新类型**：无论数据集的具体情况如何，了解各种刷新类型都可以帮助你了解 Power BI 在刷新操作期间将时间花在哪些地方。 将这些详细信息与存储模式细节相结合有助于了解为数据集选择“立即刷新”时 Power BI 的确切执行情况  。

### <a name="storage-modes-and-dataset-types"></a>存储模式和数据集类型

Power BI 数据集可以在下列模式之一中运行，以访问各种数据源中的数据。 有关详细信息，请参阅 [Power BI Desktop 中的存储模式](desktop-storage-mode.md)。

- 导入模式
- DirectQuery 模式
- LiveConnect 模式
- 推送模式

下图阐释了基于存储模式的不同数据流。 最重要的一点是，只有导入模式数据集才需要刷新源数据。 之所以需要刷新，是因为只有这种数据集才会从其数据源导入数据，并且导入的数据可能会定期或临时更新。 DirectQuery 数据集以及在 LiveConnect 模式下连接到 Analysis Services 的数据集不导入数据；它们通过每次用户交互查询基础数据源。 推送模式下的数据集不直接访问任何数据源，但需要你将数据推送到 Power BI 中。 数据集刷新要求因存储模式/数据集类型而异。

![存储模式和数据集类型](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>导入模式下的数据集

Power BI 将数据从原始数据源导入到数据集中。 提交到数据集的 Power BI 报表和仪表板查询从导入的表和列中返回结果。 可以将此类数据集视为时间点副本。 由于 Power BI 复制数据，因此必须刷新数据集以从基础数据源提取更改。

由于 Power BI 缓存数据，因此导入模式数据集可能会很大。 有关每种容量的最大数据集大小，请参阅下表。 通过将数据集大小保持在远低于最大大小的水平，可避免在刷新操作期间数据集需要的资源超过可用资源上限时出现刷新问题。

| 容量类型 | 最大数据集大小 |
| --- | --- |
| 共享、A1、A2 或 A3 | 1GB |
| A4 或 P1 | 3 GB |
| A5 或 P2 | 6 GB |
| A6 或 P3 | 10GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>DirectQuery/LiveConnect 模式下的数据集

Power BI 不会通过在 DirectQuery/LiveConnect 模式下运行的连接导入数据。 相反，只要报表或仪表板查询数据集，数据集就会从基础数据源返回结果。 Power BI 转换查询并将其转发到数据源。

尽管在 DirectQuery 模式和 LiveConnect 模式下，Power BI 都会将查询转发到源，但值得注意的是，Power BI 在 LiveConnect 模式下不必转换查询。 查询直接转到托管数据库的 Analysis Services 实例，而不会消耗共享容量或高级容量上的资源。

由于 Power BI 不导入数据，因此无需运行数据刷新。 但是，Power BI 仍执行磁贴刷新，还有可能执行报表刷新，如介绍刷新类型的下一节所述。 磁贴是固定到仪表板的报表视觉对象，仪表板磁贴大约每隔一小时刷新一次，以便磁贴显示最新的结果。 可以在数据集设置中更改计划，如下面的屏幕截图所示，或使用“立即刷新”选项手动强制更新仪表板  。

![刷新计划](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> “数据集”选项卡的“计划的缓存刷新”部分不适用于导入模式下的数据集   。 这些数据集不需要单独刷新磁贴，因为 Power BI 会在每次计划或按需数据刷新期间自动刷新磁贴。

#### <a name="push-datasets"></a>推送数据集

推送数据集不包含数据源的正式定义，因此它们不要求你在 Power BI 中执行数据刷新。 可以通过使用外部服务或进程（例如 Azure 流分析）将数据推送到数据集来刷新它们。 这是使用 Power BI 进行实时分析的常用方法。 Power BI 仍会对基于推送数据集使用的所有磁贴执行缓存刷新。 有关详细演练，请参阅[教程：流分析和 Power BI：针对流式处理数据的实时分析仪表板](/azure/stream-analytics/stream-analytics-power-bi-dashboard)。

> [!NOTE]
> 如 [Power BI REST API 限制](developer/api-rest-api-limitations.md)中所述，推送模式存在若干限制。

### <a name="power-bi-refresh-types"></a>Power BI 刷新类型

Power BI 刷新操作可以包含多种刷新类型，包括数据刷新、OneDrive 刷新、查询缓存刷新、磁贴刷新和报表视觉对象刷新。 虽然 Power BI 会自动确定给定数据集所需的刷新步骤，但你应该知道它们如何影响刷新操作的复杂性和持续时间。 有关快速参考，请参阅下表。

| 存储模式 | 数据刷新 | OneDrive 刷新 | 查询缓存 | 磁贴刷新 | 报表视觉对象 |
| --- | --- | --- | --- | --- | --- |
| 导入 | 计划和按需 | 是，针对已连接的数据集 | 如果已在高级容量上启用 | 自动和按需 | 否 |
| DirectQuery | 不适用 | 是，针对已连接的数据集 | 如果已在高级容量上启用 | 自动和按需 | 否 |
| LiveConnect | 不适用 | 是，针对已连接的数据集 | 如果已在高级容量上启用 | 自动和按需 | 是 |
| 推送 | 不适用 | 不适用 | 不可行 | 自动和按需 | 否 |
| | | | | | |

#### <a name="data-refresh"></a>数据刷新

对 Power BI 用户而言，刷新数据通常意味着根据刷新计划或按需将数据从原始数据源导入到数据集。 可以每天执行多次数据集刷新，如果基础源数据经常更改，则可能必须执行多次刷新。 Power BI 将共享容量上的数据集限制为每天最多刷新 8 次。 如果数据集驻留在 Premium 容量上，则每天最多可在数据集设置中计划 48 次刷新。 有关详细信息，请参阅本文后面的[配置计划刷新](#configure-scheduled-refresh)。

还有一点非常重要，就是每日刷新的共享容量限制适用于计划刷新和组合 API 刷新。 还可以通过在数据集菜单中选择“立即刷新”来触发按需刷新，如下面的屏幕截图所示  。 刷新限制不包括按需刷新。 另请注意，Premium 容量中的数据集不会对 API 刷新施加限制。 如果你有兴趣使用 Power BI REST API 生成自己的刷新解决方案，请参阅[数据集 - 刷新数据集](/rest/api/power-bi/datasets/refreshdataset)。

![立即刷新](media/refresh-data/refresh-now.png)

> [!NOTE]
> 在共享容量中，数据刷新必须在 2 小时内完成。 如果数据集需要进行更长时间的刷新操作，请考虑将数据集移到高级容量上。 在高级容量上，最长刷新持续时间为 5 小时。

#### <a name="onedrive-refresh"></a>OneDrive 刷新

如果数据集和报表是基于 OneDrive 或 SharePoint Online 上的 Power BI Desktop 文件、Excel 工作簿或逗号分隔值 (.csv) 文件创建的，则 Power BI 会执行另一种类型的刷新，称为 OneDrive 刷新。 有关详细信息，请参阅[从 Power BI 文件获取数据](service-get-data-from-files.md)。

OneDrive 刷新与 Power BI 将数据从数据源导入到数据集的数据集刷新不同，它会将数据集和报表与其源文件同步。 默认情况下，Power BI 以大约每小时一次的频率检查连接到 OneDrive 或 SharePoint Online 上的文件的数据集是否需要同步。

> [!IMPORTANT]
> 注意如何在 OneDrive 上处理文件管理。 如果将 OneDrive 文件设置为数据源，Power BI 在执行刷新时会引用该文件的项 ID，这可能会在某些情况下引发问题。 请考虑这种情况：你有主文件 A 和该文件的生产副本 B，同时你为文件 B 配置了 OneDrive 刷新。如果随后复制文件 A 而不是文件 B，则复制操作会删除旧的文件 B，并新建具有不同项 ID 的文件 B，而这会中断 OneDrive 刷新    。 所以应改为上传并替换文件 B，这样即可保留相同的项 ID。

可以将文件移动（例如，使用拖放操作）到其他位置，由于 PBI 仍可识别文件 ID，刷新将继续进行。 但如果将该文件复制到其他位置，则会新建该文件的实例和文件 ID。 因而 Power BI 文件引用将失效，且刷新将失败。

若要查看过去的同步周期，请检查刷新历史记录中的 OneDrive 选项卡。 以下屏幕截图显示了示例数据集的完整同步周期。

![刷新历史记录](media/refresh-data/refresh-history.png)

如上面的屏幕截图所示，Power BI 将此 OneDrive 刷新标识为**计划**刷新，但无法配置刷新间隔。 只能在数据集设置中停用 OneDrive 刷新。 如果不希望 Power BI 中的数据集和报表自动从源文件中获取任何更改，则停用刷新非常有用。

请注意，仅当数据集连接到 OneDrive 或 SharePoint Online 中的文件时，数据集设置页面才会显示“OneDrive 凭据”和“OneDrive 刷新”部分，如以下屏幕截图所示   。 未连接到 OneDrive 或 SharePoint Online 中的源文件的数据集不显示这些部分。

![OneDrive 凭据和 OneDrive 刷新](media/refresh-data/onedrive-credentials-refresh.png)

为数据集禁用 OneDrive 刷新后，仍可以通过在数据集菜单中选择“立即刷新”来按需同步数据集  。 在按需刷新过程中，Power BI 会检查 OneDrive 或 SharePoint Online 上的源文件是否比 Power BI 中的数据集更新，如果是，则同步数据集。 “刷新历史记录”会在“OneDrive”选项卡上将这些活动列为按需刷新   。

请记住，OneDrive 刷新不会从原始数据源中请求数据， 而只是使用 .pbix、.xlsx 或 .csv 文件中的元数据和数据更新 Power BI 中的资源，如下图所示。 为确保数据集具有数据源中的最新数据，Power BI 还会在按需刷新过程中触发数据刷新。 你可以在“刷新历史记录”中切换到“计划”选项卡来对此进行验证   。

![OneDrive 刷新图](media/refresh-data/onedrive-refresh-diagram.png)

如果为连接 OneDrive 或 SharePoint Online 的数据集一直启用 OneDrive 刷新，并且希望按计划执行数据刷新，请确保配置计划，以便 Power BI 在 OneDrive 刷新后执行数据刷新。 例如，如果你创建自己的服务或进程，以在每天凌晨 1 点更新 OneDrive 或 SharePoint Online 中的源文件，则可以将计划刷新配置为凌晨 2:30，以便为 Power BI 提供足够的时间来完成 OneDrive 刷新，然后再启动数据刷新。

#### <a name="refresh-of-query-caches"></a>查询缓存刷新

如果数据集驻留在高级容量上，则可以通过启用查询缓存来提高所有关联报表和仪表板的性能，如以下屏幕截图所示。 查询缓存会指示高级容量使用其本地缓存服务来维护查询结果，避免基本数据源计算这些结果。 有关详细信息，请参阅 [Power BI Premium 中的查询缓存](power-bi-query-caching.md)。

![查询缓存](media/refresh-data/query-caching.png)

但是，在进行数据刷新之后，先前缓存的查询结果便不再有效。 Power BI 会丢弃这些缓存结果，并且必须重新生成它们。 因此，对于与经常刷新（例如每天 48 次）的数据集关联的报表和仪表板，使用查询缓存的意义不大。

#### <a name="tile-refresh"></a>磁贴刷新

Power BI 为仪表板上的每个磁贴视觉对象维护一个缓存，并在数据更改时主动更新磁贴缓存。 换句话说，在数据刷新之后会自动进行磁贴刷新。 计划刷新操作和按需刷新操作都是如此。 还可以通过选择仪表板右上角的“更多选项”(...) 并选择“刷新仪表板磁贴”来强制进行磁贴刷新   。

![刷新仪表板磁贴](media/refresh-data/refresh-dashboard-tiles.png)

由于它是自动发生的，因此可以将磁贴刷新视为数据刷新固有的一部分。 此外，你可能会注意到刷新持续时间随着磁贴数量的增加而增加。 磁贴刷新开销可能很大。

默认情况下，Power BI 为每个磁贴维护一个缓存，但如果使用动态安全性根据用户角色来限制数据访问（如 [Power BI 行级别安全性 (RLS)](service-admin-rls.md) 一文所述），则 Power BI 必须为每个角色和每个磁贴维护一个缓存。 磁贴缓存的数量乘以角色的数量。

如教程[通过 Analysis Services 表格模型实现动态行级别安全性](desktop-tutorial-row-level-security-onprem-ssas-tabular.md)中所强调的那样，如果数据集通过 RLS 实时连接到 Analysis Services 数据模型，则情况会更加复杂。 在这种情况下，Power BI 必须为每个磁贴和每个查看过仪表板的用户维护和刷新缓存。 此类数据刷新操作的磁贴刷新部分会远远超出从源提取数据所花费的时间，且这种情况并不少见。 有关磁贴刷新的更多详细信息，请参阅[磁贴错误故障排除](refresh-troubleshooting-tile-errors.md)。

#### <a name="refresh-of-report-visuals"></a>报表视觉对象刷新

此刷新过程不太重要，因为它仅与 Analysis Services 的实时连接有关。 对于这些连接，Power BI 会缓存报表视觉对象的最后一个状态，这样一来，当你再次查看报表时，Power BI 就不必查询 Analysis Services 表格模型。 当你与报表交互时（例如通过更改报表筛选器），Power BI 会查询表格模型并自动更新报表视觉对象。 如果你怀疑报表显示过时数据，还可以选择报表的“刷新”按钮来触发所有报表视觉对象的刷新操作，如以下屏幕截图所示。

![刷新报表视觉对象](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>查看数据基础结构依赖项

无论采用哪种存储模式，都必须能够访问基础数据源，否则将无法成功刷新数据。 有三种主要的数据访问方案：

- 数据集使用驻留在本地的数据源
- 数据集使用云中的数据源
- 数据集使用来自本地源和云源的数据

### <a name="connecting-to-on-premises-data-sources"></a>连接到本地数据源

如果数据集使用 Power BI 无法通过直接网络连接访问的数据源，则必须先为此数据集配置网关连接，然后才能启用刷新计划或执行按需数据刷新。 有关数据网关及其工作原理的详细信息，请参阅[什么是本地数据网关？](service-gateway-onprem.md)

你有以下选择：

- 选择具有所需数据源定义的企业数据网关
- 部署个人数据网关

> [!NOTE]
> 可以在[管理数据源 - 导入/计划刷新](service-gateway-enterprise-manage-scheduled-refresh.md)一文中找到需要数据网关的数据源类型列表。

#### <a name="using-an-enterprise-data-gateway"></a>使用企业数据网关

Microsoft 建议使用企业数据网关（而不是个人网关）将数据集连接到本地数据源。 请确保正确配置网关，这意味着网关必须具有最新的更新和所有必需的数据源定义。 数据源定义可为 Power BI 提供给定源的连接信息，包括连接终结点、身份验证模式和凭据。 有关在网关上管理数据源的详细信息，请参阅[管理数据源 - 导入/计划刷新](service-gateway-enterprise-manage-scheduled-refresh.md)。

如果你是网关管理员，则将数据集连接到企业网关相对来说比较简单。 必要时，可以使用管理员权限立即更新网关并添加缺少的数据源。 事实上，可以直接从数据集设置页面向网关添加缺少的数据源。 展开切换按钮以查看数据源，然后选择“添加到网关”链接，如以下屏幕截图所示  。 但如果你不是网关管理员，则必须联系网关管理员添加所需的数据源定义。

> [!NOTE]
> 仅网关管理员可将数据源添加到网关。 此外，确保网关管理员将你的用户帐户添加到有权使用数据源的用户的列表。 数据集设置页仅允许选择你有权使用其匹配数据源的企业网关。

![添加到网关](media/refresh-data/add-to-gateway.png)

请确保将正确的数据源定义映射到数据源。 如上面的屏幕截图所示，网关管理员可在连接到同一数据源的单个网关上创建多个定义，其中每个定义使用不同的凭据。 如示例中所示，销售部门中的数据集所有者会选择 AdventureWorksProducts-Sales 数据源定义，而支持部门中的数据集所有者会将数据集映射到 AdventureWorksProducts-Support 数据源定义。 如果数据源定义的名称不直观，请联系网关管理员来明确要选择哪个定义。

> [!NOTE]
> 一个数据集只能使用一个网关连接。 换句话说，不能跨多个网关连接访问本地数据源。 因此，必须将所有必需的数据源定义添加到同一网关。

#### <a name="deploying-a-personal-data-gateway"></a>部署个人数据网关

如果你无权访问企业数据网关，并且你是唯一管理数据集的人员，因此无需与其他人共享数据源，则可以在个人模式下部署数据网关。 在“网关连接”部分的“未安装个人网关”下，选择“立即安装”    。 如[本地数据网关（个人模式）](service-gateway-personal-mode.md)中所述，个人数据网关存在若干限制。

与企业数据网关不同，你无需向个人网关添加数据源定义， 而是使用数据集设置中的“数据源凭据”部分来管理数据源配置，如以下屏幕截图所示  。

![配置网关的数据源凭据](media/refresh-data/configure-data-source-credentials-gateway.png)

> [!NOTE]
> 个人数据网关不支持 DirectQuery/LiveConnect 模式下的数据集。 数据集设置页面可能会提示你安装它，但如果你只有个人网关，则无法配置网关连接。 请确保安装企业数据网关来支持这些类型的数据集。

### <a name="accessing-cloud-data-sources"></a>访问云数据源

如果 Power BI 可以与云数据源（如 Azure SQL DB）建立直接网络连接，则使用该源的数据集不需要数据网关。 相应地，可以使用数据集设置中的“数据源凭据”部分来管理这些数据源的配置  。 如以下屏幕截图所示，你无需配置网关连接。

![在没有网关的情况下配置数据源凭据](media/refresh-data/configure-data-source-credentials.png)

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>在同一源查询中访问本地源和云源

数据集可以从多个源获取数据，这些源可以驻留在本地或云中。 但是，如前所述，一个数据集只能使用一个网关连接。 虽然云数据源不一定需要网关，但如果数据集在单个糅合查询中同时连接到本地源和云源，则需要网关。 在此方案中，Power BI 也必须使用网关来访问云数据源。 下图阐释了此类数据集如何访问其数据源。

![云和本地数据源](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> 如果数据集使用不同的糅合查询连接到本地源和云源，则 Power BI 使用网关连接访问本地源，使用直接网络连接访问云源。 如果糅合查询合并或追加​​来自本地源和云源的数据，则即使是云源，Power BI 也会切换为使用网关连接。

Power BI 数据集依靠 Power Query 来访问和检索源数据。 以下糅合列表显示了合并来自本地源和云源的数据的基本查询示例。

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

可通过以下两种方式来配置数据网关，以支持合并或追加来自本地源和云源的​​数据：

- 除本地数据源外，将云源的数据源定义也添加到数据网关。
- 启用复选框“允许用户的云数据源通过此网关群集刷新”  。

![通过网关群集刷新](media/refresh-data/refresh-gateway-cluster.png)

如果启用“允许用户的云数据源通过网关配置中的此网关群集刷新”复选框（如上面的屏幕截图所示），则 Power BI 可使用用户在数据集设置中的“数据源凭据”下为云源定义的配置   。 这有助于降低网关配置开销。 但是，如果希望更好地控制网关建立的连接，则不应启用此复选框。 在这种情况下，必须向网关添加要支持的每个云源的显式数据源定义。 也可以启用该复选框，并向网关添加云源的显式数据源定义。 在这种情况下，网关会使用所有匹配源的数据源定义。

### <a name="configuring-query-parameters"></a>配置查询参数

使用 Power Query 创建的糅合或 M 查询的复杂程度可能不同，既有可能是简单的步骤，也有可能是复杂的参数化构造。 以下列表显示了一个小型糅合查询示例，它使用两个名为 _SchemaName_ 和 _TableName_ 的参数来访问 AdventureWorks 数据库中的给定表。

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> 查询参数仅适用于导入模式数据集。 DirectQuery/LiveConnect 模式不支持查询参数定义。

若要确保参数化数据集访问正确的数据，必须在数据集设置中配置糅合查询参数。 也可以使用 [Power BI REST API](/rest/api/power-bi/datasets/updateparametersingroup) 以编程方式更新参数。 以下屏幕截图显示了一个用户界面，可在其中配置使用上述糅合查询的数据集的查询参数。

![配置查询参数](media/refresh-data/configure-query-parameters.png)

> [!NOTE]
> Power BI 当前不支持参数化数据源定义，也称为动态数据源。 例如，无法参数化数据访问函数 Sql.Database("SqlServer01", "AdventureWorks")。 如果数据集依赖于动态数据源，Power BI 会通知你它检测到未知或不受支持的数据源。 如果希望 Power BI 能够识别并连接到数据源，则必须使用静态值替换数据访问函数中的参数。 有关详细信息，请参阅[不支持刷新的数据源故障排除](service-admin-troubleshoot-unsupported-data-source-for-refresh.md)。

## <a name="configure-scheduled-refresh"></a>配置计划刷新

配置数据刷新时，在 Power BI 和数据源之间建立连接是目前为止最具挑战性的任务。 其余步骤（包括设置刷新计划和启用刷新失败通知）相对来说比较简单。 有关分步说明，请参阅操作指南[配置计划刷新](refresh-scheduled-refresh.md)。

### <a name="setting-a-refresh-schedule"></a>设置刷新计划

可在“计划刷新”部分定义数据集的刷新频率和时间段  。 如前所述，如果数据集位于共享容量上，则可以配置每天最多 8 个时间段，如果位于 Power BI Premium 上，则可以配置每天最多 48 个时间段。 以下屏幕截图显示了时间间隔为 12 小时的刷新计划。

![配置计划刷新](media/refresh-data/configure-scheduled-refresh.png)

配置完刷新计划后，数据集设置页面会通知你下一个刷新时间，如上面的屏幕截图所示。 如果要加快数据刷新速度以执行网关和数据源配置测试等操作，请使用导航窗格的数据集菜单中的“立即刷新”选项进行按需刷新  。 按需刷新不会影响下一计划的刷新时间。

另请注意，配置的刷新时间可能不是 Power BI 启动下一个计划进程的确切时间。 Power BI 会尽最大努力启动计划刷新。 目标是在计划时间段的 15 分钟内启动刷新，但如果服务无法更快地分配所需资源，则可能会延迟最多一小时。

> [!NOTE]
> Power BI 会在连续四次失败后或当服务检测到需要配置更新的不可恢复错误（例如无效或过期的凭据）时停用刷新计划。 无法更改连续失败阈值。

### <a name="getting-refresh-failure-notifications"></a>获取刷新失败通知

默认情况下，Power BI 通过电子邮件将刷新失败通知发送给数据集所有者，以便在发生刷新问题时，所有者可以及时采取行动。 当服务因连续失败而禁用你的计划时，Power BI 也会向你发送通知。 Microsoft 建议将复选框“向我发送刷新失败通知电子邮件”保留为启用状态  。

也可以使用“刷新失败时，向这些用户发送电子邮件”文本框来指定其他收件人  。 除数据集所有者以外，指定收件人也会接收刷新失败通知。 可以是在你度假时处理你数据集的同事。 也可以是为你的部门或组织处理刷新问题的支持团队的电子邮件别名。 向除数据集所有者以外的其他人发送刷新失败通知有助于确保及时察觉和处理问题。

请注意，Power BI 不仅会在刷新失败时发送通知，还会在服务因数据集不活动而暂停计划刷新时发送通知。 两个月后，如果没有用户访问过基于数据集生成的任何仪表板或报表，Power BI 会将数据集视为不活动。 在这种情况下，Power BI 会向数据集所有者发送一封电子邮件，指出服务已暂停数据集的刷新计划。 有关此类通知的示例，请参阅以下屏幕截图。

![关于暂停刷新的电子邮件](media/refresh-data/email-paused-refresh.png)

若要恢复计划刷新，请访问使用此数据集生成的报表或仪表板，或使用“立即刷新”选项手动刷新数据集  。

### <a name="checking-refresh-status-and-history"></a>检查刷新状态和历史记录

除了失败通知之外，最好定期检查数据集是否存在刷新错误。 一种快速方法是查看工作区中的数据集列表。 有错误的数据集会显示一个小警告图标。 选中警告图标可获取附加信息，如以下屏幕截图所示。 有关解决特定刷新错误的详细信息，请参阅[刷新方案故障排除](refresh-troubleshooting-refresh-scenarios.md)。

![刷新状态警告](media/refresh-data/refresh-status-warning.png)

警告图标有助于指示当前的数据集问题，但偶尔检查刷新历史记录也不失为一个好办法。 顾名思义，通过刷新历史记录可以查看过去同步周期的成功或失败状态。 例如，网关管理员可能已更新一组过期的数据库凭据。 如以下屏幕截图所示，刷新历史记录显示受影响的刷新何时再次开始工作。

![刷新历史记录消息](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> 可以在数据集设置中找到显示刷新历史记录的链接。 也可以使用 [Power BI REST API](/rest/api/power-bi/datasets/getrefreshhistoryingroup) 以编程方式检索刷新历史记录。 通过使用自定义解决方案，可以集中监视多个数据集的刷新历史记录。

## <a name="automatic-page-refresh"></a>自动页面刷新

自动页面刷新针对报表页面执行，使用此功能，报表作者可以为页面中仅在使用页面时处于活动状态的视觉对象设置刷新间隔。 自动页面刷新仅适用于 DirectQuery 数据源。 最小刷新间隔取决于要在其中发布报表的工作区的类型，以及高级工作区的容量管理设置。

有关自动页面刷新的详细信息，请参阅[自动页面刷新](desktop-automatic-page-refresh.md)一文。


## <a name="best-practices"></a>最佳做法

若要确保报表和仪表板使用当前数据，定期检查数据集的刷新历史记录是可采用的最重要的最佳做法之一。 一旦发现问题，请及时解决，并在必要时跟进数据源所有者和网关管理员。

此外，请考虑以下建议，以便为数据集建立和维护可靠的数据刷新过程：

- 将刷新安排在较空闲的时间进行，特别是当数据集位于 Power BI Premium 上时。 如果在更宽的时间范围内分配数据集的刷新周期，则可以帮助避开可能过度占用可用资源的高峰时间段。 延迟启动刷新周期意味着资源过载。 如果 Premium 容量完全耗尽，Power BI 甚至有可能跳过刷新周期。
- 记住刷新限制。 如果源数据频繁更改或数据量很大，并且源中增加的负载以及对查询性能的影响是可接受的，则考虑使用 DirectQuery/LiveConnect 模式而不是导入模式。 避免不断刷新导入模式数据集。 但是，如[在 Power BI Desktop 中使用 DirectQuery](desktop-use-directquery.md) 所述，DirectQuery/LiveConnect 模式存在一些限制，例如返回数据的行数限制为一百万行，运行查询的响应时间限制为 225 秒。 这些限制可能会导致你仍然使用导入模式。 对于非常大的数据量，请考虑使用 [Power BI 中的聚合](desktop-aggregations.md)。
- 确保数据集刷新时间不超过最大刷新持续时间。 使用 Power BI Desktop 检查刷新持续时间。 如果需要超过 2 小时，请考虑将数据集移至 Power BI Premium。 数据集可能无法在共享容量上刷新。 另考虑对大于 1GB 或刷新时间长达几小时的数据集使用 [Power BI Premium 中的增量刷新](service-premium-incremental-refresh.md)。
- 优化数据集以仅包括报表和仪表板使用的表和列。 优化糅合查询，如有可能，避免使用动态数据源定义和高成本的 DAX 计算。 特别是避免使用测试表中每一行的 DAX 函数，因为这种函数的内存消耗和处理开销非常高。
- 应用与 Power BI Desktop 中相同的隐私设置，确保 Power BI 可以生成有效的源查询。 记住，Power BI Desktop 不会发布隐私设置。 发布数据集后，必须手动重新应用数据源定义中的设置。
- 限制仪表板上视觉对象的数量，尤其是在使用[行级别安全性 (RLS)](service-admin-rls.md) 时。 如本文前面所述，过多的仪表板磁贴会显著增加刷新持续时间。
- 使用可靠的企业数据网关部署将数据集连接到本地数据源。 如果发现与网关相关的刷新故障（例如网关不可用或过载），请让网关管理员向现有群集添加其他网关或部署新群集（纵向扩展与横向扩展），直至问题得到解决。
- 为导入数据集和 DirectQuery/LiveConnect 数据集使用不同的数据网关，以使计划刷新期间的数据导入不影响基于 DirectQuery/LiveConnect 数据集（通过每次用户交互查询数据源）的报表和仪表板的性能。
- 确保 Power BI 可以向你的邮箱发送刷新失败通知。 垃圾邮件筛选器可能会阻止电子邮件或将其移至你可能不会立即注意到的单独文件夹中。


## <a name="next-steps"></a>后续步骤

[配置计划刷新](refresh-scheduled-refresh.md)  
[用于解决刷新问题的工具](service-gateway-onprem-tshoot.md)  
[刷新方案故障排除](refresh-troubleshooting-refresh-scenarios.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

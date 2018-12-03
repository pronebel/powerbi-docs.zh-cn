---
title: 在 Power BI Desktop 中使用 DirectQuery
description: 在 Power BI Desktop 中使用 DirectQuery（亦称为“实时连接”）
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 350378be4a9e24b844cf1ad17133db65ab674573
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670477"
---
# <a name="use-directquery-in-power-bi-desktop"></a>在 Power BI Desktop 中使用 DirectQuery
使用 **Power BI Desktop** 时，若已连接数据源，始终可以将数据副本导入 **Power BI Desktop**。 对于某些数据源，还可使用另一种方法︰使用 **DirectQuery** 直接连接到数据源。

## <a name="supported-data-sources"></a>受支持的数据源
有关支持 DirectQuery 的数据源的完整列表，请参阅 [DirectQuery 支持的数据源](desktop-directquery-data-sources.md)。

## <a name="how-to-connect-using-directquery"></a>如何使用 DirectQuery 建立连接
当使用**获取数据**连接到受 **DirectQuery** 支持的数据源时，连接窗口将让你选择连接方式。  

![](media/desktop-use-directquery/directquery_2a.png)

**导入**选项和 **DirectQuery** 选项之间的差异如下︰

**导入** - 将选定的表和列导入 **Power BI Desktop** 中。 在你创建可视化效果或与之进行交互时，**Power BI Desktop** 需要使用导入的数据。 你必须刷新数据（这将导入完整的数据集）才能查看自初始导入或最近一次刷新以来基础数据所发生的任何更改。

**DirectQuery** - 不会将任何数据导入或复制到 **Power BI Desktop** 中。 对于关系源，选定的表和列显示在“字段”列表中。 对于 SAP Business Warehouse 等多维源，所选多维数据集的维度和度量值会显示在“字段”列中。 在你创建可视化效果或与之进行交互时，**Power BI Desktop** 会查询基础数据源。也就是说，你查看的始终都是最新数据。

在使用 **DirectQuery** 时许多数据建模和数据转换功能可用，但存在一些限制。 当创建可视化效果或与其互动时，必须查询基础数据源。刷新可视化效果所需的时间取决于基础数据源的性能。 当最近已请求为处理请求而必需的数据时，Power BI Desktop 将使用最近数据来减少显示可视化效果时所需的时间。 通过从**主页**功能区中选择**刷新**，将确保使用当前数据刷新所有可视化效果。

[Power BI 和 DirectQuery](desktop-directquery-about.md) 一文详细介绍了 DirectQuery。 另请参阅以下各节，详细了解使用 DirectQuery 的好处、限制条件和重要注意事项。

## <a name="benefits-of-using-directquery"></a>通过使用 DirectQuery 带来的好处
使用 **DirectQuery** 带来的几个好处是：

* DirectQuery 可使你在超大型数据集上生成可视化效果，除此之外将无法使用预聚合首先导入所有数据
* 对基础数据的更改可能需要刷新数据。对于某些报表，需显示当前数据，而这可能需要传输大量数据，使得重新导入的数据的操作变得不可行。 与此相反，**DirectQuery** 报表始终会使用当前数据
* 1 GB 的数据集限制*不*适用于 **DirectQuery**

## <a name="limitations-of-directquery"></a>DirectQuery 的限制
目前，在使用 **DirectQuery** 时存在一些限制：

* 所有表都必须来自单个数据库
* 如果“查询编辑器”查询过于复杂，将会出错。 要更正错误，必须在“查询编辑器”中删除有问题的步骤，或者导入数据，而不是使用 DirectQuery。 对于 SAP Business Warehouse 等多维度源而言，没有查询编辑器
* 关系筛选操作仅限于在单方向上执行，而不能在两个方向上执行（尽管可能要在 DirectQuery 的两个方向上启用作为预览功能的交叉筛选）。 对于 SAP Business Warehouse 等多维源而言，模型中未定义任何关系
* **DirectQuery** 不提供时间智能功能。 例如，**DirectQuery** 模式不支持日期列（年、季度、月、日等）的特殊处理方式。
* 默认情况下，会限制允许在度量值中使用的 DAX 表达式；请参阅下一段落（在此项目符号列表后）了解详细信息
* 使用 **DirectQuery** 时，返回数据有 100 万行的限制。 这不影响用于创建使用 **DirectQuery** 返回的数据集的聚合或计算，仅影响返回的行。 例如，你可以使用在数据源上运行的查询聚合 1000 万行，并且只要返回到 Power BI 的数据不超过 100 万行，即可使用 **DirectQuery** 将该聚合的结果准确地返回到 Power BI。 如果从 **DirectQuery** 返回的结果超过 100 万行，则 Power BI 返回错误。

为了确保发送到基础数据源的查询具有可接受的性能，默认情况下对度量值进行了限制。 高级用户可以选择绕过此限制，方法是依次选择“文件”>“选项和设置”>“选项”>“DirectQuery”，然后选择选项“允许 DirectQuery 模式下的度量值不受限制”。 选中该选项后，即可使用对度量值有效的任何 DAX 表达式。 但是，用户必须知道，可在导入数据的情况下正常工作的某些表达式，在 DirectQuery 模式下则可能会导致针对后端数据源的查询速度缓慢。

## <a name="important-considerations-when-using-directquery"></a>使用 DirectQuery 的重要注意事项
使用 **DirectQuery** 时，应考虑以下三点：

* **性能和负载** - 所有 **DirectQuery** 请求都会发送到源数据库，因此刷新视觉对象所需的时间取决于后端源响应查询结果所需的时间。 使用 **DirectQuery** 的视觉对象的建议响应时间（包括返回请求数据）应为 5 秒或更短，建议的最长结果响应时间为 30 秒。 超过此时间会使报表的用户体验变得令人无法接受的差。 此外，将报表发布到 Power BI 服务后，超过几分钟时间的任何查询将会超时，且用户将收到错误。
  
  还应当根据使用发布报表的 Power BI 用户数量，考虑源数据库的负载。 使用*行级安全性* (RLS) 也可能会产生显著的影响；多个用户共享的非 RLS 仪表板磁贴将导致对数据库的单个查询，但是，在仪表板磁贴上使用 RLS 意味着刷新一个磁贴需要*每个用户*一个查询，因而将显著增加源数据库负载，并可能会影响性能。
  
  Power BI 将创建尽可能高效的查询。 但是在某些情况下，生成的查询可能不能高效到避免失败的刷新。 其中一个示例是生成的查询将从后端数据源检索大量行（超过 100 万），在这种情况下会发生以下错误：
  
      The resultset of a query to external data source has exceeded
      the maximum allowed size of '1000000' rows.
  
  生成包含非常高的基数列的简单图表，聚合选项设置为*不汇总*。 视觉对象应只具有基数低于 100 万的列，或必须应用适当的筛选器。
* **安全** -使用发布报表的所有用户都使用发布到 Power BI 服务后输入的凭据连接到后端数据源。 这与导入数据的情况相同：所有用户会看到相同的数据，而不考虑后端源中定义的任何安全规则。 希望通过 DirectQuery 源实现每用户安全性的客户应使用 RLS。 [详细了解 RLS](service-admin-rls.md)。
* **支持的功能** - **DirectQuery** 模式不支持 **Power BI Desktop** 的所有功能，或对某些功能有限制。 此外，Power BI 服务中的某些功能（如*快速见解*）对使用 **DirectQuery** 的数据集不可用。 因此，决定是否使用 **DirectQuery** 时，应当考虑使用 **DirectQuery** 时这些功能的限制。   

## <a name="publish-to-the-power-bi-service"></a>发布到 Power BI 服务
通过**DirectQuery** 创建的报表可发布到 Power BI 服务。

如果使用的数据源不需要本地数据网关（Azure SQL 数据库、Azure SQL 数据仓库或 Redshift）则必须提供凭据，然后所发布的报表才能在 Power BI 服务中显示。

可以通过在 Power BI 中选择**设置**齿轮状图标然后选择**设置**来提供凭据。

![](media/desktop-use-directquery/directquery_3.png)

Power BI 将显示**设置**窗口。 在此窗口中，选择**数据集**选项卡，选择将使用 **DirectQuery** 的数据集，然后选择**编辑凭据**。

![](media/desktop-use-directquery/directquery_4.png)

在提供凭据之前，如果打开已发布的报表或浏览通过与此类数据源的 DirectQuery 连接创建的数据集，会导致出错。

对于除 Azure SQL 数据库、Azure SQL 数据仓库和 Redshift 外使用 DirectQuery 的数据源，必须安装本地数据网关，并且必须注册数据源才能建立数据连接。 可[了解有关本地数据网关的详细信息](http://go.microsoft.com/fwlink/p/?LinkID=627094)。

## <a name="next-steps"></a>后续步骤
有关 DirectQuery 的详细信息，请查看以下资源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支持的数据源](desktop-directquery-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [本地数据网关](service-gateway-onprem.md)


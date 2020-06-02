---
title: 在 Power BI Desktop 中使用增强的数据集元数据（预览）
description: 本文介绍了如何在 Power BI 中使用增强的数据集元数据。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 42e3f36689e62b196f5d8cb82bd4dd5ee118bf8b
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2020
ms.locfileid: "83793400"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>使用增强的数据集元数据（预览）

Power BI Desktop 创建报表时，还会使用相应的 PBIX 和 PBIT 文件创建数据集元数据。 以前，元数据以特定于 Power BI Desktop 的格式存储。 它使用 Base-64 编码的 M 表达式和数据源，并对元数据的存储方式进行了假设。

随着增强的数据集元数据功能的发布，许多这些限制都已消除。 启用增强的数据集元数据功能后，由 Power BI Desktop 创建的元数据根据[表格对象模型](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)使用与 Analysis Services 表格模型使用的格式相似的格式。


增强的数据集元数据功能具有战略性和基础性，因为未来的 Power BI 功能将基于其元数据构建。 始终都可从增强的数据集元数据中获益的一些其他功能包括用于管理 Power BI 数据集的 [XMLA 读/写](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)，以及将 Analysis Services 工作负载迁移到 Power BI 以受益于下一代功能。



## <a name="enable-enhanced-dataset-metadata"></a>启用增强的数据集元数据

增强的数据集元数据功能目前为预览版。 要启用增强的数据集元数据，请在 Power BI Desktop 中选择“文件”>“选项和设置”>“选项”>“预览功能”，然后选中“使用增强的元数据格式存储数据集”复选框，如下图所示 。 

![启用预览功能](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

系统会提示你重启 Power BI Desktop。

![重启提示](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

启用预览功能后，Power BI Desktop 会尝试升级使用以前的元数据格式的 PBIX 和 PBIT 文件。 

> [!IMPORTANT]
> 启用“增强型数据集元数据”功能会导致不可逆地升级报表。 在启用“增强型数据集元数据”后，任何使用 Power BI Desktop 加载或创建的 Power BI 报表都会不可逆地转换为增强型数据集元数据格式。

## <a name="report-backup-files"></a>报表备份文件

将报表更新为使用“增强的数据集元数据”功能是不可逆的。 但在更新过程中，会创建报表备份文件，以保存一个原始格式（更新前）的报表版本。 备份文件将在 30 天后删除。 

若要查找备份报表文件，请执行以下操作：

1. 导航到以下位置：```C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\TempSaves\Backup``` 如果使用 Power BI Desktop 的 Microsoft Store 版本，还可以使用以下位置：```C:\Users\<user>\Microsoft\Power BI Desktop Store App\TempSaves\Backups``` 

2. 使用原始文件的名称和时间戳查找报表的副本。

3. 将该文件复制到想要保留的位置。

4. 如果选择打开或使用原始文件，请确保在 Power BI Desktop 中禁用“增强的元数据格式”预览功能。 

备份文件是在升级报表时创建的，因此不包含升级之后所做的任何更改。 启用“增强的元数据格式”功能时创建的新报表没有备份文件。


## <a name="considerations-and-limitations"></a>注意事项和限制

在预览版中，启用预览功能时存在以下限制。

### <a name="unsupported-features-and-connectors"></a>不支持的功能和连接器
打开尚未升级的现有 PBIX 或 PBIT 文件时，如果数据集包含以下任何功能或连接器，则升级将失败。 如果发生此类失败，不会对用户体验产生直接影响，Power BI Desktop 继续使用以前的元数据格式。

* 所有自定义连接器
* Python 脚本
* 自定义连接器
* Azure DevOps Server
* BI 连接器
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* MarkLogic ODBC
* Qubole Presto
* Team Desk
* 列名中包含特定字符组合（例如“\\n”）的 M 表达式
* 使用启用了“增强的数据集元数据”功能的数据集时，无法在 Power BI 服务中设置单一登录 (SSO) 数据源

使用这些列出的连接器的报表不会升级为新格式。 对于已升级的报表或在启用此新功能之后创建的报表，将不支持添加所列出的不受支持的功能或连接器。 

不支持包含动态数据源的查询。 具有动态数据源的报表将不会升级为新格式，并且已升级的报表或在启用该功能的情况下新创建的报表将不支持添加动态数据源。 如果源随着参数、函数输入或可变函数而发生变化，则查询具有动态数据源。 

不支持在上游步骤或分支中出现错误的查询。 

此外，已成功升级为使用“增强的数据集元数据”的 PBIX 和 PBIT 文件无法在当前版本中使用上述功能或连接器。




### <a name="lineage-view"></a>世系视图
使用新元数据格式的数据集当前不会在 Power BI 服务的沿袭视图中显示指向数据流的链接。

## <a name="next-steps"></a>后续步骤

可以使用 Power BI Desktop 执行各种操作。 有关其功能的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的新增功能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop 的查询概述](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的数据类型](desktop-data-types.md)
* [使用 Power BI Desktop 成型和合并数据](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常见查询任务](../transform-model/desktop-common-query-tasks.md)

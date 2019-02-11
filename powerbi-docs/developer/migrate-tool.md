---
title: Power BI Embedded 迁移工具
description: 此迁移工具可用于将报表从 Power BI Embedded Azure 服务 (PaaS) 复制到 Power BI 服务 (SaaS)。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/30/2018
ms.openlocfilehash: 41ab7f06da3038e48e2d1188edc8b91edeee8d4f
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762343"
---
# <a name="power-bi-embedded-migration-tool"></a>Power BI Embedded 迁移工具

此迁移工具可用于将报表从 Power BI Embedded Azure 服务 (PaaS) 复制到 Power BI 服务 (SaaS)。

将内容从工作区集合迁移到 Power BI 服务可与当前解决方案同步进行，并且不需要停机。

## <a name="limitations"></a>限制

* 无法下载推送的数据集，需要使用 Power BI 服务的 Power BI REST API 重新创建。
* 2016 年 11 月 26 日前导入的 PBIX 文件将无法下载。

## <a name="download"></a>下载

可以从 [GitHub](https://github.com/Microsoft/powerbi-migration-sample) 下载迁移工具示例。 可以下载存储库的压缩文件，也可以将其复制到本地。 下载完成后，可以在 Visual Studio 中打开 powerbi-migration-sample.sln，以生成和运行迁移工具。

## <a name="migration-plans"></a>迁移计划

迁移计划涉及对 Power BI Embedded 中的内容编辑目录的元数据，以及希望以何种方式将其发布到 Power BI 服务。

### <a name="start-with-a-new-migration-plan"></a>开始新的迁移计划

迁移计划涉及 Power BI Embedded 中可用项的元数据，随后会将该元数据移动到 Power BI 服务。 迁移计划存储为 XML 文件。

首先需要新建一个迁移计划。 请执行以下操作新建迁移计划。

1. 选择“文件” > “新建迁移计划”。

    ![工具计划](media/migrate-tool/migrate-tool-plan.png)

2. 在“选择 Power BI Embedded 资源组”对话框中，建议选择“环境”下拉列表，然后选择“生产”。

3. 系统将提示你进行登录。 请使用 Azure 订阅登录名。

   > [!IMPORTANT]
   > 不是用于登录 Power BI 的 Office 365 组织帐户。

4. 选择存储着 Power BI Embedded 工作区集合的 Azure 订阅。

    ![资源组](media/migrate-tool/migrate-tool-select-resource-group.png)
5. 在订阅列表下，选择包含工作区集合的“资源组”，然后选择“选择”。

    ![选择资源组](media/migrate-tool/migrate-tool-select-resource-group2.png)

6. 选择“分析”。 此操作可以得出 Azure 订阅中的项的清单，方便开始执行计划。

    ![分析组](media/migrate-tool/migrate-tool-analyze-group.png)

   > [!NOTE]
   > 分析过程可能需要几分钟时间，具体取决于工作区集合的数量和工作区集合中存在内容的多少。

7. “分析”完成后，系统会提示保存迁移计划。

至此，已经将迁移计划连接到 Azure 订阅。 阅读以下内容，了解执行迁移计划的流程。 流程包括分析与计划迁移、下载、创建组和上传。

### <a name="save-your-migration-plan"></a>保存迁移计划

可以保存迁移计划供以后使用。 为此需要创建一个 XML 文件，在文件中包含迁移计划的所有信息。

执行以下操作保存迁移计划。

1. 选择“文件” > “保存迁移计划”。

    ![保存计划](media/migrate-tool/migrate-tool-save-plan.png)

2. 命名文件或使用生成的文件名，然后选择“保存”。

### <a name="open-an-existing-migration-plan"></a>打开现有的迁移计划

可以打开保存的迁移计划以继续执行迁移。

执行以下操作打开已保存的迁移计划。

1. 选择“文件” > “打开现有的迁移计划”。

    ![打开计划](media/migrate-tool/migrate-tool-open-plan.png)

2. 选择迁移文件，然后选择“打开”。

## <a name="step-1-analyze--plan-migration"></a>步骤 1：分析与计划迁移

可以在“分析与计划迁移”选项卡上查看 Azure 订阅的资源组中的现有内容。

![“分析与计划迁移”选项卡](media/migrate-tool/migrate-tool-step1.png)

此处以 *SampleResourceGroup* 为例。

### <a name="paas-topology"></a>PaaS 拓扑

PaaS 拓扑是“资源组”>“工作区集合”>“工作区”的列表。 资源组和工作区集合将显示友好名称。 工作区将显示 GUID。

列表中的项还会以 (#/#) 格式显示带颜色的数值。 数值表示可以下载的报表数。
黑色表示所有报表都可以下载。

红色表示有报表都不可下载。 左边的数值表示可以下载的报表总数。 右边的数值表示组内报表的总数。

可以选择 PaaS 拓扑内的某一项，然后在报表部分查看报表。

### <a name="reports"></a>报表

报表部分将列出可用的报表，并指示该报表是否可下载。

![分析报表](media/migrate-tool/migrate-tool-analyze-reports.png)

### <a name="target-structure"></a>目标结构

“目标结构”可指示工具将内容下载到哪里，以及如何上传内容。

#### <a name="download-plan"></a>下载计划

系统会自动创建路径。 可以根据需要更改路径。 如果确实更改路径，需要选择“更新路径”。

> [!NOTE]
> 此操作不会实际执行下载。 它只指定报表将要下载到的位置。

#### <a name="upload-plan"></a>上传计划

可以在这里指定 Power BI 服务中创建的应用工作区的前缀。 之后，该前缀将作为 Azure 中的工作区的 GUID。

![上传计划](media/migrate-tool/migrate-tool-upload-plan.png)

> [!NOTE]
> 此操作不会实际在 Power BI 服务中创建组。 它只会定义组的命名结构。

如果更改了前缀，则需要选择“生成上传计划”。

可以根据需要右键单击某个组，然后在上传计划中直接选择重命名该组。

![上传报表和重命名项](media/migrate-tool/migrate-tool-upload-report-rename-item.png)

> [!NOTE]
> 组名称不能包含空格或无效字符。

## <a name="step-2-download"></a>步骤 2：下载

在“下载”选项卡上可以看到报表和关联元数据的列表。 可以查看现在的导出状态和以前的导出状态。

![](media/migrate-tool/migrate-tool-download-tab.png)

有两个选项。

* 选择特定报表，然后选择“下载选定报表”。
* 选择“全部下载”。

![下载选项](media/migrate-tool/migrate-tool-download-options.png)

下载成功后会显示“完成”状态，该状态表示存在 PBIX 文件。

下载完成后，选择“创建组”选项卡。

## <a name="step-3-create-groups"></a>步骤 3：创建组

下载可用报表后，可以转到“创建组”选项卡。此选项卡将根据之前创建的迁移计划在 Power BI 服务内创建应用工作区。 它会使用“分析与计划迁移”中“上传”选项卡上提供的名称创建应用工作区。

![创建组](media/migrate-tool/migrate-tool-create-groups.png)

若要创建应用工作区，可以选择“创建所选组”或“创建所有缺少的组”。

选择任何一个选项后，系统都将提示你进行登录。 为在 Power BI 服务上创建应用工作区，建议使用 Power BI 服务的凭据。

![创建组登录](media/migrate-tool/migrate-tool-create-group-sign-in.png)

此操作会在 Power BI 服务中创建应用工作区。 但不会将报表上传到应用工作区。

可以登录 Power BI 并验证是否存在工作区，以此来验证是否已创建应用工作区。 这时可以看到工作区中不存在任何内容。

![应用工作区](media/migrate-tool/migrate-tool-app-workspace.png)

创建工作区后，可以移到“上传”选项卡。

## <a name="step-4-upload"></a>步骤 4：上传

在“上传”选项卡上进行操作可以将报表上传到 Power BI 服务。 在此可以看到之前在“下载”选项卡上下载的一系列报表，以及基于迁移计划的目标组名称。

![上传选项卡](media/migrate-tool/migrate-tool-upload-tab.png)

可以上传选定报表，也可以上传所有报表。 也可以将上传状态重置为重新上传项。

如果存在具有相同名称的报表，可以选择要执行的操作。 可以选择“中止”、“忽略”和“覆盖”。

![上传报表相同名称](media/migrate-tool/migrate-tool-upload-report-same-name.png)

![上传选定内容](media/migrate-tool/migrate-tool-upload-selected.png)

### <a name="duplicate-report-names"></a>重复的报表名称

如果某个报表与之前的报表名称相同，但你知道其内容不同，则需要更改此报表的“TargetName”。 可以通过手动编辑迁移计划 XML 来更改名称。

需要关闭迁移工具进行更改，然后重新打开工具和迁移计划。

在上面的示例中，有一个复制报表失败，其原因是存在具有相同名称的报表。 如果查看迁移计划 XML，可以看到以下内容。

```
<ReportMigrationData>
    <PaaSWorkspaceCollectionName>SampleWorkspaceCollection</PaaSWorkspaceCollectionName>
    <PaaSWorkspaceId>4c04147b-d8fc-478b-8dcb-bcf687149823</PaaSWorkspaceId>
    <PaaSReportId>525a8328-b8cc-4f0d-b2cb-c3a9b4ba2efe</PaaSReportId>
    <PaaSReportLastImportTime>1/3/2017 2:10:19 PM</PaaSReportLastImportTime>
    <PaaSReportName>cloned</PaaSReportName>
    <IsPushDataset>false</IsPushDataset>
    <IsBoundToOldDataset>false</IsBoundToOldDataset>
    <PbixPath>C:\MigrationData\SampleResourceGroup\SampleWorkspaceCollection\4c04147b-d8fc-478b-8dcb-bcf687149823\cloned-525a8328-b8cc-4f0d-b2cb-c3a9b4ba2efe.pbix</PbixPath>
    <ExportState>Done</ExportState>
    <LastExportStatus>OK</LastExportStatus>
    <SaaSTargetGroupName>SampleMigrate</SaaSTargetGroupName>
    <SaaSTargetGroupId>6da6f072-0135-4e6c-bc92-0886d8aeb79d</SaaSTargetGroupId>
    <SaaSTargetReportName>cloned</SaaSTargetReportName>
    <SaaSImportState>Failed</SaaSImportState>
    <SaaSImportError>Report with the same name already exists</SaaSImportError>
</ReportMigrationData>
```

建议更改失败项的 SaaSTargetReportName 名称。

```
<SaaSTargetReportName>cloned2</SaaSTargetReportName>
```

然后在迁移工具中重新打开该计划，并上传之前失败的报表。

回到 Power BI，可以看到报表和数据集已上传到应用工作区中。

![上传应用工作区](media/migrate-tool/migrate-tool-upload-app-workspace.png)

<a name="upload-local-file"></a>

### <a name="upload-a-local-pbix-file"></a>上传本地 PBIX 文件

可以上传本地版本的 Power BI Desktop 文件。 需要关闭工具、编辑 XML 并在“PbixPath”属性中输入本地 PBIX 的完整路径。

```
<PbixPath>[Full Path to PBIX file]</PbixPath>
```

编辑 xml 后，在迁移工具中重新打开计划并上传报表。

<a name="directquery-reports"></a>

### <a name="directquery-reports"></a>DirectQuery 报表

需要进行更新，以便更新 DirectQuery 报表的连接字符串。 在 powerbi.com 中完成此操作，也可以通过编程方式从 Power BI Embedded (Paas) 查询连接字符串。 有关示例，请参阅[从 PaaS 报表提取 DirectQuery 连接字符串](migrate-code-snippets.md#extract-directquery-connection-string-from-paas-report)。

然后可以在 Power BI 服务 (Saas) 中更新数据集的连接字符串，并设置数据源的凭据。 请参阅以下示例，了解如何执行此操作。

* [在 SaaS 工作区中更新 DirectQuery 连接字符串](migrate-code-snippets.md#update-directquery-connection-string-is-saas-workspace)
* [在 SaaS 工作区中设置 DirectQuery 凭据](migrate-code-snippets.md#set-directquery-credentials-in-saas-workspace)

## <a name="embedding"></a>嵌入

将报表从 Power BI Embedded Azure 服务迁移到 Power BI 服务之后，现在可以更新应用程序，并将报表嵌入此应用工作区中。

有关详细信息，请参阅[如何将 Power BI Embedded 工作区集合内容迁移到 Power BI](migrate-from-powerbi-embedded.md)。

## <a name="next-steps"></a>后续步骤

[使用 Power BI 嵌入](embedding.md)  
[如何将 Power BI Embedded 工作区集合内容迁移到 Power BI](migrate-from-powerbi-embedded.md)  
[什么是 Power BI Premium？](../service-premium.md)  
[JavaScript API Git 存储库](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git 存储库](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript 嵌入示例](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Power BI Premium 白皮书](https://aka.ms/pbipremiumwhitepaper)  

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
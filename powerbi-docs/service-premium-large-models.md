---
title: Power BI Premium 中的大型模型（预览）
description: 大型模型功能允许 Power BI Premium 中的数据集的大小超过 10 GB。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/03/2020
LocalizationGroup: Premium
ms.openlocfilehash: 007ff786fcee5d2a7b7237ad578a202cfcf25b69
ms.sourcegitcommit: 743167a911991d19019fef16a6c582212f6a9229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78401932"
---
# <a name="large-models-in-power-bi-premium-preview"></a>Power BI Premium 中的大型模型（预览）

Power BI 数据集可以在高度压缩的内存中缓存中存储数据，以便优化查询性能，从而在大型数据集上实现快速的用户交互性。 大型模型功能允许 Power BI Premium 中的数据集的大小超过 10 GB。 相反，数据集的大小受 Power BI Premium 容量大小的限制，这与 Azure Analysis Services 的模型大小限制类似。 有关 Power BI Premium 中的容量大小的详细信息，请参阅容量节点。 可以为所有 Premium P SKU 和 Embedded A SKU 设置大型模型；但它们仅适用于[新工作区](service-create-the-new-workspaces.md)。

大型模型不会影响 PBIX 上传大小，该大小仍限制为 10 GB。 然而刷新后，服务中的数据集将超过 10 GB。 可以使用增量刷新将数据集配置为可超过 10 GB。

## <a name="enable-large-models"></a>启用大型模型

若要创建超过 10 GB 的数据集，请按以下步骤操作：

1. 在 Power BI Desktop 中创建数据集，并配置[增量刷新](service-premium-incremental-refresh.md)。

1. 将数据集发布到 Power BI Premium 服务。

1. 运行以下 PowerShell cmdlet 允许数据集使用大型模型。 这些 cmdlet 会导致 Power BI 将数据集存储在 Azure 高级文件上，而不是强制实施 10 GB 的限制。

1. 调用刷新以加载基于增量刷新策略的历史记录数据。 第一次刷新可能需要一些时间来加载历史记录。 后续刷新速度应该会更快，因为是增量刷新。

### <a name="powershell-cmdlets"></a>PowerShell cmdlet

在最新版本的大型模型中，使用 PowerShell cmdlet 允许数据集使用高级文件存储。 若要运行 PowerShell cmdlet，必须拥有容量管理员和工作区管理员权限。

1. 查找数据集 ID (GUID)。 在工作区“数据集”选项卡的“数据集设置”下方，可以看到 URL 中的 ID  。

    ![数据集 GUID](media/service-premium-large-models/dataset-guid.png)

1. 从 PowerShell 管理员提示符，安装 [MicrosoftPowerBIMgmt](/powershell/module/microsoftpowerbimgmt.data/) 模块。

    ```powershell
    Install-Module -Name MicrosoftPowerBIMgmt
    ```

1. 运行以下 cmdlet 以登录并检查数据集存储模式。

    ```powershell
    Login-PowerBIServiceAccount

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    响应应如下所示。 存储模式为 ABF（Analysis Services 备份文件），这是默认设置。

    ```
    Id                   StorageMode

    --                   -----------

    <Dataset ID>         Abf
    ```

1. 运行以下 cmdlet，将存储模式设置为“高级文件”并选中它。 转换为“高级文件”可能需要几秒钟。

    ```powershell
    Set-PowerBIDataset -Id <Dataset ID> -TargetStorageMode PremiumFiles

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    响应应如下所示。 现在，存储模式已设置为“高级文件”。

    ```
    Id                   StorageMode
    
    --                   -----------
    
    <Dataset ID>         PremiumFiles
    ```

可以使用 [Get-PowerBIWorkspaceMigrationStatus](/powershell/module/microsoftpowerbimgmt.workspaces/get-powerbiworkspacemigrationstatus) cmdlet 检查数据集转为使用和转为不使用“高级文件”的状态。

## <a name="dataset-eviction"></a>数据集逐出

Power BI 使用动态内存管理从内存中逐出不活动的数据集。 Power BI 逐出数据集，以便加载其他数据集来处理用户查询。 动态内存管理允许数据集大小的总和远超过容量中的可用内存，但单个数据集必须符合内存大小要求。 有关动态内存管理的详细信息，请参阅[容量工作原理](service-premium-what-is.md#how-capacities-function)。

应考虑大型模型中逐出的影响。 尽管数据集加载速度相对增加，但如果用户必须等待重新加载已逐出的大型数据集，则可能仍会出现明显的延迟。 出于此原因，在其当前窗体中，建议主要将大型模型功能用于专用于企业 BI 要求的容量，而不将其用于与自助 BI 要求混合的容量。 专用于企业 BI 要求的容量较不可能由于频繁触发逐出而需要重新加载数据集。 另一方面，用于自助 BI 的容量可以拥有许多更频繁地加载和逐出内存的小型数据集。

## <a name="checking-dataset-size"></a>检查数据集大小

加载历史记录数据后，可以通过 [XMLA 终结点](service-premium-connect-tools.md)使用 [SSMS](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 在模型属性窗口中检查估计的数据集大小。

![估计的数据集大小](media/service-premium-large-models/estimated-dataset-size.png)

还可以从 SSMS 运行以下 DMV 查询来检查数据集大小。 对输出中的 DICTIONARY\_SIZE 和 USED\_SIZE 列求和，得出以字节为单位的数据集大小。

```sql
SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMNS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum DICTIONARY_SIZE (bytes)

SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum USED_SIZE (bytes)
```

## <a name="limitations-and-considerations"></a>限制和注意事项

使用大型模型时，记住以下限制：

- **创建自己的密钥 BYOK 加密**：启用了“高级文件”的数据集不通过 [BYOK](service-encryption-byok.md) 进行加密。
- **Multi-Geo 支持**：如果同时启用了 [multi-geo](service-admin-premium-multi-geo.md)，启用了“高级文件”的数据集将出现容量故障。

- **下载到 Power BI Desktop**：如果数据集存储在高级文件中，[下载为 .pbix](service-export-to-pbix.md) 文件将失败。
- **支持的区域**：支持高级文件存储的所有 Azure 区域都支持大型模型。 若要了解详细信息，请参阅[按区域提供的产品](https://azure.microsoft.com/global-infrastructure/services/?products=storage)，并参考以下部分中的表格。


## <a name="availability-in-regions"></a>区域可用性

Power BI 中的大型模型只在支持 [Azure 高级文件存储](https://docs.microsoft.com/azure/storage/files/storage-files-planning#storage-tiers)的特定 Azure 区域中可用。

以下列表提供了可以使用 Power BI 中的大型模型的区域。 未在以下列表中列出的区域不支持使用大型模型：


|Azure 区域  |Azure 区域缩写  |
|---------|---------|
|澳大利亚东部     | australiaeast        |
|澳大利亚东南部     | australiasoutheast        |
|美国中部     | centralus        |
|东亚     | eastasia        |
|美国东部     | eastus        |
|美国东部 2     | eastus2        |
|日本东部     | japaneast        |
|日本西部     | japanwest        |
|韩国中部     | koreacentral        |
|韩国南部     | koreasouth        |
|美国中北部     | northcentralus        |
|北欧     | northeurope        |
|美国中南部     | southcentralus        |
|东南亚     | southeastasia        |
|英国南部     | uksouth        |
|英国西部     | ukwest        |
|西欧     | westeurope        |
|美国西部     | westus        |
|美国西部 2     | westus2        |



## <a name="next-steps"></a>后续步骤

以下链接提供了与使用大型模型相关的有用信息：

* [Azure 高级文件存储](https://docs.microsoft.com/azure/storage/files/storage-files-planning#storage-tiers)
* [配置 Power BI Premium 的 Multi-Geo 支持](service-admin-premium-multi-geo.md)
* [对 Power BI 创建自己的加密密钥](service-encryption-byok.md)
* [容量工作原理](service-premium-what-is.md#how-capacities-function)
* [增量刷新](service-premium-incremental-refresh.md)。
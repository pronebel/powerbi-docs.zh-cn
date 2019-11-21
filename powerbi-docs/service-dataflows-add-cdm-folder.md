---
title: 将 CDM 文件夹添加到 Power BI 作为数据流
description: 将工作区配置为在 Azure Data Lake Storage Gen2 中存储其数据流定义文件和数据文件
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5b6b8658e4480173c32a591c2fc763a238cfd13a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872692"
---
# <a name="add-a-cdm-folder-to-power-bi-as-a-dataflow-preview"></a>将 CDM 文件夹添加到 Power BI 作为数据流（预览）

在 Power BI 中，可以添加存储在组织的 Azure Data Lake Store Gen2 中的 Common Data Model (CDM) 文件夹作为数据流。 从 CDM 文件夹创建数据流后，则可以基于置于 CDM 文件夹的数据使用 Power BI Desktop 和 Power BI 服务创建数据集、报表、仪表板和应用。  

![CDM 文件夹中的数据流](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

下面列出了从 CDM 文件夹创建数据流的几个要求：

* 从 CDM 文件夹创建数据流  仅适用于[新的工作区体验](service-create-the-new-workspaces.md)。 
* 将 CDM 文件夹添加到 Power BI 要求用户添加文件夹以便拥有 [CDM 文件夹及其文件的授权](https://go.microsoft.com/fwlink/?linkid=2029121)。
* 必须授予对 CDM 文件夹中的所有文件和文件夹的读取和执行权限，以便将其添加到 Power BI。

以下部分介绍了如何从 CDM 文件夹创建数据流。

## <a name="create-a-dataflow-from-a-cdm-folder"></a>从 CDM 文件夹创建数据流

若要开始从 CDM 文件夹创建数据流，请启动“Power BI 服务”，然后从导航窗格中选择“工作区”   。 也可以新建一个工作区，可用于创建新的工作流。

![在 Power BI 服务中创建数据流](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_02.jpg)

在显示的屏幕中，选择如下图所示的“创建并附加”  。

![创建并附加新数据流](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_03.jpg)

接下来显示的屏幕可让你命名数据流，提供数据流的说明，并提供组织的 Azure Data Lake Gen2 帐户中的 CDM 文件夹的路径。 阅读本文中介绍[如何获取 CDM 文件夹路径](service-dataflows-configure-workspace-storage-settings.md#get-the-uri-of-stored-dataflow-files)的部分。 

![CDM 文件夹中的数据流](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

提供信息后，请选择“创建并附加”  以创建数据流。

CDM 文件夹中的数据流显示在 Power BI 中时标有  “外部”图标。 在下一部分中，我们将介绍标准数据流与 CDM 文件夹中创建的数据流之间的差异。

按本文前面所述正确设置权限后，可以在 Power BI Desktop 中连接到数据流  。


## <a name="considerations-and-limitations"></a>注意事项和限制

使用 CDM 文件夹中创建的数据流的权限时，该过程类似于 Power BI 中的外部数据源。 权限在数据源中（而不是在 Power BI 中）进行管理。 必须在数据源本身（例如 CDM 文件夹中创建的数据流）中正确设置权限，才能正确使用 Power BI。

以下列表可帮助说明如何使用 Power BI 运行 CDM 文件夹中的数据流。

Power BI Pro、Premium 和 Embedded 工作区：
* 无法编辑 CDM 文件夹中的数据流
* 读取 CDM 文件夹中创建的数据流的权限由 CDM 文件夹的所有者（而不是 Power BI）管理

Power BI Desktop：
* 只有有权访问创建数据流的工作区和 CDM 文件夹的用户才能从 Power BI 数据流连接器访问其数据


下面还列出了一些其他注意事项：

* 从 CDM 文件夹创建数据流  仅适用于[新的工作区体验](service-create-the-new-workspaces.md)
* 链接实体不适用于 CDM 文件夹中创建的数据流


 Power BI Desktop 客户无法访问存储在 Azure Data Lake Storage Gen2 帐户中的数据流，除非他们是数据流的所有者，或者他们已被显式授权访问数据流的 CDM 文件夹。 请考虑以下情况：

1.  Anna 创建了一个新的工作区，并将其配置为存储 CDM 文件夹中的数据流。
2.  Ben 也是 Anna 所创建工作区的成员，他希望利用 Power BI Desktop 和数据流连接器从 Anna 创建的数据流获取数据。
3.  Ben 收到一个错误，因为他没有被添加为 Data Lake 中数据流的 CDM 文件夹的授权用户。

    ![尝试使用数据流时出错](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

要解决此问题，必须授予 Ben 对 CDM 文件夹及其文件的读取权限。 可以在[本文](https://go.microsoft.com/fwlink/?linkid=2029121)中了解有关如何授予 CDM 文件夹访问权限的详细信息。


## <a name="next-steps"></a>后续步骤

本文提供了有关如何配置数据流的工作区存储的指南。 有关详细信息，请参阅以下文章：

有关数据流、CDM 和 Azure Data Lake Storage Gen2 的详细信息，请参阅以下文章：

* [数据流和 Azure Data Lake 集成（预览）](service-dataflows-azure-data-lake-integration.md)
* [配置工作区数据流设置（预览）](service-dataflows-configure-workspace-storage-settings.md)
* [连接 Azure Data Lake Storage Gen2 以存储数据流（预览）](service-dataflows-connect-azure-data-lake-storage-gen2.md)

有关总体数据流的信息，请查看以下这些文章：

* [在 Power BI 中创建和使用数据流](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用计算实体](service-dataflows-computed-entities-premium.md)
* [将数据流与本地数据源配合使用](service-dataflows-on-premises-gateways.md)
* [Power BI 数据流的开发人员资源](service-dataflows-developer-resources.md)

有关 Azure 存储的详细信息，可以阅读以下这些文章：
* [Azure 存储安全指南](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [配置计划刷新](refresh-scheduled-refresh.md)
* [开始使用 Azure 数据服务中的 github 示例](https://aka.ms/cdmadstutorial)

有关通用数据模型的详细信息，可以阅读其概述文章：
* [通用数据模型 - 概述](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM 文件夹](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM 模型文件定义](https://go.microsoft.com/fwlink/?linkid=2045521)

也可以随时尝试[通过 Power BI 社区提问](https://community.powerbi.com/)。


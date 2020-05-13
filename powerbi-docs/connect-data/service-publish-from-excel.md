---
title: 从 Microsoft Excel 发布到 Power BI
description: 了解如何将 Excel 工作簿发布到 Power BI 站点。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ca3e954f64665798c439fba47c3135e93fe51ac0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83305602"
---
# <a name="publish-to-power-bi-from-microsoft-excel"></a>从 Microsoft Excel 发布到 Power BI
使用 Microsoft Excel 2016 及更高版本，可以将 Excel 工作簿直接发布到 [Power BI](https://powerbi.microsoft.com) 工作区，在其中能够根据工作簿数据创建高度交互的报表和仪表板。 然后你可以与组织中的其他人共享你的见解。

![将工作簿发布到 Power BI](media/service-publish-from-excel/pbi_uploadexport2.png)

将工作簿发布到 Power BI 时，需要注意以下几点：

* 用于登录 Office、OneDrive for Business（若要使用其中保存的工作簿）和 Power BI 的帐户必须相同。
* 不能发布空工作簿，也不能发布没有任何 Power BI 支持的内容的工作簿。
* 不能发布加密或受密码保护的工作簿，或具有信息保护管理的工作簿。
* 发布到 Power BI 需要启用新式验证（默认）。 如果禁用，“文件”菜单中将不会出现“发布”选项。

## <a name="publish-your-excel-workbook"></a>发布 Excel 工作簿
若要发布 Excel 工作簿，请在 Excel 中依次选择“文件”   > “发布”  ，然后选择“上传”  或“导出”  。

如果选择“上传”  将工作簿上传到 Power BI，可以与工作簿交互，就像使用 Excel Online 进行交互一样。 还可以将工作簿中的选定内容固定到 Power BI 仪表板，并通过 Power BI 共享工作簿或选定元素。

如果选择“导出”  ，可以将表数据及其数据模型导出到 Power BI 数据集中，然后可以使用数据集来创建 Power BI 报表和仪表板。

### <a name="local-file-publishing"></a>本地文件发布
Excel 支持发布本地 Excel 文件。 不需要将文件保存到 OneDrive for Business 或 SharePoint Online。

> [!IMPORTANT]
> 仅在结合使用 Excel 2016（或更高版本）与 Office 365 订阅时，才能发布本地文件。 只有在工作簿保存到 OneDrive for Business 或 SharePoint Online 时，Excel 2016 独立安装才支持“发布到 Power BI”。
> 

选择“发布”  时，可以选择要将文件发布到哪个工作区。 如果 Excel 文件位于 OneDrive for Business 上，则只能发布到“我的工作区”  。 如果 Excel 文件位于本地驱动器上，则可以发布到“我的工作区”或你有权访问的共享工作区  。

![发布到 Power BI](media/service-publish-from-excel/pbi_choose_workspace.png)

用于将工作簿发布到 Power BI 的选项有两个。

![发布到 Power BI](media/service-publish-from-excel/pbi_uploadexport3.png)

发布后，你发布的工作簿内容就会导入到 Power BI 中，与本地文件分隔开来。 若要更新 Power BI 中的文件，必须重新发布更新后的版本，也可以通过对工作簿或 Power BI 中的数据集配置计划刷新来刷新数据。

### <a name="publishing-from-a-standalone-excel-installation"></a>从独立 Excel 安装进行发布
必须将工作簿保存到 OneDrive for Business，才能从独立 Excel 安装进行发布。 依次选择“保存到云”  和 OneDrive for Business 中的位置。

![保存到 OneDrive for Business](media/service-publish-from-excel/pbi_savetoonedrive2.png)

将工作簿保存到 OneDrive for Business 后，选择“发布”  便会看到两个将工作簿导入到 Power BI 的选项，即“上传”  或“导出”  ：

![将工作簿导入到 Power BI 的选项](media/service-publish-from-excel/pbi_uploadexport2.png)

#### <a name="upload-your-workbook-to-power-bi"></a>将工作簿上传到 Power BI
如果你选择“上传”  选项，工作簿就会显示在 Power BI 中，就像在 Excel Online 中一样。 但与 Excel Online 不同的是，有一些可用于将工作表中的元素固定到仪表板的选项。

不能在 Power BI 中编辑你的工作簿。 如果需要对数据进行一些更改，可以选择“编辑”  ，然后选择是在 Excel Online 中编辑工作簿，还是在计算机上的 Excel 中打开工作簿。 所做的任何更改都会保存到 OneDrive for Business 上的工作簿中。

选择“上传”  时，不会在 Power BI 中创建任何数据集。 你的工作簿将显示在工作区导航窗格的“报表”中。 上传到 Power BI 的工作簿具有特殊的 Excel 图标，该图标将其标识为已上传的 Excel 工作簿。

如果工作表中只有数据，或要在 Power BI 中查看数据透视表和图表，请选择“上传”  。

使用 Excel 内“发布到 Power BI”中的“上传”选项类似于在浏览器中使用 Power BI 的“获取数据”>“文件”>“OneDrive for Business”>“在 Power BI 中连接、管理和查看 Excel”  体验。

#### <a name="export-workbook-data-to-power-bi"></a>将工作簿数据导出到 Power BI
如果你选择“导出”  选项，表和/或数据模型中的所有受支持数据都会导入到 Power BI 中的新数据集中。 工作簿中的所有 Power View 工作表都在 Power BI 中重新创建为报表。

你可以继续编辑工作簿。 保存后，你所做的更改便会与 Power BI 中的数据集同步（通常大约在一小时内完成）。 如果需要进行更多即时更新，可以再次选择 Excel 中的“发布”  ，所做的更改就会立即导出。 报表和仪表板中的所有可视化效果也会更新。

如果你已使用“获取并转换数据”或 Power Pivot 功能将数据加载到数据模型中，或者如果工作簿的 Power View 表中包含你要在 Power BI 中查看的可视化效果，请选择“发布”  选项。

使用“导出”  非常类似于在浏览器中使用 Power BI 的“获取数据”>“文件”>“OneDrive for Business”>“将 Excel 数据导出到 Power BI”  体验。

## <a name="publishing"></a>发布
在你选择两个选项之一后，Excel 会使用你的当前帐户登录 Power BI，然后将你的工作簿发布到 Power BI 工作区。 可以监视 Excel 中的状态栏，以查看发布进度。

![“发布到 Power BI”的状态栏](media/service-publish-from-excel/pbi_publishingstatus.png)

完成后，可以直接从 Excel 转到 Power BI。

![转到 Power BI](media/service-publish-from-excel/pbi_gotopbi.png)

## <a name="next-steps"></a>后续步骤
[Power BI 中的 Excel 数据](service-excel-workbook-files.md)  
更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)


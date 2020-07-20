---
title: 从逗号分隔值 (.CSV) 文件中获取数据。
description: 了解如何将数据从 CSV 文件导入到 Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 20c289648dc6e9b9784335c0d92f6725328dfffc
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216334"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>从逗号分隔值 (.CSV) 文件中获取数据。
![CSV 图标](media/service-comma-separated-value-files/csv_icon.png)

逗号分隔值文件（通常称为 .CSV）是简单的文本文件，其中数据行中的每个值用逗号隔开。 这些类型的文件可以在相对较小的文件中包含大量数据，使其成为 Power BI的理想数据源。 你可以在[此处](https://go.microsoft.com/fwlink/?LinkID=619356)下载一个示例 .CSV 文件。

如果你已有 .CSV 文件，现在就可以将其作为数据集导入到你的 Power BI 网站，在其中你可以开始浏览数据、创建一些仪表板，并与他人共享你的见解。

>[!TIP]
>很多组织使用每天更新的数据输出 .CSV。 若要确保 Power BI 中的数据集与更新后的文件保持同步，请确保该文件以相同的名称保存到 OneDrive 中。

## <a name="where-your-file-is-saved-makes-a-difference"></a>保存文件的位置不同会有所差异
**本地** -如果你将 .CSV 文件保存到计算机上的本地驱动器中或者组织中的其他位置，则在 Power BI 中，你可以将文件导入到 Power BI。 你的文件实际上一直保存在本地驱动器中，因此整个文件并未真正导入到 Power BI。 实际情况则是在 Power BI 中创建的新数据集以及 .CSV 中的数据会加载到数据集中。

**OneDrive - 企业** – 如果你有 OneDrive for Business，并且使用登录 Power BI 的同一帐户登录到其中，这是将 .CSV 文件与你在 Power BI 中的数据集、报表和仪表板保持同步的有史以来最有效的方法。由于 Power BI 和 OneDrive 都位于云中，Power BI 大约每小时会连接你在 OneDrive 上的文件一次。 如果发现任何更改，你的数据集、报表和仪表板会在 Power BI 中自动更新。

**OneDrive - 个人** – 如果你将文件保存到自己的 OneDrive 帐户，你会像使用 OneDrive for Business 那样获得很多相同优势。 最大的不同之处在于，当你首次连接至你的文件（使用“获取数据 > 文件 > OneDrive – 个人”）时，你将需要使用 Microsoft 帐户登录 OneDrive，这通常与你用于登录 Power BI 的帐户不同。 当使用你的 Microsoft 帐户登录 OneDrive 时，请务必选择“使我保持登录状态”选项。 这样一来，Power BI 将能够大约每小时连接你的文件一次，并确保你在 Power BI 中的数据集同步。

**SharePoint 团队网站** – 将 Power BI Desktop 文件保存到 SharePoint 团队网站与保存到 OneDrive for Business 大致相同。 最大的区别是你从 Power BI 连接到文件的方式。 你可以指定一个 URL 或连接到根文件夹。

## <a name="import-or-connect-to-a-csv-file"></a>导入或连接到 .CSV 文件
>[!IMPORTANT]
>可以导入 Power BI 的最大文件大小为 1 千兆字节。

1. 在 Power BI 中的导航窗格中，单击“获取数据”。
   
   ![Power BI Desktop 中“获取数据”的屏幕截图，其中显示了导航窗格中的按钮。](media/service-comma-separated-value-files/csv_get_data_button.png)
2. 在“文件”中，单击“获取”。
   
   ![“文件”对话框的屏幕截图，其中显示了“获取”按钮。](media/service-comma-separated-value-files/csv_files_get.png)
3. 查找你的文件。
   
   ![用于查找文件的四个磁贴的屏幕截图，其中显示了本地文件、OneDrive Business、OneDrive Personal 和 SharePoint。](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>后续步骤
**浏览你的数据** - 将文件中的数据导入 Power BI 后，就可以浏览文件了。 只需右键单击新的数据集，然后单击“浏览”。

**计划刷新** - 如果你的文件保存到本地驱动器中，你可以设置计划刷新，以便让 Power BI 中的数据集和报表保持最新状态。 若要了解详细信息，请参阅 [Power BI 中的数据刷新](refresh-data.md)。 如果你的文件保存到 OneDrive 中，Power BI 将大约每小时自动与该文件同步一次。


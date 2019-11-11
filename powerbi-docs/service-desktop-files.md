---
title: 从 Power BI Desktop 文件获取数据
description: 了解如何将数据和报表从 Power BI Desktkop 导入 Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ea5e4a4af3f4049ccb9d69fbe95a13dc08a8cf05
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877109"
---
# <a name="get-data-from-power-bi-desktop-files"></a>从 Power BI Desktop 文件获取数据
![](media/service-desktop-files/pbid_file_icon.png)

借助 **Power BI Desktop**，可以轻松处理商业智能任务和报表。 无论你是要连接众多类型的数据源、查询和转换数据、对数据进行建模，还是要生成功能强大的动态报表，**Power BI Desktop** 可方便你直观、快速地执行商业智能任务。 如果你不熟悉 **Power BI Desktop**，请参阅 [Power BI Desktop 入门](desktop-getting-started.md)。

将数据导入 **Power BI Desktop** 并生成几个报表后，即可将保存的文件导入 **Power BI 服务**。

## <a name="where-your-file-is-saved-makes-a-difference"></a>保存文件的位置具有重要意义
**本地** - 如果你将文件保存到计算机上的本地驱动器中或者组织中的其他位置，则可导入  或从 Power BI Desktop 发布  文件，以便将其数据和报表加入 Power BI。 你的文件实际上一直保存在本地驱动器中，因此整个文件并未真正移动到 Power BI。 实际上，在 Power BI 中创建的新数据集以及 Power BI Desktop 中的数据和数据模型将加载到数据集中。 如果你的文件有任何报表，则这些报表会显示在你的 Power BI 网站中的“报表”下。

**OneDrive - 企业** – 如果你有 OneDrive for Business，并且使用登录 Power BI 的同一帐户登录到其中，这是将 Power BI Desktop 中的工作与你在 Power BI 中的数据集、报表和仪表板保持同步的有史以来最有效的方法。由于 Power BI 和 OneDrive 都位于云中，Power BI 大约每小时会连接  你在 OneDrive 上的文件一次。 如果发现任何更改，你的数据集、报表和仪表板会在 Power BI 中自动更新。

**OneDrive - 个人** – 如果你将文件保存到自己的 OneDrive 帐户，你会像使用 OneDrive for Business 那样获得很多相同优势。 最大的不同之处在于，当你首次连接至你的文件（使用“获取数据 > 文件 > OneDrive – 个人”）时，你将需要使用 Microsoft 帐户登录 OneDrive，这通常与你用于登录到 Power BI 的帐户不同。 当使用你的 Microsoft 帐户登录 OneDrive 时，请务必选择“使我保持登录状态”选项。 这样一来，Power BI 将能够大约每小时连接你的文件一次，并确保你在 Power BI 中的数据集同步。

**SharePoint 团队网站** – 将 Power BI Desktop 文件保存到 SharePoint 团队网站与保存到 OneDrive for Business 大致相同。 最大的区别是你从 Power BI 连接到文件的方式。 你可以指定一个 URL 或连接到根文件夹。

## <a name="import-or-connect-to-a-power-bi-desktop-file-from-power-bi"></a>从 Power BI 导入或连接到 Power BI Desktop 文件
>[!IMPORTANT]
>可以导入 Power BI 的最大文件大小为 1 千兆字节。

1. 在 Power BI 的导航窗格中，单击**“获取数据”**。
   
   ![](media/service-desktop-files/pbid_get_data_button.png)
2. 在“文件”  中，单击“获取”  。
   
   ![](media/service-desktop-files/pbid_files_get.png)
3. 查找你的文件。 Power BI Desktop 文件具有 .PBIX 扩展名。
   
   ![](media/service-desktop-files/pbid_find_your_file.png)

## <a name="publish-a-file-from-power-bi-desktop-to-your-power-bi-site"></a>将文件从 Power BI Desktop 发布到 Power BI 站点
使用 Power BI Desktop 中的“发布”效果与使用 Power BI 中的“获取数据”相同，都可导入本地驱动器上的文件或连接到 OneDrive 上的文件。  下面介绍了快速操作方法，但也可参阅[从 Power BI Desktop 发布](desktop-upload-desktop-files.md)以了解详细信息。

1. 在 Power BI Desktop 中，单击**文件** > **发布** > **发布到 Power BI**，或在功能区上单击**发布**。
   
   ![](media/service-desktop-files/pbid_publish.png)
2. 登录到 Power BI。 仅首次使用使需执行此操作。
   
   完成后，你将获得一个链接，使用该链接将在 Power BI 网站中打开报表。
   
   ![](media/service-desktop-files/pbid_publishing.png)

## <a name="next-steps"></a>后续步骤
**浏览你的数据** - 将文件中的数据和报表导入到 Power BI 后，就可以浏览文件了。 如果你的文件中已包含报表，则这些文件将显示在**报表**的导航器窗格中。 如果你的文件仅包含数据，你可以创建新报表：右键单击新数据集，然后单击**浏览**即可。

**刷新外部数据源** - 如果你的 Power BI Desktop 文件连接到外部数据源，你可以设置计划的刷新，以确保数据集始终处于最新状态。 在大多数情况下，设置计划刷新非常容易，但本文不会进行详细介绍。 若要了解详细信息，请参阅 [Power BI 中的数据刷新](refresh-data.md)。


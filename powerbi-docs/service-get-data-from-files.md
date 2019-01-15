---
title: 从 Power BI 文件获取数据
description: 了解如何将数据从 Excel、Power BI Desktop 和 CSV 文件导入 Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: cbf0550c12fad37af528622b35584898b3a697f4
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282324"
---
# <a name="get-data-from-files-for-power-bi"></a>从 Power BI 文件获取数据
![](media/service-get-data-from-files/file_icons.png)

在 Power BI 中，可以连接到或从三种类型的文件导入数据和报表。

* Microsoft Excel（.xlsx 或 .xlsm）
* Power BI Desktop (.pbix)
* 逗号分隔值 (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>从文件中获取数据实际意味着什么？
在 Power BI 中，你浏览的数据来自数据集。 但是，首先需要获取一些数据，才能拥有数据集。 本文将重点介绍从文件中获取数据。

为了更好地了解数据集的重要性，以及如何为其获取数据，让我们看一看汽车。 坐在车里，看着仪表板。 这很像坐在计算机前，查看 Power BI 中的仪表板。 仪表板显示汽车正在执行的所有操作：引擎旋转速度、温度、档位、车速等。

在 Power BI 中，数据集就像汽车的引擎。 数据集提供显示在 Power BI 仪表板中的数据、指标和信息。 当然你的引擎（或者说数据集）需要燃油，而在 Power BI 中，燃油就是数据。 汽车具有为引擎提供汽油的油箱。 Power BI 中的情况与此很相似，你需要一个油箱，将其中的数据馈送到数据集。 在我们的例子中，油箱是 Power BI Desktop 文件、Excel 工作簿文件或 .CSV 文件。

我们还可以更进一步。 汽车的油箱需要装满汽油。 对于 Power BI Desktop、Excel 或 .CSV 文件而言，汽油就是来自其他数据源的数据。 我们从其他数据源获取数据，并将其放入 Excel、Power BI Desktop 或 .CSV 文件中。 如果是 Excel 工作簿或 .CSV 文件，我们可以手动输入数据行。 或者，我们可以连接到外部数据源进行查询，并将数据加载到我们的文件中。 当文件有一些数据后，我们可以将其作为数据集放入 Power BI。

> [!NOTE]
> Excel 工作簿中的数据必须位于表或数据模型中，才能由 Power BI 导入。
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>保存文件的位置具有重要意义
**本地** - 如果你将文件保存到计算机上的本地驱动器中或者组织中的其他位置，则在 Power BI 中，你可以将文件导入到 Power BI。 你的文件实际上一直保存在本地驱动器中，因此整个文件并未真正导入到 Power BI。 实际上，在 Power BI 网站中创建新的数据集，数据（某些情况下为数据模型）将加载到数据集中。 如果你的文件有任何报表，则这些报表会显示在你的 Power BI 网站中的“报表”下。

**OneDrive - 企业** – 如果你有 OneDrive for Business，并且使用登录 Power BI 的同一帐户登录到其中，这是将 Excel Power BI Desktop 或 .CSV 文件中的工作与你在 Power BI 中的数据集、报表和仪表板保持同步的有史以来最有效的方法。由于 Power BI 和 OneDrive 都位于云中，Power BI 大约每小时会连接你在 OneDrive 上的文件一次。 如果发现任何更改，你的数据集、报表和仪表板会在 Power BI 中自动更新。

**OneDrive - 个人** – 如果你将文件保存到自己的 OneDrive 帐户，你会像使用 OneDrive for Business 那样获得很多相同优势。 最大的不同之处在于，当你首次连接至你的文件（使用“获取数据 > 文件 > OneDrive – 个人”）时，你将需要使用 Microsoft 帐户登录 OneDrive，这通常与你用于登录到 Power BI 的帐户不同。 当使用你的 Microsoft 帐户登录 OneDrive 时，请务必选择“使我保持登录状态”选项。 这样一来，Power BI 将能够大约每小时连接你的文件一次，并确保你在 Power BI 中的数据集同步。

**SharePoint 团队网站** – 将 Power BI Desktop 文件保存到 SharePoint 团队网站与保存到 OneDrive for Business 大致相同。 最大的区别是你从 Power BI 连接到文件的方式。 你可以指定一个 URL 或连接到根文件夹。

## <a name="ready-to-get-started"></a>准备好开始了吗？
请参阅下列文章了解有关将文件放入 Power BI 的详细信息。

* [从 Excel 工作簿文件中获取数据](service-excel-workbook-files.md)
* [从 Power BI Desktop 文件获取数据](service-desktop-files.md)
* [从逗号分隔值文件中获取数据](service-comma-separated-value-files.md)


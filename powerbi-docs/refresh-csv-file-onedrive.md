---
title: 在 OneDrive 中刷新基于 .csv 文件创建的数据集
description: 在 OneDrive 上刷新使用逗号分隔值 (.csv) 文件创建的数据集
author: davidiseminger
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/12/2019
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: d18d3a5b5d85a121f67c5b3109a150a21ab72d1a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "74699696"
---
# <a name="refresh-a-dataset-created-from-a-csv-file-on-onedrive-or-sharepoint-online"></a>刷新使用 OneDrive 或 SharePoint Online 上的 .CSV 文件创建的数据集
## <a name="what-are-the-advantages"></a>有什么好处？
当连接到 OneDrive 或 SharePoint Online 上的 .csv 文件时，将在 Power BI 中创建数据集。 然后，.csv 文件中的数据将导入 Power BI 中的数据集。 Power BI 将自动连接到该文件，并使用 Power BI 中的数据集刷新任何更改。 如果在 OneDrive 或 SharePoint Online 中编辑 .csv 文件，则在保存之后，通常大约一小时，这些更改将在 Power BI 中显示。 Power BI 中基于数据集的任何可视化效果也会自动更新。

如果你的文件位于 OneDrive for Business 或 SharePoint Online 上的共享文件夹中，那么其他用户可处理同一文件。 在保存之后，Power BI 中将自动更新所做的任何更改，通常在一小时之内。

许多组织都运行自动查询数据库的进程，数据库中的数据每天都保存到 .csv 文件中。 如果该文件存储在 OneDrive 或 SharePoint Online 中，那么每天都将覆盖同一文件，而不是每天都创建一个具有不同名称的新文件，你可以在 Power BI 中连接该文件。 OneDrive 或 SharePoint Online 上的文件更新后将立即同步连接到此文件的数据集。 基于此数据集的任何可视化效果也会自动更新。

## <a name="whats-supported"></a>支持的功能有哪些？
逗号分隔值文件是简单的文本文件，因此，不支持连接到外部数据源和报表。 你无法对使用逗号分隔文件创建的数据集的刷新制定计划。 但是，当文件在 OneDrive 或 SharePoint Online 中时，Power BI 将自动每隔一小时向数据集同步对文件的任何更改。

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive 或 OneDrive for Business。 有什么区别？
如果同时拥有个人版 OneDrive 和 OneDrive for Business，建议将 Power BI 中要连接到的任何文件保存在 OneDrive for Business 中。 原因如下：你有可能使用两个不同的帐户登录到它们。

连接到 Power BI 中的 OneDrive for Business 通常是无缝的，因为你用于登录 Power BI 的同一个帐户通常是用来登录 OneDrive for Business 的同一个帐户。 但使用个人 OneDrive 时，你可能需要使用其他 [Microsoft 帐户](https://account.microsoft.com)才能登录。

登录 Microsoft 帐户时，请确保选中“保持我的登录状态”。 然后 Power BI 将与 Power BI 中的数据集同步任何更新

![登录示例](media/refresh-csv-file-onedrive/refresh_signin_keepmesignedin.png)

如果由于 Microsoft 帐户凭据可能已更改而无法将 OneDrive 上的 .csv 文件的更改与 Power BI 中的数据集进行同步，那么你需要连接到该文件并再次从个人 OneDrive 中导入该文件。

## <a name="when-things-go-wrong"></a>出现问题时
如果 OneDrive 上的.csv 文件中的数据发生更改，并且这些更改反映未在 Power BI 中反映，那么很可能是因为 Power BI 无法连接到 OneDrive。 请尝试连接该文件并再次导入。 如果系统提示你登录，请确保选中**保持我的登录状态**。

## <a name="next-steps"></a>后续步骤
[用于解决刷新问题的工具](service-gateway-onprem-tshoot.md)
[刷新方案故障排除](refresh-troubleshooting-refresh-scenarios.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)


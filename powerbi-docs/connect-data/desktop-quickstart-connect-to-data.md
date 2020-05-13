---
title: 连接到 Power BI Desktop 中的数据的快速入门
description: 如何连接到 Power BI Desktop 中可用的数据源
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: d689258b4e4da5349d57b41f72d4266eb759029b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348588"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>快速入门：连接到 Power BI Desktop 中的数据

在本快速入门教程中，使用 Power BI Desktop 连接到数据，这是生成数据模型和创建报表的第一步。

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

如果未注册 Power BI，请[免费注册](https://app.powerbi.com/signupredirect?pbi_source=web)后再进行操作。

## <a name="prerequisites"></a>必备组件

若要完成本文中的步骤，需要准备好以下资源：

* 下载并安装 Power BI Desktop - 可在本地计算机上运行的免费应用程序。 可以直接[下载 Power BI Desktop](https://powerbi.microsoft.com/desktop)，也可以从 [Microsoft Store ](https://aka.ms/pbidesktopstore)获取该应用。
* [下载此示例 Excel 工作簿](https://go.microsoft.com/fwlink/?LinkID=521962)，并创建一个名为“C:\PBID-qs”  的文件夹，可以在其中存储 Excel 文件。 本快速入门中的后续步骤假设这是已下载的 Excel 工作簿的文件位置。
* 对于 Power BI Desktop 中的大量数据连接器，需要 Internet Explorer 10（或更高版本）进行身份验证。

## <a name="launch-power-bi-desktop"></a>启动 Power BI Desktop

安装 Power BI Desktop 后，启动应用程序，以便它在本地计算机上运行。 你会看到一个 Power BI 教程。 按照教程或关闭对话以从空白画布开始。 在画布中，从数据创建视觉对象和报表。

![使用空白画布的 Power BI Desktop](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>连接到数据

使用 Power BI Desktop 可以连接到许多不同类型的数据。 这些源包括基本数据源，如 Microsoft Excel 文件。 也可以连接到包含各类数据的联机服务，例如 Salesforce、Microsoft Dynamics、Azure Blob 存储等。

若要连接到数据，请在“主页”  功能区中选择“获取数据”  。

![获取“主页”功能区上的数据](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

“获取数据”窗口随机显示  。 在其中从 Power BI Desktop 可以连接到的众多不同数据源中进行选择。 在本快速入门中，请使用[先决条件](#prerequisites)中下载的 Excel 工作簿。

![获取数据所有源](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

由于该数据源是 Excel 文件，请从“获取数据”窗口中选择“Excel”，然后选择“连接”按钮    。

Power BI 提示你提供要连接的 Excel 文件的位置。 下载的文件称为“财务示例”  。 选择该文件，然后选择“打开”  。

![获取财务示例中的数据](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

之后，Power BI Desktop 会加载工作簿并读取其内容，然后在“导航器”窗口显示文件中的可用数据  。 在该窗口中，可以选择要加载到 Power BI Desktop 的数据。 通过标记每个想要导入的表旁边的复选框来选择该表。 导入两个可用表。

![在“导航器”窗口中选择数据](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

一旦作出选择，请选择“加载”将数据导入到 Power BI Desktop 当中。 

## <a name="view-data-in-the-fields-pane"></a>在“字段”窗格中查看数据

表加载完成后，“字段”窗格将显示导入数据。  可以通过选择其名称旁边的箭头展开每个表。 在下图中，“财务”表已展开并显示其中每个字段。 

![获取数据](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

就是这么简单！ 你已使用 Power BI Desktop 连接到数据源并加载该数据，现在可以看到这些表中的所有可用字段。

## <a name="next-steps"></a>后续步骤

一旦连接到数据，便可以通过 Power BI Desktop 执行各类操作。 你可以创建视觉对象和报表。 请参阅以下资源继续：

* [Power BI Desktop 入门](../fundamentals/desktop-getting-started.md)

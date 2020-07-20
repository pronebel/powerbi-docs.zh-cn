---
title: Project Online：通过 Power BI Desktop 连接到数据
description: Project Online：通过 Power BI Desktop 连接到数据
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 04/01/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 807ba59066508d063dba2e2f921eff19cf018bc5
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214596"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>通过 Power BI Desktop 连接到 Project Online 数据
可以通过 Power BI Desktop 连接到 Project Online 中的数据。

## <a name="step-1-download-power-bi-desktop"></a>步骤 1：下载 Power BI Desktop
1. [下载 Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662)，然后运行安装程序，以在计算机上安装 **Power BI Desktop**。

## <a name="step-2-connect-to-project-online-with-odata"></a>步骤 2：通过 OData 连接到 Project Online
1. 打开 **Power BI Desktop**。
2. 在“欢迎”屏幕上，选择“获取数据”。
3. 依次选择“**OData 数据源**”和“**连接**”。
4. 在 URL 框中输入 OData 数据源的地址，然后单击确定。
   
   如果你的 Project Web App 站点的地址类似于 https://\<tenantname\>.sharepoint.com/sites/pwa，则为 OData 源输入的地址是 https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata。
   
   此示例使用的是：

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. Power BI Desktop 将提示你使用工作或学校帐户进行身份验证。 请选择组织帐户，然后输入你的凭据。
   
   ![Power BI Desktop 的屏幕截图，其中显示了要连接的凭据提示。](media/desktop-project-online-connect-to-data/image.png)

用于连接到 OData 源的帐户必须对 Project Web App 站点至少具有项目组合查看者访问权限。 

从此处你可以选择想要连接到的表并生成查询。  想了解如何开始？  下面的博客文章将演示如何从你的 Project Online 数据生成燃尽图。  博客文章中使用了 Power Query 连接到 Project Online，Power BI Desktop 也同样适用。

[使用 Power Pivot 和 Power Query 为项目创建燃尽图](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)


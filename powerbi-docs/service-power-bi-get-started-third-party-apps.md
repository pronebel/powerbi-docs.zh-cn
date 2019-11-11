---
title: Power BI 开始使用第三方应用
description: Power BI 开始使用第三方应用
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.cunstom: ''
ms.date: 09/16/2019
LocalizationGroup: Get started
ms.openlocfilehash: a3c060693a218a4c7a9dc5d0dea726c10e07d276
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871946"
---
# <a name="get-started-with-third-party-apps"></a>开始使用第三方应用

借助 Power BI，你可以使用由 Microsoft 以外的其他公司或个人构建的应用。 例如，可以使用一个第三方应用，该应用将 Power BI 集成到自定义生成的 web 应用程序中。 当你使用第三方应用时，系统将要求你向应用程序授予对你的 Power BI 帐户和资源的某些权限。 重要的一点是，应仅向你知晓和信任的应用程序授予权限。 可随时撤消已授予应用程序的权限。 请参阅[撤消第三方应用权限](#revoke)。

以下是应用程序可以请求的访问权限类型。

## <a name="power-bi-app-permissions"></a>Power BI 应用权限

* **查看所有仪表板**
  
  * 此权限使应用程序可查看你有权访问的所有仪表板。 其中包括你自己的仪表板、你从内容包获取的仪表板、与你共享的仪表板以及你所属的组中的仪表板。 应用程序不能对仪表板做出任何修改。 此权限的作用之一是，应用程序可将你的仪表板内容嵌入到其体验中。

* **查看所有报表**
  
  * 凭借此权限，应用程序能够查看你有权访问的所有报表。 其中包括你自己的仪表板、你从内容包获取的仪表板以及你所属的组中的仪表板。 作为查看报表的一部分，这意味着应用程序也可以查看其中的数据。 应用程序不能对报表本身进行任何修改。 此权限的作用之一是，应用程序可将你的报表内容嵌入到其体验中。

* **查看所有数据集**
  
  * 凭借此权限，应用程序能够列出你有权访问的所有数据集。 其中包括你自己的数据集、你从内容包获取的数据集以及你所属的组中的数据集。 应用程序能够看到你的全部数据集的名称及其结构，其中包括表格和列名称。 该权限给予读取数据集中数据的能力。 该权限不授予应用程序向数据集进行添加或做出更改的权限。
* **读取和写入所有数据集**
  
  * 凭借此权限，应用程序能够列出你有权访问的所有数据集。 其中包括你自己的数据集、你从内容包获取的数据集以及你所属的组中的数据集。 应用程序能够看到你的全部数据集的名称及其结构，其中包括表格和列名称。 该权限给予读写数据集中数据的能力。 应用程序还可以创建新的数据集或对现有数据集进行修改。 应用程序通常使用该权限将数据直接发送到 Power BI。

* **查看用户的组**
  
  * 凭借此权限，应用程序能够列出你所属的所有组。 它可以将此权限与列出的某些其他权限配合使用来查看或更新特定组的内容。 应用程序不能对组本身做出任何修改。

<a name="revoke"/>

## <a name="revoke-third-party-app-permissions"></a>撤销第三方应用权限

可通过转到 Office 365 我的应用网站撤销向第三方应用授予的权限。

下面介绍如何在 Office 365 我的应用  网站上撤销第三方权限：

1. 转到 [Office 365 我的应用网站](https://portal.office.com/myapps)。

2. 在“我的应用”  页上，查找第三方应用。

3. 将鼠标悬停在该应用磁贴上，单击 **(...)** 按钮，然后单击**删除**。

   ![删除](media/service-power-bi-get-started-third-party-apps/remove.png)
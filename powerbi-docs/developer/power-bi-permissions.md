---
title: Power BI 权限
description: Power BI 权限
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 8a48ec007f2d8c9c07de5cc0d51049e3dbf19662
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61269318"
---
# <a name="power-bi-permissions"></a>Power BI 权限

## <a name="permission-scopes"></a>权限范围

Power BI 权限使应用程序能够代表用户执行某些操作。 所有权限均必须经过用户批准才有效。

| 显示名称 | 说明 | 范围值 |
| --- | --- | --- |
| 查看所有数据集 |该应用可以查看已登录用户的所有数据集以及该用户有权访问的数据集。 |Dataset.Read.All |
| 读写所有数据集 |该应用可以查看和写入已登录用户的所有数据集以及该用户有权访问的数据集。 |Dataset.ReadWrite.All |
| 将数据添加到用户的数据集 |对应用授予添加或删除用户的数据集行的访问权限。 此权限不会对应用授予访问用户数据的权限。 |Data.Alter_Any |
| 创建内容 |应用可以自动为用户创建内容和数据集。 |Content.Create |
| 查看用户组 |该应用可以查看已登录用户所属的所有组。 |Group.Read |
| 查看所有组 |该应用可以查看已登录用户所属的所有组。 |Group.Read.All |
| 读取和写入所有组 |该应用可以查看和写入已登录用户的所有组以及该用户有权限访问的任何组。 |Group.ReadWrite.All |
| 查看所有仪表板 |该应用可以查看已登录用户的所有仪表板以及该用户有权访问的仪表板。 |Dashboard.Read.All |
| 查看所有报表 |该应用可以查看已登录用户的所有报表以及该用户有权访问的报表。 该应用还可以查看报表数据及其结构。 |Report.Read.All |
| 读取和写入所有报表 |该应用可以查看和写入已登录用户的所有报表以及该用户有权访问的任何报表。 这不提供创建新报表的权限。 |Report.ReadWrite.All |
| 读取和写入所有容量 |该应用可以查看和写入已登录用户的所有容量以及该用户有权限访问的任何容量。 这不会提供创建新容量的权限。 |Capacities.ReadWrite.All |
| 读取所有容量 |该应用可以查看和写入已登录用户的所有容量以及该用户有权限访问的任何容量。 这不会提供创建新容量的权限。 |Capacities.Read.All |
| 读取和写入租户中的所有内容 |该应用可以查看和写入所有项目，例如 Power BI 中的组、报表、仪表板以及数据集。 前提是已登录用户为 Power BI 服务管理员。 |Tenant.ReadWrite.All |
| 查看租户中的所有内容 |该应用可以查看所有项目，例如 Power BI 中的组、报表、仪表板以及数据集。 前提是已登录用户为 Power BI 服务管理员。 |Tenant.Read.All |

应用程序可以在首次尝试登录到用户页面时通过在调用的范围参数中传入请求的权限来请求权限。 如果授予了该权限，则会向该应用返回一个访问令牌，可在将来的 API 调用上使用该令牌。 该访问权限只能由特定应用程序使用。

> [!NOTE]
> Power BI API 仍将应用工作区视作为组。 对组的任何引用意味着正在使用应用工作区。

## <a name="requesting-permissions"></a>请求权限

虽然你可以调用 API 通过用户名和密码进行验证，以便代表其他用户进行操作，但是他们将需要请求该用户随后批准的权限，然后将生成的访问令牌发送到所有的将来的调用。 对于此过程，我们将遵循标准 [OAuth 2.0](http://oauth.net/2/) 协议。 尽管实际实现可能会有所不同，但 Power BI 的 OAuth 流具有以下元素：

* **登录 UI** - 这是一个开发人员可以调用来请求权限的 UI。 如果用户尚未登录，它将要求该用户登录。 用户还需要批准应用程序请求的权限。 登录窗口将回发访问代码或错误消息，以重定向提供的 URL。
  * 标准重定向 URL 应由 Power BI 提供，以由本机应用程序使用。
* **授权代码** - 通过重定向 URL 中的 URL 参数登录后，授权代码将返回到 Web 应用程序。 由于它们是参数形式，因此存在某些安全风险。 Web 应用程序将必须使用授权代码交换授权令牌
* **授权令牌** - 用于代表其他用户对 API 调用进行验证。 它们将限制用于特定应用程序。 令牌具有已设定的生命周期，过期时，需要将其进行刷新。
* **刷新令牌** - 令牌过期时，将有一个刷新它们的过程。

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
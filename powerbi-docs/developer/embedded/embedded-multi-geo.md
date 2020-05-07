---
title: Power BI Embedded 的 Multi-Geo 支持
description: 了解如何将内容部署到除 Power BI Embedded 主区域以外区域的数据中心。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 269fe87a61df3470a8d11e4934ff1fca4bde7e86
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114649"
---
# <a name="multi-geo-support-for-power-bi-embedded"></a>Power BI Embedded 的 Multi-Geo 支持

Power BI Embedded 的 Multi-Geo 支持意味着，对于使用 Power BI Embedded 构建应用程序并将分析嵌入其应用程序的 ISV 和组织，现在可以在全球不同地区部署其数据  。

现在，使用 Power BI Embedded  的客户可以根据 [Power BI Premium 支持使用 Multi-Geo](../../service-admin-premium-Multi-Geo.md) 中的相同功能和限制，通过“Multi-Geo”  选项设置 A 容量  。

## <a name="creating-new-power-bi-embedded-capacity-resource-with-multi-geo"></a>使用 Multi-Geo 创建新的 Power BI Embedded 容量资源

在“创建资源”  屏幕中，需要选择容量的位置。 到目前为止，它仅限于你的 Power BI 租户的位置，因此只有一个位置可用。 使用 Multi-Geo，可以在不同区域之间进行选择以部署容量。

![Power BI Embedded Multi-Geo 设置](media/embedded-multi-geo/pbie-multi-geo-setup.png)

请注意，打开位置下拉菜单时，主租户为默认选项。
  
![Power BI Embedded Multi Geo 默认位置](media/embedded-multi-geo/pbie-multi-geo-default-location.png)

选择其他位置时，会显示一条消息，提示你确认已知道该选择。

![位置更改](media/embedded-multi-geo/pbie-multi-geo-location-change.png)

## <a name="view-capacity-location"></a>查看容量位置

可以在 Azure门户中转到 Power BI Embedded 管理主页面，轻松查看容量位置。

![不同位置的容量](media/embedded-multi-geo/pbie-multi-geo-location-different.png)

还可以在 Powerbi.com 中的管理门户中查看。 在管理门户中，选择“容量设置”，然后切换到“Power BI Embedded”选项卡。

![在管理门户中查看](media/embedded-multi-geo/pbie-multi-geo-admin-portal.png)

[详细了解如何创建 Power BI Embedded 容量。](azure-pbie-create-capacity.md)

## <a name="manage-existing-capacities-location"></a>管理现有容量位置

创建新的容量后，不能更改 Power BI Embedded 的资源位置。

要将 Power BI 内容移动到其他区域，请按照下面的步骤操作：

1. 在不同区域中[创建新的容量](azure-pbie-create-capacity.md)。

2. 将现有容量中的所有工作区分配给新容量。

3. 删除或暂停旧的容量。

请务必注意，如果决定在不重新分配内容的情况下删除容量，则该容量中的所有内容都将移至共享容量，该容量位于主区域中。

## <a name="api-support-for-multi-geo"></a>Multi-Geo 的 API 支持

为通过 API 支持使用 Multi-Geo 管理容量，我们对现有 API 进行了一些更改：

1.  [获取容量](https://docs.microsoft.com/rest/api/power-bi/capacities/getcapacities) - API 向用户返回一列具有访问权限的容量。 现在，响应包含一个名为“region”的附加属性，用于指定容量的位置。

2.  [分配到容量](https://docs.microsoft.com/rest/api/power-bi/capacities) - API 允许将给定的工作区分配到容量。 此操作不允许将工作区分配到主区域之外的容量，也不允许在不同区域的容量之间移动工作区。 要执行此操作，用户或[服务主体](embed-service-principal.md)仍需要工作区的管理员权限，以及目标容量的管理或分配权限。

3.  [Azure 资源管理器 API](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities)：所有 Azure 资源管理器 API 操作（包括创建  和删除  ）都支持 Multi-Geo。

## <a name="limitations-and-considerations"></a>限制和注意事项

* 在启动数据传输之前，确认在区域之间发起的任何移动都遵循所有企业和政府的合规性要求。

* 存储在远程区域中的缓存查询将停留在该区域内。 然而，传输中的其他数据可能在不同地区之间来回切换。

* 当在 Multi-Geo 环境中将数据从一个区域移动到另一个区域时，源数据可能保留在从中移出数据的区域内达 30 天。 在此期间，用户无权访问该数据。 该数据会在 30 天内从该区域中删除并销毁。

* 一般情况下，Multi-Geo 不会促进性能提升。 加载报表和仪表板仍涉及到对主区域元数据的请求。

## <a name="next-steps"></a>后续步骤

请参考以下链接，详细了解 Power BI Embedded 容量和所有容量的 Multi-Geo 选项。

* [Power BI Embedded 是什么？](azure-pbie-what-is-power-bi-embedded.md)

* [创建 Power BI Embedded 容量](azure-pbie-create-capacity.md)

* [Power BI Premium 容量中的 Multi-Geo](../../service-admin-premium-multi-geo.md)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
---
title: 仪表板数据分类
description: 了解仪表板数据分类，包括管理员应如何设置以及仪表板所有者可如何更改分类。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 08/10/2017
LocalizationGroup: Dashboards
ms.openlocfilehash: e576cb5c0092d61d8c4b30fd180f66cef2922b0e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388784"
---
# <a name="dashboard-data-classification"></a>仪表板数据分类
每个仪表板都不同，具体取决于你连接到的数据源，你可能会发现你和你与其共享的同事将需要根据数据的敏感性采取不同的预防措施。 一些仪表板永远不应与公司外部的人员共享，或打印出来，而其它仪表板则可以随意共享。 通过使用仪表板数据分类，你将能够提高查看你仪表板的人员应使用何种安全级别方面的意识。 你可以使用公司 IT 部门定义的分类来标记仪表板，以便查看该内容的每个人对于数据的敏感性都有相同层面的理解。

![仪表板的屏幕截图，其中显示了示例中的数据分类。](media/service-data-classification/dashboard_tagged_as_hbi.png)

## <a name="data-classification-tags"></a>数据分类标记
数据分类标记显示于仪表板名称旁，让任何查看它的人都知道应该应用到仪表板和其所包含的数据的安全级别。

![仪表板的屏幕截图，其中显示了仪表板名称旁的数据分类标记。](media/service-data-classification/tag_next_to_title.png)

它也会在你的收藏夹列表中的仪表板磁贴旁显示。

![收藏夹列表的屏幕截图，其中显示了收藏夹列表中仪表板磁贴旁的数据分类标记。](media/service-data-classification/tag_on_dashboard_tile.png)

将鼠标悬停在标记上时，你将看到该分类的完整名称。

![HBI 标记的屏幕截图，其中显示了将鼠标悬停在标记上时的分类全名。 ](media/service-data-classification/tag_tooltip.png)

管理员还可以设置标记的 URL，以提供附加信息。

> [!NOTE]
> 根据你的管理员设置的分类设置，某些分类类型可能不会在仪表板上显示为标记。 如果你是仪表板所有者，你可以随时在仪表板设置下检查仪表板分类类型。
> 
> 

## <a name="setting-a-dashboards-classification"></a>设置仪表板的分类
如果为你的公司启用了数据分类，则所有仪表板均以默认分类类型开始，但作为仪表板所有者，你可以更改分类以匹配你的仪表板安全级别。

若要更改分类类型，请执行以下操作：

1. 通过选择仪表板名称旁的省略号，然后选择“设置”，转到仪表板设置。
   
    ![仪表板的屏幕截图，其中显示了“设置”选项。](media/service-data-classification/dashboard_settings.png)
2. 在仪表板设置下，你将能够看到仪表板的当前分类，然后使用下拉列表来更改分类类型。
   
    ![仪表板设置的屏幕截图，其中显示了当前分类和“数据分类”下拉列表选项。](media/service-data-classification/classification_setting_dropdown.png)
3. 完成时，选择“应用”。

应用更改后，你与之共享的任何人都将在下次重新加载仪表板时看到更新。

## <a name="working-with-data-classification-tags-as-an-admin"></a>作为管理员使用数据分类标签
通过组织的全局管理员设置数据分类。 若要开启数据分类，请执行以下操作：

1. 选择“设置”齿轮，然后选择“管理门户”。
   
    ![“设置”齿轮的屏幕截图，其中显示了“管理门户”选项。](media/service-data-classification/admin_portal_in_settings.png)
2. 在“租户设置”选项卡中，将“仪表板和报表的数据分类”切换为“开启”。
   
    ![“管理门户”的屏幕截图，其中显示了“租户设置”以及“仪表板和报表的数据分类”选项。](media/service-data-classification/data_classification_switch_location.png)

开启后，将出现一个用于在组织中创建各种分类的表单。

![表单的屏幕截图，其中显示了组织中各种分类的字段条目。](media/service-data-classification/blank_classification_form.png)

每个分类都有“名称”和“速记形式”，这将显示在仪表板上。 对于每个分类，通过选择“显示标记”，你可以决定是否在仪表板上显示速记标记。 如果你决定不在仪表板上显示分类类型，所有者将仍然能够通过检查仪表板设置来查看类型。 此外，你可以选择添加一个包含你的组织分类指南和使用要求相关的详细信息的 **URL**。  

你需要决定的最后一件事是将哪个分类类型作为默认类型。  

使用分类类型填充表单后，请选择“应用”以保存更改。

![表单的屏幕截图，其中显示了要应用的分类类型的已填充条目。](media/service-data-classification/filled_in_classification_form.png)

此时，将为所有仪表板分配默认分类。 仪表板所有者现在可以将分类类型更新为适合其内容的类型。 之后你可以返回此处来添加或删除分类类型或更改默认类型。  

> [!NOTE]
> 返回此处进行更改时，需要注意几个重要事项：
> 
> * 如果关闭数据分类，将不会记住任何标记。 如果之后你决定重新打开它，你将需要重新启动。  
> * 如果删除了一个分类类型，则任何分配了该已删除分类类型的仪表板都将被分配回默认设置，直到所有者再次进入并重新设置。  
> * 如果更改默认设置，则所有未经所有者分配分类类型的仪表板都将更改为新的默认设置。
> 
> 

